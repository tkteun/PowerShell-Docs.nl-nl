---
ms.date: 09/20/2019
ms.topic: reference
title: DSC-Service Resource
description: DSC-Service Resource
ms.openlocfilehash: 68055983a8d2880b4d556fe990310f439afffe41
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664197"
---
# <a name="dsc-service-resource"></a>DSC-Service Resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **service** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt.

## <a name="syntax"></a>Syntax

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee wordt de service naam aangegeven. Houd er rekening mee dat dit verschilt van de weergave naam. U kunt een lijst met de services en de huidige status van de `Get-Service` cmdlet ophalen. |
|BuiltInAccount |Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService** , **LocalSystem** en **Network Service** . |
|Referentie |Hiermee geeft u de referenties op voor het account waaronder de service wordt uitgevoerd. Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt. |
|StartupTimeout | De tijd die moet worden gewacht voordat de service wordt uitgevoerd in milliseconden.|
|Opstart type |Hiermee geeft u het opstart type voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **automatisch** , **uitgeschakeld** en **hand matig** . |
|Staat |Hiermee wordt de status aangegeven die u voor de service wilt controleren. De waarden zijn: **actief** of **gestopt** . |
|TerminateTimeout |De tijd die moet worden gewacht voordat de service wordt gestopt in milliseconden.|
|Afhankelijkheden | Een matrix met de namen van de afhankelijkheden die de service moet hebben. |
|Beschrijving |Hiermee wordt de beschrijving van de doel service aangegeven. |
|DesktopInteract | Hiermee wordt aangegeven of de service kan communiceren met een venster op het bureau blad. Moet onwaar zijn voor services die niet als LocalSystem worden uitgevoerd.|
|DisplayName |Hiermee wordt de weergave naam van de doel service aangegeven. |
|Pad |Hiermee wordt het pad naar het binaire bestand voor een nieuwe service aangegeven. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee geeft u op of de doel service op het systeem bestaat. Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de doel service niet bestaat. **Als u** deze instelling inschakelt, zorgt u ervoor dat de doel service bestaat. De standaard waarde is **aanwezig** . |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
