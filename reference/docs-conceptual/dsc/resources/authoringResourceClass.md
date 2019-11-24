---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een aangepaste DSC-resource schrijven met Power shell-klassen
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941157"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="a731c-103">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="a731c-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="a731c-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="a731c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a731c-105">Met de introductie van Power shell-klassen in Windows Power shell 5,0 kunt u nu een DSC-resource definiëren door een klasse te maken.</span><span class="sxs-lookup"><span data-stu-id="a731c-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="a731c-106">De klasse definieert zowel het schema als de implementatie van de resource, dus het is niet nodig om een afzonderlijk MOF-bestand te maken.</span><span class="sxs-lookup"><span data-stu-id="a731c-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="a731c-107">De mapstructuur voor een bron op basis van een klasse is ook eenvoudiger, omdat een **DSCResources** -map niet nodig is.</span><span class="sxs-lookup"><span data-stu-id="a731c-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="a731c-108">In een DSC-resource op basis van een klasse wordt het schema gedefinieerd als eigenschappen van de klasse die kan worden gewijzigd met kenmerken om het eigenschaps type op te geven.</span><span class="sxs-lookup"><span data-stu-id="a731c-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="a731c-109">De resource wordt geïmplementeerd met de methoden **Get ()** , **set ()** en **test ()** (gelijk aan de functies **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** in een script bron.</span><span class="sxs-lookup"><span data-stu-id="a731c-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="a731c-110">In dit onderwerp maakt u een eenvoudige resource met de naam **FileResource** die een bestand beheert in een opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="a731c-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="a731c-111">Zie voor meer informatie over DSC-resources [aangepaste Windows Power shell-configuratie resources voor desired state bouwen](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="a731c-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="a731c-112">**Opmerking:** Algemene verzamelingen worden niet ondersteund in op klassen gebaseerde resources.</span><span class="sxs-lookup"><span data-stu-id="a731c-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="a731c-113">Mapstructuur voor een klassen resource</span><span class="sxs-lookup"><span data-stu-id="a731c-113">Folder structure for a class resource</span></span>

<span data-ttu-id="a731c-114">Als u een aangepaste DSC-resource wilt implementeren met een Power shell-klasse, maakt u de volgende mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="a731c-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="a731c-115">De klasse wordt gedefinieerd in **MyDscResource. psm1** en het module manifest is gedefinieerd in **MyDscResource. psd1**.</span><span class="sxs-lookup"><span data-stu-id="a731c-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="a731c-116">De klasse maken</span><span class="sxs-lookup"><span data-stu-id="a731c-116">Create the class</span></span>

<span data-ttu-id="a731c-117">U kunt het sleutel woord class gebruiken om een Power shell-klasse te maken.</span><span class="sxs-lookup"><span data-stu-id="a731c-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="a731c-118">Gebruik het kenmerk **dscresource bieden ()** om op te geven dat een klasse een DSC-resource is.</span><span class="sxs-lookup"><span data-stu-id="a731c-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="a731c-119">De naam van de klasse is de naam van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="a731c-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="a731c-120">Eigenschappen declareren</span><span class="sxs-lookup"><span data-stu-id="a731c-120">Declare properties</span></span>

<span data-ttu-id="a731c-121">Het DSC-resource schema is gedefinieerd als eigenschappen van de klasse.</span><span class="sxs-lookup"><span data-stu-id="a731c-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="a731c-122">We declareren drie eigenschappen als volgt.</span><span class="sxs-lookup"><span data-stu-id="a731c-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="a731c-123">U ziet dat de eigenschappen zijn gewijzigd op basis van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="a731c-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="a731c-124">De betekenis van de kenmerken is als volgt:</span><span class="sxs-lookup"><span data-stu-id="a731c-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="a731c-125">**DscProperty (sleutel)** : de eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="a731c-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="a731c-126">De eigenschap is een sleutel.</span><span class="sxs-lookup"><span data-stu-id="a731c-126">The property is a key.</span></span> <span data-ttu-id="a731c-127">De waarden van alle eigenschappen die als sleutels zijn gemarkeerd, moeten combi neren om een bron exemplaar binnen een configuratie uniek te identificeren.</span><span class="sxs-lookup"><span data-stu-id="a731c-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="a731c-128">**DscProperty (verplicht)** : de eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="a731c-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="a731c-129">**DscProperty (NotConfigurable)** : de eigenschap is alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="a731c-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="a731c-130">Eigenschappen die zijn gemarkeerd met dit kenmerk, kunnen niet worden ingesteld met een configuratie, maar worden gevuld door de methode **Get ()** wanneer deze aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="a731c-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="a731c-131">**DscProperty ()** : de eigenschap kan worden geconfigureerd, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="a731c-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="a731c-132">De eigenschappen **$Path** en **$SourcePath** zijn beide teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="a731c-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="a731c-133">De **$CreationTime** is een [datum/tijd](/dotnet/api/system.datetime) -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="a731c-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="a731c-134">De eigenschap **$ensure** is een opsommings type dat als volgt is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a731c-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="a731c-135">De methoden implementeren</span><span class="sxs-lookup"><span data-stu-id="a731c-135">Implementing the methods</span></span>

<span data-ttu-id="a731c-136">De methoden **Get ()** , **set ()** en **test ()** zijn vergelijkbaar met de functies **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** in een script bron.</span><span class="sxs-lookup"><span data-stu-id="a731c-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="a731c-137">Deze code bevat ook de functie CopyFile (), een helper-functie waarmee het bestand wordt gekopieerd van **$SourcePath** naar **$Path**.</span><span class="sxs-lookup"><span data-stu-id="a731c-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

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

