---
description: Hierin wordt beschreven hoe Power shell bepaalt welke opdracht moet worden uitgevoerd.
Locale: en-US
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: ee5d2dfcd8e7353950bec27a320bf3e0f76281c7
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195035"
---
# <a name="about-command-precedence"></a>Over opdracht prioriteit

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe Power shell bepaalt welke opdracht moet worden uitgevoerd.

## <a name="long-description"></a>Lange beschrijving

Opdracht prioriteit beschrijft hoe Power shell bepaalt welke opdracht moet worden uitgevoerd wanneer een sessie meer dan één opdracht met dezelfde naam bevat. Opdrachten in een sessie kunnen worden verborgen of vervangen door opdrachten met dezelfde naam. In dit artikel leest u hoe u verborgen opdrachten uitvoert en conflicten met opdracht namen voor komt.

## <a name="command-precedence"></a>Opdracht prioriteit

Wanneer een Power shell-sessie meer dan één opdracht met dezelfde naam bevat, bepaalt Power shell welke opdracht moet worden uitgevoerd met behulp van de volgende regels.

Als u het pad naar een opdracht opgeeft, voert Power shell de opdracht uit op de locatie die is opgegeven door het pad.

Met de volgende opdracht wordt bijvoorbeeld het FindDocs.ps1 script uitgevoerd in de map ' C: \\ TechDocs ':

```
C:\TechDocs\FindDocs.ps1
```

Als beveiligings functie voert Power shell geen uitvoer bare (systeem eigen) opdrachten uit, inclusief Power shell-scripts, tenzij de opdracht zich bevindt in een pad dat wordt vermeld in de omgevings variabele PATH `$env:path` of tenzij u het pad naar het script bestand opgeeft.

