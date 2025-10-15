---
title: Run DME as a Docker Container
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The DME is designed as an embedded device with a large flexible feature set. It is able to run in a [virtual environment](doc:install-a-new-dme#ovf-software-only-dme-installation) and now as a **Docker** container.  Please review the Prerequisites and Assumptions before attempting any installation.

## Prerequisites and Assumptions

Key Assumptions:

* For the first release of the DME [Docker](https://www.docker.com/) container, the entire feature set provided by the DME will run in a single container. 
* The DME **Docker** container uses a **Rocky 8** operating system with **systemd** managing the services running in the container.
* The DME **Docker** container runs in **Docker Host Network** mode.  An overview and tutorial on [Host networking](https://docs.docker.com/network/host/) can be found in the **Docker** documentation.  The DME uses IPV6 internally so it needs to be enabled on the host whether or not you intend to have DME do networking via IPV6.  
* DME **Docker** container is targeted to be deployed on **RedHat 8 Host v239** host OS -- with standard OS packages for **RHEL8**. After v3.34, it can also be deployed on a **Rocky 8** host OS -- with standard OS packages.
* The DME **Docker** container must be provisioned (at a minimum) with the requisite hardware (CPU, Memory, Disk) requirements dependent upon the licensing and use cases required by each customer.  For this Docker version, we require the same HW requirements per DME size as required by our VM installations.  Please see [Virtual DME Recommendations](doc:pre-installation-requirements#virtual-dme-hardware-specifications-and-load-recommendations) to make sure you understand the hardware and available load requirements for your specific use case. 
* The host OS enables the **firewalld** service by default. This service must be either disabled or configured to allow the ports in the table below.

It is important that you review [Pre-Installation Requirements](doc:pre-installation-requirements) and DME [installation](doc:install-a-new-dme) procedures. 

## Port Configuration

As mentioned above, the DME Docker container must be run in **Docker Host Network** mode, on a **RedHat 8 Host v239** host or **Rocky 8** host which will enable the service **firewalld** by default.  If you do not disable this service, it must be configured to allow the ports below.

| Port      | Protocol      | Component                                 | External or Internal |
| :-------- | :------------ | :---------------------------------------- | :------------------- |
| 20        | TCP           | ftp data port                             | External             |
| 21        | TCP           | ftp command port                          | External             |
| 222       | TCP           | ssh                                       | External             |
| 53        | UDP/TCP       | DNS and DNSSEC look up                    | External             |
| 80        | TCP           | squid - HTTP port                         | External             |
| 123       | UDP           | chrony -  ntp comms                       | External             |
| 161       | UDP           | SNMP                                      | External             |
| 162       | UDP           | SNMP traps                                | External             |
| 323       | UDP           | chrony – ntp comms                        | External             |
| 443       | TCP           | squid – HTTPS port                        | External             |
| 514       | UDP           | Remote logging                            | External             |
| 554       | TCP           | VBrickStreamingServer RTSP port           | External             |
| 1935      | TCP           | RTMPServer RTMP server port               | External             |
| 3130-3138 | UDP           | dme-squid ICP comms port                  | External             |
| 4443      | TCP           | RTMPServer RTMPS server port              | External             |
| 5544      | TCP           | RTMPServer RTSP server port               | External             |
| 8022      | TCP           | SFTP port                                 | External             |
| 8080      | TCP           | VBrickStreamingServer HTTP tunnel port    | External             |
| 8181      | TCP           | streamingadminserver HTTP webserver port  | External             |
| 8383      | TCP           | streamingadminserver HTTPS webserver port | External             |
| 9875      | UDP multicast | Management SAPs                           | External             |
| 9876      | UDP multicast | Stream SAPs                               | External             |

## Installations and Upgrades

There are two different methods for pulling, running, and managing the DME Docker container, including running with or without using the [Docker Compose plugin](https://docs.docker.com/compose/install/linux/#install-the-plugin-manually) installed. 

Both methods *require* that you retrieve the DME Docker image. The DME Docker image is available in the Vbrick Docker repo. If you do not already have access to the Docker repo and image, please contact [Vbrick Support](https://vbrick.com/support/) to gain access.

### The Docker Compose Plugin

> 👍 Tip
>
> We recommend that the Docker Compose plugin is installed on the Docker host machine and used to manage your deployment.

 To install the plugin on RHEL8 or Rocky 8 use the following command:

```
    curl -L "https://github.com/docker/compose/releases/download/v2.15.1/docker-compose-linux-x86_64" -o 
    /usr/local/bin/docker-compose
```

A sample Docker Compose **YAML** file (displayed below) will be supplied along with details regarding the DME docker repository. 

> 📘 Note
>
> It is assumed that commands are run from the same folder as a YAML file named `docker-compose.yaml`.  Compose, by default, operates on a file named docker-compose.yaml in the local directory. 
>
> If you want to run Compose with a different filename or directory, you can use the `-f` option with any of the [Compose file run actions](doc:dme-installation-in-a-docker-container#docker-compose-file-run-command-field-descriptions) to specify the path and file name.

### Using the Docker Compose Plugin

> 📘 Note
>
> The sample YAML Compose file provided by Vbrick *must* be customized for your environment. Each of the fields in the file is displayed below.
>
> Our sample Compose file includes a version line which was supported in older Compose versions but may cause a yaml warning message that 'version' is obsolete in newer Compose versions.  The message can be ignored.

<h4>Docker Compose Sample YAML File</h4>

```yaml YAML
version: "3.9"
services:
  dme-docker:
    cap_add:
      - CAP_SYS_TIME
      - CAP_SYS_NICE
      - CAP_SYS_ADMIN
    dns:
      - 172.16.0.121
      - 172.16.0.122
    dns_search: vb.loc
    hostname: dme-hostname
    network_mode: host
    container_name: dme-docker-container
    image: 651425670494.dkr.ecr.us-east-1.amazonaws.com/dme-docker or dme-docker
    restart: unless-stopped
    cpu_count: 4
    cpuset: 0-3
    mem_limit: 16G
    memswap_limit: 48G
    tmpfs:
      - /run
      - /tmp
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
      - dme-content-disk:/lvm      
    environment:
        DOCKERETH0: ens192
             
volumes:
  dme-content-disk:
```

To manage your **DME Docker** container using the **Compose** plugin, complete each step below.

1. Pull the Docker image.

   `docker-compose pull `

2. Run the DME Docker container.

   `docker-compose up -d`

3. Upgrade the DME Docker container.  If Vbrick releases a new version of the DME, to apply this upgrade without losing data and/or files stored in the container's persistent volume, perform the following commands:

   `docker-compose stop`\
   `docker-compose down`\
   `docker-compose pull`\
   `docker-compose up -d`

### Without Using the Docker Compose Plugin

To manage your **DME Docker** container *without* using the **Compose** plugin, complete each step below.

1. Pull the Docker image from the Vbrick repo provided to you.

   `docker pull <DME-Docker-Repo>:<release-tag>`

2. Create the volume that stores the DME's persistent data.

   `docker volume create dme-content-disk`

3. Run the DME Docker container. This command *must* be customized for your Host environment, demonstrated below.

   ```
   docker run –itd --tmpfs /tmp --tmpfs /run –v /sys/fs/cgroup:/sys/fs/cgroup:ro --mount source=dme-content- 
   disk,target=/lvm --dns 172.16.0.121 --dns 172.16.0.122 --dns-search vb.loc --hostname=dme-hostname
   --cap-add=CAP_SYS_NICE --cap-add=CAP_SYS_TIME --cap-add=CAP_SYS_ADMIN --network host --cpuset-cpus 0-3 --memory 16G --memory-swap 
   48G --name dme-docker-container --env DOCKERETH0=ens192 
   651425670494.dkr.ecr.us-east-1.amazonaws.com/dme-docker or<dme-docker
   ```

4. Upgrade the DME Docker container.  A DME running on Docker cannot be upgraded from Rev Admin.  When Vbrick releases a new version of the DME, to apply the upgrade without losing data and/or files stored in the container's persistent volume, perform the following commands. Make sure to map the same Docker volumes you used *before* the upgrade:

     `docker stop dme-docker-container`\
     `docker rm dme-docker-container`\
     `docker pull retro2.lab.vbrick.com:4043/dme-docker`

   ```
   docker run –itd --tmpfs /tmp --tmpfs /run –v /sys/fs/cgroup:/sys/fs/cgroup:ro --mount source=dme-content- 
   disk,target=/lvm --dns 172.16.0.121 --dns 172.16.0.122 --dns-search vb.loc --hostname=dme-hostname --cap-add=CAP_SYS_NICE --cap-add=CAP_SYS_TIME --cap-add=CAP_SYS_ADMIN --network host --cpuset-cpus 0-3 --memory 16G --memory-swap 
   48G --name dme-docker-container --env DOCKERETH0=ens192 
   651425670494.dkr.ecr.us-east-1.amazonaws.com/dme-docker or dme-docker
   ```

> 📘 Note
>
> It is important that you type the run command instead of attempting to copy/paste from this document to your Docker host because non-printable characters can be added during a copy/paste that may corrupt your command line entry.

## Initialize the DME Docker Container

The DME Docker container requires a one-time initialization step at the time of its first deployment just as any other DME installation requires.  Use the following Docker command to determine if your container has started correctly and is fully functional.

`docker logs dme-docker-container`

If the last line in the logs displays `Your current IP address is: xxx.xx.xxx.xx` or `Starting DME container`, your DME should be accessible via its Web page or its [SSH CLI](doc:secure-shell-ssh-administration).  On initial deployment, it may take 1-2 minutes to reach this point.

Once you confirm the DME Docker container is running, initialize it by completing the following steps (this is a one-time series of steps you must follow):

1. [Login to VBAdmin](doc:dme-login-options). The default username and password is `admin/admin`. You will be presented with the EULA that you should review and accept. You are presented with the ability to apply a DME license file. You may need to contact Vbrick Customer Support to get the license file and, if so, please have your DME Mac address available (DME displays this on the License page.).  View the [Register the DME](doc:register-the-dme) topic for details on license types on how to apply them.

2. Once the licensing method has been chosen and applied, the DME container restarts its services. The Web page will be inaccessible for about 30 seconds. When the Web page is accessible again, login to the VBAdmin again and navigate to the [Manage Configuration](doc:configuration-files-and-factory-defaults) tab under **System Configuration**.  Select **Set Factory Defaults**. This will again cause the DME to reset its services.

3. When the web page is accessible again login to the web interface again and navigate to the **Manage Configuration** tab. Select **Set Defaults**. Once again this causes a reset of the services.

4. When the Web page is accessible again it is recommended that you login to the Web interface and navigate to the [SSL Certificates](doc:ssl-certificates) tab under **System Configuration** and follow the instructions under the section entitled **Install a New Certificate** to apply an SSL certificate to the DME. The DME services will be restarted once more after applying the certificate.

5. Finally, now that your **SSL certificate** is installed you may want to login to the Web interface one more time and navigate to the [Security](doc:security-settings) tab under **System Configuration** and select **HTTPS Only** for the **External VBAdmin** setting. This will prevent insecure access to the DME via its Web interface. Changing this setting will reset the services one more time. 

6. Your DME Docker container is now ready for use.

## Docker Compose File Run Commands

This table describes how the fields in the run command or Docker Compose file are used by the Docker container and calls out any fields that may or should be modified.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Field
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        cap\_add
      </td>

      <td>
        Allows the user to add capabilities to the docker container. It is required that this field be set to CAP\_SYS\_NICE. In addition the user may choose to add the following capabilities to the DME docker container. This field should include CAP\_SYS\_TIME in order to allow the DME to utilize network time protocol (NTP). This field should include CAP\_SYS\_ADMIN in order to allow the user to use SFTP (SSH FTP) as an external FTP mode to connect to the DME.
      </td>
    </tr>

    <tr>
      <td>
        dns\:/--dns
      </td>

      <td>
        Allows the user to specify the addresses of the DNS servers available in their network. This field should be changed by the user to match the address(es) of the DNS servers on their network.
      </td>
    </tr>

    <tr>
      <td>
        dns\_search:/--dns-search vb.loc
      </td>

      <td>
        Allows the user to set the search domain for DNS. This field should be changed by the user to match the search domain that is appropriate for their network.
      </td>
    </tr>

    <tr>
      <td>
        hostname:/--hostname
      </td>

      <td>
        This field must be modified before running the DME Docker container.  It must be set to the name that matches the Docker container IP address in your network DNS configuration.  

        If you change this field it is recommended that you stop and remove an existing Docker container before running the container with the changed hostname. You do not need to remove any created volumes.
      </td>
    </tr>

    <tr>
      <td>
        network\_mode/--network
      </td>

      <td>
        This field must be set to host and should *not* be modified.
      </td>
    </tr>

    <tr>
      <td>
        container\_name/--name
      </td>

      <td>
        The default container name is `dme-docker-container` but can be modified to fit your preference.
      </td>
    </tr>

    <tr>
      <td>
        image
      </td>

      <td>
        This must be set to [651425670494.dkr.ecr.us-east-1.amazonaws.com/dme-docker](651425670494.dkr.ecr.us-east-1.amazonaws.com/dme-docker) if you pulled the image from the Vbrick docker repo in Amazon, or "dme-docker" if an exported image was provided to you by a Vbrick representative.  

        * \*Note:\*\*  This may, and likely will, be changed with the full release of this feature.
      </td>
    </tr>

    <tr>
      <td>
        restart
      </td>

      <td>
        Optional field that is used to describe the restart behavior of the container.
      </td>
    </tr>

    <tr>
      <td>
        cpuset:/--cpuset-cpus
      </td>

      <td>
        Allows you to specify which processors the container is allowed to use in its processing.  Note that this value should be set appropriately based on your use case. Please see [Virtual DME Recommendations](doc:pre-installation-requirements#virtual-dme-hardware-specifications-and-load-recommendations) to make sure you understand the hardware and available load requirements for your specific use case.  

        It is important to specify this value. It is used by the container not only for status but also for determining how many processes and or threads will be spawned by various services within the container.
      </td>
    </tr>

    <tr>
      <td>
        mem\_limit:/–memory
      </td>

      <td>
        Allows you to restrict the amount of RAM that the container is allowed to use. Note that this number should be set appropriately based on your use case.  Please see [Virtual DME Recommendations](doc:pre-installation-requirements#virtual-dme-hardware-specifications-and-load-recommendations) to make sure you understand the hardware and available load requirements for your specific use case.  

        The RAM usage reported on the DME Docker container web interface will include both the memory used by the DME-specific code plus the memory overhead required by Docker to operate the container. This value will match that reported by the Docker stats command on the Docker host. This is important to note if you have set memory limits for the container in your run command or compose file.  

        This is an optional field.
      </td>
    </tr>

    <tr>
      <td>
        memswap\_limit:/--memory-swap
      </td>

      <td>
        Allows you to specify the maximum amount of swap available to the container. This field value is the sum of physical ram plus swap. Note that this number should be set appropriately based on your use case.  Please see [Virtual DME Recommendations](doc:pre-installation-requirements#virtual-dme-hardware-specifications-and-load-recommendations) to make sure you understand the hardware and available load requirements for your specific use case.  

        This is an optional field.
      </td>
    </tr>
  </tbody>
</Table>

### TMPFS Folders Requirements

| Field           | Description                                                                                                                                                     |
| :-------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| tmpfs\:/--tmpfs | The DME Docker container requires two tmpfs folders to be created `/run` and `/tmp`. These fields must *not* be changed in the run command or the Compose file. |

### Volume Requirements

`volumes:/-v or --mount` - There are two volumes used by the DME Docker container.  Both are described in the table below.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Volume
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        /sys/fs/cgroup\:/sys/fs/cgroup:ro
      </td>

      <td>
        The services within the DME Docker container are managed by `systemd`.  

        `systemd` running in a Docker container requires read only access to the cgroup folder on the host. For this reason, this read only volume is required by the DME Docker container and must *not* be modified in the run command or the Compose file.
      </td>
    </tr>

    <tr>
      <td>
        dme-content-disk:/lvm/--mount source=dme-content-disk,target=/lvm
      </td>

      <td>
        This volume maps the DME Docker container's persistent data to a Docker volume stored on the host.  

        While this volume is required by the DME and the target name is required to be `/lvm`, the name of the Docker volume is not important.  

        Keep in mind that if you are using a Compose file and you modify the volume name under the volumes: section under services: you must make the same name change under the top-level volumes: section. Furthermore, if you allow Docker Compose to create the volume, Docker Compose will prepend the volume name with `compose_`.  

        By default, Docker places its volumes in the path `/var/lib/docker`. If you wish to change this path to a different location, please refer to [https://docs.docker.com/engine/reference/commandline/dockerd/](https://docs.docker.com/engine/reference/commandline/dockerd/) for instructions for setting the "data-root" run time parameter which can be used for this purpose.
      </td>
    </tr>
  </tbody>
</Table>

### Environment Variables

The following commands are used to manage your environment variables:

* Run Command: use `–env`
* Compose File: use `environment:` 

| Variable   | Description                                                                                                                                                                                                        |
| :--------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DOCKERETH0 | Use this environment variable to specify the name of the host ethernet interface that should be used by the DME. If this environment variable is not specified, the container will attempt to use eth0.            |
| SSHPORT    | Use this environment variable to change the default ssh port used by the Docker container. The default port used by the container is 222, which avoids the ssh port of 22 used by RHEL8 and Rocky 8 distributions. |

## Caveats and Limitations

The initial release of the DME Docker container contains the following caveats and restrictions. It is expected that many of these restrictions will no longer apply in subsequent releases.

* The DME **Docker** container will only support the use of one network interface for the initial release. This interface will not be the result of ethernet bonding.
* You may not change any network settings or the hostname using the DME Web interface but it is permissible within the CLI accessible through SSH. However, you should avoid making any changes to network settings or OS level settings when using the CLI.
* The [Trace Capture](doc:traceroute-test) feature on the **Diagnostics** menu in the Web interface will allow you to select any of the host interfaces when configuring a packet capture on the DME Docker.
* The DME utilizes a content disk for storing VOD videos, live HLS content, logs, and other files. In the case of a DME Docker container, this content disk will actually be a Docker volume on the host. While the DME runs an LRU algorithm to manage usage on its content disk, it is your responsibility to ensure that the size of the content disk allows for leftover disk space to operate the host.
