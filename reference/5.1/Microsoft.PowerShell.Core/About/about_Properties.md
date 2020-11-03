---
description: Hierin wordt beschreven hoe u object eigenschappen gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: c8e711086922ea6a76978085a63380156591bb1d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252585"
---
# <a name="about-properties"></a>Over eigenschappen

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u object eigenschappen gebruikt in Power shell.

## <a name="long-description"></a>Lange beschrijving

Power shell gebruikt gestructureerde verzamelingen gegevens die objecten worden genoemd om de items in de gegevens archieven of de status van de computer weer te geven. Normaal gesp roken werkt u met een object dat deel uitmaakt van het Microsoft .NET Framework, maar u kunt ook aangepaste objecten maken in Power shell.

De koppeling tussen een item en het bijbehorende object is zeer dicht bij elkaar. Wanneer u een object wijzigt, wijzigt u meestal het item dat het vertegenwoordigt. Wanneer u bijvoorbeeld een bestand in Power shell ophaalt, krijgt u niet het daad werkelijke bestand. In plaats daarvan krijgt u een file info-object dat het bestand vertegenwoordigt. Wanneer u het file info-object wijzigt, wordt het bestand ook gewijzigd.

De meeste objecten hebben eigenschappen. Eigenschappen zijn de gegevens die aan een object zijn gekoppeld. Verschillende object typen hebben andere eigenschappen. Bijvoorbeeld een file info-object, dat een bestand vertegenwoordigt, een eigenschap **IsReadOnly** heeft die $True bevat als het bestand het kenmerk alleen-lezen heeft en $False als dit niet het geval is.
Een DirectoryInfo-object, dat een directory van het bestands systeem vertegenwoordigt, heeft een bovenliggende eigenschap die het pad naar de bovenliggende map bevat.

### <a name="object-properties"></a>Object eigenschappen

Als u de eigenschappen van een object wilt ophalen, gebruikt u de `Get-Member` cmdlet. Als u bijvoorbeeld de eigenschappen van een **file info** -object wilt ophalen, gebruikt u de `Get-ChildItem` cmdlet om het file info-object op te halen dat een bestand vertegenwoordigt. Gebruik vervolgens een pijplijn operator (&#124;) om het **file info** -object naar te verzenden `Get-Member` . Met de volgende opdracht wordt het PowerShell.exe-bestand opgehaald en verzonden naar `Get-Member` .
De \$ Automatische variabele Pshome bevat het pad van de installatie directory van Power shell.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

De uitvoer van de opdracht geeft een lijst van de leden van het object **file info** .
Leden bevatten zowel eigenschappen als methoden. Wanneer u in Power shell werkt, hebt u toegang tot alle leden van de objecten.

Als u alleen de eigenschappen van een object en niet de methoden wilt ophalen, gebruikt u de para meter member type van de `Get-Member` cmdlet met de waarde ' Property ', zoals in het volgende voor beeld wordt weer gegeven.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

Nadat u de eigenschappen hebt gevonden, kunt u deze gebruiken in uw Power shell-opdrachten.

## <a name="property-values"></a>Eigenschaps waarden

Hoewel elk object van een specifiek type dezelfde eigenschappen heeft, beschrijven de waarden van die eigenschappen het specifieke object. Elk file info-object heeft bijvoorbeeld een eigenschap CreationTime, maar de waarde van die eigenschap verschilt voor elk bestand.

De meest voorkomende manier om de waarden van de eigenschappen van een object op te halen, is door de punt methode te gebruiken. Typ een verwijzing naar het object, bijvoorbeeld een variabele die het object bevat, of een opdracht die het object ophaalt. Typ vervolgens een punt (.), gevolgd door de naam van de eigenschap.

Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap CreationTime van het PowerShell.exe-bestand weer gegeven. De `Get-ChildItem` opdracht retourneert een file info-object dat het PowerShell.exe bestand vertegenwoordigt. De opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze wordt uitgevoerd voordat er eigenschappen worden geopend. De `Get-ChildItem` opdracht wordt als volgt gevolgd door een punt en de naam van de eigenschap CreationTime:

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

U kunt ook een object opslaan in een variabele en vervolgens de eigenschappen ophalen met behulp van de punt methode, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

U kunt ook de `Select-Object` `Format-List` cmdlets en gebruiken om de eigenschaps waarden van een object weer te geven. `Select-Object` en `Format-List` elk hebben een **eigenschaps** parameter. U kunt de para meter **Property** gebruiken om een of meer eigenschappen en hun waarden op te geven. U kunt ook het Joker teken () gebruiken \* om alle eigenschappen weer te geven.

Met de volgende opdracht worden bijvoorbeeld de waarden van alle eigenschappen van het PowerShell.exe-bestand weer gegeven.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a>Statische eigenschappen

U kunt de statische eigenschappen van .NET-klassen gebruiken in Power shell. Statische eigenschappen zijn eigenschappen van klasse, in tegens telling tot standaard eigenschappen, die eigenschappen van een object zijn.

Als u de statische eigenschappen van een klasse wilt ophalen, gebruikt u de statische para meter van de cmdlet Get-Member.

Met de volgende opdracht worden bijvoorbeeld de statische eigenschappen van de `System.DateTime` klasse opgehaald.

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

Als u de waarde van een statische eigenschap wilt ophalen, gebruikt u de volgende syntaxis.

```
[<ClassName>]::<Property>
```

Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap UtcNow static van de `System.DateTime` klasse opgehaald.

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a>Eigenschappen van scalaire objecten en verzamelingen

De eigenschappen van een object ("scalair") van een bepaald type zijn vaak anders dan de eigenschappen van een verzameling objecten van hetzelfde type.
Elke service heeft bijvoorbeeld de eigenschap **DisplayName** , maar een verzameling services heeft geen eigenschap **DisplayName** .

Met de volgende opdracht wordt de waarde van de eigenschap **DisplayName** van de service ' AudioSrv ' opgehaald.

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

Vanaf Power Shell 3,0 probeert Power shell script fouten te voor komen die het resultaat zijn van de verschillende eigenschappen van scalaire objecten en verzamelingen. Dezelfde opdracht retourneert de waarde van de eigenschap **DisplayName** van elke service die `Get-Service` retourneert.

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

Wanneer u een verzameling verzendt, maar een eigenschap aanvraagt die alleen voor één (' scalaire ') objecten bestaat, retourneert Power shell de waarde van die eigenschap voor elk object in de verzameling.

Alle verzamelingen hebben een eigenschap **Count** die het aantal objecten in de verzameling retourneert.

```powershell
(Get-Service).Count
```

```output
176
```

Als u vanaf Power Shell 3,0 de eigenschap Count of length van nul objecten of één object aanvraagt, retourneert Power shell de juiste waarde.

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

Als er een eigenschap bestaat voor de afzonderlijke objecten en de verzameling, wordt alleen de eigenschap van de verzameling geretourneerd.

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

Deze functie werkt ook met methoden van scalaire objecten en verzamelingen. Zie [about_Methods](about_methods.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Methods](about_Methods.md)

[about_Objects](about_Objects.md)

[Get-member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)
