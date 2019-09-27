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
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="dc9dc-103">Samengestelde resources: Een DSC-configuratie gebruiken als resource</span><span class="sxs-lookup"><span data-stu-id="dc9dc-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="dc9dc-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="dc9dc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="dc9dc-105">In praktijk situaties kunnen configuraties lang en complex worden, waardoor veel verschillende bronnen worden aangeroepen en een groot aantal eigenschappen kan worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="dc9dc-106">U kunt deze complexiteit helpen aanpakken door een Windows Power shell desired state Configuration (DSC)-configuratie te gebruiken als een resource voor andere configuraties.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="dc9dc-107">Dit is een samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-107">We call this a composite resource.</span></span> <span data-ttu-id="dc9dc-108">Een samengestelde resource is een DSC-configuratie waarvoor para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="dc9dc-109">De para meters van de configuratie Act als de eigenschappen van de resource.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="dc9dc-110">De configuratie wordt opgeslagen als een bestand met de extensie **. schema. psm1** en neemt de plaats van zowel het MOF-schema als het bron script op in een typische DSC-resource (Zie de [gewenste status van Windows Power shell voor meer informatie over DSC-resources Configuratie resources](resources.md).</span><span class="sxs-lookup"><span data-stu-id="dc9dc-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="dc9dc-111">De samengestelde resource maken</span><span class="sxs-lookup"><span data-stu-id="dc9dc-111">Creating the composite resource</span></span>

<span data-ttu-id="dc9dc-112">In ons voor beeld maken we een configuratie die een aantal bestaande resources aanroept om virtuele machines te configureren.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="dc9dc-113">In plaats van de waarden op te geven die moeten worden ingesteld in configuratie blokken, neemt de configuratie een aantal para meters die vervolgens worden gebruikt in de configuratie blokken.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="dc9dc-114">De configuratie opslaan als een samengestelde resource</span><span class="sxs-lookup"><span data-stu-id="dc9dc-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="dc9dc-115">Als u de geparametriseerde configuratie wilt gebruiken als een DSC-resource, slaat u deze op in een directory structuur, zoals die van een andere op MOF gebaseerde resource, en geef deze de naam met de extensie **. schema. psm1** .</span><span class="sxs-lookup"><span data-stu-id="dc9dc-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="dc9dc-116">In dit voor beeld noemen we het bestand **xVirtualMachine. schema. psm1**.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-116">For this example, we'll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="dc9dc-117">U moet ook een manifest maken met de naam **xVirtualMachine. psd1** die de volgende regel bevat.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="dc9dc-118">Houd er rekening mee dat dit een aanvulling is op **MyDscResources. psd1**, het module manifest voor alle resources in de map **MyDscResources** .</span><span class="sxs-lookup"><span data-stu-id="dc9dc-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="dc9dc-119">Wanneer u klaar bent, moet de mapstructuur de volgende zijn.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="dc9dc-120">De resource kan nu worden gedetecteerd met behulp van de cmdlet Get-Dscresource bieden en de bijbehorende eigenschappen kunnen worden gedetecteerd door die cmdlet of door het automatisch volt ooien van **Ctrl + spatie balk** te gebruiken in de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="dc9dc-121">De samengestelde Resource gebruiken</span><span class="sxs-lookup"><span data-stu-id="dc9dc-121">Using the composite resource</span></span>

<span data-ttu-id="dc9dc-122">Vervolgens maken we een configuratie die de samengestelde resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="dc9dc-123">Deze configuratie roept de xVirtualMachine-samengestelde bron op om een virtuele machine te maken en roept vervolgens de **xComputer** -resource aan om de naam ervan te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="dc9dc-124">PsDscRunAsCredential ondersteunen</span><span class="sxs-lookup"><span data-stu-id="dc9dc-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="dc9dc-125">**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="dc9dc-126">De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="dc9dc-127">Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-127">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="dc9dc-128">Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele `$PsDscContext`gebruiken.</span><span class="sxs-lookup"><span data-stu-id="dc9dc-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="dc9dc-129">Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:</span><span class="sxs-lookup"><span data-stu-id="dc9dc-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="dc9dc-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc9dc-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="dc9dc-131">Concepten</span><span class="sxs-lookup"><span data-stu-id="dc9dc-131">Concepts</span></span>
* [<span data-ttu-id="dc9dc-132">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="dc9dc-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="dc9dc-133">Aan de slag met Windows Power shell desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="dc9dc-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)