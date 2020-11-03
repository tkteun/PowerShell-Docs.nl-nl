---
description: Hierin worden de WMI Query Language (WQL) beschreven die kunnen worden gebruikt voor het ophalen van WMI-objecten in Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252726"
---
# <a name="about-wql"></a>Over WQL

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden de WMI Query Language (WQL) beschreven die kunnen worden gebruikt voor het ophalen van WMI-objecten in Windows Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

WQL is de query taal van de Windows Management Instrumentation (WMI), de taal die wordt gebruikt om informatie op te halen van WMI.

U hoeft WQL niet te gebruiken om een WMI-query uit te voeren in Windows Power shell.
In plaats daarvan kunt u de para meters van de Get-WmiObject-of Get-CimInstance-cmdlets gebruiken. WQL-query's zijn iets sneller dan de standaard Get-WmiObject-opdrachten en de verbeterde prestaties zijn duidelijk wanneer de opdrachten op honderden systemen worden uitgevoerd. U moet er echter voor zorgen dat de tijd die u besteedt aan het schrijven van een geslaagde WQL-query niet voldoet aan de verbetering van de prestaties.

De basis WQL-instructies die u nodig hebt voor het gebruik van WQL zijn selecteren, waar en van.

## <a name="when-to-use-wql"></a>WANNEER WQL GEBRUIKEN?

Wanneer u met WMI werkt en met name WQL, vergeet dan niet dat u ook Windows Power shell gebruikt. Als een WQL-query niet werkt zoals verwacht, is het eenvoudiger om een standaard Windows Power shell-opdracht te gebruiken dan bij het opsporen van fouten in de WQL-query.

Tenzij u enorme hoeveel heden gegevens uit verschillende band breedte-gebonden externe systemen retourneert, is het nog nooit zo productief dat er uren worden besteed aan een ingewikkelde en convolutieve WQL-query wanneer er sprake is van een perfecte Windows-cmdlet die hetzelfde doet als een beetje langzamer.

## <a name="using-the-select-statement"></a>DE SELECT-INSTRUCTIE GEBRUIKEN

Een typische WMI-query begint met een SELECT-instructie waarmee alle eigenschappen of specifieke eigenschappen van een WMI-klasse worden opgehaald. Als u alle eigenschappen van een WMI-klasse wilt selecteren, gebruikt u een asterisk ( \* ). Met het sleutel woord from geeft u de WMI-klasse op.

Een SELECT-instructie heeft de volgende indeling:

```
Select <property> from <WMI-class>
```

De volgende SELECT-instructie selecteert bijvoorbeeld alle eigenschappen (*) uit de exemplaren van de WMI-klasse Win32_Bios.

```
Select * from Win32_Bios
```

Als u een bepaalde eigenschap van een WMI-klasse wilt selecteren, plaatst u de naam van de eigenschap tussen de tref woorden Select en from.

Met de volgende query wordt alleen de naam van het BIOS uit de WMI-klasse Win32_Bios geselecteerd. Met de opdracht wordt de query opgeslagen in de variabele $queryName.

```
Select Name from Win32_Bios
```

Als u meer dan één eigenschap wilt selecteren, gebruikt u komma's om de eigenschapnamen van elkaar te scheiden.
De volgende WMI-query selecteert de naam en de versie van de WMI-klasse Win32_Bios. Met de opdracht wordt de query opgeslagen in de variabele $queryNameVersion.

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a>DE WQL-QUERY GEBRUIKEN

Er zijn drie manieren om WQL-query's te gebruiken in Windows Power shell-opdracht.

- De cmdlet Get-WmiObject gebruiken
- De cmdlet Get-CimInstance gebruiken
- Gebruik de [wmisearcher] type Accelerator.

## <a name="using-the-get-wmiobject-cmdlet"></a>DE CMDLET GET-WMIOBJECT GEBRUIKEN

De belangrijkste manier om de WQL-query te gebruiken, is deze tussen aanhalings tekens (als een teken reeks) te plaatsen en vervolgens de query reeks als de waarde van de query parameter van de cmdlet Get-WmiObject te gebruiken, zoals in het volgende voor beeld wordt weer gegeven.

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

U kunt de WQL-instructie ook opslaan in een variabele en de variabele vervolgens gebruiken als de waarde van de query parameter, zoals wordt weer gegeven in de volgende opdracht.

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

