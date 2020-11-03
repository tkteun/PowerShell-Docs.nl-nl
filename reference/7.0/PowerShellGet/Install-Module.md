---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: 0e6dfd00da246b5632474c45d3794d796715240c
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2020
ms.locfileid: "93251700"
---
# Install-Module

## SAMENVATTING
Hiermee downloadt u een of meer modules uit een opslag plaats en installeert u deze op de lokale computer.

## SYNTAXIS

### NameParameterSet (standaard)

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Install-Module` cmdlet haalt een of meer modules op die voldoen aan opgegeven criteria vanuit een online opslagplaats. De cmdlet controleert of de zoek resultaten geldige modules zijn en kopieert de module mappen naar de installatie locatie. Geïnstalleerde modules worden na de installatie niet automatisch geïmporteerd.
U kunt filteren welke module is geïnstalleerd op basis van de minimum-, maximum-en exacte versie van de opgegeven modules.

Als de module die wordt geïnstalleerd dezelfde naam of versie heeft, of opdrachten bevat in een bestaande module, worden waarschuwings berichten weer gegeven. Nadat u hebt bevestigd dat u de module wilt installeren en de waarschuwingen wilt negeren, gebruikt u de `-Force` `-AllowClobber` para meters en. Afhankelijk van de instellingen van uw opslag plaats moet u mogelijk een vraag beantwoorden om de module-installatie voort te zetten.

In deze voor beelden wordt de [PowerShell Gallery](https://www.powershellgallery.com/) als de enige geregistreerde opslag plaats gebruikt. `Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen weer gegeven. Als u meerdere geregistreerde opslag plaatsen hebt, gebruikt u de `-Repository` para meter om de naam van de opslag plaats op te geven.

## VOORBEELDEN

### Voor beeld 1: een module zoeken en installeren

In dit voor beeld wordt een module in de opslag plaats gevonden en wordt de module geïnstalleerd.

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

