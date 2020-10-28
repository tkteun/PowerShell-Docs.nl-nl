---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Een aangepaste DSC-resource schrijven met Power shell-klassen
description: In dit artikel wordt beschreven hoe u een eenvoudige bron maakt die een bestand beheert in een opgegeven pad.
ms.openlocfilehash: 72a828795c29e10ff66f164b8871b0fea7a1e0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667314"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="78d6e-104">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="78d6e-104">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="78d6e-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="78d6e-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="78d6e-106">Met de introductie van Power shell-klassen in Windows Power shell 5,0 kunt u nu een DSC-resource definiëren door een klasse te maken.</span><span class="sxs-lookup"><span data-stu-id="78d6e-106">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="78d6e-107">De klasse definieert zowel het schema als de implementatie van de resource, dus het is niet nodig om een afzonderlijk MOF-bestand te maken.</span><span class="sxs-lookup"><span data-stu-id="78d6e-107">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="78d6e-108">De mapstructuur voor een bron op basis van een klasse is ook eenvoudiger, omdat een **DSCResources** -map niet nodig is.</span><span class="sxs-lookup"><span data-stu-id="78d6e-108">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="78d6e-109">In een DSC-resource op basis van een klasse wordt het schema gedefinieerd als eigenschappen van de klasse die kan worden gewijzigd met kenmerken om het eigenschaps type op te geven.</span><span class="sxs-lookup"><span data-stu-id="78d6e-109">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="78d6e-110">De resource wordt geïmplementeerd door `Get()` , `Set()` en- `Test()` methoden (gelijk aan de `Get-TargetResource` `Set-TargetResource` functies, en `Test-TargetResource` in een script bron.</span><span class="sxs-lookup"><span data-stu-id="78d6e-110">The resource is implemented by `Get()`, `Set()`, and `Test()` methods (equivalent to the `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions in a script resource.</span></span>

