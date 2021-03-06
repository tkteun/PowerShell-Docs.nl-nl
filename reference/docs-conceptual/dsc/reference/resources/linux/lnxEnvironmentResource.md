---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxEnvironment-resource
description: DSC voor Linux nxEnvironment-resource
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644670"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC voor Linux nxEnvironment-resource

De **nxEnvironment** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen op een Linux-knoop punt.

## <a name="syntax"></a>Syntax

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen. |
|Waarde |De waarde die moet worden toegewezen aan de omgevings variabele. |
|Pad |Hiermee definieert u de omgevings variabele die wordt geconfigureerd. Stel deze eigenschap in op `$true` als de variabele een **padvariabele** is. anders stelt u deze in op `$false` . De standaardwaarde is `$false`. Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt bepaald of er wordt gecontroleerd of de variabele bestaat. Stel deze eigenschap in op **presen teren** om ervoor te zorgen dat de variabele bestaat. Stel deze in op **afwezig** om te controleren of de variabele niet bestaat. De standaard waarde is **aanwezig** . |

## <a name="additional-information"></a>Aanvullende informatie

- Als het **pad** ontbreekt of is ingesteld op `$false` , worden omgevings variabelen beheerd in `/etc/environment` .
  Uw Program ma's of scripts kunnen de configuratie van het `/etc/environment` bestand vereisen om toegang te krijgen tot de variabelen van de beheerde omgeving.
- Als **Path** is ingesteld op `$true` , wordt de omgevings variabele in het bestand beheerd `/etc/profile.d/DSCenvironment.sh` . Dit bestand wordt gemaakt als het niet bestaat. Als het is ingesteld op **afwezig** en **pad** **is ingesteld** op `$true` , wordt een bestaande omgevings variabele alleen uit `/etc/profile.d/DSCenvironment.sh` andere bestanden verwijderd.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u de **nxEnvironment** -resource gebruikt om ervoor te zorgen dat **TestEnvironmentVariable** aanwezig is en de waarde test-value heeft. Als **TestEnvironmentVariable** niet aanwezig is, wordt deze gemaakt.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
