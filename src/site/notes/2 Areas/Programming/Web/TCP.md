---
{"dg-publish":true,"permalink":"/2-areas/programming/web/tcp/","tags":["internet"],"created":"2025-12-30T15:47:18.810+07:00","updated":"2025-12-30T15:59:07.507+07:00"}
---

TCP (Transmission Control Protocol) is a transport-layer protocol that reliably delivers a stream of bytes between two hosts. Key traits:
- Connection-oriented: client and server perform a handshake to establish a session.
- Reliable, ordered delivery: retransmits lost data, reorders out-of-sequence packets, removes duplicates.
- Flow and congestion control: adjusts sending rate to match receiver capacity and network conditions.
- Byte-stream abstraction: apps read/write a continuous stream, while TCP handles packetization under the hood.