---
title: "Sonic Namespace"
description: "Runtime information about the init system and seat manager."
---

# Sonic Namespace

Runtime information about the init system and seat manager.

## Namespaces {#namespaces}

### namespace Sonic::InitInfo

Detection reads PID 1's identity and that init's own configuration; it never consults runtime marker files. Nothing is cached, so callers that query repeatedly should keep the result.

In containers and sandboxes PID 1 is the sandbox helper, so [Pid1::Unknown](sonic-initinfo.md#Pid1-enum), [ServiceManager::Unknown](sonic-initinfo.md#ServiceManager-enum) and [SeatManager::None](sonic-initinfo.md#SeatManager-enum) are normal results that callers must handle.