### <a name="the-complete-file"></a><span data-ttu-id="a731c-138">Het volledige bestand</span><span class="sxs-lookup"><span data-stu-id="a731c-138">The complete file</span></span>

<span data-ttu-id="a731c-139">Het volledige klassen bestand volgt.</span><span class="sxs-lookup"><span data-stu-id="a731c-139">The complete class file follows.</span></span>

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

## <a name="create-a-manifest"></a><span data-ttu-id="a731c-140">Een manifest maken</span><span class="sxs-lookup"><span data-stu-id="a731c-140">Create a manifest</span></span>

<span data-ttu-id="a731c-141">Als u een op een klasse gebaseerde resource beschikbaar wilt maken voor de DSC-engine, moet u een **DscResourcesToExport** -instructie in het manifest bestand toevoegen die de module de opdracht geeft de resource te exporteren.</span><span class="sxs-lookup"><span data-stu-id="a731c-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="a731c-142">Het manifest ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="a731c-142">Our manifest looks like this:</span></span>

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

## <a name="test-the-resource"></a><span data-ttu-id="a731c-143">De resource testen</span><span class="sxs-lookup"><span data-stu-id="a731c-143">Test the resource</span></span>

<span data-ttu-id="a731c-144">Nadat u de klasse en de manifest bestanden in de mappen structuur hebt opgeslagen zoals eerder beschreven, kunt u een configuratie maken die gebruikmaakt van de nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="a731c-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="a731c-145">Zie voor meer informatie over het uitvoeren van een DSC-configuratie [configuraties](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="a731c-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="a731c-146">Met de volgende configuratie wordt gecontroleerd of het bestand op `c:\test\test.txt` bestaat, en, als dat niet het geval is, kopieert u het bestand van `c:\test.txt` (u moet `c:\test.txt` maken voordat u de configuratie uitvoert).</span><span class="sxs-lookup"><span data-stu-id="a731c-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="a731c-147">PsDscRunAsCredential ondersteunen</span><span class="sxs-lookup"><span data-stu-id="a731c-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="a731c-148">**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="a731c-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="a731c-149">De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="a731c-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="a731c-150">Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a731c-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="a731c-151">PsDscRunAsCredential voor uw resource vereisen of weigeren</span><span class="sxs-lookup"><span data-stu-id="a731c-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="a731c-152">Het kenmerk **dscresource bieden ()** gebruikt een optionele para meter **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="a731c-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="a731c-153">Deze para meter heeft een van de drie volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="a731c-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="a731c-154">`Optional` **PsDscRunAsCredential** is optioneel voor configuraties die deze bron aanroepen.</span><span class="sxs-lookup"><span data-stu-id="a731c-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="a731c-155">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="a731c-155">This is the default value.</span></span>
- <span data-ttu-id="a731c-156">`Mandatory` **PsDscRunAsCredential** moet worden gebruikt voor elke configuratie die deze bron aanroept.</span><span class="sxs-lookup"><span data-stu-id="a731c-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="a731c-157">`NotSupported` configuraties die deze resource aanroepen, kunnen **PsDscRunAsCredential**niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a731c-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="a731c-158">`Default` hetzelfde als `Optional`.</span><span class="sxs-lookup"><span data-stu-id="a731c-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="a731c-159">Gebruik bijvoorbeeld het volgende kenmerk om op te geven dat uw aangepaste resource geen ondersteuning biedt voor het gebruik van **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="a731c-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="a731c-160">Meerdere klassen resources declareren in een module</span><span class="sxs-lookup"><span data-stu-id="a731c-160">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="a731c-161">Een module kan meerdere DSC-resources op basis van klassen definiëren.</span><span class="sxs-lookup"><span data-stu-id="a731c-161">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="a731c-162">U kunt de mapstructuur op de volgende manieren maken:</span><span class="sxs-lookup"><span data-stu-id="a731c-162">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="a731c-163">Definieer de eerste resource in het bestand '<ModuleName>. psm1 ' en de volgende resources in de map **DSCResources** .</span><span class="sxs-lookup"><span data-stu-id="a731c-163">Define the first resource in the "<ModuleName>.psm1" file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. <span data-ttu-id="a731c-164">Definieer alle resources in de map **DSCResources** .</span><span class="sxs-lookup"><span data-stu-id="a731c-164">Define all resources under the **DSCResources** folder.</span></span>

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
> <span data-ttu-id="a731c-165">Voeg in de bovenstaande voor beelden PSM1-bestanden onder de **DSCResources** toe aan de sleutel **NESTEDMODULES** in uw PSD1-bestand.</span><span class="sxs-lookup"><span data-stu-id="a731c-165">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="a731c-166">De gebruikers context openen</span><span class="sxs-lookup"><span data-stu-id="a731c-166">Access the user context</span></span>

<span data-ttu-id="a731c-167">Als u toegang wilt krijgen tot de gebruikers context vanuit een aangepaste resource, kunt u de automatische variabele `$global:PsDscContext`gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a731c-167">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="a731c-168">Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:</span><span class="sxs-lookup"><span data-stu-id="a731c-168">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="a731c-169">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a731c-169">See Also</span></span>

[<span data-ttu-id="a731c-170">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="a731c-170">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
