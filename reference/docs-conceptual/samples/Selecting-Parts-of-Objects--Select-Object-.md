---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Delen van objecten selecteren object selecteren
description: U kunt de `Select-Object` cmdlet gebruiken om nieuwe aangepaste Power shell-objecten te maken die eigenschappen bevatten die zijn geselecteerd uit de objecten op de pijp lijn.
ms.openlocfilehash: 92635ac54ea1469739bcb228c5e9a0a8dbfc648b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501028"
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
