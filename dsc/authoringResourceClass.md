---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Schrijven van een aangepaste DSC-resource met de PowerShell-klassen
ms.openlocfilehash: a8f08323f2cced8a17de4224bea94a54ba5ef0cd
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226080"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="d6fd0-103">Schrijven van een aangepaste DSC-resource met de PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="d6fd0-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="d6fd0-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d6fd0-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d6fd0-105">U kunt nu een DSC-resource met het maken van een klasse met de introductie van PowerShell-klassen in Windows PowerShell 5.0 definiëren.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="d6fd0-106">De klasse definieert de schema- en de implementatie van de resource, dus u hoeft niet te maken van een afzonderlijk MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="d6fd0-107">De mapstructuur voor een resource op basis van een klasse is ook eenvoudiger, omdat een **DSCResources** map is niet nodig.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="d6fd0-108">In een resource van de DSC-klasse op basis van is het schema gedefinieerd als eigenschappen van de klasse op die kunnen worden gewijzigd met kenmerken om op te geven van het eigenschapstype...</span><span class="sxs-lookup"><span data-stu-id="d6fd0-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="d6fd0-109">De resource is geïmplementeerd door **Get()**, **Set()**, en **Test()** methoden (gelijk aan de **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource** functies in de bron van een script.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="d6fd0-110">In dit onderwerp, maken we een eenvoudige resource met de naam **FileResource** die een bestand in een opgegeven pad worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="d6fd0-111">Zie voor meer informatie over DSC-resources [maken aangepaste Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="d6fd0-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="d6fd0-112">**Opmerking:** algemene verzamelingen worden niet ondersteund in resources op basis van een klasse.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="d6fd0-113">Mapstructuur voor een klasse-resource</span><span class="sxs-lookup"><span data-stu-id="d6fd0-113">Folder structure for a class resource</span></span>

<span data-ttu-id="d6fd0-114">Voor het implementeren van een aangepaste DSC-resource met een PowerShell-klasse, maken de volgende mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="d6fd0-115">De klasse is gedefinieerd in **MyDscResource.psm1** en de module-manifest is gedefinieerd in **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="d6fd0-116">De klasse maken</span><span class="sxs-lookup"><span data-stu-id="d6fd0-116">Create the class</span></span>

<span data-ttu-id="d6fd0-117">U het sleutelwoord klasse gebruiken om een PowerShell-klasse te maken.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="d6fd0-118">Als u wilt opgeven dat een klasse een DSC-resource is, gebruikt u de **DscResource()** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="d6fd0-119">De naam van de klasse is de naam van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="d6fd0-120">Eigenschappen declareren</span><span class="sxs-lookup"><span data-stu-id="d6fd0-120">Declare properties</span></span>

