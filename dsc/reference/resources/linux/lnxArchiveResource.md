---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxArchive-resource
ms.openlocfilehash: 77b52ad68344ba791501baeb585a5001cc97a126
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324851"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC voor Linux nxArchive-resource

De **nxArchive** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitpakken van archief bestanden (. tar,. zip) op een specifiek pad op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Bronpad |Hiermee geeft u het bronpad van het archief bestand. Dit moet een. tar-,. zip-of. tar. gz-bestand zijn. |
|DestinationPath |Hiermee geeft u de locatie op waar de archief inhoud moet worden uitgepakt. |
|Controlesom |Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of het bron archief is bijgewerkt. Waarden zijn: **ctime**, **mtime**of **MD5**. De standaard waarde is **MD5**. |
|Force |Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout. Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd. De standaardwaarde is `$false`. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt bepaald of wordt gecontroleerd of de inhoud van het archief bestaat op de **bestemming**. Stel deze eigenschap in op **aanwezig** om te controleren of de inhoud bestaat. Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan. De standaard waarde is **aanwezig**. |

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u de **nxArchive** -resource kunt gebruiken om ervoor te zorgen dat `website.tar` de inhoud van een archief bestand met de naam exists wordt geëxtraheerd op een bepaalde bestemming.

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```