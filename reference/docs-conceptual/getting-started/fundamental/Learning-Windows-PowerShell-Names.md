---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Meer informatie over Windows PowerShell-namen
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 381aa619a41ccacb2ff3a4cdbc2b75b7f04282d1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953470"
---
# <a name="learning-windows-powershell-names"></a>Meer informatie over Windows PowerShell-namen
Namen van opdrachten en parameters van de Learning is een aanzienlijke tijd investering met de meeste opdrachtregelinterfaces. Het probleem is dat er heel weinig patronen, dus de enige manier om te leren door bewerkingsopdrachten van elke opdracht en elke parameter die u wilt gebruiken op regelmatige basis.

Wanneer u met een nieuwe opdracht of een parameter werkt, kan niet in het algemeen u wat u al weet; u hebt om erachter te komen van een nieuwe naam. Als u hoe interfaces Breid uit van een kleine set van hulpprogramma's met incrementele toevoegingen aan functionaliteit kijken, is het eenvoudig om te zien waarom de structuur is niet-standaard. Met de namen van opdrachten in het bijzonder klinkt dit logisch omdat elke opdracht een afzonderlijk hulpprogramma is, maar er een betere manier is voor het verwerken van opdrachten.

De meeste opdrachten zijn voor het beheren van de elementen van het besturingssysteem of toepassingen, zoals services of processen gebouwd. De opdrachten hebben een aantal namen die al dan niet in een serie kunnen passen. Bijvoorbeeld, op Windows-systemen, kunt u de **net start** en **net stop** opdrachten starten en stoppen van een service. Er is een andere meer algemene service beheer hulpprogramma voor Windows met een andere naam **sc**, die past niet in het naamgevingspatroon voor de **net** service-opdrachten. Voor beheer, Windows heeft de **tasklist** opdracht lijst processen en de **taskkill** opdracht afsluiten van processen.

Opdrachten die parameters hebben onregelmatige parameter specificaties. U kunt geen gebruiken de **net start** opdracht een service te starten op een externe computer. De **sc** opdracht een service wordt gestart op een externe computer, maar als u de externe computer, moet u de naam met een dubbele backslash voorafgaan. Bijvoorbeeld, als u wilt de spooler-service starten op een externe computer met de naam DC01, typt u **sc \\ \\DC01 start spooler**. Aan de lijst met taken uitgevoerd op DC01, die u wilt gebruiken, de **/S** parameter (voor 'systeem') en geef de naam DC01 zonder backslashes als volgt: **tasklist /S DC01**.

Er zijn belangrijke technische verschillen tussen een service en een proces, zijn ze beide voorbeelden van beheerbare elementen op een computer die een goed gedefinieerde levenscyclus hebben. U kunt starten of stoppen van een service of het proces of een lijst met alle actieve services of processen. Met andere woorden, hoewel een service en een proces verschillende dingen zijn, zijn de acties die we op een service of een proces uitvoeren vaak conceptueel gezien hetzelfde. Bovendien maken we een actie aanpassen door te geven van parameters keuzes mogelijk gelijksoortige ook.

Windows PowerShell misbruik maakt van deze overeenkomsten om te beperken het aantal unieke namen die u moet weten om te begrijpen en cmdlets gebruiken.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Namen van de cmdlets gebruiken werkwoord-zelfstandig naamwoord te verminderen van de opdracht te onthouden
Windows PowerShell maakt gebruik van een systeem voor 'werkwoord-zelfstandig naamwoord' naamgeving, waarbij de naam van elke cmdlet bestaat uit een standaard term afgebroken met een specifieke zelfstandig naamwoord. Windows PowerShell-werkwoorden zijn niet altijd Engelse termen, maar ze express specifieke acties in Windows PowerShell. De volgende zelfstandige naamwoorden lijkt veel op woorden in een andere taal, ze beschrijven bepaalde soorten objecten die belangrijk in Systeembeheer zijn. Het is gemakkelijk om te demonstreren hoe deze namen tweedelige learning inspanning verminderen door te kijken enkele voorbeelden van termen en woorden.

De volgende zelfstandige naamwoorden minder beperkt zijn, maar ze beschrijven moeten altijd een opdracht fungeert bij. Windows PowerShell bevat opdrachten zoals **Get-Process**, **Stop-Process**, **Get-Service**, en **Service stoppen**.

In het geval van twee zelfstandige naamwoorden en twee termen vereenvoudigen consistentie niet deel te leren. Echter, als u een standaardset 10 termen en 10 woorden bekijkt, vervolgens hebt u slechts 20 woorden om te begrijpen, maar deze woorden kunnen worden gebruikt om het formulier 100 afzonderlijke opdrachtnamen.

