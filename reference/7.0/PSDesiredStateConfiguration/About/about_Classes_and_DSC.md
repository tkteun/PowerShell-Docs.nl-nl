---
description: Hierin wordt beschreven hoe u klassen kunt gebruiken om te ontwikkelen in Power shell met desired state Configuration (DSC).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: 00a7d18bb1ccf618b22b61d2197053365ea3f21b
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349786"
---
# <a name="about-classes-and-desired-state-configuration"></a>Informatie over klassen en desired state Configuration

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe u klassen kunt gebruiken om te ontwikkelen in Power shell met desired state Configuration (DSC).

## <a name="long-description"></a>Lange beschrijving

Met ingang van Windows Power shell 5,0 is de taal toegevoegd om klassen en andere door de gebruiker gedefinieerde typen te definiëren, door gebruik te maken van formele syntaxis en semantiek die vergelijkbaar zijn met andere object georiënteerde programmeer talen. Het doel is om ontwikkel aars en IT-professionals in staat te stellen Power shell te gebruiken voor een breder scala aan gebruiks voorbeelden, de ontwikkeling van Power shell-artefacten, zoals DSC-resources, te vereenvoudigen en de dekking van management-Opper vlakken te versnellen.

## <a name="supported-scenarios"></a>Ondersteunde scenario's

De volgende scenario's worden ondersteund:

- DSC-resources en de bijbehorende typen definiëren met behulp van de Power shell-taal.
- Definieer aangepaste typen in Power shell met behulp van vertrouwde object georiënteerde Programmeer constructies, zoals klassen, eigenschappen, methoden en overname.
- Typen fout opsporing met behulp van de Power shell-taal.
- U kunt uitzonde ringen genereren en verwerken door formele mechanismen te gebruiken en op het juiste niveau.

## <a name="define-dsc-resources-with-classes"></a>DSC-resources definiëren met klassen

Naast de syntaxis wijzigingen, zijn de belangrijkste verschillen tussen een door een klasse gedefinieerde DSC-resource en een cmdlet DSC resource provider de volgende items:

- Een MOF-bestand (Management Object Format) is niet vereist.
- Een Dscresource bieden-submap in de module map is niet vereist.
- Een Power shell-module bestand kan meerdere DSC-resource klassen bevatten.

## <a name="create-a-class-defined-dsc-resource-provider"></a>Een door een klasse gedefinieerde DSC-resource provider maken

Het volgende voor beeld is een door een klasse gedefinieerde DSC-resource provider die is opgeslagen als een module, MyDSCResource. psm1. U moet altijd een sleutel eigenschap in een door klasse gedefinieerde DSC-resource provider toevoegen.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
    This resource manages the file in a specific path.
    [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
        This property is the fully qualified path to the file that is
        expected to be present or absent.

        The [DscProperty(Key)] attribute indicates the property is a
        key and its value uniquely identifies a resource instance.
        Defining this attribute also means the property is required
        and DSC will ensure a value is set before calling the resource.

        A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
        This property defines the fully qualified path to a file that will
        be placed on the system if $Ensure = Present and $Path does not
        exist.

        NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
        This property reports the file's create timestamp.

        [DscProperty(NotConfigurable)] attribute indicates the property is
        not configurable in DSC configuration.  Properties marked this way
        are populated by the Get() method to report additional details
        about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
{
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }
        return $this
    }

    <#
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($null -eq $item)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }
        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a>Een module manifest maken

Maak na het maken van de door de klasse gedefinieerde DSC-resource provider een module manifest voor de module en sla het op als een module. Als u een op een klasse gebaseerde resource beschikbaar wilt maken voor de DSC-engine, moet u een `DscResourcesToExport` instructie in het manifest bestand toevoegen die de module de opdracht geeft de resource te exporteren. In dit voor beeld wordt het volgende module manifest opgeslagen als MyDscResource.psd1.

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a>Een DSC-resource provider implementeren

