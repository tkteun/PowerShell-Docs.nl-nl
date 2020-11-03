---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250582"
---
# <span data-ttu-id="22045-103">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-103">Remove-EventLog</span></span>

## <span data-ttu-id="22045-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="22045-104">SYNOPSIS</span></span>
<span data-ttu-id="22045-105">Hiermee verwijdert u een gebeurtenis logboek of maakt u de registratie van een gebeurtenis bron ongedaan.</span><span class="sxs-lookup"><span data-stu-id="22045-105">Deletes an event log or unregisters an event source.</span></span>

## <span data-ttu-id="22045-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="22045-106">SYNTAX</span></span>

### <span data-ttu-id="22045-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="22045-107">Default (Default)</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="22045-108">Bron</span><span class="sxs-lookup"><span data-stu-id="22045-108">Source</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="22045-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="22045-109">DESCRIPTION</span></span>
<span data-ttu-id="22045-110">De cmdlet **Remove-Eventlog** verwijdert een gebeurtenis logboek bestand van een lokale of externe computer en maakt de registratie van alle gebeurtenis bronnen voor het logboek ongedaan.</span><span class="sxs-lookup"><span data-stu-id="22045-110">The **Remove-EventLog** cmdlet deletes an event log file from a local or remote computer and unregisters all its event sources for the log.</span></span>
<span data-ttu-id="22045-111">U kunt deze cmdlet ook gebruiken voor het opheffen van de registratie van gebeurtenis bronnen zonder gebeurtenis logboeken te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="22045-111">You can also use this cmdlet to unregister event sources without deleting any event logs.</span></span>

<span data-ttu-id="22045-112">De cmdlets die de zelfstandig naam van het **gebeurtenis logboek** bevatten, de **Eventlog** -cmdlets, werken alleen in klassieke gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="22045-112">The cmdlets that contain the **EventLog** noun, the **EventLog** cmdlets, work only on classic event logs.</span></span>
<span data-ttu-id="22045-113">Gebruik Get-Wine vent om gebeurtenissen op te halen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="22045-113">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use Get-WinEvent.</span></span>

<span data-ttu-id="22045-114">Let op: met deze cmdlet kunnen gebeurtenis logboeken van het besturings systeem worden verwijderd. Dit kan leiden tot toepassings fouten en onverwacht gedrag van het systeem.</span><span class="sxs-lookup"><span data-stu-id="22045-114">CAUTION: This cmdlet can delete operating system event logs, which might cause application failures and unexpected system behavior.</span></span>

## <span data-ttu-id="22045-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="22045-115">EXAMPLES</span></span>

### <span data-ttu-id="22045-116">Voor beeld 1: een gebeurtenis logboek van de lokale computer verwijderen</span><span class="sxs-lookup"><span data-stu-id="22045-116">Example 1: Remove an event log from the local computer</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

<span data-ttu-id="22045-117">Met deze opdracht wordt het MyLog-gebeurtenis logboek van de lokale computer verwijderd en worden de registratie van de gebeurtenis bronnen ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="22045-117">This command deletes the MyLog event log from the local computer and unregisters its event sources.</span></span>

### <span data-ttu-id="22045-118">Voor beeld 2: een gebeurtenis logboek van verschillende computers verwijderen</span><span class="sxs-lookup"><span data-stu-id="22045-118">Example 2: Remove an event log from several computers</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="22045-119">Met deze opdracht worden de gebeurtenis logboeken MyLog en TestLog van de lokale computer en de externe computers Server01 en Server02 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="22045-119">This command deletes the MyLog and TestLog event logs from the local computer and the Server01 and Server02 remote computers.</span></span>
<span data-ttu-id="22045-120">Met deze opdracht wordt ook de registratie van de gebeurtenis bronnen voor deze logboeken ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="22045-120">The command also unregisters the event sources for these logs.</span></span>

### <span data-ttu-id="22045-121">Voor beeld 3: een gebeurtenis bron verwijderen</span><span class="sxs-lookup"><span data-stu-id="22045-121">Example 3: Delete an event source</span></span>

```
PS C:\> Remove-EventLog -Source "MyApp"
```

<span data-ttu-id="22045-122">Met deze opdracht wordt de gebeurtenis bron MyApp verwijderd uit de logboeken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="22045-122">This command deletes the MyApp event source from the logs on the local computer.</span></span>
<span data-ttu-id="22045-123">Wanneer de opdracht is voltooid, kan het programma Mijntoep niet schrijven naar gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="22045-123">When the command finishes, the MyApp program cannot write to any event logs.</span></span>

### <span data-ttu-id="22045-124">Voor beeld 4: een gebeurtenis logboek verwijderen en de actie bevestigen</span><span class="sxs-lookup"><span data-stu-id="22045-124">Example 4: Remove an event log and confirm the action</span></span>

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

<span data-ttu-id="22045-125">Deze opdrachten laten zien hoe u de gebeurtenis logboeken op een computer kunt weer geven en kunt controleren of de opdracht **Remove-Eventlog** is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="22045-125">These commands show how to list the event logs on a computer and verify that a **Remove-EventLog** command was successful.</span></span>

### <span data-ttu-id="22045-126">Voor beeld 5: een gebeurtenis bron verwijderen en de actie bevestigen</span><span class="sxs-lookup"><span data-stu-id="22045-126">Example 5: Remove an event source and confirm the action</span></span>

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

<span data-ttu-id="22045-127">Deze opdrachten gebruiken de cmdlet Get-WmiObject om de gebeurtenis bronnen op de lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22045-127">These commands use the Get-WmiObject cmdlet to list the event sources on the local computer.</span></span>
<span data-ttu-id="22045-128">U kunt deze opdrachten om het succes van een opdracht te controleren of om een gebeurtenis bron te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="22045-128">You can these commands to verify the success of a command or to delete an event source.</span></span>

