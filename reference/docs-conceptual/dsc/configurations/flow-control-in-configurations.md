---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Voorwaardelijke instructies en lussen in configuraties
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736893"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="32538-103">Voorwaardelijke instructies en lussen in een configuratie</span><span class="sxs-lookup"><span data-stu-id="32538-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="32538-104">U kunt uw [configuratie](configurations.md) dynamischer maken met behulp van Power shell-Flow Control-tref woorden.</span><span class="sxs-lookup"><span data-stu-id="32538-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="32538-105">Dit artikel laat u zien hoe u voorwaardelijke instructies en lussen kunt gebruiken om uw `Configuration` dynamischer te maken.</span><span class="sxs-lookup"><span data-stu-id="32538-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="32538-106">Als u voorwaardelijke instructies en lussen met [para meters](add-parameters-to-a-configuration.md) en [configuratie gegevens](configData.md) combineert, hebt u meer flexibiliteit en controle `Configuration`bij het compileren van uw.</span><span class="sxs-lookup"><span data-stu-id="32538-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="32538-107">Net als een functie of een script blok kunt u elke Power shell-taal functie binnen een `Configuration`gebruiken.</span><span class="sxs-lookup"><span data-stu-id="32538-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="32538-108">De instructies die u gebruikt, worden alleen geëvalueerd wanneer u uw `Configuration` voor het compileren van een `.mof` bestand aanroept.</span><span class="sxs-lookup"><span data-stu-id="32538-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="32538-109">In de onderstaande voor beelden ziet u scenario's om concepten te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="32538-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="32538-110">Voorwaardelijke instructies en lussen worden vaker gebruikt met para meters en configuratie gegevens.</span><span class="sxs-lookup"><span data-stu-id="32538-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="32538-111">In dit voor beeld haalt het **service** resource blok de huidige status van een service op tijdens het compileren om `.mof` een bestand te genereren dat de huidige status behoudt.</span><span class="sxs-lookup"><span data-stu-id="32538-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="32538-112">Het gebruik van dynamische resource blokken heeft voor rang op de effectiviteit van IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="32538-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="32538-113">De Power shell-parser kan niet bepalen of de opgegeven waarden acceptabel `Configuration` zijn totdat de is gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="32538-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

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

<span data-ttu-id="32538-114">Daarnaast kunt u met een `foreach` lus een **service** resource blok maken voor elke service op de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="32538-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

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

<span data-ttu-id="32538-115">U kunt ook een `Configuration` alleen voor computers maken die online zijn met behulp `if` van een-instructie.</span><span class="sxs-lookup"><span data-stu-id="32538-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

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
> <span data-ttu-id="32538-116">De dynamische resource blokken in de bovenstaande voor beelden verwijzen naar de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="32538-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="32538-117">In dit geval is dat de computer waarop u de `Configuration` op, niet het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="32538-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="32538-118">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="32538-118">Summary</span></span>

<span data-ttu-id="32538-119">In samen vatting kunt u elke Power shell-taal functie binnen `Configuration`een gebruiken.</span><span class="sxs-lookup"><span data-stu-id="32538-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="32538-120">Dit omvat zaken als:</span><span class="sxs-lookup"><span data-stu-id="32538-120">This includes things like:</span></span>

- <span data-ttu-id="32538-121">Aangepaste objecten</span><span class="sxs-lookup"><span data-stu-id="32538-121">Custom Objects</span></span>
- <span data-ttu-id="32538-122">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="32538-122">Hashtables</span></span>
- <span data-ttu-id="32538-123">Teken reeks manipulatie</span><span class="sxs-lookup"><span data-stu-id="32538-123">String manipulation</span></span>
- <span data-ttu-id="32538-124">Externe communicatie</span><span class="sxs-lookup"><span data-stu-id="32538-124">Remoting</span></span>
- <span data-ttu-id="32538-125">WMI en CIM</span><span class="sxs-lookup"><span data-stu-id="32538-125">WMI and CIM</span></span>
- <span data-ttu-id="32538-126">Active Directory-objecten</span><span class="sxs-lookup"><span data-stu-id="32538-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="32538-127">en meer...</span><span class="sxs-lookup"><span data-stu-id="32538-127">and more...</span></span>

<span data-ttu-id="32538-128">Elke Power shell-code die `Configuration` in a is gedefinieerd, wordt tijdens de compilatie geëvalueerd, maar u kunt ook code in `Configuration`het script plaatsen dat uw bevat.</span><span class="sxs-lookup"><span data-stu-id="32538-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="32538-129">Code buiten het `Configuration` blok wordt uitgevoerd wanneer u uw `Configuration`importeert.</span><span class="sxs-lookup"><span data-stu-id="32538-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="32538-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="32538-130">See also</span></span>

- [<span data-ttu-id="32538-131">Para meters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="32538-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="32538-132">Configuratiegegevens van configuraties scheiden</span><span class="sxs-lookup"><span data-stu-id="32538-132">Separate Configuration data from Configurations</span></span>](configData.md)
