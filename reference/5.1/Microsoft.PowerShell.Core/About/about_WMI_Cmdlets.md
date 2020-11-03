---
description: Bevat achtergrond informatie over Windows Management Instrumentation (WMI) en Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252727"
---
# <a name="about-wmi-cmdlets"></a>Over WMI-cmdlets

## <a name="short-description"></a>KORTE BESCHRIJVING

Bevat achtergrond informatie over Windows Management Instrumentation (WMI) en Windows Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

In dit onderwerp vindt u informatie over de WMI-technologie, de WMI-cmdlets voor Windows Power shell, op WMI gebaseerde externe toegang, WMI-accelerators en WMI-probleem oplossing. Dit onderwerp bevat ook koppelingen naar meer informatie over WMI.

### <a name="about-wmi"></a>OVER WMI

Windows Management Instrumentation (WMI) is de Microsoft-implementatie van Web-Based Enterprise Management (WBEM), een industrie-initiatief om een standaardtechnologie te ontwikkelen voor het werken met beheerinformatie in een bedrijfsomgeving. WMI maakt gebruik van het industrie-initiatief Common Information Model (CIM) om systemen, toepassingen, netwerken, apparaten en andere beheerde onderdelen te representeren. CIM is ontwikkeld en wordt onderhouden door Distributed Management Task Force (DMTF). U kunt WMI gebruiken voor het beheren van lokale en externe computers. U kunt WMI bijvoorbeeld gebruiken om het volgende te doen:

- Start een proces op een externe computer.
- Een computer op afstand opnieuw opstarten.
- Een lijst ophalen van de toepassingen die op een lokale of externe computer zijn geïnstalleerd.
- Een query uitvoeren op de Windows-gebeurtenis logboeken op een lokale of externe computer.

### <a name="the-wmi-cmdlets-for-windows-powershell"></a>DE WMI-CMDLETS VOOR WINDOWS POWER SHELL

Windows Power shell implementeert WMI-functionaliteit via een set cmdlets die standaard beschikbaar zijn in Windows Power shell. U kunt deze cmdlets gebruiken voor het volt ooien van de end-to-end taken die nodig zijn voor het beheren van lokale en externe computers.

De volgende WMI-cmdlets zijn opgenomen.

|Cmdlet           |Beschrijving                                   |
|-----------------|----------------------------------------------|
|Get-WmiObject    |Hiermee worden instanties van WMI-klassen of-gegevens opgehaald  |
|                 |over de beschik bare klassen.                  |
|Invoke-WmiMethod |WMI-methoden aanroept.                            |
|Register-WmiEvent|Abonneren op een WMI-gebeurtenis.                    |
|Remove-WmiObject |WMI-klassen en-instanties worden verwijderd.            |
|Set-WmiInstance  |Hiermee worden instanties van WMI-klassen gemaakt of gewijzigd. |

### <a name="sample-commands"></a>VOORBEELD OPDRACHTEN
Met de volgende opdracht wordt de BIOS-informatie voor de lokale computer weer gegeven.

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

De volgende opdracht geeft informatie weer over de WinRM-service voor drie externe computers.

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

Met de volgende complexe opdracht worden alle exemplaren van een programma afgesloten.

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a>EXTERNE TOEGANG OP BASIS VAN WMI

Hoewel de mogelijkheid om een lokaal systeem te beheren via WMI nuttig is, is dit de mogelijkheden voor externe toegang die WMI een krachtig beheer programma maken. WMI maakt gebruik van gedistribueerde Component Object Model (DCOM) van micro soft voor het maken van verbinding met en het beheren van systemen. Mogelijk moet u sommige systemen configureren om DCOM-verbindingen toe te staan.
Firewall instellingen en vergrendelde DCOM-machtigingen kunnen de mogelijkheid van WMI om systemen op afstand te beheren blok keren.

### <a name="wmi-type-accelerators"></a>WMI-TYPE ACCELERATORS

Windows Power shell bevat WMI-type Accelerators. Deze WMI-type Accelerators (snelkoppelingen) bieden meer directe toegang tot WMI-objecten dan een niet-type versnelling zou toestaan.

De volgende typen accelerators worden ondersteund met WMI:

[WMISEARCHER]-een snelkoppeling voor het zoeken naar WMI-objecten.

[WMICLASS]: een snelkoppeling voor het openen van de statische eigenschappen en methoden van een klasse.

[WMI]: een snelkoppeling voor het ophalen van één exemplaar van een klasse.

[WMISEARCHER] is een type Accelerator voor een ManagementObjectSearcher. Dit kan een teken reeks constructor zijn om een zoek programma te maken waarin u vervolgens een GET () op kunt uitvoeren.

Bijvoorbeeld:

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

[WMICLASS] is een type Accelerator voor ManagementClass. Dit heeft een teken reeks constructor die een lokaal of absoluut WMI-pad naar een WMI-klasse gebruikt en een object retourneert dat is gekoppeld aan deze klasse.

Bijvoorbeeld:

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

[WMI] is een type Accelerator voor ManagementObject. Dit heeft een teken reeks constructor die een lokaal of absoluut WMI-pad naar een WMI-exemplaar gebruikt en een object retourneert dat is gekoppeld aan dat exemplaar.

Bijvoorbeeld:

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a>WMI-PROBLEMEN OPLOSSEN

De volgende problemen zijn de meest voorkomende problemen die zich kunnen voordoen wanneer u verbinding probeert te maken met een externe computer.

Probleem 1: de externe computer is niet online.

Als een computer offline is, kunt u er geen verbinding mee maken met behulp van WMI.
U ontvangt mogelijk het volgende foutbericht:

```
Remote server machine does not exist or is unavailable
```

Als dit fout bericht wordt weer gegeven, controleert u of de computer online is. Probeer de externe computer te pingen.

Probleem 2: u hebt geen lokale Administrator rechten op de externe computer.

Als u WMI op afstand wilt gebruiken, moet u over lokale beheerders rechten beschikken op de externe computer. Als u dit niet doet, wordt de toegang tot die computer geweigerd.

Naam ruimte beveiliging controleren:

1. Klik op Start, klik met de rechter muisknop op mijn computer en klik vervolgens op beheren.
2. In computer beheer vouwt u services en toepassingen uit, klikt u met de rechter muisknop op WMI-beheer en klikt u vervolgens op Eigenschappen.
3. Klik in het dialoog venster WMI Control-eigenschappen op het tabblad Beveiliging.

Probleem 3: de toegang tot de externe computer wordt geblokkeerd door een firewall.

WMI maakt gebruik van de protocollen DCOM (Distributed COM) en RPC (Remote Procedure Call) om via het netwerk te passeren. Standaard blok keren firewalls DCOM en RPC-verkeer. Als uw firewall deze protocollen blokkeert, mislukt de verbinding. Windows Firewall in micro soft Windows XP Service Pack 2 is bijvoorbeeld zodanig geconfigureerd dat alle ongevraagde netwerk verkeer, waaronder DCOM en WMI, automatisch wordt geblokkeerd. In de standaard configuratie wijst Windows Firewall een binnenkomende WMI-aanvraag af en wordt het volgende fout bericht weer gegeven:

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a>ZIE OOK

[Over WMI](/windows/win32/wmisdk/about-wmi)

[WMI-problemen oplossen](/windows/win32/wmisdk/wmi-troubleshooting)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[Invoke-WmiMethod](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[REGI ster-WmiEvent](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[Remove-WmiObject](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[Set-WmiInstance](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
