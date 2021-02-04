---
description: Hierin wordt beschreven hoe u klassen kunt gebruiken om te ontwikkelen in Power shell met desired state Configuration (DSC).
Locale: en-US
ms.date: 01/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: a5819ac54f34393e0fbbf3b8933e840730c5d827
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349875"
---
# <a name="about-classes-and-desired-state-configuration"></a><span data-ttu-id="0ac44-103">Informatie over klassen en desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="0ac44-103">About Classes and Desired State Configuration</span></span>

## <a name="short-description"></a><span data-ttu-id="0ac44-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="0ac44-104">Short description</span></span>

<span data-ttu-id="0ac44-105">Hierin wordt beschreven hoe u klassen kunt gebruiken om te ontwikkelen in Power shell met desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="0ac44-105">Describes how you can use classes to develop in PowerShell with Desired State Configuration (DSC).</span></span>

## <a name="long-description"></a><span data-ttu-id="0ac44-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="0ac44-106">Long description</span></span>

<span data-ttu-id="0ac44-107">Met ingang van Windows Power shell 5,0 is de taal toegevoegd om klassen en andere door de gebruiker gedefinieerde typen te definiëren, door gebruik te maken van formele syntaxis en semantiek die vergelijkbaar zijn met andere object georiënteerde programmeer talen.</span><span class="sxs-lookup"><span data-stu-id="0ac44-107">Starting in Windows PowerShell 5.0, language was added to define classes and other user-defined types, by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="0ac44-108">Het doel is om ontwikkel aars en IT-professionals in staat te stellen Power shell te gebruiken voor een breder scala aan gebruiks voorbeelden, de ontwikkeling van Power shell-artefacten, zoals DSC-resources, te vereenvoudigen en de dekking van management-Opper vlakken te versnellen.</span><span class="sxs-lookup"><span data-stu-id="0ac44-108">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts such as DSC resources, and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="0ac44-109">Ondersteunde scenario's</span><span class="sxs-lookup"><span data-stu-id="0ac44-109">Supported scenarios</span></span>

<span data-ttu-id="0ac44-110">De volgende scenario's worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="0ac44-110">The following scenarios are supported:</span></span>

- <span data-ttu-id="0ac44-111">DSC-resources en de bijbehorende typen definiëren met behulp van de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="0ac44-111">Define DSC resources and their associated types by using the PowerShell language.</span></span>
- <span data-ttu-id="0ac44-112">Definieer aangepaste typen in Power shell met behulp van vertrouwde object georiënteerde Programmeer constructies, zoals klassen, eigenschappen, methoden en overname.</span><span class="sxs-lookup"><span data-stu-id="0ac44-112">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, and inheritance.</span></span>
- <span data-ttu-id="0ac44-113">Typen fout opsporing met behulp van de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="0ac44-113">Debug types by using the PowerShell language.</span></span>
- <span data-ttu-id="0ac44-114">U kunt uitzonde ringen genereren en verwerken door formele mechanismen te gebruiken en op het juiste niveau.</span><span class="sxs-lookup"><span data-stu-id="0ac44-114">Generate and handle exceptions by using formal mechanisms, and at the right level.</span></span>

## <a name="define-dsc-resources-with-classes"></a><span data-ttu-id="0ac44-115">DSC-resources definiëren met klassen</span><span class="sxs-lookup"><span data-stu-id="0ac44-115">Define DSC resources with classes</span></span>

<span data-ttu-id="0ac44-116">Naast de syntaxis wijzigingen, zijn de belangrijkste verschillen tussen een door een klasse gedefinieerde DSC-resource en een cmdlet DSC resource provider de volgende items:</span><span class="sxs-lookup"><span data-stu-id="0ac44-116">Apart from syntax changes, the major differences between a class-defined DSC resource and a cmdlet DSC resource provider are the following items:</span></span>

