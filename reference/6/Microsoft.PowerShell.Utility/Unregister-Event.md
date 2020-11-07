---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 7aff17c29c8105c79d9bb3955552c75a3a05f752
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344710"
---
# <span data-ttu-id="896cf-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="896cf-103">Unregister-Event</span></span>

## <span data-ttu-id="896cf-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="896cf-104">SYNOPSIS</span></span>
<span data-ttu-id="896cf-105">Hiermee wordt een gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="896cf-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="896cf-106">SYNTAX</span></span>

### <span data-ttu-id="896cf-107">BySource (standaard)</span><span class="sxs-lookup"><span data-stu-id="896cf-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="896cf-108">ById</span><span class="sxs-lookup"><span data-stu-id="896cf-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="896cf-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="896cf-109">DESCRIPTION</span></span>

<span data-ttu-id="896cf-110">De `Unregister-Event` cmdlet annuleert een gebeurtenis abonnement dat is gemaakt met behulp van de `Register-EngineEvent` -, `Register-ObjectEvent` -of- `Register-WmiEvent` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896cf-110">The `Unregister-Event` cmdlet cancels an event subscription that was created by using the `Register-EngineEvent`, `Register-ObjectEvent`, or `Register-WmiEvent` cmdlet.</span></span>

<span data-ttu-id="896cf-111">Wanneer een gebeurtenis abonnement wordt geannuleerd, wordt de gebeurtenis abonnee verwijderd uit de sessie en worden de geabonneerde gebeurtenissen niet meer toegevoegd aan de gebeurtenis wachtrij.</span><span class="sxs-lookup"><span data-stu-id="896cf-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span> <span data-ttu-id="896cf-112">Wanneer u een abonnement opzegt op een gebeurtenis die is gemaakt met behulp van de `New-Event` cmdlet, wordt de nieuwe gebeurtenis ook verwijderd uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="896cf-112">When you cancel a subscription to an event created by using the `New-Event` cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="896cf-113">`Unregister-Event` verwijdert geen gebeurtenissen uit de wachtrij van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="896cf-113">`Unregister-Event` does not delete events from the event queue.</span></span> <span data-ttu-id="896cf-114">Als u gebeurtenissen wilt verwijderen, gebruikt u de `Remove-Event` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896cf-114">To delete events, use the `Remove-Event` cmdlet.</span></span>

## <span data-ttu-id="896cf-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="896cf-115">EXAMPLES</span></span>

### <span data-ttu-id="896cf-116">Voor beeld 1: een gebeurtenis abonnement op bron-id annuleren</span><span class="sxs-lookup"><span data-stu-id="896cf-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="896cf-117">Met deze opdracht wordt het gebeurtenis abonnement met de bron-id ProcessStarted geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="896cf-118">Gebruik de cmdlet om de bron-id van een gebeurtenis te vinden `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="896cf-118">To find the source identifier of an event, use the `Get-Event` cmdlet.</span></span> <span data-ttu-id="896cf-119">Als u de bron-id van een gebeurtenis abonnement wilt zoeken, gebruikt u de `Get-EventSubscriber` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896cf-119">To find the source identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="896cf-120">Voor beeld 2: een gebeurtenis abonnement op abonnements-id annuleren</span><span class="sxs-lookup"><span data-stu-id="896cf-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="896cf-121">Met deze opdracht wordt het gebeurtenis abonnement met de abonnements-id 2 geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="896cf-122">Gebruik de cmdlet om de abonnements-id van een gebeurtenis abonnement te vinden `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="896cf-122">To find the subscription identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="896cf-123">Voor beeld 3: alle gebeurtenis abonnementen annuleren</span><span class="sxs-lookup"><span data-stu-id="896cf-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="896cf-124">Met deze opdracht worden alle gebeurtenis abonnementen in de sessie geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="896cf-125">De opdracht gebruikt de `Get-EventSubscriber` cmdlet om alle Event Subscriber-objecten in de sessie op te halen, met inbegrip van de abonnees die zijn verborgen met behulp van de para meter **SupportEvent** van de cmdlets voor gebeurtenis registratie.</span><span class="sxs-lookup"><span data-stu-id="896cf-125">The command uses the `Get-EventSubscriber` cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the **SupportEvent** parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="896cf-126">Er wordt gebruikgemaakt van een pijplijn operator ( `|` ) om de abonnee objecten te verzenden `Unregister-Event` , waardoor ze uit de sessie worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="896cf-126">It uses a pipeline operator (`|`) to send the subscriber objects to `Unregister-Event`, which deletes them from the session.</span></span> <span data-ttu-id="896cf-127">Voor het volt ooien van de taak is de para meter **Forces** ook vereist voor `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="896cf-127">To complete the task, the **Force** parameter is also required on `Unregister-Event`.</span></span>

