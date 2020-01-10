---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Voorwaardelijke instructies en lussen in configuraties
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736893"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Voorwaardelijke instructies en lussen in een configuratie

U kunt uw [configuratie](configurations.md) dynamischer maken met behulp van Power shell-Flow Control-tref woorden. Dit artikel laat u zien hoe u voorwaardelijke instructies en lussen kunt gebruiken om uw `Configuration` dynamischer te maken. Door voorwaardelijke instructies en lussen met [para meters](add-parameters-to-a-configuration.md) en [configuratie gegevens](configData.md) te combi neren kunt u meer flexibiliteit en controle krijgen bij het compileren van uw `Configuration`.

Net als een functie of een script blok kunt u elke Power shell-taal functie binnen een `Configuration`gebruiken.
De instructies die u gebruikt, worden alleen geëvalueerd wanneer u uw `Configuration` aanroept om een `.mof` bestand te compileren. In de onderstaande voor beelden ziet u scenario's om concepten te demonstreren. Voorwaardelijke instructies en lussen worden vaker gebruikt met para meters en configuratie gegevens.

In dit voor beeld haalt het **service** resource blok de huidige status van een service op het moment van compilatie op om een `.mof` bestand te genereren dat de huidige status behoudt.

> [!NOTE]
> Het gebruik van dynamische resource blokken heeft voor rang op de effectiviteit van IntelliSense. De Power shell-parser kan niet bepalen of de opgegeven waarden acceptabel zijn totdat de `Configuration` is gecompileerd.

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

Daarnaast kunt u een **service** resource Block maken voor elke service op de huidige computer met behulp van een `foreach`-lus.

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

U kunt ook een `Configuration` maken voor machines die online zijn met behulp van een `if`-instructie.

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
> De dynamische resource blokken in de bovenstaande voor beelden verwijzen naar de huidige computer. In dit geval is dat de computer waarop u de `Configuration` maakt, niet op het doel knooppunt.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Samenvatting

In samen vatting kunt u elke Power shell-taal functie binnen een `Configuration`gebruiken.

Dit omvat zaken als:

- Aangepaste objecten
- Hashtabellen
- Teken reeks manipulatie
- Externe communicatie
- WMI en CIM
- Active Directory-objecten
- en meer...

Elke Power shell-code die in een `Configuration` is gedefinieerd, wordt tijdens de compilatie geëvalueerd, maar u kunt ook code in het script plaatsen dat uw `Configuration`bevat. Code buiten het `Configuration` blok wordt uitgevoerd wanneer u uw `Configuration`importeert.

## <a name="see-also"></a>Zie ook

- [Para meters toevoegen aan een configuratie](add-parameters-to-a-configuration.md)
- [Afzonderlijke configuratie gegevens van configuraties](configData.md)
