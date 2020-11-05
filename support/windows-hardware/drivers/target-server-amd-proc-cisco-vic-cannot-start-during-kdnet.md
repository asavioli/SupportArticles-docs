---
title: Target server that has AMD processor and CISCO VIC cannot start if KDNET debugging is enabled
description: This article discusses a workaround for an issue that affects network kernel (KDNET) debugging on target servers that have AMD processors and Cisco virtual interface card (VIC) adapters.
ms.date: 10/27/2020
author: Teresa-Motiv
ms.author: v-tea
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-hardware
localization_priority: medium
ms.reviewer: kaushika
keywords: amd processor, cisco VIC
ms.prod-support-area-path: Kerberos authentication
ms.technology: drivers
---
# Target server that has AMD processor and CISCO VIC cannot start if KDNET debugging is enabled

This article discusses a workaround for an issue that affects network kernel (KDNET) debugging on target servers that have AMD processors and Cisco virtual interface card (VIC) adapters.

_Original product version:_ &nbsp;Windows Server 2019, version 2004 and earlier versions, Windows Server 2016

## Symptoms

You try to use KDNET network kernel debugging, and your target server meets all the following criteria:

- The operating system is Windows Server 2019, version 2004 or an earlier version, or Windows Server 2016.
- The server has an AMD processor installed.
- The server has a Cisco virtual interface card (VIC) adapter installed.

You set up the target and host servers, and turn on KDNET debugging (by using **bcdedit /debug on**). However, when you restart the target server, the startup process stops at the Windows logo screen.

## Cause

This is a known issue for the specific configurations that are described in the "Symptoms" section. The issue has been fixed in Windows Server versions that are later than Windows Server 2019, version 2004.

## Workaround

To work around this issue, open an administrative Command Prompt window on the target server, and then run the following commands:

```cmd
bcdedit.exe /set {bootmgr} bootdebug true
bcdedit.exe /set {default} bootdebug true
```

After you run these commands, restart the target server as you typically do for KDNET debugging.

## References

- [Setting Up Kernel-Mode Debugging](https://docs.microsoft.com/windows-hardware/drivers/debugger/setting-up-kernel-mode-debugging-in-windbg--cdb--or-ntsd)
- [BCDEdit Command-Line Options](https://docs.microsoft.com/windows-hardware/manufacture/desktop/bcdedit-command-line-options)