Implementeer de nieuwe DSC-resource provider door een MyDscResource-map in `$pshome\Modules` of te maken `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .

U hoeft geen submap Dscresource bieden te maken. Kopieer de module-en module manifest bestanden (MyDscResource. psm1 en MyDscResource.psd1) naar de map MyDscResource.

Vanaf dit punt maakt en voert u een configuratie script uit zoals u dat zou doen met een DSC-resource.

## <a name="create-a-dsc-configuration-script"></a>Een DSC-configuratiescript maken

Nadat u de klasse en de manifest bestanden in de mappen structuur hebt opgeslagen zoals eerder beschreven, kunt u een configuratie maken die gebruikmaakt van de nieuwe resource. De volgende configuratie verwijst naar de MyDSCResource-module. Sla de configuratie op als een script, MyResource.ps1.

Voor informatie over het uitvoeren van een DSC-configuratie raadpleegt u [Windows Power shell desired state Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers)(Engelstalig).

Voordat u de configuratie uitvoert, maakt u `C:\test.txt` . De configuratie controleert of het bestand bestaat op `c:\test\test.txt` . Als het bestand niet bestaat, kopieert de configuratie het bestand van `C:\test.txt` .

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

Voer dit script uit zoals u een DSC-configuratie script zou uitvoeren. Als u de configuratie wilt starten, voert u in een Power shell-console met verhoogde bevoegdheid de volgende opdracht uit:

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a>Overname in Power shell-klassen

### <a name="declare-base-classes-for-powershell-classes"></a>Basis klassen voor Power shell-klassen declareren

U kunt een Power shell-klasse declareren als basis type voor een andere Power shell-klasse, zoals wordt weer gegeven in het volgende voor beeld, waarbij **fruit** een basis type is voor **Apple**.

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a>Geïmplementeerde interfaces voor Power shell-klassen declareren

U kunt geïmplementeerde interfaces na basis typen of direct na een dubbele punt ( `:` ) declareren als er geen basis type is opgegeven. Scheid alle type namen met behulp van komma's. Dit is vergelijkbaar met de syntaxis van C#.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a>Constructors van basis klasse aanroepen

Als u een basis klasse-constructor wilt aanroepen vanuit een subklasse, voegt u het `base` tref woord toe, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
class A {
    [int]$a
    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

    [B]::new().a # return 103
```

Als een basis klasse een standaardconstructor (zonder para meters) heeft, kunt u een expliciete aanroep van een constructor weglaten, zoals wordt weer gegeven.

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a>Methoden van basis klasse aanroepen

U kunt bestaande methoden in subklassen overschrijven. Als u de onderdrukking wilt uitvoeren, declareert u methoden met dezelfde naam en hand tekening.

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

Als u basis klassen methoden wilt aanroepen vanuit overschreven implementaties, moet u deze op de basis klasse `([baseclass]$this)` bij het aanroepen casten.

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

Alle Power shell-methoden zijn virtueel. U kunt niet-virtuele .NET-methoden in een subklasse verbergen door dezelfde syntaxis te gebruiken als voor een onderdrukking: Declareer methoden met dezelfde naam en hand tekening.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="current-limitations-with-class-inheritance"></a>Huidige beperkingen met betrekking tot klasse-overname

Een beperking met een klasse-overname is dat er geen syntaxis is voor het declareren van interfaces in Power shell.

## <a name="defining-custom-types-in-powershell"></a>Aangepaste typen definiëren in Power shell

Windows Power shell 5,0 heeft verschillende taal elementen geïntroduceerd.

### <a name="class-keyword"></a>Tref woord klasse

Hiermee definieert u een nieuwe klasse.
Het `class` sleutel woord is een True-.NET Framework type.
Klasse-leden zijn openbaar.

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a>Tref woord en opsommingen inventariseren

Ondersteuning voor het `enum` tref woord is toegevoegd en is een belang rijke wijziging. Het `enum` scheidings teken is momenteel een nieuwe regel. Een tijdelijke oplossing voor degenen die al worden gebruikt `enum` , is het invoegen van een ampersand ( `&` ) voor het woord. Huidige beperkingen: u kunt een enumerator niet definiëren in termen van zichzelf, maar initialisatie van `enum` de voor waarden van een andere `enum` , zoals wordt weer gegeven in het volgende voor beeld:

