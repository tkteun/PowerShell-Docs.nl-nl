---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030339"
---
# <a name="appendix-1---compatibility-aliases"></a>Bijlage 1 - Compatibiliteitsaliassen

Windows PowerShell heeft verschillende overgang aliassen die UNIX- en Cmd gebruikers bekende opdrachtnamen gebruiken in Windows PowerShell. De meest voorkomende aliassen worden weergegeven in de onderstaande tabel, samen met de Windows PowerShell-opdracht achter de alias en de standaard Windows PowerShell-alias als er een bestaat.

Hier vindt u de Windows PowerShell-opdracht die een alias verwijst naar uit in Windows PowerShell met de cmdlet Get-Alias. Typ bijvoorbeeld **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Opdracht CMD|UNIX-opdracht|PS-Opdracht|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**Wissen**|**Clear-Host** (functie)|**cls**|
|**DEL, wissen, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Item verplaatsen**|**mi**|
|**Wijzig de naam**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
