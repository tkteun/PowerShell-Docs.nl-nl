---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxEnvironment-resource
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
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

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen. |
|Value |De waarde die moet worden toegewezen aan de omgevings variabele. |
|Pad |Hiermee definieert u de omgevings variabele die wordt geconfigureerd. Stel deze eigenschap in op `$true` **als de variabele een padvariabele** is; Stel deze in andere gevallen in op `$false`. De standaardwaarde is `$false`. Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|Zo |Hiermee wordt bepaald of er wordt gecontroleerd of de variabele bestaat. Stel deze eigenschap in op **presen teren** om ervoor te zorgen dat de variabele bestaat. Stel deze in op **afwezig** om te controleren of de variabele niet bestaat. De standaard waarde is **aanwezig**. |

## <a name="additional-information"></a>Als u meer informatie

- Als het **pad** ontbreekt of is ingesteld op `$false`, worden omgevings variabelen in `/etc/environment`beheerd.
  Uw Program ma's of scripts kunnen configuratie nodig hebben om het `/etc/environment`-bestand te bron om toegang te krijgen tot de variabelen van de beheerde omgeving.
- Als **pad** is ingesteld op `$true`, wordt de omgevings variabele beheerd in het bestand `/etc/profile.d/DSCenvironment.sh`. Dit bestand wordt gemaakt als het niet bestaat. Als **dat** is ingesteld op **afwezig** en het **pad** is ingesteld op `$true`, wordt een bestaande omgevings variabele alleen verwijderd uit `/etc/profile.d/DSCenvironment.sh` en niet uit andere bestanden.

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