<span data-ttu-id="78d6e-111">In dit artikel maken we een eenvoudige resource met de naam **FileResource** die een bestand beheert in een opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="78d6e-111">In this article, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="78d6e-112">Zie voor meer informatie over DSC-resources [aangepaste Windows Power shell-configuratie resources voor desired state bouwen](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="78d6e-112">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

> [!Note]
> <span data-ttu-id="78d6e-113">Algemene verzamelingen worden niet ondersteund in op klassen gebaseerde resources.</span><span class="sxs-lookup"><span data-stu-id="78d6e-113">Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="78d6e-114">Mapstructuur voor een klassen resource</span><span class="sxs-lookup"><span data-stu-id="78d6e-114">Folder structure for a class resource</span></span>

<span data-ttu-id="78d6e-115">Als u een aangepaste DSC-resource wilt implementeren met een Power shell-klasse, maakt u de volgende mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="78d6e-115">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span>
<span data-ttu-id="78d6e-116">De klasse is gedefinieerd in `MyDscResource.psm1` en het module manifest is gedefinieerd in `MyDscResource.psd1` .</span><span class="sxs-lookup"><span data-stu-id="78d6e-116">The class is defined in `MyDscResource.psm1` and the module manifest is defined in `MyDscResource.psd1`.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="78d6e-117">De klasse maken</span><span class="sxs-lookup"><span data-stu-id="78d6e-117">Create the class</span></span>

<span data-ttu-id="78d6e-118">U kunt het sleutel woord class gebruiken om een Power shell-klasse te maken.</span><span class="sxs-lookup"><span data-stu-id="78d6e-118">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="78d6e-119">Gebruik het kenmerk om op te geven dat een klasse een DSC-resource is `DscResource()` .</span><span class="sxs-lookup"><span data-stu-id="78d6e-119">To specify that a class is a DSC resource, use the `DscResource()` attribute.</span></span> <span data-ttu-id="78d6e-120">De naam van de klasse is de naam van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="78d6e-120">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="78d6e-121">Eigenschappen declareren</span><span class="sxs-lookup"><span data-stu-id="78d6e-121">Declare properties</span></span>

<span data-ttu-id="78d6e-122">Het DSC-resource schema is gedefinieerd als eigenschappen van de klasse.</span><span class="sxs-lookup"><span data-stu-id="78d6e-122">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="78d6e-123">We declareren drie eigenschappen als volgt.</span><span class="sxs-lookup"><span data-stu-id="78d6e-123">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="78d6e-124">U ziet dat de eigenschappen zijn gewijzigd op basis van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="78d6e-124">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="78d6e-125">De betekenis van de kenmerken is als volgt:</span><span class="sxs-lookup"><span data-stu-id="78d6e-125">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="78d6e-126">**DscProperty (sleutel)** : de eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="78d6e-126">**DscProperty(Key)** : The property is required.</span></span> <span data-ttu-id="78d6e-127">De eigenschap is een sleutel.</span><span class="sxs-lookup"><span data-stu-id="78d6e-127">The property is a key.</span></span> <span data-ttu-id="78d6e-128">De waarden van alle eigenschappen die als sleutels zijn gemarkeerd, moeten combi neren om een bron exemplaar binnen een configuratie uniek te identificeren.</span><span class="sxs-lookup"><span data-stu-id="78d6e-128">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="78d6e-129">**DscProperty (verplicht)** : de eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="78d6e-129">**DscProperty(Mandatory)** : The property is required.</span></span>
- <span data-ttu-id="78d6e-130">**DscProperty (NotConfigurable)** : de eigenschap is alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="78d6e-130">**DscProperty(NotConfigurable)** : The property is read-only.</span></span> <span data-ttu-id="78d6e-131">Eigenschappen die zijn gemarkeerd met dit kenmerk, kunnen niet worden ingesteld met een configuratie, maar worden gevuld door de `Get()` methode wanneer deze aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="78d6e-131">Properties marked with this attribute cannot be set by a configuration, but are populated by the `Get()` method when present.</span></span>
- <span data-ttu-id="78d6e-132">**DscProperty ()** : de eigenschap kan worden geconfigureerd, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="78d6e-132">**DscProperty()** : The property is configurable, but it is not required.</span></span>

<span data-ttu-id="78d6e-133">De `$Path` `$SourcePath` Eigenschappen en zijn beide teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="78d6e-133">The `$Path` and `$SourcePath` properties are both strings.</span></span> <span data-ttu-id="78d6e-134">De `$CreationTime` eigenschap is een [datum/tijd](/dotnet/api/system.datetime) .</span><span class="sxs-lookup"><span data-stu-id="78d6e-134">The `$CreationTime` is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="78d6e-135">De `$Ensure` eigenschap is een opsommings type dat als volgt is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="78d6e-135">The `$Ensure` property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="78d6e-136">De methoden implementeren</span><span class="sxs-lookup"><span data-stu-id="78d6e-136">Implementing the methods</span></span>

<span data-ttu-id="78d6e-137">De `Get()` `Set()` methoden, en `Test()` zijn vergelijkbaar met de `Get-TargetResource` functies, `Set-TargetResource` en en `Test-TargetResource` in een script bron.</span><span class="sxs-lookup"><span data-stu-id="78d6e-137">The `Get()`, `Set()`, and `Test()` methods are analogous to the `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions in a script resource.</span></span>

<span data-ttu-id="78d6e-138">Deze code bevat ook de `CopyFile()` functie, een helper-functie waarmee het bestand wordt gekopieerd van `$SourcePath` naar `$Path` .</span><span class="sxs-lookup"><span data-stu-id="78d6e-138">This code also includes the `CopyFile()` function, a helper function that copies the file from `$SourcePath` to `$Path`.</span></span>

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="78d6e-139">Het volledige bestand</span><span class="sxs-lookup"><span data-stu-id="78d6e-139">The complete file</span></span>

<span data-ttu-id="78d6e-140">Het volledige klassen bestand volgt.</span><span class="sxs-lookup"><span data-stu-id="78d6e-140">The complete class file follows.</span></span>

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
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a><span data-ttu-id="78d6e-141">Een manifest maken</span><span class="sxs-lookup"><span data-stu-id="78d6e-141">Create a manifest</span></span>

<span data-ttu-id="78d6e-142">Als u een op een klasse gebaseerde resource beschikbaar wilt maken voor de DSC-engine, moet u een `DscResourcesToExport` instructie in het manifest bestand toevoegen die de module de opdracht geeft de resource te exporteren.</span><span class="sxs-lookup"><span data-stu-id="78d6e-142">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="78d6e-143">Het manifest ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="78d6e-143">Our manifest looks like this:</span></span>

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

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="78d6e-144">De resource testen</span><span class="sxs-lookup"><span data-stu-id="78d6e-144">Test the resource</span></span>

<span data-ttu-id="78d6e-145">Nadat u de klasse en de manifest bestanden in de mappen structuur hebt opgeslagen zoals eerder beschreven, kunt u een configuratie maken die gebruikmaakt van de nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="78d6e-145">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="78d6e-146">Zie voor meer informatie over het uitvoeren van een DSC-configuratie [configuraties](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="78d6e-146">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="78d6e-147">Met de volgende configuratie wordt gecontroleerd of het bestand `c:\test\test.txt` al bestaat, en, als dat niet het geval is, kopieert u het bestand van `c:\test.txt` (u moet maken `c:\test.txt` voordat u de configuratie uitvoert).</span><span class="sxs-lookup"><span data-stu-id="78d6e-147">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="78d6e-148">PsDscRunAsCredential ondersteunen</span><span class="sxs-lookup"><span data-stu-id="78d6e-148">Supporting PsDscRunAsCredential</span></span>

> <span data-ttu-id="78d6e-149">Eraan **PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="78d6e-149">[Note] **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="78d6e-150">De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="78d6e-150">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="78d6e-151">Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="78d6e-151">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="78d6e-152">PsDscRunAsCredential voor uw resource vereisen of weigeren</span><span class="sxs-lookup"><span data-stu-id="78d6e-152">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="78d6e-153">Het `DscResource()` kenmerk accepteert een optionele para meter **RunAsCredential** .</span><span class="sxs-lookup"><span data-stu-id="78d6e-153">The `DscResource()` attribute takes an optional parameter **RunAsCredential** .</span></span> <span data-ttu-id="78d6e-154">Deze para meter heeft een van de drie volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="78d6e-154">This parameter takes one of three values:</span></span>

- <span data-ttu-id="78d6e-155">`Optional`**PsDscRunAsCredential** is optioneel voor configuraties die deze bron aanroepen.</span><span class="sxs-lookup"><span data-stu-id="78d6e-155">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="78d6e-156">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="78d6e-156">This is the default value.</span></span>
- <span data-ttu-id="78d6e-157">`Mandatory`**PsDscRunAsCredential** moet worden gebruikt voor elke configuratie die deze bron aanroept.</span><span class="sxs-lookup"><span data-stu-id="78d6e-157">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="78d6e-158">`NotSupported` Configuraties die deze resource aanroepen, kunnen **PsDscRunAsCredential** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="78d6e-158">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential** .</span></span>
- <span data-ttu-id="78d6e-159">`Default` Hetzelfde als `Optional` .</span><span class="sxs-lookup"><span data-stu-id="78d6e-159">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="78d6e-160">Gebruik bijvoorbeeld het volgende kenmerk om op te geven dat uw aangepaste resource geen ondersteuning biedt voor het gebruik van **PsDscRunAsCredential** :</span><span class="sxs-lookup"><span data-stu-id="78d6e-160">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential** :</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="78d6e-161">Meerdere klassen resources declareren in een module</span><span class="sxs-lookup"><span data-stu-id="78d6e-161">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="78d6e-162">Een module kan meerdere DSC-resources op basis van klassen definiëren.</span><span class="sxs-lookup"><span data-stu-id="78d6e-162">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="78d6e-163">U kunt de mapstructuur op de volgende manieren maken:</span><span class="sxs-lookup"><span data-stu-id="78d6e-163">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="78d6e-164">Definieer de eerste resource in het `<ModuleName>.psm1` bestand en de volgende resources in de map **DSCResources** .</span><span class="sxs-lookup"><span data-stu-id="78d6e-164">Define the first resource in the `<ModuleName>.psm1` file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

1. <span data-ttu-id="78d6e-165">Definieer alle resources in de map **DSCResources** .</span><span class="sxs-lookup"><span data-stu-id="78d6e-165">Define all resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> <span data-ttu-id="78d6e-166">Voeg in de bovenstaande voor beelden PSM1-bestanden onder de **DSCResources** toe aan de sleutel **NESTEDMODULES** in uw PSD1-bestand.</span><span class="sxs-lookup"><span data-stu-id="78d6e-166">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="78d6e-167">De gebruikers context openen</span><span class="sxs-lookup"><span data-stu-id="78d6e-167">Access the user context</span></span>

<span data-ttu-id="78d6e-168">Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele gebruiken `$global:PsDscContext` .</span><span class="sxs-lookup"><span data-stu-id="78d6e-168">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="78d6e-169">Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:</span><span class="sxs-lookup"><span data-stu-id="78d6e-169">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="78d6e-170">Zie ook</span><span class="sxs-lookup"><span data-stu-id="78d6e-170">See Also</span></span>

[<span data-ttu-id="78d6e-171">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="78d6e-171">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
