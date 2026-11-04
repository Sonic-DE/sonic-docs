---
title: "Sonic Namespace"
description: "Framed peer-to-peer messages over local sockets."
---

# Sonic Namespace

Framed peer-to-peer messages over local sockets.

## Namespaces {#namespaces}

### namespace Sonic::Ipc

The Sonic IPC frame. Big-endian header of 20 bytes, then the payload:

| Type | Field |
| --- | --- |
| quint32 | magic 0x534F4E43 |
| quint16 | frame format 1 |
| quint16 | application protocol |
| quint32 | type |
| quint32 | payload length |
| quint32 | CRC-32 of the payload |
