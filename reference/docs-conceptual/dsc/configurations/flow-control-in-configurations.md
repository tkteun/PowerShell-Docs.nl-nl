---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Voorwaardelijke instructies en lussen in configuraties
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942032"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="e04ec-103">Voorwaardelijke instructies en lussen in configuraties</span><span class="sxs-lookup"><span data-stu-id="e04ec-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="e04ec-104">U kunt uw [configuraties](configurations.md) dynamisch maken met behulp van Power shell-Flow Control-tref woorden.</span><span class="sxs-lookup"><span data-stu-id="e04ec-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="e04ec-105">In dit artikel wordt uitgelegd hoe u voorwaardelijke instructies kunt gebruiken en lussen om uw configuraties dynamischer te maken.</span><span class="sxs-lookup"><span data-stu-id="e04ec-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="e04ec-106">Door voorwaardelijke en lussen te combi neren met [para meters](add-parameters-to-a-configuration.md) en [configuratie gegevens](configData.md) hebt u meer flexibiliteit en controle bij het compileren van uw configuraties.</span><span class="sxs-lookup"><span data-stu-id="e04ec-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="e04ec-107">Net als een functie of een script blok kunt u elke Power shell-taal in een configuratie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e04ec-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="e04ec-108">De instructies die u gebruikt, worden alleen geëvalueerd wanneer u de configuratie aanroept om een '. MOF-bestand ' te compileren.</span><span class="sxs-lookup"><span data-stu-id="e04ec-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="e04ec-109">In de onderstaande voor beelden ziet u eenvoudige scenario's om concepten te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="e04ec-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="e04ec-110">Voor waarden zijn lussen die vaker worden gebruikt met para meters en configuratie gegevens.</span><span class="sxs-lookup"><span data-stu-id="e04ec-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="e04ec-111">In dit eenvoudige voor beeld haalt het **service** resource blok de huidige status van een service op tijdens het compileren om een '. MOF-bestand ' te genereren dat de huidige status behoudt.</span><span class="sxs-lookup"><span data-stu-id="e04ec-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="e04ec-112">Het gebruik van dynamische resource blokken heeft voor rang op de effectiviteit van IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e04ec-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="e04ec-113">De Power shell-parser kan niet bepalen of de opgegeven waarden acceptabel zijn totdat de configuratie is gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="e04ec-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="e04ec-114">Daarnaast kunt u een **service** blok resource maken voor elke service op de huidige machine, met behulp van een `foreach`-lus.</span><span class="sxs-lookup"><span data-stu-id="e04ec-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="e04ec-115">U kunt ook configuraties maken voor machines die online zijn, met behulp van een eenvoudige `if`-instructie.</span><span class="sxs-lookup"><span data-stu-id="e04ec-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="e04ec-116">De dynamische resource blokken in de bovenstaande voor beelden verwijzen naar de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="e04ec-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="e04ec-117">In dit geval is dat de computer waarop u de configuratie wilt ontwerpen, niet op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="e04ec-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="e04ec-118">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="e04ec-118">Summary</span></span>

<span data-ttu-id="e04ec-119">In samen vatting kunt u elke Power shell-taal in een configuratie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e04ec-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="e04ec-120">Dit omvat zaken als:</span><span class="sxs-lookup"><span data-stu-id="e04ec-120">This includes things like:</span></span>

- <span data-ttu-id="e04ec-121">Aangepaste objecten</span><span class="sxs-lookup"><span data-stu-id="e04ec-121">Custom Objects</span></span>
- <span data-ttu-id="e04ec-122">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="e04ec-122">Hashtables</span></span>
- <span data-ttu-id="e04ec-123">Teken reeks manipulatie</span><span class="sxs-lookup"><span data-stu-id="e04ec-123">String manipulation</span></span>
- <span data-ttu-id="e04ec-124">Externe communicatie</span><span class="sxs-lookup"><span data-stu-id="e04ec-124">Remoting</span></span>
- <span data-ttu-id="e04ec-125">WMI en CIM</span><span class="sxs-lookup"><span data-stu-id="e04ec-125">WMI and CIM</span></span>
- <span data-ttu-id="e04ec-126">Active Directory-objecten</span><span class="sxs-lookup"><span data-stu-id="e04ec-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="e04ec-127">en nog veel meer...</span><span class="sxs-lookup"><span data-stu-id="e04ec-127">and more...</span></span>

<span data-ttu-id="e04ec-128">Elke Power shell-code die in een configuratie is gedefinieerd, wordt een compilatie tijd geëvalueerd, maar u kunt ook code in het script plaatsen dat uw configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="e04ec-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="e04ec-129">Code buiten het configuratie blok wordt uitgevoerd wanneer u de configuratie importeert.</span><span class="sxs-lookup"><span data-stu-id="e04ec-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="e04ec-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e04ec-130">See also</span></span>

- [<span data-ttu-id="e04ec-131">Para meters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="e04ec-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="e04ec-132">Afzonderlijke configuratie gegevens van configuraties</span><span class="sxs-lookup"><span data-stu-id="e04ec-132">Separate Configuration data from Configurations</span></span>](configData.md)
