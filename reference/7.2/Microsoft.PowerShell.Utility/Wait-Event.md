---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: caf2a1c80848d3140e7ad46fdf54dbe71886c633
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704728"
---
# <span data-ttu-id="4e1e7-102">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="4e1e7-102">Wait-Event</span></span>

## <span data-ttu-id="4e1e7-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4e1e7-103">SYNOPSIS</span></span>
<span data-ttu-id="4e1e7-104">Er wordt gewacht tot een bepaalde gebeurtenis is opgetreden voordat de uitvoering wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-104">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="4e1e7-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4e1e7-105">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="4e1e7-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4e1e7-106">DESCRIPTION</span></span>

<span data-ttu-id="4e1e7-107">De `Wait-Event` cmdlet onderbreekt de uitvoering van een script of functie totdat een bepaalde gebeurtenis wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-107">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="4e1e7-108">De uitvoering wordt hervat wanneer de gebeurtenis wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-108">Execution resumes when the event is detected.</span></span> <span data-ttu-id="4e1e7-109">U annuleert het wachten door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-109">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="4e1e7-110">Deze functie biedt een alternatief voor het opvragen van een gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-110">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="4e1e7-111">Daarnaast kunt u het antwoord op twee verschillende manieren bepalen voor een gebeurtenis:</span><span class="sxs-lookup"><span data-stu-id="4e1e7-111">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="4e1e7-112">de **actie** parameter van het gebeurtenis abonnement gebruiken</span><span class="sxs-lookup"><span data-stu-id="4e1e7-112">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="4e1e7-113">wachten tot een gebeurtenis is geretourneerd en vervolgens reageert met een actie</span><span class="sxs-lookup"><span data-stu-id="4e1e7-113">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="4e1e7-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4e1e7-114">EXAMPLES</span></span>

### <span data-ttu-id="4e1e7-115">Voor beeld 1: wachten op de volgende gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="4e1e7-115">Example 1: Wait for the next event</span></span>

<span data-ttu-id="4e1e7-116">In dit voor beeld wordt gewacht op de volgende gebeurtenis die optreedt.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-116">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="4e1e7-117">Voor beeld 2: wachten op een gebeurtenis met een opgegeven bron-id</span><span class="sxs-lookup"><span data-stu-id="4e1e7-117">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="4e1e7-118">In dit voor beeld wordt gewacht op de volgende gebeurtenis die optreedt en die een bron-id van ProcessStarted heeft.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-118">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="4e1e7-119">Voor beeld 3: wachten op gebeurtenis die is verstreken met een timer</span><span class="sxs-lookup"><span data-stu-id="4e1e7-119">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="4e1e7-120">In dit voor beeld wordt de `Wait-Event` cmdlet gebruikt om te wachten op een timer gebeurtenis in een timer die is ingesteld op 2000 milliseconden.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-120">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

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

### <span data-ttu-id="4e1e7-121">Voor beeld 4: wachten op een gebeurtenis na een opgegeven time-out</span><span class="sxs-lookup"><span data-stu-id="4e1e7-121">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="4e1e7-122">In dit voor beeld wordt 90 seconden gewacht op de volgende gebeurtenis die optreedt en die een bron-id van **ProcessStarted** heeft.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-122">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted**.</span></span> <span data-ttu-id="4e1e7-123">Als de opgegeven tijd verloopt, wordt het wachten beëindigd.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-123">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="4e1e7-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e1e7-124">PARAMETERS</span></span>

### <span data-ttu-id="4e1e7-125">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="4e1e7-125">-SourceIdentifier</span></span>

<span data-ttu-id="4e1e7-126">Hiermee geeft u de bron-id op die met deze cmdlet wordt gewacht op gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-126">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="4e1e7-127">Standaard wordt `Wait-Event` gewacht op een gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-127">By default, `Wait-Event` waits for any event.</span></span>

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

### <span data-ttu-id="4e1e7-128">-Time-out</span><span class="sxs-lookup"><span data-stu-id="4e1e7-128">-Timeout</span></span>

<span data-ttu-id="4e1e7-129">Hiermee geeft u de maximale tijds duur in seconden op waarmee wordt `Wait-Event` gewacht tot de gebeurtenis plaatsvindt.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-129">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="4e1e7-130">De standaard waarde-1, wacht oneindig.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-130">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="4e1e7-131">De timing wordt gestart wanneer u de `Wait-Event` opdracht verzendt.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-131">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="4e1e7-132">Als de opgegeven tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt geretourneerd, zelfs als de gebeurtenis niet is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-132">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="4e1e7-133">Er wordt geen fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-133">No error message is displayed.</span></span>

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

### <span data-ttu-id="4e1e7-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e1e7-134">CommonParameters</span></span>

<span data-ttu-id="4e1e7-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e1e7-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e1e7-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="4e1e7-137">INPUTS</span></span>

### <span data-ttu-id="4e1e7-138">System. String</span><span class="sxs-lookup"><span data-stu-id="4e1e7-138">System.String</span></span>

## <span data-ttu-id="4e1e7-139">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4e1e7-139">OUTPUTS</span></span>

### <span data-ttu-id="4e1e7-140">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="4e1e7-140">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="4e1e7-141">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4e1e7-141">NOTES</span></span>

<span data-ttu-id="4e1e7-142">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-142">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="4e1e7-143">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-143">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="4e1e7-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4e1e7-144">RELATED LINKS</span></span>

[<span data-ttu-id="4e1e7-145">Get-Event</span><span class="sxs-lookup"><span data-stu-id="4e1e7-145">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="4e1e7-146">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="4e1e7-146">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="4e1e7-147">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="4e1e7-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="4e1e7-148">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="4e1e7-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="4e1e7-149">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="4e1e7-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="4e1e7-150">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="4e1e7-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="4e1e7-151">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="4e1e7-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="4e1e7-152">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="4e1e7-152">Wait-Event</span></span>](Wait-Event.md)