- <span data-ttu-id="0ac44-117">Een MOF-bestand (Management Object Format) is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="0ac44-117">A Management Object Format (MOF) file is not required.</span></span>
- <span data-ttu-id="0ac44-118">Een Dscresource bieden-submap in de module map is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="0ac44-118">A DSCResource subfolder in the module folder is not required.</span></span>
- <span data-ttu-id="0ac44-119">Een Power shell-module bestand kan meerdere DSC-resource klassen bevatten.</span><span class="sxs-lookup"><span data-stu-id="0ac44-119">A PowerShell module file can contain multiple DSC resource classes.</span></span>

## <a name="create-a-class-defined-dsc-resource-provider"></a><span data-ttu-id="0ac44-120">Een door een klasse gedefinieerde DSC-resource provider maken</span><span class="sxs-lookup"><span data-stu-id="0ac44-120">Create a class-defined DSC resource provider</span></span>

<span data-ttu-id="0ac44-121">Het volgende voor beeld is een door een klasse gedefinieerde DSC-resource provider die is opgeslagen als een module, MyDSCResource. psm1.</span><span class="sxs-lookup"><span data-stu-id="0ac44-121">The following example is a class-defined DSC resource provider that is saved as a module, MyDSCResource.psm1.</span></span> <span data-ttu-id="0ac44-122">U moet altijd een sleutel eigenschap in een door klasse gedefinieerde DSC-resource provider toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0ac44-122">You must always include a key property in a class-defined DSC resource provider.</span></span>

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

## <a name="create-a-module-manifest"></a><span data-ttu-id="0ac44-123">Een module manifest maken</span><span class="sxs-lookup"><span data-stu-id="0ac44-123">Create a module manifest</span></span>

<span data-ttu-id="0ac44-124">Maak na het maken van de door de klasse gedefinieerde DSC-resource provider een module manifest voor de module en sla het op als een module.</span><span class="sxs-lookup"><span data-stu-id="0ac44-124">After creating the class-defined DSC resource provider, and saving it as a module, create a module manifest for the module.</span></span> <span data-ttu-id="0ac44-125">Als u een op een klasse gebaseerde resource beschikbaar wilt maken voor de DSC-engine, moet u een `DscResourcesToExport` instructie in het manifest bestand toevoegen die de module de opdracht geeft de resource te exporteren.</span><span class="sxs-lookup"><span data-stu-id="0ac44-125">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="0ac44-126">In dit voor beeld wordt het volgende module manifest opgeslagen als MyDscResource.psd1.</span><span class="sxs-lookup"><span data-stu-id="0ac44-126">In this example, the following module manifest is saved as MyDscResource.psd1.</span></span>

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

## <a name="deploy-a-dsc-resource-provider"></a><span data-ttu-id="0ac44-127">Een DSC-resource provider implementeren</span><span class="sxs-lookup"><span data-stu-id="0ac44-127">Deploy a DSC resource provider</span></span>

<span data-ttu-id="0ac44-128">Implementeer de nieuwe DSC-resource provider door een MyDscResource-map in `$pshome\Modules` of te maken `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-128">Deploy the new DSC resource provider by creating a MyDscResource folder in `$pshome\Modules` or `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="0ac44-129">U hoeft geen submap Dscresource bieden te maken.</span><span class="sxs-lookup"><span data-stu-id="0ac44-129">You do not need to create a DSCResource subfolder.</span></span> <span data-ttu-id="0ac44-130">Kopieer de module-en module manifest bestanden (MyDscResource. psm1 en MyDscResource.psd1) naar de map MyDscResource.</span><span class="sxs-lookup"><span data-stu-id="0ac44-130">Copy the module and module manifest files (MyDscResource.psm1 and MyDscResource.psd1) to the MyDscResource folder.</span></span>

<span data-ttu-id="0ac44-131">Vanaf dit punt maakt en voert u een configuratie script uit zoals u dat zou doen met een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="0ac44-131">From this point, you create and run a configuration script as you would with any DSC resource.</span></span>

