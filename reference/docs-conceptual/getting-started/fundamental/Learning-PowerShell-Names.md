---
ms.date: 08/24/2018
keywords: PowerShell-cmdlet
title: Meer informatie over PowerShell-namen
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 44c66488a20c38d8528c92d753f6b32dda5a2dcb
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353263"
---
# <a name="learning-powershell-names"></a>Meer informatie over PowerShell-namen

Meer informatie over de namen van opdrachten en parameters vereist een aanzienlijke tijd-investering met de meeste opdrachtregelinterfaces. Het probleem is dat er enkele patronen zijn. Te onthouden is alleen manier om te leren van de opdrachten en parameters die u wilt een regelmatig gebruikt.

Wanneer u met een nieuwe opdracht of een parameter werkt, u niet altijd gebruiken wat u al kent. U hebt om erachter te komen van een nieuwe naam. Traditioneel opdrachtregelinterfaces beginnen met een kleine set hulpprogramma's en laten groeien met incrementele toevoegingen. Het is gemakkelijk om te zien waarom er geen standaard-structuur is.
Dit lijkt het logisch is voor de namen van opdrachten na elke opdracht een afzonderlijk hulpprogramma wordt. PowerShell is een betere manier voor het afhandelen van namen van opdrachten.

## <a name="learning-command-names-in-traditional-shells"></a>Meer informatie over opdrachtnamen in traditionele shells

De meeste opdrachten zijn gemaakt voor de elementen van het besturingssysteem of toepassingen, zoals services of processen beheren. De opdrachten hebben namen die kunnen of kunnen past niet in een serie. Bijvoorbeeld, op Windows-systemen, kunt u de `net start` en `net stop` opdrachten starten en stoppen van een service. **SC.exe** is een ander hulpprogramma voor service-beheer voor Windows. Deze naam past niet in het naamgevingspatroon voor de **net.exe** opdrachten-service. Windows heeft voor het beheer van bedrijfsprocessen, de **tasklist.exe** opdracht lijst processen en de **taskkill.exe** opdracht voor het beëindigen van processen.

Ook hebben deze opdrachten onregelmatige parameter specificaties. U kunt geen gebruiken de `net start` opdracht voor het starten van een service op een externe computer. De **sc.exe** opdracht kan een service starten op een externe computer. Maar als de externe computer, moet u de naam met een dubbele backslash voorafgaan. Als u wilt de spooler-service op een externe computer met de naam DC01 start, typt u `sc.exe \\DC01 start spooler`.
Aan de lijst met taken die worden uitgevoerd op DC01, gebruikt u de **/S** parameter en de naam van de computer zonder backslash-tekens. Voorbeeld: `tasklist /S DC01`.

> [!NOTE]
> Voorafgaand aan PowerShell v6, `sc` is een alias voor de `Set-Content` cmdlet. Om uit te voeren de **sc.exe** opdracht, moet u de bestandsextensie opnemen.

Services en -processen zijn voorbeelden van beheerbare elementen op een computer die goed gedefinieerde levenscyclus hebben. U kan starten of stoppen van services en -processen of een lijst van alle actieve services of processen. Hoewel er belangrijke technische verschillen daartussen zijn, zijn welke acties die u op services en -processen uitvoeren conceptueel gezien hetzelfde. Bovendien, de opties die we voor het aanpassen van een actie door de parameters op te geven mogelijk qua ontwerp vergelijkbaar ook.

PowerShell misbruik maakt van deze overeenkomsten om het aantal afzonderlijke namen die u moet weten om te begrijpen en gebruiken van cmdlets te verminderen.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlets werkwoord-zelfstandig naamwoord namen gebruiken om te beperken van de opdracht te onthouden

PowerShell maakt gebruik van een systeem voor de naamgeving 'werkwoord-zelfstandig naamwoord'. De cmdletnaam van elke bestaat van een standard bewerking afgebroken met een specifieke zelfstandig naamwoord. PowerShell-werkwoorden zijn niet altijd Engels termen, maar ze specifieke acties in PowerShell express. Zelfstandige naamwoorden zijn erg veel lijkt op zelfstandige naamwoorden in elke taal. Ze beschrijven bepaalde soorten objecten die belangrijk in Systeembeheer zijn. Het is gemakkelijk om te laten zien hoe deze namen tweedelige Vereenvoudig learning door te kijken naar enkele voorbeelden.

