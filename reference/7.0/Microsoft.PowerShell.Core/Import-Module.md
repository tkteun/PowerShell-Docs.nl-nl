---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: efb82cb938f7b044b863a8192f4c66673d47a4e0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249777"
---
# Import-Module

## SAMENVATTING
Hiermee voegt u modules toe aan de huidige sessie.

## SYNTAXIS

### Naam (standaard)

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### PSSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### CimSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### UseWindowsPowerShell

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### FullyQualifiedName

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### FullyQualifiedNameAndPSSession

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### FullyQualifiedNameAndUseWindowsPowerShell

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### Assembly

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### ModuleInfo

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## BESCHRIJVING

De `Import-Module` cmdlet voegt een of meer modules toe aan de huidige sessie. Vanaf Power Shell 3,0 worden geïnstalleerde modules automatisch geïmporteerd in de sessie wanneer u opdrachten of providers in de module gebruikt. U kunt echter nog steeds de `Import-Module` opdracht gebruiken om een module te importeren.
U kunt het automatisch importeren van modules uitschakelen met behulp van de `$PSModuleAutoloadingPreference` Voorkeurs variabele. Zie about_Preference_Variables voor meer informatie over de `$PSModuleAutoloadingPreference` variabele [about_Preference_Variables](About/about_Preference_Variables.md).

Een module is een pakket dat leden bevat die kunnen worden gebruikt in Power shell. Leden zijn onder andere cmdlets, providers, scripts, functies, variabelen en andere hulpprogram ma's en bestanden. Nadat een module is geïmporteerd, kunt u de module leden in uw sessie gebruiken. Zie [about_Modules](About/about_Modules.md)voor meer informatie over modules.

Standaard worden `Import-Module` alle leden geïmporteerd die de module exporteert, maar u kunt de para meters **alias** , **Function** , **cmdlet** en **Variable** gebruiken om te beperken welke leden worden geïmporteerd. Met de para meter **NoClobber** wordt voor komen dat `Import-Module` leden met dezelfde namen als leden in de huidige sessie worden geïmporteerd.

`Import-Module` Hiermee wordt een module alleen in de huidige sessie geïmporteerd. Als u de module wilt importeren in elke nieuwe sessie, voegt `Import-Module` u een opdracht toe aan uw Power shell-profiel. Zie [about_Profiles](About/about_Profiles.md)voor meer informatie over profielen.

U kunt externe Windows-computers waarvoor Power shell Remoting is ingeschakeld, beheren door een **PSSession** te maken op de externe computer. Gebruik vervolgens de para meter **PSSession** van `Import-Module` om de modules te importeren die zijn geïnstalleerd op de externe computer. U kunt nu de geïmporteerde opdrachten in de huidige sessie gebruiken. De opdrachten worden impliciet uitgevoerd op de externe computer.

Vanaf Windows Power Shell 3,0 kunt u gebruiken `Import-Module` om Common Information Model-modules (CIM) te importeren waarin de cmdlets worden gedefinieerd in de cmdlet definition XML-bestanden (CDXML). Met deze functie kunt u cmdlets gebruiken die zijn geïmplementeerd in niet-beheerde code-assembly's, zoals die zijn geschreven in C++.

Voor externe computers waarvoor geen externe communicatie van Power shell is ingeschakeld, met inbegrip van computers waarop het Windows-besturings systeem niet wordt uitgevoerd, kunt u de para meter **CIMSession** van gebruiken `Import-Module` voor het importeren van CIM-modules van de externe computer. De geïmporteerde opdrachten worden impliciet uitgevoerd op de externe computer. Een **CIMSession** is een verbinding met Windows Management INSTRUMENTATION (WMI) op de externe computer.

## VOORBEELDEN

### Voor beeld 1: de leden van een module importeren in de huidige sessie

In dit voor beeld worden de leden van de module **PSDiagnostics** in de huidige sessie geïmporteerd.

```powershell
Import-Module -Name PSDiagnostics
```

### Voor beeld 2: alle modules importeren die zijn opgegeven in het pad naar de module

In dit voor beeld worden alle beschik bare modules in het pad dat door de `$env:PSModulePath` omgevings variabele is opgegeven, in de huidige sessie geïmporteerd.

```powershell
Get-Module -ListAvailable | Import-Module
```

### Voor beeld 3: de leden van verschillende modules importeren in de huidige sessie

In dit voor beeld worden de leden van de **PSDiagnostics** -en **DISM** -modules in de huidige sessie geïmporteerd.

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

