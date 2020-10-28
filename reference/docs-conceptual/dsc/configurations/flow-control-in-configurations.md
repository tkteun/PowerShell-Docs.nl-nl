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
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Voorwaardelijke instructies en lussen in een configuratie

U kunt uw [configuratie](configurations.md) dynamischer maken met behulp van Power shell-Flow Control-tref woorden. Dit artikel laat u zien hoe u voorwaardelijke instructies en lussen kunt gebruiken om uw `Configuration` dynamischer te maken. Als u voorwaardelijke instructies en lussen met [para meters](add-parameters-to-a-configuration.md) en [configuratie gegevens](configData.md) combineert, hebt u meer flexibiliteit en controle bij het compileren van uw `Configuration` .

Net als een functie of een script blok kunt u elke Power shell-taal functie binnen een gebruiken `Configuration` . De instructies die u gebruikt, worden alleen geëvalueerd wanneer u uw `Configuration` voor het compileren van een bestand aanroept `.mof` . In de onderstaande voor beelden ziet u scenario's om concepten te demonstreren. Voorwaardelijke instructies en lussen worden vaker gebruikt met para meters en configuratie gegevens.

In dit voor beeld haalt het **service** resource blok de huidige status van een service op tijdens het compileren om een bestand te genereren `.mof` dat de huidige status behoudt.

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

Daarnaast kunt u met een lus een **service** resource blok maken voor elke service op de huidige computer `foreach` .

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

U kunt ook een `Configuration` alleen voor computers maken die online zijn met behulp van een- `if` instructie.

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
> De dynamische resource blokken in de bovenstaande voor beelden verwijzen naar de huidige computer. In dit geval is dat de computer waarop u de `Configuration` op, niet het doel knooppunt.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Samenvatting

In samen vatting kunt u elke Power shell-taal functie binnen een gebruiken `Configuration` .

Dit omvat zaken als:

- Aangepaste objecten
- Hashtabellen
- Teken reeks manipulatie
- Externe communicatie
- WMI en CIM
- Active Directory-objecten
- en meer...

Elke Power shell-code die in a `Configuration` is gedefinieerd, wordt tijdens de compilatie geëvalueerd, maar u kunt ook code in het script plaatsen dat uw bevat `Configuration` . Code buiten het `Configuration` blok wordt uitgevoerd wanneer u uw importeert `Configuration` .

## <a name="see-also"></a>Zie ook

- [Para meters toevoegen aan een configuratie](add-parameters-to-a-configuration.md)
- [Configuratiegegevens van configuraties scheiden](configData.md)
