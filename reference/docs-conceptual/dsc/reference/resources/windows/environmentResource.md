---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-omgevings resource
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942480"
---
# <a name="dsc-environment-resource"></a>DSC-omgevings resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **omgevings** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen.

## <a name="syntax"></a>Syntaxis

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Name |Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen. |
|Path |Hiermee definieert u de omgevings variabele die wordt geconfigureerd. Stel deze eigenschap in `$true` op **als de variabele een padvariabele** is. anders stelt u deze in `$false`op. De standaardwaarde is `$false`. Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd. |
|Value |De waarde die moet worden toegewezen aan de omgevings variabele. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
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