---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Bijlage 1 compatibiliteit aliassen
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="appendix-1---compatibility-aliases"></a>Bijlage 1 - compatibiliteit aliassen
Windows PowerShell heeft verschillende overgang aliassen die gebruikers met UNIX- en Cmd bekend opdrachtnamen in Windows PowerShell gebruiken. De meest voorkomende aliassen worden weergegeven in de onderstaande tabel, samen met de Windows PowerShell-opdracht achter de alias en de standaard Windows PowerShell-alias als er een bestaat.

U vindt de Windows PowerShell-opdracht die elke alias verwijst naar van Windows PowerShell met de cmdlet Get-Alias. Typ bijvoorbeeld **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Opdracht CMD|UNIX-opdracht|PS-Opdracht|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**GCI**|
|**CLS**|**wissen**|**Schakel Host** (functie)|**CLS**|
|**DEL, wissen, rmdir**|**RM**|**Item verwijderen**|**k**|
|**kopiëren**|**CP**|**Copy-Item**|**CI**|
|**verplaatsen**|**MV**|**Item verplaatsen**|**MI**|
|**naam wijzigen**|**MV**|**Wijzig de naam-Item**|**rni**|
|**type**|**CAT**|**Get-inhoud**|**GC**|
|**cd**|**cd**|**Locatie instellen**|**SL**|
|**MD**|**mkdir**|**Nieuw Item**|**Ni**|
|**pushd**|**pushd**|**Push-locatie**|**pushd**|
|**popd**|**popd**|**Pop-locatie**|**popd**|

