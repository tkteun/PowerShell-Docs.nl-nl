---
description: Opdrachten in de Power shell combi neren in pijp lijnen
Locale: en-US
ms.date: 03/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: 91c0d5f1f7b05b8c8536bf27a443c3894da01347
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104726414"
---
# <a name="about-pipelines"></a>Over pijp lijnen

## <a name="short-description"></a>Korte beschrijving

Opdrachten in de Power shell combi neren in pijp lijnen

## <a name="long-description"></a>Lange beschrijving

Een pijp lijn is een reeks opdrachten die zijn verbonden door pijplijn operators ( `|` ) (ASCII 124). Elke pijplijn operator verzendt de resultaten van de voor gaande opdracht naar de volgende opdracht.

De uitvoer van de eerste opdracht kan worden verzonden voor verwerking als invoer voor de tweede opdracht. En die uitvoer kan naar nog een andere opdracht worden verzonden. Het resultaat is een complexe opdracht reeks of- _pijp lijn_ die bestaat uit een reeks eenvoudige opdrachten.

Bijvoorbeeld:

```powershell
Command-1 | Command-2 | Command-3
```

In dit voor beeld worden de objecten `Command-1` verzonden naar `Command-2` .
`Command-2` Hiermee worden de objecten verwerkt en verzonden naar `Command-3` . `Command-3` de objecten worden verwerkt en verzonden naar de pijp lijn. Omdat er geen opdrachten meer in de pijp lijn staan, worden de resultaten weer gegeven in de console.

In een pijp lijn worden de opdrachten verwerkt in volg orde van links naar rechts. De verwerking wordt verwerkt als één bewerking en de uitvoer wordt weer gegeven wanneer deze wordt gegenereerd.

Hier volgt een eenvoudig voor beeld. Met de volgende opdracht wordt het klad blok proces opgehaald en vervolgens gestopt.

Bijvoorbeeld:

```powershell
Get-Process notepad | Stop-Process
```

Met de eerste opdracht wordt de `Get-Process` cmdlet gebruikt om een object op te halen dat het klad blok-proces vertegenwoordigt. Er wordt een pijplijn operator ( `|` ) gebruikt om het proces object naar de cmdlet te verzenden `Stop-Process` , waardoor het klad blok-proces wordt gestopt. U ziet dat de `Stop-Process` opdracht geen **naam** of **id-** para meter heeft om het proces op te geven, omdat het opgegeven proces via de pijp lijn wordt verzonden.

In dit voor beeld van de pijp lijn worden de tekst bestanden in de huidige map opgehaald, worden alleen de bestanden geselecteerd die meer dan 10.000 bytes lang zijn, worden gesorteerd op lengte en worden de naam en de lengte van elk bestand in een tabel weer gegeven.

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

Deze pijp lijn bestaat uit vier opdrachten in de opgegeven volg orde. In de volgende afbeelding ziet u de uitvoer van elke opdracht die wordt door gegeven aan de volgende opdracht in de pijp lijn.

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a>Pijp lijnen gebruiken

De meeste Power shell-cmdlets zijn ontworpen ter ondersteuning van pijp lijnen. In de meeste _gevallen kunt u_ de resultaten van een **Get** -cmdlet door geven aan een andere cmdlet van hetzelfde zelfstandig naam woord.
U kunt bijvoorbeeld de uitvoer van de cmdlet door sluizen `Get-Service` naar de `Start-Service` `Stop-Service` cmdlets of.

In deze voorbeeld pijplijn wordt de WMI-service op de computer gestart:

```powershell
Get-Service wmi | Start-Service
```

Een ander voor beeld: u kunt de uitvoer van `Get-Item` of `Get-ChildItem` binnen de Power shell-register provider door geven aan de `New-ItemProperty` cmdlet. In dit voor beeld wordt een nieuwe register vermelding, **NoOfEmployees**, met de waarde **8124**, toegevoegd aan de register sleutel **mijn bedrijf** .

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

Veel van de cmdlets van het hulp programma, zoals,,, `Get-Member` `Where-Object` `Sort-Object` `Group-Object` en `Measure-Object` worden bijna uitsluitend in pijp lijnen gebruikt. U kunt elk object type door sluizen naar deze cmdlets. In dit voor beeld ziet u hoe alle processen op de computer worden gesorteerd op het aantal geopende ingangen in elk proces.

