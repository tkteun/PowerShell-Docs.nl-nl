---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: be7ffa38a0409fa7ef0d01649b863a32732e34de
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249730"
---
# Register-PSRepository

## SAMENVATTING
Registreert een Power shell-opslag plaats.

## SYNTAXIS

### NameParameterSet (standaard)

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### PSGalleryParameterSet

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## BESCHRIJVING

De `Register-PSRepository` cmdlet registreert de standaard opslagplaats voor Power shell-modules. Nadat een opslag plaats is geregistreerd, kunt u ernaar verwijzen vanuit `Find-Module` de `Install-Module` `Publish-Module` cmdlets, en. De geregistreerde opslag plaats wordt de standaard opslagplaats in `Find-Module` en `Install-Module` .

Geregistreerde opslag plaatsen zijn gebruikersspecifieke. Ze worden niet geregistreerd in een context voor het hele systeem.

Elke geregistreerde opslag plaats is gekoppeld aan een OneGet-pakket provider, die wordt opgegeven met de para meter **PackageManagementProvider** . Elke OneGet-provider is ontworpen om te communiceren met een specifiek type opslag plaats. De NuGet-provider is bijvoorbeeld ontworpen om te communiceren met op NuGet gebaseerde opslag plaatsen. Als tijdens de registratie geen OneGet-provider is opgegeven, probeert PowerShellGet een OneGet-provider te vinden die de opgegeven bron locatie kan verwerken.

## VOORBEELDEN

### Voor beeld 1: een opslag plaats registreren

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

De eerste opdracht wordt geregistreerd `https://www.myget.org/F/powershellgetdemo/` als een opslag plaats voor de huidige gebruiker. Nadat myNuGetSource is geregistreerd, kunt u er expliciet naar verwijzen tijdens het zoeken, installeren en publiceren van modules. Omdat de para meter **PackageManagementProvider** niet is opgegeven, is de opslag plaats niet expliciet gekoppeld aan een OneGet-pakket provider, dus PowerShellGet polls beschik bare pakket providers en koppelt deze aan de NuGet-provider.

Met de tweede opdracht worden de geregistreerde opslag plaatsen opgehaald en worden de resultaten weer gegeven.

## PARAMETERS

### -Credential

Hiermee geeft u de referenties op van een account met rechten voor het registreren van een opslag plaats.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Default

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstallationPolicy

Hiermee geeft u het installatie beleid op. Geldige waarden zijn: vertrouwd, niet vertrouwd. De standaard waarde is niet vertrouwd.

Het installatie beleid van een opslag plaats specificeert Power shell-gedrag bij het installeren vanuit die opslag plaats. Wanneer er modules worden geïnstalleerd vanuit een niet-vertrouwde opslag plaats, wordt de gebruiker gevraagd om bevestiging.

U kunt de **InstallationPolicy** instellen met de `Set-PSRepository` cmdlet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam op van de opslag plaats die u wilt registreren. U kunt deze naam gebruiken om de opslag plaats in cmdlets zoals en te specificeren `Find-Module` `Install-Module` .

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Hiermee geeft u een OneGet-pakket provider op. Als u geen waarde opgeeft voor deze para meter, PowerShellGet polls beschik bare pakket providers en koppelt deze opslag plaats aan de eerste pakket provider waarmee wordt aangegeven dat de opslag plaats kan worden verwerkt.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

Hiermee wordt de URI van de publicatie locatie opgegeven. Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de publicatie locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2/Packages` .

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Hiermee geeft u de publicatie locatie van het script op.

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Hiermee geeft u de bron locatie van het script op.

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceLocation

Hiermee geeft u de URI op voor het detecteren en installeren van modules uit deze opslag plaats. Een URI kan een NuGet zijn (de meest voorkomende situatie), de HTTP-, HTTPS-, FTP-of file-locatie.

Bijvoorbeeld: voor opslag plaatsen op basis van NuGet is de bron locatie vergelijkbaar met `https://someNuGetUrl.com/api/v2` .

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSCredential

### System. URI

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-PSRepository](Get-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Registratie ongedaan maken-PSRepository](Unregister-PSRepository.md)