De `Find-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. Standaard wordt de nieuwste versie van de module gedownload uit de opslag plaats. Het object wordt vanuit de pijp lijn naar de `Install-Module` cmdlet verzonden. `Install-Module` installeert de module voor alle gebruikers in `$env:ProgramFiles\PowerShell\Modules` .

### Voor beeld 2: een module installeren op naam

In dit voor beeld is de nieuwste versie van de **PowerShellGet** -module geïnstalleerd.

```powershell
Install-Module -Name PowerShellGet
```

De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. Standaard wordt de nieuwste versie van de module gedownload uit de opslag plaats en geïnstalleerd.

### Voor beeld 3: een module installeren met de minimale versie

In dit voor beeld is de minimale versie van de **PowerShellGet** -module geïnstalleerd. De **MinimumVersion** para meter geeft u de laagste versie van de module op die moet worden geïnstalleerd. Als er een nieuwere versie van de module beschikbaar is, wordt die versie gedownload en geïnstalleerd voor alle gebruikers.

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. De para meter **MinimumVersion** geeft aan dat versie **2.0.1** is gedownload uit de opslag plaats en moet worden geïnstalleerd. Omdat versie **2.0.4** beschikbaar is, wordt die versie gedownload en geïnstalleerd voor alle gebruikers.

### Voor beeld 4: een specifieke versie van een module installeren

In dit voor beeld wordt een specifieke versie van de **PowerShellGet** -module geïnstalleerd.

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. De para meter **RequiredVersion** geeft aan dat versie **2.0.0** wordt gedownload en geïnstalleerd voor alle gebruikers.

### Voor beeld 5: een module alleen voor de huidige gebruiker installeren

In dit voor beeld wordt de nieuwste versie van een module gedownload en geïnstalleerd, alleen voor de huidige gebruiker.

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.
`Install-Module` downloadt en installeert de nieuwste versie van **PowerShellGet** in de map van de huidige gebruiker `$home\Documents\PowerShell\Modules` .

## PARAMETERS

### -AcceptLicense

Voor modules waarvoor een licentie is vereist, accepteert **AcceptLicense** automatisch de licentie overeenkomst tijdens de installatie. Zie voor meer informatie [modules waarvoor acceptatie van licenties is vereist](/powershell/scripting/gallery/concepts/module-license-acceptance).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowClobber

Onderdrukt waarschuwings berichten over de installatie conflicten met bestaande opdrachten op een computer.
Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.
**AllowClobber** en **Force** kunnen samen worden gebruikt in een `Install-Module` opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrerelease

Hiermee kunt u een module installeren die als voorlopige versie is gemarkeerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat de cmdlet wordt uitgevoerd `Install-Module` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een module voor een opgegeven pakket provider of bron.

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

### -Force

Hiermee wordt een module geïnstalleerd en worden waarschuwings berichten over de installatie conflicten van de module genegeerd. Als er al een module met dezelfde naam op de computer aanwezig is **, kunnen** er meerdere versies worden geïnstalleerd. Als er een bestaande module met dezelfde naam en versie is, wordt door **geforceerd** de versie overschreven. **Force** en **AllowClobber** kunnen samen worden gebruikt in een `Install-Module` opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Wordt gebruikt voor de invoer van de pijp lijn.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u de maximum versie van één module op die moet worden geïnstalleerd. De geïnstalleerde versie moet kleiner zijn dan of gelijk zijn aan **MaximumVersion**. Als u meerdere modules wilt installeren, kunt u **MaximumVersion** niet gebruiken. **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde `Install-Module` opdracht.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de minimum versie op van één module die moet worden geïnstalleerd. De geïnstalleerde versie moet groter dan of gelijk zijn aan **MinimumVersion**. Als er een nieuwere versie van de module beschikbaar is, wordt de nieuwere versie geïnstalleerd. Als u meerdere modules wilt installeren, kunt u **MinimumVersion** niet gebruiken.
**MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde `Install-Module` opdracht.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de exacte namen van modules op die u wilt installeren vanuit de online galerie. Een door komma's gescheiden lijst met module namen wordt geaccepteerd. De module naam moet overeenkomen met de module naam in de opslag plaats. Gebruiken `Find-Module` om een lijst met module namen op te halen.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
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

### -Opslag plaats

Gebruik de para meter **opslagplaats** om op te geven welke opslag plaats wordt gebruikt voor het downloaden en installeren van een module. Wordt gebruikt wanneer meerdere opslag plaatsen zijn geregistreerd. Hiermee geeft u de naam van een geregistreerde opslag plaats in de `Install-Module` opdracht op. Als u een opslag plaats wilt registreren, gebruikt u `Register-PSRepository` .
Gebruik om geregistreerde opslag plaatsen weer te geven `Get-PSRepository` .

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u de exacte versie van één module op die u wilt installeren. Als er geen overeenkomst in de opslag plaats voor de opgegeven versie is, wordt er een fout bericht weer gegeven. Als u meerdere modules wilt installeren, kunt u **RequiredVersion** niet gebruiken. **RequiredVersion** kan niet worden gebruikt in dezelfde `Install-Module` opdracht als **MinimumVersion** of **MaximumVersion**.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het installatie bereik van de module op. De acceptabele waarden voor deze para meter zijn **ALLUSERS** en **CurrentUser**.

Met het **ALLUSERS** -bereik worden modules geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer:

`$env:ProgramFiles\PowerShell\Modules`

De map **CurrentUser** installeert modules op een locatie die alleen toegankelijk is voor de huidige gebruiker van de computer. Bijvoorbeeld:

`$home\Documents\PowerShell\Modules`

Als er geen **bereik** is gedefinieerd, wordt de standaard waarde ingesteld op basis van de PowerShellGet-versie.

- In PowerShellGet-versies 2.0.0 en hoger is de standaard versie **CurrentUser** , waarvoor geen uitbrei ding van bevoegdheden voor installatie vereist is.
- In PowerShellGet 1. x versies is de standaard waarde **ALLUSERS** , waarvoor uitbrei ding van bevoegdheden vereist is voor installatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

Hiermee kunt u een nieuwere versie installeren van een module die al op uw computer aanwezig is. Bijvoorbeeld wanneer een bestaande module digitaal is ondertekend door een vertrouwde uitgever, maar de nieuwe versie niet digitaal is ondertekend door een vertrouwde uitgever.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Laat zien wat er zou gebeuren als een `Install-Module` opdracht werd uitgevoerd. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### PSRepositoryItemInfo

`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten waarnaar de pijp lijn kan worden verzonden `Install-Module` .

