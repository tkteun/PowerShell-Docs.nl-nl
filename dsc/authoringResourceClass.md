---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Schrijven van een aangepaste DSC-resource met PowerShell-klassen
ms.openlocfilehash: 53757f965c51fee699409b5a8ecda802dda9801f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Schrijven van een aangepaste DSC-resource met PowerShell-klassen

> Van toepassing op: Windows Windows PowerShell 5.0

Dankzij de introductie van de klassen van PowerShell in Windows PowerShell 5.0, kunt u nu een DSC-resource definiëren door een klasse maken. De klasse definieert de schema- en de implementatie van de resource, dus u hoeft niet te maken van een afzonderlijke MOF-bestand. De mapstructuur voor een bron op basis van een klasse is ook eenvoudiger, omdat een **DSCResources** map is niet nodig.

Het schema is in een klasse gebaseerde DSC-resource gedefinieerd als de eigenschappen van de klasse die kan worden gewijzigd met kenmerken om op te geven van het eigenschapstype... De resource wordt geïmplementeerd door **Get()**, **Set()**, en **Test()** methoden (gelijk aan de **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource** functies in de bron van een script.

In dit onderwerp, maken we een eenvoudige resource met de naam **FileResource** die een bestand in een opgegeven pad beheert.

Zie voor meer informatie over DSC-resources [bouwen aangepaste Windows PowerShell Desired status configuratie Resources](authoringResource.md)

>**Opmerking:** algemene verzamelingen worden niet ondersteund in de klasse-bronnen.

## <a name="folder-structure-for-a-class-resource"></a>Mapstructuur voor een klasse-bron

Voor het implementeren van een aangepaste DSC-resource met een PowerShell-klasse, maken de volgende mapstructuur. De klasse is gedefinieerd in **MyDscResource.psm1** en de module-manifest wordt gedefinieerd in **MyDscResource.psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1 
           MyDscResource.psd1 
```

## <a name="create-the-class"></a>De klasse maken

Het sleutelwoord klasse kunt u een PowerShell-klasse maken. Als u wilt opgeven dat een klasse een DSC-resource is, gebruiken de **DscResource()** kenmerk. De naam van de klasse is de naam van de DSC-resource.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Eigenschappen declareren

De DSC-resource-schema is gedefinieerd als de eigenschappen van de klasse. We declareren drie eigenschappen als volgt.

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

U ziet dat de eigenschappen zijn gewijzigd door de kenmerken. De betekenis van de kenmerken is als volgt:

- **DscProperty(Key)**: de eigenschap is vereist. De eigenschap is een sleutel. De waarden van alle eigenschappen die zijn gemarkeerd als sleutels combineren moeten om een unieke identificatie van een resource-instantie in een configuratie.
- **DscProperty(Mandatory)**: de eigenschap is vereist.
- **DscProperty(NotConfigurable)**: de eigenschap is alleen-lezen. Eigenschappen die zijn gemarkeerd met dit kenmerk kan niet worden ingesteld door een configuratie, maar worden ingevuld met de **Get()** methode indien aanwezig.
- **DscProperty()**: de eigenschap kan worden geconfigureerd, maar is niet vereist.

De **$Path** en **$SourcePath** eigenschappen zijn beide tekenreeksen. De **$CreationTime** is een [DateTime](https://technet.microsoft.com/library/system.datetime.aspx) eigenschap. De **$Ensure** eigenschap is een opsommingstype als volgt gedefinieerd.

```powershell
enum Ensure 
{ 
    Absent 
    Present 
}
```

### <a name="implementing-the-methods"></a>Implementeren van de methoden

De **Get()**, **Set()**, en **Test()** methoden zijn vergelijkbaar met de **Get-TargetResource**, **Set TargetResource** , en **Test TargetResource** functies in de bron van een script.

Deze code bevat ook de functie CopyFile(), een Help-functie waarmee het bestand worden gekopieerd **$SourcePath** naar **$Path**. 

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

### <a name="the-complete-file"></a>Het volledige bestand
Het klassebestand voltooid volgt.

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


## <a name="create-a-manifest"></a>Maken van een manifest

Als u een resource op basis van een klasse met de DSC-engine, moet u opnemen een **DscResourcesToExport** -instructie in het manifestbestand geeft u de module voor het exporteren van de resource. Onze manifest ziet er als volgt:

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

## <a name="test-the-resource"></a>De resource testen

Na het opslaan van de klasse en de manifest-bestanden in de mapstructuur zoals eerder beschreven, kunt u een configuratie die gebruikmaakt van de nieuwe resource. Zie voor meer informatie over het uitvoeren van een DSC-configuratie [vast te stellen configuraties](enactingConfigurations.md). De volgende configuratie wordt gecontroleerd of het bestand op `c:\test\test.txt` bestaat en als dat niet het geval is, kopieert u het bestand van `c:\test.txt` (u moet maken `c:\test.txt` voordat u de configuratie uitvoeren).

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

## <a name="supporting-psdscrunascredential"></a>Ondersteunende PsDscRunAsCredential

>**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in PowerShell 5.0 en hoger.

De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](configurations.md) resource blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie voor meer informatie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>Vereist of niet toestaan van PsDscRunAsCredential voor uw resource

De **DscResource()** kenmerk duurt een optionele parameter **RunAsCredential**.
Deze parameter heeft een van drie waarden:

- `Optional` **PsDscRunAsCredential** is optioneel voor configuraties die aanroepen van deze resource. Dit is de standaardwaarde.
- `Mandatory` **PsDscRunAsCredential** moet worden gebruikt voor een configuratie die deze resource roept.
- `NotSupported` Configuraties die aanroepen van deze resource kunnen niet worden gebruikt **PsDscRunAsCredential**.
- `Default` Hetzelfde als `Optional`.

Het volgende kenmerk bijvoorbeeld gebruiken om op te geven dat uw aangepaste resource biedt geen ondersteuning met behulp van **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a>Toegang tot de gebruikerscontext

Voor toegang tot de gebruikerscontext van binnen een aangepaste bron, kunt u de automatische variabele `$global:PsDscContext`.

De volgende code zou bijvoorbeeld de gebruikerscontext waaronder de bron wordt uitgevoerd naar de uitgebreide uitvoerstroom schrijven:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zie ook
### <a name="concepts"></a>Concepten
[Aangepaste Windows PowerShell Desired State Configuration Resources bouwen](authoringResource.md)

