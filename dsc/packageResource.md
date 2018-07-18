---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Pakketresource
ms.openlocfilehash: 3046ba7d57776a996a0b917348a0e863db6cd0c8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093800"
---
# <a name="dsc-package-resource"></a>DSC-Pakketresource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **pakket** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te installeren of verwijderen van pakketten, zoals Windows Installer en setup.exe pakketten, op een doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Geeft de naam van het pakket waarvan u wilt om te controleren of een specifieke status.|
| Pad| Geeft het pad waar het pakket zich bevindt.|
| product-id| Geeft de product-ID die een unieke identificatie van het pakket.|
| Argumenten| Geeft een lijst van een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies hetzelfde als de opgegeven.|
| Referentie| Biedt toegang tot het pakket op een externe bron. Deze eigenschap wordt niet gebruikt om het pakket te installeren. Het pakket is altijd geïnstalleerd op het lokale systeem.|
| Zorg ervoor dat| Geeft aan of het pakket is geïnstalleerd. Deze eigenschap instellen op 'Afwezig"Controleer of dat het pakket niet is geïnstalleerd (of het pakket verwijderen als deze is geïnstalleerd). Instellen om "" (de standaardwaarde) om te controleren of dat het pakket is geïnstalleerd.|
| Logboekpad| Geeft het volledige pad waar u wilt dat de provider een logboekbestand om te installeren of verwijderen van het pakket op te slaan.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.|
| ReturnCode| Geeft aan dat de verwachte retourcode. Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde die hier beschikbaar zijn, dat de configuratie wordt een fout geretourneerd.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt het MSI-installatieprogramma dat zich bevindt in het opgegeven pad en de opgegeven product-id heeft.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```