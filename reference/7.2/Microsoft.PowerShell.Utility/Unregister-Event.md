---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 863dbba4c106f1f57c9396823692620bb358b646
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705705"
---
# <span data-ttu-id="1a2c7-102">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="1a2c7-102">Unregister-Event</span></span>

## <span data-ttu-id="1a2c7-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1a2c7-103">SYNOPSIS</span></span>
<span data-ttu-id="1a2c7-104">Hiermee wordt een gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-104">Cancels an event subscription.</span></span>

## <span data-ttu-id="1a2c7-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1a2c7-105">SYNTAX</span></span>

### <span data-ttu-id="1a2c7-106">BySource (standaard)</span><span class="sxs-lookup"><span data-stu-id="1a2c7-106">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1a2c7-107">ById</span><span class="sxs-lookup"><span data-stu-id="1a2c7-107">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1a2c7-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1a2c7-108">DESCRIPTION</span></span>

<span data-ttu-id="1a2c7-109">De `Unregister-Event` cmdlet annuleert een gebeurtenis abonnement dat is gemaakt met behulp van de `Register-EngineEvent` -, `Register-ObjectEvent` -of- `Register-WmiEvent` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-109">The `Unregister-Event` cmdlet cancels an event subscription that was created by using the `Register-EngineEvent`, `Register-ObjectEvent`, or `Register-WmiEvent` cmdlet.</span></span>

<span data-ttu-id="1a2c7-110">Wanneer een gebeurtenis abonnement wordt geannuleerd, wordt de gebeurtenis abonnee verwijderd uit de sessie en worden de geabonneerde gebeurtenissen niet meer toegevoegd aan de gebeurtenis wachtrij.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-110">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span> <span data-ttu-id="1a2c7-111">Wanneer u een abonnement opzegt op een gebeurtenis die is gemaakt met behulp van de `New-Event` cmdlet, wordt de nieuwe gebeurtenis ook verwijderd uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-111">When you cancel a subscription to an event created by using the `New-Event` cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="1a2c7-112">`Unregister-Event` verwijdert geen gebeurtenissen uit de wachtrij van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-112">`Unregister-Event` does not delete events from the event queue.</span></span> <span data-ttu-id="1a2c7-113">Als u gebeurtenissen wilt verwijderen, gebruikt u de `Remove-Event` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-113">To delete events, use the `Remove-Event` cmdlet.</span></span>

## <span data-ttu-id="1a2c7-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1a2c7-114">EXAMPLES</span></span>

### <span data-ttu-id="1a2c7-115">Voor beeld 1: een gebeurtenis abonnement op bron-id annuleren</span><span class="sxs-lookup"><span data-stu-id="1a2c7-115">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="1a2c7-116">Met deze opdracht wordt het gebeurtenis abonnement met de bron-id ProcessStarted geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-116">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="1a2c7-117">Gebruik de cmdlet om de bron-id van een gebeurtenis te vinden `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="1a2c7-117">To find the source identifier of an event, use the `Get-Event` cmdlet.</span></span> <span data-ttu-id="1a2c7-118">Als u de bron-id van een gebeurtenis abonnement wilt zoeken, gebruikt u de `Get-EventSubscriber` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-118">To find the source identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="1a2c7-119">Voor beeld 2: een gebeurtenis abonnement op abonnements-id annuleren</span><span class="sxs-lookup"><span data-stu-id="1a2c7-119">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="1a2c7-120">Met deze opdracht wordt het gebeurtenis abonnement met de abonnements-id 2 geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-120">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="1a2c7-121">Gebruik de cmdlet om de abonnements-id van een gebeurtenis abonnement te vinden `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="1a2c7-121">To find the subscription identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="1a2c7-122">Voor beeld 3: alle gebeurtenis abonnementen annuleren</span><span class="sxs-lookup"><span data-stu-id="1a2c7-122">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="1a2c7-123">Met deze opdracht worden alle gebeurtenis abonnementen in de sessie geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-123">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="1a2c7-124">De opdracht gebruikt de `Get-EventSubscriber` cmdlet om alle Event Subscriber-objecten in de sessie op te halen, met inbegrip van de abonnees die zijn verborgen met behulp van de para meter **SupportEvent** van de cmdlets voor gebeurtenis registratie.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-124">The command uses the `Get-EventSubscriber` cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the **SupportEvent** parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="1a2c7-125">Er wordt gebruikgemaakt van een pijplijn operator ( `|` ) om de abonnee objecten te verzenden `Unregister-Event` , waardoor ze uit de sessie worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-125">It uses a pipeline operator (`|`) to send the subscriber objects to `Unregister-Event`, which deletes them from the session.</span></span> <span data-ttu-id="1a2c7-126">Voor het volt ooien van de taak is de para meter **Forces** ook vereist voor `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="1a2c7-126">To complete the task, the **Force** parameter is also required on `Unregister-Event`.</span></span>

