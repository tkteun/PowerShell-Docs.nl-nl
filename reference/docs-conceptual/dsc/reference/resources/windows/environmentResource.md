---
ms.date: 07/16/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-omgevings resource
ms.openlocfilehash: d8519a66d457767dcbc0e08b01a69a9264997479
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464414"
---
# <a name="dsc-environment-resource"></a>DSC-omgevings resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **omgevings** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen.

## <a name="syntax"></a>Syntax

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen. |
|Pad |Hiermee definieert u de omgevings variabele die wordt geconfigureerd. Stel deze eigenschap in op `$true` als de variabele een **padvariabele** is. anders stelt u deze in op `$false` . De standaardwaarde is `$false`. Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd. |
|Doel| Hiermee wordt aangegeven waar de variabele moet worden opgehaald: de computer of het proces. Als beide worden aangegeven, wordt alleen de waarde van de computer geretourneerd. De standaard waarde is beide, omdat dit de standaard waarde is voor de rest van de resource. |
|Waarde |De waarde die moet worden toegewezen aan de omgevings variabele. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of een variabele bestaat. Stel deze eigenschap in op **presen teren** om de omgevings variabele te maken als deze niet bestaat of om ervoor te zorgen dat de waarde overeenkomt met wat is opgegeven via de eigenschap **Value** als de variabele al bestaat. Stel deze in op **afwezig** om de variabele te verwijderen als deze bestaat. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt ervoor gezorgd dat TestEnvironmentVariable aanwezig is en de waarde _TestValue_heeft. Als deze niet aanwezig is, wordt deze gemaakt.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
