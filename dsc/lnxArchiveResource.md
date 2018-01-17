---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxArchive Resource
ms.openlocfilehash: e91ef5bcf4bdf413844c23d1d3bd823a535b536f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC voor Linux nxArchive Resource

De **nxArchive** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het uitpakken van bestanden te archiveren (tar, .zip) op een specifiek pad op een Linux-knooppunt.

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
| SourcePath| Hiermee geeft u het bronpad van het bestand. Dit moet een tar .zip, of..GZ-bestand. | 
| DestinationPath| Hiermee geeft u de locatie waar u Zorg ervoor dat de inhoud van het archief worden opgehaald.| 
| Controlesom| Definieert het type moet worden gebruikt bij het bepalen of de bron-archief is bijgewerkt. Waarden zijn: 'ctime', 'mtime' of 'md5'. De standaardwaarde is 'md5'.| 
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een map die is niet leeg) leidt tot een fout opgetreden. Met behulp van de **Force** eigenschap heeft een dergelijke fouten. De standaardwaarde is **$false**.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 
| Zorg ervoor dat| Hiermee bepaalt u of Controleer of de inhoud van het archief bestaat op de **bestemming**. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de inhoud bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat ze bestaan niet. De standaardwaarde is 'Aanwezig'.| 

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de **nxArchive** resource om ervoor te zorgen dat de inhoud van een archiefbestand aangeroepen `website.tar` bestaan en op een bepaalde bestemming worden opgehaald.

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

