---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: 695a13d4fbbf60caadeed994c1aa9c36432be917
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250832"
---
# <span data-ttu-id="7fa3e-103">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa3e-103">Clear-EventLog</span></span>

## <span data-ttu-id="7fa3e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7fa3e-104">SYNOPSIS</span></span>
<span data-ttu-id="7fa3e-105">Hiermee worden alle vermeldingen uit de opgegeven gebeurtenis logboeken op de lokale of externe computers gewist.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-105">Clears all entries from specified event logs on the local or remote computers.</span></span>

## <span data-ttu-id="7fa3e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7fa3e-106">SYNTAX</span></span>

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7fa3e-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7fa3e-107">DESCRIPTION</span></span>

<span data-ttu-id="7fa3e-108">Met de `Clear-EventLog` cmdlet worden alle vermeldingen uit de opgegeven gebeurtenis logboeken op de lokale computer of op externe computers verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-108">The `Clear-EventLog` cmdlet deletes all of the entries from the specified event logs on the local computer or on remote computers.</span></span>
<span data-ttu-id="7fa3e-109">Als u wilt gebruiken `Clear-EventLog` , moet u lid zijn van de groep Administrators op de desbetreffende computer.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-109">To use `Clear-EventLog`, you must be a member of the Administrators group on the affected computer.</span></span>

<span data-ttu-id="7fa3e-110">De cmdlets die het zelfstandig naam woord van het **gebeurtenissen logboek** bevatten (de Eventlog-cmdlets) werken alleen in klassieke gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-110">The cmdlets that contain the **EventLog** noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="7fa3e-111">Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows, gebruikt u de cmdlet Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="7fa3e-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7fa3e-112">EXAMPLES</span></span>

### <span data-ttu-id="7fa3e-113">Voor beeld 1: specifieke gebeurtenis logboek typen wissen van de lokale computer</span><span class="sxs-lookup"><span data-stu-id="7fa3e-113">Example 1: Clear specific event log types from the local computer</span></span>

```powershell
Clear-EventLog "Windows PowerShell"
```

<span data-ttu-id="7fa3e-114">Met deze opdracht worden de vermeldingen uit het gebeurtenis logboek van Windows Power shell op de lokale computer gewist.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-114">This command clears the entries from the Windows PowerShell event log on the local computer.</span></span>

### <span data-ttu-id="7fa3e-115">Voor beeld 2: specifieke meerdere logboek typen wissen van de lokale en externe computers</span><span class="sxs-lookup"><span data-stu-id="7fa3e-115">Example 2: Clear specific multiple log types from the local and remote computers</span></span>

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

<span data-ttu-id="7fa3e-116">Met deze opdracht worden alle vermeldingen in de logboeken Microsoft Office Diagnostics (ODiag) en Microsoft Office Sessions (OSession) op de lokale computer en de Server02 externe computer gewist.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-116">This command clears all of the entries in the Microsoft Office Diagnostics (ODiag) and Microsoft Office Sessions (OSession) logs on the local computer and the Server02 remote computer.</span></span>

### <span data-ttu-id="7fa3e-117">Voor beeld 3: alle logboeken op de opgegeven computers wissen vervolgens de lijst met gebeurtenis logboeken weer geven</span><span class="sxs-lookup"><span data-stu-id="7fa3e-117">Example 3: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
Clear-EventLog -LogName application, system -confirm
```

<span data-ttu-id="7fa3e-118">Met deze opdracht wordt u om bevestiging gevraagd voordat de vermeldingen in de opgegeven gebeurtenis logboeken worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-118">This command prompts you for confirmation before deleting the entries in the specified event logs.</span></span>

### <span data-ttu-id="7fa3e-119">Voor beeld 4: alle logboeken op de opgegeven computers wissen vervolgens de lijst met gebeurtenis logboeken weer geven</span><span class="sxs-lookup"><span data-stu-id="7fa3e-119">Example 4: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

<span data-ttu-id="7fa3e-120">Met deze functie worden alle gebeurtenis logboeken op de opgegeven computers gewist en wordt vervolgens de resulterende lijst met gebeurtenis logboeken weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-120">This function clears all event logs on the specified computers and then displays the resulting event log list.</span></span>

<span data-ttu-id="7fa3e-121">U ziet dat er een paar vermeldingen zijn toegevoegd aan de systeem-en beveiligings Logboeken nadat de logboeken zijn gewist, maar voordat ze werden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-121">Notice that a few entries were added to the System and Security logs after the logs were cleared but before they were displayed.</span></span>

## <span data-ttu-id="7fa3e-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fa3e-122">PARAMETERS</span></span>

### <span data-ttu-id="7fa3e-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7fa3e-123">-ComputerName</span></span>

<span data-ttu-id="7fa3e-124">Hiermee geeft u een externe computer.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-124">Specifies a remote computer.</span></span>
<span data-ttu-id="7fa3e-125">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-125">The default is the local computer.</span></span>

<span data-ttu-id="7fa3e-126">Typ de NetBIOS-naam, een Internet Protocol (IP)-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="7fa3e-127">Typ de computer naam, een punt (.) of ' localhost ' om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-127">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="7fa3e-128">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="7fa3e-129">U kunt de para meter **ComputerName** gebruiken `Get-EventLog` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-129">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7fa3e-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="7fa3e-130">-LogName</span></span>

<span data-ttu-id="7fa3e-131">Hiermee geeft u de gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-131">Specifies the event logs.</span></span>
<span data-ttu-id="7fa3e-132">Voer de naam van het logboek in (de waarde van de eigenschap log, niet de LogDisplayName) van een of meer gebeurtenis logboeken, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="7fa3e-133">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="7fa3e-134">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7fa3e-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7fa3e-135">-Confirm</span></span>

<span data-ttu-id="7fa3e-136">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7fa3e-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7fa3e-137">-WhatIf</span></span>

<span data-ttu-id="7fa3e-138">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-138">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7fa3e-139">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7fa3e-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fa3e-140">CommonParameters</span></span>

<span data-ttu-id="7fa3e-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fa3e-142">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-142">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7fa3e-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="7fa3e-143">INPUTS</span></span>

### <span data-ttu-id="7fa3e-144">Geen</span><span class="sxs-lookup"><span data-stu-id="7fa3e-144">None</span></span>

<span data-ttu-id="7fa3e-145">U kunt geen objecten pipeen naar `Clear-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="7fa3e-145">You cannot pipe objects to `Clear-EventLog`.</span></span>

## <span data-ttu-id="7fa3e-146">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7fa3e-146">OUTPUTS</span></span>

### <span data-ttu-id="7fa3e-147">Geen</span><span class="sxs-lookup"><span data-stu-id="7fa3e-147">None</span></span>

<span data-ttu-id="7fa3e-148">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-148">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7fa3e-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7fa3e-149">NOTES</span></span>

- <span data-ttu-id="7fa3e-150">Als u wilt gebruiken `Clear-EventLog` voor Windows Vista en latere versies van Windows, start u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7fa3e-150">To use `Clear-EventLog` on Windows Vista and later versions of Windows, start Windows PowerShell with the "Run as administrator" option.</span></span>

## <span data-ttu-id="7fa3e-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7fa3e-151">RELATED LINKS</span></span>

[<span data-ttu-id="7fa3e-152">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa3e-152">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="7fa3e-153">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa3e-153">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="7fa3e-154">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="7fa3e-154">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="7fa3e-155">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa3e-155">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="7fa3e-156">Weer geven-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa3e-156">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="7fa3e-157">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="7fa3e-157">Write-EventLog</span></span>](Write-EventLog.md)