## <a name="create-a-dsc-configuration-script"></a><span data-ttu-id="0ac44-132">Een DSC-configuratiescript maken</span><span class="sxs-lookup"><span data-stu-id="0ac44-132">Create a DSC configuration script</span></span>

<span data-ttu-id="0ac44-133">Nadat u de klasse en de manifest bestanden in de mappen structuur hebt opgeslagen zoals eerder beschreven, kunt u een configuratie maken die gebruikmaakt van de nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="0ac44-133">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="0ac44-134">De volgende configuratie verwijst naar de MyDSCResource-module.</span><span class="sxs-lookup"><span data-stu-id="0ac44-134">The following configuration references the MyDSCResource module.</span></span> <span data-ttu-id="0ac44-135">Sla de configuratie op als een script, MyResource.ps1.</span><span class="sxs-lookup"><span data-stu-id="0ac44-135">Save the configuration as a script, MyResource.ps1.</span></span>

<span data-ttu-id="0ac44-136">Voor informatie over het uitvoeren van een DSC-configuratie raadpleegt u [Windows Power shell desired state Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers)(Engelstalig).</span><span class="sxs-lookup"><span data-stu-id="0ac44-136">For information about how to run a DSC configuration, see [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers).</span></span>

<span data-ttu-id="0ac44-137">Voordat u de configuratie uitvoert, maakt u `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-137">Before you run the configuration, create `C:\test.txt`.</span></span> <span data-ttu-id="0ac44-138">De configuratie controleert of het bestand bestaat op `c:\test\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-138">The configuration checks if the file exists at `c:\test\test.txt`.</span></span> <span data-ttu-id="0ac44-139">Als het bestand niet bestaat, kopieert de configuratie het bestand van `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-139">If the file does not exist, the configuration copies the file from `C:\test.txt`.</span></span>

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

<span data-ttu-id="0ac44-140">Voer dit script uit zoals u een DSC-configuratie script zou uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0ac44-140">Run this script as you would any DSC configuration script.</span></span> <span data-ttu-id="0ac44-141">Als u de configuratie wilt starten, voert u in een Power shell-console met verhoogde bevoegdheid de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="0ac44-141">To start the configuration, in an elevated PowerShell console, run the following:</span></span>

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="0ac44-142">Overname in Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="0ac44-142">Inheritance in PowerShell classes</span></span>

### <a name="declare-base-classes-for-powershell-classes"></a><span data-ttu-id="0ac44-143">Basis klassen voor Power shell-klassen declareren</span><span class="sxs-lookup"><span data-stu-id="0ac44-143">Declare base classes for PowerShell classes</span></span>

<span data-ttu-id="0ac44-144">U kunt een Power shell-klasse declareren als basis type voor een andere Power shell-klasse, zoals wordt weer gegeven in het volgende voor beeld, waarbij **fruit** een basis type is voor **Apple**.</span><span class="sxs-lookup"><span data-stu-id="0ac44-144">You can declare a PowerShell class as a base type for another PowerShell class, as shown in the following example, in which **fruit** is a base type for **apple**.</span></span>

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a><span data-ttu-id="0ac44-145">Geïmplementeerde interfaces voor Power shell-klassen declareren</span><span class="sxs-lookup"><span data-stu-id="0ac44-145">Declare implemented interfaces for PowerShell classes</span></span>

<span data-ttu-id="0ac44-146">U kunt geïmplementeerde interfaces na basis typen of direct na een dubbele punt ( `:` ) declareren als er geen basis type is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0ac44-146">You can declare implemented interfaces after base types, or immediately after a colon (`:`) if there is no base type specified.</span></span> <span data-ttu-id="0ac44-147">Scheid alle type namen met behulp van komma's.</span><span class="sxs-lookup"><span data-stu-id="0ac44-147">Separate all type names by using commas.</span></span> <span data-ttu-id="0ac44-148">Dit is vergelijkbaar met de syntaxis van C#.</span><span class="sxs-lookup"><span data-stu-id="0ac44-148">This is similar to C# syntax.</span></span>

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

