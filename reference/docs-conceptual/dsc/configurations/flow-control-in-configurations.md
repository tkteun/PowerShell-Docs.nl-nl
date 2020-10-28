---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Voorwaardelijke instructies en lussen in configuraties
description: In dit artikel wordt beschreven hoe u voorwaardelijke instructies en lussen kunt gebruiken om uw configuratie dynamischer te maken. Door voorwaardelijke instructies en lussen met para meters en configuratie gegevens te combi neren, kunt u meer flexibiliteit en controle krijgen bij het compileren van uw configuratie.
ms.openlocfilehash: 7af8a360c17a0842fa2b95d1d1fb288323c327ef
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658454"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="aea86-105">Voorwaardelijke instructies en lussen in een configuratie</span><span class="sxs-lookup"><span data-stu-id="aea86-105">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="aea86-106">U kunt uw [configuratie](configurations.md) dynamischer maken met behulp van Power shell-Flow Control-tref woorden.</span><span class="sxs-lookup"><span data-stu-id="aea86-106">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="aea86-107">Dit artikel laat u zien hoe u voorwaardelijke instructies en lussen kunt gebruiken om uw `Configuration` dynamischer te maken.</span><span class="sxs-lookup"><span data-stu-id="aea86-107">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="aea86-108">Als u voorwaardelijke instructies en lussen met [para meters](add-parameters-to-a-configuration.md) en [configuratie gegevens](configData.md) combineert, hebt u meer flexibiliteit en controle bij het compileren van uw `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="aea86-108">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="aea86-109">Net als een functie of een script blok kunt u elke Power shell-taal functie binnen een gebruiken `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="aea86-109">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span> <span data-ttu-id="aea86-110">De instructies die u gebruikt, worden alleen geëvalueerd wanneer u uw `Configuration` voor het compileren van een bestand aanroept `.mof` .</span><span class="sxs-lookup"><span data-stu-id="aea86-110">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="aea86-111">In de onderstaande voor beelden ziet u scenario's om concepten te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="aea86-111">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="aea86-112">Voorwaardelijke instructies en lussen worden vaker gebruikt met para meters en configuratie gegevens.</span><span class="sxs-lookup"><span data-stu-id="aea86-112">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="aea86-113">In dit voor beeld haalt het **service** resource blok de huidige status van een service op tijdens het compileren om een bestand te genereren `.mof` dat de huidige status behoudt.</span><span class="sxs-lookup"><span data-stu-id="aea86-113">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="aea86-114">Het gebruik van dynamische resource blokken heeft voor rang op de effectiviteit van IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="aea86-114">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="aea86-115">De Power shell-parser kan niet bepalen of de opgegeven waarden acceptabel zijn totdat de `Configuration` is gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="aea86-115">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

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

<span data-ttu-id="aea86-116">Daarnaast kunt u met een lus een **service** resource blok maken voor elke service op de huidige computer `foreach` .</span><span class="sxs-lookup"><span data-stu-id="aea86-116">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

<span data-ttu-id="aea86-117">U kunt ook een `Configuration` alleen voor computers maken die online zijn met behulp van een- `if` instructie.</span><span class="sxs-lookup"><span data-stu-id="aea86-117">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="aea86-118">De dynamische resource blokken in de bovenstaande voor beelden verwijzen naar de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="aea86-118">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="aea86-119">In dit geval is dat de computer waarop u de `Configuration` op, niet het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="aea86-119">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="aea86-120">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="aea86-120">Summary</span></span>

<span data-ttu-id="aea86-121">In samen vatting kunt u elke Power shell-taal functie binnen een gebruiken `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="aea86-121">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="aea86-122">Dit omvat zaken als:</span><span class="sxs-lookup"><span data-stu-id="aea86-122">This includes things like:</span></span>

- <span data-ttu-id="aea86-123">Aangepaste objecten</span><span class="sxs-lookup"><span data-stu-id="aea86-123">Custom Objects</span></span>
- <span data-ttu-id="aea86-124">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="aea86-124">Hashtables</span></span>
- <span data-ttu-id="aea86-125">Teken reeks manipulatie</span><span class="sxs-lookup"><span data-stu-id="aea86-125">String manipulation</span></span>
- <span data-ttu-id="aea86-126">Externe communicatie</span><span class="sxs-lookup"><span data-stu-id="aea86-126">Remoting</span></span>
- <span data-ttu-id="aea86-127">WMI en CIM</span><span class="sxs-lookup"><span data-stu-id="aea86-127">WMI and CIM</span></span>
- <span data-ttu-id="aea86-128">Active Directory-objecten</span><span class="sxs-lookup"><span data-stu-id="aea86-128">ActiveDirectory objects</span></span>
- <span data-ttu-id="aea86-129">en meer...</span><span class="sxs-lookup"><span data-stu-id="aea86-129">and more...</span></span>

<span data-ttu-id="aea86-130">Elke Power shell-code die in a `Configuration` is gedefinieerd, wordt tijdens de compilatie geëvalueerd, maar u kunt ook code in het script plaatsen dat uw bevat `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="aea86-130">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="aea86-131">Code buiten het `Configuration` blok wordt uitgevoerd wanneer u uw importeert `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="aea86-131">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="aea86-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="aea86-132">See also</span></span>

- [<span data-ttu-id="aea86-133">Para meters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="aea86-133">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="aea86-134">Configuratiegegevens van configuraties scheiden</span><span class="sxs-lookup"><span data-stu-id="aea86-134">Separate Configuration data from Configurations</span></span>](configData.md)
