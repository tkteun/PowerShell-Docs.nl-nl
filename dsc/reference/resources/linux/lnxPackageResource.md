---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxPackage-Resource
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077868"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC voor Linux nxPackage-Resource

De **nxPackage** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van pakketten op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Description |
|---|---|
| Naam| De naam van het pakket waarvan u wilt om te controleren of een specifieke status.|
| Zorg ervoor dat| Hiermee bepaalt u of om te controleren of het pakket bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het pakket bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat het pakket bestaat niet. De standaardwaarde is 'Aanwezig'.|
| PackageManager| Ondersteunde waarden zijn "yum", 'apt' en 'zypper'. Hiermee geeft u de package manager te gebruiken bij het installeren van pakketten. Als **FilePath** is opgegeven, wordt het opgegeven pad wordt gebruikt om het pakket te installeren. Anders wordt het pakket installeren vanuit een vooraf geconfigureerde opslagplaats Pakketbeheer gebruikt. Als geen van beide **PackageManager** noch **FilePath** zijn opgegeven, de standaard package manager voor het systeem wordt gebruikt.|
| FilePath| Het pad waar het pakket zich bevindt|
| PackageGroup| Als **$true**, wordt de **naam** wordt verwacht dat de naam van de groep van een pakket voor gebruik met een **PackageManager**. **PacakgeGroup** is niet geldig bij het opgeven van een **FilePath**.|
| Argumenten| Een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies hetzelfde als de opgegeven.|
| ReturnCode| De verwachte retourcode. Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde die hier beschikbaar zijn, dat de configuratie wordt een fout geretourneerd.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat het pakket met de naam 'httpd' is geïnstalleerd op een Linux-computer, met behulp van de 'Yum' package manager.

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```