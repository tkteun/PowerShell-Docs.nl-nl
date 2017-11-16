---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Aan de slag met PowerShell Desired State Configuration
ms.openlocfilehash: 403badd11749cfa5c6a5d07e1b537fa3a5f954da
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a>Aan de slag met PowerShell Desired State Configuration #

Deze handleiding wordt beschreven hoe u begint met het maken van PowerShell Desired State Configuration documenten en toegepast op computers. Er wordt vanuit gegaan enigszins bekend bent met PowerShell-cmdlets, modules en -functies. 


## <a name="create-a-configuration"></a>Een configuratie maken ##

[**Configuraties** ](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) zijn documenten die worden beschreven van een omgeving. Omgevingen bestaan uit '**knooppunten**', die meestal worden virtuele of fysieke machines. 

Configuraties kunnen worden geleverd in verschillende vormen. De eenvoudigste manier om te maken van een nieuwe configuratie is een ps1-bestand (PowerShell-script) te maken. U doet dit door uw keuze-editor te openen. De PowerShell ISE is een goede keuze, omdat deze DSC systeemeigen begrijpt. De volgende opslaan als een PS1:

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a>Onderdelen van een configuratie ##
**Configuratie** is een sleutelwoord die is toegevoegd aan PowerShell 4.0. Dit geeft aan dat een speciaal type van de PowerShell-functie die wordt gebruikt door Desired State Configuration. In dit voorbeeld is de functie myFirstConfiguration naam. 

De volgende regel wordt een importinstructie, vergelijkbaar met het importeren van een module. Dit zal later worden besproken.

'Knooppunt' definieert de naam van de machine die deze configuratie wordt toegepast. Hoewel deze configuratie lokaal bewerkt wordt, kunnen configuraties externe knooppunten bereiken en configureren. 

Knooppunten kunnen namen voor machines of IP-adressen zijn. U kunt meerdere knooppunten in een configuratie voor één document hebben. Met behulp van [configuratiegegevens](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), u kunt ook van toepassing op meerdere knooppunten dezelfde configuratie hebben. Het knooppunt is in dit geval 'localhost' - wat betekent de lokale computer dat. 

Het volgende item is een [ **resource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources). Resources zijn de bouwstenen van configuraties. Elke bron is een module die de logica van de implementatie van een enkele aspect van een machine definieert. U kunt elke resource weergeven op uw computer door te voeren **Get-DscResource** in PowerShell. Resources moet aanwezig zijn op de lokale computer en geïmporteerd voordat ze kunnen worden gebruikt in een configuratie met **importeren DscResource** die zich op de tweede regel met deze configuratie. 

**Een configuratie vast te stellen**

Als het bovenstaande script is opgeslagen en worden uitgevoerd, wordt geen uitvoer geproduceerd. Dit is omdat een configuratie alleen een functie is en het bovenstaande script heeft de functie gedefinieerd, maar nog niet uitvoeren. Nadat de functie is gedefinieerd, moet worden aangeroepen:
```powershell
myFirstConfiguration
```

Tijdens de uitvoering van functies van de configuratie van de configuratie valideren is geldig. Er is geen syntaxisfouten, resources moet alle verplichte parameters gedefinieerd en alle resources moeten worden geïmporteerd voordat wordt uitgevoerd.

Zodra de configuratie wordt uitgevoerd, wordt een map gemaakt met de naam van de configuratie die een **. MOF-bestand** voor elk knooppunt in de configuratie. De. MOF-bestand is een op standaarden gebaseerde management-indeling die wordt gebruikt door PowerShell DSC om te communiceren via het netwerk.

Op te nemen in de configuratie:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Hiermee maakt u een PowerShell-taak die gezocht naar de knooppunten in de configuratie en configureert u deze. Als de uitvoer van de taak wilt weergeven, gebruikt - wachttijd. 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