## <span data-ttu-id="1a2c7-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a2c7-127">PARAMETERS</span></span>

### <span data-ttu-id="1a2c7-128">-Force</span><span class="sxs-lookup"><span data-stu-id="1a2c7-128">-Force</span></span>

<span data-ttu-id="1a2c7-129">Annuleert alle gebeurtenis abonnementen, inclusief abonnementen die zijn verborgen met de para meter **SupportEvent** van `Register-ObjectEvent` , `Register-WmiEvent` en `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="1a2c7-129">Cancels all event subscriptions, including subscriptions that were hidden by using the **SupportEvent** parameter of `Register-ObjectEvent`, `Register-WmiEvent`, and `Register-EngineEvent`.</span></span>

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

### <span data-ttu-id="1a2c7-130">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="1a2c7-130">-SourceIdentifier</span></span>

<span data-ttu-id="1a2c7-131">Hiermee geeft u een bron-id op die met deze cmdlet gebeurtenis abonnementen annuleert.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-131">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="1a2c7-132">Een **SourceIdentifier** -of **SubscriptionId** -para meter moet worden opgenomen in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-132">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

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

### <span data-ttu-id="1a2c7-133">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="1a2c7-133">-SubscriptionId</span></span>

<span data-ttu-id="1a2c7-134">Hiermee geeft u een bron-id-ID op die met deze cmdlet gebeurtenis abonnementen annuleert.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-134">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="1a2c7-135">Een **SourceIdentifier** -of **SubscriptionId** -para meter moet worden opgenomen in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-135">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

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

### <span data-ttu-id="1a2c7-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a2c7-136">-Confirm</span></span>

<span data-ttu-id="1a2c7-137">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-137">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1a2c7-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a2c7-138">-WhatIf</span></span>

<span data-ttu-id="1a2c7-139">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-139">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1a2c7-140">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-140">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1a2c7-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a2c7-141">CommonParameters</span></span>

<span data-ttu-id="1a2c7-142">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a2c7-143">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a2c7-144">INVOER</span><span class="sxs-lookup"><span data-stu-id="1a2c7-144">INPUTS</span></span>

### <span data-ttu-id="1a2c7-145">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="1a2c7-145">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="1a2c7-146">U kunt de uitvoer door sluizen van `Get-EventSubscriber` naar `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="1a2c7-146">You can pipe the output from `Get-EventSubscriber` to `Unregister-Event`.</span></span>

## <span data-ttu-id="1a2c7-147">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1a2c7-147">OUTPUTS</span></span>

### <span data-ttu-id="1a2c7-148">Geen</span><span class="sxs-lookup"><span data-stu-id="1a2c7-148">None</span></span>

<span data-ttu-id="1a2c7-149">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="1a2c7-150">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1a2c7-150">NOTES</span></span>

<span data-ttu-id="1a2c7-151">Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-151">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="1a2c7-152">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="1a2c7-153">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="1a2c7-154">`Unregister-Event` kan geen gebeurtenissen verwijderen die zijn gemaakt met behulp van de `New-Event` cmdlet tenzij u bent geabonneerd op de gebeurtenis met behulp van de `Register-EngineEvent` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-154">`Unregister-Event` cannot delete events created by using the `New-Event` cmdlet unless you have subscribed to the event by using the `Register-EngineEvent` cmdlet.</span></span> <span data-ttu-id="1a2c7-155">Als u een aangepaste gebeurtenis uit de sessie wilt verwijderen, moet u deze programmatisch verwijderen of de sessie sluiten.</span><span class="sxs-lookup"><span data-stu-id="1a2c7-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

## <span data-ttu-id="1a2c7-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1a2c7-156">RELATED LINKS</span></span>

[<span data-ttu-id="1a2c7-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="1a2c7-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="1a2c7-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="1a2c7-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="1a2c7-159">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="1a2c7-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="1a2c7-160">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="1a2c7-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="1a2c7-161">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="1a2c7-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="1a2c7-162">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="1a2c7-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="1a2c7-163">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="1a2c7-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="1a2c7-164">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="1a2c7-164">Wait-Event</span></span>](Wait-Event.md)
