---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten uit de pijplijn verwijderen Where-Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293143"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Objecten verwijderen uit de pijplijn (Where-Object)

In Windows PowerShell kunt u vaak genereren en geven meer objecten voor een pijplijn dan u wilt. Kunt u de eigenschappen van bepaalde objecten om weer te geven met behulp van de **indeling** cmdlets, maar dit niet helpt met het probleem van het gehele objecten verwijderen uit de weergave. U wilt filteren objecten vóór het einde van een pijplijn, zodat u acties op slechts een subset van de objecten in eerste instantie gegenereerd uitvoeren kunt.

Windows PowerShell bevat een `Where-Object` u elk object in de pijplijn testen en alleen langs de pijplijn te doorgeven kunt als deze voldoet aan de voorwaarde van een bepaalde test-cmdlet. Objecten die niet door de test worden verwijderd uit de pijplijn. U de testvoorwaarde opgeven als de waarde van de `Where-Object` **FilterScript** parameter.

## <a name="performing-simple-tests-with-where-object"></a>Uitvoeren van eenvoudige tests uit met het Where-Object

De waarde van **FilterScript** is een *scriptblok* -een of meer Windows PowerShell-opdrachten omgeven door accolades {} -die wordt geëvalueerd op waar of ONWAAR. Deze scriptblokken kunnen zeer eenvoudig, maar ze worden gemaakt moet weten over andere Windows PowerShell-concept, vergelijkingsoperators. Een vergelijkingsoperator vergelijkt de items die worden weergegeven voor elke zijde van het. Vergelijkingsoperators beginnen met een '-' teken en worden gevolgd door een naam. Basic vergelijkingsoperators werken op vrijwel elk soort object. De meer geavanceerde vergelijkingsoperators kunnen uitsluitend worden gebruikt voor tekst- of -matrices.

> [!NOTE]
> Windows PowerShell-vergelijkingsoperators zijn standaard bij het werken met tekst, niet hoofdlettergevoelig.

Vanwege het parseren van overwegingen, symbolen zoals <>, en = niet als vergelijkingsoperators worden gebruikt. In plaats daarvan vergelijkingsoperators bestaan uit letters. De basic vergelijkingsoperators worden weergegeven in de volgende tabel.

|Vergelijkingsoperator|Betekenis|Voorbeeld (retourneert ' True ')|
|-----------------------|-----------|--------------------------|
|-eq|is gelijk aan|1 -eq 1|
|-ne|Is niet gelijk aan|1 - ne 2|
|-lt|Is kleiner dan|1 - lt 2|
|-le|is kleiner dan of gelijk aan|1 - le 2|
|-gt|Is groter dan|2 - gt 1|
|-ge|is groter dan of gelijk zijn aan|2 -ge 1|
|-like|Is vergelijkbaar met (vergelijking van jokertekens voor tekst)|"bestand.doc"-, zoals ' f\*basisbedrijfstoepassingen? "|
|-notlike zijn|Is niet als (vergelijking van jokertekens voor tekst)|"bestand.doc"-notlike zijn "p\*.doc"|
|-bevat|bevat|1,2,3 - 1 bevat|
|-notcontains|Bevat niet|1,2,3 -notcontains 4|

WHERE-Object-scriptblokken de speciale variabele gebruiken `$_` om te verwijzen naar het huidige object in de pijplijn. Hier volgt een voorbeeld van hoe het werkt. Als u een lijst met getallen hebben en alleen wilt retourneren die minder dan 3 zijn, kunt u Where-Object voor het filteren van de getallen door te typen:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filteren op basis van eigenschappen van het Object

Aangezien `$_` verwijst naar de huidige pipeline-object, hebben we toegang tot de eigenschappen voor onze tests.

Als u bijvoorbeeld kunt kijken we de klasse Win32_SystemDriver in WMI. Er zijn mogelijk honderden stuurprogramma's op een bepaald systeem, maar u alleen mogelijk ook geïnteresseerd in een bepaalde set de systeem-stuurprogramma's, zoals die momenteel worden uitgevoerd. Als u een Get-Member kunt Win32_SystemDriver leden weergeven (**Get-WmiObject-klasse Win32_SystemDriver | De eigenschap Get-Member - MemberType**) ziet u dat de relevante eigenschap status is en dat er een waarde van het 'Uitvoeren' als het stuurprogramma wordt uitgevoerd. U kunt de stuurprogramma's, filteren selecteren alleen de actieve door door te typen:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Dit levert nog steeds een lange lijst. U wilt filteren zodat alleen de stuurprogramma's automatisch worden gestart door de waarde van StartMode ook testen selecteren:

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

Dit biedt ons een grote hoeveelheid informatie die we niet langer nodig hebt omdat we weten dat de stuurprogramma's worden uitgevoerd. De enige informatie die we waarschijnlijk nodig hebt op dit moment zijn in feite de naam en de weergavenaam. De volgende opdracht bevat alleen deze twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:

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

Er zijn twee Where-Object-elementen in de bovenstaande opdracht, maar ze kunnen worden uitgedrukt in één element Where-Object met behulp van de - en de logische operator, als volgt:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

De standaard logische operators worden weergegeven in de volgende tabel.

|Logische Operator|Betekenis|Voorbeeld (retourneert ' True ')|
|--------------------|-----------|--------------------------|
|- en|Logische en; ' True ' als beide kanten ' True ' zijn|(1 - eq 1) - en (2 - eq 2).|
|- of|Logische of; ' True ' als beide kanten ingesteld op true is|(1 - eq 1) - of (1 - eq 2).|
|-niet|Logische not; keert de waarde true en false|-geen (1 - eq 2)|
|\!|Logische not; keert de waarde true en false|\!(1 - eq 2)|
