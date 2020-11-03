---
description: Power shell registreert interne bewerkingen van de engine, providers en cmdlets.
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: 5face386a479a0264f5ff2ba3f6665cb1e218a4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252044"
---
# <a name="about-logging-non-windows"></a>Over het registreren van niet-Windows

## <a name="short-description"></a>Korte beschrijving

Power shell registreert interne bewerkingen van de engine, providers en cmdlets.

## <a name="long-description"></a>Lange beschrijving

Power shell registreert gegevens van Power shell-bewerkingen. Power shell registreert bijvoorbeeld bewerkingen, zoals het starten en stoppen van de engine en het starten en stoppen van providers. Er worden ook gegevens over Power shell-opdrachten vastgelegd.

De locatie van Power shell-Logboeken is afhankelijk van het doel platform. In **Linux** kunnen Power shell-logboeken worden gebruikt voor **syslog** en **rsyslog. conf** . Raadpleeg de lokale pagina's van de Linux-computer voor meer informatie `man` . In **macOS** wordt het **os_log** -logboek registratie systeem gebruikt. Zie [os_log ontwikkelaars documentatie](https://developer.apple.com/documentation/os/os_log)voor meer informatie.

## <a name="viewing-powershell-log-output-on-linux"></a>Power shell-logboek uitvoer in Linux weer geven

Power shell meldt zich aan op **syslog** in Linux en een van de hulpprogram ma's die vaak worden gebruikt om **syslog** -inhoud weer te geven, kan worden gebruikt.

De indeling van de logboek vermeldingen maakt gebruik van de volgende sjabloon:

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|Veld        |Beschrijving                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |Een datum/tijd waarop de logboek vermelding is geproduceerd.            |
|`MACHINENAME`|De naam van het systeem waarop het logboek is gemaakt.      |
|`PID`        |De proces-ID van het proces dat de logboek vermelding heeft geschreven. |
|`COMMITID`   |De `git commit` id of het label dat wordt gebruikt om de build te maken.   |
|`TID`        |De thread-ID van de thread die de logboek vermelding heeft geschreven.   |
|`CID`        |De hexadecimale kanaal-id van de logboek vermelding.            |
|             |10 = operationeel, 11 = analyse                         |
|`EVENTID`    |De gebeurtenis-id van de logboek vermelding.                  |
|`TASK`       |De taak-id voor de gebeurtenis vermelding                 |
|`OPCODE`     |De opcode voor de gebeurtenis vermelding                          |
|`LEVEL`      |Het logboek niveau voor de gebeurtenis vermelding                       |
|`MESSAGE`    |Het bericht dat is gekoppeld aan de gebeurtenis vermelding             |

> [!NOTE]
> `EVENTID`, `TASK` , `OPCODE` en `LEVEL` zijn dezelfde waarden die worden gebruikt bij het vastleggen van Logboeken in het Windows-gebeurtenis logboek.

### <a name="filtering-powershell-log-entries-using-rsyslog"></a>Power shell-logboek vermeldingen filteren met rsyslog

Normaal gesp roken worden Power shell-logboek vermeldingen naar de standaard waarde `location/file` voor **syslog** geschreven. Het is echter mogelijk om de vermeldingen om te leiden naar een aangepast bestand.

1. Maak een conf voor de logboek configuratie van Power shell en geef een getal op dat kleiner is dan 50 (voor `50-default.conf` ), zoals `40-powershell.conf` . Het bestand moet onder worden geplaatst `/etc/rsyslog.d` .

1. Voeg de volgende vermelding toe aan het bestand:

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. Zorg ervoor dat `/etc/rsyslog.conf` het nieuwe bestand is opgenomen. Vaak heeft het een algemene include-instructie die eruitziet als de volgende configuratie:

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   Als dat niet het geval is, moet u een instructie include hand matig toevoegen.

1. Zorg ervoor dat de kenmerken en machtigingen juist zijn ingesteld.

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. Eigendom instellen op **hoofdmap**.

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. Toegangs machtigingen instellen: **hoofdmap** heeft lezen/schrijven, **gebruikers** hebben lezen.

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a>Power shell-logboek uitvoer in macOS weer geven

De eenvoudigste methode voor het weer geven van Power shell-logboek uitvoer in macOS is het gebruik van de **console** toepassing.

1. Zoek naar de **console** toepassing en start deze.
1. Selecteer de computer naam onder **apparaten**.
1. Voer in het **Zoek** veld in `pwsh` voor het binaire hoofd bestand van Power shell.
1. Wijzig het zoek filter van `Any` in `Process` .
1. Voer de bewerkingen uit.
1. Sla de zoek opdracht eventueel op voor toekomstig gebruik.

Als u wilt filteren op een specifiek proces exemplaar van Power shell in de- **console** , bevat de variabele `$pid` de proces-id.

1. Voer de **PID** (proces-id) in het **Zoek** veld in.
1. Wijzig het zoek filter in `PID` .
1. Voer de bewerkingen uit.

### <a name="viewing-powershell-log-output-from-a-command-line"></a>Power shell log-uitvoer weer geven vanaf een opdracht regel

De `log` opdracht kan worden gebruikt om Power shell-logboek vermeldingen weer te geven vanaf de opdracht regel.

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a>Power shell-logboek uitvoer persistent maken

Power Shell maakt standaard gebruik van de standaard logboek registratie voor alleen geheugen in macOS. Dit gedrag kan worden gewijzigd om persistentie in te scha kelen met behulp van de `log config` opdracht.

Met het volgende script worden logboek registratie en persistentie op info niveau ingeschakeld:

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

Met de volgende opdracht wordt Power shell-logboek registratie teruggezet naar de standaard status:

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

Nadat persistentie is ingeschakeld, `log show` kan de opdracht worden gebruikt om logboek items te exporteren. De opdracht bevat opties voor het exporteren van de laatste N items, items sinds een bepaalde tijd of items binnen een bepaalde periode.

De volgende opdracht exporteert bijvoorbeeld items sinds `9am on April 5 of 2018` :

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

U kunt hulp krijgen voor `log` door uit te voeren `log show --help` voor aanvullende informatie.

> [!TIP]
> Wanneer u een van de logboek opdrachten uitvoert vanuit een Power shell-prompt of-script, gebruikt u dubbele aanhalings tekens rond de hele predicaat reeks en enkele aanhalings tekens in. Zo voor komt u dat dubbele aanhalings tekens in de predicaat teken reeks niet meer nodig zijn.

U kunt ook overwegen om de gebeurtenis logboeken op een veiligere locatie, zoals een centrale gebeurtenis logboek verzamelaar of [Siem][] aggregator, op te slaan. U kunt SIEM instellen in Azure. Zie [algemene Siem-integratie](/cloud-app-security/siem)voor meer informatie.

## <a name="configuring-logging-on-a-non-windows-system"></a>Logboek registratie configureren op een niet-Windows-systeem

In Windows wordt logboek registratie geconfigureerd door ETW-listeners te maken of door de Logboeken te gebruiken om analytische logboek registratie in te scha kelen. In Linux en macOS wordt logboek registratie geconfigureerd met behulp van het bestand `powershell.config.json` . In de rest van deze sectie wordt beschreven hoe u Power shell-logboek registratie configureert op een niet-Windows-systeem.

Standaard maakt Power shell informatie logboek registratie mogelijk aan het operationele kanaal. Dit betekent dat een logboek uitvoer wordt gemaakt door Power shell en dat is gemarkeerd als operationeel, en dat er een logboek (tracerings niveau) groter is dan informatief wordt geregistreerd. Soms is het mogelijk dat er een extra logboek uitvoer vereist is, zoals uitgebreide logboek uitvoer of het inschakelen van de logboek uitvoer van analytic.

Het bestand `powershell.config.json` is een bestand met **JSON** -indeling dat zich in de Power shell-map bevindt `$PSHOME` . Elke installatie van Power shell gebruikt een eigen kopie van dit bestand. Voor een normale werking blijft dit bestand ongewijzigd. Hoewel het nuttig kan zijn om enkele van de instellingen in het bestand te wijzigen voor diagnose of om onderscheid te maken tussen meerdere Power shell-versies op hetzelfde systeem of zelfs meerdere kopieën van dezelfde versie (Zie `LogIdentity` de onderstaande tabel).

De volgende code is een voorbeeld configuratie:

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

De eigenschappen voor het configureren van Power shell-logboek registratie worden weer gegeven in de volgende tabel. Waarden die zijn gemarkeerd met een asterisk, zoals `Operational*` , geven de standaard waarde aan wanneer er geen waarde in het bestand is opgenomen.

|Eigenschap   |Waarden        |Beschrijving                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|(teken reeks naam) |De naam die moet worden gebruikt bij het vastleggen van gegevens. Met  |
|           |zo   |Power shell is de identiteit. Deze waarde kan worden|
|           |              |Hiermee wordt het verschil tussen twee      |
|           |              |instanties van een Power shell-installatie, zoals |
|           |              |Als release-en bèta versie. Deze waarde is |
|           |              |wordt ook gebruikt om de logboek uitvoer om te leiden naar een        |
|           |              |afzonderlijk bestand op Linux. Zie de bespreking van|
|           |              |**rsyslog** hierboven.                           |
|`LogChannels`|Functioneren  |De kanalen die moeten worden ingeschakeld. De waarden scheiden|
|           |Analytisch      |met een komma bij het opgeven van meer dan één.  |
|`LogLevel`   |Altijd        |Geef één waarde op. De waarde kan  |
|           |Kritiek      |zelf en alle waarden erboven in        |
|           |Fout         |aan de linkerkant weer gegeven.                            |
|           |Waarschuwing       |                                             |
|           |Informatief|                                             |
|           |Uitgebreid       |                                             |
|           |Fouten opsporen         |                                             |
|`LogKeywords`|Runspace      |Tref woorden bieden de mogelijkheid om logboek registratie te beperken|
|           |Pijplijn      |naar specifieke onderdelen in Power shell. Door |
|           |Protocol      |Standaard worden alle tref woorden ingeschakeld en gewijzigd |
|           |Transport     |Deze waarde is alleen nuttig voor zeer           |
|           |Host          |gespecialiseerde probleem oplossing.                |
|           |Cmdlets       |                                             |
|           |Serializer    |                                             |
|           |Sessie       |                                             |
|           |ManagedPlugin |                                             |

## <a name="see-also"></a>Zie ook

Raadpleeg de lokale pagina's van de Linux-computer voor meer informatie over Linux **syslog** en **rsyslog. conf** . `man`

Raadpleeg [os_log Developer-documentatie](https://developer.apple.com/documentation/os/os_log)voor informatie over macOS **os_log** .

[about_Logging_Windows](about_Logging_Windows.md)

[Algemene SIEM-integratie](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management