## <span data-ttu-id="896cf-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="896cf-128">PARAMETERS</span></span>

### <span data-ttu-id="896cf-129">-Force</span><span class="sxs-lookup"><span data-stu-id="896cf-129">-Force</span></span>

<span data-ttu-id="896cf-130">Annuleert alle gebeurtenis abonnementen, inclusief abonnementen die zijn verborgen met de para meter **SupportEvent** van `Register-ObjectEvent` , `Register-WmiEvent` en `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="896cf-130">Cancels all event subscriptions, including subscriptions that were hidden by using the **SupportEvent** parameter of `Register-ObjectEvent`, `Register-WmiEvent`, and `Register-EngineEvent`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="896cf-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="896cf-131">-SourceIdentifier</span></span>

<span data-ttu-id="896cf-132">Hiermee geeft u een bron-id op die met deze cmdlet gebeurtenis abonnementen annuleert.</span><span class="sxs-lookup"><span data-stu-id="896cf-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="896cf-133">Een **SourceIdentifier** -of **SubscriptionId** -para meter moet worden opgenomen in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="896cf-133">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="896cf-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="896cf-134">-SubscriptionId</span></span>

<span data-ttu-id="896cf-135">Hiermee geeft u een bron-id-ID op die met deze cmdlet gebeurtenis abonnementen annuleert.</span><span class="sxs-lookup"><span data-stu-id="896cf-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="896cf-136">Een **SourceIdentifier** -of **SubscriptionId** -para meter moet worden opgenomen in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="896cf-136">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="896cf-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="896cf-137">-Confirm</span></span>

<span data-ttu-id="896cf-138">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="896cf-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="896cf-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="896cf-139">-WhatIf</span></span>

<span data-ttu-id="896cf-140">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="896cf-140">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="896cf-141">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="896cf-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="896cf-142">CommonParameters</span></span>

<span data-ttu-id="896cf-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="896cf-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="896cf-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="896cf-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="896cf-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="896cf-145">INPUTS</span></span>

### <span data-ttu-id="896cf-146">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="896cf-146">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="896cf-147">U kunt de uitvoer door sluizen van `Get-EventSubscriber` naar `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="896cf-147">You can pipe the output from `Get-EventSubscriber` to `Unregister-Event`.</span></span>

## <span data-ttu-id="896cf-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="896cf-148">OUTPUTS</span></span>

### <span data-ttu-id="896cf-149">Geen</span><span class="sxs-lookup"><span data-stu-id="896cf-149">None</span></span>

<span data-ttu-id="896cf-150">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="896cf-151">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="896cf-151">NOTES</span></span>

<span data-ttu-id="896cf-152">Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.</span><span class="sxs-lookup"><span data-stu-id="896cf-152">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="896cf-153">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="896cf-153">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="896cf-154">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="896cf-154">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="896cf-155">`Unregister-Event` kan geen gebeurtenissen verwijderen die zijn gemaakt met behulp van de `New-Event` cmdlet tenzij u bent geabonneerd op de gebeurtenis met behulp van de `Register-EngineEvent` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="896cf-155">`Unregister-Event` cannot delete events created by using the `New-Event` cmdlet unless you have subscribed to the event by using the `Register-EngineEvent` cmdlet.</span></span> <span data-ttu-id="896cf-156">Als u een aangepaste gebeurtenis uit de sessie wilt verwijderen, moet u deze programmatisch verwijderen of de sessie sluiten.</span><span class="sxs-lookup"><span data-stu-id="896cf-156">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

## <span data-ttu-id="896cf-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="896cf-157">RELATED LINKS</span></span>

[<span data-ttu-id="896cf-158">Get-Event</span><span class="sxs-lookup"><span data-stu-id="896cf-158">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="896cf-159">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="896cf-159">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="896cf-160">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="896cf-160">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="896cf-161">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="896cf-161">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="896cf-162">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="896cf-162">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="896cf-163">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="896cf-163">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="896cf-164">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="896cf-164">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="896cf-165">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="896cf-165">Wait-Event</span></span>](Wait-Event.md)
