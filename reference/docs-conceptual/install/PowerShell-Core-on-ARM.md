---
title: Power shell Core installeren op arm
description: Power shell Core installeren op arm-gebaseerde systemen
ms.date: 11/11/2020
ms.openlocfilehash: 1477b99767c19d24f8540714942f63c8347550e9
ms.sourcegitcommit: ef25c8bc95df12697725958c9814f0e187cfc683
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/12/2021
ms.locfileid: "98130136"
---
# <a name="powershell-core-on-arm"></a>Power shell Core op arm

Ondersteuning van Power shell op arm is gebaseerd op het door **.net core ondersteunde besturingssysteem levenscyclus beleid**.

Power shell 7,0 is gebaseerd op het [.net Core 3,1 ondersteunde besturingssysteem levenscyclus beleid](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) en ondersteunt de volgende platforms:

|         Besturingssysteem          |          Versie           | Architecturen |          Levenscyclus           |
| ------------------- | -------------------------- | ------------- | ---------------------------- |
| Windows nano server | Versie 1803 +              | Arm32         | [Windows][Windows-lifecycle] |
| Alpine Linux        | 3.10 +                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian              | 9 +                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu              | 20,10, 20,04, 18,04, 16,04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

Power shell 7,1 is gebaseerd op het door [.net 5,0 ondersteunde besturingssysteem levenscyclus beleid](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) en ondersteunt de volgende platforms:

|        Besturingssysteem         |          Versie           | Architecturen |          Levenscyclus           |
| ----------------- | -------------------------- | ------------- | ---------------------------- |
| Windows 10-client | Versie 1709 +              | Arm64         | [Windows][Windows-lifecycle] |
| Alpine Linux      | 3.11 +                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian            | 9 +                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu            | 20,10, 20,04, 18,04, 16,04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

[Windows-lifecycle]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Alpine-lifecycle]: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases
[Debian-lifecycle]: https://wiki.debian.org/DebianReleases
[Ubuntu-lifecycle]: https://wiki.ubuntu.com/Releases

Raadpleeg de volgende artikelen voor installatie-instructies:

- [Windows 10 op arm](installing-powershell-core-on-windows.md#installing-the-zip-package)
- [Windows 10 IoT Enterprise](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-enterprise)
- [Windows 10 IoT Core](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-core)
- [Raspbian](installing-powershell-core-on-linux.md#raspbian)