Het basis type kan momenteel niet worden opgegeven. Het basis type is altijd [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Een enumerator-waarde moet een geparseerd tijd constante zijn. De enumerator-waarde kan niet worden ingesteld op het resultaat van een aangeroepen opdracht.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

`Enum` ondersteunt reken kundige bewerkingen, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a>Verborgen tref woord

Met het `hidden` sleutel woord dat is geïntroduceerd in Windows Power shell 5,0, worden klasse-leden verborgen op basis van standaard `Get-Member` resultaten. Geef de verborgen eigenschap op zoals weer gegeven op de volgende regel:

```powershell
hidden [type] $classmember = <value>
```

Verborgen leden worden niet weer gegeven met behulp van Tab-aanvulling of IntelliSense, tenzij de voltooiing plaatsvindt in de klasse die het verborgen lid definieert.

Er is een nieuw kenmerk, **System. Management. Automation. HiddenAttribute**, toegevoegd, zodat C#-code dezelfde semantiek kan hebben in Power shell.

Zie [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)voor meer informatie.

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` is nu een echt dynamisch sleutel woord. Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk Dscresource bieden bevatten.

### <a name="properties"></a>Eigenschappen

Er is een nieuw veld, `ImplementingAssembly` , toegevoegd aan `ModuleInfo` . Als het script klassen definieert, of als de geladen assembly voor binaire modules `ImplementingAssembly` is ingesteld op de dynamische assembly die is gemaakt voor een script module. Deze is niet ingesteld als module type = manifest.

Reflectie op het `ImplementingAssembly` veld Hiermee worden bronnen in een module gedetecteerd. Dit betekent dat u resources kunt detecteren die in Power shell of andere beheerde talen zijn geschreven.

Velden met initialisatie functies.

`[int] $i = 5`

Statisch wordt ondersteund en werkt als een kenmerk, vergelijkbaar met de type beperkingen, zodat het kan worden opgegeven in een wille keurige volg orde.

`static [int] $count = 0`

Een type is optioneel.

`$s = "hello"`

Alle leden zijn openbaar. Eigenschappen vereisen een nieuwe regel of een punt komma. Als er geen object type is opgegeven, is het eigenschaps type **object**.

### <a name="constructors-and-instantiation"></a>Constructors en instantiëring

Power shell-klassen kunnen constructors hebben die dezelfde naam hebben als hun klasse. Constructors kunnen overbelast zijn. Statische Constructors worden ondersteund.
Eigenschappen met initialisatie-expressies worden geïnitialiseerd voordat code in een constructor wordt uitgevoerd. Statische eigenschappen worden geïnitialiseerd voordat de hoofd tekst van een statische constructor, en instantie-eigenschappen worden geïnitialiseerd vóór de hoofd tekst van de niet-statische constructor. Er is momenteel geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor, zoals de C#-syntaxis: `": this()")` . De tijdelijke oplossing is het definiëren van een algemene init-methode.

Hier volgen enkele manieren waarop u klassen kunt instantiëren:

- Instantiëren met behulp van de standaardconstructor. Opmerking: `New-Object` wordt niet ondersteund in deze release.

  `$a = [MyClass]::new()`

- Een constructor met een para meter aanroepen.

  `$b = [MyClass]::new(42)`

- Een matrix door geven aan een constructor met meerdere para meters

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

Voor deze release is de type naam alleen lexicalief zichtbaar, wat betekent dat deze niet zichtbaar is buiten de module of het script waarmee de klasse wordt gedefinieerd. Functies kunnen exemplaren retour neren van een klasse die is gedefinieerd in Power shell, en instanties werken goed buiten de module of het script.

Met de `Get-Member` **statische** para meters worden constructors weer gegeven, zodat u Overloads op dezelfde manier kunt bekijken als andere methoden. De prestaties van deze syntaxis zijn ook aanzienlijk sneller dan `New-Object` .

De pseudo-statische methode met de naam **New** werkt met .net-typen, zoals wordt weer gegeven in het volgende voor beeld. `[hashtable]::new()`

U kunt nu overbelasting van constructor zien met `Get-Member` , of zoals in dit voor beeld wordt weer gegeven:

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a>Methoden

Een Power shell-klassen methode wordt geïmplementeerd als een **script Block** die alleen een eind blok heeft. Alle methoden zijn openbaar. Hieronder ziet u een voor beeld van het definiëren van een methode met de naam **DoSomething**.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a>Methode aanroep

Overbelaste methoden worden ondersteund. Overbelaste methoden hebben dezelfde naam als een bestaande methode, maar worden gedifferentieerd met de opgegeven waarden.

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a>Aanroep

Zie [methode aanroep](#method-invocation).

### <a name="attributes"></a>Kenmerken

Er zijn drie nieuwe kenmerken toegevoegd: `DscResource` , `DscResourceKey` en `DscResourceMandatory` .

### <a name="return-types"></a>Retour typen

Retour type is een contract. De geretourneerde waarde wordt geconverteerd naar het verwachte type.
Als er geen retour type is opgegeven, is het retour type void. Het streamen van objecten en objecten kan niet opzettelijk of per ongeluk naar de pijp lijn worden geschreven.

### <a name="lexical-scoping-of-variables"></a>Lexicale bereik van variabelen

Hieronder ziet u een voor beeld van hoe lexicale scoping werkt in deze release.

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a>Voor beeld: aangepaste klassen maken

In het volgende voor beeld worden verschillende nieuwe aangepaste klassen gemaakt om een HTML Dynamic Style Sheet Language (DSL) te implementeren. In het voor beeld worden hulp functies toegevoegd om specifieke element typen te maken als onderdeel van de klasse element, zoals kopstijlen en tabellen, omdat typen niet buiten het bereik van een module kunnen worden gebruikt.

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
function HREF
{
    param (
        $Name,
        $Link
    )

    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
        [Parameter(Mandatory)]
        [object[]]
            $Data,
        [Parameter()]
        [string[]]
            $Properties = "*",
        [Parameter()]
        [hashtable]
            $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )

    $bodyText = ""
    # Add the header tags
    $bodyText +=  $Properties.foreach{TH $_}
    # Add the rows
    $bodyText += foreach ($row in $Data)
                {
                            TR (-join $Properties.Foreach{ TD ($row.$_) } )
                }

    $table = [Element] @{
                Tag = "Table"
                Attributes = $Attributes
                Text = $bodyText
            }
    $table
}
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a>Zie ook

[about_Enum](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Methods](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[Aangepaste Power shell-configuratie bronnen voor desired state bouwen](/powershell/scripting/dsc/resources/authoringResource)
