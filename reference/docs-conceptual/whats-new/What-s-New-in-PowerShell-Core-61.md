---
title: Wat is er nieuw in PowerShell Core 6.1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: b95b9dd504ea2a165a4689a3b28d2298644e5e68
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611519"
---
# <a name="whats-new-in-powershell-core-61"></a>Wat is er nieuw in PowerShell Core 6.1

Hieronder ziet u een selectie van een aantal van de belangrijkste nieuwe functies en wijzigingen die zijn geïntroduceerd in PowerShell Core 6.1.

Er is ook **ton** van "fijne" waardoor PowerShell sneller en stabieler (plus veel en veel fouten opgelost).
Voor een volledige lijst van wijzigingen, Bekijk onze [changelog op GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

En hoewel we noemen enkele onderstaande namen, Hartelijk dank aan [alle van de community-inzenders](https://github.com/PowerShell/PowerShell/graphs/contributors) die deze versie mogelijk gemaakt.

## <a name="net-core-21"></a>.NET core 2.1

PowerShell Core 6.1 verplaatst naar .NET Core 2.1 nadat deze is [die zijn uitgebracht in mei](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), wat resulteert in een aantal verbeteringen in PowerShell, met inbegrip van:

- Verbeterde prestaties (Zie [hieronder](#performance-improvements))
- Alpine Linux-ondersteuning (preview)
- [Ondersteuning voor .NET-algemeen hulpmiddel](/dotnet/core/tools/global-tools) - komende snel naar PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows-compatibiliteitspakket voor .NET Core

Op Windows, het team van .NET verzonden de [Windows-compatibiliteitspakket voor .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), een set met assembly's die een aantal toevoegen verwijderd API's terug naar .NET Core in Windows.

We hebben het Windows-compatibiliteitspakket naar PowerShell Core 6.1 release toegevoegd zodat alle modules of scripts die gebruikmaken van deze API's kunnen erop vertrouwen dat ze beschikbaar worden gesteld.

De Windows-compatibiliteitspakket kunt u PowerShell Core gebruiken **meer dan 1900 cmdlets die worden geleverd met Windows 10 oktober 2018 Update en Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Ondersteuning voor opname in de Whitelist

PowerShell Core 6.1 heeft pariteit met de ondersteuning van Windows PowerShell 5.1 [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) en [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) opname in de whitelist.
Opname in de whitelist kunt gedetailleerde controle over welke binaire bestanden mogen worden uitgevoerd gebruikt in combinatie met PowerShell [beperkte taalmodus](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).

## <a name="performance-improvements"></a>Verbeterde prestaties

Enkele belangrijke prestatieverbeteringen doorgevoerd in PowerShell Core 6.0.
PowerShell Core 6.1 blijft voor het verbeteren van de snelheid van bepaalde bewerkingen.

Bijvoorbeeld, `Group-Object` met 66% van heeft zijn sped:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tijd (sec)   | 25.178                 | 19.653              | 6.641               |
| Versnellen (%) | N.v.t.                    | 21,9%               | 66.2%               |

Op deze manier zijn sorteren scenario's zoals deze verbeterd door meer dan 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tijd (sec)   | 12.170                 | 8.493               | 7.08                |
| Versnellen (%) | N.v.t.                    | 30,2%               | 16.6%               |

`Import-Csv` heeft ook zijn sped van aanzienlijk na een regressie vanuit Windows PowerShell.
Het volgende voorbeeld wordt een test CSV met 26,616 rijen en zes kolommen:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tijd (sec)   | 0.441                  | 1.069               | 0.268                  |
| Versnellen (%) | N.v.t.                    | -142.4%             | 74.9% (% 39.2 van WPS) |

Ten slotte de conversie van JSON in `PSObject` up heeft zijn sped met meer dan 50% sinds Windows PowerShell.
Het volgende voorbeeld wordt een ~ 2MB test JSON-bestand:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tijd (sec)   | 0.259                  | 0.577               | 0,125                  |
| Versnellen (%) | N.v.t.                    | -122.8%             | 78,3% (% 51.7 van WPS) |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a>Controleer `system32` voor modules die compatibel zijn postvak in op Windows

Een getal van postvak in PowerShell-modules om ze te markeren als zijnde compatibel met PowerShell Core is bijgewerkt in de Windows 10 1809 update en Windows Server 2019.

Wanneer PowerShell Core 6.1 wordt gestart, wordt deze automatisch bevatten `$windir\System32` als onderdeel van de `PSModulePath` omgevingsvariabele.
Echter het toont alleen modules `Get-Module` en `Import-Module` als de `CompatiblePSEdition` is gemarkeerd als compatibel met `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Mogelijk ziet u andere beschikbare modules, afhankelijk van welke functies en onderdelen zijn geïnstalleerd.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

U kunt dit gedrag om weer te geven van alle modules met behulp van overschrijven de `-SkipEditionCheck` parameter overschakelen.
We hebben ook hebt toegevoegd een `PSEdition` eigenschap aan de tabeluitvoer.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Bekijk voor meer informatie over dit gedrag [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Markdown-cmdlets en -rendering

Markdown is een standaard voor het maken van documenten in leesbare tekst zonder opmaak met eenvoudige opmaak die kan worden gerenderd in HTML.

We hebben enkele cmdlets toegevoegd in 6.1 waarmee u kunt converteren en Markdown-documenten in de console weergegeven met inbegrip van:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Bijvoorbeeld, `Show-Markdown` een Markdown-bestand in de console wordt weergegeven:

![Show-Markdown-voorbeeld](./images/markdown_example.png)

Bekijk voor meer informatie over de werking van deze cmdlets [deze RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Vlaggen voor experimentele functie

Vlaggen voor experimentele functie kunnen gebruikers in te schakelen functies die nog niet is voltooid.
Deze experimentele functies worden niet ondersteund en fouten kunnen hebben.

U kunt meer informatie over deze functie in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Verbeteringen voor web-cmdlet

Dankzij @markekraus, heel veel verbeteringen zijn aangebracht aan onze web-cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
en [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [Pull-aanvraag #6109](https://github.com/PowerShell/PowerShell/pull/6109) -codering is ingesteld op UTF-8 voor standaard `application-json` antwoorden
- [Pull-aanvraag #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parameter om toe te staan `Content-Type` kopteksten die niet compatibel zijn met standaarden
- [Pull-aanvraag #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` parameter voor de ondersteuning van vereenvoudigd `multipart/form-data` ondersteunen
- [Pull-aanvraag #6338](https://github.com/PowerShell/PowerShell/pull/6338) - compatibele, niet-hoofdlettergevoelige verwerken van relatie-sleutels
- [Pull-aanvraag #6447](https://github.com/PowerShell/PowerShell/pull/6447) -toevoegen `-Resume` parameter voor cmdlets voor web

## <a name="remoting-improvements"></a>Verbeteringen voor externe toegang

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a>PowerShell Direct probeert eerst te gebruiken PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is een functie van PowerShell en Hyper-V, waarmee u verbinding maken met een Hyper-V virtuele machine zonder netwerkverbinding of andere services extern beheer.

In het verleden verbonden PowerShell Direct met behulp van het postvak in Windows PowerShell-exemplaar op de virtuele machine.
Nu, PowerShell Direct eerst verbinding probeert te maken met behulp van de beschikbare `pwsh.exe` op de `PATH` omgevingsvariabele.
Als `pwsh.exe` is niet beschikbaar is, PowerShell Direct terugvalt voor het gebruik van `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` nu maakt u afzonderlijke externe eindpunten voor de preview-versies

`Enable-PSRemoting` u maakt nu twee externe communicatie van sessieconfiguraties:

- Een voor de belangrijkste versie van PowerShell. Bijvoorbeeld,`PowerShell.6`. Dit eindpunt dat kan worden gebruikt voor updates van de secundaire versie als de sessieconfiguratie 'systeembrede' PowerShell 6
- Een specifieke versies sessieconfiguratie, bijvoorbeeld: `PowerShell.6.1.0`

Dit gedrag is handig als u wilt dat meerdere versies van PowerShell 6 geïnstalleerd en toegankelijk is op dezelfde computer.

Bovendien preview-versies van PowerShell nu toegang tot hun eigen remoting sessieconfiguraties nadat de `Enable-PSRemoting` cmdlet:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

De uitvoer kan afwijken als u WinRM voordat u dit nog niet hebt ingesteld.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Vervolgens ziet u afzonderlijke PowerShell-sessie-configuraties voor de Preview-versie en stabiel builds van PowerShell 6, en voor elke specifieke versie.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port` syntaxis die worden ondersteund voor SSH

SSH clients ondersteunen meestal een verbindingsreeks in de indeling `user@host:port`.
Met de toevoeging van SSH als protocol voor externe communicatie van PowerShell, is er ondersteuning toegevoegd voor deze indeling van de verbindingsreeks:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>MSI-optie voor het toevoegen van contextmenu explorer-shell op Windows

Dankzij @bergmeister, nu u in het contextmenu op Windows kunt. U kunt nu uw systeembrede-installatie van PowerShell 6.1 openen vanuit een willekeurige map in Windows Explorer:

![Shell-contextmenu voor PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Goodies

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Als Administrator uitvoeren' in de lijst met Windows snelkoppeling naar de landingspagina

Dankzij @bergmeister, van de snelkoppeling van de PowerShell Core jump lijst bevat nu 'Als Administrator uitvoeren':

![Uitvoeren als administrator in de lijst met PowerShell 6 landingspagina](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` terug naar de vorige map

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Of op Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Bovendien `cd --` wordt gewijzigd in `$HOME`.

### `Test-Connection`

Dankzij @iSazonov, wordt de [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet heeft zijn overgezet naar PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` Als niet-beheerder

Op veler verzoek `Update-Help` langer moet worden uitgevoerd als beheerder.
`Update-Help` opslaan van Help-informatie naar een map binnen het bereik van gebruiker is nu standaard.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nieuwe methoden/eigenschappen op `PSCustomObject`

Dankzij @iSazonov, hebben we nieuwe methoden en eigenschappen die moeten toegevoegd `PSCustomObject`.
`PSCustomObject` bevat nu een `Count` / `Length` eigenschap waarmee het aantal items.

Deze voorbeelden retourneren `2` als het aantal `PSCustomObjects` in de verzameling.

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

Deze taak bevat ook `ForEach` en `Where` methoden waarmee u kunt werken en te filteren op `PSCustomObject` items:

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

Dankzij @SimonWahlin, hebben we toegevoegd aan de `-Not` parameter `Where-Object`.
U kunt nu een object in de pijplijn voor de niet-aanwezigheid van een eigenschap of een eigenschapswaarde van null/leeg filteren.

Met deze opdracht retourneert bijvoorbeeld alle services die niet geen afhankelijke services gedefinieerd zijn:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` Hiermee maakt u een stuklijst zonder UTF-8-document

Opgegeven onze verplaatsen naar stuklijst zonder UTF-8 in PowerShell 6.0, we hebben bijgewerkt de `New-ModuleManifest` cmdlet om een document stuklijst zonder UTF-8 in plaats van een UTF-16 een te maken.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversies van PSMethod gemachtigde

Dankzij @powercode, we ondersteunen nu de conversie van een `PSMethod` in een gemachtigde.
Hiermee kunt u voor handelingen zoals doorgeven `PSMethod` `[M]::DoubleStrLen` als de waarde van een gemachtigde in `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Bekijk voor meer informatie over deze wijziging [pull-aanvraag #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Standaarddeviatie in `Measure-Object`

Dankzij @CloudyDino, hebben we toegevoegd aan een `StandardDeviation` eigenschap `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Dankzij @maybe-hello-world, `Get-PfxCertificate` heeft nu de `Password` parameter, waarbij een `SecureString`. Hiermee kunt u niet-interactief gebruiken:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Het verwijderen van de `more` functie

In het verleden PowerShell een functie in Windows met de naam verzonden `more` die verpakt `more.com`.
Deze functie is nu verwijderd.

Ook de `help` functie gewijzigd in het gebruik van `more.com` op Windows of van het systeem standaard pager is opgegeven door `$env:PAGER` op niet-Windows-platforms.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` retourneert nu gebruikers aan de huidige werkmap op het desbetreffende station

Eerder, met behulp van `Set-Location` of `cd` om terug te keren naar een PSDrive gebruikers verzonden naar de standaardlocatie voor dat station.

Dankzij @mcbobke, gebruikers worden nu verzonden naar de laatste bekende huidige werkmap voor deze sessie.

### <a name="windows-powershell-type-accelerators"></a>Windows PowerShell type accelerators

In Windows PowerShell, hebben we het volgende type accelerators zodat het eenvoudiger om te werken met hun respectieve gegevenstypen opgenomen:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Deze accelerators type niet zijn opgenomen in PowerShell 6, maar zijn toegevoegd aan die wordt uitgevoerd op Windows PowerShell-6.1.

Deze typen zijn nuttig bij het maken van eenvoudig AD en WMI-objecten.

U kunt bijvoorbeeld een query met behulp van LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Deze voorbeelden maken een Win32_OperatingSystem CIM-object:

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp` alias voor alle `-LiteralPath` parameters

Dankzij @kvprasoon, we hebben nu een parameteralias `-lp` voor alle de ingebouwde PowerShell-cmdlets die u hebt een `-LiteralPath` parameter.

## <a name="breaking-changes"></a>Belangrijke wijzigingen

### <a name="msi-based-installation-paths-on-windows"></a>MSI-gebaseerde installatiepaden op Windows

Op Windows, is het MSI-pakket nu wordt geïnstalleerd in het volgende pad:

- `$env:ProgramFiles\PowerShell\6\` voor de installatie van de stabiele van 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` voor de installatie van de Preview-versie van 6.x

Deze wijziging zorgt ervoor dat PowerShell Core bijgewerkt/afgehandeld door de Microsoft Update worden kunnen.

Bekijk voor meer informatie, [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetrie kan alleen worden uitgeschakeld met een omgevingsvariabele

PowerShell Core worden standaard telemetriegegevens naar Microsoft verzonden wanneer deze wordt gestart. De gegevens bevatten de naam van besturingssysteem, de versie van het besturingssysteem en de PowerShell-versie. Deze gegevens kan we meer inzicht in de omgevingen waar PowerShell wordt gebruikt en kan we nieuwe functies en oplossingen prioriteren.

Als u wilt zich afmelden deze telemetrische gegevens, stel de omgevingsvariabele `POWERSHELL_TELEMETRY_OPTOUT` naar `true`, `yes`, of `1`. We bieden geen ondersteuning voor het verwijderen van het bestand `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` telemetrie uitschakelen.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Basisverificatie toegestaan via HTTP in PowerShell voor externe toegang voor Unix-platforms

Om te voorkomen dat het gebruik van niet-versleuteld verkeer, nu vereist gebruik van NTLM/Negotiate- of HTTPS PowerShell voor externe toegang op Unix-platforms.

Bekijk voor meer informatie over deze wijzigingen [pull-aanvraag #6799](https://github.com/PowerShell/PowerShell/pull/6799).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Verwijderd `VisualBasic` als een ondersteunde taal in Add-Type

In het verleden kon u compileren Visual Basic met behulp van code de `Add-Type` cmdlet.
Visual Basic is die zelden worden gebruikt met `Add-Type`. We hebben verwijderd deze functie om de grootte van PowerShell te verkleinen.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Het gebruik van opgeschoond `CommandTypes.Workflow` en `WorkflowInfoCleaned`

Bekijk voor meer informatie over deze wijzigingen [pull-aanvraag #6708](https://github.com/PowerShell/PowerShell/pull/6708).