```powershell
Get-Process | Sort-Object -Property handles
```

U kunt objecten door sluizen naar de indelings-, export-en uitvoer-cmdlets, zoals `Format-List` ,, `Format-Table` `Export-Clixml` , `Export-CSV` en `Out-File` .

In dit voor beeld ziet u hoe u de `Format-List` cmdlet gebruikt om een lijst met eigenschappen voor een proces object weer te geven.

```powershell
Get-Process winlogon | Format-List -Property *
```

U kunt ook de uitvoer van systeem eigen opdrachten door sluizen naar Power shell-cmdlets. Bijvoorbeeld:

```powershell
PS> ipconfig.exe | Select-String -Pattern 'IPv4'

   IPv4 Address. . . . . . . . . . . : 172.24.80.1
   IPv4 Address. . . . . . . . . . . : 192.168.1.45
   IPv4 Address. . . . . . . . . . . : 100.64.108.37
```

> [!IMPORTANT]
> De **slagen** -en **fout** stromen zijn vergelijkbaar met de stdin-en stderr-streams van andere shells. Stdin is echter niet verbonden met de Power shell-pijp lijn voor invoer. Zie [about_Redirection](about_Redirection.md)voor meer informatie.

Met een beetje van de praktijk zult u zien dat het combi neren van eenvoudige opdrachten in pijp lijnen tijd en typen bespaart en uw scripting efficiënter maakt.

## <a name="how-pipelines-work"></a>Hoe pijp lijnen werken

In deze sectie wordt uitgelegd hoe invoer objecten zijn gebonden aan cmdlet-para meters en verwerkt tijdens de uitvoering van de pijp lijn.

### <a name="accepts-pipeline-input"></a>Invoer van pijp lijn accepteren

Voor de ondersteuning van pipelining moet de ontvangende cmdlet een para meter hebben die de invoer van de pijp lijn accepteert. Gebruik de `Get-Help` opdracht met de opties **Full** of **para meter** om te bepalen welke para meters van een cmdlet pijplijn invoer accepteren.

Als u bijvoorbeeld wilt bepalen welke para meters van de `Start-Service` cmdlet pijplijn invoer accepteren, typt u:

```powershell
Get-Help Start-Service -Full
```

of

```powershell
Get-Help Start-Service -Parameter *
```

In de Help voor de `Start-Service` cmdlet ziet u dat alleen de **input object** -en **name** -para meters pijplijn invoer accepteren.

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

Wanneer u objecten via de pijp lijn verzendt naar `Start-Service` , probeert Power shell de objecten te koppelen aan de para meters **input object** en **name** .

### <a name="methods-of-accepting-pipeline-input"></a>Methoden voor het accepteren van pijp lijn invoer

Cmdlets-para meters kunnen de invoer van de pijp lijn op twee verschillende manieren accepteren:

- **ByValue**: de para meter accepteert waarden die overeenkomen met het verwachte .net-type of die kunnen worden geconverteerd naar dat type.

  De para meter **name** van accepteert de `Start-Service` invoer van de pijp lijn op waarde. Het kan teken reeks objecten of objecten accepteren die kunnen worden geconverteerd naar teken reeksen.

- **ByPropertyName**: de para meter accepteert alleen invoer wanneer het invoer object een eigenschap heeft met dezelfde naam als de para meter.

  De para meter name van kan bijvoorbeeld `Start-Service` objecten accepteren die een eigenschap **naam** hebben. Als u de eigenschappen van een object wilt weer geven, pipet u het naar `Get-Member` .

Sommige para meters kunnen objecten accepteren op basis van waarde of eigenschaps naam, waardoor het gemakkelijker wordt om invoer uit de pijp lijn te halen.

### <a name="parameter-binding"></a>Parameter binding

Wanneer u objecten van de ene opdracht naar een andere opdracht Pipet, probeert Power shell de pijp lijn objecten te koppelen aan een para meter van de ontvangende cmdlet.

Het onderdeel parameter binding van Power shell koppelt de invoer objecten aan cmdlet-para meters op basis van de volgende criteria:

