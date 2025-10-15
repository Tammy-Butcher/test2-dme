---
title: Supported Protocols
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
<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Protocol
      </th>

      <th style={{ textAlign: "left" }}>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        Incoming
      </td>

      <td style={{ textAlign: "left" }}>
        <ul>
          <li>RTSP Announce</li>
          <li>RTP Over UDP (with RTCP) Unicast and Multicast</li>
          <li>RTP over TCP (with RTCP) Unicast Only</li>
          <li>RTP over UDP (SDP file delivered via FTP)</li>
          <li>FTP for VOD file transfer</li>
          <li>RTMP via RTMP Push over TCP</li>
          <li>Transport Stream (MPEG2TS delivery of H.264 audio and video content)</li>
        </ul>
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Outgoing
      </td>

      <td style={{ textAlign: "left" }}>
        <ul>
          <li>RTP via RTSP (stream)</li>
          <li>UDP, TCP Interleaved, and HTTP Tunneled</li>
          <li>RTP via RTSP (relay - Push)</li>
          <li>UDP, TCP Interleaved using Announce</li>
          <li>RTMP (stream and relay)</li>
          <li>RTMP</li>
          <li>HTTP (progressive download)</li>
          <li>TS (transport stream)</li>
          <li>HLS (Apple HTTP iPad/iPhone live streaming)</li>
          <li>HDS</li>
          <li>HTTP Caching Server</li>
        </ul>
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Management
      </td>

      <td style={{ textAlign: "left" }}>
        <ul>
          <li>HTTP/HTTPS for management</li>
          <li>IGMPv3</li>
        </ul>
      </td>
    </tr>
  </tbody>
</Table>