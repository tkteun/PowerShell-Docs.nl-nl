---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-logboek resource
description: DSC-logboek resource
ms.openlocfilehash: 281d1f8aeeb4d075f073419ac02a0f81888ed2b5
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142460"
---
# <a name="dsc-log-resource"></a>DSC-logboek resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **logboek** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>Eigenschappen

| Eigenschap |                                                   Beschrijving                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| Bericht  | Hiermee wordt het bericht aangegeven dat u wilt schrijven naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic. |

## <a name="common-properties"></a>Algemene eigenschappen

|       Eigenschap       |                                                                                                                                                          Beschrijving                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DependsOn            | Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
| PsDscRunAsCredential | Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.                                                                                                                                                                                                                                                                        |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een bericht opneemt in het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.

> [!NOTE]
> Als u [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) uitvoert met deze bron geconfigureerd, wordt er altijd **$False** geretourneerd.

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
