---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxEnvironment-resource
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941437"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC voor Linux nxEnvironment-resource

De **nxEnvironment** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

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

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Name |Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen. |
|Value |De waarde die moet worden toegewezen aan de omgevings variabele. |
|Path |Hiermee definieert u de omgevings variabele die wordt geconfigureerd. Stel deze eigenschap in `$true` op **als de variabele een padvariabele** is. anders stelt u deze in `$false`op. De standaardwaarde is `$false`. Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt bepaald of er wordt gecontroleerd of de variabele bestaat. Stel deze eigenschap in op **presen teren** om ervoor te zorgen dat de variabele bestaat. Stel deze in op **afwezig** om te controleren of de variabele niet bestaat. De standaard waarde is **aanwezig**. |

## <a name="additional-information"></a>Als u meer informatie

- Als het **pad** ontbreekt of is ingesteld `$false`op, worden omgevings variabelen `/etc/environment`beheerd in.
  Uw Program ma's of scripts kunnen de configuratie van het `/etc/environment` bestand vereisen om toegang te krijgen tot de variabelen van de beheerde omgeving.
- Als **Path** is ingesteld op `$true`, wordt de omgevings variabele in het bestand `/etc/profile.d/DSCenvironment.sh`beheerd. Dit bestand wordt gemaakt als het niet bestaat. Als **het** is ingesteld op **afwezig** en **pad** is ingesteld op `$true`, wordt een bestaande omgevings variabele alleen uit `/etc/profile.d/DSCenvironment.sh` andere bestanden verwijderd.

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