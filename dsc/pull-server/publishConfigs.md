---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Publiceren naar een Pull-Server met behulp van configuratie-ID's (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686367"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publiceren naar een Pull-Server met behulp van configuratie-ID's (v4/v5)

De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server. Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)

Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren. In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources. Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.

## <a name="compile-configurations"></a>Configuraties compileren

De eerste stap bij het opslaan van [configuraties](../configurations/configurations.md) is gecompileerd in MOF-bestanden op een Pull-Server. Als u een configuratie algemene en van toepassing op meer clients bevatten, gebruikt u `localhost` in het knooppunt-blok. Het volgende voorbeeld ziet u een configuratie-shell die gebruikmaakt van `localhost` in plaats van de naam van een specifieke client.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Nadat u hebt de configuratie van uw algemene gecompileerd, moet u een bestand 'localhost.mof' hebben.

## <a name="renaming-the-mof-file"></a>Naam van het MOF-bestand

U kunt opslaan '.mof' configuratiebestanden op een Pull-Server door **ConfigurationName** of **ConfigurationID**. Afhankelijk van hoe u van plan bent voor het instellen van uw pull-clients, kunt u een sectie hieronder goed uw gecompileerde ".mof" om bestandsnamen te wijzigen.

### <a name="configuration-ids-guid"></a>Configuratie-ID's (GUID)

U moet de naam van uw bestand 'localhost.mof' naar '<GUID>.mof "bestand. U kunt een willekeurige maken **Guid** met behulp van het voorbeeld hieronder of met behulp van de [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Voorbeelduitvoer

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Vervolgens kunt u uw 'MOF'-bestand met behulp van een acceptabele methode wijzigen. Het onderstaande voorbeeld wordt de [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Voor meer informatie over het gebruik van **GUID's** in uw omgeving, Zie [plannen voor GUID's](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Configuratienamen

U moet de naam van uw bestand 'localhost.mof' naar '<Configuration Name>.mof "bestand. In het volgende voorbeeld wordt wordt de naam van de configuratie van de vorige sectie gebruikt. Vervolgens kunt u uw 'MOF'-bestand met behulp van een acceptabele methode wijzigen. Het onderstaande voorbeeld wordt de [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>De controlesom maken

Elk bestand '.mof' die is opgeslagen op een Pull-Server of SMB-share moet een bijbehorende ".checksum"-bestand hebt. Dit bestand kiest, kunnen clients weten wanneer het bestand gekoppeld ".mof" is gewijzigd en moet opnieuw worden gedownload.

U kunt maken een **controlesom** met de [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. U kunt ook uitvoeren `New-DSCCheckSum` op basis van een map met bestanden met behulp van de `-Path` parameter. Als een controlesom al bestaat, kunt u zorgen dat niet opnieuw worden gemaakt met de `-Force` parameter. Het volgende voorbeeld opgegeven van een map met het bestand '.mof' uit de vorige sectie en maakt gebruik van de `-Force` parameter.

```powershell
New-DscChecksum -Path '.\' -Force
```

Er is geen uitvoer wordt weergegeven, maar u ziet nu een '<GUID or Configuration Name>. mof.checksum "bestand.

## <a name="where-to-store-mof-files-and-checksums"></a>Waar om op te slaan en controlesommen van het MOF-bestanden

### <a name="on-a-dsc-http-pull-server"></a>Op een DSC-HTTP-Pull-Server

Bij het instellen van uw HTTP-Pull-Server, zoals uitgelegd in [instellen van een DSC HTTP-Pull-Server](pullServer.md), geeft u de mappen voor de **ModulePath** en **ConfigurationPath** sleutels. De **ConfigurationPath** sleutel geeft aan waar alle bestanden ".mof" moeten worden opgeslagen. De **ConfigurationPath** geeft aan waar een MOF-bestanden en ".checksum" bestanden moeten worden opgeslagen.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Op een SMB-Share

Bij het instellen van een Pull-Client een SMB-share te gebruiken, geeft u een **ConfigurationRepositoryShare**. Alle bestanden van ".mof" en ".checksum" bestanden moeten vervolgens worden opgeslagen in de **bronpad** map van de **ConfigurationRepositoryShare** blokkeren.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Volgende stappen

Vervolgens wilt u Pull-Clients om op te halen van de opgegeven configuratie configureren. Zie voor meer informatie, een van de volgende handleidingen:

- [Instellen van een Pull-Client met behulp van configuratie-ID's (v4)](pullClientConfigId4.md)
- [Instellen van een Pull-Client met behulp van configuratie-ID's (v5)](pullClientConfigId.md)
- [Instellen van een Pull-Client met behulp van configuratienamen (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Zie ook

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)
- [Pakket- en Resources uploaden naar een Pull-Server](package-upload-resources.md)