### <a name="call-base-class-constructors"></a><span data-ttu-id="0ac44-149">Constructors van basis klasse aanroepen</span><span class="sxs-lookup"><span data-stu-id="0ac44-149">Call base class constructors</span></span>

<span data-ttu-id="0ac44-150">Als u een basis klasse-constructor wilt aanroepen vanuit een subklasse, voegt u het `base` tref woord toe, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="0ac44-150">To call a base class constructor from a subclass, add the `base` keyword, as shown in the following example:</span></span>

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

<span data-ttu-id="0ac44-151">Als een basis klasse een standaardconstructor (zonder para meters) heeft, kunt u een expliciete aanroep van een constructor weglaten, zoals wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0ac44-151">If a base class has a default constructor (no parameters), you can omit an explicit constructor call, as shown.</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a><span data-ttu-id="0ac44-152">Methoden van basis klasse aanroepen</span><span class="sxs-lookup"><span data-stu-id="0ac44-152">Call base class methods</span></span>

<span data-ttu-id="0ac44-153">U kunt bestaande methoden in subklassen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="0ac44-153">You can override existing methods in subclasses.</span></span> <span data-ttu-id="0ac44-154">Als u de onderdrukking wilt uitvoeren, declareert u methoden met dezelfde naam en hand tekening.</span><span class="sxs-lookup"><span data-stu-id="0ac44-154">To do the override, declare methods by using the same name and signature.</span></span>

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

<span data-ttu-id="0ac44-155">Als u basis klassen methoden wilt aanroepen vanuit overschreven implementaties, moet u deze op de basis klasse `([baseclass]$this)` bij het aanroepen casten.</span><span class="sxs-lookup"><span data-stu-id="0ac44-155">To call base class methods from overridden implementations, cast to the base class `([baseclass]$this)` on invocation.</span></span>

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

<span data-ttu-id="0ac44-156">Alle Power shell-methoden zijn virtueel.</span><span class="sxs-lookup"><span data-stu-id="0ac44-156">All PowerShell methods are virtual.</span></span> <span data-ttu-id="0ac44-157">U kunt niet-virtuele .NET-methoden in een subklasse verbergen door dezelfde syntaxis te gebruiken als voor een onderdrukking: Declareer methoden met dezelfde naam en hand tekening.</span><span class="sxs-lookup"><span data-stu-id="0ac44-157">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: declare methods with same name and signature.</span></span>

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

### <a name="current-limitations-with-class-inheritance"></a><span data-ttu-id="0ac44-158">Huidige beperkingen met betrekking tot klasse-overname</span><span class="sxs-lookup"><span data-stu-id="0ac44-158">Current limitations with class inheritance</span></span>

<span data-ttu-id="0ac44-159">Een beperking met een klasse-overname is dat er geen syntaxis is voor het declareren van interfaces in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0ac44-159">A limitation with class inheritance is that there is no syntax to declare interfaces in PowerShell.</span></span>

## <a name="defining-custom-types-in-powershell"></a><span data-ttu-id="0ac44-160">Aangepaste typen definiëren in Power shell</span><span class="sxs-lookup"><span data-stu-id="0ac44-160">Defining custom types in PowerShell</span></span>

<span data-ttu-id="0ac44-161">Windows Power shell 5,0 heeft verschillende taal elementen geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="0ac44-161">Windows PowerShell 5.0 introduced several language elements.</span></span>

### <a name="class-keyword"></a><span data-ttu-id="0ac44-162">Tref woord klasse</span><span class="sxs-lookup"><span data-stu-id="0ac44-162">Class keyword</span></span>

