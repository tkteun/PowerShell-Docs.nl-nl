---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: 'Samengestelde resources: met behulp van een DSC-configuratie als resource'
ms.openlocfilehash: 79fe94bd5bab8fa460714e5994d2e2487f302410
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415894"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Samengestelde resources: het gebruik van een DSC-configuratie als een resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

In praktijk situaties kunnen configuraties lang en complex worden, waardoor veel verschillende bronnen worden aangeroepen en een groot aantal eigenschappen kan worden ingesteld. U kunt deze complexiteit helpen aanpakken door een Windows Power shell desired state Configuration (DSC)-configuratie te gebruiken als een resource voor andere configuraties. Dit wordt een samengestelde resource genoemd. Een samengestelde resource is een DSC-configuratie waarvoor para meters worden gebruikt. De para meters van de configuratie Act als de eigenschappen van de resource. De configuratie wordt opgeslagen als een bestand met een `.schema.psm1`-extensie. Het is de plaats van zowel het MOF-schema als het bron script in een typische DSC-resource. Zie [Windows Power shell desired state Configuration resources](resources.md)(Engelstalig) voor meer informatie over DSC-resources.

## <a name="creating-the-composite-resource"></a>De samengestelde resource maken

In ons voor beeld maken we een configuratie die een aantal bestaande resources aanroept om virtuele machines te configureren. In plaats van de waarden op te geven die moeten worden ingesteld in configuratie blokken, neemt de configuratie in para meters die vervolgens worden gebruikt in de configuratie blokken.

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

> [!NOTE]
> DSC biedt momenteel geen ondersteuning voor het plaatsen van samengestelde resources of geneste configuraties binnen een samengestelde resource.

### <a name="saving-the-configuration-as-a-composite-resource"></a>De configuratie opslaan als een samengestelde resource

Als u de para meter configuratie wilt gebruiken als een DSC-resource, slaat u deze op in een directory structuur, zoals die van elke andere op MOF gebaseerde resource, en noemt u deze met een `.schema.psm1`-extensie. In dit voor beeld noemen we het bestand `xVirtualMachine.schema.psm1`. U moet ook een manifest maken met de naam `xVirtualMachine.psd1` die de volgende regel bevat.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> Dit is een aanvulling op `MyDscResources.psd1`, het module manifest voor alle resources in de map `MyDscResources`.

Wanneer u klaar bent, moet de mapstructuur de volgende zijn.

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

De resource kan nu worden gedetecteerd met behulp van de cmdlet `Get-DscResource`, en de bijbehorende eigenschappen kunnen worden gedetecteerd door de cmdlet of door gebruik te maken van <kbd>Ctrl</kbd>+<kbd>Space</kbd> automatisch aanvullen in de Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>De samengestelde Resource gebruiken

Vervolgens maken we een configuratie die de samengestelde resource aanroept. Deze configuratie roept de xVirtualMachine-samengestelde bron op om een virtuele machine te maken en roept vervolgens de **xComputer** -resource aan om de naam ervan te wijzigen.

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

U kunt deze resource ook gebruiken om meerdere Vm's te maken door een matrix van VM-namen door te geven aan de xVirtualMachine-resource.

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential ondersteunen

> [!NOTE]
> **PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.

De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties. Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.

Als u toegang wilt krijgen tot de gebruikers context vanuit een aangepaste resource, kunt u de automatische variabele `$PsDscContext`gebruiken.

Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zie ook

### <a name="concepts"></a>Concepten

- [Een aangepaste DSC-resource schrijven met MOF](authoringResourceMOF.md)
- [Aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)
