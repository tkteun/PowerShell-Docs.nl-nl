---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: c1d0d0bc2452e7f05fd47574dedeb4a1b9686fad
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251599"
---
# Set-PSSessionConfiguration

## SAMENVATTING
Hiermee wijzigt u de eigenschappen van een geregistreerde sessie configuratie.

## SYNTAXIS

### NameParameterSet (standaard)

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Set-PSSessionConfiguration` cmdlet wijzigt de eigenschappen van de sessie configuraties op de lokale computer.

Gebruik de para meter **name** om de sessie configuratie te identificeren die u wilt wijzigen. Gebruik de andere para meters om nieuwe waarden op te geven voor de eigenschappen van de sessie configuratie. Als u een eigenschaps waarde uit de configuratie wilt verwijderen en de standaard waarde wilt gebruiken, voert u een lege teken reeks ("") of een waarde van `$Null` voor de bijbehorende para meter in.

Vanaf Power Shell 3,0 kunt u een configuratie bestand voor de sessie gebruiken om een sessie configuratie te definiëren. Deze functie biedt een eenvoudige en Detecteer bare methode voor het instellen en wijzigen van de eigenschappen van sessies die gebruikmaken van de sessie configuratie. Als u een sessie configuratie bestand wilt opgeven, gebruikt u de para meter **Path** van `Set-PSSessionConfiguration` . Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.
Voor informatie over het maken en wijzigen van een sessie configuratie bestand, raadpleegt u de `New-PSSessionConfigurationFile` cmdlet.

Met sessie configuraties wordt de omgeving van externe sessies ( **PSSessions** ) gedefinieerd die verbinding maken met de lokale computer. Elke **PSSession** maakt gebruik van een sessie configuratie. De sessie configuratie bepaalt de functies van de **PSSession** , zoals de modules die beschikbaar zijn in de sessie, de cmdlets die mogen worden uitgevoerd, de taal modus, quota en time-outs. De security descriptor van de sessie configuratie bepaalt wie de sessie configuratie kan gebruiken om verbinding te maken met de lokale computer. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

Als u de eigenschappen van een sessie configuratie wilt bekijken, gebruikt u de `Get-PSSessionConfiguration` cmdlet of de WSMan-provider. Typ voor meer informatie over de WSMan-provider `Get-Help WSMan` .

## VOORBEELDEN

### Voor beeld 1: een sessie configuratie maken en wijzigen

In dit voor beeld ziet u hoe u een opstart script kunt toevoegen aan en verwijderen uit een configuratie.

Met de eerste opdracht wordt de **AdminShell** -configuratie gemaakt. Met de tweede opdracht wordt het `AdminConfig.ps1` script aan de configuratie toegevoegd. De wijziging is van kracht wanneer u **WinRM** opnieuw opstart.
Met de derde opdracht wordt het `AdminConfig.ps1` script uit de configuratie verwijderd.

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### Voor beeld 2: resultaten weer geven

In dit voor beeld wordt de waarde van de eigenschap **MaximumReceivedObjectSizeMB** verhoogd naar 20. Met deze opdracht wordt ook gevraagd de **WinRM** -service opnieuw te starten. De wijziging is pas van kracht nadat de **WinRM** -service opnieuw is opgestart.

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### Voor beeld 3: resultaten op verschillende manieren weer geven

In dit voor beeld wordt `Set-PSSessionConfiguration` het opstart script in de **MaintenanceShell** -sessie configuratie gewijzigd in `Maintenance.ps1` . In de uitvoer ziet u de wijziging en wordt u gevraagd de **WinRM** -service opnieuw te starten. De reactie is ' y ' (Ja).

`Get-PSSessionConfiguration` Hiermee wordt de **MaintenanceShell** -sessie configuratie opgehaald. De pijplijn operator (|) verzendt de resultaten van de opdracht naar `Format-List` , waarin alle eigenschappen van het configuratie object in een lijst worden weer gegeven. Vervolgens worden de initialisatie parameters voor de **MaintenanceShell** -configuratie weer gegeven met behulp van de WSMan-provider. `Get-ChildItem` (alias `dir` ) Hiermee worden de onderliggende items in het **InitializationParameters** -knoop punt voor de **MaintenanceShell** -invoeg toepassing opgehaald. Typ voor meer informatie over de WSMan-provider `Get-Help wsman` .

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## PARAMETERS

### -AccessMode

Hiermee wordt de sessie configuratie in-en uitgeschakeld en wordt bepaald of deze kan worden gebruikt voor externe of lokale sessies op de computer. De aanvaardbare waarden voor deze parameter zijn:

- Uitgeschakeld. Hiermee schakelt u de sessie configuratie uit. Het kan niet worden gebruikt voor externe of lokale toegang tot de computer. Met deze waarde wordt de eigenschap **enabled** van de sessie configuratie ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` ) ingesteld op **False**.
- Lokale. Hiermee voegt u een **Network_Deny_All** vermelding toe aan security descriptor van de sessie configuratie.
  Gebruikers van de lokale computer kunnen de sessie configuratie gebruiken om een lokale loop back-sessie op dezelfde computer te maken, maar externe gebruikers krijgen geen toegang.