<span data-ttu-id="0ac44-163">Hiermee definieert u een nieuwe klasse.</span><span class="sxs-lookup"><span data-stu-id="0ac44-163">Defines a new class.</span></span>
<span data-ttu-id="0ac44-164">Het `class` sleutel woord is een True-.NET Framework type.</span><span class="sxs-lookup"><span data-stu-id="0ac44-164">The `class` keyword is a true .NET Framework type.</span></span>
<span data-ttu-id="0ac44-165">Klasse-leden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="0ac44-165">Class members are public.</span></span>

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="0ac44-166">Tref woord en opsommingen inventariseren</span><span class="sxs-lookup"><span data-stu-id="0ac44-166">Enum keyword and enumerations</span></span>

<span data-ttu-id="0ac44-167">Ondersteuning voor het `enum` tref woord is toegevoegd en is een belang rijke wijziging.</span><span class="sxs-lookup"><span data-stu-id="0ac44-167">Support for the `enum` keyword was added and is a breaking change.</span></span> <span data-ttu-id="0ac44-168">Het `enum` scheidings teken is momenteel een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="0ac44-168">The `enum` delimiter is currently a newline.</span></span> <span data-ttu-id="0ac44-169">Een tijdelijke oplossing voor degenen die al worden gebruikt `enum` , is het invoegen van een ampersand ( `&` ) voor het woord.</span><span class="sxs-lookup"><span data-stu-id="0ac44-169">A workaround for those who are already using `enum` is to insert an ampersand (`&`) before the word.</span></span> <span data-ttu-id="0ac44-170">Huidige beperkingen: u kunt een enumerator niet definiëren in termen van zichzelf, maar initialisatie van `enum` de voor waarden van een andere `enum` , zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="0ac44-170">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize `enum` in terms of another `enum`, as shown in the following example:</span></span>

<span data-ttu-id="0ac44-171">Het basis type kan momenteel niet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0ac44-171">The base type cannot currently be specified.</span></span> <span data-ttu-id="0ac44-172">Het basis type is altijd [int].</span><span class="sxs-lookup"><span data-stu-id="0ac44-172">The base type is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="0ac44-173">Een enumerator-waarde moet een geparseerd tijd constante zijn.</span><span class="sxs-lookup"><span data-stu-id="0ac44-173">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="0ac44-174">De enumerator-waarde kan niet worden ingesteld op het resultaat van een aangeroepen opdracht.</span><span class="sxs-lookup"><span data-stu-id="0ac44-174">The enumerator value cannot be set to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="0ac44-175">`Enum` ondersteunt reken kundige bewerkingen, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="0ac44-175">`Enum` supports arithmetic operations, as shown in the following example:</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a><span data-ttu-id="0ac44-176">Verborgen tref woord</span><span class="sxs-lookup"><span data-stu-id="0ac44-176">Hidden keyword</span></span>

<span data-ttu-id="0ac44-177">Met het `hidden` sleutel woord dat is geïntroduceerd in Windows Power shell 5,0, worden klasse-leden verborgen op basis van standaard `Get-Member` resultaten.</span><span class="sxs-lookup"><span data-stu-id="0ac44-177">The `hidden` keyword, introduced in Windows PowerShell 5.0, hides class members from default `Get-Member` results.</span></span> <span data-ttu-id="0ac44-178">Geef de verborgen eigenschap op zoals weer gegeven op de volgende regel:</span><span class="sxs-lookup"><span data-stu-id="0ac44-178">Specify the hidden property as shown in the following line:</span></span>

```powershell
hidden [type] $classmember = <value>
```

<span data-ttu-id="0ac44-179">Verborgen leden worden niet weer gegeven met behulp van Tab-aanvulling of IntelliSense, tenzij de voltooiing plaatsvindt in de klasse die het verborgen lid definieert.</span><span class="sxs-lookup"><span data-stu-id="0ac44-179">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="0ac44-180">Er is een nieuw kenmerk, **System. Management. Automation. HiddenAttribute**, toegevoegd, zodat C#-code dezelfde semantiek kan hebben in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0ac44-180">A new attribute, **System.Management.Automation.HiddenAttribute**, was added, so that C# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="0ac44-181">Zie [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0ac44-181">For more information, see [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span></span>