### System.String[]

### System. Management. Automation. PSObject []

### System. String

### System. Management. Automation. PSCredential

### System. URI

## UITVOER

### Micro soft. Power shell. commands. PSRepositoryItemInfo

Wanneer u de para meter **PassThru** gebruikt, wordt `Install-Module` een **PSRepositoryItemInfo** -object uitgevoerd voor de module. Dit is dezelfde informatie die u van de cmdlet krijgt `Find-Module` .

## OPMERKINGEN

`Install-Module` wordt uitgevoerd op Power shell 5,0 of hoger, op Windows 7 of Windows 2008 R2 en latere versies van Windows.

Als beveiligings best practice kunt u de code van een module evalueren voordat u cmdlets of functions voor de eerste keer uitvoert. Om te voor komen dat modules worden uitgevoerd die schadelijke code bevatten, worden geïnstalleerde modules na de installatie niet automatisch geïmporteerd.

Als de module naam die is opgegeven door de para meter **name** niet voor komt in de opslag plaats, `Install-Module` wordt een fout geretourneerd.

Als u meerdere modules wilt installeren, gebruikt u de para meter **name** en geeft u een door komma's gescheiden matrix van module namen op. Als u meerdere module namen opgeeft, kunt u **MinimumVersion** , **MaximumVersion** of **RequiredVersion** niet gebruiken. `Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten waarnaar de pijp lijn kan worden verzonden `Install-Module` . De pijp lijn is een andere manier om meerdere modules op te geven die u wilt installeren in één opdracht.

Standaard worden modules voor het bereik van **ALLUSERS** geïnstalleerd in `$env:ProgramFiles\PowerShell\Modules` . De standaard instelling voor komt Verwar ring bij de installatie van Power shell desired state Configuration (DSC)-resources.

Een module-installatie mislukt en kan niet worden geïmporteerd als deze geen `.psm1` , `.psd1` of `.dll` dezelfde naam in de map heeft. Gebruik de para meter **Force** om de module te installeren.

Als de versie van een bestaande module overeenkomt met de naam die is opgegeven door de para meter **name** en de para meter **MinimumVersion** of **RequiredVersion** niet wordt gebruikt, wordt `Install-Module` de module op de achtergrond uitgevoerd, maar wordt deze niet geïnstalleerd.

Als de versie van een bestaande module groter is dan de waarde van de para meter **MinimumVersion** , of gelijk is aan de waarde van de para meter **RequiredVersion** , wordt `Install-Module` de module op de achtergrond voortgezet, maar wordt niet de modules geïnstalleerd.

Als de bestaande module niet overeenkomt met de waarden die zijn opgegeven door de para meters **MinimumVersion** of **RequiredVersion** , treedt er een fout op in de `Install-Module` opdracht. Als de versie van de bestaande geïnstalleerde module bijvoorbeeld lager is dan de **MinimumVersion** -waarde of niet gelijk is aan de **RequiredVersion** -waarde.

Bij een module-installatie worden ook alle afhankelijke modules geïnstalleerd die vereist zijn voor de module Uitgever.
De uitgever geeft de vereiste modules en hun versies op in het module manifest.

## GERELATEERDE KOPPELINGEN

[Find-Module](Find-Module.md)

[Get-PSRepository](Get-PSRepository.md)

[Import-module](../Microsoft.PowerShell.Core/Import-Module.md)

[Publish-Module](Publish-Module.md)

[REGI ster-PSRepository](Register-PSRepository.md)

[Uninstall-module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[about_Module](../Microsoft.PowerShell.Core/About/about_Modules.md)