U kunt beide indelingen gebruiken met elke WQL-instructie. De volgende opdracht gebruikt de query in de variabele $queryName om alleen de naam en versie-eigenschappen van het systeem-BIOS op te halen.

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

Houd er rekening mee dat u de para meters van de Get-WmiObject cmdlet kunt gebruiken om hetzelfde resultaat te verkrijgen. Met de volgende opdracht worden bijvoorbeeld ook de waarden van de eigenschappen name en version van exemplaren van de WMI-klasse Win32_Bios opgehaald.

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a>DE CMDLET GET-CIMINSTANCE GEBRUIKEN

Vanaf Windows Power Shell 3,0 kunt u de cmdlet Get-CimInstance gebruiken om WQL-query's uit te voeren.

Get-CimInstance haalt instanties van CIM-compatibele klassen op, met inbegrip van WMI-klassen. Met de CIM-cmdlets, geïntroduceerde Windows Power Shell 3,0, worden dezelfde taken uitgevoerd als voor de WMI-cmdlets. De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de Common Information Model (CIM) standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van Windows-computers en computers waarop andere besturings systemen worden uitgevoerd.

De volgende opdracht maakt gebruik van de cmdlet Get-CimInstance om een WQL-query uit te voeren.

Elke WQL-query die met Get-WmiObject kan worden gebruikt, kan ook worden gebruikt met Get-CimInstance.

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Get-CimInstance retourneert een CimInstance-object in plaats van de ManagementObject die Get-WmiObject retourneert, maar de objecten zijn heel vergelijkbaar.

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a>DE [wmisearcher] TYPE ACCELERATOR gebruiken

De [wmisearcher] type Accelerator maakt een ManagementObjectSearcher-object van een WQL-instructie teken reeks. Het ManagementObjectSearcher-object heeft veel eigenschappen en methoden, maar de meest eenvoudige methode is de Get-methode, waarmee de opgegeven WMI-query wordt aangeroepen en de resulterende objecten worden geretourneerd.

Met [wmisearcher] krijgt u eenvoudig toegang tot de klasse ManagementObjectSearcher .NET Framework. Hiermee kunt u een query uitvoeren op WMI en de manier configureren waarop de query wordt uitgevoerd.

De [wmisearcher] type Accelerator gebruiken:

1. De WQL-teken reeks casten naar een ManagementObjectSearcher-object.
2. Roep de Get-methode aan van het ManagementObjectSearcher-object.

Met de volgende opdracht wordt bijvoorbeeld de query ' Alles selecteren ' gecast, wordt het resultaat opgeslagen in de variabele $bios en wordt vervolgens de Get-methode aangeroepen van het object ManagementObjectSearcher in de variabele $bios.

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Opmerking: alleen geselecteerde object eigenschappen worden standaard weer gegeven. Deze eigenschappen worden gedefinieerd in het XML-bestand van Types.ps1.

U kunt de [wmisearcher] type Accelerator gebruiken om de query of de variabele te casten. In het volgende voor beeld wordt de type versnelling [wmisearcher] gebruikt voor het casten van de variabele. Het resultaat is hetzelfde.

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Wanneer u de [wmisearcher] type Accelerator gebruikt, wordt de query reeks gewijzigd in een ManagementObjectSearcher-object, zoals wordt weer gegeven in de volgende opdrachten.

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

Deze opdracht indeling werkt voor elke query. Met de volgende opdracht wordt de waarde van de eigenschap name van de WMI-klasse Win32_Bios opgehaald.

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

U kunt deze bewerking uitvoeren in één opdracht, hoewel de opdracht iets moeilijker te interpreteren is.

In deze indeling gebruikt u de [wmisearcher] type Accelerator voor het casten van de WQL-query teken reeks naar een ManagementObjectSearcher en roept u vervolgens de Get-methode aan voor het object-alle in één opdracht. De haakjes () die de geconverteerde teken reeks direct Windows Power shell omsluiten om de teken reeks te casten voordat de methode wordt aangeroepen.

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a>DE BASIS WQL WHERE-INSTRUCTIE GEBRUIKEN

Een WHERE-instructie bepaalt de voor waarden voor de gegevens die een SELECT-instructie retourneert.

De instructie WHERE heeft de volgende indeling:

```
where <property> <operator> <value>
```

Bijvoorbeeld:

```
where Name = 'Notepad.exe'
```

De instructie WHERE wordt gebruikt met de instructie SELECT, zoals wordt weer gegeven in het volgende voor beeld.

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

