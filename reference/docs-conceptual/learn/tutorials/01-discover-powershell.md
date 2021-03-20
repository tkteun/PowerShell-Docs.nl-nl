---
title: Power shell detecteren
ms.date: 03/12/2021
ms.custom: chnoring
ms.reviewer: sewhee
description: Meer informatie over Power shell en enkele essentiële opdrachten die worden gebruikt om meer te weten te komen over Power shell.
ms.openlocfilehash: 34bbd465a918224c203e7243834e7fb3a3a6070c
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730017"
---
# <a name="discover-powershell"></a>Power shell detecteren

Power shell is een opdracht regel shell en een script taal in één. Power shell is gestart op Windows. Het is bedoeld om u te helpen bij het automatiseren van taken voor beheer taken, maar is nu gegroeid naar meerdere platformen en kan worden gebruikt voor verschillende taken.

Het maken van een unieke Power shell is het accepteren en retour neren van .NET-objecten in plaats van tekst.
Dit betekent dat het eenvoudiger is om verschillende opdrachten in reeksen te verbinden in een _pijp lijn_.

> [!NOTE]
> Pijp lijnen worden gedetailleerd besproken in deze zelfstudie reeks.

Het kan ook voor komen dat u de resultaten enigszins moet _massage_ .

## <a name="what-can-powershell--be-used-for"></a>Waarvoor kan Power shell worden gebruikt?

Het gebruik van Power shell is toegenomen sinds de dagen waarop het alleen Windows is. Het wordt nog steeds gebruikt voor Windows-taak automatisering, maar u kunt deze gebruiken voor verschillende taken, zoals:

- **Cloud beheer**. Power shell kan worden gebruikt om cloud resources te beheren. U kunt bijvoorbeeld informatie over cloud resources ophalen en nieuwe resources bijwerken of implementeren.
- **CI/cd**. Het kan ook worden gebruikt als onderdeel van een continue integratie/doorlopende implementatie pijplijn.
- **Taken automatiseren voor Active Directory en Exchange**. U kunt dit gebruiken om bijna elke taak in Windows te automatiseren, zoals het maken van gebruikers in Active Directory en post vakken in Exchange.

Er zijn veel meer gebruiks gebieden, maar de bovenstaande lijst biedt u een hint die Power shell op een lange manier heeft geduurd.

## <a name="who-uses-powershell"></a>Wie gebruikt Power shell?

Power shell is zeer krachtig en veel mensen die in talrijke rollen werken, kunnen profiteren van het gebruik ervan. Traditioneel is Power shell gebruikt door de rol systeem beheerder, maar wordt dit nu gebruikt door mensen die zelf DevOps, Cloud-Ops en zelfs ontwikkel aars aanroepen.

## <a name="powershell-cmdlets"></a>PowerShell-cmdlets

Power shell wordt geleverd met honderden vooraf geïnstalleerde opdrachten. De Power shell-opdracht worden cmdlets genoemd. uitgesp roken als ' opdracht-Hiermee '.

De naam van elke cmdlet bestaat uit een ' verb-zelfstandig '-paar. bijvoorbeeld `Get-Process` . Deze naamgevings Conventie maakt het gemakkelijker om te begrijpen wat de cmdlet doet. U kunt de opdracht die u zoekt ook gemakkelijker vinden. Wanneer u op zoek bent naar een cmdlet die moet worden gebruikt, kunt u filteren op de term of het zelfstandig naam woord.

### <a name="using-cmdlets-to-explore-powershell"></a>Cmdlets gebruiken om Power shell te verkennen

Wanneer u Power shell voor het eerst ophaalt, kan dit intimideren lijken, omdat er zo veel te leren is.
Power shell is echter ontworpen om u te helpen een beetje per keer te leren, zoals u dat nodig hebt.

Power shell bevat cmdlets die u helpen bij het detecteren van Power shell. Met deze drie cmdlets kunt u ontdekken welke opdrachten beschikbaar zijn, wat ze doen en op welke typen ze worden uitgevoerd.

