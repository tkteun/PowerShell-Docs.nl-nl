---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxFile Resource
ms.openlocfilehash: f1eb98092049ae837d144ccf99a84fe5614144e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189853"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC voor Linux nxFile Resource

De **nxFile** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme op voor het beheren van bestanden en mappen op een Linux-knooppunt.

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

|  Eigenschap |  Beschrijving |
|---|---|
| DestinationPath| Hiermee geeft u de locatie op waar u om te controleren of de status voor een bestand of map.|
| Bronpad| Hiermee geeft u het pad van waaruit de bron van het bestand of map kopiëren. Dit pad is mogelijk een lokaal pad of een `http/https/ftp` URL. Externe `http/https/ftp` URL's worden alleen ondersteund wanneer de waarde van de **Type** eigenschap bestand is.|
| Zorg ervoor dat| Bepaalt of Controleer of het bestand bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het bestand bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat het bestand bestaat niet. De standaardwaarde is 'Aanwezig'.|
| Type| Hiermee geeft u op of de resource die wordt geconfigureerd een map of een bestand is. Deze eigenschap instellen op 'map' om aan te geven dat de resource een map is. Stel deze in op 'file' om aan te geven dat de resource een bestand is. De standaardwaarde is "bestand"|
| Inhoud| Hiermee geeft u de inhoud van een bestand, zoals een bepaalde tekenreeks.|
| Controlesom| Definieert het type moet worden gebruikt bij het bepalen of twee bestanden hetzelfde zijn. Als **controlesom** niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor vergelijking. Waarden zijn: 'ctime', 'mtime' of 'md5'.|
| Recurse| Hiermee wordt aangegeven als submappen opgenomen worden. Deze eigenschap instellen op **$true** om aan te geven dat u wilt dat de submappen worden opgenomen. De standaardwaarde is **$false**. **Opmerking:** deze eigenschap is alleen geldig wanneer de **Type** eigenschap is ingesteld op de directory.|
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een map die is niet leeg) leidt tot een fout opgetreden. Met behulp van de **Force** eigenschap heeft een dergelijke fouten. De standaardwaarde is **$false**.|
| Koppelingen| Hiermee geeft u het gewenste gedrag voor symbolische koppelingen. Deze eigenschap instellen op 'volgen' symbolische koppelingen volgen en reageren op de doel-koppelingen (bijvoorbeeld) Kopieer het bestand in plaats van de koppeling). Deze eigenschap instellen op 'beheren' om te reageren op de koppeling (bijvoorbeeld) Kopieer de koppeling zelf). Deze eigenschap instellen op 'negeren' om door te negeren symbolische koppelingen.|
| Groep| De naam van de **groep** eigenaar van het bestand of map.|
| Modus| Hiermee geeft u de gewenste machtigingen voor de resource octaal of symbolische-notatie. (bijvoorbeeld 777 of rwxrwxrwx). Als symbolische notatie wordt gebruikt, bieden niet het eerste teken waarmee wordt aangegeven van de map of bestand.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Als u meer informatie


Linux- en Windows verschillende regeleindeteken in tekstbestanden standaard en dit kan leiden tot onverwachte resultaten bij het configureren van een aantal bestanden op een Linux-computer met __nxFile__. Er zijn meerdere manieren voor het beheren van de inhoud van een Linux-bestand zonder problemen veroorzaakt door een onverwachte regeleindeteken:

Stap 1: Het bestand kopiëren vanaf een externe bron (http, https of ftp): een bestand op Linux maken met de gewenste inhoud, en de knooppunten die u configureert Faseren op een webserver of FTP-server toegankelijk is. Definieer de __bronpad__ eigenschap in de __nxFile__ resource met de webserver of FTP-URL naar het bestand.

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


Stap 2: De inhoud van het bestand in het PowerShell-script met lezen [Get-inhoud](https://technet.microsoft.com/library/hh849787.aspx) nadat u de __$OFS__ eigenschap om de Linux-regeleinde-teken te gebruiken.


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


Stap 3: Een PowerShell-functie gebruiken Windows regeleinden vervangt door de regeleindetekens Linux.

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

Het volgende voorbeeld zorgt ervoor dat de map `/opt/mydir` bestaat, en of een bestand met de opgegeven inhoud deze map bestaat.

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