---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086303"
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