- `Get-Verb`. Als u deze opdracht uitvoert, wordt een lijst geretourneerd met de woorden die de meeste opdrachten naleven.
  Daarnaast wordt met het antwoord de werking van deze termen beschreven. Aangezien de meeste opdrachten deze naam volgen, worden er verwachtingen ingesteld voor wat een opdracht doet, waarmee u de juiste opdracht kunt selecteren, maar ook de naam van een opdracht moet u er een maken.
- `Get-Command`. Met deze opdracht wordt een lijst opgehaald met alle opdrachten die op uw computer zijn geïnstalleerd.
- `Get-Member`. Het werkt op objecten gebaseerd op uitvoer en kan detecteren welk object, eigenschappen en methoden beschikbaar zijn voor een opdracht.
- `Get-Help`. Als u deze opdracht aanroept met de naam van een opdracht als argument, wordt een Help-pagina weer gegeven met een beschrijving van de verschillende onderdelen van een opdracht.

Met deze opdrachten kunt u bijna alles ontdekken wat u nodig hebt om te weten te komen over Power shell.

### <a name="verb"></a>Verb

Term is een belang rijke concepten in Power shell. Het is een naamgevings standaard die de meeste cmdlets volgt. Het is ook een naamgevings standaard die u verwacht te volgen, wanneer u uw eigen opdrachten schrijft. Het idee is dat de _term_ aangeeft wat u probeert te doen, gegevens te lezen of te wijzigen. Power Shell heeft een gestandaardiseerde lijst met termen. Gebruik de cmdlet om een volledige lijst met alle mogelijke termen te verkrijgen `Get-Verb` :

```powershell
Get-Verb
```

De uitvoer van de uitvoering is een lange lijst met woorden. Wat er op de hoogte is van het antwoord, is dat er ook meer context wordt weer gegeven, wat een dergelijke term bedoeld is. Dit is de eerste rij van de uitvoer:

```output
Verb        AliasPrefix Group          Description
----        ----------- -----          -----------
Add         a           Common         Adds a resource to a container, or attaches an item to ano…
```

## <a name="find-commands-with-get-command"></a>Zoek opdrachten met Get-Command

De `Get-Command` cmdlet retourneert een lijst van alle beschik bare opdrachten die op uw systeem zijn geïnstalleerd.
Deze lijst wordt weer gegeven, maar is wel erg groot. Als u de Zoek opdrachten eenvoudiger wilt maken, kunt u de hoeveelheid gegevens die wordt weer gegeven, beperken. U kunt het antwoord filteren met behulp van para meters of met helper-cmdlets.

### <a name="filter-on-name"></a>Filteren op naam

U kunt de uitvoer van filteren `Get-Command` met behulp van verschillende para meters. Als u op deze manier filtert, wordt een query uitgevoerd op een specifieke eigenschap van de opdracht. Het idee is dat u opgeeft op welke eigenschap u wilt filteren en vervolgens een teken reeks opgeeft waarmee u wilt zoeken. Daarom krijgt u een vergelijking die er als volgt uitziet:

```powershell
Get-Command -Name '*Process'
```

Op dit moment probeert het filter precies te vergelijken met het gegeven teken reeks argument.
Als u meer flexibiliteit wilt, kunt u in de vergelijking gebruikmaken van een Joker teken `*` dat overeenkomt met het patroon. De volgende code zoekt naar alle opdrachten, waarvan de naam eindigt met het proces:

Hierboven, de para meter `-Name` die wordt gebruikt om te filteren. `-Name`U kunt ook filteren op `-ParameterName` en `-Type` , bijvoorbeeld.

### <a name="filtering-on-noun-and-verb"></a>Filteren op zelfstandig naam woord en werk woord

U hebt gezien hoe u kunt filteren op `-Name` en u kunt ook andere para meters filteren. Werk woord en zelfstandig naam woord kan ook worden gefilterd. Dergelijke filters hebben als doel een deel van de naam van een opdracht.

