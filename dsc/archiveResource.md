---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Archiveren van de DSC-Resource
ms.openlocfilehash: 1accd48f3862ee09b88d2792f9b7e5a7324bcf17
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-archive-resource"></a>Archiveren van de DSC-Resource

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

|  Eigenschap  |  Beschrijving   |
|---|---|
| Bestemming| Hiermee geeft u de locatie waar u Zorg ervoor dat de inhoud van het archief worden opgehaald.|
| Pad| Hiermee geeft u het bronpad van het bestand.|
| __Controlesom__| Definieert het type moet worden gebruikt bij het bepalen of twee bestanden hetzelfde zijn. Als __controlesom__ niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor vergelijking. Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate none (standaardwaarde). Als u opgeeft __controlesom__ zonder __valideren__, mislukt de configuratie.|
| Zorg ervoor dat| Hiermee bepaalt u of Controleer of de inhoud van het archief bestaat op de __bestemming__. Deze eigenschap instellen op __aanwezig__ om te controleren of de inhoud bestaat. Stel deze in op __afwezig__ om te controleren of ze bestaan niet. De standaardwaarde is __aanwezig__.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van het scriptblok voor resource configuratie die u wilt uitvoeren eerst ResourceName en het type is __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| valideren| De eigenschap controlesom gebruikt om te bepalen of het archief dat overeenkomt met de handtekening. Als u controlesom zonder valideren opgeeft, mislukt de configuratie. Als u valideren zonder controlesom opgeeft, wordt standaard een controlesom SHA-256 gebruikt.|
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een map die is niet leeg) leidt tot een fout opgetreden. Met de eigenschap Force, overschrijft dergelijke fouten. De standaardwaarde is ONWAAR.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld laat zien hoe de archief-bron gebruiken om ervoor te zorgen dat de inhoud van een archiefbestand aangeroepen Test.zip bestaan en op een bepaalde bestemming worden opgehaald.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```