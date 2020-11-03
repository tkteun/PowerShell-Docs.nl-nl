---
description: Hierin worden eenvoudiger, effectievere manieren voor het uitvoeren van script filters voor verzamelingen van objecten beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: d2e603b4d2092d4ba4ed9c1d7253991cc34ddca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252217"
---
# <a name="about_simplified_syntax"></a>about_Simplified_Syntax

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden eenvoudiger, effectievere manieren voor het uitvoeren van script filters voor verzamelingen van objecten beschreven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Dankzij de vereenvoudigde syntaxis, geïntroduceerd in Windows Power Shell 3,0, kunt u bepaalde filter opdrachten maken zonder gebruik te maken van script blokken. De vereenvoudigde syntaxis lijkt sterk op natuurlijke taal en is vooral nuttig voor verzamelingen van objecten die in opdrachten worden weer gegeven `Where-Object` en `ForEach-Object` de bijbehorende aliassen `where` en `foreach` .

U kunt een methode gebruiken voor de leden van een verzameling (meestal een matrix) zonder te verwijzen naar de automatische variabele `$_` in een-script blok.

Houd rekening met de volgende twee aanroepen:

### <a name="standard-syntax"></a>Standaard syntaxis

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a>Vereenvoudigde syntaxis

Onder de vereenvoudigde syntaxis worden vergelijkings operatoren die werken aan leden van objecten in een verzameling beschouwd als para meters. U kunt een methode aanroepen voor objecten in een verzameling zonder te verwijzen naar de automatische variabele `$_` in een-script blok.
Vergelijk de volgende twee aanroepen met die van het vorige voor beeld:
```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

Hoewel beide syntaxis werken, retourneert de vereenvoudigde syntaxis resultaten zonder te verwijzen naar de automatische variabele `$_` in een-script blok.
De naam van de methode `GetKeyAlgorithm` wordt behandeld als een para meter van `ForEach-Object` .
De tweede opdracht retourneert dezelfde resultaten, maar zonder fouten, omdat de vereenvoudigde syntaxis niet probeert resultaten te retour neren voor items waarvoor het opgegeven argument niet is toegepast.

In dit voor beeld `Process` wordt de eigenschap `Description` door gegeven als para meter voor de lidnaam aan de `ForEach-Object` opdracht. De resultaten zijn beschrijvingen van actieve processen.

```powershell
Get-Process | foreach Description
```

In dit voor beeld wordt de- `DirectoryInfo` methode `GetFiles` door gegeven als de para meter voor de lidnaam van de `ForEach-Object` opdracht.  
De methode wordt aangeroepen met de zoek patroon parameter `.*` .  
De resultaten zijn `FileInfo` records voor alle verborgen UNIX-bestanden in de basis mappen van gebruikers. 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a>ZIE OOK

- [about_Comparison_Operators](about_Comparison_Operators.md)
- [about_Foreach](about_Foreach.md)
- [Where-object](xref:Microsoft.PowerShell.Core.Where-Object)
- [Foreach-object](xref:Microsoft.PowerShell.Core.ForEach-Object)
