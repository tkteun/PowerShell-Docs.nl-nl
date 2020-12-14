---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: a41c52bf163aa0a73b54e75b5192389a14da82bb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705622"
---
# New-PSSessionConfigurationFile

## SAMENVATTING
Hiermee maakt u een bestand dat een sessie configuratie definieert.

## SYNTAXIS

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## BESCHRIJVING

`New-PSSessionConfigurationFile`Met de cmdlet wordt een bestand met instellingen gemaakt waarmee een sessie configuratie en de omgeving van sessies worden gedefinieerd die worden gemaakt met behulp van de sessie configuratie.
Als u het bestand in een sessie configuratie wilt gebruiken, gebruikt u de para meter **Path** van de `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` cmdlets.

Het bestand met de sessie configuratie dat wordt `New-PSSessionConfigurationFile` gemaakt, is een tekst bestand dat is gelezen met menselijke Lees baarheid dat een hash-tabel van de eigenschappen en waarden van de sessie configuratie bevat. Het bestand heeft de `.pssc` bestands extensie.

Alle para meters van `New-PSSessionConfigurationFile` zijn optioneel, met uitzonde ring van de para meter **Path** .
Als u een para meter weglaat, wordt de bijbehorende sleutel in het sessie configuratie bestand commentaar-out, behalve wanneer vermeld in de parameter beschrijving.

Een sessie configuratie, ook wel een eind punt genoemd, is een verzameling instellingen op de lokale computer die de omgeving definiëren voor Power shell-sessies (**PSSessions**) die verbinding maken met de computer. Alle **PSSessions** gebruiken een sessie configuratie. Als u een bepaalde sessie configuratie wilt opgeven, gebruikt u de para meter **configuratiepad** van cmdlets die een sessie maken, zoals de `New-PSSession` cmdlet.

Met een sessie configuratie bestand kunt u eenvoudig een sessie configuratie definiëren zonder complexe scripts of code-assembly's. De instellingen in het bestand worden gebruikt met het optionele opstart script en alle assembly's in de sessie configuratie.