- De para meter moet invoer van een pijp lijn accepteren.
- De para meter moet het type object accepteren dat wordt verzonden of een type dat kan worden geconverteerd naar het verwachte type.
- De para meter wordt niet gebruikt in de opdracht.

De `Start-Service` cmdlet heeft bijvoorbeeld een groot aantal para meters, maar slechts twee hiervan, de **naam** en **input object** accepteren pijplijn invoer. De para meter **name** heeft teken reeksen en de para meter **input object** maakt gebruik van service objecten. Daarom kunt u teken reeksen, service objecten en objecten pipet met eigenschappen die kunnen worden geconverteerd naar teken reeks-of service objecten.

Power shell beheert de parameter binding zo efficiënt mogelijk. U kunt de Power shell niet om te koppelen aan een specifieke para meter Voorst Ellen of afdwingen. De opdracht mislukt als Power shell de objecten in de pijp lijn niet kan binden.

Zie voor meer informatie over het oplossen van verbindings fouten verderop in dit artikel [pijplijn fouten onderzoeken](#investigating-pipeline-errors) .

### <a name="one-at-a-time-processing"></a>Een-op-een-verwerking

Pijpleiding objecten naar een opdracht zijn vergelijkbaar met het gebruik van een para meter van de opdracht voor het indienen van de objecten. Laten we eens kijken naar een voor beeld van een pijp lijn. In dit voor beeld gebruiken we een pijp lijn om een tabel met Service objecten weer te geven.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

Dit is functioneel, zoals het gebruik van de para meter **input object** van `Format-Table` om de object verzameling in te dienen.

We kunnen bijvoorbeeld het verzamelen van services opslaan in een variabele die wordt door gegeven met behulp van de para meter **input object** .

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

Of we kunnen de opdracht insluiten in de para meter **input object** .

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

Er is echter een belang rijk verschil. Wanneer u meerdere objecten naar een opdracht Pipet, verzendt Power shell de objecten een voor een naar de opdracht. Wanneer u een opdracht parameter gebruikt, worden de objecten als één matrix object verzonden. Dit secundaire verschil heeft aanzienlijke gevolgen.

Bij het uitvoeren van een pijp lijn wordt door Power shell automatisch een wille keurig type geïnventariseerd dat de interface implementeert `IEnumerable` en de leden een voor een verzendt via de pijp lijn. De uitzonde ring is `[hashtable]` , waarvoor een aanroep naar de methode is vereist `GetEnumerator()` .

In de volgende voor beelden worden een matrix en een hashtabel door gegeven aan de `Measure-Object` cmdlet om het aantal ontvangen objecten van de pijp lijn te tellen. De matrix heeft meerdere leden en de hashtabel heeft meerdere sleutel-waardeparen. Alleen de matrix wordt een voor een opgesomd.

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

En als u meerdere proces objecten van de `Get-Process` cmdlet naar de cmdlet pipet `Get-Member` , verzendt Power shell elk proces object, één per keer, naar `Get-Member` . `Get-Member` Hiermee worden de .NET-klasse (type) van de proces objecten en hun eigenschappen en methoden weer gegeven.

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> `Get-Member` elimineert dubbele items, dus als de objecten allemaal van hetzelfde type zijn, wordt slechts één object type weer gegeven.

Als u echter de para meter **input object** van gebruikt `Get-Member` , `Get-Member` ontvangt deze een matrix van **System. Diagnostics. process** -objecten als één eenheid. De eigenschappen van een matrix met objecten worden weer gegeven. (Noteer het matrix symbool ( `[]` ) na de naam van het type **System. object** .)

Bijvoorbeeld:

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

Dit resultaat is mogelijk niet geschikt voor u. Maar wanneer u het begrijpt, kunt u het gebruiken. Alle Matrix objecten hebben bijvoorbeeld een eigenschap **Count** . U kunt dit gebruiken om het aantal processen te tellen dat op de computer wordt uitgevoerd.

Bijvoorbeeld:

```powershell
(Get-Process).count
```

Het is belang rijk om te onthouden dat objecten die via de pijp lijn zijn verzonden, een voor een worden bezorgd.

## <a name="investigating-pipeline-errors"></a>Pijplijn fouten onderzoeken

Wanneer Power shell de objecten in de pipes niet kan koppelen aan een para meter van de ontvangende cmdlet, mislukt de opdracht.

In het volgende voor beeld proberen we een register vermelding van de ene register sleutel naar een andere te verplaatsen. `Get-Item`Met de cmdlet wordt het doelpad opgehaald, dat vervolgens wordt doorgeleid naar de `Move-ItemProperty` cmdlet. De `Move-ItemProperty` opdracht geeft het huidige pad en de naam van de register vermelding die moet worden verplaatst.

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

De opdracht mislukt en in Power shell wordt het volgende fout bericht weer gegeven:

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

Als u wilt onderzoeken, gebruikt u de `Trace-Command` cmdlet voor het traceren van het parameter bindings onderdeel van Power shell. In het volgende voor beeld wordt de parameter binding tijdens de uitvoering van de pijp lijn traceren. De para meter **PSHost** geeft de tracerings resultaten in de-console en de **filepath** para meter de tracerings resultaten naar het `debug.txt` bestand verzenden voor latere referentie.

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

De resultaten van de tracering zijn lang, maar ze tonen de waarden die aan de cmdlet zijn gebonden `Get-Item` en vervolgens worden de benoemde waarden gebonden aan de `Move-ItemProperty` cmdlet.

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

Ten slotte ziet u dat de poging om het pad te binden aan de para meter **Destination** van `Move-ItemProperty` failed.

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

Gebruik de `Get-Help` cmdlet om de kenmerken van de **doel** parameter weer te geven.

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

De resultaten geven aan dat de **bestemming** alleen voor de invoer van de pijp lijn wordt gebruikt door de naam van de eigenschap. Daarom moet het object met pijp lijn een eigenschap met de naam **Destination** hebben.

Gebruiken `Get-Member` om de eigenschappen van het object weer te geven die afkomstig zijn van `Get-Item` .

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

In de uitvoer ziet u dat het item een **micro soft. Win32. RegistryKey** -object is dat geen **doel** eigenschap heeft. In dit artikel wordt uitgelegd waarom de opdracht is mislukt.

De para meter **Path** accepteert de invoer van de pijp lijn op naam of op waarde.

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

Als u de opdracht wilt herstellen, moet u het doel opgeven in de `Move-ItemProperty` cmdlet en gebruiken `Get-Item` om het **pad** op te halen van het item dat u wilt verplaatsen.

Bijvoorbeeld:

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a>Intrinsieke regel voortzetting

Zoals al besproken, is een pijp lijn een reeks opdrachten die zijn verbonden door pijplijn operators ( `|` ), die meestal op één regel zijn geschreven. Voor de Lees baarheid kunt u met Power shell echter de pijp lijn splitsen over meerdere regels.
Wanneer een pipe-operator het laatste token op de regel is, voegt de Power shell-parser de volgende regel toe aan de huidige opdracht om door te gaan met de constructie van de pijp lijn.

Bijvoorbeeld de volgende pijp lijn met één regel:

```powershell
Command-1 | Command-2 | Command-3
```

kan worden geschreven als:

```powershell
Command-1 |
  Command-2 |
    Command-3
```

De voorloop spaties op de volgende regels zijn niet significant. De inspringing verbetert de Lees baarheid.

Power shell 7 voegt ondersteuning toe voor voortzetting van pijp lijnen met het pijp lijn teken aan het begin van een regel. In de volgende voor beelden ziet u hoe u deze nieuwe functionaliteit kunt gebruiken.

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> Wanneer u interactief werkt in de shell, moet u code met pijp lijnen alleen aan het begin van een regel plakken wanneer u <kbd>CTRL</kbd> + <kbd>V</kbd> gebruikt om te plakken.
> Klik met de rechter muisknop op plak bewerkingen Voeg de regels een voor een in. Omdat de regel niet eindigt met een pijp lijn teken, beschouwt Power shell de invoer als voltooid en wordt die regel uitgevoerd als ingevoerd.

## <a name="see-also"></a>Zie ook

[about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

[about_Objects](about_objects.md)

[about_Parameters](about_parameters.md)

[about_Command_Syntax](about_command_syntax.md)

[about_ForEach](about_foreach.md)