### <a name="import-dscresource"></a><span data-ttu-id="0ac44-182">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="0ac44-182">Import-DscResource</span></span>

<span data-ttu-id="0ac44-183">`Import-DscResource` is nu een echt dynamisch sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="0ac44-183">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="0ac44-184">Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk Dscresource bieden bevatten.</span><span class="sxs-lookup"><span data-stu-id="0ac44-184">PowerShell parses the specified module's root module, searching for classes that contain the DscResource attribute.</span></span>

### <a name="properties"></a><span data-ttu-id="0ac44-185">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0ac44-185">Properties</span></span>

<span data-ttu-id="0ac44-186">Er is een nieuw veld, `ImplementingAssembly` , toegevoegd aan `ModuleInfo` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-186">A new field, `ImplementingAssembly`, was added to `ModuleInfo`.</span></span> <span data-ttu-id="0ac44-187">Als het script klassen definieert, of als de geladen assembly voor binaire modules `ImplementingAssembly` is ingesteld op de dynamische assembly die is gemaakt voor een script module.</span><span class="sxs-lookup"><span data-stu-id="0ac44-187">If the script defines classes, or the loaded assembly for binary modules `ImplementingAssembly` is set to the dynamic assembly created for a script module.</span></span> <span data-ttu-id="0ac44-188">Deze is niet ingesteld als module type = manifest.</span><span class="sxs-lookup"><span data-stu-id="0ac44-188">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="0ac44-189">Reflectie op het `ImplementingAssembly` veld Hiermee worden bronnen in een module gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="0ac44-189">Reflection on the `ImplementingAssembly` field discovers resources in a module.</span></span> <span data-ttu-id="0ac44-190">Dit betekent dat u resources kunt detecteren die in Power shell of andere beheerde talen zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="0ac44-190">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="0ac44-191">Velden met initialisatie functies.</span><span class="sxs-lookup"><span data-stu-id="0ac44-191">Fields with initializers.</span></span>

`[int] $i = 5`

<span data-ttu-id="0ac44-192">Statisch wordt ondersteund en werkt als een kenmerk, vergelijkbaar met de type beperkingen, zodat het kan worden opgegeven in een wille keurige volg orde.</span><span class="sxs-lookup"><span data-stu-id="0ac44-192">Static is supported and works like an attribute, similar to the type constraints, so it can be specified in any order.</span></span>

`static [int] $count = 0`

<span data-ttu-id="0ac44-193">Een type is optioneel.</span><span class="sxs-lookup"><span data-stu-id="0ac44-193">A type is optional.</span></span>

`$s = "hello"`

<span data-ttu-id="0ac44-194">Alle leden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="0ac44-194">All members are public.</span></span> <span data-ttu-id="0ac44-195">Eigenschappen vereisen een nieuwe regel of een punt komma.</span><span class="sxs-lookup"><span data-stu-id="0ac44-195">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="0ac44-196">Als er geen object type is opgegeven, is het eigenschaps type **object**.</span><span class="sxs-lookup"><span data-stu-id="0ac44-196">If no object type is specified, the property type is **Object**.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="0ac44-197">Constructors en instantiëring</span><span class="sxs-lookup"><span data-stu-id="0ac44-197">Constructors and instantiation</span></span>