Als u een script wilt uitvoeren dat zich in de huidige map bevindt, geeft u het volledige pad op of typt u een punt `.\` om de huidige map weer te geven.

Als u bijvoorbeeld het FindDocs.ps1-bestand in de huidige map wilt uitvoeren, typt u:

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a>Joker tekens gebruiken in uitvoering

U kunt joker tekens gebruiken bij het uitvoeren van de opdracht. Het gebruik van joker tekens wordt ook wel *globbing* genoemd.

Power Shell voert een bestand uit met een Joker teken, voordat een letterlijke overeenkomst wordt gevonden.

Denk bijvoorbeeld aan een map met de volgende bestanden:

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

Beide script bestanden hebben dezelfde inhoud: `$MyInvocation.MyCommand.Path` .
Met deze opdracht wordt de naam van het script weer gegeven dat wordt aangeroepen.

Wanneer u uitvoert `[a1].ps1` , wordt het bestand `a.ps1` uitgevoerd, zelfs als het bestand `[a1].ps1` een letterlijke overeenkomst is.

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

We gaan nu het `a.ps1` bestand verwijderen en proberen het opnieuw uit te voeren.

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

U kunt in de uitvoer zien dat `[a1].ps1` deze keer wordt uitgevoerd omdat de letterlijke overeenkomst het enige bestand is dat overeenkomt met het Joker teken.

Zie [about_Wildcards](about_Wildcards.md)voor meer informatie over het gebruik van joker tekens in Power shell.

> [!NOTE]
> Als u de zoek opdracht wilt beperken tot een relatief pad, moet u een voor voegsel van de script naam met het `.\` pad opgeven. Hiermee beperkt u de Zoek opdrachten naar bestanden in het relatieve pad. Zonder dit voor voegsel kan de andere Power shell-syntaxis conflicteren en zijn er weinig garanties dat het bestand wordt gevonden.

Als u geen pad opgeeft, maakt Power shell gebruik van de volgende volg orde van prioriteit wanneer opdrachten worden uitgevoerd voor alle items die in de huidige sessie worden geladen:

  1. Alias
  2. Functie
  3. Cmdlet
  4. Externe uitvoer bare bestanden (Program ma's en niet-Power shell-scripts)

Als u ' Help ' typt, zoekt Power shell eerst naar een alias met de naam `help` , vervolgens een functie `Help` met de naam en ten slotte een cmdlet met de naam `Help` . Het eerste item dat wordt gevonden, wordt uitgevoerd `help` .

Als uw sessie bijvoorbeeld een cmdlet bevat en een functie met `Get-Map` de naam, wanneer u typt `Get-Map` , voert Power shell de functie uit.

> [!NOTE]
> Dit is alleen van toepassing op geladen opdrachten. Als er een `build` uitvoerbaar bestand en een alias `build` voor een functie met de naam van `Invoke-Build` binnen een module die niet in de huidige sessie is geladen, voert Power shell het `build` uitvoer bare bestand uit. Modules worden niet automatisch geladen als het externe uitvoer bare bestand in dit geval wordt gevonden. Het is alleen wanneer er geen extern uitvoerbaar bestand wordt gevonden dat een alias, functie of cmdlet met de opgegeven naam wordt aangeroepen, waardoor automatisch laden van de module wordt geactiveerd.

Wanneer de sessie items van hetzelfde type bevat die dezelfde naam hebben, voert Power shell het nieuwere item uit.

Als u bijvoorbeeld een andere `Get-Date` cmdlet uit een module importeert terwijl u typt `Get-Date` , voert Power shell de geïmporteerde versie uit via de systeem eigen.

## <a name="hidden-and-replaced-items"></a>Verborgen en vervangen items

Als gevolg van deze regels kunnen items worden vervangen of verborgen door items met dezelfde naam.

Items zijn "verborgen" of "schaduw" als u nog steeds toegang hebt tot het oorspronkelijke item, bijvoorbeeld door de naam van het item te kwalificeren met een module of module naam.

Als u bijvoorbeeld een functie importeert die dezelfde naam heeft als een cmdlet in de sessie, wordt de cmdlet verborgen (maar niet vervangen) omdat deze is geïmporteerd uit een module of module.

Items zijn "vervangen" of "overschreven" als u het oorspronkelijke item niet meer kunt openen.

Als u bijvoorbeeld een variabele importeert die dezelfde naam heeft als een variabele in de sessie, wordt de oorspronkelijke variabele vervangen en is deze niet meer toegankelijk.
U kunt een variabele met een module naam niet kwalificeren.

Als u een functie typt op de opdracht regel en vervolgens een functie importeert die dezelfde naam heeft, wordt de oorspronkelijke functie vervangen en is deze niet meer toegankelijk.

### <a name="finding-hidden-commands"></a>Verborgen opdrachten zoeken

Met de para meter **all** van de cmdlet [Get-opdracht](xref:Microsoft.PowerShell.Core.Get-Command) worden alle opdrachten met de opgegeven naam opgehaald, zelfs als ze worden verborgen of vervangen. Vanaf Power Shell 3,0 worden standaard `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.

