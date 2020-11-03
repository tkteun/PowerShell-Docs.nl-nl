---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: 42a2b37144d9af188a7204500227fddf4827bdf9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251065"
---
# Update-Module

## SAMENVATTING
Downloadt en installeert de nieuwste versie van de opgegeven modules van een online galerie naar de lokale computer.

## SYNTAXIS

### Alles

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet wordt de `Update-Module` nieuwste versie van een module in een online galerie geïnstalleerd. U wordt gevraagd om de update te bevestigen voordat deze wordt geïnstalleerd. Updates worden alleen geïnstalleerd voor modules die zijn geïnstalleerd op de lokale computer met `Install-Module` . `Update-Module` Hiermee zoekt u naar `$env:PSModulePath` geïnstalleerde modules.

`Update-Module` Als er geen para meters zijn opgegeven, worden alle geïnstalleerde modules bijgewerkt. Gebruik de para meter **name** om een module op te geven die moet worden bijgewerkt. U kunt bijwerken naar de specifieke versie van een module met behulp van de para meter **RequiredVersion** .

Als een geïnstalleerde module al de nieuwste versie is, wordt de module niet bijgewerkt. Als de module niet wordt gevonden in `$env:PSModulePath` , wordt een fout bericht weer gegeven.

Als u de geïnstalleerde modules wilt weer geven, gebruikt u `Get-InstalledModule` .

## VOORBEELDEN

### Voor beeld 1: alle modules bijwerken

In dit voor beeld worden alle geïnstalleerde modules bijgewerkt naar de nieuwste versie in een online galerie.

```powershell
Update-Module
```

### Voor beeld 2: een module bijwerken op naam

In dit voor beeld wordt een specifieke module in een online galerie bijgewerkt naar de nieuwste versie.

```powershell
Update-Module -Name SpeculationControl
```

`Update-Module` maakt gebruik van de para meter **name** voor het bijwerken van een specifieke module, **SpeculationControl**.

### Voor beeld 3: wat-als-Update-Module worden uitgevoerd weer geven

In dit voor beeld wordt een wat-als-scenario weer gegeven wat er gebeurt als `Update-Module` wordt uitgevoerd. De opdracht wordt niet uitgevoerd.

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

`Update-Module` Hiermee wordt de **WhatIf** -para meter weer gegeven wat er zou gebeuren als ze `Update-Module` werden uitgevoerd.

### Voor beeld 4: een module bijwerken naar een opgegeven versie

In dit voor beeld wordt een module bijgewerkt naar een specifieke versie. De versie moet in de online galerie bestaan, anders wordt er een fout bericht weer gegeven.

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

`Update-Module` maakt gebruik van de para meter **name** om de module **SpeculationControl** op te geven. De **RequiredVersion** para meter geeft u de versie, **1.0.14**.

### Voor beeld 5: een module bijwerken zonder bevestiging

In dit voor beeld wordt geen bevestiging gevraagd om de module bij te werken naar de nieuwste versie vanuit een online galerie. Als de module al is geïnstalleerd, wordt de module met de para meter **Force** opnieuw geïnstalleerd.

```powershell
Update-Module -Name SpeculationControl -Force
```

`Update-Module` maakt gebruik van de para meter **name** om de module **SpeculationControl** op te geven. Met de para meter **Force** wordt de module bijgewerkt zonder dat de gebruiker om bevestiging wordt gevraagd.

## PARAMETERS

### -AcceptLicense

Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.

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

Hiermee kunt u een module bijwerken met de nieuwere module die is gemarkeerd als een voorlopige versie.

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

### -Confirm

Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-Module` .

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

Hiermee geeft u een gebruikers account op dat gemachtigd is om een module bij te werken.

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

Hiermee wordt een update van elke opgegeven module geforceerd zonder dat u wordt gevraagd om een bevestiging te vragen. Als de module al is geïnstalleerd, wordt de module **geforceerd** opnieuw geïnstalleerd.

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

### -MaximumVersion

Hiermee geeft u de maximum versie van één module op die moet worden bijgewerkt. U kunt deze para meter niet toevoegen als u probeert meerdere modules bij te werken. De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen op van een of meer modules die moeten worden bijgewerkt. `Update-Module` Hiermee wordt gezocht naar `$env:PSModulePath` de modules die moeten worden bijgewerkt. Als er geen overeenkomsten worden gevonden in `$env:PSModulePath` voor de opgegeven module naam, treedt er een fout op.

Joker tekens worden geaccepteerd in module namen. Als u Joker tekens toevoegt aan de opgegeven naam en er geen overeenkomsten worden gevonden, treedt er geen fout op.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.

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

Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.

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

### -RequiredVersion

Hiermee geeft u de exacte versie op waarop de bestaande geïnstalleerde module wordt bijgewerkt. De versie die is opgegeven door **RequiredVersion** moet aanwezig zijn in de online galerie, anders wordt er een fout bericht weer gegeven. Als er meer dan één module in één opdracht is bijgewerkt, kunt u **RequiredVersion** niet gebruiken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het installatie bereik van de module op. De acceptabele waarden voor deze para meter zijn **ALLUSERS** en **CurrentUser**. Als **Scope** niet is opgegeven, wordt de update geïnstalleerd in het bereik van **CurrentUser** .

Het bereik **ALLUSERS** vereist verhoogde machtigingen en installeert modules op een locatie die toegankelijk is voor alle gebruikers van de computer:

`$env:ProgramFiles\PowerShell\Modules`

Voor de **CurrentUser** zijn geen verhoogde machtigingen vereist en modules geïnstalleerd op een locatie die alleen toegankelijk is voor de huidige gebruiker van de computer:

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
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Update-Module` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### System.String[]

### System. String

### System. Management. Automation. PSCredential

### System. URI

## UITVOER

### System. object

## OPMERKINGEN

Voor de Power shell-versie 6,0 en hoger is het standaard installatie bereik altijd **CurrentUser**.
Module-updates voor **CurrentUser** , `$home\Documents\PowerShell\Modules` , hebben geen verhoogde machtigingen nodig. Module-updates voor **ALLUSERS** , `$env:ProgramFiles\PowerShell\Modules` , vereist verhoogde machtigingen.

`Update-Module` wordt uitgevoerd op Power Shell 3,0 of latere versies van Power shell, op Windows 7 of Windows 2008 R2 en latere versies van Windows.

Als de module die u opgeeft met de para meter **name** niet is geïnstalleerd met behulp van `Install-Module` , treedt er een fout op.

U kunt alleen uitvoeren `Update-Module` op modules die u hebt geïnstalleerd vanuit de online galerie door uit te voeren `Install-Module` .

Als er `Update-Module` wordt geprobeerd binaire bestanden bij te werken, `Update-Module` retourneert een fout die de probleem processen identificeert. De gebruiker wordt op de hoogte gesteld `Update-Module` wanneer de processen zijn gestopt.

## GERELATEERDE KOPPELINGEN

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Installatie-module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Uninstall-module](Uninstall-Module.md)