- Beveiligingslek. Hiermee verwijdert u **Deny_All** en **Network_Deny_All** vermeldingen uit de security descriptors van de sessie configuratie. Gebruikers van lokale en externe computers kunnen de sessie configuratie gebruiken om sessies te maken en opdrachten uit te voeren op deze computer.

De standaard waarde is **extern**.

Andere cmdlets kunnen de waarde van deze para meter later overschrijven. Met de cmdlet worden bijvoorbeeld `Enable-PSRemoting` alle sessie configuraties op de computer ingeschakeld en externe toegang tot deze computers toegestaan. met de `Disable-PSRemoting` cmdlet wordt alleen lokale toegang tot alle sessie configuraties op de computer toegestaan.

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

Hiermee geeft u het pad op van het assembly bestand ( \* . dll) dat is opgegeven in de waarde van de para meter **assemblyname** .

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

Hiermee geeft u de naam van de assembly. Met deze cmdlet maakt u een sessie configuratie op basis van een klasse die is gedefinieerd in een assembly.

Voer de bestands naam of het volledige pad van een assembly. dll-bestand in dat een sessie configuratie definieert. Als u alleen de bestands naam opgeeft, kunt u het pad opgeven in de waarde van de para meter **Application base** .

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

Hiermee geeft u het type sessie configuratie op dat in de assembly in de para meter **assemblyname** is gedefinieerd. Voor het type dat u opgeeft, moet de klasse **System. Management. Automation. Remoting. PSSessionConfiguration** worden geïmplementeerd.

Deze para meter is vereist wanneer u de naam van een assembly opgeeft.

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

Onderdrukt alle gebruikers prompts en start de **WinRM** -service opnieuw op zonder toestemming te vragen. Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.

Als u het opnieuw opstarten wilt voor komen en de prompt voor opnieuw opstarten wilt onderdrukken, gebruikt u de para meter **NoServiceRestart** .

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

Hiermee geeft u de limiet op voor de hoeveelheid gegevens die naar deze computer kan worden verzonden in één externe opdracht. Voer de gegevens grootte in mega bytes (MB) in. De standaard waarde is 50 MB.

Als er een limiet voor gegevens grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt. De waarde van deze para meter wordt genegeerd.

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

Hiermee geeft u de limieten op voor de hoeveelheid gegevens die in een enkel object naar deze computer kan worden verzonden.
Voer de gegevens grootte in mega bytes in. De standaard waarde is 10 MB.

Als een limiet voor object grootte is gedefinieerd in het configuratie type dat is opgegeven in de para meter **ConfigurationTypeName** , wordt de limiet in het configuratie type gebruikt. De waarde van deze para meter wordt genegeerd.

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

### -ModulesToImport

Hiermee geeft u de modules en modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van de sessie configuratie. Voer de naam van de module en module in.

Standaard wordt alleen de module **micro soft. Power shell. core** geïmporteerd in sessies, maar tenzij de cmdlets worden uitgesloten, kunt u de `Import-Module` cmdlets en Add-PSSnapin gebruiken om modules en modules toe te voegen aan de sessie.

De modules die zijn opgegeven in deze parameter waarde worden geïmporteerd in toevoegingen aan modules die zijn opgegeven in het sessie configuratie bestand ( `New-PSSessionConfigurationFile` ). Instellingen in het bestand met de sessie configuratie kunnen echter de opdrachten die door modules worden geëxporteerd, verbergen of voor komen dat gebruikers ze gebruiken.

De modules die zijn opgegeven in deze parameter waarde, vervangen de lijst met modules die zijn opgegeven met behulp van de para meter **ModulesToImport** van de `Register-PSSessionConfiguration` cmdlet.

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

Hiermee geeft u de naam van de sessie configuratie op die u wilt wijzigen.

U kunt deze para meter niet gebruiken om de naam van de sessie configuratie te wijzigen.

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

Wanneer u uitvoert `Set-PSSessionConfiguration` , wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de nieuwe sessie configuratie effectief te maken. Totdat de **WinRM** -service opnieuw is gestart, is de nieuwe sessie configuratie niet effectief.

Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, gebruikt u de para meter **Force** . Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .

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

Hiermee geeft u het pad van een sessie configuratie bestand (. pssc), zoals een door de `New-PSSessionConfigurationFile` cmdlet gemaakt. Als u het pad weglaat, de standaard instelling is de huidige map.

Zie het Help-onderwerp voor de cmdlet voor meer informatie over het wijzigen van een configuratie bestand voor een sessie `New-PSSessionConfigurationFile` .

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

