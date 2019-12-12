---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC serviceset-resource
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941297"
---
# <a name="dsc-serviceset-resource"></a>DSC serviceset-resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **serviceset** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op het doel knooppunt. Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [Service Resource](serviceResource.md) aanroept voor elke service die in de eigenschap **name** is opgegeven.

Gebruik deze resource als u een aantal services wilt configureren met dezelfde status.

## <a name="syntax"></a>Syntaxis

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee worden de service namen aangegeven. Houd er rekening mee dat dit verschilt van de weergave namen. U kunt een lijst met de services en de huidige status ophalen met de cmdlet `Get-Service`. |
|Opstart type |Hiermee wordt het opstart type voor de Services aangegeven. De waarden die zijn toegestaan voor deze eigenschap zijn: **automatisch**, **uitgeschakeld**en **hand matig**. |
|BuiltInAccount |Hiermee wordt het aanmeldings account aangegeven dat moet worden gebruikt voor de services. De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**en **Network Service**. |
|Status |Hiermee wordt de status aangegeven die u voor de services wilt garanderen: **gestopt** of **actief**. |
|Referentie |Hiermee geeft u de referenties op voor het account dat wordt uitgevoerd door de service bron. Deze eigenschap en de eigenschap **BuiltinAccount** kunnen niet tegelijk worden gebruikt. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|Zo |Hiermee wordt aangegeven of de services bestaan op het systeem. Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de services niet bestaan. Als u deze optie instelt op **presen teren** , zorgt u ervoor dat doel services bestaan. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

Met de volgende configuratie worden de services Windows Audio en Extern bureaublad-services gestart.

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```