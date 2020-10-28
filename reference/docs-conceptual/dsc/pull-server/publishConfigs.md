---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Publiceren naar een pull-server met behulp van configuratie-Id's (v4/V5)
description: In dit artikel wordt beschreven hoe u bronnen uploadt, zodat deze beschikbaar zijn om te worden gedownload en clients configureren voor het automatisch downloaden van resources.
ms.openlocfilehash: 20e12e3cac6b6e4a86563576f4a915429b18aadb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646840"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Publiceren naar een pull-server met behulp van configuratie-Id's (v4/V5)

In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld. Als u uw pull-server nog niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)

Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan. In dit artikel wordt beschreven hoe u bronnen uploadt, zodat deze beschikbaar zijn om te worden gedownload en clients configureren voor het automatisch downloaden van resources. Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** of **Push** (V5), worden de resources die vereist zijn voor de configuratie automatisch gedownload van de locatie die is opgegeven in de lokale Configuration Manager (LCM).

## <a name="compile-configurations"></a>Configuraties compileren

De eerste stap voor het opslaan van [configuraties](../configurations/configurations.md) op een pull-server is het compileren van deze in `.mof` bestanden. Als u een algemeen configuratie wilt maken en van toepassing is op meer clients, gebruikt u `localhost` in uw knooppunt blok. In het onderstaande voor beeld ziet u een configuratie shell die wordt gebruikt `localhost` in plaats van een specifieke client naam.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Wanneer u de algemene configuratie hebt gecompileerd, hebt u een `localhost.mof` bestand nodig.

## <a name="renaming-the-mof-file"></a>De naam van het MOF-bestand wijzigen

U kunt configuratie `.mof` bestanden opslaan op een pull-server via **configuratiepad** of **ConfigurationID** . Afhankelijk van hoe u uw pull-clients wilt instellen, kunt u een van de onderstaande secties kiezen om de naam van uw gecompileerde bestanden goed te wijzigen `.mof` .

### <a name="configuration-ids-guid"></a>Configuratie-Id's (GUID)

U moet de naam van het `localhost.mof` bestand wijzigen in `<GUID>.mof` bestand. U kunt een wille keurige **GUID** maken met behulp van het voor beeld hieronder of met de cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .

```powershell
[System.Guid]::NewGuid()
```

Voorbeelduitvoer

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

U kunt de naam van uw bestand vervolgens wijzigen `.mof` met behulp van een aanvaard bare methode. In het onderstaande voor beeld wordt de cmdlet [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) gebruikt.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Zie voor meer informatie over het gebruik van **guid's** in uw omgeving [plan for guid's](secureServer.md#guids).

### <a name="configuration-names"></a>Configuratie namen

U moet de naam van het `localhost.mof` bestand wijzigen in `<Configuration Name>.mof` bestand. In het volgende voor beeld wordt de naam van de configuratie uit de vorige sectie gebruikt. U kunt de naam van uw bestand vervolgens wijzigen `.mof` met behulp van een aanvaard bare methode. In het onderstaande voor beeld wordt de cmdlet [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) gebruikt.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>De controlesom maken

Elk `.mof` bestand dat is opgeslagen op een pull-server of de SMB-share moet een bijbehorend `.checksum` bestand hebben.
Met dit bestand kunnen clients weten wanneer het bijbehorende `.mof` bestand is gewijzigd en het opnieuw moet worden gedownload.

U kunt een **controlesom** maken met de cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) . U kunt ook uitvoeren `New-DSCCheckSum` op een map met bestanden met behulp van de `-Path` para meter.
Als er al een controlesom bestaat, kunt u afdwingen dat deze opnieuw wordt gemaakt met de `-Force` para meter. In het volgende voor beeld is een map opgegeven met het `.mof` bestand uit de vorige sectie en wordt de `-Force` para meter gebruikt.

```powershell
New-DscChecksum -Path '.\' -Force
```

Er wordt geen uitvoer weer gegeven, maar u ziet nu een `<GUID or Configuration Name>.mof.checksum` bestand.

## <a name="where-to-store-mof-files-and-checksums"></a>Waar u MOF-bestanden en controle sommen opslaat

### <a name="on-a-dsc-http-pull-server"></a>Op een DSC HTTP-pull-server

Wanneer u de HTTP-pull-server instelt, zoals wordt uitgelegd in [een DSC HTTP-pull-server instellen](pullServer.md), geeft u directory's op voor de sleutels **para modulepath in** en **ConfigurationPath** . De **para modulepath in** -sleutel geeft aan waar de verpakte bestanden van een module `.zip` moeten worden opgeslagen. De **ConfigurationPath** geeft aan waar `.mof` bestanden en `.checksum` bestanden moeten worden opgeslagen.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Op een SMB-share

Wanneer u een pull-client instelt voor het gebruik van een SMB-share, geeft u een **ConfigurationRepositoryShare** op.
Alle `.mof` bestanden en `.checksum` bestanden moeten worden opgeslagen in de map **SourcePath** van het **ConfigurationRepositoryShare** -blok.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Volgende stappen

Vervolgens moet u pull-clients configureren voor het ophalen van de opgegeven configuratie. Zie een van de volgende hand leidingen voor meer informatie:

- [Een pull-client instellen met behulp van configuratie-Id's (v4)](pullClientConfigId4.md)
- [Een pull-client instellen met behulp van configuratie-Id's (V5)](pullClientConfigId.md)
- [Een pull-client instellen met behulp van configuratie namen (V5)](pullClientConfigNames.md)

## <a name="see-also"></a>Zie ook

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)
- [Resources verpakken en uploaden naar een pull-server](package-upload-resources.md)
