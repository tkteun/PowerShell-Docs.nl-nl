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
# <a name="conditional-statements-and-loops-in-configurations"></a>Voorwaardelijke instructies en lussen in configuraties

Kunt u uw [configuraties](configurations.md) meer dynamische met behulp van PowerShell-gegevenstransportbesturing trefwoorden. Dit artikel wordt beschreven hoe u voorwaardelijke instructies en lussen gebruiken kunt om uw configuraties meer dynamische. Voorwaardelijke combineren en lussen met [parameters](add-parameters-to-a-configuration.md) en [configuratiegegevens](configData.md) kunt u meer flexibiliteit en controle bij het compileren van uw configuraties.

Net als een functie of een scriptblok, kunt u een PowerShell-taal in een configuratie. Bij het aanroepen van de configuratie voor het compileren van een bestand '.mof' worden alleen de instructies die met u geëvalueerd. De voorbeelden hieronder ziet u eenvoudige scenario's ter illustratie van concepten. Voorwaarden zijn lussen vaker worden gebruikt met parameters en configuratiegegevens.

In dit eenvoudige voorbeeld de **Service** resource blok haalt de huidige status van een service bij het compileren om een '.mof'-bestand die wordt onderhouden door de huidige status te genereren.

> [!NOTE]
> Met behulp van dynamische Resource blokkeert, wordt de effectiviteit van Intellisense voorrang. De PowerShell-parser kan niet bepalen of de opgegeven waarden acceptabel totdat de configuratie is gecompileerd.

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

Bovendien kunt u een **Service** blokkeren resource voor elke service op de huidige computer, met behulp van een `foreach` lus.

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

U kunt ook alleen configuraties voor computers die online, zijn met behulp van een eenvoudige maken `if` instructie.

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
> De dynamische resource wordt geblokkeerd in de bovenstaande voorbeelden de huidige computer. In dit geval, die de computer die u bij het ontwerpen van de configuratie op, niet het doel-knooppunt.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Samenvatting

Kortom, kunt u een PowerShell-taal in een configuratie.

Dit omvat items zoals:

- Aangepaste objecten
- Hashtabellen
- Manipuleren van tekenreeksen
- Externe toegang
- WMI- en CIM
- Active Directory-objecten
- en nog veel meer...

Een PowerShell-code die is gedefinieerd in een configuratie met een compileren worden geëvalueerd, maar u kunt ook code plaatsen in het script dat uw configuratie bevat. Code buiten het blok configuratie wordt uitgevoerd bij het importeren van uw configuratie.

## <a name="see-also"></a>Zie ook

- [Voeg parameters toe aan een configuratie](add-parameters-to-a-configuration.md)
- [Configuratiegegevens te scheiden van configuraties](configData.md)
