---
description: Power shell registreert interne bewerkingen van de engine, providers en cmdlets.
keywords: powershell
Locale: en-US
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging
ms.openlocfilehash: 5d061b38b5b0fa45cf0a86c2f5b7e0efcb8d1f7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252605"
---
# <a name="about-logging"></a><span data-ttu-id="69390-104">Over logboek registratie</span><span class="sxs-lookup"><span data-stu-id="69390-104">About Logging</span></span>

## <a name="short-description"></a><span data-ttu-id="69390-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="69390-105">Short description</span></span>

<span data-ttu-id="69390-106">Power shell registreert interne bewerkingen van de engine, providers en cmdlets.</span><span class="sxs-lookup"><span data-stu-id="69390-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="69390-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="69390-107">Long description</span></span>

<span data-ttu-id="69390-108">Power shell registreert gegevens over Power shell-bewerkingen, zoals het starten en stoppen van de engine en providers, en het uitvoeren van Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="69390-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="69390-109">Windows Power shell-versies 3,0, 4,0, 5,0 en 5,1 bevatten **Eventlog** -cmdlets voor de Windows-gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="69390-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="69390-110">In deze versies geeft u de lijst van het type **Eventlog** -cmdlets weer: `Get-Command -Noun EventLog` .</span><span class="sxs-lookup"><span data-stu-id="69390-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="69390-111">Raadpleeg de cmdlet-documentatie en-about_EventLogs voor uw versie van Windows Power shell voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="69390-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="69390-112">De logboek vermeldingen van het Power shell-logboek in Windows weer geven</span><span class="sxs-lookup"><span data-stu-id="69390-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="69390-113">Power shell-logboeken kunnen worden weer gegeven met behulp van de Windows-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="69390-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="69390-114">Het gebeurtenis logboek bevindt zich in de groep toepassings-en service logboeken en heeft de naam `Microsoft-Windows-PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="69390-114">The event log is located in the Application and Services Logs group and is named `Microsoft-Windows-PowerShell`.</span></span> <span data-ttu-id="69390-115">De gekoppelde ETW-provider `GUID` is `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}` .</span><span class="sxs-lookup"><span data-stu-id="69390-115">The associated ETW provider `GUID` is `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}`.</span></span>

<span data-ttu-id="69390-116">Wanneer de logboek registratie van script blokken is ingeschakeld, registreert Power shell de volgende gebeurtenissen in het `Microsoft-Windows-PowerShell/Operational` logboek:</span><span class="sxs-lookup"><span data-stu-id="69390-116">When Script Block Logging is enabled, PowerShell logs the following events to the `Microsoft-Windows-PowerShell/Operational` log:</span></span>

|<span data-ttu-id="69390-117">Veld</span><span class="sxs-lookup"><span data-stu-id="69390-117">Field</span></span>| <span data-ttu-id="69390-118">Waarde</span><span class="sxs-lookup"><span data-stu-id="69390-118">Value</span></span>|
|-|-|
|<span data-ttu-id="69390-119">Gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="69390-119">EventId</span></span>|`4104` / `0x1008`|
|<span data-ttu-id="69390-120">Kanaal</span><span class="sxs-lookup"><span data-stu-id="69390-120">Channel</span></span>|`Operational`|
|<span data-ttu-id="69390-121">Niveau</span><span class="sxs-lookup"><span data-stu-id="69390-121">Level</span></span>|`Verbose`|
|<span data-ttu-id="69390-122">Code</span><span class="sxs-lookup"><span data-stu-id="69390-122">Opcode</span></span>|`Create`|
|<span data-ttu-id="69390-123">Taak</span><span class="sxs-lookup"><span data-stu-id="69390-123">Task</span></span>|`CommandStart`|
|<span data-ttu-id="69390-124">Zoek</span><span class="sxs-lookup"><span data-stu-id="69390-124">Keyword</span></span>|`Runspace`|

## <a name="enabling-script-block-logging"></a><span data-ttu-id="69390-125">Logboek registratie van script blok inschakelen</span><span class="sxs-lookup"><span data-stu-id="69390-125">Enabling Script Block Logging</span></span>

<span data-ttu-id="69390-126">Wanneer u logboek registratie van script blokken inschakelt, registreert Power shell de inhoud van alle script blokken die worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="69390-126">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="69390-127">Wanneer deze functie is ingeschakeld, wordt deze informatie door een nieuwe Power shell-sessie geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="69390-127">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="69390-128">Het is raadzaam om beveiligde logboek registratie in te scha kelen, zoals hieronder wordt beschreven, wanneer script blok logboek registratie alleen voor diagnostische doel einden wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="69390-128">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="69390-129">Logboek registratie van script blokken kan worden ingeschakeld via groepsbeleid of een register instelling.</span><span class="sxs-lookup"><span data-stu-id="69390-129">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="69390-130">Met behulp van Groepsbeleid</span><span class="sxs-lookup"><span data-stu-id="69390-130">Using Group Policy</span></span>

<span data-ttu-id="69390-131">Als u automatische transcriptie wilt inschakelen, schakelt u de `Turn on PowerShell Script Block
Logging` functie in Groepsbeleid in `Administrative Templates -> Windows
Components -> Windows PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="69390-131">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="69390-132">Het REGI ster gebruiken</span><span class="sxs-lookup"><span data-stu-id="69390-132">Using the Registry</span></span>

