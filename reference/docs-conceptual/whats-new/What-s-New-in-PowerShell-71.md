---
title: Wat is er nieuw in Power shell 7,1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell 7,1
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577204"
---
# <a name="whats-new-in-powershell-71"></a>Wat is er nieuw in Power shell 7,1

Op 11 november 2020 hebben we de algemene Beschik baarheid van Power shell 7,1 [aangekondigd](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) . Voortbouwend op de basis die is vastgesteld in Power shell 7,0, onze inspanningen gericht op problemen van de community en bevatten een aantal verbeteringen en oplossingen. We streven ernaar om ervoor te zorgen dat Power shell een stabiel en het beste platform blijft.

Power shell 7,1 bevat de volgende functies, updates en belang rijke wijzigingen.

- PSReadLine 2.1.0, met inbegrip van voorspellende IntelliSense
- Power shell 7,1 is gepubliceerd op de Microsoft Store
- Installatie pakketten bijgewerkt voor nieuwe versies van besturings systemen met ondersteuning voor ARM64
- 4 nieuwe experimentele functies en twee experimentele functies gepromoveerd tot mainstream
- Verschillende belang rijke wijzigingen om de bruikbaarheid te verbeteren

Zie de [wijzigingen logboek](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in de GitHub-opslag plaats voor een volledige lijst met wijzigingen.

## <a name="psreadline-210"></a>PSReadLine 2.1.0

Power shell 7,1 bevat ook PSReadLine 2.1.0. Deze versie bevat voorspellende IntelliSense. Zie de [aankondiging](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in het Power shell-blog voor meer informatie over de functie voor voorspellende IntelliSense.

## <a name="microsoft-store-installer-package"></a>Microsoft Store Installer-pakket

Power shell 7,1 is gepubliceerd op de Microsoft Store. U kunt de Power shell-release vinden op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.

Voor delen van het Microsoft Store-pakket:

- Automatische updates zijn direct in Windows 10 ingebouwd
- Kan worden geïntegreerd met andere software distributie mechanismen, zoals intune en SCCM

> [!NOTE]
> Alle configuratie-instellingen op systeem niveau die zijn opgeslagen in, `$PSHOME` kunnen niet worden gewijzigd. Dit omvat de WSMAN-configuratie. Hiermee voor komt u dat externe sessies verbinding maken met op opslag gebaseerde installaties van Power shell. Configuraties op gebruikers niveau en externe SSH-communicatie worden ondersteund.

## <a name="other-installers"></a>Andere installatie Programma's

Zie de [Power shell-ondersteunings levenscyclus](/powershell/scripting/powershell-support-lifecycle)voor meer actuele informatie over de ondersteunde besturings systemen en de levens cyclus van de ondersteuning.

Controleer de installatie-instructies voor uw voorkeurs besturings systeem:

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [MacOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

Daarnaast ondersteunt Power shell 7,1 ARM32-en ARM64-smaakten van Debian, Ubuntu en ARM64 Alpine Linux.

Hoewel niet officieel wordt ondersteund, heeft de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux verschaft.

> [!NOTE]
> Debian 10 +, CentOS 8 +, Ubuntu 20,04, alpine en arm bieden momenteel geen ondersteuning voor externe toegang via WinRM. Zie voor meer informatie over het instellen van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="experimental-features"></a>Experimentele functies

Zie [experimentele functies gebruiken](../learn/experimental-features.md)voor meer informatie over de experimentele functies.

De volgende experimentele functies zijn nu algemene functies in deze release:

- [PSNullConditionalOperators](../learn/experimental-features.md#psnullconditionaloperators)
- [PSUnixFileStat](../learn/experimental-features.md#psunixfilestat)

In deze release zijn de volgende experimentele functies toegevoegd:

- [Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - Power shell 7,1 breidt deze experimentele functie uit om de para meter **runs Pace** toe te voegen aan alle `*-PSBreakpoint` cmdlets. De para meter **runs Pace** geeft een **runs Pace** -object op om te communiceren met onderbrekings punten in de opgegeven runs Pace.

- [PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) : met deze functie kunt u de paden van de Power shell-provider door geven aan systeem eigen opdrachten die geen Power shell-pad-syntaxis ondersteunen.

- [PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) : wanneer de linkeroperand in een `-replace` operator instructie geen teken reeks is, wordt die operand geconverteerd naar een teken reeks. Als de functie is ingeschakeld, gebruikt de conversie geen cultuur instellingen voor teken reeks conversie.

- [PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) legt de basis voor de ondersteuning van toekomstige voorspellende IntelliSense-invoeg toepassingen.

## <a name="breaking-changes-and-improvements"></a>Wijzigingen en verbeteringen te verbreken

- Oplossing `$?` niet wanneer een `$false` systeem eigen opdracht schrijft naar `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))

  Het is gebruikelijk dat systeem eigen opdrachten schrijven naar `stderr` zonder dat ze een fout aangeven.
  Deze wijziging `$?` is alleen ingesteld op `$false` wanneer de systeem eigen opdracht ook een afsluit code heeft die niet gelijk is aan nul. Deze wijziging is niet gerelateerd aan het experimentele onderdeel `PSNotApplyErrorActionToStderr` .

- `$ErrorActionPreference`Geen invloed hebben op de `stderr` uitvoer van systeem eigen opdrachten ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))

  Het is gebruikelijk dat systeem eigen opdrachten schrijven naar `stderr` zonder dat ze een fout aangeven.
  Met deze wijziging `stderr` wordt de uitvoer nog steeds vastgelegd in **ErrorRecord** -objecten, maar de runtime is niet meer van toepassing `$ErrorActionPreference` als de **ErrorRecord** afkomstig is van een native opdracht.

- Wijzig de naam in `-FromUnixTime` `-UnixTimeSeconds` `Get-Date` om Unix-tijd invoer ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) toe te staan (bedankt @aetos382 !)

  De `-FromUnixTime` para meter is toegevoegd tijdens 7,1-Preview. 2. De naam van de para meter is gewijzigd om deze beter te laten overeenkomen met het gegevens type. Deze para meter neemt een geheel getal in seconden sinds 1 januari 1970, 0:00:00.

  In dit voor beeld wordt een Unix-tijd (vertegenwoordigd door het aantal seconden sinds 1970-01-01 0:00:00) geconverteerd naar DateTime.

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- Een expliciet opgegeven benoemde para meter mag vervangen door de naam van de hashtabel splatting (#13162)

  Met deze wijziging worden de benoemde para meters van splatting verplaatst naar het einde van de lijst met para meters, zodat deze zijn gebonden nadat alle expliciet opgegeven benoemde para meters zijn gebonden. Parameter binding voor eenvoudige functies genereert geen fout wanneer een opgegeven benoemde para meter niet kan worden gevonden. Onbekende benoemde para meters zijn gekoppeld aan de `$args` para meter van de functie Simple. Als u splatting verplaatst naar het einde van de argumenten lijst, wordt de volg orde gewijzigd waarin de para meters worden weer gegeven `$args` .

  Bijvoorbeeld:

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  In het vorige gedrag is **MYPATH** niet gebonden aan `-Path` het derde argument in de lijst met argumenten. # #, Zodat deze wordt gecenteerd in ' $args ' samen met `Blah = "World"`

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  Met deze wijziging worden de argumenten van `@hash` verplaatst naar het einde van de lijst met argumenten. **MYPATH** wordt het eerste argument in de lijst, dus is het gebonden aan `-Path` .

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- De para meter voor de switch parameter `-Qualifier` niet positioneel instellen `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (bedankt @yecril71pl !)

- De werkmap omzetten als letterlijk pad voor `Start-Process` wanneer deze niet is opgegeven ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (bedankt @NoMoreFood !)

- Stel de `-OutFile` para meter in Web-cmdlets als volgt `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (bedankt @iSazonov !)

- Teken reeks parameter binding voor `BigInteger` numerieke letterlijke waarden ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) oplossen (bedankt @vexx32 !)

- In Windows `Start-Process` maakt een proces omgeving met alle omgevings variabelen uit de huidige sessie, met behulp van `-UseNewEnvironment` een nieuwe standaard proces omgeving ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (bedankt @iSazonov !)

- Retour resultaat niet laten teruglopen bij `PSObject` het converteren van een `ScriptBlock` naar een gemachtigde ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))

  Wanneer een `ScriptBlock` is geconverteerd naar een type gemachtigde dat moet worden gebruikt in de C#-context, wordt het resultaat in een niet- `PSObject` nood zakelijk probleem gewrappt:

  - Wanneer de waarde wordt geconverteerd naar het retour type van de gemachtigde, `PSObject` wordt in feite onverpakt opgehaald. Het `PSObject` is dus niet nodig.
  - Wanneer het retour type van de gemachtigde is `object` , wordt het verpakt in een gepakte manier `PSObject` om in C#-code te werken.

  Na deze wijziging is het geretourneerde object het onderliggende object.
