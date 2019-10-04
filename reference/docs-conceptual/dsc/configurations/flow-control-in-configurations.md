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
# <a name="conditional-statements-and-loops-in-configurations"></a>Voorwaardelijke instructies en lussen in configuraties

U kunt uw [configuraties](configurations.md) dynamisch maken met behulp van Power shell-Flow Control-tref woorden. In dit artikel wordt uitgelegd hoe u voorwaardelijke instructies kunt gebruiken en lussen om uw configuraties dynamischer te maken. Door voorwaardelijke en lussen te combi neren met [para meters](add-parameters-to-a-configuration.md) en [configuratie gegevens](configData.md) hebt u meer flexibiliteit en controle bij het compileren van uw configuraties.

Net als een functie of een script blok kunt u elke Power shell-taal in een configuratie gebruiken. De instructies die u gebruikt, worden alleen geëvalueerd wanneer u de configuratie aanroept om een '. MOF-bestand ' te compileren. In de onderstaande voor beelden ziet u eenvoudige scenario's om concepten te demonstreren. Voor waarden zijn lussen die vaker worden gebruikt met para meters en configuratie gegevens.

In dit eenvoudige voor beeld haalt het **service** resource blok de huidige status van een service op tijdens het compileren om een '. MOF-bestand ' te genereren dat de huidige status behoudt.

> [!NOTE]
> Het gebruik van dynamische resource blokken heeft voor rang op de effectiviteit van IntelliSense. De Power shell-parser kan niet bepalen of de opgegeven waarden acceptabel zijn totdat de configuratie is gecompileerd.

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

Daarnaast kunt u een **service** blok resource maken voor elke service op de huidige machine, met behulp van een `foreach`-lus.

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

U kunt ook configuraties maken voor machines die online zijn, met behulp van een eenvoudige `if`-instructie.

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
> De dynamische resource blokken in de bovenstaande voor beelden verwijzen naar de huidige computer. In dit geval is dat de computer waarop u de configuratie wilt ontwerpen, niet op het doel knooppunt.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Samenvatting

In samen vatting kunt u elke Power shell-taal in een configuratie gebruiken.

Dit omvat zaken als:

- Aangepaste objecten
- Hashtabellen
- Teken reeks manipulatie
- Externe communicatie
- WMI en CIM
- Active Directory-objecten
- en nog veel meer...

Elke Power shell-code die in een configuratie is gedefinieerd, wordt een compilatie tijd geëvalueerd, maar u kunt ook code in het script plaatsen dat uw configuratie bevat. Code buiten het configuratie blok wordt uitgevoerd wanneer u de configuratie importeert.

## <a name="see-also"></a>Zie ook

- [Para meters toevoegen aan een configuratie](add-parameters-to-a-configuration.md)
- [Afzonderlijke configuratie gegevens van configuraties](configData.md)
