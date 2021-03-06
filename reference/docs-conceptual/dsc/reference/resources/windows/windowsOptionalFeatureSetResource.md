---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsOptionalFeatureSet-resource
description: DSC WindowsOptionalFeatureSet-resource
ms.openlocfilehash: f72cc27bfc8847d2c87cfb289f3e2c729a21d1f4
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143038"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet-resource

> Van toepassing op: Windows Power shell 5. x

De **WindowsOptionalFeatureSet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt. Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [WindowsOptionalFeature-resource](windowsOptionalFeatureResource.md) aanroept voor elk onderdeel dat is opgegeven in de eigenschap **name** .

Gebruik deze resource als u een aantal optionele Windows-functies wilt configureren in dezelfde status.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee geeft u de naam op van de functies die u wilt inschakelen, worden in-of uitgeschakeld. |
|NoWindowsUpdateCheck |Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om functies in te scha kelen. Als `$true` kan DISM geen contact opnemen met Wu. |
|RemoveFilesOnDisable |Stel deze waarde in `$true` om alle bestanden te verwijderen die zijn **Ensure** gekoppeld aan de functies wanneer het is ingesteld op **afwezig** . |
|Logniveau |Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken. De geaccepteerde waarden zijn: **ErrorsOnly** , **ErrorsAndWarning** en **ErrorsAndWarningAndInformation** . |
|Logboekpad |Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of de functies zijn ingeschakeld. Stel deze eigenschap in op **inschakelen** om ervoor te zorgen dat de functies zijn ingeschakeld. Stel de eigenschap in op **uitschakelen** om ervoor te zorgen dat de functies zijn uitgeschakeld. De standaard waarde is **ingeschakeld** . |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.