<span data-ttu-id="d6fd0-121">De DSC-resource-schema wordt gedefinieerd als de eigenschappen van de klasse.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="d6fd0-122">We declareren drie eigenschappen als volgt.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="d6fd0-123">U ziet dat de eigenschappen zijn gewijzigd door kenmerken.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="d6fd0-124">De betekenis van de kenmerken is als volgt:</span><span class="sxs-lookup"><span data-stu-id="d6fd0-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="d6fd0-125">**DscProperty(Key)**: de eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="d6fd0-126">De eigenschap is een sleutel.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-126">The property is a key.</span></span> <span data-ttu-id="d6fd0-127">De waarden van alle eigenschappen die zijn gemarkeerd als sleutels moeten een combinatie van als unieke identificatie van een resource-instanties binnen een configuratie.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="d6fd0-128">**DscProperty(Mandatory)**: de eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="d6fd0-129">**DscProperty(NotConfigurable)**: de eigenschap is alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="d6fd0-130">Eigenschappen die zijn gemarkeerd met dit kenmerk kan niet worden ingesteld door een configuratie, maar worden ingevuld door de **Get()** methode indien aanwezig.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="d6fd0-131">**DscProperty()**: de eigenschap kan worden geconfigureerd, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="d6fd0-132">De **$Path** en **$SourcePath** eigenschappen zijn beide tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="d6fd0-133">De **$CreationTime** is een [datum-/](https://technet.microsoft.com/library/system.datetime.aspx) eigenschap.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-133">The **$CreationTime** is a [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) property.</span></span> <span data-ttu-id="d6fd0-134">De **$Ensure** eigenschap is een opsommingstype, als volgt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="d6fd0-135">Implementatie van de methoden</span><span class="sxs-lookup"><span data-stu-id="d6fd0-135">Implementing the methods</span></span>

<span data-ttu-id="d6fd0-136">De **Get()**, **Set()**, en **Test()** methoden zijn vergelijkbaar met de **Get-TargetResource**, **Set TargetResource** , en **Test TargetResource** functies in de bron van een script.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="d6fd0-137">Deze code bevat ook de functie CopyFile(), een Help-functie waarmee het bestand worden gekopieerd **$SourcePath** naar **$Path**.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

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

### <a name="the-complete-file"></a><span data-ttu-id="d6fd0-138">Het volledige bestand</span><span class="sxs-lookup"><span data-stu-id="d6fd0-138">The complete file</span></span>
<span data-ttu-id="d6fd0-139">De volledige klassebestand volgt.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-139">The complete class file follows.</span></span>

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


## <a name="create-a-manifest"></a><span data-ttu-id="d6fd0-140">Een manifest maken</span><span class="sxs-lookup"><span data-stu-id="d6fd0-140">Create a manifest</span></span>

<span data-ttu-id="d6fd0-141">Als u een resource op basis van een klasse met de DSC-engine, moet u opnemen een **DscResourcesToExport** -instructie in het manifestbestand geeft u de module voor het exporteren van de resource.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="d6fd0-142">Onze manifest ziet er als volgt:</span><span class="sxs-lookup"><span data-stu-id="d6fd0-142">Our manifest looks like this:</span></span>

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

## <a name="test-the-resource"></a><span data-ttu-id="d6fd0-143">Testen van de resource</span><span class="sxs-lookup"><span data-stu-id="d6fd0-143">Test the resource</span></span>

<span data-ttu-id="d6fd0-144">Na het opslaan van de klasse en de manifest-bestanden in de mapstructuur, zoals eerder beschreven, kunt u een configuratie die gebruikmaakt van de nieuwe resource maken.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="d6fd0-145">Zie voor meer informatie over het uitvoeren van een DSC-configuratie [configuraties doorvoeren](enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="d6fd0-145">For information about how to run a DSC configuration, see [Enacting configurations](enactingConfigurations.md).</span></span> <span data-ttu-id="d6fd0-146">De volgende configuratie wordt gecontroleerd om te zien of het bestand op `c:\test\test.txt` bestaat en, als dit niet het geval is, kopieert u het bestand van `c:\test.txt` (u moet maken `c:\test.txt` voordat u de configuratie uitvoeren).</span><span class="sxs-lookup"><span data-stu-id="d6fd0-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="d6fd0-147">Ondersteunende PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d6fd0-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="d6fd0-148">**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="d6fd0-149">De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](configurations.md) resource blokkeren om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="d6fd0-150">Zie voor meer informatie, [DSC uitvoeren met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d6fd0-150">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="d6fd0-151">Vereist of PsDscRunAsCredential weigeren voor uw resource</span><span class="sxs-lookup"><span data-stu-id="d6fd0-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="d6fd0-152">De **DscResource()** kenmerk heeft een optionele parameter **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="d6fd0-153">Deze parameter heeft een van drie waarden:</span><span class="sxs-lookup"><span data-stu-id="d6fd0-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="d6fd0-154">`Optional` **PsDscRunAsCredential** is optioneel voor configuraties die aanroepen van deze resource.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="d6fd0-155">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-155">This is the default value.</span></span>
- <span data-ttu-id="d6fd0-156">`Mandatory` **PsDscRunAsCredential** moet worden gebruikt voor de configuratie die deze resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="d6fd0-157">`NotSupported` Configuraties die aanroepen van deze resource kunnen niet worden gebruikt **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="d6fd0-158">`Default` Hetzelfde als `Optional`.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="d6fd0-159">Het volgende kenmerk bijvoorbeeld gebruiken om op te geven dat uw aangepaste resource biedt geen ondersteuning met behulp van **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="d6fd0-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="d6fd0-160">Toegang tot de context van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="d6fd0-160">Access the user context</span></span>

<span data-ttu-id="d6fd0-161">U kunt de automatische variabele gebruiken voor toegang tot de gebruikerscontext uit binnen een aangepaste resource, `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="d6fd0-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="d6fd0-162">Bijvoorbeeld schrijft de volgende code de gebruikerscontext waarmee de resource wordt uitgevoerd naar de stroom uitgebreide uitvoer:</span><span class="sxs-lookup"><span data-stu-id="d6fd0-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="d6fd0-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d6fd0-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="d6fd0-164">Concepten</span><span class="sxs-lookup"><span data-stu-id="d6fd0-164">Concepts</span></span>
[<span data-ttu-id="d6fd0-165">Maken van aangepaste Windows PowerShell Desired State Configuration Resources</span><span class="sxs-lookup"><span data-stu-id="d6fd0-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)