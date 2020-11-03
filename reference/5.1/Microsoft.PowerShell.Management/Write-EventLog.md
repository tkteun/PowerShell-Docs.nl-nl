---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: cae34c4cf942d9aa4abb9a2d716ef9854f70de2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250517"
---
# <span data-ttu-id="31bb2-103">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-103">Write-EventLog</span></span>

## <span data-ttu-id="31bb2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="31bb2-104">SYNOPSIS</span></span>
<span data-ttu-id="31bb2-105">Hiermee wordt een gebeurtenis naar een gebeurtenis logboek geschreven.</span><span class="sxs-lookup"><span data-stu-id="31bb2-105">Writes an event to an event log.</span></span>

## <span data-ttu-id="31bb2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="31bb2-106">SYNTAX</span></span>

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## <span data-ttu-id="31bb2-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="31bb2-107">DESCRIPTION</span></span>
<span data-ttu-id="31bb2-108">Met de cmdlet **Write-Eventlog** wordt een gebeurtenis naar een gebeurtenis logboek geschreven.</span><span class="sxs-lookup"><span data-stu-id="31bb2-108">The **Write-EventLog** cmdlet writes an event to an event log.</span></span>

<span data-ttu-id="31bb2-109">Als u een gebeurtenis naar een gebeurtenis logboek wilt schrijven, moet het gebeurtenis logboek op de computer bestaan en moet de bron zijn geregistreerd voor het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="31bb2-109">To write an event to an event log, the event log must exist on the computer and the source must be registered for the event log.</span></span>

<span data-ttu-id="31bb2-110">De cmdlets die het zelfstandig naam woord van het **gebeurtenissen logboek** bevatten (de **Eventlog** -cmdlets) werken alleen in klassieke gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="31bb2-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="31bb2-111">Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van het Windows-besturings systeem, gebruikt u de cmdlet Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="31bb2-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="31bb2-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="31bb2-112">EXAMPLES</span></span>

### <span data-ttu-id="31bb2-113">Voor beeld 1: een gebeurtenis naar het gebeurtenis logboek van de toepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="31bb2-113">Example 1: Write an event to the Application event log</span></span>

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

<span data-ttu-id="31bb2-114">Met deze opdracht wordt een gebeurtenis van de Mijntoep-bron naar het toepassings gebeurtenis logboek geschreven.</span><span class="sxs-lookup"><span data-stu-id="31bb2-114">This command writes an event from the MyApp source to the Application event log.</span></span>

### <span data-ttu-id="31bb2-115">Voor beeld 2: een gebeurtenis schrijven naar het toepassings gebeurtenis logboek van een externe computer</span><span class="sxs-lookup"><span data-stu-id="31bb2-115">Example 2: Write an event to the Application event log of a remote computer</span></span>

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

<span data-ttu-id="31bb2-116">Met deze opdracht schrijft u een gebeurtenis van de Mijntoep-bron naar het toepassings gebeurtenis logboek op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="31bb2-116">This command writes an event from the MyApp source to the Application event log on the Server01 remote computer.</span></span>

## <span data-ttu-id="31bb2-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31bb2-117">PARAMETERS</span></span>

### <span data-ttu-id="31bb2-118">-Categorie</span><span class="sxs-lookup"><span data-stu-id="31bb2-118">-Category</span></span>
<span data-ttu-id="31bb2-119">Hiermee geeft u een taak categorie op voor de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="31bb2-119">Specifies a task category for the event.</span></span>
<span data-ttu-id="31bb2-120">Voer een geheel getal in dat is gekoppeld aan de teken reeksen in het categorie bericht bestand voor het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="31bb2-120">Enter an integer that is associated with the strings in the category message file for the event log.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-121">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="31bb2-121">-ComputerName</span></span>
<span data-ttu-id="31bb2-122">Hiermee geeft u een externe computer.</span><span class="sxs-lookup"><span data-stu-id="31bb2-122">Specifies a remote computer.</span></span>
<span data-ttu-id="31bb2-123">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="31bb2-123">The default is the local computer.</span></span>

<span data-ttu-id="31bb2-124">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="31bb2-124">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="31bb2-125">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="31bb2-125">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="31bb2-126">U kunt de para meter *ComputerName* van de cmdlet Get-EventLog ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="31bb2-126">You can use the *ComputerName* parameter of the Get-EventLog cmdlet even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-127">-Entry type is</span><span class="sxs-lookup"><span data-stu-id="31bb2-127">-EntryType</span></span>
<span data-ttu-id="31bb2-128">Hiermee geeft u het vermeldings type van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="31bb2-128">Specifies the entry type of the event.</span></span>
<span data-ttu-id="31bb2-129">De acceptabele waarden voor deze para meter zijn: fout, waarschuwing, informatie, SuccessAudit en FailureAudit.</span><span class="sxs-lookup"><span data-stu-id="31bb2-129">The acceptable values for this parameter are: Error, Warning, Information, SuccessAudit, and FailureAudit.</span></span>
<span data-ttu-id="31bb2-130">De standaard waarde is informatie.</span><span class="sxs-lookup"><span data-stu-id="31bb2-130">The default value is Information.</span></span>

