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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="1ac1e-104">Delen van objecten selecteren (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="1ac1e-104">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="1ac1e-105">U kunt de `Select-Object` cmdlet gebruiken om nieuwe aangepaste Power shell-objecten te maken die eigenschappen bevatten die zijn geselecteerd in de objecten die u gebruikt om ze te maken.</span><span class="sxs-lookup"><span data-stu-id="1ac1e-105">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="1ac1e-106">Typ de volgende opdracht om een nieuw object te maken dat alleen de **naam** en de eigenschappen van de **beschik bare ruimte** van de **Win32_LogicalDisk** WMI-klasse bevat:</span><span class="sxs-lookup"><span data-stu-id="1ac1e-106">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="1ac1e-107">Met `Select-Object` kunt u berekende eigenschappen maken.</span><span class="sxs-lookup"><span data-stu-id="1ac1e-107">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="1ac1e-108">U kunt dus **vrije ruimte** in gigabytes in plaats van bytes weer geven.</span><span class="sxs-lookup"><span data-stu-id="1ac1e-108">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
