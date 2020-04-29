---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: 'Samengestelde resources: met behulp van een DSC-configuratie als resource'
ms.openlocfilehash: 79fe94bd5bab8fa460714e5994d2e2487f302410
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75415894"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="b9b58-103">Samengestelde resources: het gebruik van een DSC-configuratie als een resource</span><span class="sxs-lookup"><span data-stu-id="b9b58-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="b9b58-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="b9b58-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b9b58-105">In praktijk situaties kunnen configuraties lang en complex worden, waardoor veel verschillende bronnen worden aangeroepen en een groot aantal eigenschappen kan worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="b9b58-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="b9b58-106">U kunt deze complexiteit helpen aanpakken door een Windows Power shell desired state Configuration (DSC)-configuratie te gebruiken als een resource voor andere configuraties.</span><span class="sxs-lookup"><span data-stu-id="b9b58-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="b9b58-107">Dit wordt een samengestelde resource genoemd.</span><span class="sxs-lookup"><span data-stu-id="b9b58-107">This is called a composite resource.</span></span> <span data-ttu-id="b9b58-108">Een samengestelde resource is een DSC-configuratie waarvoor para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9b58-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="b9b58-109">De para meters van de configuratie Act als de eigenschappen van de resource.</span><span class="sxs-lookup"><span data-stu-id="b9b58-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="b9b58-110">De configuratie wordt opgeslagen als een bestand met een `.schema.psm1` extensie.</span><span class="sxs-lookup"><span data-stu-id="b9b58-110">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="b9b58-111">Het is de plaats van zowel het MOF-schema als het bron script in een typische DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="b9b58-111">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="b9b58-112">Zie [Windows Power shell desired state Configuration resources](resources.md)(Engelstalig) voor meer informatie over DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="b9b58-112">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="b9b58-113">De samengestelde resource maken</span><span class="sxs-lookup"><span data-stu-id="b9b58-113">Creating the composite resource</span></span>

<span data-ttu-id="b9b58-114">In ons voor beeld maken we een configuratie die een aantal bestaande resources aanroept om virtuele machines te configureren.</span><span class="sxs-lookup"><span data-stu-id="b9b58-114">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="b9b58-115">In plaats van de waarden op te geven die moeten worden ingesteld in configuratie blokken, neemt de configuratie in para meters die vervolgens worden gebruikt in de configuratie blokken.</span><span class="sxs-lookup"><span data-stu-id="b9b58-115">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

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
> <span data-ttu-id="b9b58-116">DSC biedt momenteel geen ondersteuning voor het plaatsen van samengestelde resources of geneste configuraties binnen een samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="b9b58-116">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="b9b58-117">De configuratie opslaan als een samengestelde resource</span><span class="sxs-lookup"><span data-stu-id="b9b58-117">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="b9b58-118">Als u de para meter configuratie wilt gebruiken als een DSC-resource, slaat u deze op in een directory structuur zoals die van elke andere op MOF gebaseerde resource, `.schema.psm1` en noemt u deze met een uitbrei ding.</span><span class="sxs-lookup"><span data-stu-id="b9b58-118">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="b9b58-119">In dit voor beeld noemen we het bestand `xVirtualMachine.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="b9b58-119">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="b9b58-120">U moet ook een manifest maken met de `xVirtualMachine.psd1` naam die de volgende regel bevat.</span><span class="sxs-lookup"><span data-stu-id="b9b58-120">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="b9b58-121">Dit is een aanvulling op `MyDscResources.psd1`het module manifest voor alle resources in de `MyDscResources` map.</span><span class="sxs-lookup"><span data-stu-id="b9b58-121">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="b9b58-122">Wanneer u klaar bent, moet de mapstructuur de volgende zijn.</span><span class="sxs-lookup"><span data-stu-id="b9b58-122">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="b9b58-123">De resource kan nu worden gedetecteerd met behulp van `Get-DscResource` de-cmdlet, en de bijbehorende eigenschappen kunnen worden gedetecteerd door de cmdlet of door gebruik te maken van de functie voor automatisch aanvullen met <kbd>CTRL</kbd>+-<kbd>ruimte</kbd> in de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b9b58-123">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="b9b58-124">De samengestelde Resource gebruiken</span><span class="sxs-lookup"><span data-stu-id="b9b58-124">Using the composite resource</span></span>

<span data-ttu-id="b9b58-125">Vervolgens maken we een configuratie die de samengestelde resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="b9b58-125">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="b9b58-126">Deze configuratie roept de xVirtualMachine-samengestelde bron op om een virtuele machine te maken en roept vervolgens de **xComputer** -resource aan om de naam ervan te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b9b58-126">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="b9b58-127">U kunt deze resource ook gebruiken om meerdere Vm's te maken door een matrix van VM-namen door te geven aan de xVirtualMachine-resource.</span><span class="sxs-lookup"><span data-stu-id="b9b58-127">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="b9b58-128">PsDscRunAsCredential ondersteunen</span><span class="sxs-lookup"><span data-stu-id="b9b58-128">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="b9b58-129">**PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="b9b58-129">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="b9b58-130">De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="b9b58-130">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="b9b58-131">Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9b58-131">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="b9b58-132">Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele `$PsDscContext`gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b9b58-132">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="b9b58-133">Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:</span><span class="sxs-lookup"><span data-stu-id="b9b58-133">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="b9b58-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9b58-134">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="b9b58-135">Concepten</span><span class="sxs-lookup"><span data-stu-id="b9b58-135">Concepts</span></span>

- [<span data-ttu-id="b9b58-136">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="b9b58-136">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="b9b58-137">Aan de slag met Windows Power shell desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="b9b58-137">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