<span data-ttu-id="69390-133">Voer de volgende functie uit:</span><span class="sxs-lookup"><span data-stu-id="69390-133">Run the following function:</span></span>

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a><span data-ttu-id="69390-134">Beveiligde logboek registratie</span><span class="sxs-lookup"><span data-stu-id="69390-134">Protected Event Logging</span></span>

<span data-ttu-id="69390-135">Het verhogen van het niveau van logboek registratie op een systeem verhoogt de kans dat geregistreerde inhoud gevoelige gegevens kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="69390-135">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="69390-136">Als bijvoorbeeld script logboek registratie is ingeschakeld, kunnen referenties of andere gevoelige gegevens die door een script worden gebruikt, naar het gebeurtenis logboek worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="69390-136">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="69390-137">Wanneer een computer met gevoelige gegevens is aangetast, kunnen de logboeken een aanvaller de benodigde informatie geven om hun bereik te verg Roten.</span><span class="sxs-lookup"><span data-stu-id="69390-137">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="69390-138">Voor het beveiligen van deze informatie introduceert Windows 10 beveiligde logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="69390-138">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="69390-139">Met logboek registratie van beveiligde gebeurtenissen kunnen deelnemende toepassingen gevoelige gegevens die naar het gebeurtenis logboek zijn geschreven, versleutelen.</span><span class="sxs-lookup"><span data-stu-id="69390-139">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="69390-140">Later kunt u deze logboeken ontsleutelen en verwerken op een veiligere en gecentraliseerde logboek verzamelaar.</span><span class="sxs-lookup"><span data-stu-id="69390-140">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="69390-141">De inhoud van het gebeurtenis logboek wordt beveiligd met de CMS-standaard (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="69390-141">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="69390-142">CMS maakt gebruik van open bare-sleutel cryptografie.</span><span class="sxs-lookup"><span data-stu-id="69390-142">CMS uses public key cryptography.</span></span> <span data-ttu-id="69390-143">De sleutels die worden gebruikt voor het versleutelen van inhoud en het ontsleutelen van inhoud worden gescheiden bewaard.</span><span class="sxs-lookup"><span data-stu-id="69390-143">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="69390-144">De open bare sleutel kan breed worden gedeeld en kan geen gevoelige gegevens zijn.</span><span class="sxs-lookup"><span data-stu-id="69390-144">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="69390-145">Alle inhoud die is versleuteld met deze open bare sleutel kan alleen worden ontsleuteld door de persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="69390-145">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="69390-146">Zie voor meer informatie over crypto grafie met open bare sleutels [Wikipedia-open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="69390-146">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="69390-147">Als u een beleid voor beveiligde logboek registratie wilt inschakelen, implementeert u een open bare sleutel voor alle computers met gebeurtenis logboek gegevens die moeten worden beveiligd.</span><span class="sxs-lookup"><span data-stu-id="69390-147">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="69390-148">De bijbehorende persoonlijke sleutel wordt gebruikt voor het verwerken van de gebeurtenis logboeken op een veiligere locatie, zoals een centrale gebeurtenis logboek verzamelaar of [Siem][] aggregator.</span><span class="sxs-lookup"><span data-stu-id="69390-148">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="69390-149">U kunt SIEM instellen in Azure.</span><span class="sxs-lookup"><span data-stu-id="69390-149">You can set up SIEM in Azure.</span></span> <span data-ttu-id="69390-150">Zie [algemene Siem-integratie](/cloud-app-security/siem)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="69390-150">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="69390-151">Beveiligde logboek registratie via groepsbeleid inschakelen</span><span class="sxs-lookup"><span data-stu-id="69390-151">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="69390-152">Als u beveiligde logboek registratie wilt inschakelen, schakelt u de `Enable Protected Event Logging` functie in Groepsbeleid in `Administrative Templates -> Windows Components
-> Event Logging` .</span><span class="sxs-lookup"><span data-stu-id="69390-152">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="69390-153">Voor deze instelling is een versleutelings certificaat vereist, dat u kunt opgeven in een van de volgende formulieren:</span><span class="sxs-lookup"><span data-stu-id="69390-153">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="69390-154">De inhoud van een base-64 Encoded X. 509-certificaat (bijvoorbeeld, zoals aangeboden door de `Export` optie in Certificate Manager).</span><span class="sxs-lookup"><span data-stu-id="69390-154">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="69390-155">De vinger afdruk van een certificaat dat kan worden gevonden in het certificaat archief van de lokale computer (kan worden geïmplementeerd door de PKI-infra structuur).</span><span class="sxs-lookup"><span data-stu-id="69390-155">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="69390-156">Het volledige pad naar een certificaat (kan lokaal of op een externe share zijn).</span><span class="sxs-lookup"><span data-stu-id="69390-156">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="69390-157">Het pad naar een map met een certificaat of certificaten (lokaal of op een externe share).</span><span class="sxs-lookup"><span data-stu-id="69390-157">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="69390-158">De onderwerpnaam van een certificaat dat kan worden gevonden in het certificaat archief van de lokale computer (kan worden geïmplementeerd door de PKI-infra structuur).</span><span class="sxs-lookup"><span data-stu-id="69390-158">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="69390-159">Het resulterende certificaat moet `Document Encryption` als Enhanced Key Usage ( `1.3.6.1.4.1.311.80.1` ) en `Data Encipherment` of `Key
Encipherment` sleutel gebruik zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="69390-159">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="69390-160">De persoonlijke sleutel mag niet worden geïmplementeerd op de computer registratie gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="69390-160">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="69390-161">Het moet worden bewaard op een veilige locatie waar u de berichten ontsleutelt.</span><span class="sxs-lookup"><span data-stu-id="69390-161">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="69390-162">Beveiligde gebeurtenis logboek registratie berichten decoderen</span><span class="sxs-lookup"><span data-stu-id="69390-162">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="69390-163">Het volgende script wordt opgehaald en ontsleuteld, ervan uitgaande dat u beschikt over de persoonlijke sleutel:</span><span class="sxs-lookup"><span data-stu-id="69390-163">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="69390-164">Zie ook</span><span class="sxs-lookup"><span data-stu-id="69390-164">See also</span></span>

[<span data-ttu-id="69390-165">Het blauwe team van Power shell</span><span class="sxs-lookup"><span data-stu-id="69390-165">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="69390-166">Algemene SIEM-integratie</span><span class="sxs-lookup"><span data-stu-id="69390-166">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
