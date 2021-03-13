---
description: Configuratie bestanden voor Power shell, waarbij de Register configuratie wordt vervangen.
Locale: en-US
ms.date: 03/12/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: e6688e91f0cf14ae54a0585ae199f098e98e1146
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412961"
---
# <a name="about-powershell-config"></a>Over Power shell-configuratie

## <a name="short-description"></a>KORTE BESCHRIJVING
Configuratie bestanden voor Power shell core, waarbij de Register configuratie wordt vervangen.

## <a name="long-description"></a>LANGE BESCHRIJVING

Het `powershell.config.json` bestand bevat configuratie-instellingen voor Power shell core. Power shell laadt deze configuratie bij het opstarten. De instellingen kunnen tijdens runtime ook worden gewijzigd. Voorheen werden deze instellingen opgeslagen in het Windows-REGI ster voor Power shell, maar zijn ze nu opgenomen in een bestand om de configuratie in macOS en Linux in te scha kelen.

> [!WARNING]
> Niet-herkende sleutels of ongeldige waarden in het configuratie bestand worden op de achtergrond genegeerd. Als het `powershell.config.json` bestand een ongeldige JSON bevat, kan Power shell geen interactieve sessie starten. Als dit het geval is, moet u het configuratie bestand herstellen.

### <a name="allusers-shared-configuration"></a>AllUsers (gedeelde) configuratie

Een `powershell.config.json` bestand in de `$PSHOME` map definieert de configuratie voor alle Power shell-kern sessies die worden uitgevoerd vanaf die Power shell Core-installatie.

> [!NOTE]
> De `$PSHOME` locatie wordt gedefinieerd als dezelfde map als de uitvoerende System.Management.Automation.dll-assembly. Dit geldt ook voor gehoste Power shell SDK-exemplaren.

### <a name="currentuser-per-user-configurations"></a>Instellingen voor het CurrentUser-configuratie (per gebruiker)

U kunt Power shell ook configureren op basis van per gebruiker door het bestand in de map voor het configureren van de gebruikers scope te plaatsen. De map gebruikers configuratie kan worden gevonden op verschillende platformen met de opdracht `Split-Path $PROFILE.CurrentUserCurrentHost` .

## <a name="general-configuration-settings"></a>Algemene configuratie-instellingen

### <a name="executionpolicy"></a>ExecutionPolicy

> [!IMPORTANT]
> Deze configuratie is alleen van toepassing op Windows-platforms.

Hiermee configureert u het uitvoerings beleid voor Power shell-sessies, waarbij u bepaalt welke scripts kunnen worden uitgevoerd. Power Shell maakt standaard gebruik van het bestaande uitvoerings beleid.

Voor AllUsers-configuraties wordt hiermee het beleid voor het uitvoeren van **LocalMachine** ingesteld.
Hiermee wordt het beleid voor het uitvoeren **van CurrentUser ingesteld** .

> [!NOTE]
> De [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet wijzigt deze instelling in het configuratie bestand ALLUSERS wanneer deze wordt aangeroepen met `-Scope LocalMachine` en wijzigt deze instelling in het bestand van het bestand CurrentUser wanneer aangeroepen met `-Scope CurrentUser` .

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

Waar:

- `<shell-id>` verwijst naar de ID van de huidige Power shell-host. Voor de normale Power shell Core is dit `Microsoft.PowerShell` . In een Power shell-sessie kunt u deze detecteren met `$ShellId` .
- `<execution-policy>` verwijst naar een geldige naam voor het uitvoerings beleid.

In het volgende voor beeld wordt het uitvoerings beleid van Power shell ingesteld op `RemoteSigned` .

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

In Windows kunt u de equivalente register sleutels vinden in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` onder `HKEY_LOCAL_MACHINE` en `HKEY_CURRENT_USER` .

### <a name="psmodulepath"></a>PSModulePath

Onderdrukt de `PSModulePath` instellingen voor deze Power shell-sessie. Als de configuratie voor de huidige gebruiker is, stelt het pad van de **CurrentUser** -module in. Als de configuratie voor alle gebruikers is ingesteld, stelt het pad naar de **ALLUSERS** -module in.

> [!WARNING]
> Als u hier een pad naar een **ALLUSERS** of **CurrentUser** -module configureert, wordt de installatie locatie met het bereik voor PowerShellGet-cmdlets zoals [installatie-module](/powershell/module/powershellget/install-module)niet gewijzigd. Deze cmdlets gebruiken altijd de _standaard_ module paden.

Als er geen waarde is ingesteld, gebruikt Power shell de standaard waarde voor de betreffende instelling van het pad naar de module. Zie [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath)voor meer informatie over deze standaard waarden.

Met deze instelling kunt u omgevings variabelen gebruiken door ze in te sluiten tussen `%` tekens, zoals `"%HOME%\Documents\PowerShell\Modules"` , op dezelfde manier als met Cmd. Deze syntaxis is ook van toepassing op Linux en macOS. Hieronder vindt u voor beelden.

```Schema
"PSModulePath": "<ps-module-path>"
```

Waar:

- `<ps-module-path>` is het absolute pad naar een module directory. Voor alle gebruikers configuraties is dit de map AllUsers Shared module. Voor de huidige gebruikers configuraties is dit de map van de CurrentUser-module.

Dit voor beeld toont een `PSModulePath` configuratie voor een Windows-omgeving:

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

Dit voor beeld toont een `PSModulePath` configuratie voor een macOS-of Linux-omgeving:

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

In dit voor beeld ziet u het insluiten van een omgevings variabele in een `PSModulePath` configuratie. Houd er rekening mee dat met behulp `HOME` van de omgevings variabele en het `/` mappen scheidings teken dit werkt in Windows, MacOS en Linux.

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

In dit voor beeld ziet u het insluiten van een omgevings variabele in een `PSModulePath` configuratie die alleen wordt gebruikt voor macOS en Linux:

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> Power shell-variabelen kunnen niet worden inge sloten in `PSModulePath` configuraties.
> `PSModulePath` configuraties voor Linux en macOS zijn hoofdletter gevoelig. Een `PSModulePath` configuratie moet geldige mappen scheidings tekens voor het platform gebruiken. Op macOS en Linux betekent dit `/` . In Windows zijn beide `/` en `\` werkt.

### <a name="experimentalfeatures"></a>ExperimentalFeatures

De namen van de experimentele functies die in Power shell moeten worden ingeschakeld. Standaard zijn er geen experimentele functies ingeschakeld. De standaard waarde is een lege matrix.

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

Waar:

- `<experimental-feature-name>` is de naam van een experimentele functie die moet worden ingeschakeld.

In het volgende voor beeld worden de experimentele functies **PSImplicitRemoting** en **PSUseAbbreviationExpansion** ingeschakeld wanneer Power shell wordt gestart.

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

Zie [experimentele functies gebruiken](/powershell/scripting/learn/experimental-features)voor meer informatie over experimentele functies.

## <a name="non-windows-logging-configuration"></a>Configuratie van niet-Windows-logboek registratie

> [!IMPORTANT]
> De configuratie opties in deze sectie zijn alleen van toepassing op macOS en Linux.
> Logboek registratie voor Windows wordt beheerd door de Windows-Logboeken.

De logboek registratie van de Power shell in macOS en Linux kan worden geconfigureerd in het Power shell-configuratie bestand. Zie [over logboek registratie](./about_Logging_Non-Windows.md)voor een volledige beschrijving van Power shell-logboek registratie voor niet-Windows-systemen.

### <a name="logidentity"></a>LogIdentity

> [!IMPORTANT]
> Deze instelling kan alleen worden gebruikt in macOS en Linux.

Hiermee stelt u de identiteits naam in die wordt gebruikt om naar het systeem logboek te schrijven. De standaard waarde is Power shell.

```Schema
"LogIdentity": "<log-identity>"
```

Waar:

- `<log-identity>` is de teken reeks-id die Power shell moet gebruiken voor het schrijven naar syslog.

> [!NOTE]
> U wilt mogelijk verschillende **LogIdentity** -waarden hebben voor elk exemplaar van Power shell dat u hebt geïnstalleerd.

In dit voor beeld configureren we de **LogIdentity** voor een preview-release van Power shell.

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a>Logniveau

> [!IMPORTANT]
> Deze instelling kan alleen worden gebruikt in macOS en Linux.

Hiermee geeft u het minimale Ernst niveau op waarmee Power shell moet registreren.

```Schema
"LogLevel": "<log-level>|default"
```

Waar:

- `<log-level>` heeft een van de volgende waarden:
  - Altijd
  - Kritiek
  - Fout
  - Waarschuwing
  - Informatief
  - Uitgebreid
  - Fouten opsporen

> [!NOTE]
> Als u een logboek niveau instelt, worden alle bovenstaande logboek niveaus ingeschakeld.

Als u deze instelling instelt op **standaard** , wordt de standaard waarde geïnterpreteerd.
De standaard waarde is **informatief**.

In het volgende voor beeld wordt de waarde ingesteld op **uitgebreid**.

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a>LogChannels

> [!IMPORTANT]
> Deze instelling kan alleen worden gebruikt in macOS en Linux.

Hiermee wordt bepaald welke registratie kanalen worden ingeschakeld.

```Schema
"LogChannels": "<log-channel>,..."
```

Waar:

- `<log-channel>` heeft een van de volgende waarden:
  - Operationeel: registreert basis informatie over Power shell-activiteiten
  - Analytische-registreert meer gedetailleerde diagnostische gegevens

De standaard waarde is **operationeel**. Als u beide kanalen wilt inschakelen, neemt u beide waarden op als één door komma's gescheiden teken reeks. Bijvoorbeeld:

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a>LogKeywords

> [!IMPORTANT]
> Deze instelling kan alleen worden gebruikt in macOS en Linux.

Hiermee wordt bepaald welke delen van Power shell worden vastgelegd. Standaard zijn alle logboek trefwoorden ingeschakeld. Als u meerdere tref woorden wilt inschakelen, vermeldt u de waarden in één door komma's gescheiden teken reeks.

```Schema
"LogKeywords": "<log-keyword>,..."
```

Waar:

- `<log-keyword>` heeft een van de volgende waarden:
  - Runs Pace-beheer van runs Pace
  - Pijp lijn-pijplijn bewerkingen
  - Protocol-Communication handling, zoals PSRP
  - Ondersteuning voor transport lagen, zoals SSH
  - Host-Power shell-host-functionaliteit, bijvoorbeeld interactie met de console
  - Cmdlets-ingebouwde Power shell-cmdlets
  - Logica van serializer-serialisatie
  - Sessie-Power shell-sessie status
  - ManagedPlugin-WSMan-invoeg toepassing

> [!NOTE]
> Het wordt over het algemeen aangeraden deze waarde uit te stellen, tenzij u probeert een bepaald gedrag in een bekend deel van Power shell op te sporen. Als u deze waarde wijzigt, wordt alleen de hoeveelheid vastgelegde informatie verkleind.

In dit voor beeld wordt de logboek registratie beperkt tot runs Pace-bewerkingen, pijplijn logica en cmdlet-gebruik. Alle andere logboek registratie wordt wegge laten.

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a>Meer voorbeeld configuraties

### <a name="example-windows-configuration"></a>Voor beeld van Windows-configuratie

Voor deze configuratie zijn meer instellingen expliciet ingesteld:

- Uitvoerings beleid voor deze Power shell-installatie is `AllSigned`
- Het pad van de CurrentUser-module wordt ingesteld op een module directory op een gedeeld station
- De `PSImplicitRemotingBatching` experimentele functie is ingeschakeld

> [!NOTE]
> De `ExecutionPolicy` instellingen en worden `PSModulePath` hier alleen op een Windows-platform toegepast, omdat het pad naar de module gebruik maakt van `\` `;` scheidings tekens en het uitvoerings beleid niet `Unrestricted` (het enige beleid dat is toegestaan op UNIX-achtige platformen).

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a>Voor beeld van niet-Windows-configuratie

Met deze configuratie wordt een aantal opties ingesteld die alleen in macOS of Linux werken:

- Het pad naar de CurrentUser-module is ingesteld op een aangepaste module directory in `$HOME`
- De functie **PSImplicitRemotingBatching** experimentele is ingeschakeld
- Het Power shell-logboek niveau is ingesteld op **uitgebreid**, voor meer logboek registratie
- Met deze Power shell-installatie wordt er naar de logboeken geschreven met de **Home-Power shell-** identiteit.

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a>Zie ook

[Over uitvoerings beleid](./about_Execution_Policies.md)

[Over automatische variabelen](./about_Automatic_Variables.md)