De `Get-Module` cmdlet haalt de **PSDiagnostics** -en **DISM** -modules op en slaat de objecten op in de `$m` variabele. De para meter **ListAvailable** is vereist als u modules gaat ophalen die nog niet in de sessie zijn geïmporteerd.

De para meter **ModuleInfo** van `Import-Module` wordt gebruikt voor het importeren van de modules in de huidige sessie.

### Voor beeld 4: alle modules importeren die zijn opgegeven met een pad

In dit voor beeld wordt een expliciet pad gebruikt om te bepalen welke module moet worden geïmporteerd.

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

Het gebruik van de **uitgebreide** para meter zorgt ervoor dat `Import-Module` de voortgang wordt gerapporteerd bij het laden van de module.
Zonder de para meter **uitgebreid** , **PassThru** of **AsCustomObject** wordt geen `Import-Module` uitvoer gegenereerd wanneer een module wordt geïmporteerd.

### Voor beeld 5: module leden beperken die in een sessie zijn geïmporteerd

In dit voor beeld ziet u hoe u kunt beperken welke module leden in de sessie worden geïmporteerd en wat het effect van deze opdracht voor de sessie is. De **functie** parameter beperkt de leden die worden geïmporteerd uit de module. U kunt ook de para meters **alias** , **variabele** en **cmdlet** gebruiken om andere leden te beperken die door de module worden geïmporteerd.

De `Get-Module` cmdlet haalt het object op dat de module **PSDiagnostics** vertegenwoordigt. De eigenschap **ExportedCmdlets** geeft een lijst van alle cmdlets die de module exporteert, ook al zijn ze niet allemaal geïmporteerd.

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

Met de **module** para meter van de `Get-Command` cmdlet worden de opdrachten weer gegeven die zijn geïmporteerd uit de **PSDiagnostics** -module. De resultaten bevestigen dat alleen de `Disable-PSTrace` `Enable-PSTrace` cmdlets en zijn geïmporteerd.

### Voor beeld 6: de leden van een module importeren en een voor voegsel toevoegen

In dit voor beeld wordt de module **PSDiagnostics** in de huidige sessie geïmporteerd, wordt een voor voegsel toegevoegd aan de lidnamen en worden vervolgens de namen van de voor voegsels weer gegeven. De **voor voegsel** -para meter van `Import-Module` voegt het **x** -voor voegsel toe aan alle leden die worden geïmporteerd uit de module. Het voor voegsel is alleen van toepassing op de leden van de huidige sessie. De module wordt niet gewijzigd. De para meter **PassThru** retourneert een module-object dat de geïmporteerde module vertegenwoordigt.

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

`Get-Command` Hiermee worden de leden opgehaald die zijn geïmporteerd uit de module. In de uitvoer ziet u dat de module leden correct zijn voor speld.

### Voor beeld 7: een aangepast object ophalen en gebruiken

In dit voor beeld ziet u hoe u het aangepaste object dat wordt geretourneerd door **import-module** kunt ophalen en gebruiken.

Aangepaste objecten bevatten synthetische leden die elk van de geïmporteerde module leden vertegenwoordigen. De cmdlets en functies in een module worden bijvoorbeeld geconverteerd naar script methoden van het aangepaste object.

Aangepaste objecten zijn handig voor het uitvoeren van scripts. Ze zijn ook handig wanneer verschillende geïmporteerde objecten dezelfde namen hebben. Het gebruik van de script methode van een object is gelijk aan het opgeven van de volledig gekwalificeerde naam van een geïmporteerd lid, inclusief de module naam.

De para meter **AsCustomObject** kan alleen worden gebruikt bij het importeren van een script module. Gebruiken `Get-Module` om te bepalen welke van de beschik bare modules een script module is.

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

De script module **show-calendar** wordt geïmporteerd met de para meter **AsCustomObject** voor het aanvragen van een aangepast object en de para meter **PassThru** om het object te retour neren. Het resulterende aangepaste object wordt opgeslagen in de `$a` variabele.

De `$a` variabele wordt naar de cmdlet gepiped `Get-Member` om de eigenschappen en methoden van het opgeslagen object weer te geven. In de uitvoer ziet u een script methode voor het **weer geven** van een agenda.

Als u de script methode voor het **weer geven** van de agenda wilt aanroepen, moet de naam van de methode tussen aanhalings tekens worden geplaatst, omdat de naam een koppel teken bevat.

### Voor beeld 8: een module opnieuw importeren in dezelfde sessie

