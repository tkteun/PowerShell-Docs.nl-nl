---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De Package DSC-Resource
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-package-resource"></a>De Package DSC-Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **pakket** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te installeren of verwijderen van pakketten, zoals Windows Installer en setup.exe pakketten in een doelknooppunt.

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
| Argumenten| Geeft een lijst van een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies zoals opgegeven.|
| referentie| Biedt toegang tot het pakket op een externe bron. Deze eigenschap wordt niet gebruikt om het pakket te installeren. Het pakket is altijd geïnstalleerd op het lokale systeem.|
| Zorg ervoor dat| Hiermee wordt aangegeven of het pakket is geïnstalleerd. Deze eigenschap instellen op 'Afwezig' controleert u dat het pakket niet is geïnstalleerd (of het pakket verwijderen als deze is geïnstalleerd). Instellen om "" (de standaardwaarde) om te controleren of dat het pakket is geïnstalleerd.|
| Logboekpad| Hiermee geeft u het volledige pad waar u de provider een logboekbestand om te installeren of verwijderen van het pakket opslaan.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.|
| ReturnCode| Geeft aan de verwachte retourcode. Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde opgegeven, dat wordt de configuratie een fout geretourneerd.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt het .msi-installatieprogramma dat zich bevindt op het opgegeven pad en de opgegeven product-ID.

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