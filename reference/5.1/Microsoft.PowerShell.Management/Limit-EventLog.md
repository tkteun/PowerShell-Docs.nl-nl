---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250609"
---
# <span data-ttu-id="13c53-103">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-103">Limit-EventLog</span></span>

## <span data-ttu-id="13c53-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="13c53-104">SYNOPSIS</span></span>
<span data-ttu-id="13c53-105">Hiermee stelt u de eigenschappen van het gebeurtenis logboek in die de grootte van het gebeurtenis logboek en de leeftijd van de vermeldingen beperken.</span><span class="sxs-lookup"><span data-stu-id="13c53-105">Sets the event log properties that limit the size of the event log and the age of its entries.</span></span>

## <span data-ttu-id="13c53-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="13c53-106">SYNTAX</span></span>

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="13c53-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="13c53-107">DESCRIPTION</span></span>
<span data-ttu-id="13c53-108">Met de cmdlet **Limit-Eventlog** wordt de maximale grootte van een klassiek gebeurtenis logboek ingesteld, hoe lang elke gebeurtenis moet worden bewaard en wat er gebeurt als het logboek de maximum grootte bereikt.</span><span class="sxs-lookup"><span data-stu-id="13c53-108">The **Limit-EventLog** cmdlet sets the maximum size of a classic event log, how long each event must be retained, and what happens when the log reaches its maximum size.</span></span>
<span data-ttu-id="13c53-109">U kunt deze gebruiken om de gebeurtenis logboeken op lokale of externe computers te beperken.</span><span class="sxs-lookup"><span data-stu-id="13c53-109">You can use it to limit the event logs on local or remote computers.</span></span>

<span data-ttu-id="13c53-110">De cmdlets die het zelfstandig naam woord van het gebeurtenissen logboek bevatten (de EventLog-cmdlets) werken alleen in klassieke gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="13c53-110">The cmdlets that contain the EventLog noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="13c53-111">Gebruik Get-Wine vent om gebeurtenissen op te halen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="13c53-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use Get-WinEvent.</span></span>

## <span data-ttu-id="13c53-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="13c53-112">EXAMPLES</span></span>

### <span data-ttu-id="13c53-113">Voor beeld 1: de grootte van een gebeurtenis logboek verg Roten</span><span class="sxs-lookup"><span data-stu-id="13c53-113">Example 1: Increase the size of an event log</span></span>

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

<span data-ttu-id="13c53-114">Met deze opdracht wordt de maximale grootte van het Windows Power shell-gebeurtenis logboek op de lokale computer verhoogd tot 20480 bytes (20 KB).</span><span class="sxs-lookup"><span data-stu-id="13c53-114">This command increases the maximum size of the Windows PowerShell event log on the local computer to 20480 bytes (20 KB).</span></span>

### <span data-ttu-id="13c53-115">Voor beeld 2: een gebeurtenis logboek voor een opgegeven duur bewaren</span><span class="sxs-lookup"><span data-stu-id="13c53-115">Example 2: Retain an event log for a specified duration</span></span>

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

<span data-ttu-id="13c53-116">Met deze opdracht zorgt u ervoor dat gebeurtenissen in het beveiligings logboek op de Server01-en Server02-computers ten minste 7 dagen worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="13c53-116">This command ensures that events in the Security log on the Server01 and Server02 computers are retained for at least 7 days.</span></span>

### <span data-ttu-id="13c53-117">Voor beeld 3: de overloop actie van alle gebeurtenis logboeken wijzigen</span><span class="sxs-lookup"><span data-stu-id="13c53-117">Example 3: Change the overflow action of all event logs</span></span>

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

<span data-ttu-id="13c53-118">In dit voor beeld wordt de overloop actie van alle gebeurtenis logboeken op de lokale computer gewijzigd in OverwriteOlder.</span><span class="sxs-lookup"><span data-stu-id="13c53-118">This example changes the overflow action of all event logs on the local computer to OverwriteOlder.</span></span>