In dit voor beeld ziet u hoe u de **Force** -para meter van gebruikt `Import-Module` Wanneer u een module opnieuw importeert in dezelfde sessie. Met de para meter **Force** wordt de geladen module verwijderd en vervolgens opnieuw geïmporteerd.

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

Met de eerste opdracht wordt de **PSDiagnostics** -module geïmporteerd. Met de tweede opdracht wordt de module opnieuw geïmporteerd. deze keer gebruikt u de para meter **prefix** .

Zonder de para meter **Force** bevat de sessie twee exemplaren van elke **PSDiagnostics** -cmdlet, een met de standaard naam en één met de naam van de voor voegsel.

### Voor beeld 9: opdrachten uitvoeren die zijn verborgen door geïmporteerde opdrachten

In dit voor beeld ziet u hoe u opdrachten kunt uitvoeren die zijn verborgen door geïmporteerde opdrachten. De **TestModule** -module bevat een functie `Get-Date` met de naam die het jaar en de dag van het jaar retourneert.

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

De eerste `Get-Date` cmdlet retourneert een **DateTime** -object met de huidige datum. Na het importeren van de **TestModule** -module `Get-Date` retourneert het jaar en de dag van het jaar.

De para meter **all** gebruiken om `Get-Command` alle `Get-Date` opdrachten in de sessie weer te geven. In de resultaten ziet u dat er twee `Get-Date` opdrachten in de sessie zijn, een functie uit de **TestModule** -module en een cmdlet uit de module **micro soft. Power shell. Utility** .

Omdat functies voor rang hebben boven cmdlets, `Get-Date` wordt de functie van de **TestModule** -module uitgevoerd in plaats van de `Get-Date` cmdlet. Als u de oorspronkelijke versie van wilt uitvoeren `Get-Date` , moet u de naam van de opdracht kwalificeren met de module naam.

Zie [about_Command_Precedence](about/about_Command_Precedence.md)voor meer informatie over de prioriteit van opdrachten in Power shell.

### Voor beeld 10: een minimum versie van een module importeren

In dit voor beeld wordt de module **PowerShellGet** geïmporteerd. Hierbij wordt de para meter **MinimumVersion** van gebruikt `Import-Module` voor het importeren van alleen versie 2.0.0 of hoger van de module.

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

U kunt ook de para meter **RequiredVersion** gebruiken om een bepaalde versie van een module te importeren, of gebruik de **module** -en **versie** parameters van het `#Requires` tref woord om een bepaalde versie van een module in een script te vereisen.

### Voor beeld 11: importeren met een volledig gekwalificeerde naam

In dit voor beeld wordt een specifieke versie van een module geïmporteerd met behulp van de FullyQualifiedName.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### Voor beeld 12: importeren met een volledig gekwalificeerd pad

In dit voor beeld wordt een specifieke versie van een module met het volledig gekwalificeerde pad geïmporteerd.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### Voor beeld 13: een module van een externe computer importeren

In dit voor beeld ziet u hoe u de- `Import-Module` cmdlet gebruikt om een module te importeren vanaf een externe computer.
Met deze opdracht wordt de impliciete externe functie van Power shell gebruikt.

Wanneer u modules uit een andere sessie importeert, kunt u de cmdlets in de huidige sessie gebruiken.
Opdrachten die gebruikmaken van de cmdlets worden echter uitgevoerd in de externe sessie.

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

`New-PSSession` Hiermee maakt u een externe sessie ( **PSSession** ) op de Server01-computer. De **PSSession** wordt opgeslagen in de `$s` variabele.