PowerShell is een aanbevolen set van standaardbewerkingen. Zelfstandige naamwoorden zijn minder beperkt, maar altijd wordt beschreven wat de term reageert. PowerShell heeft opdrachten zoals `Get-Process`, `Stop-Process`, `Get-Service`, en `Stop-Service`.

Voor dit voorbeeld van twee zelfstandige naamwoorden en werkwoorden vereenvoudigen consistentie niet weten dat veel eenvoudiger. Breid uit die lijst op een gestandaardiseerde verzameling 10 woorden en 10 woorden. Nu hoeft u slechts 20 woorden om te begrijpen.
Maar deze woorden kunnen worden gecombineerd tot 100 namen van afzonderlijke opdrachten formulier.

Het is gemakkelijk te begrijpen wat een PowerShell-opdracht door te lezen van de naam doet. De opdracht voor het afsluiten van een computer is `Stop-Computer`. De opdracht om een lijst van alle computers in een netwerk is `Get-Computer`. De opdracht voor het ophalen van de systeemdatum is `Get-Date`.

U kunt alle opdrachten die een bepaalde bewerking met bevatten een lijst de **term** parameter voor `Get-Command`. Bijvoorbeeld, om te zien van alle cmdlets die gebruikmaken van de term `Get`, type:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Gebruik de **zelfstandig naamwoord** parameter om te zien van een reeks opdrachten die invloed hebben op hetzelfde type object. Bijvoorbeeld, voer de volgende opdracht om te zien van de opdrachten die beschikbaar zijn voor het beheren van services:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Cmdlets standaard parameters gebruiken

Zoals eerder opgemerkt, hebt geen opdrachten die worden gebruikt in traditionele opdrachtregelinterfaces altijd consistent parameternamen. Parameters zijn vaak één teken of afgekort woorden die eenvoudig te typen, maar worden niet door nieuwe gebruikers gemakkelijk te begrijpen.

In tegenstelling tot de meeste andere traditionele opdrachtregelinterfaces PowerShell verwerkt parameters rechtstreeks en deze direct toegang tot de parameters en richtlijnen voor ontwikkelaars om te standaardiseren parameternamen wordt gebruikt. In deze richtlijnen worden gebruikers aangemoedigd maar is geen garantie dat elke cmdlet aan de norm voldoet.

PowerShell standaardiseert ook de parameter-scheidingsteken. Namen van parameters hebben altijd een '-' aan hen voorafgegaan door een PowerShell-opdracht. Houd rekening met het volgende voorbeeld:

```powershell
Get-Command -Name Clear-Host
```

De naam van de parameter is **naam**, maar deze wordt getypt als `-Name` wanneer op de opdrachtregel gebruikt als parameter.

Hier volgen enkele van de algemene kenmerken van de standaard parameternamen en het gebruik.

### <a name="the-help-parameter-"></a>De Help-parameter (?)

Wanneer u opgeeft de `-Help` of `-?` parameter in een PowerShell-cmdlet geeft de help voor de cmdlet weer. De cmdlet wordt niet uitgevoerd.

### <a name="common-parameters"></a>Algemene parameters

PowerShell heeft diverse *algemene parameters*. Deze parameters worden bepaald door de PowerShell-engine. Algemene parameters gedrag altijd hetzelfde. De algemene parameters zijn **WhatIf**, **bevestigen**, **uitgebreid**, **Debug**, **waarschuwen**, **ErrorAction**, **ErrorVariable**, **OutVariable**, en **OutBuffer**.

### <a name="recommended-parameter-names"></a>Aanbevolen parameternamen

De PowerShell core-cmdlets gebruiken standaard namen voor gelijksoortige parameters. Het gebruik van deze standaard namen niet wordt afgedwongen, maar er expliciete richtlijnen om aan te moedigen standaardisatie is.

Bijvoorbeeld, de naam van de aanbevolen voor een parameter die naar een computer verwijst is **ComputerName**, in plaats van de Server, Host, systeem, knooppunt of enkele andere algemene alternatief. De namen van andere belangrijke aanbevolen taakparameters zijn **Force**, **uitsluiten**, **opnemen**, **PassThru**, **pad**, en **CaseSensitive**.