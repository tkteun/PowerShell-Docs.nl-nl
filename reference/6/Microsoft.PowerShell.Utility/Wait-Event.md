---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: 8384cf6a4922bf408f4ac569f651c1a3b584d8af
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250944"
---
# <span data-ttu-id="b94e9-103">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="b94e9-103">Wait-Event</span></span>

## <span data-ttu-id="b94e9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b94e9-104">SYNOPSIS</span></span>
<span data-ttu-id="b94e9-105">Er wordt gewacht tot een bepaalde gebeurtenis is opgetreden voordat de uitvoering wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="b94e9-105">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="b94e9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b94e9-106">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="b94e9-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b94e9-107">DESCRIPTION</span></span>

<span data-ttu-id="b94e9-108">De `Wait-Event` cmdlet onderbreekt de uitvoering van een script of functie totdat een bepaalde gebeurtenis wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b94e9-108">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="b94e9-109">De uitvoering wordt hervat wanneer de gebeurtenis wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="b94e9-109">Execution resumes when the event is detected.</span></span> <span data-ttu-id="b94e9-110">U annuleert het wachten door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="b94e9-110">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="b94e9-111">Deze functie biedt een alternatief voor het opvragen van een gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b94e9-111">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="b94e9-112">Daarnaast kunt u het antwoord op twee verschillende manieren bepalen voor een gebeurtenis:</span><span class="sxs-lookup"><span data-stu-id="b94e9-112">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="b94e9-113">de **actie** parameter van het gebeurtenis abonnement gebruiken</span><span class="sxs-lookup"><span data-stu-id="b94e9-113">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="b94e9-114">wachten tot een gebeurtenis is geretourneerd en vervolgens reageert met een actie</span><span class="sxs-lookup"><span data-stu-id="b94e9-114">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="b94e9-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b94e9-115">EXAMPLES</span></span>

### <span data-ttu-id="b94e9-116">Voor beeld 1: wachten op de volgende gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b94e9-116">Example 1: Wait for the next event</span></span>

<span data-ttu-id="b94e9-117">In dit voor beeld wordt gewacht op de volgende gebeurtenis die optreedt.</span><span class="sxs-lookup"><span data-stu-id="b94e9-117">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="b94e9-118">Voor beeld 2: wachten op een gebeurtenis met een opgegeven bron-id</span><span class="sxs-lookup"><span data-stu-id="b94e9-118">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="b94e9-119">In dit voor beeld wordt gewacht op de volgende gebeurtenis die optreedt en die een bron-id van ProcessStarted heeft.</span><span class="sxs-lookup"><span data-stu-id="b94e9-119">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="b94e9-120">Voor beeld 3: wachten op gebeurtenis die is verstreken met een timer</span><span class="sxs-lookup"><span data-stu-id="b94e9-120">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="b94e9-121">In dit voor beeld wordt de `Wait-Event` cmdlet gebruikt om te wachten op een timer gebeurtenis in een timer die is ingesteld op 2000 milliseconden.</span><span class="sxs-lookup"><span data-stu-id="b94e9-121">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### <span data-ttu-id="b94e9-122">Voor beeld 4: wachten op een gebeurtenis na een opgegeven time-out</span><span class="sxs-lookup"><span data-stu-id="b94e9-122">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="b94e9-123">In dit voor beeld wordt 90 seconden gewacht op de volgende gebeurtenis die optreedt en die een bron-id van **ProcessStarted** heeft.</span><span class="sxs-lookup"><span data-stu-id="b94e9-123">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted**.</span></span> <span data-ttu-id="b94e9-124">Als de opgegeven tijd verloopt, wordt het wachten beëindigd.</span><span class="sxs-lookup"><span data-stu-id="b94e9-124">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="b94e9-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b94e9-125">PARAMETERS</span></span>

### <span data-ttu-id="b94e9-126">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="b94e9-126">-SourceIdentifier</span></span>

<span data-ttu-id="b94e9-127">Hiermee geeft u de bron-id op die met deze cmdlet wordt gewacht op gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="b94e9-127">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="b94e9-128">Standaard wordt `Wait-Event` gewacht op een gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b94e9-128">By default, `Wait-Event` waits for any event.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b94e9-129">-Time-out</span><span class="sxs-lookup"><span data-stu-id="b94e9-129">-Timeout</span></span>

<span data-ttu-id="b94e9-130">Hiermee geeft u de maximale tijds duur in seconden op waarmee wordt `Wait-Event` gewacht tot de gebeurtenis plaatsvindt.</span><span class="sxs-lookup"><span data-stu-id="b94e9-130">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="b94e9-131">De standaard waarde-1, wacht oneindig.</span><span class="sxs-lookup"><span data-stu-id="b94e9-131">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="b94e9-132">De timing wordt gestart wanneer u de `Wait-Event` opdracht verzendt.</span><span class="sxs-lookup"><span data-stu-id="b94e9-132">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="b94e9-133">Als de opgegeven tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt geretourneerd, zelfs als de gebeurtenis niet is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b94e9-133">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="b94e9-134">Er wordt geen fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b94e9-134">No error message is displayed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b94e9-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b94e9-135">CommonParameters</span></span>

<span data-ttu-id="b94e9-136">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b94e9-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b94e9-137">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b94e9-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b94e9-138">INVOER</span><span class="sxs-lookup"><span data-stu-id="b94e9-138">INPUTS</span></span>

### <span data-ttu-id="b94e9-139">System. String</span><span class="sxs-lookup"><span data-stu-id="b94e9-139">System.String</span></span>

## <span data-ttu-id="b94e9-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b94e9-140">OUTPUTS</span></span>

### <span data-ttu-id="b94e9-141">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="b94e9-141">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="b94e9-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b94e9-142">NOTES</span></span>

<span data-ttu-id="b94e9-143">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b94e9-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="b94e9-144">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="b94e9-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="b94e9-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b94e9-145">RELATED LINKS</span></span>

[<span data-ttu-id="b94e9-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="b94e9-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="b94e9-147">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="b94e9-147">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="b94e9-148">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b94e9-148">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="b94e9-149">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="b94e9-149">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="b94e9-150">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="b94e9-150">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="b94e9-151">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b94e9-151">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="b94e9-152">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b94e9-152">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="b94e9-153">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b94e9-153">Wait-Event</span></span>](Wait-Event.md)
