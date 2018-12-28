---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Samengestelde resources--met behulp van een DSC-configuratie als een resource
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403907"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Samengestelde resources: Met behulp van een DSC-configuratie als een resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

In praktijksituaties, worden de configuraties kunnen worden lange en complexe, aanroepen van veel verschillende bronnen en het instellen van een groot aantal eigenschappen. Om te helpen deze complexe adres, kunt u een Windows PowerShell Desired State Configuration (DSC)-configuratie als een resource voor andere configuraties. We noemen dit een samengestelde resource. Een samengestelde resource is een DSC-configuratie die parameters zijn vereist. De parameters van de configuratie van de fungeren als de eigenschappen van de resource. De configuratie wordt opgeslagen als een bestand met een **. schema.psm1** -extensie en wordt de locatie van de MOF-schema- en de resource een script in een typische DSC-resource (Zie voor meer informatie over DSC-resources [Windows PowerShell Desired State Configuration Resources](resources.md).

## <a name="creating-the-composite-resource"></a>Het maken van de samengestelde resource

In ons voorbeeld maken we een configuratie die een aantal bestaande resources voor het configureren van virtuele machines aanroept. In plaats van de waarden worden ingesteld in blokken van de configuratie op te geven, wordt de configuratie van een aantal parameters die worden gebruikt in de configuratie-blokken.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a>De configuratie opslaan als een samengestelde resource

Voor het gebruik van de configuratie van de parameters als een DSC-resource, opslaan in een directory-structuur, zoals die van een andere op basis van MOF bron en deze met de naam een **. schema.psm1** extensie. In dit voorbeeld wordt het bestand naam **xVirtualMachine.schema.psm1**. U moet ook maken van een manifestbestand met de naam **xVirtualMachine.psd1** die de volgende regel bevat. Let op: dit is een aanvulling op **MyDscResources.psd1**, de module-manifest voor alle resources onder de **MyDscResources** map.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Wanneer u klaar bent, moet de mapstructuur als volgt.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

De resource kan nu worden gedetecteerd met behulp van de cmdlet Get-sleutelwoorden dscresource bieden en de eigenschappen kunnen worden gevonden door een van beide die cmdlet of met behulp van **Ctrl + spatie** automatisch aanvullen in de Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Met behulp van de samengestelde resource

Vervolgens maken we een configuratie die de samengestelde resource aanroept. Deze configuratie roept de xVirtualMachine samengestelde resource voor het maken van een virtuele machine en roept vervolgens de **xComputer** resource te wijzigen.

```powershell

configuration RenameVM
{

    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>Ondersteunende PsDscRunAsCredential

>**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in PowerShell 5.0 en hoger.

De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](../configurations/configurations.md) resource blokkeren om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie voor meer informatie, [DSC uitvoeren met gebruikersreferenties](../configurations/runAsUser.md).

U kunt de automatische variabele gebruiken voor toegang tot de gebruikerscontext uit binnen een aangepaste resource, `$PsDscContext`.

Bijvoorbeeld schrijft de volgende code de gebruikerscontext waarmee de resource wordt uitgevoerd naar de stroom uitgebreide uitvoer:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zie ook
### <a name="concepts"></a>Concepten
* [Een aangepaste DSC-resource met MOF schrijven](authoringResourceMOF.md)
* [Aan de slag met Windows PowerShell Desired State Configuration](../overview/overview.md)