Hiermee geeft u een andere SDDL-teken reeks (Security Descriptor Definition Language) op voor de configuratie.

Deze teken reeks bepaalt de machtigingen die nodig zijn voor het gebruik van de nieuwe sessie configuratie. Als u een sessie configuratie wilt gebruiken in een sessie, moeten gebruikers ten minste een machtiging voor uitvoeren (invoke) voor de configuratie hebben.

Als u de standaard security descriptor voor de configuratie wilt gebruiken, voert u een lege teken reeks ("") of een waarde van in `$Null` . De standaard waarde is de hoofd-SDDL in het WSMan:-station.

Als de security descriptor complex is, kunt u overwegen de para meter **ShowSecurityDescriptorUI** te gebruiken in plaats van deze. U kunt niet beide para meters in dezelfde opdracht gebruiken.

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

Hiermee wordt aangegeven dat deze cmdlet een eigenschappen venster is waarmee u een nieuwe SDDL voor de sessie configuratie kunt maken. Het eigenschappen venster wordt weer gegeven nadat u de opdracht hebt uitgevoerd `Set-PSSessionConfiguration` en de **WinRM** -service opnieuw hebt gestart.

Wanneer u machtigingen instelt voor de configuratie, moet u er rekening mee houden dat gebruikers ten minste de machtiging voor uitvoeren (invoke) moeten hebben om de sessie configuratie in een sessie te kunnen gebruiken.

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

Hiermee geeft u het opstart script voor de configuratie. Geef het volledig gekwalificeerde pad van een Power shell-script op. Het opgegeven script wordt uitgevoerd in de nieuwe sessie die gebruikmaakt van de sessie configuratie.

Als u een opstart script uit een sessie configuratie wilt verwijderen, voert u een lege teken reeks ("") of een waarde van in `$Null` .

U kunt een opstart script gebruiken om de gebruikers sessie verder te configureren. Als het script een fout genereert, zelfs een niet-afsluit fout, wordt de sessie niet gemaakt en mislukt de `New-PSSession` opdracht.

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

Hiermee geeft u de instelling thread opties in de configuratie. Deze instelling bepaalt hoe threads worden gemaakt en gebruikt wanneer een opdracht in de sessie wordt uitgevoerd. De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- ReuseThread
- UseCurrentThread
- UseNewThread

De standaard waarde is **UseCurrentThread**.

Zie [PSThreadOptions Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.psthreadoptions)voor meer informatie.

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

Hiermee geeft u de transport opties voor de sessie configuratie. Voer een transport opties-object in, zoals het **WSManConfigurationOption** -object dat de `New-PSTransportOption` cmdlet retourneert.

De opties voor sessies die gebruikmaken van de sessie configuratie, worden bepaald door de waarden van de sessie-opties en de opties voor sessie configuratie. Tenzij opgegeven, hebben opties die in de sessie zijn ingesteld, zoals met behulp van de `New-PSSessionOption` cmdlet, voor rang boven de opties die zijn ingesteld in de sessie configuratie. De waarden van de sessie optie kunnen echter niet groter zijn dan de maximum waarden die zijn ingesteld in de sessie configuratie.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

### Micro soft. WSMan. Management. WSManConfigLeafElement

## OPMERKINGEN

Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren.

De `Set-PSSessionConfiguration` cmdlet heeft geen invloed op de configuratie naam en de **WSMan** -provider biedt geen ondersteuning voor de `Rename-Item` cmdlet. Als u de naam van een sessie configuratie wilt wijzigen, gebruikt u de `Unregister-PSSessionConfiguration` cmdlet om de configuratie te verwijderen en gebruikt u vervolgens de `Register-PSSessionConfiguration` cmdlet om een nieuwe sessie configuratie te maken en te registreren.

U kunt de `Set-PSSessionConfiguration` cmdlet gebruiken om de standaard sessie configuraties van micro soft. Power shell en micro soft. PowerShell32 te wijzigen. Ze zijn niet beveiligd. Als u wilt terugkeren naar de oorspronkelijke versie van een standaard sessie configuratie, gebruikt u de `Unregister-PSSessionConfiguration` cmdlet om de standaard sessie configuratie te verwijderen en gebruikt u vervolgens de `Enable-PSRemoting` cmdlet om deze te herstellen.

De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties. Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.

U kunt opdrachten in WSMan: drive gebruiken om de eigenschappen van sessie configuraties te wijzigen.
U kunt echter niet het WSMan:-station in Power Shell 2,0 gebruiken om de eigenschappen van de sessie configuratie te wijzigen die zijn geïntroduceerd in Power Shell 3,0, zoals **OutputBufferingMode**. Windows Power Shell 2,0-opdrachten genereren geen fout, maar zijn niet effectief. Als u eigenschappen wilt wijzigen die zijn geïntroduceerd in Power Shell 3,0, gebruikt u het station WSMan: in Power Shell 3,0.

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
