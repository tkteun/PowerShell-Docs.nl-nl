---
description: Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: b5f13fdbfbc24e19e5ad0b1cd6ecc1b99f68914f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705781"
---
# <a name="about-wildcards"></a>Over joker tekens

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Joker tekens vertegenwoordigen een of meer tekens. U kunt ze gebruiken om woord patronen te maken in opdrachten. Als u bijvoorbeeld alle bestanden in de `C:\Techdocs` map met een `.ppt` bestands extensie wilt ophalen, typt u:

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

In dit geval `*` vertegenwoordigt het Joker teken sterretje () alle tekens die voor de bestandsnaam extensie worden weer gegeven `.ppt` .

Power shell ondersteunt de volgende joker tekens:

|Vervanging|Beschrijving               |Voorbeeld |Match        |Geen overeenkomst|
|--------|--------------------------|--------|-------------|--------|
|\*      |Nul of meer tekens | één\*  | aA, AG, Apple | bananen |
|?       |Komt overeen met één teken op die positie | ? n | een, in, op | uitgevoerd |
|\[ \]   |Komt overeen met een reeks tekens | \[a-l \] ook | Book, Cook, zoeken | spoed |
|\[ \]   |Overeenkomen met specifieke tekens | \[BC \] ook | Book, Cook | accolade |

U kunt meerdere joker tekens in hetzelfde woord patroon toevoegen. Als u bijvoorbeeld tekst bestanden zoekt met namen die beginnen met de letters **a** t/m **l**, typt u:

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

Veel cmdlets accepteren joker tekens in parameter waarden. In het Help-onderwerp voor elke cmdlet wordt beschreven welke para meters joker tekens accepteren. Voor para meters die joker tekens accepteren, is het gebruik niet hoofdletter gevoelig.

U kunt joker tekens gebruiken in opdrachten en script blokken, zoals het maken van een Word-patroon dat eigenschaps waarden vertegenwoordigt. Met de volgende opdracht worden bijvoorbeeld services opgehaald waarin de waarde van de eigenschap **service** type **interactief** is opgenomen.

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

In het volgende voor beeld `If` bevat de instructie een voor waarde die joker tekens gebruikt om eigenschaps waarden te vinden. Als de **Beschrijving** van het herstel punt **Power shell** bevat, voegt de opdracht de waarde van de eigenschap **CreationTime** van het herstel punt toe aan een logboek bestand.

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a>ZIE OOK

[about_Language_Keywords](about_Language_Keywords.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)