<span data-ttu-id="22045-129">Met de eerste opdracht worden de gebeurtenis bronnen van het TestLog-gebeurtenis logboek op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22045-129">The first command gets the event sources of the TestLog event log on the local computer.</span></span>
<span data-ttu-id="22045-130">MyApp is een van de bronnen.</span><span class="sxs-lookup"><span data-stu-id="22045-130">MyApp is one of the sources.</span></span>

<span data-ttu-id="22045-131">De tweede opdracht maakt gebruik van de para meter *Source* van **Remove-Eventlog** om de gebeurtenis bron MyApp te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="22045-131">The second command uses the *Source* parameter of **Remove-EventLog** to delete the MyApp event source.</span></span>

<span data-ttu-id="22045-132">De derde opdracht is identiek aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="22045-132">The third command is identical to the first.</span></span>
<span data-ttu-id="22045-133">U ziet dat de gebeurtenis bron MyApp is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="22045-133">It shows that the MyApp event source was deleted.</span></span>

## <span data-ttu-id="22045-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="22045-134">PARAMETERS</span></span>

### <span data-ttu-id="22045-135">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="22045-135">-ComputerName</span></span>
<span data-ttu-id="22045-136">Hiermee geeft u een externe computer.</span><span class="sxs-lookup"><span data-stu-id="22045-136">Specifies a remote computer.</span></span>
<span data-ttu-id="22045-137">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="22045-137">The default is the local computer.</span></span>

<span data-ttu-id="22045-138">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="22045-138">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="22045-139">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="22045-139">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="22045-140">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="22045-140">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="22045-141">U kunt de para meter *ComputerName* van **Remove-Eventlog gebruiken,** zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="22045-141">You can use the *ComputerName* parameter of **Remove-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22045-142">-LogName</span><span class="sxs-lookup"><span data-stu-id="22045-142">-LogName</span></span>
<span data-ttu-id="22045-143">Hiermee geeft u de gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="22045-143">Specifies the event logs.</span></span>
<span data-ttu-id="22045-144">Voer de logboek naam in van een of meer gebeurtenis logboeken, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="22045-144">Enter the log name of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="22045-145">De logboek naam is de waarde van de eigenschap **logboek** , niet de *LogDisplayName*. joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="22045-145">The log name is the value of the **Log** property, not the *LogDisplayName* , Wildcard characters are not permitted.</span></span>
<span data-ttu-id="22045-146">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="22045-146">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22045-147">-Source</span><span class="sxs-lookup"><span data-stu-id="22045-147">-Source</span></span>
<span data-ttu-id="22045-148">Hiermee geeft u de gebeurtenis bronnen op die met deze cmdlet worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="22045-148">Specifies the event sources that this cmdlet unregisters.</span></span>
<span data-ttu-id="22045-149">Voer de bron namen in, niet de naam van het uitvoer bare bestand, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="22045-149">Enter the source names, not the executable name, separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22045-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="22045-150">-Confirm</span></span>
<span data-ttu-id="22045-151">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22045-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="22045-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="22045-152">-WhatIf</span></span>
<span data-ttu-id="22045-153">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="22045-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="22045-154">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="22045-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="22045-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22045-155">CommonParameters</span></span>
<span data-ttu-id="22045-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="22045-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22045-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22045-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="22045-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="22045-158">INPUTS</span></span>

### <span data-ttu-id="22045-159">Geen</span><span class="sxs-lookup"><span data-stu-id="22045-159">None</span></span>
<span data-ttu-id="22045-160">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22045-160">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="22045-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="22045-161">OUTPUTS</span></span>

### <span data-ttu-id="22045-162">Geen</span><span class="sxs-lookup"><span data-stu-id="22045-162">None</span></span>
<span data-ttu-id="22045-163">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="22045-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="22045-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="22045-164">NOTES</span></span>

* <span data-ttu-id="22045-165">Als u **Remove-Eventlog** wilt gebruiken in Windows Vista en latere versies van het Windows-besturings systeem, start u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="22045-165">To use **Remove-EventLog** on Windows Vista and later versions of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

  <span data-ttu-id="22045-166">Als u een gebeurtenis logboek verwijdert en vervolgens het logboek opnieuw maakt, kunt u niet dezelfde gebeurtenis bronnen registreren.</span><span class="sxs-lookup"><span data-stu-id="22045-166">If you remove an event log and then re-create the log, you will not be able to register the same event sources.</span></span>
<span data-ttu-id="22045-167">Toepassingen die de gebeurtenis bronnen hebben gebruikt om vermeldingen naar het oorspronkelijke logboek te schrijven, kunnen niet naar het nieuwe logboek schrijven.</span><span class="sxs-lookup"><span data-stu-id="22045-167">Applications that used the events sources to write entries to the original log will not be able to write to the new log.</span></span>

* <span data-ttu-id="22045-168">Wanneer u de registratie van een gebeurtenis bron voor een bepaald logboek ongedaan maakt, kan de gebeurtenis bron mogelijk geen vermeldingen in andere gebeurtenis logboeken schrijven.</span><span class="sxs-lookup"><span data-stu-id="22045-168">When you unregister an event source for a particular log, the event source might be prevented from writing entries in other event logs.</span></span>

## <span data-ttu-id="22045-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="22045-169">RELATED LINKS</span></span>

[<span data-ttu-id="22045-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="22045-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="22045-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="22045-173">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="22045-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="22045-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="22045-175">Weer geven-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="22045-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="22045-176">Write-EventLog</span></span>](Write-EventLog.md)
