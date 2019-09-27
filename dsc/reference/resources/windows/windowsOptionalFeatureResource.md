---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsOptionalFeature-resource
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323900"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature-resource

> Van toepassing op: Windows Power shell 5. x

De **WindowsOptionalFeature** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Name |Hiermee wordt de naam aangegeven van de functie die u wilt inschakelen, is ingeschakeld of uitgeschakeld. |
|Source |Niet geïmplementeerd. |
|NoWindowsUpdateCheck |Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om een functie in te scha kelen. Als `$true`kan DISM geen contact opnemen met Wu. |
|RemoveFilesOnDisable |Stel deze optie in omallebestandenteverwijderendiezijngekoppeldaandefunctiealsuzekerweetdatdezeisingesteldop`$true` afwezig. |
|Logniveau |Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken. De geaccepteerde waarden zijn: **ErrorsOnly**, **ErrorsAndWarning**en **ErrorsAndWarningAndInformation**. |
|Logboekpad |Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt aangegeven of de functie is ingeschakeld. Stel deze eigenschap in op _inschakelen_om ervoor te zorgen dat de functie is ingeschakeld. Om ervoor te zorgen dat de functie is uitgeschakeld, stelt u de eigenschap in op _uitschakelen_. De standaard waarde is _ingeschakeld_. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.