<span data-ttu-id="0ac44-198">Power shell-klassen kunnen constructors hebben die dezelfde naam hebben als hun klasse.</span><span class="sxs-lookup"><span data-stu-id="0ac44-198">PowerShell classes can have constructors that have the same name as their class.</span></span> <span data-ttu-id="0ac44-199">Constructors kunnen overbelast zijn.</span><span class="sxs-lookup"><span data-stu-id="0ac44-199">Constructors can be overloaded.</span></span> <span data-ttu-id="0ac44-200">Statische Constructors worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0ac44-200">Static constructors are supported.</span></span>
<span data-ttu-id="0ac44-201">Eigenschappen met initialisatie-expressies worden geïnitialiseerd voordat code in een constructor wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0ac44-201">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="0ac44-202">Statische eigenschappen worden geïnitialiseerd voordat de hoofd tekst van een statische constructor, en instantie-eigenschappen worden geïnitialiseerd vóór de hoofd tekst van de niet-statische constructor.</span><span class="sxs-lookup"><span data-stu-id="0ac44-202">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="0ac44-203">Er is momenteel geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor, zoals de C#-syntaxis: `": this()")` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-203">Currently, there is no syntax for calling a constructor from another constructor such as the C# syntax: `": this()")`.</span></span> <span data-ttu-id="0ac44-204">De tijdelijke oplossing is het definiëren van een algemene init-methode.</span><span class="sxs-lookup"><span data-stu-id="0ac44-204">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="0ac44-205">Hier volgen enkele manieren waarop u klassen kunt instantiëren:</span><span class="sxs-lookup"><span data-stu-id="0ac44-205">The following are ways of instantiating classes:</span></span>

- <span data-ttu-id="0ac44-206">Instantiëren met behulp van de standaardconstructor.</span><span class="sxs-lookup"><span data-stu-id="0ac44-206">Instantiating by using the default constructor.</span></span> <span data-ttu-id="0ac44-207">Opmerking: `New-Object` wordt niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="0ac44-207">Note that `New-Object` is not supported in this release.</span></span>

  `$a = [MyClass]::new()`

- <span data-ttu-id="0ac44-208">Een constructor met een para meter aanroepen.</span><span class="sxs-lookup"><span data-stu-id="0ac44-208">Calling a constructor with a parameter.</span></span>

  `$b = [MyClass]::new(42)`

- <span data-ttu-id="0ac44-209">Een matrix door geven aan een constructor met meerdere para meters</span><span class="sxs-lookup"><span data-stu-id="0ac44-209">Passing an array to a constructor with multiple parameters</span></span>

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

