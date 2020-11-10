---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxFile-resource
description: DSC voor Linux nxFile-resource
ms.openlocfilehash: 14a8174a92f1bbde9b1f16cf814ef7c83309c737
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389025"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC voor Linux nxFile-resource

De **nxFile** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DestinationPath |Hiermee geeft u de locatie op waar u de status van een bestand of map wilt controleren. |
|Bronpad |Hiermee geeft u het pad op waaruit het bestand of de bron van de map moet worden gekopieerd. Dit pad mag een lokaal pad of een URL zijn `http/https/ftp` . Externe `http/https/ftp` url's worden alleen ondersteund wanneer de waarde van de eigenschap **type** **File** is. |
|Type |Hiermee geeft u op of de resource die wordt geconfigureerd een map of een bestand is. Stel deze eigenschap in op **Directory** om aan te geven dat de resource een directory is. Stel deze in op **bestand** om aan te geven dat de resource een bestand is. De standaard waarde is **File**. |
|Inhoud |Hiermee geeft u de inhoud van een bestand, zoals een bepaalde teken reeks. |
|Controlesom |Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn. Als er geen **controlesom** is opgegeven, wordt alleen de naam van het bestand of de map gebruikt voor de vergelijking. Waarden zijn: **ctime** , **mtime** of **MD5**. |
|Recurse |Hiermee wordt aangegeven of submappen zijn opgenomen. Stel deze eigenschap in op `$true` om aan te geven dat u submappen wilt opnemen. De standaardwaarde is `$false`. Deze eigenschap is alleen geldig wanneer de eigenschap **type** is ingesteld op **Directory**. |
|Force |Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout. Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd. De standaardwaarde is `$false`. |
|Koppelingen |Hiermee geeft u het gewenste gedrag voor symbolische koppelingen op. Stel deze eigenschap in op **volgen** van symbolische koppelingen volgen en reageren op het doel van de koppelingen. Kopieer bijvoorbeeld het bestand in plaats van de koppeling. Stel deze eigenschap in op **beheren** om op de koppeling te reageren. Kopieer bijvoorbeeld de koppeling zelf. Stel deze eigenschap in op **negeren** om symbolische koppelingen te negeren. |
|Groep |De naam van de **groep** die machtigingen voor het bestand of de map moet hebben. |
|Modus |Hiermee geeft u de gewenste machtigingen voor de resource op in een octale of symbolische notatie. Bijvoorbeeld **777** of **rwxrwxrwx**. Als u de symbolische notatie gebruikt, geeft u niet het eerste teken op dat map of bestand aangeeft. |
|Eigenaar |De naam van de groep die eigenaar is van het bestand of de map. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt bepaald of het bestand al bestaat. Stel deze eigenschap in op **presen teren** om te controleren of het bestand bestaat. Stel deze in op **afwezig** om te controleren of het bestand niet bestaat. De standaard waarde is **aanwezig**. |

## <a name="additional-information"></a>Aanvullende informatie

Linux en Windows gebruiken standaard andere regel-afbreek tekens in tekst bestanden. Dit kan leiden tot onverwachte resultaten bij het configureren van een aantal bestanden op een Linux-computer met **nxFile**. Er zijn meerdere manieren om de inhoud van een Linux-bestand te beheren, terwijl er problemen ontstaan die worden veroorzaakt door onverwachte regel einde tekens:

1. Het bestand kopiëren van een externe bron (http, https of FTP)

   Maak een bestand op Linux met de gewenste inhoud en werk het op een web-of FTP-server toegankelijk voor de knoop punten die u wilt configureren. Definieer de eigenschap **SourcePath** in de **nxFile** -resource met de web-of FTP-URL voor het bestand.

   ```powershell
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

1. Lees de bestands inhoud in het Power shell-script met [Get-content](xref:Microsoft.PowerShell.Management.Get-Content) nadat u de eigenschap **$OFS** hebt ingesteld op het gebruik van het Linux-regel scheidings teken.

   ```powershell
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

1. Gebruik een Power shell-functie om Windows-regel einden te vervangen door Linux-regel einde tekens.

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
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

In het volgende voor beeld wordt ervoor gezorgd dat de map `/opt/mydir` bestaat en dat er voor een bestand met de opgegeven inhoud deze map bestaat.

```powershell
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
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```
