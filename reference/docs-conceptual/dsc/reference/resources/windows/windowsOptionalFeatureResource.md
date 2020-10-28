---
ms.date: 08/28/2020
ms.topic: reference
title: DSC WindowsOptionalFeature-resource
description: DSC WindowsOptionalFeature-resource
ms.openlocfilehash: edaa69f956033e6036b88f63b6b40832ad3a32f9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656606"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature-resource

> Van toepassing op: Windows Power shell 5. x

De **WindowsOptionalFeature** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt.

> [!NOTE]
> **WindowsOptionalFeature** werkt alleen op Windows-client computers zoals Windows 10.

## <a name="syntax"></a>Syntax

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee wordt de naam aangegeven van de functie die u wilt inschakelen, is ingeschakeld of uitgeschakeld. |
|NoWindowsUpdateCheck |Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om een functie in te scha kelen. Als `$true` kan DISM geen contact opnemen met Wu. |
|RemoveFilesOnDisable |Stel deze `$true` optie in om alle bestanden te verwijderen die zijn gekoppeld aan de functie als u **zeker weet dat** deze is ingesteld op **afwezig** . |
|Logniveau |Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken. De geaccepteerde waarden zijn: **ErrorsOnly** , **ErrorsAndWarning** en **ErrorsAndWarningAndInformation** . |
|Logboekpad |Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of de functie is ingeschakeld. Stel deze eigenschap in op _inschakelen_ om ervoor te zorgen dat de functie is ingeschakeld. Om ervoor te zorgen dat de functie is uitgeschakeld, stelt u de eigenschap in op _uitschakelen_ . De standaard waarde is _ingeschakeld_ . |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.
