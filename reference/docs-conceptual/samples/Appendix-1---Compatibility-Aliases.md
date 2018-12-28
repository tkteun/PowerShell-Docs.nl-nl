---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404598"
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
|**dir**|**Ls**|**Get-ChildItem**|**GCI**|
|**CLS**|**Wissen**|**Clear-Host** (functie)|**CLS**|
|**DEL, wissen, rmdir**|**RM**|**Item verwijderen**|**gereserveerde instanties**|
|**Kopiëren**|**CP**|**Copy-Item**|**CI**|
|**verplaatsen**|**MV**|**Item verplaatsen**|**MI**|
|**Wijzig de naam**|**MV**|**Rename-Item**|**rni**|
|**Type**|**CAT**|**Get-inhoud**|**GC-exemplaar**|
|**cd**|**cd**|**Locatie instellen**|**SL**|
|**MD**|**mkdir**|**Nieuw Item**|**Ni**|
|**pushd**|**pushd**|**Push-locatie**|**pushd**|
|**popd**|**popd**|**Pop-locatie**|**popd**|