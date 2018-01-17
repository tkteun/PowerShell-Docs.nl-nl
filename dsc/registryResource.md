---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-Resource voor register
ms.openlocfilehash: 1e73e4275c0d9db5d8fac7641514ea8190f719ca
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-registry-resource"></a>DSC-Resource voor register

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **register** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van registersleutels en -waarden in een doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Toets| Geeft het pad van de registersleutel waarvoor u wilt om te controleren of een specifieke status. Dit pad moet de component bevatten.| 
| ValueName| Geeft de naam van de registerwaarde. Als u wilt toevoegen of verwijderen van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks zonder ValueType of Waardegegevens te geven. Als u wilt wijzigen of verwijderen van de standaardwaarde van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks ook specificeren ValueType of Waardegegevens.| 
| Zorg ervoor dat| Hiermee wordt aangegeven als de sleutel en waarde bestaan. Om ervoor te zorgen dat ze doen, stel deze eigenschap in op 'Aanwezig'. Om ervoor te zorgen dat ze niet bestaat, de eigenschap instellen op 'Afwezig'. De standaardwaarde is 'Aanwezig'.| 
| Force| Als de opgegeven registersleutel aanwezig is, __Force__ overschreven met de nieuwe waarde. Als een registersleutel met subsleutels verwijdert, moet dit __$true__| 
| Hex| Hiermee wordt aangegeven als gegevens zullen worden uitgedrukt in hexadecimale notatie. Als u opgeeft, wordt de waardegegevens DWORD/QWORD is opgenomen in hexadecimale notatie. Niet geldig voor andere typen. De standaardwaarde is __$false__.| 
| dependsOn| Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| De gegevens voor de registerwaarde.| 
| ValueType| Geeft het type van de waarde. De ondersteunde typen zijn: 
<ul><li>Tekenreeks (REG_SZ)</li>


<li>Binair (REG-BINARY)</li>


<li>DWORD 32-bits (REG_DWORD)</li>


<li>Qword 64-bits (REG_QWORD)</li>


<li>Met meerdere tekenreeksen (REG_MULTI_SZ)</li>


<li>Uit te breiden tekenreeks (REG_EXPAND_SZ)</li></ul>

## <a name="example"></a>Voorbeeld
In dit voorbeeld zorgt ervoor dat een sleutel met de naam 'ExampleKey' aanwezig is in de **HKEY\_lokale\_MACHINE** hive.
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

>**Opmerking:** aanbrengen in een registerinstelling in de **HKEY\_huidige\_gebruiker** hive vereist dat de configuratie wordt uitgevoerd met gebruikersgegevens, in plaats van als het systeem.
>U kunt de **PsDscRunAsCredential** eigenschap gebruikersreferenties voor de configuratie opgeven. Zie voor een voorbeeld [DSC uitgevoerd met gebruikersgegevens](runAsUser.md)