Vaak u een opdracht wordt door te lezen van de naam ervan kan herkennen, en is meestal duidelijk welke naam moet worden gebruikt voor een nieuwe opdracht. Bijvoorbeeld, een afsluitopdracht computer mogelijk **Stop-Computer**. Een opdracht met een lijst met alle computers in een netwerk mogelijk **Get-Computer**. De opdracht die de systeemdatum krijgt is **Get-Date**.

U kunt alle opdrachten die een bepaalde bewerking met bevatten lijst de **-term** parameter voor **Get-Command** (bespreken We **Get-Command** beschreven in de volgende sectie). Bijvoorbeeld, om te zien alle cmdlets die gebruikmaken van de term **ophalen**, type:

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

De **-zelfstandig naamwoord** parameter zijn nog meer nuttig omdat deze kunt u een reeks opdrachten die invloed hebben op hetzelfde type object. Bijvoorbeeld als u wilt zien vindt welke opdrachten u voor het beheren van services, type volgende opdracht:

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

Een opdracht is niet noodzakelijkerwijs een cmdlet, omdat er een schematische naam werkwoord-zelfstandig naamwoord. Een voorbeeld van een systeemeigen Windows PowerShell-opdracht is niet een cmdlet, maar heeft een naam werkwoord-zelfstandig naamwoord is de opdracht voor het wissen van een consolevenster, Clear-Host. De opdracht Clear-Host is daadwerkelijk een interne functie, zoals u zien kunt als u tegen Get-opdracht uitvoeren:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>Standaard Parameters van de cmdlets gebruiken
Zoals eerder opgemerkt, opdrachten gebruikt in traditionele opdrachtregelinterfaces in het algemeen geen consistente parameternamen. Soms parameters geen namen in alle. Wanneer ze doen, ze zijn vaak één teken of afgekort woorden die niet eenvoudig worden begrepen door nieuwe gebruikers, maar kunnen snel worden getypt.

In tegenstelling tot de meeste andere traditionele opdrachtregelinterfaces Windows PowerShell parameters rechtstreeks verwerkt en deze direct toegang tot de parameters die samen met de handleiding voor ontwikkelaars te standaardiseren parameternamen wordt gebruikt. Hoewel dit wordt niet gegarandeerd dat elke cmdlet altijd wordt voldoen aan de normen, ondersteunt deze het.

> [!NOTE]
> Namen van parameters hebben altijd een '-' voorafgegaan toe wanneer u deze, om toe te staan van Windows PowerShell duidelijk om ze te identificeren als parameters. In de **Get-Command - naam wissen-Host** bijvoorbeeld de naam van de parameter is **naam**, maar het is ingevoerd als -**naam**.

Hier zijn enkele van de algemene kenmerken van de standaard parameternamen en gebruik.

#### <a name="the-help-parameter-"></a>De Help-Parameter (?)
Wanneer u opgeeft de **-?** parameter voor een cmdlet, de cmdlet is niet uitgevoerd. Hiermee wordt in plaats daarvan Windows PowerShell help voor de cmdlet weergegeven.

#### <a name="common-parameters"></a>Algemene Parameters
Windows PowerShell heeft verschillende parameters, ook wel *algemene parameters*. Omdat deze parameters worden bepaald door de Windows PowerShell-engine, wanneer ze worden geïmplementeerd door een cmdlet, wordt ze altijd dezelfde manier werken. De algemene parameters zijn **WhatIf**, **bevestigen**, **uitgebreid**, **Debug**, **waarschuwen**, **ErrorAction**, **ErrorVariable**, **OutVariable**, en **OutBuffer**.

#### <a name="suggested-parameters"></a>Voorgestelde Parameters
De Windows PowerShell-kern-cmdlets gebruiken standaard namen voor de overeenkomstige parameters. Hoewel het gebruik van de namen van parameters niet wordt afgedwongen, is het expliciete richtlijnen voor het gebruik ter bevordering van normalisatie.

Bijvoorbeeld de richtlijnen beveelt een parameter naam verwijst naar een computer met de naam als **ComputerName**, in plaats van de Server, Host, systeem, knooppunt of andere veelvoorkomende alternatieve woorden. Namen zijn onder de belangrijke voorgestelde parameter **Force**, **uitsluiten**, **opnemen**, **PassThru**, **pad**, en **CaseSensitive**.