In de volgende voor beelden bevat de sessie een `Get-Date` functie en een [Get-date-](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.

De volgende opdracht wordt de `Get-Date` opdracht die wordt uitgevoerd wanneer u typt `Get-Date` .

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

De volgende opdracht gebruikt de **alle** para meters om alle opdrachten op te halen `Get-Date` .

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a>Verborgen opdrachten uitvoeren

U kunt bepaalde opdrachten uitvoeren door item eigenschappen op te geven die de opdracht onderscheiden van andere opdrachten die dezelfde naam kunnen hebben. U kunt deze methode gebruiken om elke opdracht uit te voeren, maar dit is vooral handig voor het uitvoeren van verborgen opdrachten.

#### <a name="qualified-names"></a>Gekwalificeerde namen

Met de module-gekwalificeerde naam van een cmdlet kunt u opdrachten uitvoeren die zijn verborgen door een item met dezelfde naam. U kunt de cmdlet bijvoorbeeld uitvoeren `Get-Date` door deze te kwalificeren met de module naam **micro soft. Power shell. Utility**.

Gebruik deze voorkeurs methode voor het schrijven van scripts die u wilt distribueren. U kunt niet voors pellen welke opdrachten mogelijk aanwezig zijn in de sessie waarin het script wordt uitgevoerd.

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

Als u een `New-Map` opdracht wilt uitvoeren die is toegevoegd door de `MapFunctions` module, gebruikt u de module-gekwalificeerde naam:

```powershell
MapFunctions\New-Map
```

Gebruik de eigenschap PropertyName van opdrachten om **de module te** vinden van waaruit een opdracht is geïmporteerd.

```
(Get-Command <command-name>).ModuleName
```

Als u bijvoorbeeld de bron van de cmdlet wilt zoeken `Get-Date` , typt u:

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> U kunt geen variabelen of aliassen kwalificeren.

#### <a name="call-operator"></a>Aanroep operator

U kunt ook de `Call` operator gebruiken `&` om verborgen opdrachten uit te voeren door deze te combi neren met een aanroep naar [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) (de alias is ' dir ') `Get-Command` of [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).

De aanroep operator voert teken reeksen en script blokken uit in een onderliggend bereik. Zie [about_Operators](about_Operators.md)voor meer informatie.

Als u bijvoorbeeld een functie hebt `Map` met de naam die is verborgen met een alias met `Map` de naam, gebruikt u de volgende opdracht om de functie uit te voeren.

```powershell
&(Get-Command -Name Map -CommandType Function)
```

of

```powershell
&(dir Function:\map)
```

U kunt ook uw verborgen opdracht opslaan in een variabele, zodat u deze eenvoudiger kunt uitvoeren.

Met de volgende opdracht wordt bijvoorbeeld de `Map` functie in de `$myMap` variabele opgeslagen en vervolgens de `Call` operator gebruikt om deze uit te voeren.

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a>Vervangen items

Er is een vervangend item die u niet meer kunt openen. U kunt items vervangen door items met dezelfde naam te importeren uit een module of module.

Als u bijvoorbeeld een `Get-Map` functie in uw sessie typt en u een functie importeert `Get-Map` , wordt de oorspronkelijke functie vervangen. U kunt deze niet ophalen in de huidige sessie.

Variabelen en aliassen kunnen niet worden verborgen omdat u geen aanroep operator of gekwalificeerde naam kunt gebruiken om ze uit te voeren. Wanneer u variabelen en aliassen uit een module of module importeert, vervangen deze variabelen in de sessie met dezelfde naam.

### <a name="avoiding-name-conflicts"></a>Naam conflicten vermijden

De beste manier om conflicten met opdracht namen te beheren is om te voor komen dat. Gebruik een unieke naam wanneer u uw opdrachten een naam geef. U kunt bijvoorbeeld uw initialen of bedrijfs naam acroniem toevoegen aan de uitvoeringen in de opdrachten.

Wanneer u vanuit een Power shell-module of vanuit een andere sessie opdrachten in uw sessie importeert, gebruikt u ook de `Prefix` para meter van de [import-module](xref:Microsoft.PowerShell.Core.Import-Module) of

De cmdlet [import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession) om een voor voegsel toe te voegen aan de naam woorden in de namen van opdrachten.

Met de volgende opdracht wordt bijvoorbeeld een conflict voor komen met de `Get-Date` `Set-Date` cmdlets en die bij Power shell worden geleverd bij het importeren van de `DateFunctions` module.

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

Zie en hieronder voor meer `Import-Module` informatie `Import-PSSession` .

## <a name="see-also"></a>Zie ook

- [about_Path_Syntax](about_Path_Syntax.md)
- [about_Aliases](about_Aliases.md)
- [about_Functions](about_Functions.md)
- [Alias provider](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [Functie-provider](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Import-module](xref:Microsoft.PowerShell.Core.Import-Module)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)