Met `Get-Module` de para meter **PSSession** wordt aangegeven dat de module **netsecurity** is geïnstalleerd en beschikbaar is op de externe computer. Deze opdracht is gelijk aan het gebruik `Invoke-Command` van de cmdlet om de `Get-Module` opdracht uit te voeren in de externe sessie. Bijvoorbeeld: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`

Met `Import-Module` de para meter **PSSession** wordt de module **netsecurity** van de externe computer in de huidige sessie geïmporteerd. De `Get-Command` cmdlet wordt gebruikt om opdrachten op te halen die beginnen met de **firewall** **Get** en include in de module **netsecurity** . De uitvoer bevestigt dat de module en de bijbehorende cmdlets zijn geïmporteerd in de huidige sessie.

Vervolgens haalt de `Get-NetFirewallRule` cmdlet Windows Remote Management firewall-regels op de Server01-computer op. Dit komt overeen met het gebruik `Invoke-Command` van de cmdlet om uit te voeren `Get-NetFirewallRule` op de externe sessie.

### Voor beeld 14: opslag beheren op een externe computer zonder het Windows-besturings systeem

In dit voor beeld heeft de beheerder van de computer de WMI-provider voor module detectie geïnstalleerd, waarmee u CIM-opdrachten kunt gebruiken die zijn ontworpen voor de provider.

`New-CimSession`Met de cmdlet wordt een sessie gemaakt op de externe computer met de naam RSDGF03. De sessie maakt verbinding met de WMI-service op de externe computer. De CIM-sessie wordt opgeslagen in de `$cs` variabele.
`Import-Module` maakt gebruik van de **CimSession** in `$cs` om de CIM- **opslag** module te importeren van de RSDGF03-computer.

De `Get-Command` cmdlet toont de `Get-Disk` opdracht in de module **opslag** . Wanneer u een CIM-module in de lokale sessie importeert, zet Power shell de CDXML-bestanden voor elke opdracht om in Power shell-scripts, die als functies in de lokale sessie worden weer gegeven.

Hoewel `Get-Disk` in de lokale sessie wordt getypt, wordt de cmdlet impliciet uitgevoerd op de externe computer van waaruit deze is geïmporteerd. De opdracht retourneert objecten van de externe computer naar de lokale sessie.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## PARAMETERS

### -Alias

Hiermee geeft u de aliassen op die met deze cmdlet worden geïmporteerd van de module in de huidige sessie. Voer een door komma's gescheiden lijst met aliassen in. Joker tekens zijn toegestaan.

Sommige modules exporteren automatisch geselecteerde aliassen in uw sessie wanneer u de module importeert.
Met deze para meter kunt u uit de geëxporteerde aliassen selecteren.

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

### -Argument List

Hiermee wordt een matrix met argumenten, of parameter waarden, opgegeven die worden door gegeven aan een script module tijdens de `Import-Module` opdracht. Deze para meter is alleen geldig wanneer u een script module importeert.

U kunt ook naar de para meter **argument List** verwijzen met behulp van de alias, **args**. Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

Hiermee wordt aangegeven dat met deze cmdlet een aangepast object wordt geretourneerd met leden die de geïmporteerde module leden vertegenwoordigen. Deze para meter is alleen geldig voor script modules.

Wanneer u de para meter **AsCustomObject** gebruikt, worden `Import-Module` de module leden in de sessie geïmporteerd en wordt vervolgens een **PSCustomObject** -object geretourneerd in plaats van een **PSModuleInfo** -object. U kunt het aangepaste object opslaan in een variabele en de punt notatie gebruiken om de leden aan te roepen.

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

### -Assembly

Hiermee wordt een matrix van assembly-objecten opgegeven. Met deze cmdlet worden de cmdlets en providers geïmporteerd die in de opgegeven assembly-objecten zijn geïmplementeerd. Voer een variabele in die assembly-objecten of een opdracht voor het maken van assembly-objecten bevat. U kunt ook een assembly-object pipeen naar `Import-Module` .

Wanneer u deze para meter gebruikt, worden alleen de cmdlets en providers geïmporteerd die door de opgegeven assembly's worden geïmplementeerd. Als de module andere bestanden bevat, worden deze niet geïmporteerd en ontbreken er mogelijk belang rijke leden van de module. Gebruik deze para meter voor het opsporen van fouten en het testen van de module, of wanneer u wordt gevraagd deze te gebruiken door de module auteur.

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimNamespace

Hiermee geeft u de naam ruimte van een alternatieve CIM-provider die CIM-modules beschikbaar stelt. De standaard waarde is de naam ruimte van de WMI-provider van de module detectie.

Gebruik deze para meter om CIM-modules te importeren van computers en apparaten waarop geen Windows-besturings systeem wordt uitgevoerd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

Hiermee geeft u een alternatieve locatie voor CIM-modules op. De standaard waarde is de resource-URI van de module detectie WMI-provider op de externe computer.

Gebruik deze para meter om CIM-modules te importeren van computers en apparaten waarop geen Windows-besturings systeem wordt uitgevoerd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

Hiermee geeft u een CIM-sessie op de externe computer op. Voer een variabele in die de CIM-sessie bevat of een opdracht waarmee de CIM-sessie wordt opgehaald, zoals een [Get-CimSession-](../CimCmdlets/Get-CimSession.md) opdracht.

`Import-Module` maakt gebruik van de verbinding met de CIM-sessie om modules van de externe computer te importeren in de huidige sessie. Wanneer u de opdrachten van de geïmporteerde module in de huidige sessie gebruikt, worden de opdrachten uitgevoerd op de externe computer.

U kunt deze para meter gebruiken om modules te importeren van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd, en Windows-computers met Power shell, maar waarvoor geen externe communicatie van Power shell is ingeschakeld.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cmdlet

Hiermee geeft u een matrix met cmdlets op die met deze cmdlet van de module in de huidige sessie worden geïmporteerd.
Joker tekens zijn toegestaan.

Sommige modules exporteren geselecteerde cmdlets automatisch naar uw sessie wanneer u de module importeert.
Met deze para meter kunt u uit de geëxporteerde cmdlets selecteren.

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

### -DisableNameChecking

Geeft aan dat deze cmdlet het bericht onderdrukt dat u waarschuwt wanneer u een cmdlet of functie importeert waarvan de naam een niet-goedgekeurde term of een verboden teken bevat.

Als een module die u importeert, cmdlets of functies met een niet-goedgekeurde term in hun namen exporteert, wordt standaard het volgende waarschuwings bericht weer gegeven:

> Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd. Gebruik de para meter uitgebreid voor meer details of typ Get-Verb om de lijst met goedgekeurde werk woorden weer te geven.

Dit bericht wordt alleen een waarschuwing gegeven. De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten. Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.

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

### -Force

Deze para meter zorgt ervoor dat een module wordt geladen, of opnieuw geladen, boven op de huidige.

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

### -FullyQualifiedName

Hiermee geeft u de volledig gekwalificeerde naam van de module op als een hash-tabel. De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen. De hash-tabel bevat de volgende sleutels.

- `ModuleName` - **Vereist** Hiermee geeft u de module naam op.
- `GUID` - **Optioneel** Hiermee geeft u de GUID van de module.
- Het is ook **vereist** om een van de drie onderstaande sleutels op te geven. Deze sleutels kunnen niet tegelijk worden gebruikt.
  - `ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.
  - `RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.
  - `MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedNameAndPSSession, FullyQualifiedName, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Functie

