---
description: Hierin wordt uitgelegd hoe u objecten maakt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 8903af794c83e4c84709e3eeb21489557458e988
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252786"
---
# <a name="about-object-creation"></a>Over het maken van objecten

## <a name="short-description"></a>Korte beschrijving

Hierin wordt uitgelegd hoe u objecten maakt in Power shell.

## <a name="long-description"></a>Lange beschrijving

U kunt objecten in Power shell maken en de objecten gebruiken die u in opdrachten en scripts hebt gemaakt.

Er zijn veel manieren om objecten te maken. deze lijst is niet definitief:

- [New-object](xref:Microsoft.PowerShell.Utility.New-Object): maakt een exemplaar van een .NET Framework-object of COM-object.
- [Import-CSV](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): maakt aangepaste objecten ( **PSCustomObject** ) van de items die zijn gedefinieerd als door komma's gescheiden waarden.
- [ConvertFrom-JSON](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): maakt aangepaste objecten gedefinieerd in JavaScript object NOTATION (JSON).
- [ConvertFrom-string](xref:Microsoft.PowerShell.Utility.ConvertFrom-String): gebouwd op [FlashExtract](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples), `ConvertFrom-String` maakt aangepaste objecten van gestructureerde teken reeks gegevens.
  In dit onderwerp wordt elk van deze methoden gedemonstreerd en besproken.
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): maakt aangepaste objecten die als sleutel-waardeparen zijn gedefinieerd.
- [Add-type](xref:Microsoft.PowerShell.Utility.Add-Type): Hiermee kunt u een klasse in uw Power shell-sessie definiëren waarmee u een exemplaar kunt maken `New-Object` .
- [New-module](xref:Microsoft.PowerShell.Core.New-Module): met de para meter **AsCustomObject** maakt u een aangepast object dat u definieert met behulp van een script blok.
- [Add-member](xref:Microsoft.PowerShell.Utility.Add-Member): voegt eigenschappen toe aan bestaande objecten. U kunt gebruiken `Add-Member` om een aangepast object van een eenvoudig type te maken, zoals `[System.Int32]` .
- [Select-object](xref:Microsoft.PowerShell.Utility.Select-Object): Hiermee selecteert u de eigenschappen van een object. U kunt gebruiken `Select-Object` om aangepaste en berekende eigenschappen te maken voor een object dat al is geïnstantieerd.

De volgende aanvullende methoden zijn opgenomen in dit artikel:

- Door de constructor van een type aan te roepen met behulp van een statische `new()` methode
- Door typecasting hash-tabellen van eigenschaps namen en eigenschaps waarden

## <a name="static-new-method"></a>Statische methode New ()

Alle .NET-typen hebben een `new()` methode waarmee u gemakkelijker instanties kunt bouwen. U kunt ook alle beschik bare constructors voor een bepaald type weer geven.

Als u de Constructors voor een type wilt zien, geeft u de naam van de `new` methode op na de naam van het type en drukt u op `<ENTER>` .

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

U kunt nu een **System. URI** maken door de juiste constructor op te geven.

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

U kunt het volgende voor beeld gebruiken om te bepalen welke .NET-typen op dit moment worden geladen om te instantiëren.

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

Objecten die zijn gemaakt met de `new()` methode, hebben mogelijk niet dezelfde eigenschappen als objecten van hetzelfde type die zijn gemaakt door Power shell-cmdlets. Power shell-cmdlets, providers en uitgebreid type systeem kunnen extra eigenschappen toevoegen aan het exemplaar.

Zo voegt de bestandssysteem provider in Power shell zes **NoteProperty** -waarden toe aan het **DirectoryInfo** -object dat wordt geretourneerd door `Get-Item` .

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

Wanneer u een **DirectoryInfo** -object rechtstreeks maakt, heeft dit niet de zes **NoteProperty** -waarden.

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

Zie voor meer informatie over het uitgebreide-type systeem [about_Types.ps1XML](about_Types.ps1xml.md).

Deze functie is toegevoegd in Power shell 5,0

## <a name="create-objects-from-hash-tables"></a>Objecten maken op basis van hash-tabellen

U kunt een object maken op basis van een hash-tabel met eigenschappen en eigenschaps waarden.

De syntaxis is als volgt:

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

Deze methode werkt alleen voor klassen die een constructor zonder para meters hebben. De object eigenschappen moeten openbaar en instelbaar zijn.

Deze functie is toegevoegd aan Power shell-versie 3,0

## <a name="create-custom-objects-from-hash-tables"></a>Aangepaste objecten maken op basis van hash-tabellen

Aangepaste objecten zijn erg nuttig en zijn gemakkelijk te maken met behulp van de hash-tabel methode. De **PSCustomObject** -klasse is speciaal ontworpen voor dit doel einde.

Aangepaste objecten zijn een uitstekende manier om een aangepaste uitvoer van een functie of script te retour neren. Dit is nuttiger dan de geretourneerde uitvoer die niet opnieuw kan worden geformatteerd of naar andere opdrachten kan worden gesluisd.

De opdrachten in de `Test-Object function` set variabele waarden en gebruiken deze waarden vervolgens om een aangepast object te maken. U ziet dit object in gebruik in de sectie voor beeld van het `Update-Help` Help-onderwerp van de cmdlet.

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

De uitvoer van deze functie is een verzameling aangepaste objecten die standaard zijn opgemaakt als een tabel.

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

Gebruikers kunnen de eigenschappen van de aangepaste objecten net als bij standaard objecten beheren.

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a>Niet-aangepaste objecten maken op basis van hash-tabellen

U kunt ook hash-tabellen gebruiken om objecten voor niet-aangepaste klassen te maken. Wanneer u een-object voor een niet-aangepaste klasse maakt, is de naam ruimte-gekwalificeerde typenaam vereist, maar u kunt ook een eerste **systeem** naam ruimte onderdeel weglaten.

Met de volgende opdracht wordt bijvoorbeeld een sessie optie object gemaakt.

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

De vereisten van de functie hash-tabel, met name de vereiste para meters voor constructors, elimineren veel bestaande klassen. De meeste Power shell- _optie_ klassen zijn echter ontworpen voor gebruik met deze functie en andere zeer nuttige klassen, zoals de **ProcessStartInfo** -klasse.

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

U kunt ook de functie hash table gebruiken bij het instellen van parameter waarden. Bijvoorbeeld, de waarde van de para meter **SessionOption** van de `New-PSSession` .
cmdlet kan een hash-tabel zijn.

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a>Algemene objecten

U kunt ook algemene objecten maken in Power shell. Algemene elementen zijn klassen, structuren, interfaces en methoden die tijdelijke aanduidingen (type para meters) hebben voor een of meer van de typen die ze opslaan of gebruiken.

In het volgende voor beeld wordt een **Dictionary** -object gemaakt.

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

Zie voor meer informatie over generieke [algemene gegevens in .net](/dotnet/standard/generics).

## <a name="see-also"></a>Zie ook

[about_Objects](about_Objects.md)

[about_Methods](about_Methods.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[about_Types.ps1XML](about_Types.ps1xml.md)
