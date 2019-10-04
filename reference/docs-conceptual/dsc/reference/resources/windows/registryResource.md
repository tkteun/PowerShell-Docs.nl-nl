---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-register resource
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941332"
---
# <a name="dsc-registry-resource"></a>DSC-register resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **register** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van register sleutels en-waarden op een doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Sleutel |Hiermee geeft u het pad van de register sleutel op waarvan u een specifieke status wilt waarborgen. Dit pad moet de Hive bevatten. |
|ValueName |Hiermee wordt de naam van de register waarde aangegeven. Als u een register sleutel wilt toevoegen of verwijderen, geeft u deze eigenschap op als een lege teken reeks zonder **Value type** of **ValueData**op te geven. Als u de standaard waarde van een register sleutel wilt wijzigen of verwijderen, geeft u deze eigenschap op als een lege teken reeks terwijl u ook **Value type** of **ValueData**opgeeft. |
|Force |Als de opgegeven register sleutel aanwezig is, wordt deze door **geforceerd** overschreven met de nieuwe waarde. Als u een register sleutel met subsleutels verwijdert, moet dit `$true`zijn. |
|Bovenaanzicht |Hiermee wordt aangegeven of gegevens in hexadecimale indeling worden weer gegeven. Indien opgegeven, worden de DWORD/QWORD-waardegegevens weer gegeven in hexadecimale notatie. Niet geldig voor andere typen. De standaardwaarde is `$false`. |
|ValueData |De gegevens voor de register waarde. |
|ValueType |Hiermee wordt het type van de waarde aangegeven. De ondersteunde typen zijn: **Teken reeks** (REG_SZ), **binair** (REG-BINARY), **DWORD** (32-bits REG_DWORD), **Qword** (64-bits REG_QWORD), **multistring** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt aangegeven of de sleutel en de waarde bestaan. Stel deze eigenschap in op **presen teren**om ervoor te zorgen dat ze wel aanwezig zijn. Om ervoor te zorgen dat ze niet bestaan, stelt u de eigenschap in op **afwezig**. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In dit voor beeld wordt ervoor gezorgd dat een sleutel met de naam ' ExampleKey ' aanwezig is in de **lokale\_\_machine** -component HKEY.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> Als u een register instelling in `HKEY_CURRENT_USER` het onderdeel wilt wijzigen, moet de configuratie worden uitgevoerd met gebruikers referenties in plaats van als het systeem. U kunt de eigenschap **PsDscRunAsCredential** gebruiken om gebruikers referenties op te geven voor de configuratie. Zie [DSC uitvoeren met gebruikers referenties](../../../configurations/runAsUser.md)voor een voor beeld.