<span data-ttu-id="13c53-119">Met de eerste opdracht worden de logboek namen van alle logboeken op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="13c53-119">The first command gets the log names of all of the logs on the local computer.</span></span>
<span data-ttu-id="13c53-120">Met de tweede opdracht wordt de overloop actie ingesteld.</span><span class="sxs-lookup"><span data-stu-id="13c53-120">The second command sets the overflow action.</span></span>
<span data-ttu-id="13c53-121">Met de derde opdracht worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="13c53-121">The third command displays the results.</span></span>

## <span data-ttu-id="13c53-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="13c53-122">PARAMETERS</span></span>

### <span data-ttu-id="13c53-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="13c53-123">-ComputerName</span></span>
<span data-ttu-id="13c53-124">Hiermee geeft u externe computers op.</span><span class="sxs-lookup"><span data-stu-id="13c53-124">Specifies remote computers.</span></span>
<span data-ttu-id="13c53-125">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="13c53-125">The default is the local computer.</span></span>

<span data-ttu-id="13c53-126">Typ de NetBIOS-naam, een Internet Protocol (IP-adres) of een Fully Qualified Domain Name (FQDN) van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="13c53-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="13c53-127">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="13c53-127">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="13c53-128">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="13c53-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="13c53-129">U kunt de para meter *ComputerName* van **Limit-Eventlog gebruiken,** zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="13c53-129">You can use the *ComputerName* parameter of **Limit-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13c53-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="13c53-130">-LogName</span></span>
<span data-ttu-id="13c53-131">Hiermee geeft u de gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="13c53-131">Specifies the event logs.</span></span>
<span data-ttu-id="13c53-132">Voer de naam van het logboek in (de waarde van de eigenschap log, niet de LogDisplayName) van een of meer gebeurtenis logboeken, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="13c53-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="13c53-133">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="13c53-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="13c53-134">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="13c53-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13c53-135">-MaximumSize</span><span class="sxs-lookup"><span data-stu-id="13c53-135">-MaximumSize</span></span>
<span data-ttu-id="13c53-136">Hiermee geeft u de maximale grootte van de gebeurtenis Logboeken in bytes.</span><span class="sxs-lookup"><span data-stu-id="13c53-136">Specifies the maximum size of the event logs in bytes.</span></span>
<span data-ttu-id="13c53-137">Voer een waarde in tussen 64 kB (KB) en 4 gigabyte (GB).</span><span class="sxs-lookup"><span data-stu-id="13c53-137">Enter a value between 64 kilobytes (KB) and 4 gigabytes (GB).</span></span>
<span data-ttu-id="13c53-138">De waarde moet deelbaar zijn door 64 KB (65536).</span><span class="sxs-lookup"><span data-stu-id="13c53-138">The value must be divisible by 64 KB (65536).</span></span>

<span data-ttu-id="13c53-139">Met deze para meter wordt de waarde van de eigenschap **MaximumKilobytes** van het object **System. Diagnostics. Eventlog** opgegeven dat een klassiek gebeurtenis logboek vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="13c53-139">This parameter specifies the value of the **MaximumKilobytes** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

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

### <span data-ttu-id="13c53-140">-OverflowAction</span><span class="sxs-lookup"><span data-stu-id="13c53-140">-OverflowAction</span></span>
<span data-ttu-id="13c53-141">Hiermee geeft u op wat er gebeurt als het gebeurtenis logboek de maximum grootte heeft bereikt.</span><span class="sxs-lookup"><span data-stu-id="13c53-141">Specifies what happens when the event log reaches its maximum size.</span></span>

