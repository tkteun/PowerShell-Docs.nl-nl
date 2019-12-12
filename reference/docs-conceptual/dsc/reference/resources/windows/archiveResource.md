---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-archief resource
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942515"
---
# <a name="dsc-archive-resource"></a>DSC-archief resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De archief resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitpakken van archief bestanden (. zip) op een specifiek pad.

## <a name="syntax"></a>Syntaxis

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Bestemming |Hiermee geeft u de locatie op waar de archief inhoud moet worden uitgepakt. |
|Pad |Hiermee geeft u het bronpad van het archief bestand. |
|Controlesom |Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn. Als er geen **controlesom** is opgegeven, wordt alleen de naam van het bestand of de map gebruikt voor de vergelijking. Geldige waarden zijn: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. Als u **controlesom** zonder **validatie**opgeeft, mislukt de configuratie. |
|Force |Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout. Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd. De standaardwaarde is **False**. |
|Valideren| Maakt gebruik van de eigenschap **checksum** om te bepalen of het archief overeenkomt met de hand tekening. Als u **controlesom** zonder **validatie**opgeeft, mislukt de configuratie. Als u **Validate** zonder **controlesom**opgeeft, wordt standaard een _SHA-256-_ **controlesom** gebruikt. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|Zo |Hiermee wordt bepaald of wordt gecontroleerd of de inhoud van het archief bestaat op de **bestemming**. Stel deze eigenschap in op **aanwezig** om te controleren of de inhoud bestaat. Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u de archief resource gebruikt om ervoor te zorgen dat de inhoud van een archief bestand met de naam `Test.zip` bestaan en op een bepaalde bestemming wordt geëxtraheerd.

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```