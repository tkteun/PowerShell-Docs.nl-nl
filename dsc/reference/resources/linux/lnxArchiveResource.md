---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxArchive-Resource
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048297"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC voor Linux nxArchive-Resource

De **nxArchive** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het uitpakken van bestanden te archiveren (.tar, .zip) op een specifiek pad op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
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

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| Bronpad| Hiermee geeft u het bronpad van het bestand. Dit moet een .tar .zip, of..GZ-bestand. |
| DestinationPath| Hiermee geeft u de locatie waar u om te controleren of de dat inhoud van het archief worden geëxtraheerd.|
| Controlesom| Definieert het type te gebruiken bij het bepalen of de bron-archief is bijgewerkt. Waarden zijn: 'ctime","mtime"of 'md5'. De standaardwaarde is 'md5'.|
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt. Met behulp van de **Force** eigenschap heeft voorrang op dergelijke fouten. De standaardwaarde is **$false**.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Zorg ervoor dat| Hiermee bepaalt u of om te controleren of de inhoud van het archief bestaat op de **bestemming**. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de inhoud bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat ze bestaan niet. De standaardwaarde is 'Aanwezig'.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de **nxArchive** resource om ervoor te zorgen dat de inhoud van een archiefbestand genoemd `website.tar` bestaan en op een bepaalde bestemming worden geëxtraheerd.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```