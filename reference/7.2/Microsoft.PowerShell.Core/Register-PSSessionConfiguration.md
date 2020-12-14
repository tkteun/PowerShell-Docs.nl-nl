---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: 0ec31d32ef73108b53b18b529cc93aa80787fe25
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706050"
---
# Register-PSSessionConfiguration

## SAMENVATTING
Hiermee maakt en registreert u een nieuwe sessie configuratie.

## SYNTAXIS

### NameParameterSet (standaard)

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Register-PSSessionConfiguration` cmdlet maakt en registreert een nieuwe sessie configuratie op de lokale computer. Dit is een geavanceerde cmdlet die u kunt gebruiken om aangepaste sessies voor externe gebruikers te maken.

Elke Power shell-sessie (**PSSession**) maakt gebruik van een sessie configuratie, ook wel bekend als een eind punt.
Wanneer gebruikers een sessie maken die verbinding maakt met de computer, kunnen ze een sessie configuratie selecteren of de standaard sessie configuratie gebruiken die wordt geregistreerd wanneer u externe communicatie van Power shell inschakelt.
Gebruikers kunnen ook de $PSSessionConfigurationName voorkeurs variabele instellen, waarmee een standaard configuratie wordt opgegeven voor externe sessies die zijn gemaakt in de huidige sessie.

De sessie configuratie definieert de omgeving voor de externe sessie. De configuratie kan bepalen welke opdrachten en taal elementen beschikbaar zijn in de sessie en kan instellingen bevatten waarmee de computer wordt beveiligd, zoals de onderdelen die de hoeveelheid gegevens beperken die de sessie op afstand kan ontvangen in één object of opdracht. De security descriptor van de sessie configuratie bepaalt welke gebruikers gemachtigd zijn om de sessie configuratie te gebruiken.

U kunt de configuratie-elementen definiëren met behulp van een assembly die een nieuwe configuratie klasse implementeert en met behulp van een script dat in de sessie wordt uitgevoerd. Vanaf Power Shell 3,0 kunt u ook een sessie configuratie bestand gebruiken om de sessie configuratie te definiëren.

Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie over de configuratie van sessies.
Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.

## VOORBEELDEN

### Voor beeld 1: een NewShell-sessie configuratie registreren

In dit voor beeld registreren we de **NewShell** -sessie configuratie. De para meters **assemblyname** en **Application base** geven de locatie van het **MyShell.dll** bestand op, waarmee de cmdlets en providers in de sessie configuratie worden opgegeven. De **ConfigurationTypeName** para meter geeft u de configuratie klasse op die van de assembly moet worden gebruikt.

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

Als u deze configuratie wilt gebruiken, typt u `New-PSSession -ConfigurationName newshell` .

### Voor beeld 2: een MaintenanceShell-sessie configuratie registreren

In dit voor beeld wordt de **MaintenanceShell** -sessie configuratie op de lokale computer geregistreerd. De **StartupScript** para meter geeft u het `Maintenance.ps1` script op.

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

Wanneer een gebruiker een `New-PSSession` opdracht gebruikt en de **MaintenanceShell** -configuratie selecteert, `Maintenance.ps1` wordt het script in de nieuwe sessie uitgevoerd. Met het script kan de sessie worden geconfigureerd. Dit omvat het importeren van modules en het instellen van het uitvoerings beleid voor de sessie. Als het script fouten genereert, inclusief niet-afsluit fouten, `New-PSSession` mislukt de opdracht.

### Voor beeld 3: een sessie configuratie registreren

In dit voor beeld wordt de **AdminShell** -sessie configuratie geregistreerd.

De `$sessionParams` variabele is een hashtabel die alle parameter waarden bevat. Deze hashtabel wordt door gegeven aan de cmdlet met behulp van Power shell splatting. De `Register-PSSessionConfiguration` opdracht gebruikt de para meter **SecurityDescritorSDDL** om de SDDL op te geven in de waarde van de `$sddl` variabele en de para meter **MaximumReceivedObjectSizeMB** om de limiet voor de object grootte te verhogen. De para meter **StartupScript** wordt ook gebruikt om een script op te geven waarmee de sessie wordt geconfigureerd.

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### Voor beeld 4: een configuratie container element retour neren

In dit voor beeld ziet u hoe u de **MaintenanceShell** -configuratie registreert.
`Register-PSSessionConfiguration` retourneert een **WSManConfigContainerElement** -object dat is opgeslagen in de `$s` variabele. `Format-List` Hiermee worden alle eigenschappen van het geretourneerde object weer gegeven. De eigenschap **PSPath** geeft aan dat het object is opgeslagen in een map van het WSMan:-station. `Get-ChildItem` (alias `dir` ) Hiermee worden de items in het pad weer gegeven `WSMan:\LocalHost\PlugIn` . Dit zijn onder andere de nieuwe **MaintenanceShell** -configuratie en de twee standaard configuraties die worden geleverd met Power shell.

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### Voor beeld 5: een sessie configuratie registreren met een opstart script

In dit voor beeld maken en registreren we de **WithProfile** -sessie configuratie. Met de para meter **StartupScript** wordt Power shell omgeleid om het opgegeven script uit te voeren voor elke sessie die gebruikmaakt van de sessie configuratie.

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

Het script bevat één opdracht die gebruikmaakt van punt bronnen om het **CurrentUserAllHosts** -Profiel van de gebruiker uit te voeren in het huidige bereik van de sessie.

Zie [about_Profiles](./About/about_Profiles.md)voor meer informatie over profielen. Zie [about_Scopes](./About/about_Scopes.md)voor meer informatie over punten.

## PARAMETERS

### -AccessMode

Hiermee wordt de sessie configuratie in-en uitgeschakeld en wordt bepaald of deze kan worden gebruikt voor externe of lokale sessies op de computer. De aanvaardbare waarden voor deze parameter zijn:

- Uitgeschakeld. Hiermee schakelt u de sessie configuratie uit. Het kan niet worden gebruikt voor externe of lokale toegang tot de computer.
- Lokale. Hiermee kunnen gebruikers van de lokale computer de sessie configuratie gebruiken om een lokale loop back-sessie op dezelfde computer te maken, maar wordt de toegang tot externe gebruikers geweigerd.
- Beveiligingslek. Hiermee kunnen lokale en externe gebruikers de sessie configuratie gebruiken om sessies te maken en opdrachten uit te voeren op deze computer.

De standaard waarde is extern.

Andere cmdlets kunnen de waarde van deze para meter later overschrijven. `Enable-PSRemoting`Met de cmdlet kunt u bijvoorbeeld externe toegang tot alle sessie configuraties toestaan, de `Enable-PSSessionConfiguration` cmdlet maakt sessie configuraties mogelijk en de `Disable-PSRemoting` cmdlet voor komt externe toegang tot alle sessie configuraties.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Application base

Hiermee geeft u het pad op van het assembly bestand ( \* . dll) dat is opgegeven in de waarde van de para meter **assemblyname** . Gebruik deze para meter wanneer de waarde van de para meter **assemblyname** geen pad bevat. De standaardwaarde is de huidige map.

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Assemblyname

Hiermee geeft u de naam op van een assembly bestand ( \* . dll) waarin het configuratie type is gedefinieerd. U kunt het pad van het dll-bestand opgeven in deze para meter of in de waarde van de para meter **Application base** .

Deze para meter is vereist wanneer u de para meter **ConfigurationTypeName** opgeeft.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

Hiermee geeft u de volledig gekwalificeerde naam op van het Microsoft .NET Framework-type dat wordt gebruikt voor deze configuratie. Voor het type dat u opgeeft, moet de klasse **System. Management. Automation. Remoting. PSSessionConfiguration** worden geïmplementeerd.

Als u het assembly bestand ( \* . dll) wilt opgeven dat het configuratie type implementeert, geeft u de para meters **Assemblyname** en **Application base** op.

Door een type te maken, kunt u meer aspecten van de sessie configuratie beheren, zoals het weer geven of verbergen van bepaalde para meters van cmdlets of het instellen van de grootte van de gegevens en de object grootte die gebruikers niet kunnen negeren.

Als u deze para meter weglaat, wordt de klasse **DefaultRemotePowerShellConfiguration** gebruikt voor de sessie configuratie.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Onderdrukt alle gebruikers vragen en start de **WinRM** -service opnieuw op zonder dat dit wordt gevraagd. Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.

Geef de para meter **NoServiceRestart** op om het opnieuw opstarten te voor komen en de prompt voor opnieuw opstarten te onderdrukken.

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

### -MaximumReceivedDataSizePerCommandMB

Hiermee geeft u een limiet voor de hoeveelheid gegevens die naar deze computer kan worden verzonden in één externe opdracht. Voer de gegevens grootte in mega bytes (MB) in. De standaard waarde is 50 MB.

Als een limiet voor gegevens grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt en wordt de waarde van deze para meter genegeerd.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

Hiermee geeft u een limiet voor de hoeveelheid gegevens die in een enkel object naar deze computer kan worden verzonden.
Voer de gegevens grootte in mega bytes in. De standaard waarde is 10 MB.

Als een limiet voor object grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt en wordt de waarde van deze para meter genegeerd.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Hiermee geeft u de modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van de sessie configuratie.

Standaard worden alleen **micro soft. Power shell. core** in sessies geïmporteerd. Tenzij de cmdlets worden uitgesloten, kunt u gebruiken `Import-Module` om modules toe te voegen aan de sessie.

De modules die zijn opgegeven in deze parameter waarde worden geïmporteerd in toevoegingen aan modules die zijn opgegeven met de para meter **SessionType** en die worden vermeld in de sleutel **ModulesToImport** in het configuratie bestand () van de sessie `New-PSSessionConfigurationFile` . Instellingen in het bestand met de sessie configuratie kunnen echter de opdrachten die door modules worden geëxporteerd, verbergen of voor komen dat gebruikers ze gebruiken.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een naam op voor de sessie configuratie. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoServiceRestart

De **WinRM** -service wordt niet opnieuw gestart en de prompt voor het opnieuw starten van de service wordt onderdrukt.

Wanneer u een `Register-PSSessionConfiguration` opdracht uitvoert, wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de nieuwe sessie configuratie effectief te maken. Totdat de **WinRM** -service opnieuw is gestart, is de nieuwe sessie configuratie niet effectief.

Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, geeft u de para meter **Force** op. Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .

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

### -Path

Hiermee geeft u het pad en de bestands naam van een sessie configuratie bestand (. pssc), zoals een gemaakt door `New-PSSessionConfigurationFile` . Als u het pad weglaat, de standaard instelling is de huidige map.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

Hiermee wordt bepaald of een 32-bits of 64-bits versie van het Power Shell-proces wordt gestart in sessies die gebruikmaken van deze sessie configuratie. De acceptabele waarden voor deze para meter zijn: x86 (32-bits) en AMD64 (64-bits). De standaard waarde is afhankelijk van de processor architectuur van de computer die als host fungeert voor de sessie configuratie.

U kunt deze para meter gebruiken om een 32-bits sessie te maken op een 64-bits computer. Poging tot het maken van een 64-bits proces op een 32-bits computer mislukt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSVersion

Hiermee geeft u de versie van Power shell in sessies die gebruikmaken van deze sessie configuratie.

De waarde van deze para meter heeft voor rang op de waarde van de sleutel **PowerShellVersion** in het configuratie bestand voor de sessie.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

Hiermee geeft u de referenties op voor opdrachten in de sessie. Standaard worden opdrachten uitgevoerd met de machtigingen van de huidige gebruiker.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

Hiermee geeft u een SDDL-teken reeks (Security Descriptor Definition Language) op voor de configuratie.

Deze teken reeks bepaalt de machtigingen die nodig zijn voor het gebruik van de nieuwe sessie configuratie. Als u een sessie configuratie wilt gebruiken in een sessie, moeten gebruikers ten minste een machtiging voor uitvoeren (invoke) voor de configuratie hebben.

Als de security descriptor complex is, kunt u overwegen de para meter **ShowSecurityDescriptorUI** te gebruiken in plaats van deze para meter. U kunt niet beide para meters in dezelfde opdracht gebruiken.

Als u deze para meter weglaat, wordt de hoofd-SDDL voor de **WinRM** -service gebruikt voor deze configuratie.
Als u de hoofd-SDDL wilt weer geven of wijzigen, gebruikt u de WSMan-provider. Bijvoorbeeld `Get-Item wsman:\localhost\service\rootSDDL`. Typ voor meer informatie over de WSMan-provider `Get-Help wsman` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionTypeOption

Hiermee geeft u typespecifieke opties voor de sessie configuratie op. Voer een object voor sessie type opties in, zoals het **New psworkflowexecutionoption** -object dat door de `New-PSWorkflowExecutionOption` cmdlet wordt geretourneerd.

De opties voor sessies die gebruikmaken van de sessie configuratie, worden bepaald door de waarden van de sessie-opties en de opties voor sessie configuratie. Tenzij opgegeven, hebben opties die in de sessie zijn ingesteld, zoals met behulp van de `New-PSSessionOption` cmdlet, voor rang boven de opties die zijn ingesteld in de sessie configuratie. De waarden van de sessie optie kunnen echter niet groter zijn dan de maximum waarden die zijn ingesteld in de sessie configuratie.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

Hiermee wordt aangegeven dat met deze cmdlet een eigenschappen venster wordt weer gegeven dat u helpt bij het maken van de SDDL voor de sessie configuratie. Het eigenschappen venster wordt weer gegeven nadat u de opdracht hebt ingevoerd `Register-PSSessionConfiguration` en de **WinRM** -service opnieuw hebt gestart.

Wanneer u de machtigingen voor de configuratie instelt, moet u er rekening mee houden dat gebruikers ten minste de machtiging uitvoeren (invoke) moeten hebben om de sessie configuratie in een sessie te kunnen gebruiken.

U kunt de para meter **SecurityDescriptorSDDL** en deze para meter niet gebruiken in dezelfde opdracht.

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

### -StartupScript

Hiermee geeft u het volledig gekwalificeerde pad van een Power shell-script op. Het opgegeven script wordt uitgevoerd in de nieuwe sessie die gebruikmaakt van de sessie configuratie.

U kunt het script gebruiken om de sessie verder te configureren. Als het script een fout genereert, zelfs een niet-afsluit fout, wordt de sessie niet gemaakt en mislukt de `New-PSSession` opdracht.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThreadOptions

Hiermee geeft u op hoe threads worden gemaakt en gebruikt wanneer een opdracht in de sessie wordt uitgevoerd. De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- ReuseThread
- UseCurrentThread
- UseNewThread

De standaard waarde is **UseCurrentThread**.

Zie [PSThreadOptions Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)voor meer informatie.

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransportOption

Hiermee geeft u de transport optie.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

Gebruik slechts één proces om alle sessies te hosten die door dezelfde gebruiker zijn gestart en dezelfde sessie configuratie gebruiken. Standaard wordt elke sessie gehost in een eigen proces.

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

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

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### -ThreadApartmentState

Hiermee geeft u de Apartment-status van de Threading module moet worden gebruikt. Acceptabele waarden zijn:

- Onbekend
- MTA
- Wee

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Micro soft. WSMan. Management. WSManConfigContainerElement

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .

Met deze cmdlet wordt XML gegenereerd die een invoeg toepassings configuratie voor webservices (WS-Management) vertegenwoordigt en wordt de XML naar WS-Management verzonden, waarmee de invoeg toepassing op de lokale computer ( `New-Item wsman:\localhost\plugin` ) wordt geregistreerd.

De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties. Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
