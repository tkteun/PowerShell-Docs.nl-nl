---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-register resource
ms.openlocfilehash: 3acd79fa81bc731f344d810371b961dc3af3a11d
ms.sourcegitcommit: 1ab59991c18e1b9692333d5e58ce649eaa75594f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84203644"
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

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Sleutel |Hiermee geeft u het pad van de register sleutel op waarvan u een specifieke status wilt waarborgen. Dit pad moet de Hive bevatten. |
|ValueName |Hiermee wordt de naam van de register waarde aangegeven. Als u een register sleutel wilt toevoegen of verwijderen, geeft u deze eigenschap op als een lege teken reeks zonder **Value type** of **ValueData**op te geven. Als u de standaard waarde van een register sleutel wilt wijzigen of verwijderen, geeft u deze eigenschap op als een lege teken reeks terwijl u ook **Value type** of **ValueData**opgeeft. |
|Force |Als de opgegeven register sleutel aanwezig is, wordt deze door **geforceerd** overschreven met de nieuwe waarde. Als u een register sleutel met subsleutels verwijdert, moet dit zijn `$true` . |
|Bovenaanzicht |Hiermee wordt aangegeven of gegevens in hexadecimale indeling worden weer gegeven. Indien opgegeven, worden de DWORD/QWORD-waardegegevens weer gegeven in hexadecimale notatie. Niet geldig voor andere typen. De standaardwaarde is `$false`. |
|ValueData |De gegevens voor de register waarde. |
|ValueType |Hiermee wordt het type van de waarde aangegeven. De ondersteunde typen zijn: **teken reeks** (REG_SZ), **binair** (REG-BINARY), **Dword** (32-bits REG_DWORD), **Qword** (64-bits REG_QWORD), **multistring** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of de sleutel en de waarde bestaan. Stel deze eigenschap in op **presen teren**om ervoor te zorgen dat ze wel aanwezig zijn. Om ervoor te zorgen dat ze niet bestaan, stelt u de eigenschap in op **afwezig**. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="examples"></a>Voorbeelden

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a>Voor beeld 1: Zorg ervoor dat de opgegeven waarde en gegevens onder de opgegeven register sleutel

In dit voor beeld wordt ervoor gezorgd dat de register waarde ' TestValue ' onder een sleutel met de naam ' ExampleKey1 ' aanwezig is in de `HKEY\_LOCAL\_MACHINE` component en de gegevens ' TestData ' bevat.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a>Voor beeld 2: controleren of de opgegeven register sleutel bestaat

In dit voor beeld wordt ervoor gezorgd dat een sleutel met de naam ' ExampleKey2 ' aanwezig is in de ** \_ lokale \_ machine** -component HKEY.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> Als u een register instelling in het `HKEY_CURRENT_USER` onderdeel wilt wijzigen, moet de configuratie worden uitgevoerd met gebruikers referenties in plaats van als het systeem. U kunt de eigenschap **PsDscRunAsCredential** gebruiken om gebruikers referenties op te geven voor de configuratie. Zie [DSC uitvoeren met gebruikers referenties](../../../configurations/runAsUser.md)voor een voor beeld.
