---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Delen van objecten selecteren object selecteren
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737165"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="d9915-103">Delen van objecten selecteren (select-object)</span><span class="sxs-lookup"><span data-stu-id="d9915-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="d9915-104">U kunt de cmdlet `Select-Object` gebruiken om nieuwe aangepaste Power shell-objecten te maken die eigenschappen bevatten die zijn geselecteerd in de objecten die u gebruikt om ze te maken.</span><span class="sxs-lookup"><span data-stu-id="d9915-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="d9915-105">Typ de volgende opdracht om een nieuw object te maken dat alleen de **naam** en de eigenschappen van de **beschik bare ruimte** van de **Win32_LogicalDisk** WMI-klasse bevat:</span><span class="sxs-lookup"><span data-stu-id="d9915-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="d9915-106">Met `Select-Object` kunt u berekende eigenschappen maken.</span><span class="sxs-lookup"><span data-stu-id="d9915-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="d9915-107">U kunt dus **vrije ruimte** in gigabytes in plaats van bytes weer geven.</span><span class="sxs-lookup"><span data-stu-id="d9915-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
