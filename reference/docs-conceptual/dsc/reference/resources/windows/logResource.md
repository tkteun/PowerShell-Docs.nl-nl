---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-logboek resource
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942445"
---
# <a name="dsc-log-resource"></a>DSC-logboek resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **logboek** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.

## <a name="syntax"></a>Syntaxis

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> Standaard zijn alleen de operationele logboeken voor DSC ingeschakeld. Voordat het analytische logboek beschikbaar of zichtbaar is, moet het worden ingeschakeld. Zie voor meer informatie [waar zijn DSC-gebeurtenis logboeken?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Message |Hiermee wordt het bericht aangegeven dat u wilt schrijven naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een bericht opneemt in het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.

> [!NOTE]
> Als u [test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) uitvoert met deze bron geconfigureerd, wordt er altijd **$False**geretourneerd.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```