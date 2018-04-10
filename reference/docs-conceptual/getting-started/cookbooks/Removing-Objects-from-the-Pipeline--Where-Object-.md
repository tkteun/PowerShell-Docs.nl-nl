---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten verwijderen vanuit de Pipeline waar Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 2d89defdb1b234a9d0021fc06e1f05a95bb1bce9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Verwijderen van objecten uit de pijplijn (Where-Object)

In Windows PowerShell kunt u vaak genereren en doorgegeven meer objecten voor een pijplijn dan u wenst. U kunt opgeven dat de eigenschappen van bepaalde objecten worden weergegeven met behulp van de **indeling** cmdlets, maar dit niet helpt met het probleem van het gehele objecten verwijderen uit de weergave. U wilt filteren, objecten vóór het einde van een pijplijn, zodat u acties op slechts een subset van de objecten in eerste instantie gegenereerd uitvoeren kan.

Windows PowerShell omvat een **Where-Object** u elk object in de pijplijn te testen en alleen langs de pijplijn te doorgeven kunt als deze voldoet aan de voorwaarde van een afzonderlijke test-cmdlet. Objecten die niet door de test worden verwijderd vanuit de pipeline. U de testvoorwaarde opgeven als de waarde van de **waar ObjectFilterScript** parameter.

### <a name="performing-simple-tests-with-where-object"></a>U eenvoudige tests uitvoert met de Where-Object

De waarde van **FilterScript** is een *scriptblok* - een of meer Windows PowerShell-opdrachten omgeven door accolades {} - die resulteert in waar of ONWAAR. Deze scriptblokken is zeer eenvoudig, maar ze worden gemaakt moet weten over een andere Windows PowerShell-concept vergelijkingsoperators. Een vergelijkingsoperator vergelijkt de items die worden weergegeven voor elke zijde van deze. Vergelijkingsoperators beginnen met een '-' teken en worden gevolgd door een naam. Basic vergelijkingsoperators werken op vrijwel elke soort object. De meer geavanceerde vergelijkingsoperators mogelijk werken alleen op tekst- of -matrices.

> [!NOTE]
> Als u werkt met tekst zijn, Windows PowerShell-vergelijkingsoperators standaard niet hoofdlettergevoelig.

Symbolen zoals <>, vanwege het parseren van de overwegingen en = niet als vergelijkingsoperators worden gebruikt. In plaats daarvan vergelijkingsoperators bestaan uit letters. De basic vergelijkingsoperators worden weergegeven in de volgende tabel.

|Vergelijkingsoperator|Betekenis|Voorbeeld (' true ' geretourneerd)|
|-----------------------|-----------|--------------------------|
|-eq|is gelijk aan|1 - eq 1|
|-ne|Is niet gelijk aan|1 - ne 2|
|-lt|Is kleiner dan|1 - lt 2|
|-RP|Is kleiner dan of gelijk aan|1 - RP 2|
|-gt|Is groter dan|2 - gt 1|
|-ge|Is groter dan of gelijk aan|2 -ge 1|
|-zoals|Lijkt (vergelijking van jokertekens voor tekst)|"bestand.doc'-zoals ' f\*basisbedrijfstoepassingen?"|
|-notlike|Is geen zoals (vergelijking van jokertekens voor tekst)|'bestand.doc'-notlike ' p\*.doc '|
|-bevat|Bevat|1,2,3 - 1 bevat|
|-notcontains|Bevat geen|1,2,3 -notcontains 4|

De speciale variabele '$_' WHERE-Object scriptblokken gebruiken om te verwijzen naar het huidige object in de pijplijn. Hier volgt een voorbeeld van hoe het werkt. Als u een lijst met getallen hebben en retourneren van de waarden die minder dan 3 zijn, kunt u Where-Object voor het filteren van de getallen door te typen:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a>Filteren op basis van eigenschappen van het Object

Aangezien $_ naar de huidige pipeline-object verwijst, wordt toegang tot de eigenschappen voor onze tests.

Als u bijvoorbeeld kunt kijken we de klasse Win32_SystemDriver in WMI. Er zijn mogelijk honderden besturingsprogramma's op een bepaald systeem, maar u mogelijk alleen geïnteresseerd zijn in een bepaalde set van het besturingsprogramma's, zoals die momenteel worden uitgevoerd. Als u lid zijn van Get Win32_SystemDriver leden weergeven (**Get-WmiObject-klasse Win32_SystemDriver | De eigenschap Get-Member - MemberType**) ziet u dat de relevante eigenschap status is en dat er een waarde van het 'Uitvoeren' wanneer het stuurprogramma wordt uitgevoerd. U kunt de systeem-stuurprogramma's filteren selecteren uitgevoerd die door te typen:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Dit resulteert in nog steeds een lange lijst. U wilt filteren zodat alleen de stuurprogramma's automatisch worden gestart door de waarde van StartMode ook testen selecteren:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

Dit biedt ons veel informatie die we niet meer nodig omdat we weten dat de stuurprogramma's worden uitgevoerd. De enige informatie die we waarschijnlijk nodig hebt op dit moment zijn in feite de naam en de weergavenaam. De volgende opdracht bevat alleen deze twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

Er zijn twee elementen van de Where-Object in de bovenstaande opdracht, maar ze kunnen worden uitgedrukt in een enkel element in de Where-Object met behulp van de - en de logische operator, als volgt:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

De standaard logische operators worden weergegeven in de volgende tabel.

|Logische Operator|Betekenis|Voorbeeld (' true ' geretourneerd)|
|--------------------|-----------|--------------------------|
|- en|Logische en; True als aan beide zijden wordt voldaan|(1 - eq 1) - en (2 - eq 2).|
|- of|Logische of; True als beide zijden ingesteld op true is|(1 - eq 1) - of (1 - eq 2).|
|-niet|Logische not; keert true en false|-niet (1 - eq 2)|
|\!|Logische not; keert true en false|\!(1 - eq 2)|