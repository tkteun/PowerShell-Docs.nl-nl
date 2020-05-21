---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een aangepaste DSC-resource schrijven met Power shell-klassen
ms.openlocfilehash: f96a567253ab4808381c004df243c96886948407
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692226"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a>Een aangepaste DSC-resource schrijven met Power shell-klassen

> Van toepassing op: Windows Power shell 5,0

Met de introductie van Power shell-klassen in Windows Power shell 5,0 kunt u nu een DSC-resource definiëren door een klasse te maken. De klasse definieert zowel het schema als de implementatie van de resource, dus het is niet nodig om een afzonderlijk MOF-bestand te maken. De mapstructuur voor een bron op basis van een klasse is ook eenvoudiger, omdat een **DSCResources** -map niet nodig is.

In een DSC-resource op basis van een klasse wordt het schema gedefinieerd als eigenschappen van de klasse die kan worden gewijzigd met kenmerken om het eigenschaps type op te geven. De resource wordt geïmplementeerd met de methoden **Get ()**, **set ()** en **test ()** (gelijk aan de functies **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** in een script bron.

In dit onderwerp maakt u een eenvoudige resource met de naam **FileResource** die een bestand beheert in een opgegeven pad.

Zie voor meer informatie over DSC-resources [aangepaste Windows Power shell-configuratie resources voor desired state bouwen](authoringResource.md)

>**Opmerking:** Algemene verzamelingen worden niet ondersteund in op klassen gebaseerde resources.

## <a name="folder-structure-for-a-class-resource"></a>Mapstructuur voor een klassen resource

Als u een aangepaste DSC-resource wilt implementeren met een Power shell-klasse, maakt u de volgende mapstructuur. De klasse wordt gedefinieerd in **MyDscResource. psm1** en het module manifest is gedefinieerd in **MyDscResource. psd1**.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a>De klasse maken

U kunt het sleutel woord class gebruiken om een Power shell-klasse te maken. Gebruik het kenmerk **dscresource bieden ()** om op te geven dat een klasse een DSC-resource is. De naam van de klasse is de naam van de DSC-resource.

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a>Eigenschappen declareren

Het DSC-resource schema is gedefinieerd als eigenschappen van de klasse. We declareren drie eigenschappen als volgt.

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

U ziet dat de eigenschappen zijn gewijzigd op basis van kenmerken. De betekenis van de kenmerken is als volgt:

- **DscProperty (sleutel)**: de eigenschap is vereist. De eigenschap is een sleutel. De waarden van alle eigenschappen die als sleutels zijn gemarkeerd, moeten combi neren om een bron exemplaar binnen een configuratie uniek te identificeren.
- **DscProperty (verplicht)**: de eigenschap is vereist.
- **DscProperty (NotConfigurable)**: de eigenschap is alleen-lezen. Eigenschappen die zijn gemarkeerd met dit kenmerk, kunnen niet worden ingesteld met een configuratie, maar worden gevuld door de methode **Get ()** wanneer deze aanwezig is.
- **DscProperty ()**: de eigenschap kan worden geconfigureerd, maar dit is niet vereist.

De eigenschappen **$Path** en **$SourcePath** zijn beide teken reeksen. De **$CreationTime** is een [datum/tijd](/dotnet/api/system.datetime) -eigenschap. De eigenschap **$ensure** is een opsommings type dat als volgt is gedefinieerd.

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a>De methoden implementeren

De methoden **Get ()**, **set ()** en **test ()** zijn vergelijkbaar met de functies **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** in een script bron.

Deze code bevat ook de functie CopyFile (), een helper-functie waarmee het bestand wordt gekopieerd van **$SourcePath** naar **$Path**.

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

Het volledige klassen bestand volgt.

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

## <a name="create-a-manifest"></a>Een manifest maken

Als u een op een klasse gebaseerde resource beschikbaar wilt maken voor de DSC-engine, moet u een **DscResourcesToExport** -instructie in het manifest bestand toevoegen die de module de opdracht geeft de resource te exporteren. Het manifest ziet er als volgt uit:

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

Nadat u de klasse en de manifest bestanden in de mappen structuur hebt opgeslagen zoals eerder beschreven, kunt u een configuratie maken die gebruikmaakt van de nieuwe resource. Zie voor meer informatie over het uitvoeren van een DSC-configuratie [configuraties](../pull-server/enactingConfigurations.md). Met de volgende configuratie wordt gecontroleerd of het bestand `c:\test\test.txt` al bestaat, en, als dat niet het geval is, kopieert u het bestand van `c:\test.txt` (u moet maken `c:\test.txt` voordat u de configuratie uitvoert).

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

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential ondersteunen

>**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in Power shell 5,0 en hoger.

De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a>PsDscRunAsCredential voor uw resource vereisen of weigeren

Het kenmerk **dscresource bieden ()** gebruikt een optionele para meter **RunAsCredential**.
Deze para meter heeft een van de drie volgende waarden:

- `Optional`**PsDscRunAsCredential** is optioneel voor configuraties die deze bron aanroepen. Dit is de standaardwaarde.
- `Mandatory`**PsDscRunAsCredential** moet worden gebruikt voor elke configuratie die deze bron aanroept.
- `NotSupported`Configuraties die deze resource aanroepen, kunnen **PsDscRunAsCredential**niet gebruiken.
- `Default`Hetzelfde als `Optional` .

Gebruik bijvoorbeeld het volgende kenmerk om op te geven dat uw aangepaste resource geen ondersteuning biedt voor het gebruik van **PsDscRunAsCredential**:

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a>Meerdere klassen resources declareren in een module

Een module kan meerdere DSC-resources op basis van klassen definiëren. U kunt de mapstructuur op de volgende manieren maken:

1. Definieer de eerste resource in het `<ModuleName>.psm1` bestand en de volgende resources in de map **DSCResources** .

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. Definieer alle resources in de map **DSCResources** .

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
> Voeg in de bovenstaande voor beelden PSM1-bestanden onder de **DSCResources** toe aan de sleutel **NESTEDMODULES** in uw PSD1-bestand.

### <a name="access-the-user-context"></a>De gebruikers context openen

Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele gebruiken `$global:PsDscContext` .

Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zie ook

[Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen](authoringResource.md)
