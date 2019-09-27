---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: 'Samengestelde resources: met behulp van een DSC-configuratie als resource'
ms.openlocfilehash: ef8d5665e552da01977c2f21a43246c72bb7155f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323787"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Samengestelde resources: Een DSC-configuratie gebruiken als resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

In praktijk situaties kunnen configuraties lang en complex worden, waardoor veel verschillende bronnen worden aangeroepen en een groot aantal eigenschappen kan worden ingesteld. U kunt deze complexiteit helpen aanpakken door een Windows Power shell desired state Configuration (DSC)-configuratie te gebruiken als een resource voor andere configuraties. Dit is een samengestelde resource. Een samengestelde resource is een DSC-configuratie waarvoor para meters worden gebruikt. De para meters van de configuratie Act als de eigenschappen van de resource. De configuratie wordt opgeslagen als een bestand met de extensie **. schema. psm1** en neemt de plaats van zowel het MOF-schema als het bron script op in een typische DSC-resource (Zie de [gewenste status van Windows Power shell voor meer informatie over DSC-resources Configuratie resources](resources.md).

## <a name="creating-the-composite-resource"></a>De samengestelde resource maken

In ons voor beeld maken we een configuratie die een aantal bestaande resources aanroept om virtuele machines te configureren. In plaats van de waarden op te geven die moeten worden ingesteld in configuratie blokken, neemt de configuratie een aantal para meters die vervolgens worden gebruikt in de configuratie blokken.

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

Als u de geparametriseerde configuratie wilt gebruiken als een DSC-resource, slaat u deze op in een directory structuur, zoals die van een andere op MOF gebaseerde resource, en geef deze de naam met de extensie **. schema. psm1** . In dit voor beeld noemen we het bestand **xVirtualMachine. schema. psm1**. U moet ook een manifest maken met de naam **xVirtualMachine. psd1** die de volgende regel bevat. Houd er rekening mee dat dit een aanvulling is op **MyDscResources. psd1**, het module manifest voor alle resources in de map **MyDscResources** .

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Wanneer u klaar bent, moet de mapstructuur de volgende zijn.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

De resource kan nu worden gedetecteerd met behulp van de cmdlet Get-Dscresource bieden en de bijbehorende eigenschappen kunnen worden gedetecteerd door die cmdlet of door het automatisch volt ooien van **Ctrl + spatie balk** te gebruiken in de Windows PowerShell ISE.

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

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential ondersteunen

>**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.

De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.

Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele `$PsDscContext`gebruiken.

Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zie ook
### <a name="concepts"></a>Concepten
* [Een aangepaste DSC-resource schrijven met MOF](authoringResourceMOF.md)
* [Aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)