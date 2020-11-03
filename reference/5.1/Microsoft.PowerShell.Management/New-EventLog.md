---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250598"
---
# <span data-ttu-id="87a2f-103">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-103">New-EventLog</span></span>

## <span data-ttu-id="87a2f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="87a2f-104">SYNOPSIS</span></span>
<span data-ttu-id="87a2f-105">Hiermee maakt u een nieuw gebeurtenis logboek en een nieuwe gebeurtenis bron op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="87a2f-105">Creates a new event log and a new event source on a local or remote computer.</span></span>

## <span data-ttu-id="87a2f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="87a2f-106">SYNTAX</span></span>

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## <span data-ttu-id="87a2f-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="87a2f-107">DESCRIPTION</span></span>

<span data-ttu-id="87a2f-108">Met deze cmdlet maakt u een nieuw klassiek gebeurtenis logboek op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="87a2f-108">This cmdlet creates a new classic event log on a local or remote computer.</span></span> <span data-ttu-id="87a2f-109">Het kan ook een gebeurtenis bron registreren die naar het nieuwe logboek of naar een bestaand logboek schrijft.</span><span class="sxs-lookup"><span data-stu-id="87a2f-109">It can also register an event source that writes to the new log or to an existing log.</span></span>

<span data-ttu-id="87a2f-110">De cmdlets die het zelfstandig naam woord van het gebeurtenissen logboek bevatten (de gebeurtenis logboek-cmdlets) werken alleen in klassieke gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="87a2f-110">The cmdlets that contain the EventLog noun (the Event log cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="87a2f-111">Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows, gebruikt u `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="87a2f-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use `Get-WinEvent`.</span></span>

## <span data-ttu-id="87a2f-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="87a2f-112">EXAMPLES</span></span>

### <span data-ttu-id="87a2f-113">Voor beeld 1: een nieuw gebeurtenis logboek maken</span><span class="sxs-lookup"><span data-stu-id="87a2f-113">Example 1 - create a new event log</span></span>

<span data-ttu-id="87a2f-114">Met deze opdracht wordt het TestLog-gebeurtenis logboek op de lokale computer gemaakt en wordt er een nieuwe bron voor geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="87a2f-114">This command creates the TestLog event log on the local computer and registers a new source for it.</span></span>

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### <span data-ttu-id="87a2f-115">Voor beeld 2: een nieuwe gebeurtenis bron aan een bestaand logboek toevoegen</span><span class="sxs-lookup"><span data-stu-id="87a2f-115">Example 2 - add a new event source to an existing log</span></span>

<span data-ttu-id="87a2f-116">Met deze opdracht wordt een nieuwe gebeurtenis bron, NewTestApp, toegevoegd aan het toepassings logboek op de externe computer met Server01.</span><span class="sxs-lookup"><span data-stu-id="87a2f-116">This command adds a new event source, NewTestApp, to the Application log on the Server01 remote computer.</span></span>

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

<span data-ttu-id="87a2f-117">Voor de opdracht is vereist dat het NewTestApp.dll-bestand zich op de Server01-computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="87a2f-117">The command requires that the NewTestApp.dll file is located on the Server01 computer.</span></span>

## <span data-ttu-id="87a2f-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87a2f-118">PARAMETERS</span></span>

### <span data-ttu-id="87a2f-119">-CategoryResourceFile</span><span class="sxs-lookup"><span data-stu-id="87a2f-119">-CategoryResourceFile</span></span>

<span data-ttu-id="87a2f-120">Hiermee geeft u het pad naar het bestand met categorie teken reeksen voor de bron gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="87a2f-120">Specifies the path to the file that contains category strings for the source events.</span></span> <span data-ttu-id="87a2f-121">Dit bestand wordt ook wel het categorie bericht bestand genoemd.</span><span class="sxs-lookup"><span data-stu-id="87a2f-121">This file is also known as the Category Message File.</span></span>

<span data-ttu-id="87a2f-122">Het bestand moet aanwezig zijn op de computer waarop het gebeurtenis logboek wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="87a2f-122">The file must be present on the computer on which the event log is being created.</span></span> <span data-ttu-id="87a2f-123">Met deze para meter worden geen bestanden gemaakt of verplaatst.</span><span class="sxs-lookup"><span data-stu-id="87a2f-123">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a2f-124">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="87a2f-124">-ComputerName</span></span>

<span data-ttu-id="87a2f-125">Maakt de nieuwe gebeurtenis logboeken op de opgegeven computers.</span><span class="sxs-lookup"><span data-stu-id="87a2f-125">Creates the new event logs on the specified computers.</span></span> <span data-ttu-id="87a2f-126">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="87a2f-126">The default is the local computer.</span></span>

<span data-ttu-id="87a2f-127">De NetBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="87a2f-127">The NetBIOS name, IP address, or fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="87a2f-128">Typ de computer naam, een punt (.) of ' localhost ' om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="87a2f-128">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="87a2f-129">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="87a2f-129">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="87a2f-130">U kunt de para meter **ComputerName** gebruiken `Get-EventLog` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="87a2f-130">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a2f-131">-LogName</span><span class="sxs-lookup"><span data-stu-id="87a2f-131">-LogName</span></span>

<span data-ttu-id="87a2f-132">Hiermee geeft u de naam van het gebeurtenis logboek op.</span><span class="sxs-lookup"><span data-stu-id="87a2f-132">Specifies the name of the event log.</span></span>

<span data-ttu-id="87a2f-133">Als het logboek niet bestaat, `New-EventLog` wordt het logboek gemaakt en wordt deze waarde gebruikt voor de eigenschappen **log** en **LogDisplayName** van het nieuwe gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="87a2f-133">If the log does not exist, `New-EventLog` creates the log and uses this value for the **Log** and **LogDisplayName** properties of the new event log.</span></span> <span data-ttu-id="87a2f-134">Als het logboek bestaat, `New-EventLog` registreert een nieuwe bron voor het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="87a2f-134">If the log exists, `New-EventLog` registers a new source for the event log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a2f-135">-MessageResourceFile</span><span class="sxs-lookup"><span data-stu-id="87a2f-135">-MessageResourceFile</span></span>

<span data-ttu-id="87a2f-136">Hiermee geeft u het pad naar het bestand met teken reeksen voor bericht opmaak voor de bron gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="87a2f-136">Specifies the path to the file that contains message formatting strings for the source events.</span></span>
<span data-ttu-id="87a2f-137">Dit bestand wordt ook wel het gebeurtenis bericht bestand genoemd.</span><span class="sxs-lookup"><span data-stu-id="87a2f-137">This file is also known as the Event Message File.</span></span>

<span data-ttu-id="87a2f-138">Het bestand moet aanwezig zijn op de computer waarop het gebeurtenis logboek wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="87a2f-138">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="87a2f-139">Met deze para meter worden geen bestanden gemaakt of verplaatst.</span><span class="sxs-lookup"><span data-stu-id="87a2f-139">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a2f-140">-ParameterResourceFile</span><span class="sxs-lookup"><span data-stu-id="87a2f-140">-ParameterResourceFile</span></span>

<span data-ttu-id="87a2f-141">Hiermee geeft u het pad op naar het bestand met teken reeksen die worden gebruikt voor het vervangen van para meters in gebeurtenis beschrijvingen.</span><span class="sxs-lookup"><span data-stu-id="87a2f-141">Specifies the path to the file that contains strings used for parameter substitutions in event descriptions.</span></span> <span data-ttu-id="87a2f-142">Dit bestand wordt ook wel het parameter bericht bestand genoemd.</span><span class="sxs-lookup"><span data-stu-id="87a2f-142">This file is also known as the Parameter Message File.</span></span>

<span data-ttu-id="87a2f-143">Het bestand moet aanwezig zijn op de computer waarop het gebeurtenis logboek wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="87a2f-143">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="87a2f-144">Met deze para meter worden geen bestanden gemaakt of verplaatst.</span><span class="sxs-lookup"><span data-stu-id="87a2f-144">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a2f-145">-Source</span><span class="sxs-lookup"><span data-stu-id="87a2f-145">-Source</span></span>

<span data-ttu-id="87a2f-146">Hiermee geeft u de namen van de gebeurtenis logboek bronnen, zoals toepassings Programma's die naar het gebeurtenis logboek schrijven.</span><span class="sxs-lookup"><span data-stu-id="87a2f-146">Specifies the names of the event log sources, such as application programs that write to the event log.</span></span> <span data-ttu-id="87a2f-147">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="87a2f-147">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87a2f-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87a2f-148">CommonParameters</span></span>

<span data-ttu-id="87a2f-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="87a2f-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87a2f-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="87a2f-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="87a2f-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="87a2f-151">INPUTS</span></span>

### <span data-ttu-id="87a2f-152">Geen</span><span class="sxs-lookup"><span data-stu-id="87a2f-152">None</span></span>

<span data-ttu-id="87a2f-153">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="87a2f-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="87a2f-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="87a2f-154">OUTPUTS</span></span>

### <span data-ttu-id="87a2f-155">System. Diagnostics. EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="87a2f-155">System.Diagnostics.EventLogEntry</span></span>

## <span data-ttu-id="87a2f-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="87a2f-156">NOTES</span></span>

<span data-ttu-id="87a2f-157">Als u wilt gebruiken `New-EventLog` voor Windows Vista en latere versies van Windows, opent u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="87a2f-157">To use `New-EventLog` on Windows Vista and later versions of Windows, open PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="87a2f-158">Als u een gebeurtenis bron wilt maken in Windows Vista, Windows XP Professional of Windows Server 2003, moet u lid zijn van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="87a2f-158">To create an event source in Windows Vista, Windows XP Professional, or Windows Server 2003, you must be a member of the Administrators group on the computer.</span></span>

<span data-ttu-id="87a2f-159">Wanneer u een nieuw gebeurtenis logboek en een nieuwe gebeurtenis bron maakt, registreert het systeem de nieuwe bron voor het nieuwe logboek, maar wordt het logboek niet gemaakt totdat de eerste vermelding naar het bestand wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="87a2f-159">When you create a new event log and a new event source, the system registers the new source for the new log, but the log is not created until the first entry is written to it.</span></span>

<span data-ttu-id="87a2f-160">Het besturings systeem slaat gebeurtenis logboeken op als bestanden.</span><span class="sxs-lookup"><span data-stu-id="87a2f-160">The operating system stores event logs as files.</span></span>

<span data-ttu-id="87a2f-161">Wanneer u een nieuw gebeurtenis logboek maakt, wordt het bijbehorende bestand opgeslagen in de `$env:SystemRoot\System32\Config` map op de opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="87a2f-161">When you create a new event log, the associated file is stored in the `$env:SystemRoot\System32\Config` directory on the specified computer.</span></span>

<span data-ttu-id="87a2f-162">De bestands naam is de eerste acht tekens van de **logboek** eigenschap met de bestandsnaam extensie. evt.</span><span class="sxs-lookup"><span data-stu-id="87a2f-162">The file name is the first eight characters of the **Log** property with an .evt file name extension.</span></span>

## <span data-ttu-id="87a2f-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="87a2f-163">RELATED LINKS</span></span>

[<span data-ttu-id="87a2f-164">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-164">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="87a2f-165">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-165">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="87a2f-166">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="87a2f-166">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="87a2f-167">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-167">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="87a2f-168">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="87a2f-168">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="87a2f-169">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-169">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="87a2f-170">Weer geven-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-170">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="87a2f-171">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="87a2f-171">Write-EventLog</span></span>](Write-EventLog.md)