<span data-ttu-id="13c53-142">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="13c53-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="13c53-143">DoNotOverwrite: bestaande vermeldingen worden bewaard en nieuwe vermeldingen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="13c53-143">DoNotOverwrite:  Existing entries are retained and new entries are discarded.</span></span>
- <span data-ttu-id="13c53-144">OverwriteAsNeeded: elke nieuwe vermelding overschrijft de oudste vermelding.</span><span class="sxs-lookup"><span data-stu-id="13c53-144">OverwriteAsNeeded:  Each new entry overwrites the oldest entry.</span></span>
- <span data-ttu-id="13c53-145">OverwriteOlder: nieuwe gebeurtenissen overschrijven gebeurtenissen die ouder zijn dan de waarde die is opgegeven door de eigenschap **MinimumRetentionDays** .</span><span class="sxs-lookup"><span data-stu-id="13c53-145">OverwriteOlder:  New events overwrite events older than the value specified by the **MinimumRetentionDays** property.</span></span> <span data-ttu-id="13c53-146">Als er geen gebeurtenissen ouder zijn dan opgegeven door de waarde van de eigenschap **MinimumRetentionDays** , worden nieuwe gebeurtenissen genegeerd.</span><span class="sxs-lookup"><span data-stu-id="13c53-146">If there are no events older than specified by the **MinimumRetentionDays** property value, new events are discarded.</span></span>

<span data-ttu-id="13c53-147">Met deze para meter wordt de waarde van de eigenschap **OverflowAction** van het object **System. Diagnostics. Eventlog** opgegeven dat een klassiek gebeurtenis logboek vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="13c53-147">This parameter specifies the value of the **OverflowAction** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13c53-148">-RetentionDays</span><span class="sxs-lookup"><span data-stu-id="13c53-148">-RetentionDays</span></span>
<span data-ttu-id="13c53-149">Hiermee geeft u het minimum aantal dagen op dat een gebeurtenis in het gebeurtenis logboek moet blijven.</span><span class="sxs-lookup"><span data-stu-id="13c53-149">Specifies the minimum number of days that an event must remain in the event log.</span></span>

<span data-ttu-id="13c53-150">Met deze para meter wordt de waarde van de eigenschap **MinimumRetentionDays** van het object **System. Diagnostics. Eventlog** opgegeven dat een klassiek gebeurtenis logboek vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="13c53-150">This parameter specifies the value of the **MinimumRetentionDays** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13c53-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="13c53-151">-Confirm</span></span>
<span data-ttu-id="13c53-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="13c53-152">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13c53-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="13c53-153">-WhatIf</span></span>
<span data-ttu-id="13c53-154">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="13c53-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="13c53-155">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="13c53-155">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13c53-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="13c53-156">CommonParameters</span></span>
<span data-ttu-id="13c53-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="13c53-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="13c53-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="13c53-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="13c53-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="13c53-159">INPUTS</span></span>

### <span data-ttu-id="13c53-160">Geen</span><span class="sxs-lookup"><span data-stu-id="13c53-160">None</span></span>
<span data-ttu-id="13c53-161">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="13c53-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="13c53-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="13c53-162">OUTPUTS</span></span>

### <span data-ttu-id="13c53-163">Geen</span><span class="sxs-lookup"><span data-stu-id="13c53-163">None</span></span>
<span data-ttu-id="13c53-164">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="13c53-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="13c53-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="13c53-165">NOTES</span></span>

* <span data-ttu-id="13c53-166">Als u deze cmdlet wilt gebruiken in Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="13c53-166">To use this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="13c53-167">Met deze cmdlet worden de eigenschappen van het object **System. Diagnostics. Eventlog** gewijzigd dat een klassiek gebeurtenis logboek vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="13c53-167">This cmdlet changes the properties of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>
<span data-ttu-id="13c53-168">Als u de huidige instellingen van de eigenschappen van het gebeurtenis logboek wilt zien, typt u `Get-EventLog -List` .</span><span class="sxs-lookup"><span data-stu-id="13c53-168">To see the current settings of the event log properties, type `Get-EventLog -List`.</span></span>

*

## <span data-ttu-id="13c53-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="13c53-169">RELATED LINKS</span></span>

[<span data-ttu-id="13c53-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="13c53-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="13c53-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="13c53-173">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="13c53-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="13c53-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="13c53-175">Weer geven-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="13c53-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="13c53-176">Write-EventLog</span></span>](Write-EventLog.md)
