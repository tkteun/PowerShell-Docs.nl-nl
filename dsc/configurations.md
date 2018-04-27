---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-configuraties
ms.openlocfilehash: ffeb953048c0a65352618d2ab141ee10ead4c663
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2018
---
# <a name="dsc-configurations"></a>DSC-configuraties

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-configuraties zijn PowerShell-scripts die een speciaal type van de functie definiëren.
Als u een configuratie definieert, u het sleutelwoord PowerShell **configuratie**.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

Sla het script als een ps1-bestand.

## <a name="configuration-syntax"></a>De syntaxis van de configuratie

Een configuratiescript bestaat uit de volgende onderdelen:

- De **configuratie** blok. Dit is het buitenste scriptblok. U de gegevens definiëren met behulp van de **configuratie** sleutelwoord en een naam geven. In dit geval is de naam van de configuratie 'MyDscConfiguration'.
- Een of meer **knooppunt** blokken. Dit definieert de knooppunten (computers of virtuele machines) die u configureert. In de bovenstaande configuratie, er is een **knooppunt** blok die gericht is op een computer met de naam 'TEST-PC1'.
- Een of meer resource-blokken. Dit is waar de configuratie stelt u de eigenschappen voor de resources die deze configureert. In dit geval zijn er twee resource blokken, die elk de resource 'WindowsFeature' aanroepen.

Binnen een **configuratie** blok, kunt u alles wat u normaal gesproken in een PowerShell-functie kan doen. Bijvoorbeeld in het vorige voorbeeld kan als u niet wilt harde code de naam van de doelcomputer in de configuratie u een parameter toevoegen voor de knooppuntnaam van:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

In dit voorbeeld wordt u de naam van het knooppunt door door te geven als de **ComputerName** parameter door bij het compileren van de configuratie. De naam van de standaard 'localhost'.

## <a name="compiling-the-configuration"></a>De configuratie compileren

Voordat u een configuratie op te nemen kunt, die u moet deze worden gecompileerd tot een MOF-document.
U doen dit door het aanroepen van de configuratie, zoals u zou een PowerShell-functie aanroept.
De laatste regel van het voorbeeld met alleen de naam van de configuratie, roept de configuratie.

>**Opmerking:** voor het aanroepen van een configuratie met de functie moet in het globale bereik (net als bij een andere PowerShell-functie).
>U kunt aanbrengen in dit geval ofwel door 'dotsourcing' het script of configuratiescript uit te voeren de met behulp van F5 of klik op de **-Script uitvoeren** knop in de ISE.
>Het script voor punt-bron, voert u de opdracht `. .\myConfig.ps1` waar `myConfig.ps1` is de naam van het scriptbestand dat uw configuratie bevat.

Bij het aanroepen van de configuratie het:

- Alle variabelen wordt opgelost
- Maakt een map in de huidige map met dezelfde naam als de configuratie.
- Maakt een bestand met de naam _NodeName_MOF in de nieuwe map waar _NodeName_ is de naam van het doelknooppunt van de configuratie.
    Als er meer dan één knooppunten, wordt een MOF-bestand gemaakt voor elk knooppunt.

>**Opmerking**: het MOF-bestand bevat alle van de configuratiegegevens voor het doelknooppunt. Als gevolg hiervan is het belangrijk beveiligd blijft.
>Zie voor meer informatie [beveiligen van het MOF-bestand](secureMOF.md).

Compileren van de eerste configuratie boven resultaten in de volgende mapstructuur:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Als de configuratie een parameter, zoals in het tweede voorbeeld moet heeft die worden opgegeven tijdens de compilatie. Ga als volgt die zou als volgt uitzien:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-dependson"></a>Met behulp van DependsOn

Is een nuttig DSC-sleutelwoord **DependsOn**. Normaal (maar niet noodzakelijkerwijs altijd), DSC van de resources in de volgorde waarin ze worden weergegeven in de configuratie van de toepassing.
Echter, **DependsOn** geeft aan welk resources afhankelijk zijn van andere bronnen en de LCM zorgt ervoor dat ze worden toegepast in de juiste volgorde, ongeacht de volgorde in welke resource exemplaren worden gedefinieerd.
Bijvoorbeeld: een configuratie opgeven die een exemplaar van de **gebruiker** bron is afhankelijk van de aanwezigheid van een **groep** exemplaar:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a>Met behulp van nieuwe resources in uw configuratie

Als u de eerdere voorbeelden hebt uitgevoerd, u mogelijk opgevallen dat zijn u gewaarschuwd dat u een resource zijn gebruiken zonder expliciet importeren.
Vandaag de dag DSC wordt geleverd met 12 resources als onderdeel van de module PSDesiredStateConfiguration.
Andere bronnen in externe modules moeten worden geplaatst in `$env:PSModulePath` om te kunnen worden herkend door de LCM.
Een nieuwe cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), kunnen worden gebruikt om te bepalen welke bronnen worden geïnstalleerd op het systeem en zijn beschikbaar voor gebruik door de LCM.
Zodra deze modules zijn geplaatst `$env:PSModulePath` en correct worden herkend door [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ze nog moeten worden geladen in uw configuratie.
**Importeren DscResource** is een dynamische sleutelwoord dat alleen kan worden herkend binnen een **configuratie** blok (dat wil zeggen het is niet een cmdlet).
**Importeren DscResource** ondersteunt twee parameters:
- **Modulenaam** is de aanbevolen manier van het gebruik van **importeren DscResource**. De naam van de module met de resources die worden geïmporteerd (evenals een string-matrix van modulenamen) worden geaccepteerd.
- **Naam** is de naam van de resource te importeren. Dit is niet de beschrijvende naam die wordt geretourneerd als 'Name' door [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), maar de naam van de klasse die wordt gebruikt wanneer definiëren van de resource-schema (geretourneerd als **ResourceType** door [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).

## <a name="see-also"></a>Zie ook
* [Windows PowerShell Desired State Configuration-overzicht](overview.md)
* [DSC-Resources](resources.md)
* [De lokale Configuration Manager configureren](metaConfig.md)
