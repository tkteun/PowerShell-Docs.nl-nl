---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-omgeving Resource
ms.openlocfilehash: 9c166d719ba3f168c936278acd6fb5fb7658613e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-environment-resource"></a>DSC-omgeving Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De __omgeving__ in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van omgevingsvariabelen.

## <a name="syntax"></a>Syntaxis
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Naam| Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.| 
| Zorg ervoor dat| Hiermee wordt aangegeven of een variabele bestaat. Deze eigenschap instellen op __aanwezig__ te maken van de omgevingsvariabele als deze niet bestaat of om ervoor te zorgen dat de waarde overeenkomt met wat is opgegeven via de __waarde__ eigenschap als de variabele al bestaat. Stel deze in op __afwezig__ verwijderen van de variabele als deze bestaat.| 
| Pad| Hiermee definieert u de variabele die wordt geconfigureerd. Deze eigenschap instellen op __$true__ als de variabele de __pad__ variabele, anders wordt ingesteld op __$false__. De standaardwaarde is __$false__. Als de variabele die wordt geconfigureerd de __pad__ variabele, de waarde wordt opgegeven via de __waarde__ eigenschap worden toegevoegd aan de bestaande waarde.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 
| Value| De waarde om toe te wijzen aan de omgevingsvariabele.| 

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat __TestEnvironmentVariable__ aanwezig is en of hieraan de waarde __testwaarde__. Als dit niet aanwezig is, maakt deze.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