- **Filter op term**. Het gedeelte van de naam van een opdracht is het meest linkse deel. In de opdracht `Get-Process` is het deel van de bewerking `Get` . Als u wilt filteren op het deel van de werk woord, geeft u `-Verb` als volgt op als para meter:

   ```powershell
   Get-Command -Verb 'Get'
   ```

   Met de bovenstaande opdracht worden alle opdrachten weer geven waarvan het onderdeel deel uitmaakt `Get` .

- **Filteren op zelfstandig naam woord**. Het meest rechtse deel van een opdracht is het onderdeel van de zelfstandig naam woord. Waarbij de term moet liggen tussen de bewerkingen die worden geretourneerd door aanroepen `Get-Verb` , kan een zelfstandig naam woord zijn. In de opdracht `Get-Process` is het onderdeel van de zelfstandig naam woord `Process` . Als u wilt filteren op zelfstandig naam woord, geeft u `-Noun` als een para meter en een teken reeks argument op, bijvoorbeeld:

   ```powershell
   Get-Command -Noun U*
   ```

Alleen het gebruik van de term of het zelfstandige naam om te filteren op, kan nog steeds een groot resultaat opleveren. Om uw zoek opdracht te verfijnen, is het handig om de twee para meters te combi neren, zoals in het onderstaande voor beeld:

```powershell
Get-Command -Verb Get -Noun U*
```

Het resultaat van het bovenstaande ziet er als volgt uit:

```output
CommandType     Name                         Version    Source
-----------     ----                         -------    ------
Cmdlet          Get-UICulture                7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-Unique                   7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-Uptime                   7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-UsageAggregates          2.0.0      Az.Billing
```

Zo kunt u de uitvoer echt beperken door de term te weten en wat deze wordt genoemd.

### <a name="use-helper-cmdlets-to-filter-results"></a>Helper-cmdlets gebruiken om resultaten te filteren

Naast het gebruik van para meters om te filteren, kunt u ook opdrachten gebruiken om u te helpen met deze taak. Hier volgen enkele opdrachten die kunnen fungeren als filters:

- `Select-Object`. Het is een zeer veelzijdige opdracht waarmee u specifieke eigenschappen van een of meer objecten kunt ophalen. Daarnaast kunt u met behulp van de para meters het antwoord dat u terugkrijgt, beperken. Hier volgt een voor beeld van `Select-Object` dat wordt gebruikt om te vragen naar een beperkt aantal records:

   ```powershell
   Get-Command | Select-Object -First 3
   ```

   Het resultaat van de bovenstaande is de drie eerste opdrachten, geteld vanaf de bovenkant. Het resultaat ziet er als volgt uit:

   ```output
   CommandType     Name                                               Version    Source
   -----------     ----                                               -------    ------
   Alias           Add-AdlAnalyticsDataSource                         1.0.2      Az.DataLakeAnalytics
   Alias           Add-AdlAnalyticsFirewallRule                       1.0.2      Az.DataLakeAnalytics
   Alias           Add-AdlStoreFirewallRule                           1.3.0      Az.DataLakeStore
   ```

   Het is een goed idee om te kijken naar deze opdracht, omdat het veel meer  [documenten kan selecteren-object](/powershell/module/microsoft.powershell.utility/select-object)

- `Where-Object`. Het object where helpt u bij het selecteren van objecten uit een verzameling op basis van de waarden van eigenschappen. De opdracht heeft een expressie waarin u kunt zien welke kolom/s u wilt laten overeenkomen met welke waarden. Als u wilt zoeken naar alle proces objecten waarbij de `ProcessName` begint met `p` , kunt u het `Where-Object` volgende gebruiken:

  ```powershell
  Get-Process | Where-Object {$_.ProcessName -Like "p*"}
  ```

  Hierboven maakt de `Get-Process` cmdlet een verzameling proces objecten. Als u het antwoord wilt filteren, kunt u de opdracht door _sluizen_ `Where-Object` . Leidingen houdt in dat er twee of meer opdrachten zijn verbonden via een sluis `|` teken. Het idee is dat de uitvoer van de ene opdracht als de invoer voor de volgende opdracht fungeert, zoals gelezen van links naar rechts. De `Where-Object` gebruikt een expressie om te filteren. De expressie zelf maakt gebruik van de `-Like` operator en het teken reeks argument die een Joker teken expressie zijn.