Hiermee geeft u een matrix op met functies die met deze cmdlet worden geïmporteerd van de module in de huidige sessie.
Joker tekens zijn toegestaan. In sommige modules worden geselecteerde functies automatisch geëxporteerd naar uw sessie wanneer u de module importeert. Met deze para meter kunt u kiezen uit de geëxporteerde functies.

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

### -Wereld wijd

Geeft aan dat met deze cmdlet modules worden geïmporteerd in de algemene sessie status, zodat deze beschikbaar zijn voor alle opdrachten in de sessie.

Wanneer `Import-Module` cmdlet wordt aangeroepen vanuit de opdracht prompt, script bestand of script Block, worden standaard alle opdrachten geïmporteerd in de status van de globale sessie.

Wanneer de cmdlet vanuit een andere module wordt aangeroepen, worden `Import-Module` de opdrachten in een module, inclusief opdrachten van geneste modules, in de sessie status van de aanroepende module geïmporteerd.

> [!TIP]
> U moet aanroepen `Import-Module` vanuit een module vermijden. Declareer in plaats daarvan de doel module als een geneste module in het manifest van de bovenliggende module. Het declareren van geneste modules verbetert de detectie van afhankelijkheden.

De **algemene** para meter is gelijk aan de **bereik** parameter met de waarde **Global**.

Als u de opdrachten die een module exporteert, wilt beperken, gebruikt u een `Export-ModuleMember` opdracht in de script module.

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

### -MaximumVersion

Hiermee geeft u een maximum versie op. Met deze cmdlet wordt alleen een versie van de module geïmporteerd die kleiner is dan of gelijk is aan de opgegeven waarde. Als er geen versie in aanmerking komt, `Import-Module` wordt een fout geretourneerd.

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u een minimum versie op. Met deze cmdlet wordt alleen een versie van de module geïmporteerd die groter is dan of gelijk is aan de opgegeven waarde. Gebruik de naam van de **MinimumVersion** -para meter of de alias, **versie**. Als er geen versie in aanmerking komt, wordt `Import-Module` een fout gegenereerd.

Als u een exacte versie wilt opgeven, gebruikt u de para meter **RequiredVersion** . U kunt ook de **module** en de **versie** parameters van het sleutel woord **#Requires** gebruiken om een specifieke versie van een module in een script te vereisen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleInfo

Hiermee geeft u een matrix op met module objecten die moeten worden geïmporteerd. Voer een variabele in die de module objecten bevat, of een opdracht die de module objecten ophaalt, bijvoorbeeld de volgende opdracht: `Get-Module -ListAvailable` . U kunt ook module-objecten pipet naar `Import-Module` .

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen op van de modules die u wilt importeren. Voer de naam van de module of de naam van een bestand in de module in, zoals een `.psd1` , `.psm1` , `.dll` of `.ps1` bestand. Bestands paden zijn optioneel. Joker tekens zijn niet toegestaan. U kunt ook de naam van de module en de bestands namen in de pipes `Import-Module` .

Als u een pad weglaat, `Import-Module` zoekt naar de module in de paden die zijn opgeslagen in de `$env:PSModulePath` omgevings variabele.

Geef waar mogelijk alleen de module naam op. Wanneer u een bestands naam opgeeft, worden alleen de leden geïmporteerd die in dat bestand zijn geïmplementeerd. Als de module andere bestanden bevat, worden deze niet geïmporteerd en ontbreken er mogelijk belang rijke leden van de module.

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -NoClobber

Hiermee wordt voor komen dat opdrachten die dezelfde naam hebben als bestaande opdrachten in de huidige sessie worden geïmporteerd. Standaard worden `Import-Module` alle geëxporteerde module opdrachten geïmporteerd.

Opdrachten met dezelfde naam kunnen opdrachten in de sessie verbergen of vervangen. Gebruik de **voor voegsel** -of **NoClobber** -para meter om conflicten met de naam van een sessie te voor komen. Zie ' modules en naam conflicten ' in [about_Modules](about/about_Modules.md) en [about_Command_Precedence](about/about_Command_Precedence.md)voor meer informatie over naam conflicten en de prioriteit van de opdracht.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Voor voegsel

Hiermee geeft u een voor voegsel op dat met deze cmdlet wordt toegevoegd aan de naam woorden in de namen van geïmporteerde module leden.

Gebruik deze para meter om naam conflicten te voor komen die zich kunnen voordoen wanneer verschillende leden in de sessie dezelfde naam hebben. Met deze para meter wordt de module niet gewijzigd en heeft dit geen invloed op bestanden die door de module worden geïmporteerd voor eigen gebruik. Deze worden geneste modules genoemd. Deze cmdlet is alleen van invloed op de namen van leden in de huidige sessie.

Als u bijvoorbeeld het voor voegsel UTC opgeeft en vervolgens een cmdlet importeert `Get-Date` , wordt de cmdlet bekend in de sessie als `Get-UTCDate` en wordt deze niet verward met de oorspronkelijke `Get-Date` cmdlet.

De waarde van deze para meter heeft voor rang op de eigenschap **DefaultCommandPrefix** van de module, waarmee het standaard voorvoegsel wordt opgegeven.

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

### -PSSession

Hiermee geeft u een door Power shell door de gebruiker beheerde sessie ( **PSSession** ) op waarvan de cmdlet modules in de huidige sessie importeert. Voer een variabele in die een **PSSession** of een opdracht bevat waarmee een **PSSession** wordt opgehaald, zoals een `Get-PSSession` opdracht.

Wanneer u een module vanuit een andere sessie in de huidige sessie importeert, kunt u de cmdlets uit de module in de huidige sessie gebruiken, net zoals u cmdlets van een lokale module zou gebruiken. Opdrachten die gebruikmaken van de externe cmdlets worden uitgevoerd in de externe sessie, maar de externe gegevens worden op de achtergrond beheerd door Power shell.

Deze para meter maakt gebruik van de impliciete functie voor externe communicatie van Power shell. Het is gelijk aan het gebruik `Import-PSSession` van de cmdlet om bepaalde modules vanuit een sessie te importeren.

`Import-Module` kan geen Power shell core-modules importeren uit een andere sessie. De Power shell-kern modules hebben namen die beginnen met micro soft. Power shell.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u een versie van de module op die met deze cmdlet wordt geïmporteerd. Als de versie niet is geïnstalleerd, wordt er `Import-Module` een fout gegenereerd.

Standaard wordt `Import-Module` de module geïmporteerd zonder het versie nummer te controleren.

Als u een minimum versie wilt opgeven, gebruikt u de para meter **MinimumVersion** . U kunt ook de **module** en de **versie** parameters van het sleutel woord **#Requires** gebruiken om een specifieke versie van een module in een script te vereisen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

