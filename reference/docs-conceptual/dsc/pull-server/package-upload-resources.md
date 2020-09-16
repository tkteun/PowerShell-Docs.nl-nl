---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Resources verpakken en uploaden naar een pull-server
ms.openlocfilehash: d0e070b7aa43acbbbf087729d53f06dbc7e7734a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782885"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Resources verpakken en uploaden naar een pull-server

In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld. Als u uw pull-server niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)

Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan. In dit artikel wordt uitgelegd hoe u bronnen uploadt, zodat ze beschikbaar zijn om te worden gedownload en clients zodanig configureren dat bronnen automatisch worden gedownload. Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** -of **Push** (V5), downloadt het automatisch alle resources die vereist zijn voor de configuratie van de locatie die is opgegeven in de LCM.

## <a name="package-resource-modules"></a>Pakket resource modules

Elke resource die beschikbaar is voor een client die kan worden gedownload, moet worden opgeslagen in een `.zip` bestand. In het onderstaande voor beeld ziet u de vereiste stappen met behulp van de [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) -resource.

> [!NOTE]
> Als u een client hebt die Power Shell 4,0 gebruikt, moet u de structuur van de resource mappen plat maken en alle versie mappen verwijderen. Zie [meerdere resource versies](../configurations/import-dscresource.md#multiple-resource-versions)voor meer informatie.

U kunt de resource directory comprimeren met elk hulp programma, script of methode die u wilt gebruiken. In Windows kunt u met de _rechter_ muisknop op de `xPSDesiredStateConfiguration` map klikken en vervolgens **verzenden naar**en **gecomprimeerde map**selecteren.

![Klik met de rechter muisknop en verzenden naar-gecomprimeerde map](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a>De naam van het Resource Archief benoemen

Het bron archief moet een naam hebben met de volgende indeling:

```
{ModuleName}_{Version}.zip
```

In het bovenstaande voor beeld `xPSDesiredStateConfiguration.zip` moet de naam worden gewijzigd `xPSDesiredStateConfiguration_8.4.4.0.zip` .

### <a name="create-checksums"></a>Controle sommen maken

Zodra de resource module is gecomprimeerd en de naam ervan is gewijzigd, moet u een **controlesom**maken. De **controlesom** wordt door de LCM op de client gebruikt om te bepalen of de resource is gewijzigd en moet opnieuw worden gedownload. U kunt een **controlesom** maken met de cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , zoals wordt weer gegeven in het onderstaande voor beeld.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Er wordt geen uitvoer weer gegeven, maar u ziet nu een ' xPSDesiredStateConfiguration_8.4.4.0.zip. checksum '. U kunt ook uitvoeren `New-DSCCheckSum` op een map met bestanden met behulp van de `-Path` para meter. Als er al een controlesom bestaat, kunt u afdwingen dat deze opnieuw wordt gemaakt met de `-Force` para meter.

### <a name="where-to-store-resource-archives"></a>Locatie voor het opslaan van resource archieven

#### <a name="on-a-dsc-http-pull-server"></a>Op een DSC HTTP-pull-server

Wanneer u de HTTP-pull-server instelt, zoals wordt uitgelegd in [een DSC HTTP-pull-server instellen](pullServer.md), geeft u directory's op voor de sleutels **para modulepath in** en **ConfigurationPath** . De **ConfigurationPath** -sleutel geeft aan waar de MOF-bestanden moeten worden opgeslagen. De **para modulepath in** geeft aan waar eventuele DSC-resource modules moeten worden opgeslagen.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Op een SMB-share

Als u een **ResourceRepositoryShare**hebt opgegeven, slaat u tijdens het instellen van uw pull-client de archieven en controle sommen op in de map **SourcePath** vanuit het blok **ResourceRepositoryShare** .

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

Als u alleen een **ConfigurationRepositoryShare**hebt opgegeven, slaat u tijdens het instellen van uw pull-client de archieven en controle sommen op in de map **SourcePath** vanuit het blok **ConfigurationRepositoryShare** .

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Resources bijwerken

U kunt afdwingen dat een knoop punt de resources bijwerkt door het versie nummer in de naam van het archief te wijzigen of door een nieuwe controlesom te maken. De pull-client controleert op nieuwere versies van de vereiste resources, evenals bijgewerkte controle sommen wanneer de LCM wordt vernieuwd.

## <a name="see-also"></a>Zie ook

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)