## <a name="explore-objects-with-get-member"></a>Objecten verkennen met Get-Member

Wanneer u de gewenste cmdlet hebt gevonden, wilt u meer weten over wat deze produceert, de uitvoer. De uitvoer is om verschillende redenen interessant, zoals:

- **Zelfstandig**. U kunt slechts één cmdlet uitvoeren en de uitvoer weer geven in een rapport waarop u wilt sorteren. De vraag om u te vragen of de opdracht een uitvoer produceert die geschikt is voor u, of dat u deze moet wijzigen.
- **Bij gebruik in een pijp lijn**. Het is gebruikelijk in Power shell om meerdere opdrachten in een pijp lijn te verbinden, gegevens op te halen, te filteren en tot slot te transformeren. Als u wilt dat een opdracht in een pijp lijn past, moet u kijken welke invoer en uitvoer er worden geproduceerd. Het idee is dat de uitvoer van een opdracht wordt gebruikt als invoer van een andere opdracht.

`Get-Member`Met de cmdlet worden de eigenschappen en methoden van het resultaat weer gegeven. Daarnaast wordt ook het type van het object weer gegeven. Pipet de uitvoer die u wilt inspecteren `Get-Member` .

```powershell
Get-Process | Get-Member
```

Het resultaat geeft het geretourneerde type weer als `TypeName` en vervolgens alle eigenschappen en methoden van het object. Hier volgt een fragment van een dergelijk resultaat:

```output
TypeName: System.Diagnostics.Process

Name        MemberType     Definition
----        ----------     ----------
Handles     AliasProperty  Handles = Handlecount
Name        AliasProperty  Name = ProcessName
```

Een object heeft meestal uitgebreide eigenschappen en methoden, zodat u gemakkelijker kunt vinden wat u zoekt, de resultaten kunnen filteren. Met behulp van de para meter `-MemberType` kunt u opgeven dat u bijvoorbeeld alle methoden wilt zien, zoals in het onderstaande voor beeld:

```powershell
Get-Process | Get-Member -MemberType Method
```

Wanneer u terugkeert naar een reactie, worden in Power shell meestal slechts enkele eigenschappen weer gegeven. In het bovenstaande antwoord wordt `Name` `MemberType` en `Definition` weer gegeven. Als u deze weer gave wilt wijzigen, kunt u de cmdlet gebruiken `Select-Object` . `Select-Object` Hiermee kunt u opgeven welke kolommen u wilt weer geven. U kunt deze opgeven met de naam van de kolom, een door komma's gescheiden lijst of een Joker teken `*` . Hier volgt een voor beeld waarin `Select-Object` wordt gebruikt om op te halen `Name` en `Definition` :

```powershell
Get-Process | Get-Member | Select-Object Name, Definition
```

### <a name="search-by-type"></a>Zoeken op type

Een andere manier om te zoeken naar de gewenste opdracht, is door te zoeken naar opdrachten die allemaal op hetzelfde type werken. Wanneer u hebt gebruikt `Get-Member` , hebt u het geretourneerde type als de eerste regel van de reactie als volgt:

```output
TypeName: System.Diagnostics.Process
```

U kunt dit type nu gebruiken en zoeken naar opdrachten als volgt:

```powershell
Get-Command -ParameterType Process
```

Het resultaat van het aanroepen van de bovenstaande is een lijst met opdrachten die alleen voor het type worden uitgevoerd `Process` :

