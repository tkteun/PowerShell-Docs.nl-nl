---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: 'Samengestelde resources: het gebruik van een DSC-configuratie als een resource'
description: In dit artikel wordt beschreven hoe u een samengestelde resource maakt en gebruikt.
ms.openlocfilehash: c1f0e3b45c3a393c04700b5a4bc88be365794820
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667297"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="82479-104">Samengestelde resources: het gebruik van een DSC-configuratie als een resource</span><span class="sxs-lookup"><span data-stu-id="82479-104">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="82479-105">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="82479-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="82479-106">In praktijk situaties kunnen configuraties lang en complex worden, waardoor veel verschillende bronnen worden aangeroepen en een groot aantal eigenschappen kan worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="82479-106">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="82479-107">U kunt deze complexiteit helpen aanpakken door een Windows Power shell desired state Configuration (DSC)-configuratie te gebruiken als een resource voor andere configuraties.</span><span class="sxs-lookup"><span data-stu-id="82479-107">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="82479-108">Dit wordt een samengestelde resource genoemd.</span><span class="sxs-lookup"><span data-stu-id="82479-108">This is called a composite resource.</span></span> <span data-ttu-id="82479-109">Een samengestelde resource is een DSC-configuratie waarvoor para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="82479-109">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="82479-110">De para meters van de configuratie Act als de eigenschappen van de resource.</span><span class="sxs-lookup"><span data-stu-id="82479-110">The parameters of the configuration act as the properties of the resource.</span></span>
<span data-ttu-id="82479-111">De configuratie wordt opgeslagen als een bestand met een `.schema.psm1` extensie.</span><span class="sxs-lookup"><span data-stu-id="82479-111">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="82479-112">Het is de plaats van zowel het MOF-schema als het bron script in een typische DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="82479-112">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="82479-113">Zie [Windows Power shell desired state Configuration resources](resources.md)(Engelstalig) voor meer informatie over DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="82479-113">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="82479-114">De samengestelde resource maken</span><span class="sxs-lookup"><span data-stu-id="82479-114">Creating the composite resource</span></span>

<span data-ttu-id="82479-115">In ons voor beeld maken we een configuratie die een aantal bestaande resources aanroept om virtuele machines te configureren.</span><span class="sxs-lookup"><span data-stu-id="82479-115">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="82479-116">In plaats van de waarden op te geven die moeten worden ingesteld in configuratie blokken, neemt de configuratie in para meters die vervolgens worden gebruikt in de configuratie blokken.</span><span class="sxs-lookup"><span data-stu-id="82479-116">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

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
> <span data-ttu-id="82479-117">DSC biedt momenteel geen ondersteuning voor het plaatsen van samengestelde resources of geneste configuraties binnen een samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="82479-117">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="82479-118">De configuratie opslaan als een samengestelde resource</span><span class="sxs-lookup"><span data-stu-id="82479-118">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="82479-119">Als u de para meter configuratie wilt gebruiken als een DSC-resource, slaat u deze op in een directory structuur zoals die van elke andere op MOF gebaseerde resource, en noemt u deze met een `.schema.psm1` uitbrei ding.</span><span class="sxs-lookup"><span data-stu-id="82479-119">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="82479-120">In dit voor beeld noemen we het bestand `xVirtualMachine.schema.psm1` .</span><span class="sxs-lookup"><span data-stu-id="82479-120">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="82479-121">U moet ook een manifest maken `xVirtualMachine.psd1` met de naam die de volgende regel bevat.</span><span class="sxs-lookup"><span data-stu-id="82479-121">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="82479-122">Dit is een aanvulling op `MyDscResources.psd1` het module manifest voor alle resources in de `MyDscResources` map.</span><span class="sxs-lookup"><span data-stu-id="82479-122">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="82479-123">Wanneer u klaar bent, moet de mapstructuur de volgende zijn.</span><span class="sxs-lookup"><span data-stu-id="82479-123">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="82479-124">De resource kan nu worden gedetecteerd met behulp van de `Get-DscResource` -cmdlet, en de bijbehorende eigenschappen kunnen worden gedetecteerd door de cmdlet of door <kbd>Ctrl</kbd>gebruik te maken van + de functie voor automatisch aanvullen met CTRL-<kbd>ruimte</kbd> in de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="82479-124">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="82479-125">De samengestelde Resource gebruiken</span><span class="sxs-lookup"><span data-stu-id="82479-125">Using the composite resource</span></span>

<span data-ttu-id="82479-126">Vervolgens maken we een configuratie die de samengestelde resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="82479-126">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="82479-127">Deze configuratie roept de xVirtualMachine-samengestelde bron op om een virtuele machine te maken en roept vervolgens de **xComputer** -resource aan om de naam ervan te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="82479-127">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="82479-128">U kunt deze resource ook gebruiken om meerdere Vm's te maken door een matrix van VM-namen door te geven aan de xVirtualMachine-resource.</span><span class="sxs-lookup"><span data-stu-id="82479-128">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="82479-129">PsDscRunAsCredential ondersteunen</span><span class="sxs-lookup"><span data-stu-id="82479-129">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="82479-130">**PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="82479-130">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="82479-131">De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="82479-131">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="82479-132">Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="82479-132">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="82479-133">Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele gebruiken `$PsDscContext` .</span><span class="sxs-lookup"><span data-stu-id="82479-133">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="82479-134">Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:</span><span class="sxs-lookup"><span data-stu-id="82479-134">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="82479-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="82479-135">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="82479-136">Concepten</span><span class="sxs-lookup"><span data-stu-id="82479-136">Concepts</span></span>

- [<span data-ttu-id="82479-137">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="82479-137">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="82479-138">Aan de slag met Windows Power shell desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="82479-138">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
