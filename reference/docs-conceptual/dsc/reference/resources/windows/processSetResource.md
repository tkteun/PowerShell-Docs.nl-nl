---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-Processet-resource
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941367"
---
# <a name="dsc-processset-resource"></a>DSC-Processet-resource

> Van toepassing op: Windows Power shell 5. x

De **processet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Pad |Het pad naar het uitvoer bare proces bestand. Als dit de namen zijn van de uitvoer bare bestanden (niet volledig gekwalificeerde paden), zal de DSC-resource de omgeving `$env:Path` variabele doorzoeken om de bestanden te vinden. Als de waarden van deze eigenschap volledig gekwalificeerde paden zijn, gebruikt DSC de `$env:Path` omgevings variabele niet om de bestanden te vinden en wordt er een fout gegenereerd als een van de paden niet bestaat. Relatieve paden zijn niet toegestaan. |
|Referentie |Geeft de referenties voor het starten van het proces aan. |
|StandardErrorPath |Het pad naar de standaard fout voor het schrijven van processen. Eventuele bestaande bestanden worden overschreven. |
|StandardInputPath |De stroom van waaruit het proces standaard invoer ontvangt. |
|StandardOutputPath |Het pad van het bestand waarnaar de standaard uitvoer van de processen wordt geschreven. Eventuele bestaande bestanden worden overschreven. |
|WorkingDirectory |De locatie die wordt gebruikt als de huidige werkmap voor de processen. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|Zo |Hiermee geeft u op of de processen bestaan. Stel deze eigenschap in op **aanwezig** om te zorgen dat het proces bestaat. Als dat niet het geval is, stelt u deze in op **afwezig**. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.