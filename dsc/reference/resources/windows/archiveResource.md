---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Archiefresource
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077548"
---
# <a name="dsc-archive-resource"></a>DSC-Archiefresource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De archief-resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme uit te pakken archiefbestanden (.zip) op een specifiek pad.

## <a name="syntax"></a>Syntaxis
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Description   |
|---|---|
| Bestemming| Hiermee geeft u de locatie waar u om te controleren of de dat inhoud van het archief worden geëxtraheerd.|
| Pad| Hiermee geeft u het bronpad van het bestand.|
| __Checksum__| Definieert het type te gebruiken bij het bepalen of twee bestanden hetzelfde zijn. Als __controlesom__ niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor de vergelijking. Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate none (standaard). Als u opgeeft __controlesom__ zonder __valideren__, mislukt de configuratie van de.|
| Zorg ervoor dat| Hiermee bepaalt u of om te controleren of de inhoud van het archief bestaat op de __bestemming__. Deze eigenschap instellen op __aanwezig__ om te controleren of de inhoud bestaat. Stel deze in op __afwezig__ om te controleren of ze bestaan niet. De standaardwaarde is __aanwezig__.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resource-configuratie-scriptblok die u wilt uitvoeren eerst ResourceName en het bijbehorende type is is __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Valideren| De controlesom-eigenschap wordt gebruikt om te bepalen of het archief overeenkomt met de handtekening. Als u controlesom zonder te valideren opgeeft, mislukt de configuratie. Als u valideren zonder controlesom opgeeft, wordt er een SHA-256-controlesom standaard gebruikt.|
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt. Met behulp van de Force-eigenschap heeft voorrang op dergelijke fouten. De standaardwaarde is False.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u kunt de archiefresource gebruiken om ervoor te zorgen dat de inhoud van een bestand met de naam Test.zip bestaan en op een bepaalde bestemming worden geëxtraheerd.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```