Zie [about_Session_Configurations](About/about_Session_Configurations.md) en [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuraties en sessie configuratie bestanden.

Deze cmdlet is geïntroduceerd in Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een geen-taal sessie maken en gebruiken

In dit voor beeld ziet u hoe u een sessie zonder taal maakt en hoe u deze kunt gebruiken.

De stappen zijn onder andere:

1. Maak een nieuw configuratie bestand.
1. Registreer de configuratie.
1. Maak een nieuwe sessie die gebruikmaakt van de configuratie.
1. Voer opdrachten in die nieuwe sessie uit.

Als u de opdrachten in dit voor beeld wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren. Deze optie is vereist om de cmdlet uit te voeren `Register-PSSessionConfiguration` .

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

In dit voor beeld `Invoke-Command` mislukt de fout omdat de **LanguageMode** is ingesteld op ' geen **taal**'.

### Voor beeld 2: een RestrictedLanguage-sessie maken en gebruiken

In dit voor beeld ziet u hoe u een sessie zonder taal maakt en hoe u deze kunt gebruiken.

De stappen zijn onder andere:

1. Maak een nieuw configuratie bestand.
1. Registreer de configuratie.
1. Maak een nieuwe sessie die gebruikmaakt van de configuratie.
1. Voer opdrachten in die nieuwe sessie uit.

Als u de opdrachten in dit voor beeld wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren. Deze optie is vereist om de cmdlet uit te voeren `Register-PSSessionConfiguration` .

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

In dit voor beeld `Invoke-Command` is het gelukt omdat de **LanguageMode** is ingesteld op **RestrictedLanguage**.

### Voor beeld 3: een sessie configuratie bestand wijzigen

In dit voor beeld ziet u hoe u het sessie configuratie bestand wijzigt dat wordt gebruikt in een bestaande sessie met de naam ' ITTasks '. Voorheen hadden deze sessies alleen de kern modules en een interne **ITTasks** -module. De beheerder wil de **PSScheduledJob** -module toevoegen aan sessies die zijn gemaakt met behulp van de ITTasks-sessie configuratie.

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

De `New-PSSessionConfigurationFile` cmdlet voor het maken van een sessie configuratie bestand waarmee de vereiste modules worden geïmporteerd. De `Set-PSSessionConfiguration` cmdlet vervangt het huidige configuratie bestand door de nieuwe. Deze nieuwe configuratie is alleen van invloed op nieuwe sessies die zijn gemaakt na de wijziging.
Bestaande ' ITTasks-sessies worden niet beïnvloed.

### Voor beeld 4: een sessie configuratie bestand bewerken

In dit voor beeld ziet u hoe u een sessie configuratie wijzigt door de configuratie kopie van de actieve sessie van het configuratie bestand te bewerken. Als u de sessie configuratie kopie van het configuratie bestand wilt wijzigen, moet u volledige controle over de toegang tot het bestand hebben. Hiervoor moet u mogelijk de machtigingen voor het bestand wijzigen.

In dit scenario willen we een nieuwe alias voor de `Select-String` cmdlet toevoegen door het actieve configuratie bestand te bewerken.

De voorbeeld code hieronder voert de volgende stappen uit om deze wijziging door te voeren:

1. Het pad naar het configuratie bestand voor de ITConfig-sessie ophalen.
1. De gebruiker bewerkt het configuratie bestand met **Notepad.exe** om de waarde **AliasDefinitions** als volgt te wijzigen: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .
1. Het bijgewerkte configuratie bestand testen.

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

Gebruik de para meter **uitgebreid** `Test-PSSessionConfigurationFile` om eventuele fouten weer te geven die zijn gedetecteerd. De cmdlet wordt geretourneerd `$True` als er geen fouten worden gedetecteerd in het bestand.

### Voor beeld 5: een voorbeeld configuratie bestand maken

In dit voor beeld ziet u een `New-PSSessionConfigurationFile` opdracht die gebruikmaakt van alle cmdlet-para meters.
Het is opgenomen om de juiste invoer indeling voor elke para meter weer te geven.

De resulterende SampleFile. pssc wordt weer gegeven in de uitvoer.

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## PARAMETERS

### -AliasDefinitions

Voegt de opgegeven aliassen toe aan sessies die gebruikmaken van de sessie configuratie. Voer een hash-tabel in met de volgende sleutels:

- Naam: naam van de alias. Deze sleutel is vereist.
- Waarde: de opdracht die door de alias wordt vertegenwoordigd. Deze sleutel is vereist.
- Beschrijving: een teken reeks waarmee de alias wordt beschreven. Deze sleutel is optioneel.
- Opties-alias opties. Deze sleutel is optioneel. De standaard waarde is **geen**. De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.

Bijvoorbeeld: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

Hiermee geeft u de assembly's op die moeten worden geladen in de sessies die gebruikmaken van de sessie configuratie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Author

Hiermee geeft u de auteur van de sessie configuratie of het configuratie bestand. Standaard is dit de huidige gebruiker. De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.

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

### -CompanyName

Hiermee geeft u het bedrijf op dat de sessie configuratie of het configuratie bestand heeft gemaakt. De standaard waarde is **onbekend**. De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### -Copyright

Hiermee geeft u een copyright het configuratie bestand voor de sessie. De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.

Als u deze para meter weglaat, `New-PSSessionConfigurationFile` genereert een copyright verklaring met behulp van de waarde van de para meter **Auteur** .

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

### -Beschrijving

Hiermee geeft u een beschrijving van de sessie configuratie of het sessie configuratie bestand op. De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.

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

### -Omgevings variabelen

Hiermee voegt u omgevings variabelen toe aan de sessie. Voer een hash-tabel in waarin de sleutels de namen van omgevings variabelen zijn en de waarden zijn de waarden van omgevings variabelen.

Bijvoorbeeld: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionPolicy

Hiermee geeft u het uitvoerings beleid op van sessies die gebruikmaken van de sessie configuratie. Als u deze para meter weglaat, wordt de waarde van de sleutel **ExecutionPolicy** in het sessie configuratie bestand **beperkt**. Zie [about_Execution_Policies](about/about_Execution_Policies.md)voor meer informatie over uitvoerings beleid in Power shell.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Hiermee geeft u de indelings bestanden (. ps1xml) op die worden uitgevoerd in sessies die gebruikmaken van de sessie configuratie.
De waarde van deze para meter moet een volledig of absoluut pad van de indelings bestanden zijn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Volledig

Geeft aan dat deze bewerking alle mogelijke configuratie-eigenschappen in het sessie configuratie bestand bevat.

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

### -FunctionDefinitions

Voegt de opgegeven functies toe aan sessies die gebruikmaken van de sessie configuratie. Voer een hash-tabel in met de volgende sleutels:

- Naam: naam van de functie. Deze sleutel is vereist.
- Script block-functie hoofd tekst. Voer een script blok in. Deze sleutel is vereist.
- Opties-functie opties. Deze sleutel is optioneel. De standaard waarde is **geen**. De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.

Bijvoorbeeld: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GroupManagedServiceAccount

Hiermee configureert u sessies met behulp van deze sessie configuratie om uit te voeren in de context van het opgegeven beheerde service account van de groep. De computer waarvoor deze sessie configuratie is geregistreerd, moet gemachtigd zijn om het gMSA-wacht woord aan te vragen om de sessies te kunnen maken. Dit veld kan niet worden gebruikt met de para meter **RunAsVirtualAccount** .

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

### -GUID

Hiermee geeft u een unieke id voor het sessie configuratie bestand op. Als u deze para meter weglaat, `New-PSSessionConfigurationFile` genereert een GUID voor het bestand. Als u een nieuwe GUID wilt maken in Power shell, typt u `New-Guid` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LanguageMode

Hiermee wordt bepaald welke elementen van de Power shell-taal zijn toegestaan in sessies die gebruikmaken van deze sessie configuratie. U kunt deze para meter gebruiken om de opdrachten te beperken die bepaalde gebruikers op de computer kunnen uitvoeren.

De aanvaardbare waarden voor deze parameter zijn:

- FullLanguage: alle taal elementen zijn toegestaan.
- ConstrainedLanguage-opdrachten die scripts bevatten die moeten worden geëvalueerd, zijn niet toegestaan. De ConstrainedLanguage-modus beperkt de gebruikers toegang tot Microsoft .NET Framework-typen,-objecten of-methoden.
- Taal: gebruikers kunnen cmdlets en functies uitvoeren, maar mogen geen taal elementen gebruiken, zoals script blokken, variabelen of Opera tors.
- RestrictedLanguage: gebruikers kunnen cmdlets en functies uitvoeren, maar mogen geen script blokken of variabelen gebruiken, met uitzonde ring van de volgende toegestane variabelen: `$PSCulture` , `$PSUICulture` , `$True` , en `$False` `$Null` . Gebruikers kunnen alleen de basis vergelijkings operatoren ( `-eq` , `-gt` ,) gebruiken `-lt` . Toewijzings instructies, verwijzingen naar eigenschappen en methode aanroepen zijn niet toegestaan.

De standaard waarde van de para meter **LanguageMode** is afhankelijk van de waarde van de para meter **SessionType** .

- Lege-de taal
- RestrictedRemoteServer-taal
- Default-FullLanguage

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Hiermee geeft u de modules en modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van de sessie configuratie.

Standaard wordt alleen de module **micro soft. Power shell. core** geïmporteerd in externe sessies, maar tenzij de cmdlets worden uitgesloten, kunnen gebruikers de `Import-Module` cmdlets en gebruiken `Add-PSSnapin` om modules en modules toe te voegen aan de sessie.

Elke module of module in de waarde van deze para meter kan worden vertegenwoordigd door een teken reeks of als een hash-tabel. Een module teken reeks bestaat alleen uit de naam van de module of module. Een module-hash-tabel kan **module**-, **ModuleVersion**-en **GUID** -sleutels bevatten. Alleen de **module** sleutel is vereist.

De volgende waarde bestaat bijvoorbeeld uit een teken reeks en een hash-tabel. Een combi natie van teken reeksen en hash-tabellen, in een wille keurige volg orde, is geldig.

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

De waarde van de para meter **ModulesToImport** van de `Register-PSSessionConfiguration` cmdlet krijgt voor rang op de waarde van de **ModulesToImport** -sleutel in het configuratie bestand voor de sessie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MountUserDrive

Hiermee configureert u sessies die gebruikmaken van deze sessie configuratie om de PSDrive zichtbaar te maken `User:` . Gebruikers stations zijn uniek voor elke gebruiker die verbinding maakt en waarmee gebruikers gegevens kunnen kopiëren van en naar Power shell-eind punten, zelfs als de bestandssysteem provider niet wordt weer gegeven. Roots van het gebruikers station worden gemaakt onder `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` . Voor elke gebruiker die verbinding maakt met het eind punt, wordt een map met de naam gemaakt `$env:USERDOMAIN_$env:USERNAME` .

De inhoud van het gebruikers station blijft achter gebruikers sessies en wordt niet automatisch verwijderd. Standaard kunnen gebruikers alleen de 50 MB van gegevens in het gebruikers station opslaan. Dit kan worden aangepast met de para meter **UserDriveMaximumSize** .

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

Hiermee geeft u het pad en de bestands naam van het sessie configuratie bestand. Het bestand moet een `.pssc` bestandsnaam extensie hebben.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

Hiermee geeft u de versie van de Power shell-engine in sessies die gebruikmaken van de sessie configuratie. De acceptabele waarden voor deze para meter zijn: 2,0 en 3,0. Als u deze para meter weglaat, wordt de **PowerShellVersion** -sleutel commentaar-out en de nieuwste versie van Power shell-uitvoeringen in de sessie.

De waarde van de para meter **PSVersion** van de `Register-PSSessionConfiguration` cmdlet krijgt voor rang op de waarde van de **PowerShellVersion** -sleutel in het configuratie bestand voor de sessie.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredGroups

Hiermee geeft u regels voor voorwaardelijke toegang op voor gebruikers die verbinding maken met sessies die gebruikmaken van deze sessie configuratie.

Voer een hashtabel in om de lijst met regels te maken met slechts één sleutel per hashtabel, ' en ' of ' of ', en stel de waarde in op een matrix met namen van beveiligings groepen of extra hashtabellen.

Voor beeld waarbij gebruikers worden verbonden om lid te zijn van één groep: `@{ And = 'MyRequiredGroup' }`

Voor beeld dat gebruikers moeten deel uitmaken van groep A of beide groepen B en C om toegang te krijgen tot het eind punt: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RoleDefinitions

Hiermee geeft u de toewijzing op tussen beveiligings groepen (of gebruikers) en functie mogelijkheden. Gebruikers krijgen toegang tot alle functie mogelijkheden die van toepassing zijn op hun groepslid maatschap op het moment dat de sessie wordt gemaakt.

Voer een hash-tabel in waarin de sleutels de naam van de beveiligings groep zijn en de waarden zijn hash-tabellen die een lijst met functie mogelijkheden bevatten die beschikbaar moeten worden gemaakt voor de beveiligings groep.

Bijvoorbeeld: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsVirtualAccount

Hiermee configureert u sessies met behulp van deze sessie configuratie om te worden uitgevoerd als het virtuele beheerders account van de computer. Dit veld kan niet worden gebruikt met de para meter **GroupManagedServiceAccount** .

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

### -RunAsVirtualAccountGroups

Hiermee geeft u de beveiligings groepen op die moeten worden gekoppeld aan het virtuele account wanneer een sessie die gebruikmaakt van de sessie configuratie, als een virtueel account wordt uitgevoerd. Als u dit weglaat, behoort het virtuele account bij domein Administrators op domein controllers en beheerders op alle andere computers.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SchemaVersion

Hiermee geeft u de versie van het schema van het configuratie bestand voor de sessie. De standaard waarde is "1.0.0.0".

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Voegt de opgegeven scripts toe aan sessies die gebruikmaken van de sessie configuratie. Geef het pad en de bestands namen van de scripts op. De waarde van deze para meter moet een volledig of absoluut pad van script bestandsnamen zijn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionType

Hiermee geeft u het type sessie op dat wordt gemaakt met behulp van de sessie configuratie. De standaard waarde is standaard. De aanvaardbare waarden voor deze parameter zijn:

- Leeg: er worden standaard geen modules aan de sessie toegevoegd. Gebruik de para meters van deze cmdlet om modules, functies, scripts en andere functies aan de sessie toe te voegen. Deze optie is bedoeld om aangepaste sessies te maken door geselecteerde opdrachten toe te voegen. Als u geen opdrachten toevoegt aan een lege sessie, is de sessie beperkt tot expressies en is deze mogelijk niet bruikbaar.
- Default-de module micro soft. Power shell. core wordt toegevoegd aan de sessie. Deze module bevat de `Import-Module` cmdlet die gebruikers kunnen gebruiken om andere modules te importeren, tenzij u deze cmdlet expliciet niet toestaat.
- RestrictedRemoteServer. Bevat alleen de volgende proxy functies: `Exit-PSSession` , `Get-Command` , `Get-FormatData` , `Get-Help` ,, en `Measure-Object` `Out-Default` `Select-Object` .
  Gebruik de para meters van deze cmdlet om modules, functies, scripts en andere functies aan de sessie toe te voegen.

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TranscriptDirectory

Hiermee geeft u de map voor het plaatsen van sessie transcripten voor sessies met behulp van deze sessie configuratie.

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

### -TypesToProcess

Voegt de opgegeven `.ps1xml` type bestanden toe aan sessies die gebruikmaken van de sessie configuratie. Voer de bestands namen van het type in. De waarde van deze para meter moet een volledig of absoluut pad zijn om bestands namen te kunnen typen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserDriveMaximumSize

Hiermee geeft u de maximale grootte op voor gebruikers stations die worden weer gegeven in sessies die gebruikmaken van deze sessie configuratie.
Als u dit weglaat, is de standaard grootte van elke hoofdmap van het `User:` station 50 MB.

Deze para meter moet worden gebruikt met **MountUserDrive**.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

Voegt de opgegeven variabelen toe aan sessies die gebruikmaken van de sessie configuratie. Voer een hash-tabel in met de volgende sleutels:

- Naam: naam van de variabele. Deze sleutel is vereist.
- Waarde variabele. Deze sleutel is vereist.
- Opties: variabele opties. Deze sleutel is optioneel. De standaard waarde is **geen**. De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.

Bijvoorbeeld: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

Hiermee worden de aliassen in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter, plus alle aliassen die u definieert in de para meter **AliasDefinition** . Joker tekens worden ondersteund. Standaard worden alle aliassen die zijn gedefinieerd door de Power shell-engine en alle aliassen die modules exporteren, weer gegeven in de sessie.

Bijvoorbeeld: `VisibleAliases='gcm', 'gp'`

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias uit de sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleCmdlets

Hiermee worden de cmdlets in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter. Joker tekens en modules met gekwalificeerde namen worden ondersteund.

Standaard worden alle cmdlets die modules in de sessie exporteren, weer gegeven in de sessie. Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd. Als er geen modules in **ModulesToImport** de cmdlet beschikbaar maken, probeert de juiste module automatisch te laden.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias uit de sessie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleExternalCommands

Hiermee beperkt u de externe binaire bestanden, scripts en opdrachten die in de sessie kunnen worden uitgevoerd en die zijn opgegeven in de waarde van deze para meter. Joker tekens worden ondersteund.

Standaard zijn er geen externe opdrachten zichtbaar in de sessie.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias van de sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleFunctions

Hiermee beperkt u de functies in de sessie die zijn opgegeven in de waarde van deze para meter, plus de functies die u definieert in de para meter **FunctionDefinition** . Joker tekens worden ondersteund.

Standaard zijn alle functies die modules in de sessie exporteren, weer gegeven in de sessie. Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias uit de sessie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

Hiermee worden de Power shell-providers in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.
Joker tekens worden ondersteund.

Standaard worden alle providers die modules in de sessie exporteren, weer gegeven in de sessie. Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

- In para meters, zoals **VisibleCmdlets** en **VisibleProviders**, worden geen items geïmporteerd in de sessie. In plaats daarvan selecteren ze uit de items die in de sessie worden geïmporteerd. Als de waarde van de para meter **VisibleProviders** bijvoorbeeld de certificaat provider is, maar de **ModulesToImport** -para meter geeft geen **micro soft. Power shell. Security** -module op die de certificaat provider bevat, is de certificaat provider niet zichtbaar in de sessie.
- `New-PSSessionConfigurationFile` Hiermee maakt u een sessie configuratie bestand met de bestandsnaam extensie. pssc in het pad dat u opgeeft in de para meter **Path** . Wanneer u het sessie configuratie bestand gebruikt om een sessie configuratie te maken, `Register-PSSessionConfiguration` kopieert de cmdlet het configuratie bestand en slaat het een actieve kopie van het bestand op in de **SessionConfig** -submap van de `$PSHOME` map.

  De eigenschap **ConfigFilePath** van de sessie configuratie bevat het volledig gekwalificeerde pad van het configuratie bestand van de actieve sessie. U kunt het actieve configuratie bestand `$PSHOME` op elk gewenst moment in de Directory wijzigen met behulp van een tekst editor. De wijzigingen die u aanbrengt, zijn van invloed op alle nieuwe sessies die gebruikmaken van de sessie configuratie, maar niet op bestaande sessies.

  Voordat u een bewerkte sessie configuratie bestand gebruikt, gebruikt `Test-PSSessionConfigurationFile` u de cmdlet om te controleren of de vermeldingen van het configuratie bestand geldig zijn.

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