<span data-ttu-id="31bb2-131">Zie [EventLogEntryType Enumeration](https://go.microsoft.com/fwlink/?LinkId=143599) in de MSDN-bibliotheek voor een beschrijving van de waarden.</span><span class="sxs-lookup"><span data-stu-id="31bb2-131">For a description of the values, see [EventLogEntryType Enumeration](https://go.microsoft.com/fwlink/?LinkId=143599) in the MSDN library.</span></span>

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-132">-Gebeurtenis-eigen</span><span class="sxs-lookup"><span data-stu-id="31bb2-132">-EventId</span></span>
<span data-ttu-id="31bb2-133">Hiermee geeft u de gebeurtenis-id op.</span><span class="sxs-lookup"><span data-stu-id="31bb2-133">Specifies the event identifier.</span></span>
<span data-ttu-id="31bb2-134">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="31bb2-134">This parameter is required.</span></span>
<span data-ttu-id="31bb2-135">De maximum waarde voor de *gebeurtenis* -para meter 65535.</span><span class="sxs-lookup"><span data-stu-id="31bb2-135">The maximum value for the *EventId* parameter is 65535.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-136">-LogName</span><span class="sxs-lookup"><span data-stu-id="31bb2-136">-LogName</span></span>
<span data-ttu-id="31bb2-137">Hiermee geeft u de naam op van het logboek waarnaar de gebeurtenis wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="31bb2-137">Specifies the name of the log to which the event is written.</span></span>
<span data-ttu-id="31bb2-138">Voer de naam van het logboek in.</span><span class="sxs-lookup"><span data-stu-id="31bb2-138">Enter the log name.</span></span>
<span data-ttu-id="31bb2-139">De logboek naam is de waarde van de eigenschap **logboek** , niet de **LogDisplayName**.</span><span class="sxs-lookup"><span data-stu-id="31bb2-139">The log name is the value of the **Log** property, not the **LogDisplayName**.</span></span>
<span data-ttu-id="31bb2-140">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="31bb2-140">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="31bb2-141">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="31bb2-141">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-142">-Bericht</span><span class="sxs-lookup"><span data-stu-id="31bb2-142">-Message</span></span>
<span data-ttu-id="31bb2-143">Hiermee geeft u het gebeurtenis bericht.</span><span class="sxs-lookup"><span data-stu-id="31bb2-143">Specifies the event message.</span></span>
<span data-ttu-id="31bb2-144">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="31bb2-144">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-145">-RawData</span><span class="sxs-lookup"><span data-stu-id="31bb2-145">-RawData</span></span>
<span data-ttu-id="31bb2-146">Hiermee geeft u de binaire gegevens in bytes op die zijn gekoppeld aan de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="31bb2-146">Specifies the binary data that is associated with the event, in bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-147">-Source</span><span class="sxs-lookup"><span data-stu-id="31bb2-147">-Source</span></span>
<span data-ttu-id="31bb2-148">Hiermee geeft u de bron van de gebeurtenis, meestal de naam van de toepassing die de gebeurtenis naar het logboek schrijft.</span><span class="sxs-lookup"><span data-stu-id="31bb2-148">Specifies the event source, which is typically the name of the application that is writing the event to the log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31bb2-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31bb2-149">CommonParameters</span></span>
<span data-ttu-id="31bb2-150">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31bb2-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31bb2-151">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="31bb2-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31bb2-152">INVOER</span><span class="sxs-lookup"><span data-stu-id="31bb2-152">INPUTS</span></span>

### <span data-ttu-id="31bb2-153">Geen</span><span class="sxs-lookup"><span data-stu-id="31bb2-153">None</span></span>
<span data-ttu-id="31bb2-154">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31bb2-154">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="31bb2-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="31bb2-155">OUTPUTS</span></span>

### <span data-ttu-id="31bb2-156">System. Diagnostics. EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="31bb2-156">System.Diagnostics.EventLogEntry</span></span>
<span data-ttu-id="31bb2-157">Deze cmdlet retourneert objecten die de gebeurtenissen in de logboeken vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="31bb2-157">This cmdlet returns objects that represents the events in the logs.</span></span>

## <span data-ttu-id="31bb2-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="31bb2-158">NOTES</span></span>

* <span data-ttu-id="31bb2-159">Als u **Write-Eventlog** wilt gebruiken, start u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="31bb2-159">To use **Write-EventLog** , start Windows PowerShell by using the Run as administrator option.</span></span>

*

## <span data-ttu-id="31bb2-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="31bb2-160">RELATED LINKS</span></span>

[<span data-ttu-id="31bb2-161">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-161">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="31bb2-162">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-162">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="31bb2-163">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-163">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="31bb2-164">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="31bb2-164">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="31bb2-165">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-165">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="31bb2-166">Weer geven-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-166">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="31bb2-167">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="31bb2-167">Write-EventLog</span></span>](Write-EventLog.md)