Wanneer u de WHERE-instructie gebruikt, moeten de naam en waarde van de eigenschap nauw keurig zijn.

Met de volgende opdracht worden bijvoorbeeld de klad blok-processen op de lokale computer opgehaald.

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

De volgende opdracht mislukt echter, omdat de proces naam de bestandsnaam extensie. exe bevat.

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a>WHERE-INSTRUCTIE VERGELIJKINGS OPERATORS

De volgende Opera tors zijn geldig in een WQL where-instructie.

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

Er zijn andere opera Tors, maar deze worden gebruikt voor het maken van vergelijkingen.

Met de volgende query worden bijvoorbeeld de eigenschappen name en Priority van processen in de Win32_Process klasse waarvan de prioriteit van het proces groter is dan of gelijk is aan 11. De Get-WmiObject-cmdlet voert de query uit.

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a>DE WQL-OPERA TORS IN DE FILTER PARAMETER GEBRUIKEN

De WQL-Opera tors kunnen ook worden gebruikt in de waarde van de filter parameter van de Get-WmiObject-of Get-CimInstance-cmdlets, en in de waarde van de query parameters van deze cmdlets.

Met de volgende opdracht worden bijvoorbeeld de eigenschappen name en ProcessID opgehaald van de laatste vijf processen die de waarde van ProcessID hebben die groter is dan 1004. De opdracht maakt gebruik van de para meter filter om de voor waarde van ProcessID op te geven.

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a>DE OPERATOR LIKE GEBRUIKEN

Met de operator Like kunt u Joker tekens gebruiken om de resultaten van een WQL-query te filteren.

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

Wanneer de like-operator wordt gebruikt zonder joker tekens of bereik operators, gedraagt deze zich als de gelijkheids operator (=) en retourneert alleen objecten als ze exact overeenkomen met het patroon.

U kunt de bereik bewerking combi neren met het percentage Joker teken om eenvoudige, maar krachtige filters te maken.

### <a name="like-operator-examples"></a>LIKE, OPERATOR-VOOR BEELDEN

#### <a name="example-1-range"></a>VOOR beeld 1: [ \<range> ]

De volgende opdrachten starten Klad blok en zoeken naar een exemplaar van de Win32_Process klasse met een naam die begint met een letter tussen "H" en "N" (niet hoofdletter gevoelig).

De query moet elk proces retour neren van Hotpad.exe via Notepad.exe.

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a>VOOR beeld 2: [ \<range> ] en%

De volgende opdrachten selecteren alle processen met een naam die begint met een letter tussen A en P (niet hoofdletter gevoelig), gevolgd door nul of meer letters in een combi natie hiervan.

De Get-WmiObject-cmdlet voert de query uit, de cmdlet Select-Object haalt de eigenschappen name en ProcessID op en de Sort-Object-cmdlet sorteert de resultaten in alfabetische volg orde op naam.

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a>VOOR beeld 3: niet in bereik (^)

Met de volgende opdracht worden processen opgehaald waarvan de namen niet beginnen met een van de volgende letters: A, S, W, P, R, C, U, N

en er zijn nul of meer letters gevolgd.

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a>VOOR beeld 4: wille keurige tekens--of geen (%)

Met de volgende opdrachten worden processen opgehaald die namen hebben die beginnen met ' calc '.
Het symbool% in WQL is gelijk aan het sterretje ( \* )-symbool in reguliere expressies.

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a>VOOR beeld 5: één teken (_)

Met de volgende opdrachten worden processen opgehaald die een naam hebben met het volgende patroon, ' c_lc.exe ' waarbij het onderstrepings teken een wille keurig teken vertegenwoordigt. Dit patroon komt overeen met een wille keurige naam van calc.exe via czlc.exe of c9lc.exe, maar komt niet overeen met namen waarin de ' c ' en ' l ' door meer dan één teken worden gescheiden.

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a>VOOR beeld 6: exacte overeenkomst

Met de volgende opdrachten worden processen met de naam WLIDSVC.exe opgehaald. Hoewel de query het like-tref woord gebruikt, is er een exacte overeenkomst nodig, omdat de waarde geen joker tekens bevat.

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a>DE OPERATOR OR GEBRUIKEN

Als u meerdere onafhankelijke voor waarden wilt opgeven, gebruikt u het sleutel woord of. Het sleutel woord of wordt weer gegeven in de component WHERE. Het voert een inclusieve of-bewerking uit op twee (of meer) voor waarden en retourneert items die voldoen aan de voor waarden.

