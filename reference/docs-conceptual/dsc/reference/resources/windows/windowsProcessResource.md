---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsProcess-resource
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941164"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess-resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **WindowsProcess** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Argumenten |Hiermee wordt een reeks argumenten aangegeven die moeten worden door gegeven aan het proces. Als u meerdere argumenten wilt door geven, plaatst u deze allemaal in deze teken reeks. |
|Pad |Het pad naar het uitvoer bare proces bestand. Als de bestands naam van het uitvoer bare bestand (niet het volledig gekwalificeerde pad) is, zoekt de DSC-resource in de omgeving `$env:Path` variabele om het uitvoer bare bestand te vinden. Als de waarde van deze eigenschap een volledig gekwalificeerd pad is, gebruikt DSC de `$env:Path` variabele niet om het bestand te vinden en wordt er een fout gegenereerd als het pad niet bestaat. Relatieve paden zijn niet toegestaan. |
|Referentie |Geeft de referenties voor het starten van het proces aan. |
|StandardErrorPath |Hiermee wordt het mappad aangegeven voor het schrijven van de standaard fout. Eventuele bestaande bestanden worden overschreven. |
|StandardInputPath |Hiermee wordt de standaard invoer locatie aangegeven. |
|StandardOutputPath |Hiermee wordt de locatie aangegeven waarop de standaard uitvoer moet worden geschreven. Eventuele bestaande bestanden worden overschreven. |
|WorkingDirectory |Hiermee wordt de locatie aangegeven die wordt gebruikt als de huidige werkmap voor het proces. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|Zo |Hiermee wordt aangegeven of het proces bestaat. Stel deze eigenschap in op **aanwezig** om te zorgen dat het proces bestaat. Als dat niet het geval is, stelt u deze in op **afwezig**. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |