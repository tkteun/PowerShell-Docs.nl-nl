---
description: Power shell registreert interne bewerkingen van de engine, providers en cmdlets.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: e74e357d81eddf87ad27d023eb9a8ba2977156e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705363"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="0bff9-103">Over het registreren van niet-Windows</span><span class="sxs-lookup"><span data-stu-id="0bff9-103">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="0bff9-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="0bff9-104">Short description</span></span>
<span data-ttu-id="0bff9-105">Power shell registreert interne bewerkingen van de engine, providers en cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0bff9-105">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="0bff9-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="0bff9-106">Long description</span></span>

<span data-ttu-id="0bff9-107">Power shell registreert gegevens van Power shell-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="0bff9-107">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="0bff9-108">Power shell registreert bijvoorbeeld bewerkingen, zoals het starten en stoppen van de engine en het starten en stoppen van providers.</span><span class="sxs-lookup"><span data-stu-id="0bff9-108">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="0bff9-109">Er worden ook gegevens over Power shell-opdrachten vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="0bff9-109">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="0bff9-110">De locatie van Power shell-Logboeken is afhankelijk van het doel platform.</span><span class="sxs-lookup"><span data-stu-id="0bff9-110">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="0bff9-111">In **Linux** kunnen Power shell-logboeken worden gebruikt voor **syslog** en **rsyslog. conf** .</span><span class="sxs-lookup"><span data-stu-id="0bff9-111">On **Linux**, PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="0bff9-112">Raadpleeg de lokale pagina's van de Linux-computer voor meer informatie `man` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-112">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="0bff9-113">In **macOS** wordt het **os_log** -logboek registratie systeem gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0bff9-113">On **macOS**, the **os_log** logging system is used.</span></span> <span data-ttu-id="0bff9-114">Zie [os_log ontwikkelaars documentatie](https://developer.apple.com/documentation/os/os_log)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0bff9-114">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="0bff9-115">Power shell-logboek uitvoer in Linux weer geven</span><span class="sxs-lookup"><span data-stu-id="0bff9-115">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="0bff9-116">Power shell meldt zich aan op **syslog** in Linux en een van de hulpprogram ma's die vaak worden gebruikt om **syslog** -inhoud weer te geven, kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0bff9-116">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="0bff9-117">De indeling van de logboek vermeldingen maakt gebruik van de volgende sjabloon:</span><span class="sxs-lookup"><span data-stu-id="0bff9-117">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="0bff9-118">Veld</span><span class="sxs-lookup"><span data-stu-id="0bff9-118">Field</span></span>        |<span data-ttu-id="0bff9-119">Description</span><span class="sxs-lookup"><span data-stu-id="0bff9-119">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="0bff9-120">Een datum/tijd waarop de logboek vermelding is geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="0bff9-120">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="0bff9-121">De naam van het systeem waarop het logboek is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0bff9-121">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="0bff9-122">De proces-ID van het proces dat de logboek vermelding heeft geschreven.</span><span class="sxs-lookup"><span data-stu-id="0bff9-122">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="0bff9-123">De `git commit` id of het label dat wordt gebruikt om de build te maken.</span><span class="sxs-lookup"><span data-stu-id="0bff9-123">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="0bff9-124">De thread-ID van de thread die de logboek vermelding heeft geschreven.</span><span class="sxs-lookup"><span data-stu-id="0bff9-124">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="0bff9-125">De hexadecimale kanaal-id van de logboek vermelding.</span><span class="sxs-lookup"><span data-stu-id="0bff9-125">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="0bff9-126">10 = operationeel, 11 = analyse</span><span class="sxs-lookup"><span data-stu-id="0bff9-126">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="0bff9-127">De gebeurtenis-id van de logboek vermelding.</span><span class="sxs-lookup"><span data-stu-id="0bff9-127">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="0bff9-128">De taak-id voor de gebeurtenis vermelding</span><span class="sxs-lookup"><span data-stu-id="0bff9-128">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="0bff9-129">De opcode voor de gebeurtenis vermelding</span><span class="sxs-lookup"><span data-stu-id="0bff9-129">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="0bff9-130">Het logboek niveau voor de gebeurtenis vermelding</span><span class="sxs-lookup"><span data-stu-id="0bff9-130">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="0bff9-131">Het bericht dat is gekoppeld aan de gebeurtenis vermelding</span><span class="sxs-lookup"><span data-stu-id="0bff9-131">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="0bff9-132">`EVENTID`, `TASK` , `OPCODE` en `LEVEL` zijn dezelfde waarden die worden gebruikt bij het vastleggen van Logboeken in het Windows-gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="0bff9-132">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="0bff9-133">Power shell-logboek vermeldingen filteren met rsyslog</span><span class="sxs-lookup"><span data-stu-id="0bff9-133">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="0bff9-134">Normaal gesp roken worden Power shell-logboek vermeldingen naar de standaard waarde `location/file` voor **syslog** geschreven.</span><span class="sxs-lookup"><span data-stu-id="0bff9-134">Normally, PowerShell log entries are written to the default `location/file` for **syslog**.</span></span> <span data-ttu-id="0bff9-135">Het is echter mogelijk om de vermeldingen om te leiden naar een aangepast bestand.</span><span class="sxs-lookup"><span data-stu-id="0bff9-135">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="0bff9-136">Maak een conf voor de logboek configuratie van Power shell en geef een getal op dat kleiner is dan 50 (voor `50-default.conf` ), zoals `40-powershell.conf` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-136">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="0bff9-137">Het bestand moet onder worden geplaatst `/etc/rsyslog.d` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-137">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="0bff9-138">Voeg de volgende vermelding toe aan het bestand:</span><span class="sxs-lookup"><span data-stu-id="0bff9-138">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="0bff9-139">Zorg ervoor dat `/etc/rsyslog.conf` het nieuwe bestand is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="0bff9-139">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="0bff9-140">Vaak heeft het een algemene include-instructie die eruitziet als de volgende configuratie:</span><span class="sxs-lookup"><span data-stu-id="0bff9-140">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="0bff9-141">Als dat niet het geval is, moet u een instructie include hand matig toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0bff9-141">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="0bff9-142">Zorg ervoor dat de kenmerken en machtigingen juist zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="0bff9-142">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="0bff9-143">Eigendom instellen op **hoofdmap**.</span><span class="sxs-lookup"><span data-stu-id="0bff9-143">Set ownership to **root**.</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="0bff9-144">Toegangs machtigingen instellen: **hoofdmap** heeft lezen/schrijven, **gebruikers** hebben lezen.</span><span class="sxs-lookup"><span data-stu-id="0bff9-144">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="0bff9-145">Power shell-logboek uitvoer in macOS weer geven</span><span class="sxs-lookup"><span data-stu-id="0bff9-145">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="0bff9-146">De eenvoudigste methode voor het weer geven van Power shell-logboek uitvoer in macOS is het gebruik van de **console** toepassing.</span><span class="sxs-lookup"><span data-stu-id="0bff9-146">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="0bff9-147">Zoek naar de **console** toepassing en start deze.</span><span class="sxs-lookup"><span data-stu-id="0bff9-147">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="0bff9-148">Selecteer de computer naam onder **apparaten**.</span><span class="sxs-lookup"><span data-stu-id="0bff9-148">Select the Machine name under **Devices**.</span></span>
1. <span data-ttu-id="0bff9-149">Voer in het **Zoek** veld in `pwsh` voor het binaire hoofd bestand van Power shell.</span><span class="sxs-lookup"><span data-stu-id="0bff9-149">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="0bff9-150">Wijzig het zoek filter van `Any` in `Process` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-150">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="0bff9-151">Voer de bewerkingen uit.</span><span class="sxs-lookup"><span data-stu-id="0bff9-151">Perform the operations.</span></span>
1. <span data-ttu-id="0bff9-152">Sla de zoek opdracht eventueel op voor toekomstig gebruik.</span><span class="sxs-lookup"><span data-stu-id="0bff9-152">Optionally, save the search for future use.</span></span>

<span data-ttu-id="0bff9-153">Als u wilt filteren op een specifiek proces exemplaar van Power shell in de- **console**, bevat de variabele `$pid` de proces-id.</span><span class="sxs-lookup"><span data-stu-id="0bff9-153">To filter on a specific process instance of PowerShell in the **Console**, the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="0bff9-154">Voer de **PID** (proces-id) in het **Zoek** veld in.</span><span class="sxs-lookup"><span data-stu-id="0bff9-154">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="0bff9-155">Wijzig het zoek filter in `PID` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-155">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="0bff9-156">Voer de bewerkingen uit.</span><span class="sxs-lookup"><span data-stu-id="0bff9-156">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="0bff9-157">Power shell log-uitvoer weer geven vanaf een opdracht regel</span><span class="sxs-lookup"><span data-stu-id="0bff9-157">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="0bff9-158">De `log` opdracht kan worden gebruikt om Power shell-logboek vermeldingen weer te geven vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="0bff9-158">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="0bff9-159">Power shell-logboek uitvoer persistent maken</span><span class="sxs-lookup"><span data-stu-id="0bff9-159">Persisting PowerShell log output</span></span>

<span data-ttu-id="0bff9-160">Power Shell maakt standaard gebruik van de standaard logboek registratie voor alleen geheugen in macOS.</span><span class="sxs-lookup"><span data-stu-id="0bff9-160">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="0bff9-161">Dit gedrag kan worden gewijzigd om persistentie in te scha kelen met behulp van de `log config` opdracht.</span><span class="sxs-lookup"><span data-stu-id="0bff9-161">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="0bff9-162">Met het volgende script worden logboek registratie en persistentie op info niveau ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="0bff9-162">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="0bff9-163">Met de volgende opdracht wordt Power shell-logboek registratie teruggezet naar de standaard status:</span><span class="sxs-lookup"><span data-stu-id="0bff9-163">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="0bff9-164">Nadat persistentie is ingeschakeld, `log show` kan de opdracht worden gebruikt om logboek items te exporteren.</span><span class="sxs-lookup"><span data-stu-id="0bff9-164">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="0bff9-165">De opdracht bevat opties voor het exporteren van de laatste N items, items sinds een bepaalde tijd of items binnen een bepaalde periode.</span><span class="sxs-lookup"><span data-stu-id="0bff9-165">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="0bff9-166">De volgende opdracht exporteert bijvoorbeeld items sinds `9am on April 5 of 2018` :</span><span class="sxs-lookup"><span data-stu-id="0bff9-166">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="0bff9-167">U kunt hulp krijgen voor `log` door uit te voeren `log show --help` voor aanvullende informatie.</span><span class="sxs-lookup"><span data-stu-id="0bff9-167">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="0bff9-168">Wanneer u een van de logboek opdrachten uitvoert vanuit een Power shell-prompt of-script, gebruikt u dubbele aanhalings tekens rond de hele predicaat reeks en enkele aanhalings tekens in.</span><span class="sxs-lookup"><span data-stu-id="0bff9-168">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="0bff9-169">Zo voor komt u dat dubbele aanhalings tekens in de predicaat teken reeks niet meer nodig zijn.</span><span class="sxs-lookup"><span data-stu-id="0bff9-169">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="0bff9-170">U kunt ook overwegen om de gebeurtenis logboeken op een veiligere locatie, zoals een centrale gebeurtenis logboek verzamelaar of [Siem][] aggregator, op te slaan.</span><span class="sxs-lookup"><span data-stu-id="0bff9-170">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="0bff9-171">U kunt SIEM instellen in Azure.</span><span class="sxs-lookup"><span data-stu-id="0bff9-171">You can set up SIEM in Azure.</span></span> <span data-ttu-id="0bff9-172">Zie [algemene Siem-integratie](/cloud-app-security/siem)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0bff9-172">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="0bff9-173">Logboek registratie configureren op een niet-Windows-systeem</span><span class="sxs-lookup"><span data-stu-id="0bff9-173">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="0bff9-174">In Windows wordt logboek registratie geconfigureerd door ETW-listeners te maken of door de Logboeken te gebruiken om analytische logboek registratie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="0bff9-174">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="0bff9-175">In Linux en macOS wordt logboek registratie geconfigureerd met behulp van het bestand `powershell.config.json` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-175">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="0bff9-176">In de rest van deze sectie wordt beschreven hoe u Power shell-logboek registratie configureert op een niet-Windows-systeem.</span><span class="sxs-lookup"><span data-stu-id="0bff9-176">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="0bff9-177">Standaard maakt Power shell informatie logboek registratie mogelijk aan het operationele kanaal.</span><span class="sxs-lookup"><span data-stu-id="0bff9-177">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="0bff9-178">Dit betekent dat een logboek uitvoer wordt gemaakt door Power shell en dat is gemarkeerd als operationeel, en dat er een logboek (tracerings niveau) groter is dan informatief wordt geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="0bff9-178">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="0bff9-179">Soms is het mogelijk dat er een extra logboek uitvoer vereist is, zoals uitgebreide logboek uitvoer of het inschakelen van de logboek uitvoer van analytic.</span><span class="sxs-lookup"><span data-stu-id="0bff9-179">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="0bff9-180">Het bestand `powershell.config.json` is een bestand met **JSON** -indeling dat zich in de Power shell-map bevindt `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="0bff9-180">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="0bff9-181">Elke installatie van Power shell gebruikt een eigen kopie van dit bestand.</span><span class="sxs-lookup"><span data-stu-id="0bff9-181">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="0bff9-182">Voor een normale werking blijft dit bestand ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0bff9-182">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="0bff9-183">Hoewel het nuttig kan zijn om enkele van de instellingen in het bestand te wijzigen voor diagnose of om onderscheid te maken tussen meerdere Power shell-versies op hetzelfde systeem of zelfs meerdere kopieën van dezelfde versie (Zie `LogIdentity` de onderstaande tabel).</span><span class="sxs-lookup"><span data-stu-id="0bff9-183">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="0bff9-184">De volgende code is een voorbeeld configuratie:</span><span class="sxs-lookup"><span data-stu-id="0bff9-184">The following code is an example configuration:</span></span>

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

<span data-ttu-id="0bff9-185">De eigenschappen voor het configureren van Power shell-logboek registratie worden weer gegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="0bff9-185">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="0bff9-186">Waarden die zijn gemarkeerd met een asterisk, zoals `Operational*` , geven de standaard waarde aan wanneer er geen waarde in het bestand is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="0bff9-186">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="0bff9-187">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="0bff9-187">Property</span></span>   |<span data-ttu-id="0bff9-188">Waarden</span><span class="sxs-lookup"><span data-stu-id="0bff9-188">Values</span></span>        |<span data-ttu-id="0bff9-189">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0bff9-189">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="0bff9-190">(teken reeks naam)</span><span class="sxs-lookup"><span data-stu-id="0bff9-190">(string name)</span></span> |<span data-ttu-id="0bff9-191">De naam die moet worden gebruikt bij het vastleggen van gegevens.</span><span class="sxs-lookup"><span data-stu-id="0bff9-191">The name to use when logging.</span></span> <span data-ttu-id="0bff9-192">Met</span><span class="sxs-lookup"><span data-stu-id="0bff9-192">By default,</span></span>  |
|           |<span data-ttu-id="0bff9-193">zo</span><span class="sxs-lookup"><span data-stu-id="0bff9-193">powershell\*</span></span>   |<span data-ttu-id="0bff9-194">Power shell is de identiteit.</span><span class="sxs-lookup"><span data-stu-id="0bff9-194">powershell is the identity.</span></span> <span data-ttu-id="0bff9-195">Deze waarde kan worden</span><span class="sxs-lookup"><span data-stu-id="0bff9-195">This value can be</span></span>|
|           |              |<span data-ttu-id="0bff9-196">Hiermee wordt het verschil tussen twee</span><span class="sxs-lookup"><span data-stu-id="0bff9-196">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="0bff9-197">instanties van een Power shell-installatie, zoals</span><span class="sxs-lookup"><span data-stu-id="0bff9-197">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="0bff9-198">Als release-en bèta versie.</span><span class="sxs-lookup"><span data-stu-id="0bff9-198">as a release and beta version.</span></span> <span data-ttu-id="0bff9-199">Deze waarde is</span><span class="sxs-lookup"><span data-stu-id="0bff9-199">This value is</span></span> |
|           |              |<span data-ttu-id="0bff9-200">wordt ook gebruikt om de logboek uitvoer om te leiden naar een</span><span class="sxs-lookup"><span data-stu-id="0bff9-200">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="0bff9-201">afzonderlijk bestand op Linux.</span><span class="sxs-lookup"><span data-stu-id="0bff9-201">separate file on Linux.</span></span> <span data-ttu-id="0bff9-202">Zie de bespreking van</span><span class="sxs-lookup"><span data-stu-id="0bff9-202">See the discussion of</span></span>|
|           |              |<span data-ttu-id="0bff9-203">**rsyslog** hierboven.</span><span class="sxs-lookup"><span data-stu-id="0bff9-203">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="0bff9-204">Functioneren</span><span class="sxs-lookup"><span data-stu-id="0bff9-204">Operational\*</span></span>  |<span data-ttu-id="0bff9-205">De kanalen die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="0bff9-205">The channels to enable.</span></span> <span data-ttu-id="0bff9-206">De waarden scheiden</span><span class="sxs-lookup"><span data-stu-id="0bff9-206">Separate the values</span></span>|
|           |<span data-ttu-id="0bff9-207">Analytisch</span><span class="sxs-lookup"><span data-stu-id="0bff9-207">Analytic</span></span>      |<span data-ttu-id="0bff9-208">met een komma bij het opgeven van meer dan één.</span><span class="sxs-lookup"><span data-stu-id="0bff9-208">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="0bff9-209">Altijd</span><span class="sxs-lookup"><span data-stu-id="0bff9-209">Always</span></span>        |<span data-ttu-id="0bff9-210">Geef één waarde op.</span><span class="sxs-lookup"><span data-stu-id="0bff9-210">Specify a single value.</span></span> <span data-ttu-id="0bff9-211">De waarde kan</span><span class="sxs-lookup"><span data-stu-id="0bff9-211">The value enables</span></span>  |
|           |<span data-ttu-id="0bff9-212">Kritiek</span><span class="sxs-lookup"><span data-stu-id="0bff9-212">Critical</span></span>      |<span data-ttu-id="0bff9-213">zelf en alle waarden erboven in</span><span class="sxs-lookup"><span data-stu-id="0bff9-213">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="0bff9-214">Fout</span><span class="sxs-lookup"><span data-stu-id="0bff9-214">Error</span></span>         |<span data-ttu-id="0bff9-215">aan de linkerkant weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0bff9-215">list to the left.</span></span>                            |
|           |<span data-ttu-id="0bff9-216">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="0bff9-216">Warning</span></span>       |                                             |
|           |<span data-ttu-id="0bff9-217">Informatief</span><span class="sxs-lookup"><span data-stu-id="0bff9-217">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="0bff9-218">Uitgebreid</span><span class="sxs-lookup"><span data-stu-id="0bff9-218">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="0bff9-219">Fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="0bff9-219">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="0bff9-220">Runspace</span><span class="sxs-lookup"><span data-stu-id="0bff9-220">Runspace</span></span>      |<span data-ttu-id="0bff9-221">Tref woorden bieden de mogelijkheid om logboek registratie te beperken</span><span class="sxs-lookup"><span data-stu-id="0bff9-221">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="0bff9-222">Pijplijn</span><span class="sxs-lookup"><span data-stu-id="0bff9-222">Pipeline</span></span>      |<span data-ttu-id="0bff9-223">naar specifieke onderdelen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0bff9-223">to specific components within PowerShell.</span></span> <span data-ttu-id="0bff9-224">Door</span><span class="sxs-lookup"><span data-stu-id="0bff9-224">By</span></span> |
|           |<span data-ttu-id="0bff9-225">Protocol</span><span class="sxs-lookup"><span data-stu-id="0bff9-225">Protocol</span></span>      |<span data-ttu-id="0bff9-226">Standaard worden alle tref woorden ingeschakeld en gewijzigd</span><span class="sxs-lookup"><span data-stu-id="0bff9-226">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="0bff9-227">Transport</span><span class="sxs-lookup"><span data-stu-id="0bff9-227">Transport</span></span>     |<span data-ttu-id="0bff9-228">Deze waarde is alleen nuttig voor zeer</span><span class="sxs-lookup"><span data-stu-id="0bff9-228">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="0bff9-229">Host</span><span class="sxs-lookup"><span data-stu-id="0bff9-229">Host</span></span>          |<span data-ttu-id="0bff9-230">gespecialiseerde probleem oplossing.</span><span class="sxs-lookup"><span data-stu-id="0bff9-230">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="0bff9-231">Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0bff9-231">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="0bff9-232">Serializer</span><span class="sxs-lookup"><span data-stu-id="0bff9-232">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="0bff9-233">Sessie</span><span class="sxs-lookup"><span data-stu-id="0bff9-233">Session</span></span>       |                                             |
|           |<span data-ttu-id="0bff9-234">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="0bff9-234">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="0bff9-235">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0bff9-235">See also</span></span>

<span data-ttu-id="0bff9-236">Raadpleeg de lokale pagina's van de Linux-computer voor meer informatie over Linux **syslog** en **rsyslog. conf** . `man`</span><span class="sxs-lookup"><span data-stu-id="0bff9-236">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="0bff9-237">Raadpleeg [os_log Developer-documentatie](https://developer.apple.com/documentation/os/os_log)voor informatie over macOS **os_log** .</span><span class="sxs-lookup"><span data-stu-id="0bff9-237">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="0bff9-238">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="0bff9-238">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="0bff9-239">Algemene SIEM-integratie</span><span class="sxs-lookup"><span data-stu-id="0bff9-239">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
