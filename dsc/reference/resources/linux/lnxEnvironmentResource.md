---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxEnvironment-Resource
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048349"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC voor Linux nxEnvironment-Resource

De **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van omgevingsvariabelen op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| Naam| Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.|
| Waarde| De waarde om toe te wijzen aan de omgevingsvariabele.|
| Zorg ervoor dat| Hiermee bepaalt u of om te controleren of de variabele bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de variabele bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat de variabele niet bestaat. De standaardwaarde is 'Aanwezig'.|
| Pad| Hiermee definieert u de omgevingsvariabele die wordt geconfigureerd. Deze eigenschap instellen op **$true** als de variabele de **pad** variabele, anders wordt deze ingesteld op **$false**. De standaardwaarde is **$false**. Als de variabele die wordt geconfigureerd is de **pad** variabele, de waarde wordt opgegeven via de **waarde** eigenschap toegevoegd aan de bestaande waarde.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Als u meer informatie

* Als **pad** ontbreekt of is ingesteld op **$false**, omgevingsvariabelen worden beheerd in `/etc/environment`. Uw programma's of scripts mogelijk configuratie vereist voor bron de `/etc/environment` bestand voor toegang tot de beheerde omgevingsvariabelen.
* Als **pad** is ingesteld op **$true**, de omgevingsvariabele wordt beheerd in het bestand `/etc/profile.d/DSCenvironment.sh`. Als deze niet bestaat, wordt dit bestand worden aangemaakt. Als **Zorg ervoor dat** is ingesteld op 'Ontbreekt' en **pad** is ingesteld op **$true**, een bestaande omgevingsvariabele wordt alleen verwijderd uit `/etc/profile.d/DSCenvironment.sh` en niet vanuit andere bestanden.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de **nxEnvironment** resource om ervoor te zorgen dat **TestEnvironmentVariable** aanwezig is en de waarde 'Test-waarde'. Als **TestEnvironmentVariable** is niet aanwezig is, wordt deze gemaakt.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```