Scripts die gebruikmaken van **RequiredVersion** om modules te importeren die zijn opgenomen in bestaande releases van het Windows-besturings systeem, worden niet automatisch uitgevoerd in toekomstige releases van het Windows-besturings systeem. Dit komt doordat de versie nummers van de Power shell-module in toekomstige releases van het Windows-besturings systeem hoger zijn dan de module versie nummers in bestaande releases van het Windows-besturings systeem.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u een bereik op waarin met deze cmdlet de module wordt geïmporteerd.

De aanvaardbare waarden voor deze parameter zijn:

- **Global**. Beschikbaar voor alle opdrachten in de sessie. Komt overeen met de **algemene** para meter.
- **Lokaal**. Alleen beschikbaar in het huidige bereik.

Wanneer `Import-Module` cmdlet wordt aangeroepen vanuit de opdracht prompt, script bestand of script Block, worden standaard alle opdrachten geïmporteerd in de status van de globale sessie. U kunt de para meter **-Scope** gebruiken met de waarde **lokaal** om module-inhoud te importeren in het script-of script Block-bereik.

Wanneer de cmdlet vanuit een andere module wordt aangeroepen, worden `Import-Module` de opdrachten in een module, inclusief opdrachten van geneste modules, in de sessie status van de oproepende functie geïmporteerd. Opgeven `-Scope Global` of `-Global` aangeven dat met deze cmdlet modules worden geïmporteerd in de algemene sessie status, zodat deze beschikbaar zijn voor alle opdrachten in de sessie.

De **algemene** para meter is gelijk aan de **bereik** parameter met de waarde Global.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variabele

Hiermee geeft u een matrix van variabelen op die met deze cmdlet worden geïmporteerd uit de module in de huidige sessie.
Voer een lijst met variabelen in. Joker tekens zijn toegestaan.

Sommige modules exporteren geselecteerde variabelen automatisch naar uw sessie wanneer u de module importeert.
Met deze para meter kunt u uit de geëxporteerde variabelen selecteren.

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

### -SkipEditionCheck

Hiermee wordt de selectie van het `CompatiblePSEditions` veld overgeslagen.

