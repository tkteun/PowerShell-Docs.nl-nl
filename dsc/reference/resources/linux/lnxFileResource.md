---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxFile-Resource
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078024"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC voor Linux nxFile-Resource

De **nxFile** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Description |
|---|---|
| DestinationPath| Hiermee geeft u de locatie waar u om te controleren of de status van een bestand of map.|
| SourcePath| Hiermee geeft u het pad van waaruit de resource van het bestand of map kopiëren. Dit pad is mogelijk een lokaal pad of een `http/https/ftp` URL. Externe `http/https/ftp` URL's worden alleen ondersteund wanneer de waarde van de **Type** eigenschap bestand is.|
| Zorg ervoor dat| Hiermee bepaalt u of om te controleren of het bestand bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het bestand bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat het bestand bestaat niet. De standaardwaarde is 'Aanwezig'.|
| Type| Hiermee geeft u op of de resource wordt geconfigureerd een map of een bestand is. Deze eigenschap instellen op 'directory' om aan te geven dat de resource een map is. Stelt u deze naar het 'bestand' om aan te geven dat de resource een bestand is. De standaardwaarde is 'file'|
| Inhoud| Hiermee geeft u de inhoud van een bestand, zoals een bepaalde tekenreeks.|
| Controlesom| Definieert het type te gebruiken bij het bepalen of twee bestanden hetzelfde zijn. Als **controlesom** niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor de vergelijking. Waarden zijn: 'ctime","mtime"of 'md5'.|
| Recurse| Hiermee wordt aangegeven als submappen opgenomen worden. Deze eigenschap instellen op **$true** om aan te geven dat u wilt dat de submappen moeten worden opgenomen. De standaardwaarde is **$false**. **Opmerking:** Deze eigenschap is alleen geldig wanneer de **Type** eigenschap is ingesteld op de directory.|
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt. Met behulp van de **Force** eigenschap heeft voorrang op dergelijke fouten. De standaardwaarde is **$false**.|
| Koppelingen| Hiermee geeft u het gewenste gedrag voor symbolische koppelingen. Deze eigenschap instellen op 'volgen' symbolische koppelingen volgen en reageren op de doel-koppelingen (bijvoorbeeld. Kopieer het bestand in plaats van de koppeling). Deze eigenschap instellen op 'beheren' om te reageren op de koppeling (bijvoorbeeld. Kopieer de koppeling zelf). Deze eigenschap instellen op 'negeren' symbolische koppelingen worden genegeerd.|
| Groep| De naam van de **groep** eigenaar van het bestand of map.|
| Modus| Hiermee geeft u de gewenste machtigingen voor de resource in de octale of symbolische-notatie. (bijvoorbeeld 777 of rwxrwxrwx). Als u de symbolische notatie, bieden het eerste teken waarmee wordt aangegeven van de map of het bestand.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Als u meer informatie


Linux- en Windows gebruik van verschillende regeleindetekens in tekstbestanden standaard en dit kan leiden tot onverwachte resultaten bij het configureren van bepaalde bestanden op een Linux-computer met __nxFile__. Er zijn meerdere manieren voor het beheren van de inhoud van een Linux-bestand zonder problemen veroorzaakt door onverwachte regeleindetekens:

Stap 1: Kopieer het bestand vanaf een externe bron (http, https of ftp): Maak een bestand op Linux met de gewenste inhoud, en de knooppunten die u configureert Faseren op een webserver of FTP-server toegankelijk is. Definieer de __bronpad__ eigenschap in de __nxFile__ resource met de web- of FTP-URL naar het bestand.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


Stap 2: Lezen van de inhoud van het bestand in het PowerShell-script met [Get-inhoud](https://technet.microsoft.com/library/hh849787.aspx) nadat u de __$OFS__ eigenschap om de Linux-regeleinde teken te gebruiken.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


Stap 3: Een PowerShell-functie gebruiken om te vervangen door Windows met Linux regeleinde tekens regeleinden.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat de map `/opt/mydir` bestaat, en dat een bestand met de opgegeven inhoud deze map bestaat.

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```