De operator or heeft de volgende indeling:

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

Met de volgende opdrachten worden bijvoorbeeld alle exemplaren van de WMI-klasse Win32_Process opgehaald, maar alleen geretourneerd als de proces naam winword.exe of excel.exe is.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

De instructie or kan worden gebruikt met meer dan twee voor waarden. In de volgende query haalt de instructie or Winword.exe, Excel.exe of Powershell.exe.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a>DE OPERATOR AND GEBRUIKEN

Gebruik het sleutel woord en om meerdere gerelateerde voor waarden op te geven. Het sleutel woord en wordt weer gegeven in de component WHERE. Hiermee worden items geretourneerd die voldoen aan alle voor waarden.

De operator and heeft de volgende indeling:

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

Met de volgende opdrachten worden bijvoorbeeld processen opgehaald met de naam ' Winword.exe ' en de proces-ID van 6512.

Houd er rekening mee dat de opdrachten de cmdlet Get-CimInstance gebruiken.

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

Alle Opera Tors, met inbegrip van de like-Opera Tors, zijn geldig met de Opera tors or en en. En u kunt de Opera tors or en en en in één query combi neren met haakjes die Windows Power shell laten zien welke componenten eerst moeten worden verwerkt.

Met deze opdracht wordt het Windows Power shell-vervolg teken (') gebruikt om de opdracht op twee regels te verdelen.

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a>ZOEKEN NAAR NULL-WAARDEN

Zoeken naar Null-waarden in WMI is lastig, omdat dit kan leiden tot onvoorspelbare resultaten. Null is niet nul en is niet gelijk aan of een lege teken reeks. Sommige eigenschappen van de WMI-klasse worden geïnitialiseerd en andere niet, dus het is niet mogelijk om een zoek opdracht voor NULL te gebruiken voor alle eigenschappen.

Als u wilt zoeken naar Null-waarden, gebruikt u de operator is met de waarde Null.

Met de volgende opdrachten worden bijvoorbeeld processen opgehaald die een null-waarde voor de eigenschap IntallDate hebben. De opdrachten retour neren veel processen.

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

Met de volgende opdracht worden daarentegen gebruikers accounts opgehaald die een null-waarde voor de eigenschap Description hebben. Met deze opdracht worden geen gebruikers accounts geretourneerd, hoewel de meeste gebruikers accounts geen waarde hebben voor de eigenschap Description.

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

Als u wilt zoeken naar de gebruikers accounts die geen waarde hebben voor de eigenschap Description, gebruikt u de gelijkheids operator om een lege teken reeks op te halen. Gebruik twee opeenvolgende enkele aanhalings tekens om de lege teken reeks weer te geven.

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a>WAAR OF ONWAAR GEBRUIKEN

Gebruik waar en ONWAAR om Booleaanse waarden in de eigenschappen van WMI-objecten op te halen.
De waarden zijn niet hoofdlettergevoelig.

De volgende WQL-query retourneert alleen lokale gebruikers accounts van een computer die lid is van een domein.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

Als u domein accounts wilt zoeken, gebruikt u de waarde ONWAAR, zoals in het volgende voor beeld wordt weer gegeven.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a>HET ESCAPE TEKEN GEBRUIKEN

WQL maakt gebruik van de back slash ( \) als escape-teken. Dit wijkt af van Windows Power shell, dat gebruikmaakt van het apostroffen-teken (').

Aanhalings tekens en de teken reeks die voor aanhalings tekens worden gebruikt, moeten vaak worden voorafgegaan zodat ze niet onjuist zijn geïnterpreteerd.

Als u een gebruiker wilt zoeken waarvan de naam één aanhalings teken bevat, gebruikt u een back slash om het enkele aanhalings teken te escapen, zoals wordt weer gegeven in de volgende opdracht.

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

In sommige gevallen moet de back slash ook worden ontsnapt. Met de volgende opdrachten wordt bijvoorbeeld een ongeldige query fout gegenereerd vanwege de back slash in de waarde van het bijschrift.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

Als u de back slash wilt escapeel, gebruikt u een tweede back slash-teken, zoals in de volgende opdracht wordt weer gegeven.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a>ZIE OOK

[about_Special_Characters](about_Special_Characters.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_WMI](about_WMI.md)

[about_WMI_Cmdlets](about_WMI_Cmdlets.md)