Hiermee kunt u een module laden vanuit de `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory in Power shell Core wanneer die module niet `Core` in het `CompatiblePSEditions` manifest veld is opgegeven.

Bij het importeren van een module vanuit een ander pad heeft deze switch niets omdat de controle niet wordt uitgevoerd. In Linux en macOS heeft deze switch niets.

Zie [about_PowerShell_Editions](About/about_PowerShell_Editions.md)voor meer informatie.

> [!WARNING]
> `Import-Module -SkipEditionCheck` is het waarschijnlijk dat een module niet kan worden geïmporteerd. Zelfs als de functie slaagt, kan het aanroepen van een opdracht uit de module later mislukken wanneer er een incompatibele API wordt gebruikt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedNameAndPSSession, FullyQualifiedName, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseWindowsPowerShell

Laadt een module met Windows Power shell-compatibiliteits functionaliteit. Zie [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String, System. Management. Automation. PSModuleInfo, System. reflectie. assembly

U kunt een module naam, module object of Assembly-object door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. Management. Automation. PSModuleInfo of System. Management. Automation. PSCustomObject

`Import-Module`Er wordt standaard geen uitvoer gegenereerd. Als u de para meter **PassThru** opgeeft, genereert de cmdlet een **System. Management. Automation. PSModuleInfo** -object dat de module vertegenwoordigt. Als u de para meter **AsCustomObject** opgeeft, wordt er een **PSCustomObject** -object gegenereerd.

## OPMERKINGEN

- Voordat u een module kunt importeren, moet de module op de lokale computer zijn geïnstalleerd. Dat wil zeggen dat de module directory moet worden gekopieerd naar een map die toegankelijk is voor uw lokale computer. Zie [about_Modules](About/about_Modules.md)voor meer informatie.

  U kunt ook de para meters **PSSession** en **CIMSession** gebruiken voor het importeren van modules die op externe computers zijn geïnstalleerd. Opdrachten die gebruikmaken van de cmdlets in deze modules, worden echter uitgevoerd in de externe sessie op de externe computer.

- Als u leden met dezelfde naam en hetzelfde type in uw sessie importeert, gebruikt Power Shell standaard het laatst geïmporteerde lid. Variabelen en aliassen worden vervangen en de oorspronkelijke waarden zijn niet toegankelijk. Functies, cmdlets en providers worden alleen geschaduwd door de nieuwe leden. Ze zijn toegankelijk door in aanmerking te komen voor de naam van de opdracht met de naam van de module, module of functie pad.

- Als u de opmaak gegevens wilt bijwerken voor opdrachten die zijn geïmporteerd uit een module, gebruikt u de `Update-FormatData` cmdlet. `Update-FormatData` werkt ook de opmaak gegevens bij voor opdrachten in de sessie die uit modules zijn geïmporteerd. Als het opmaak bestand voor een module wordt gewijzigd, kunt u een `Update-FormatData` opdracht uitvoeren om de opmaak gegevens voor geïmporteerde opdrachten bij te werken. U hoeft de module niet opnieuw te importeren.

- Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn geïnstalleerd met Power shell, verpakt in modules. In Windows Power Shell 2,0, en in hostgroepen die oudere sessies maken in latere versies van Power shell, worden de kern opdrachten verpakt in modules ( **PSSnapins** ). De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module. Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.

  Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)voor informatie over de **CreateDefault2** -methode waarmee nieuwe-stijl sessies met kern modules worden gemaakt.

- `Import-Module` kan geen Power shell core-modules importeren uit een andere sessie. De Power shell-kern modules hebben namen die beginnen met `Microsoft.PowerShell` .

- In Windows Power Shell 2,0 zijn sommige eigenschaps waarden van het module-object, zoals de waarden van de eigenschappen **ExportedCmdlets** en **NestedModules** , pas ingevuld wanneer de module werd geïmporteerd en niet beschikbaar was op het module object dat de para meter **PassThru** retourneert. In Windows Power Shell 3,0 worden alle waarden van de module-eigenschap ingevuld.

- Als u probeert een module te importeren die gemengde assembly's bevat die niet compatibel zijn met Windows Power Shell 3,0, `Import-Module` wordt een fout bericht als het volgende weer gegeven.

  > Import-Module: de assembly met gemengde modus is gebouwd op basis van versie ' v 2.0.50727 ' van de runtime en kan niet worden geladen in de 4,0-runtime zonder aanvullende configuratie-informatie.

  Deze fout treedt op wanneer een module die is ontworpen voor Windows Power Shell 2,0 ten minste één assembly met een gemengde module bevat, dat wil zeggen een assembly die zowel beheerde als niet-beheerde code bevat, zoals C++ en C#.

  Als u een module wilt importeren die gebruikmaakt van assembly's met gemengde modus, start u Windows Power Shell 2,0 met de volgende opdracht en probeert u het `Import-Module` opnieuw.

  `PowerShell.exe -Version 2.0`

- Als u de functie CIM-sessie wilt gebruiken, moet de externe computer beschikken over WS-Management remoting en Windows Management Instrumentation (WMI), de micro soft-implementatie van de Common Information Model (CIM)-standaard. De computer moet ook de WMI-provider voor module detectie hebben of een alternatieve CIM-provider die dezelfde basis functies heeft.

  U kunt de functie CIM-sessie gebruiken op computers waarop geen Windows-besturings systeem wordt uitgevoerd en op Windows-computers met Power shell, maar geen externe communicatie van Power shell is ingeschakeld.

  U kunt ook de CIM-para meters gebruiken om CIM-modules op te halen van computers waarop externe communicatie van Power shell is ingeschakeld, met inbegrip van de lokale computer. Wanneer u een CIM-sessie op de lokale computer maakt, gebruikt Power shell DCOM in plaats van WMI om de sessie te maken.

- Standaard `Import-Module` importeert de modules in het globale bereik, zelfs wanneer deze worden aangeroepen vanuit een onderliggend bereik. Het bereik op het hoogste niveau en alle onderliggende bereiken hebben toegang tot de geëxporteerde elementen van de module.

  In een onderliggend bereik `-Scope Local` beperkt het importeren tot dat bereik en alle onderliggende bereiken. Bovenliggende bereiken zien de geïmporteerde leden vervolgens niet.

  > [!NOTE]
  > `Get-Module` geeft alle modules weer die in de huidige sessie zijn geladen. Dit omvat modules die lokaal zijn geladen in een onderliggend bereik. Gebruiken `Get-Command -Module modulename` om te zien welke leden in het huidige bereik zijn geladen.

  Als de module klassen-en inventaris definities bevat, gebruikt u `using module` aan het begin van het script. De scripts worden geïmporteerd, met inbegrip van de klassen-en inventaris definities. Zie [about_Using](About/about_Using.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Exporteren-ModuleMember](Export-ModuleMember.md)

[Get-module](Get-Module.md)

[New-module](New-Module.md)

[Remove-module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
