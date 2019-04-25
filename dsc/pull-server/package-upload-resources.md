---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Pakket- en Resources uploaden naar een Pull-Server
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079562"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Pakket- en Resources uploaden naar een Pull-Server

De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server. Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)

Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren. In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources. Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.

## <a name="package-resource-modules"></a>Pakket Resource Modules

Elke resource die beschikbaar zijn voor een client te downloaden moet worden opgeslagen in een 'ZIP'-bestand. In het volgende voorbeeld ziet u de vereiste stappen met behulp van de [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.

> [!NOTE]
> Als u clients met behulp van PowerShell 4.0 hebt, wordt u moet flaten de mapstructuur van de resource en de versie-mappen verwijderen. Zie voor meer informatie, [meerdere versies van de Resource](../configurations/import-dscresource.md#multiple-resource-versions).

U kunt de resource-map met behulp van een hulpprogramma, script of methode die u wilt comprimeren. In Windows, kunt u *met de rechtermuisknop op* op de directory 'xPSDesiredStateConfiguration' en selecteer "Verzenden naar" en "Gecomprimeerde map".

![Klik met de rechtermuisknop](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Naamgeving van de Resource-archief

Het archief van de Resource moet worden benoemd met de volgende indeling:

```
{ModuleName}_{Version}.zip
```

In het bovenstaande voorbeeld moet 'xPSDesiredStateConfiguration.zip' hernoemd 'xPSDesiredStateConfiguration_8.4.4.0.zip'.

### <a name="create-checksums"></a>Controlesommen maken

Zodra de Resource-module is gecomprimeerd en gewijzigd, moet u maken een **controlesom**.  De **controlesom** wordt gebruikt om door de LCM op de client om te bepalen of de resource is gewijzigd en moet opnieuw worden gedownload. U kunt maken een **controlesom** met de [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, zoals weergegeven in het onderstaande voorbeeld.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Er is geen uitvoer wordt weergegeven, maar u ziet nu een 'xPSDesiredStateConfiguration_8.4.4.0.zip.checksum'. U kunt ook uitvoeren `New-DSCCheckSum` op basis van een map met bestanden met behulp van de `-Path` parameter. Als een controlesom al bestaat, kunt u zorgen dat niet opnieuw worden gemaakt met de `-Force` parameter.

### <a name="where-to-store-resource-archives"></a>Waar archieven van de Resource wordt opgeslagen

#### <a name="on-a-dsc-http-pull-server"></a>Op een DSC-HTTP-Pull-Server

Bij het instellen van uw HTTP-Pull-Server, zoals uitgelegd in [instellen van een DSC HTTP-Pull-Server](pullServer.md), geeft u de mappen voor de **ModulePath** en **ConfigurationPath** sleutels. De **ConfigurationPath** sleutel geeft aan waar alle bestanden ".mof" moeten worden opgeslagen. De **ModulePath** geeft aan waar alle Modules DSC-Resource moet worden opgeslagen.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Op een SMB-Share

Als u hebt opgegeven een **ResourceRepositoryShare**wordt bij het instellen van uw Pull-Client, opslaan-archieven en controlesommen in de **bronpad** map van de **ResourceRepositoryShare** blokkeren.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Als u alleen opgegeven een **ConfigurationRepositoryShare**wordt bij het instellen van uw Pull-Client, opslaan-archieven en controlesommen in de **bronpad** map van de  **ConfigurationRepositoryShare** blokkeren.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>De resources worden bijgewerkt

U kunt afdwingen dat een knooppunt de daarbij behorende bronnen bijwerken door het wijzigen van het versienummer in de naam van het archief, of door het maken van een nieuwe controlesom. De Pull-Client voor nieuwere versies van de vereiste resources wordt gecontroleerd, evenals controlesommen, bijgewerkt wanneer de LCM wordt vernieuwd.

## <a name="see-also"></a>Zie ook

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)
