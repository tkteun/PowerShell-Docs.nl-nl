---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Omgevingsresource
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077531"
---
# <a name="dsc-environment-resource"></a>DSC-Omgevingsresource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De __omgeving__ resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van omgevingsvariabelen.

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

|  Eigenschap  |  Description   |
|---|---|
| Naam| Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.|
| Zorg ervoor dat| Geeft aan dat er een variabele bestaat. Deze eigenschap instellen op __aanwezig__ te maken van de omgevingsvariabele als deze niet bestaat of om ervoor te zorgen dat de waarde ervan overeenkomt met wat wordt geboden via de __waarde__ eigenschap als de variabele al bestaat. Stel deze in op __afwezig__ verwijderen van de variabele als deze bestaat.|
| Pad| Hiermee definieert u de omgevingsvariabele die wordt geconfigureerd. Deze eigenschap instellen op __$true__ als de variabele de __pad__ variabele, anders wordt deze ingesteld op __$false__. De standaardwaarde is __$false__. Als de variabele die wordt geconfigureerd is de __pad__ variabele, de waarde wordt opgegeven via de __waarde__ eigenschap toegevoegd aan de bestaande waarde.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Waarde| De waarde om toe te wijzen aan de omgevingsvariabele.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat __TestEnvironmentVariable__ aanwezig is en heeft de waarde __testwaarde__. Als dit niet aanwezig is, maakt deze.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```