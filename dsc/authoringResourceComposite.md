---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Samengestelde bronnen--met een DSC-configuratie als een bron
ms.openlocfilehash: c89293fdbe9bc054a47cc6974b6bd0471f727f46
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Samengestelde bronnen: met een DSC-configuratie als een bron

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

In de praktijk situaties worden configuraties lange en complexe, aanroepen van veel verschillende bronnen en het instellen van een groot aantal eigenschappen. Om te helpen met het adres van deze complexiteit, kunt u de configuratie van een Windows PowerShell Desired State Configuration (DSC) als een resource voor andere configuraties. We noemen dit een samengestelde bron. Een samengestelde bron is een DSC-configuratie die parameters zijn vereist. De parameters van de configuratie fungeren als de eigenschappen van de resource. De configuratie wordt opgeslagen als een bestand met een **. schema.psm1** extensie en wordt de plaats van zowel het MOF-schema en de resource een script in een typische DSC-resource (Zie voor meer informatie over DSC-resources [Windows PowerShell Desired State Configuration Resources](resources.md).

## <a name="creating-the-composite-resource"></a>Maken van de samengestelde resource

In ons voorbeeld maken we een configuratie met een aantal bestaande resources voor het configureren van virtuele machines wordt aangeroepen. In plaats van de waarden worden ingesteld in configuratie blokken opgeeft, wordt de configuratie een aantal parameters die worden gebruikt in de configuratie-blokken.

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

### <a name="saving-the-configuration-as-a-composite-resource"></a>De configuratie op te slaan als een samengestelde bron

Opslaan in een mapstructuur net als elke andere MOF op basis van een bron voor het gebruik van de configuratie van de parameters als een DSC-resource, en de naam met een **. schema.psm1** extensie. In dit voorbeeld Noem we het bestand **xVirtualMachine.schema.psm1**. U moet ook een manifest met de naam maken **xVirtualMachine.psd1** die de volgende regel bevat. Dit is in aanvulling op **MyDscResources.psd1**, de module-manifest voor alle resources onder de **MyDscResources** map.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Wanneer u klaar bent, moeten de mapstructuur als volgt.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

De resource kan nu worden gedetecteerd met de cmdlet Get-DscResource en bijbehorende eigenschappen kunnen worden gevonden door beide die cmdlet of via **Ctrl + spatiebalk** automatisch aanvullen in de Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Met behulp van de samengestelde bron

Vervolgens maken we een configuratie die de samengestelde bron aanroept. Deze configuratie roept de xVirtualMachine samengestelde bron voor het maken van een virtuele machine en roept vervolgens de **xComputer** resource te wijzigen.

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

De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](configurations.md) resource blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie voor meer informatie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).

Voor toegang tot de gebruikerscontext van binnen een aangepaste bron, kunt u de automatische variabele `$PsDscContext`.

De volgende code zou bijvoorbeeld de gebruikerscontext waaronder de bron wordt uitgevoerd naar de uitgebreide uitvoerstroom schrijven:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zie ook
### <a name="concepts"></a>Concepten
* [Schrijven van een aangepaste DSC-resource met MOF](authoringResourceMOF.md)
* [Aan de slag met Windows PowerShell Desired State Configuration](overview.md)