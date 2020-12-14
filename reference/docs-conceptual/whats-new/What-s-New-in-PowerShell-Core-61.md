---
title: Wat is er nieuw in Power shell Core 6,1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,1
ms.date: 09/13/2018
ms.openlocfilehash: 4ff70be239197c7a4f64019d2aab42433f82f36c
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "96840126"
---
# <a name="whats-new-in-powershell-core-61"></a>Wat is er nieuw in Power shell Core 6,1

Hieronder vindt u een selectie van een aantal belang rijke nieuwe functies en wijzigingen die zijn geïntroduceerd in Power shell Core 6,1.

Er **zijn ook talloze** ' saaie dingen ' die Power shell sneller en stabieler maken (plus veel problemen met oplossingen). Bekijk onze [wijzigingen logboek op github](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)voor een volledige lijst met wijzigingen.

En we noemen we een aantal van de onderstaande namen, hartelijk dank voor [alle mede werkers van de Community](https://github.com/PowerShell/PowerShell/graphs/contributors) die deze release hebben gemaakt.

## <a name="net-core-21"></a>.NET Core 2.1

Power shell Core 6,1 is verplaatst naar .NET Core 2,1 nadat deze is [uitgebracht in mei](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/), wat resulteert in een aantal verbeteringen in Power shell, met inbegrip van:

- prestatie verbeteringen (Zie [hieronder](#performance-improvements))
- Ondersteuning voor Alpine Linux (preview-versie)
- [Ondersteuning voor algemeen hulp programma van .net](/dotnet/core/tools/global-tools) -binnenkort beschikbaar in Power shell
- [`Span<T>`](/dotnet/api/system.span-1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows-compatibiliteits pakket voor .NET core

In Windows leverde het .NET-team het [Windows-compatibiliteits pakket voor .net core](https://devblogs.microsoft.com/dotnet/announcing-the-windows-compatibility-pack-for-net-core/), een set assembly's die een aantal verwijderde api's toevoegen aan .net core in Windows.

We hebben het Windows-compatibiliteits pakket toegevoegd aan Power shell Core 6,1-release, zodat alle modules of scripts die gebruikmaken van deze Api's, kunnen worden gebruikt om ze beschikbaar te stellen.

Met het Windows-compatibiliteits pakket kan Power shell core gebruikmaken **van meer dan 1900 cmdlets die worden geleverd met Windows 10 oktober 2018 update en Windows Server 2019**.

## <a name="support-for-application-allow-lists"></a>Ondersteuning voor lijsten voor het toestaan van toepassingen

Power shell Core 6,1 heeft pariteit met Windows Power shell 5,1 met ondersteuning voor [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) en lijsten voor het toestaan van de [device Guard](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) -toepassing. Met lijsten met toepassingen kunt u nauw keurig bepalen welke binaire bestanden mogen worden uitgevoerd in de Power shell- [modus voor beperkte taal](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/).

## <a name="performance-improvements"></a>Prestatieverbeteringen

Power shell Core 6,0 heeft enkele belang rijke prestatie verbeteringen aangebracht. Power shell Core 6,1 blijft de snelheid van bepaalde bewerkingen verbeteren.

`Group-Object`Is bijvoorbeeld sped %66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|    Metrisch gegeven    | Windows PowerShell 5.1 | Power shell Core 6,0 | Power shell Core 6,1 |
| ------------ | ---------------------- | ------------------- | ------------------- |
| Tijd (SEC)   | 25,178                 | 19,653              | 6,641               |
| Versnellen (%) | N.v.t.                    | 21,9%               | 66,2%               |

Op dezelfde manier kunnen sorterings scenario's zoals deze worden verbeterd met meer dan 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|    Metrisch gegeven    | Windows PowerShell 5.1 | Power shell Core 6,0 | Power shell Core 6,1 |
| ------------ | ---------------------- | ------------------- | ------------------- |
| Tijd (SEC)   | 12,170                 | 8,493               | 7,08                |
| Versnellen (%) | N.v.t.                    | 30,2%               | 16,6%               |

`Import-Csv` is ook aanzienlijk sped na een regressie van Windows Power shell.
In het volgende voor beeld wordt een CSV van de test met 26.616 rijen en zes kolommen gebruikt:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|    Metrisch gegeven    | Windows PowerShell 5.1 | Power shell Core 6,0 |  Power shell Core 6,1   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| Tijd (SEC)   | 0,441                  | 1,069               | 0,268                  |
| Versnellen (%) | N.v.t.                    | -142,4%             | 74,9% (39,2% van WPS) |

Ten slotte is de conversie van JSON into `PSObject` sped meer dan 50% sinds Windows Power shell.
In het volgende voor beeld wordt een JSON-test bestand van ~ 2 MB gebruikt:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|    Metrisch gegeven    | Windows PowerShell 5.1 | Power shell Core 6,0 |  Power shell Core 6,1   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| Tijd (SEC)   | 0,259                  | 0,577               | 0,125                  |
| Versnellen (%) | N.v.t.                    | -122,8%             | 78,3% (51,7% van WPS) |

## <a name="check-system32-for-compatible-built-in-modules-on-windows"></a>Controleren `system32` op compatibele ingebouwde modules op Windows

In de Windows 10 1809-update en Windows Server 2019 hebben we een aantal ingebouwde Power shell-modules bijgewerkt om ze te markeren als compatibel met Power shell core.

Wanneer Power shell Core 6,1 wordt gestart, wordt het automatisch opgenomen `$windir\System32` als onderdeel van de `PSModulePath` omgevings variabele. Er worden echter alleen modules beschikbaar gemaakt `Get-Module` en als deze zijn `Import-Module` `CompatiblePSEdition` gemarkeerd als compatibel met `Core` .

```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> U ziet mogelijk verschillende beschik bare modules, afhankelijk van de functies en onderdelen die zijn geïnstalleerd.

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

U kunt dit gedrag negeren om alle modules weer te geven met behulp van de `-SkipEditionCheck` para meter switch.
Er is ook een `PSEdition` eigenschap toegevoegd aan de tabel uitvoer.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Raadpleeg [Power shell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)voor meer informatie over dit gedrag.

## <a name="markdown-cmdlets-and-rendering"></a>Cmdlets en rendering weer geven

Prijs verlaging is een standaard voor het maken van Lees bare tekst documenten met basis opmaak die in HTML kan worden weer gegeven.

Er zijn enkele cmdlets toegevoegd in 6,1 waarmee u de verkortings documenten kunt converteren en weer geven in de-console, met inbegrip van:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Een voor beeld `Show-Markdown` : Hiermee wordt een bestand met een prijs opgave in de-console weer gegeven.

![Show-Markdown-voor beeld](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

Bekijk [deze rfc's](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)voor meer informatie over de werking van deze cmdlets.

## <a name="experimental-feature-flags"></a>Experimentele functie vlaggen

We hebben ondersteuning voor [experimentele functies][]ingeschakeld. Hierdoor kunnen Power shell-ontwikkel aars nieuwe functies leveren en feedback ontvangen voordat het ontwerp is voltooid. Op deze manier wordt voor komen dat wijzigingen worden aangebracht naarmate het ontwerp wordt ontwikkeld.

Gebruik `Get-ExperimentalFeature` om een lijst met beschik bare experimentele functies op te halen. U kunt deze functies in-of uitschakelen met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` .

Meer informatie over deze functie vindt u in [Power shell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Verbeteringen voor web-cmdlets

Dankzij [@markekraus](https://github.com/markekraus) onze web-cmdlets hebt u een volledig Slew van verbeteringen aangebracht: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
en [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod) .

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) : standaard codering ingesteld op UTF-8 voor `application-json` antwoorden
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` para meter voor het toestaan van `Content-Type` headers die niet compatibel zijn met standaarden
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` para meter ter ondersteuning van vereenvoudigde `multipart/form-data` ondersteuning
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) -compatibele, hoofdletter gevoelige verwerking van relatie sleutels
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - `-Resume` para meter voor web-cmdlets toevoegen

## <a name="remoting-improvements"></a>Externe verbeteringen

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>Power shell direct voor containers probeert eerst Power shell core te gebruiken

[Power shell direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is een functie van Power shell en hyper-v waarmee u verbinding kunt maken met een hyper-v-VM of-container zonder netwerk verbinding of andere services voor extern beheer.

In het verleden is Power shell direct verbonden via het ingebouwde Windows Power shell-exemplaar op de container. Nu probeert Power shell direct eerst verbinding te maken met behulp van de beschik bare `pwsh.exe` `PATH` omgevings variabele. Als deze `pwsh.exe` niet beschikbaar is, valt Power shell direct terug naar het gebruik `powershell.exe` .

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` maakt nu afzonderlijke externe eind punten voor Preview-versies

`Enable-PSRemoting` maakt nu twee externe sessie configuraties:

- Een voor de primaire versie van Power shell. Bijvoorbeeld `PowerShell.6`. Dit eind punt dat kan worden verzorgd voor alle secundaire versie-updates als de ' systeembrede ' configuratie van de Power shell 6-sessie
- Een versie-specifieke sessie configuratie, bijvoorbeeld: `PowerShell.6.1.0`

Dit is handig als u wilt dat er meerdere Power shell 6-versies op dezelfde computer zijn geïnstalleerd en toegankelijk zijn.

Daarnaast krijgen Preview-versies van Power shell nu hun eigen externe sessie configuraties na het uitvoeren van de `Enable-PSRemoting` cmdlet:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Uw uitvoer kan verschillen als u WinRM nog niet hebt ingesteld.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Vervolgens kunt u afzonderlijke Power shell-sessie configuraties bekijken voor de preview-versie en stabiele builds van Power shell 6, en voor elke specifieke versies.

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

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port` syntaxis die wordt ondersteund voor SSH

SSH-clients ondersteunen doorgaans een connection string in de indeling `user@host:port` . Met het toevoegen van SSH als protocol voor externe communicatie met Power Shell hebben we ondersteuning toegevoegd voor deze indeling van connection string:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>MSI-optie om het context menu van de Explorer-Shell toe te voegen in Windows

Bedankt [@bergmeister](https://github.com/bergmeister) , u kunt nu een context menu inschakelen in Windows. U kunt nu de systeembrede installatie van Power shell 6,1 openen vanuit een wille keurige map in Windows Verkenner:

![Context menu van shell voor Power shell 6](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a>Goodies

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Als administrator uitvoeren" in de Jump List van Windows-snelkoppelingen

Hartelijk dank voor [@bergmeister](https://github.com/bergmeister) de Jump List van de Power shell core-snelkoppeling bevat nu "als administrator uitvoeren":

![Als administrator uitvoeren in de Power shell 6 Jump List](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` Hiermee wordt naar de vorige map gekeerd

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

`cd`En `cd --` Wijzig naar `$HOME` .

### `Test-Connection`

Hartelijk dank voor [@iSazonov](https://github.com/iSazonov) de [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet is geporteerd naar Power shell core.

### <a name="update-help-as-non-admin"></a>`Update-Help` Als niet-beheerder

Op de populaire vraag `Update-Help` hoeft u niet meer te worden uitgevoerd als beheerder. `Update-Help` de standaard instelling is dat de Help-informatie wordt opgeslagen in een map die door de gebruiker is gedefinieerd.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nieuwe methoden/eigenschappen op `PSCustomObject`

Hartelijk dank voor het [@iSazonov](https://github.com/iSazonov) toevoegen van nieuwe methoden en eigenschappen aan `PSCustomObject` . `PSCustomObject`bevat nu een `Count` / `Length` eigenschap zoals andere objecten.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Dit werk omvat ook `ForEach` en `Where` methoden waarmee u items kunt gebruiken en filteren `PSCustomObject` :

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Bedankt voor @SimonWahlin het toevoegen van de `-Not` para meter aan `Where-Object` . U kunt nu een object filteren in de pijp lijn voor het niet bestaan van een eigenschap, of een eigenschaps waarde van Null/empty.

Met deze opdracht worden bijvoorbeeld alle services geretourneerd waarvoor geen afhankelijke services zijn gedefinieerd:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` Hiermee maakt u een stuk lijst zonder UTF-8-document

Gezien onze overgang naar een stuk lijst-minder UTF-8 in Power shell 6,0, hebben we de `New-ModuleManifest` cmdlet bijgewerkt om een stuk lijst van minder dan UTF-8-documenten te maken in plaats van een UTF-16 1.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversies van PSMethod die moeten worden gedelegeerd

Hartelijk dank voor [@powercode](https://github.com/powercode) het ondersteunen van de conversie van een `PSMethod` naar een gemachtigde. Op die manier kunt u dingen doen `PSMethod` `[M]::DoubleStrLen` als een gemachtigde waarde in `[M]::AggregateString` :

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

Bekijk [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)voor meer informatie over deze wijziging.

### <a name="standard-deviation-in-measure-object"></a>Standaard afwijking in `Measure-Object`

Hartelijk dank voor [@CloudyDino](https://github.com/CloudyDino) het toevoegen van een `StandardDeviation` eigenschap aan `Measure-Object` :

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

Bedankt, [@maybe-hello-world](https://github.com/maybe-hello-world) `Get-PfxCertificate` nu heeft de `Password` para meter, die wordt gebruikt voor `SecureString` . Hierdoor kunt u het niet-interactief gebruiken:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>De functie verwijderen `more`

In het verleden heeft Power shell een functie geleverd in Windows `more` die is verpakt `more.com` . Deze functie is nu verwijderd.

Daarnaast is de `help` functie gewijzigd in gebruik `more.com` in Windows, of de standaard paginering van het systeem die is opgegeven door `$env:PAGER` op niet-Windows-platforms.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` retourneert nu gebruikers naar de huidige werkmap in dat station

Voorheen gebruik `Set-Location` of `cd` om terug te gaan naar een PSDrive die gebruikers naar de standaard locatie voor dat station heeft verzonden.

Bedankt voor [@mcbobke](https://github.com/mcbobke) , gebruikers worden nu verzonden naar de laatst bekende huidige werkmap voor die sessie.

### <a name="windows-powershell-type-accelerators"></a>Windows Power shell-type Accelerators

In Windows Power shell zijn de volgende typen Accelerators opgenomen om gemakkelijker te kunnen werken met hun respectieve typen:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Deze typen Accelerators zijn niet opgenomen in Power shell 6, maar zijn toegevoegd aan Power shell 6,1 uitgevoerd in Windows.

Deze typen zijn handig om eenvoudig AD-en WMI-objecten te maken.

U kunt bijvoorbeeld query's uitvoeren met behulp van LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

In het volgende voor beeld wordt een Win32_OperatingSystem CIM-object gemaakt:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

In dit voor beeld wordt een ManagementClass-object voor Win32_OperatingSystem-klasse geretourneerd.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp` alias voor alle `-LiteralPath` para meters

[@kvprasoon](https://github.com/kvprasoon)We hebben nu een parameter alias `-lp` voor alle ingebouwde Power shell-cmdlets die een `-LiteralPath` para meter hebben.

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

### <a name="msi-based-installation-paths-on-windows"></a>MSI-gebaseerde installatie paden in Windows

In Windows wordt het MSI-pakket nu geïnstalleerd op het volgende pad:

- `$env:ProgramFiles\PowerShell\6\` voor de stabiele installatie van 6. x
- `$env:ProgramFiles\PowerShell\6-preview\` voor de preview-installatie van 6. x

Met deze wijziging wordt ervoor gezorgd dat Power shell core kan worden bijgewerkt/onderhouden door Microsoft Update.

Raadpleeg [Power shell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)voor meer informatie.

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetrie kan alleen worden uitgeschakeld met een omgevings variabele

Power shell core verzendt elementaire telemetriegegevens naar micro soft wanneer deze wordt gestart. De gegevens bevatten de naam van het besturings systeem, de versie van het besturings systeem en de Power shell-versie. Met deze gegevens kunnen we beter inzicht krijgen in de omgevingen waarin Power shell wordt gebruikt en kunnen we de prioriteit van nieuwe functies en oplossingen bepalen.

Als u deze telemetrie wilt afmelden, stelt u de omgevings variabele `POWERSHELL_TELEMETRY_OPTOUT` in op `true` , `yes` of `1` . Het verwijderen van het bestand voor het uitschakelen van telemetrie wordt niet meer ondersteund `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` .

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Niet toegestaan basis verificatie via HTTP in externe communicatie met Power shell op UNIX-platforms

Om te voor komen dat niet-versleuteld verkeer wordt gebruikt, is het gebruik van NTLM/Negotiate of HTTPS vereist voor externe communicatie van Power shell op UNIX-platforms.

Voor meer informatie over deze wijzigingen raadpleegt u [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Verwijderd `VisualBasic` als een ondersteunde taal in Add-Type

In het verleden kunt u Visual Basic code compileren met behulp van de `Add-Type` cmdlet. Visual Basic wordt zelden gebruikt met `Add-Type` . Deze functie is verwijderd om de grootte van Power shell te reduceren.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Opgeruimd gebruik van `CommandTypes.Workflow` en `WorkflowInfoCleaned`

Zie [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)voor meer informatie over deze wijzigingen.

### <a name="group-object-now-sorts-the-groups"></a>Group-Object worden nu de groepen gesorteerd

Als onderdeel van de verbetering van de prestaties `Group-Object` retourneert nu een gesorteerde lijst van de groepen.
Hoewel het niet nodig is om de volg orde te gebruiken, kunt u deze wijziging door lopen als u de eerste groep wilt gebruiken. We hebben besloten dat deze verbetering van de prestaties de verandering waard was, omdat de impact van de afhankelijkheid van het vorige gedrag laag is.

Zie [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409)voor meer informatie over deze wijziging.

<!-- URL references -->
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