```output
CommandType     Name                         Version    Source
-----------     ----                         -------    ------
Cmdlet          Debug-Process                7.0.0.0    Microsoft.PowerShell.Managem…
Cmdlet          Enter-PSHostProcess          7.1.0.0    Microsoft.PowerShell.Core
Cmdlet          Get-Process                  7.0.0.0    Microsoft.PowerShell.Managem…
Cmdlet          Get-PSHostProcessInfo        7.1.0.0    Microsoft.PowerShell.Core
Cmdlet          Stop-Process                 7.0.0.0    Microsoft.PowerShell.Managem…
Cmdlet          Wait-Process                 7.0.0.0    Microsoft.PowerShell.Managem…
```

Zoals u kunt zien, is het type van een opdracht, zodat u de zoek actie aanzienlijk kunt verfijnen na opdrachten die voor u interessant kunnen zijn.

## <a name="exercise---calling-your-first-command"></a>Oefenen: uw eerste opdracht aanroepen

In deze oefening leert u hoe u uw eerste opdracht uitvoert.

1. Start een Power shell-console door het volgende te typen `pwsh` :

   ```powershell
   pwsh
   ```

1. Voer de volgende `$PSVersionTable.PSVersion` handelingen uit:

   ```powershell
   $PSVersionTable.PSVersion
   ```

   De uitvoer ziet er ongeveer als volgt uit:

   ```output
   Major  Minor  Patch  PreReleaseLabel BuildLabel
   -----  -----  -----  --------------- ----------
   7      1      0
   ```

   Gefeliciteerd, u hebt uw eerste opdracht uitgevoerd en kon informatie krijgen over de versie van Power shell die op uw systeem is geïnstalleerd.

## <a name="exercise---find-related-commands"></a>Oefenen: verwante opdrachten zoeken

In deze oefening is het doel om meer te weten te komen over een opdracht. In dat geval vindt u ook informatie over het type waarmee deze werkt en wat andere vergelijk bare opdrachten op hetzelfde type uitvoeren.

1. Zorg ervoor dat u een Power shell-shell hebt gestart
1. Voer de volgende opdracht uit `Get-Process` :

   ```powershell
   Get-Process | Get-Member | Select-Object TypeName -Unique
   ```

   De uitvoer ziet er ongeveer als volgt uit:

   ```output
   TypeName
   --------
   System.Diagnostics.Process
   --------
   ```

   Wat u terugkrijgt, is een van de typen die worden geretourneerd door de opdracht `Get-Command` . Op dit moment kunt u nu zien welke andere opdracht ook op deze typen wordt uitgevoerd.

1. Voer de opdracht `Get-Command` uit:

   ```powershell
   Get-Command -ParameterType Process
   ```

   De uitvoer ziet er ongeveer als volgt uit:

   ```output
   CommandType     Name                         Version    Source
    -----------     ----                        -------    ------
    Cmdlet          Debug-Process               7.0.0.0    Microsoft.PowerShell.Managem…
    Cmdlet          Enter-PSHostProcess         7.1.0.0    Microsoft.PowerShell.Core
    Cmdlet          Get-Process                 7.0.0.0    Microsoft.PowerShell.Managem…
    Cmdlet          Get-PSHostProcessInfo       7.1.0.0    Microsoft.PowerShell.Core
    Cmdlet          Stop-Process                7.0.0.0    Microsoft.PowerShell.Managem…
    Cmdlet          Wait-Process                7.0.0.0    Microsoft.PowerShell.Managem…
   ```

   Gefeliciteerd, u hebt beheerd om andere opdrachten te vinden die actief zijn op hetzelfde type `Process` .
   Gebruik `Get-Member` is een goed uitgangs punt om te begrijpen welke andere opdrachten u moet uitvoeren.

## <a name="summary"></a>Samenvatting

In dit eerste deel hebt u geleerd wat Power shell is en welke gebieden in kunnen worden gebruikt. Vervolgens kunt u met de cursus over cmdlets en met name `Get-Command` `Get-Verb` en `Get-Member` . Het is belang rijk dat u weet hoe u deze cmdlets kunt gebruiken. In het volgende deel wordt beschreven hoe u het krachtige Help-systeem gebruikt.

### <a name="additional-resources"></a>Aanvullende bronnen

- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member)
