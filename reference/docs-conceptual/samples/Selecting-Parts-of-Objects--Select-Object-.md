---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Delen van objecten selecteren object selecteren
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737165"
---
# <a name="selecting-parts-of-objects-select-object"></a>Delen van objecten selecteren (Select-Object)

U kunt de `Select-Object` cmdlet gebruiken om nieuwe aangepaste Power shell-objecten te maken die eigenschappen bevatten die zijn geselecteerd in de objecten die u gebruikt om ze te maken. Typ de volgende opdracht om een nieuw object te maken dat alleen de **naam** en de eigenschappen van de **beschik bare ruimte** van de **Win32_LogicalDisk** WMI-klasse bevat:

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

Met `Select-Object` kunt u berekende eigenschappen maken. U kunt dus **vrije ruimte** in gigabytes in plaats van bytes weer geven.

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
