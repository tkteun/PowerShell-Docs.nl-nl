---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Registerresource
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048303"
---
# <a name="dsc-registry-resource"></a>DSC-Registerresource

_Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_

De **register** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van registersleutels en -waarden op een doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Eigenschappen

| Eigenschap | Beschrijving |
| --- | --- |
| Toets| Geeft het pad van de registersleutel die u wilt om te controleren of een specifieke status. Dit pad moet de component bevatten.|
| Waardenaam| Geeft de naam van de registerwaarde. Als u wilt toevoegen of verwijderen van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks zonder ValueType of Waardegegevens op te geven. Als u wilt wijzigen of verwijderen van de standaardwaarde van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks tijdens het instellen van ook ValueType of Waardegegevens.|
| Zorg ervoor dat| Geeft aan of de sleutel en waarde bestaan. Om ervoor te zorgen dat ze doen, stelt u deze eigenschap in 'Aanwezig'. Om ervoor te zorgen dat deze niet bestaan, de eigenschap instellen op 'Ontbreekt'. De standaardwaarde is 'Aanwezig'.|
| Force| Als de opgegeven registersleutel aanwezig is, **Force** overschreven door de nieuwe waarde. Als een registersleutel met subsleutels verwijdert, moet dit **$true** |
| Hexadecimaal| Hiermee wordt aangegeven als gegevens zullen worden uitgedrukt in hexadecimale notatie. Als u opgeeft, worden de gegevens van de DWORD-/ QWORD-waarde wordt weergegeven in hexadecimale notatie. Niet geldig voor andere typen. De standaardwaarde is **$false**.|
| DependsOn| Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Waardegegevens| De gegevens voor de waarde van het register.|
| ValueType| Geeft het type van de waarde. De ondersteunde typen zijn: Tekenreeks (REG_SZ), binair (REG-BINARY), DWORD-32-bits (REG_DWORD), Qword 64-bits (REG_QWORD), met meerdere tekenreeksen (REG_MULTI_SZ), uitbreidbare tekenreeks (REG_EXPAND_SZ) |

## <a name="example"></a>Voorbeeld

In dit voorbeeld zorgt ervoor dat een sleutel met de naam "ExampleKey" aanwezig zijn in de **HKEY\_lokale\_MACHINE** hive.

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
> Wijzigen van een instelling in het register in de `HKEY\CURRENT\USER` hive vereist dat de configuratie wordt uitgevoerd met de referenties van gebruiker, in plaats van als het systeem. U kunt de **PsDscRunAsCredential** eigenschap om op te geven voor de configuratie van de gebruikersreferenties. Zie voor een voorbeeld [DSC uitvoeren met gebruikersreferenties](../../../configurations/runAsUser.md).