<span data-ttu-id="0ac44-210">Voor deze release is de type naam alleen lexicalief zichtbaar, wat betekent dat deze niet zichtbaar is buiten de module of het script waarmee de klasse wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="0ac44-210">For this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="0ac44-211">Functies kunnen exemplaren retour neren van een klasse die is gedefinieerd in Power shell, en instanties werken goed buiten de module of het script.</span><span class="sxs-lookup"><span data-stu-id="0ac44-211">Functions can return instances of a class defined in PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="0ac44-212">Met de `Get-Member` **statische** para meters worden constructors weer gegeven, zodat u Overloads op dezelfde manier kunt bekijken als andere methoden.</span><span class="sxs-lookup"><span data-stu-id="0ac44-212">The `Get-Member` **Static** parameter lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="0ac44-213">De prestaties van deze syntaxis zijn ook aanzienlijk sneller dan `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-213">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

<span data-ttu-id="0ac44-214">De pseudo-statische methode met de naam **New** werkt met .net-typen, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="0ac44-214">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span> `[hashtable]::new()`

<span data-ttu-id="0ac44-215">U kunt nu overbelasting van constructor zien met `Get-Member` , of zoals in dit voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="0ac44-215">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a><span data-ttu-id="0ac44-216">Methoden</span><span class="sxs-lookup"><span data-stu-id="0ac44-216">Methods</span></span>

<span data-ttu-id="0ac44-217">Een Power shell-klassen methode wordt geïmplementeerd als een **script Block** die alleen een eind blok heeft.</span><span class="sxs-lookup"><span data-stu-id="0ac44-217">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="0ac44-218">Alle methoden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="0ac44-218">All methods are public.</span></span> <span data-ttu-id="0ac44-219">Hieronder ziet u een voor beeld van het definiëren van een methode met de naam **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="0ac44-219">The following shows an example of defining a method named **DoSomething**.</span></span>

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

### <a name="method-invocation"></a><span data-ttu-id="0ac44-220">Methode aanroep</span><span class="sxs-lookup"><span data-stu-id="0ac44-220">Method invocation</span></span>

<span data-ttu-id="0ac44-221">Overbelaste methoden worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0ac44-221">Overloaded methods are supported.</span></span> <span data-ttu-id="0ac44-222">Overbelaste methoden hebben dezelfde naam als een bestaande methode, maar worden gedifferentieerd met de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="0ac44-222">Overloaded methods are named the same as an existing method but differentiated by their specified values.</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a><span data-ttu-id="0ac44-223">Aanroep</span><span class="sxs-lookup"><span data-stu-id="0ac44-223">Invocation</span></span>

<span data-ttu-id="0ac44-224">Zie [methode aanroep](#method-invocation).</span><span class="sxs-lookup"><span data-stu-id="0ac44-224">See [Method invocation](#method-invocation).</span></span>

### <a name="attributes"></a><span data-ttu-id="0ac44-225">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0ac44-225">Attributes</span></span>

<span data-ttu-id="0ac44-226">Er zijn drie nieuwe kenmerken toegevoegd: `DscResource` , `DscResourceKey` en `DscResourceMandatory` .</span><span class="sxs-lookup"><span data-stu-id="0ac44-226">Three new attributes were added: `DscResource`, `DscResourceKey`, and `DscResourceMandatory`.</span></span>

### <a name="return-types"></a><span data-ttu-id="0ac44-227">Retour typen</span><span class="sxs-lookup"><span data-stu-id="0ac44-227">Return types</span></span>

<span data-ttu-id="0ac44-228">Retour type is een contract.</span><span class="sxs-lookup"><span data-stu-id="0ac44-228">Return type is a contract.</span></span> <span data-ttu-id="0ac44-229">De geretourneerde waarde wordt geconverteerd naar het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="0ac44-229">The return value is converted to the expected type.</span></span>
<span data-ttu-id="0ac44-230">Als er geen retour type is opgegeven, is het retour type void.</span><span class="sxs-lookup"><span data-stu-id="0ac44-230">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="0ac44-231">Het streamen van objecten en objecten kan niet opzettelijk of per ongeluk naar de pijp lijn worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="0ac44-231">There is no streaming of objects and objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="0ac44-232">Lexicale bereik van variabelen</span><span class="sxs-lookup"><span data-stu-id="0ac44-232">Lexical scoping of variables</span></span>

<span data-ttu-id="0ac44-233">Hieronder ziet u een voor beeld van hoe lexicale scoping werkt in deze release.</span><span class="sxs-lookup"><span data-stu-id="0ac44-233">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="example-create-custom-classes"></a><span data-ttu-id="0ac44-234">Voor beeld: aangepaste klassen maken</span><span class="sxs-lookup"><span data-stu-id="0ac44-234">Example: Create custom classes</span></span>

<span data-ttu-id="0ac44-235">In het volgende voor beeld worden verschillende nieuwe aangepaste klassen gemaakt om een HTML Dynamic Style Sheet Language (DSL) te implementeren.</span><span class="sxs-lookup"><span data-stu-id="0ac44-235">The following example creates several new, custom classes to implement an HTML Dynamic Stylesheet Language (DSL).</span></span> <span data-ttu-id="0ac44-236">In het voor beeld worden hulp functies toegevoegd om specifieke element typen te maken als onderdeel van de klasse element, zoals kopstijlen en tabellen, omdat typen niet buiten het bereik van een module kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0ac44-236">The example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0ac44-237">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0ac44-237">See also</span></span>

[<span data-ttu-id="0ac44-238">about_Enum</span><span class="sxs-lookup"><span data-stu-id="0ac44-238">about_Enum</span></span>](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[<span data-ttu-id="0ac44-239">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="0ac44-239">about_Hidden</span></span>](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[<span data-ttu-id="0ac44-240">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="0ac44-240">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="0ac44-241">about_Methods</span><span class="sxs-lookup"><span data-stu-id="0ac44-241">about_Methods</span></span>](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[<span data-ttu-id="0ac44-242">Aangepaste Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="0ac44-242">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
