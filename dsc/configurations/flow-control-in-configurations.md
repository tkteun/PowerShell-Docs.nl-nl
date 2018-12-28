---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Voorwaardelijke instructies en lussen in configuraties
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403919"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="75242-103">Voorwaardelijke instructies en lussen in configuraties</span><span class="sxs-lookup"><span data-stu-id="75242-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="75242-104">Kunt u uw [configuraties](configurations.md) meer dynamische met behulp van PowerShell-gegevenstransportbesturing trefwoorden.</span><span class="sxs-lookup"><span data-stu-id="75242-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="75242-105">Dit artikel wordt beschreven hoe u voorwaardelijke instructies en lussen gebruiken kunt om uw configuraties meer dynamische.</span><span class="sxs-lookup"><span data-stu-id="75242-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="75242-106">Voorwaardelijke combineren en lussen met [parameters](add-parameters-to-a-configuration.md) en [configuratiegegevens](configData.md) kunt u meer flexibiliteit en controle bij het compileren van uw configuraties.</span><span class="sxs-lookup"><span data-stu-id="75242-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="75242-107">Net als een functie of een scriptblok, kunt u een PowerShell-taal in een configuratie.</span><span class="sxs-lookup"><span data-stu-id="75242-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="75242-108">Bij het aanroepen van de configuratie voor het compileren van een bestand '.mof' worden alleen de instructies die met u geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="75242-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="75242-109">De voorbeelden hieronder ziet u eenvoudige scenario's ter illustratie van concepten.</span><span class="sxs-lookup"><span data-stu-id="75242-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="75242-110">Voorwaarden zijn lussen vaker worden gebruikt met parameters en configuratiegegevens.</span><span class="sxs-lookup"><span data-stu-id="75242-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="75242-111">In dit eenvoudige voorbeeld de **Service** resource blok haalt de huidige status van een service bij het compileren om een '.mof'-bestand die wordt onderhouden door de huidige status te genereren.</span><span class="sxs-lookup"><span data-stu-id="75242-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="75242-112">Met behulp van dynamische Resource blokkeert, wordt de effectiviteit van Intellisense voorrang.</span><span class="sxs-lookup"><span data-stu-id="75242-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="75242-113">De PowerShell-parser kan niet bepalen of de opgegeven waarden acceptabel totdat de configuratie is gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="75242-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="75242-114">Bovendien kunt u een **Service** blokkeren resource voor elke service op de huidige computer, met behulp van een `foreach` lus.</span><span class="sxs-lookup"><span data-stu-id="75242-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="75242-115">U kunt ook alleen configuraties voor computers die online, zijn met behulp van een eenvoudige maken `if` instructie.</span><span class="sxs-lookup"><span data-stu-id="75242-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="75242-116">De dynamische resource wordt geblokkeerd in de bovenstaande voorbeelden de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="75242-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="75242-117">In dit geval, die de computer die u bij het ontwerpen van de configuratie op, niet het doel-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="75242-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="75242-118">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="75242-118">Summary</span></span>

<span data-ttu-id="75242-119">Kortom, kunt u een PowerShell-taal in een configuratie.</span><span class="sxs-lookup"><span data-stu-id="75242-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="75242-120">Dit omvat items zoals:</span><span class="sxs-lookup"><span data-stu-id="75242-120">This includes things like:</span></span>

- <span data-ttu-id="75242-121">Aangepaste objecten</span><span class="sxs-lookup"><span data-stu-id="75242-121">Custom Objects</span></span>
- <span data-ttu-id="75242-122">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="75242-122">Hashtables</span></span>
- <span data-ttu-id="75242-123">Manipuleren van tekenreeksen</span><span class="sxs-lookup"><span data-stu-id="75242-123">String manipulation</span></span>
- <span data-ttu-id="75242-124">Externe toegang</span><span class="sxs-lookup"><span data-stu-id="75242-124">Remoting</span></span>
- <span data-ttu-id="75242-125">WMI- en CIM</span><span class="sxs-lookup"><span data-stu-id="75242-125">WMI and CIM</span></span>
- <span data-ttu-id="75242-126">Active Directory-objecten</span><span class="sxs-lookup"><span data-stu-id="75242-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="75242-127">en nog veel meer...</span><span class="sxs-lookup"><span data-stu-id="75242-127">and more...</span></span>

<span data-ttu-id="75242-128">Een PowerShell-code die is gedefinieerd in een configuratie met een compileren worden geëvalueerd, maar u kunt ook code plaatsen in het script dat uw configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="75242-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="75242-129">Code buiten het blok configuratie wordt uitgevoerd bij het importeren van uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="75242-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="75242-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75242-130">See also</span></span>

- [<span data-ttu-id="75242-131">Voeg parameters toe aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="75242-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="75242-132">Configuratiegegevens te scheiden van configuraties</span><span class="sxs-lookup"><span data-stu-id="75242-132">Separate Configuration data from Configurations</span></span>](configData.md)
