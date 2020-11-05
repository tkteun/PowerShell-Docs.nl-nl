---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: f1f42c1e8831896feac398228e45fc0890136fff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250356"
---
# <span data-ttu-id="268f4-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="268f4-103">Unregister-Event</span></span>

## <span data-ttu-id="268f4-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="268f4-104">SYNOPSIS</span></span>
<span data-ttu-id="268f4-105">Hiermee wordt een gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="268f4-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="268f4-106">SYNTAX</span></span>

### <span data-ttu-id="268f4-107">BySource (standaard)</span><span class="sxs-lookup"><span data-stu-id="268f4-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="268f4-108">ById</span><span class="sxs-lookup"><span data-stu-id="268f4-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="268f4-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="268f4-109">DESCRIPTION</span></span>
<span data-ttu-id="268f4-110">De **registratie ongedaan maken-Event** cmdlet annuleert een gebeurtenis abonnement dat is gemaakt met behulp van de cmdlet REGI ster-EngineEvent, REGI ster-ObjectEvent of Register-WmiEvent.</span><span class="sxs-lookup"><span data-stu-id="268f4-110">The **Unregister-Event** cmdlet cancels an event subscription that was created by using the Register-EngineEvent, Register-ObjectEvent, or Register-WmiEvent cmdlet.</span></span>

<span data-ttu-id="268f4-111">Wanneer een gebeurtenis abonnement wordt geannuleerd, wordt de gebeurtenis abonnee verwijderd uit de sessie en worden de geabonneerde gebeurtenissen niet meer toegevoegd aan de gebeurtenis wachtrij.</span><span class="sxs-lookup"><span data-stu-id="268f4-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span>
<span data-ttu-id="268f4-112">Wanneer u een abonnement opzegt op een gebeurtenis die is gemaakt met behulp van de cmdlet New-Event, wordt de nieuwe gebeurtenis ook verwijderd uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="268f4-112">When you cancel a subscription to an event created by using the New-Event cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="268f4-113">**Registratie ongedaan maken:** er worden geen gebeurtenissen uit de gebeurtenis wachtrij verwijderd.</span><span class="sxs-lookup"><span data-stu-id="268f4-113">**Unregister-Event** does not delete events from the event queue.</span></span>
<span data-ttu-id="268f4-114">Als u gebeurtenissen wilt verwijderen, gebruikt u de cmdlet Remove-Event.</span><span class="sxs-lookup"><span data-stu-id="268f4-114">To delete events, use the Remove-Event cmdlet.</span></span>

## <span data-ttu-id="268f4-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="268f4-115">EXAMPLES</span></span>

### <span data-ttu-id="268f4-116">Voor beeld 1: een gebeurtenis abonnement op bron-id annuleren</span><span class="sxs-lookup"><span data-stu-id="268f4-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="268f4-117">Met deze opdracht wordt het gebeurtenis abonnement met de bron-id ProcessStarted geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="268f4-118">Gebruik de cmdlet Get-Event om de bron-id van een gebeurtenis te vinden.</span><span class="sxs-lookup"><span data-stu-id="268f4-118">To find the source identifier of an event, use the Get-Event cmdlet.</span></span>
<span data-ttu-id="268f4-119">Als u de bron-id van een gebeurtenis abonnement wilt zoeken, gebruikt u de cmdlet **Get-EventSubscriber** .</span><span class="sxs-lookup"><span data-stu-id="268f4-119">To find the source identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="268f4-120">Voor beeld 2: een gebeurtenis abonnement op abonnements-id annuleren</span><span class="sxs-lookup"><span data-stu-id="268f4-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="268f4-121">Met deze opdracht wordt het gebeurtenis abonnement met de abonnements-id 2 geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="268f4-122">Gebruik de cmdlet **Get-EventSubscriber** om de abonnements-id van een gebeurtenis abonnement te vinden.</span><span class="sxs-lookup"><span data-stu-id="268f4-122">To find the subscription identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="268f4-123">Voor beeld 3: alle gebeurtenis abonnementen annuleren</span><span class="sxs-lookup"><span data-stu-id="268f4-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="268f4-124">Met deze opdracht worden alle gebeurtenis abonnementen in de sessie geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="268f4-125">De opdracht maakt gebruik van de cmdlet **Get-EventSubscriber** om alle Event Subscriber-objecten in de sessie op te halen, met inbegrip van de abonnees die zijn verborgen met de para meter *SupportEvent* van de cmdlets voor gebeurtenis registratie.</span><span class="sxs-lookup"><span data-stu-id="268f4-125">The command uses the **Get-EventSubscriber** cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the *SupportEvent* parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="268f4-126">Er wordt gebruikgemaakt van een pijplijn operator (|) om de abonnee objecten te verzenden om de **registratie ongedaan te maken** , waardoor ze uit de sessie worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="268f4-126">It uses a pipeline operator (|) to send the subscriber objects to **Unregister-Event** , which deletes them from the session.</span></span>
<span data-ttu-id="268f4-127">Voor het volt ooien van de taak is de para meter *Forces* ook vereist voor het **ongedaan maken** van de registratie van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="268f4-127">To complete the task, the *Force* parameter is also required on **Unregister-Event**.</span></span>

## <span data-ttu-id="268f4-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="268f4-128">PARAMETERS</span></span>

### <span data-ttu-id="268f4-129">-Force</span><span class="sxs-lookup"><span data-stu-id="268f4-129">-Force</span></span>
<span data-ttu-id="268f4-130">Hiermee annuleert u alle gebeurtenis abonnementen, inclusief abonnementen die zijn verborgen met de para meter *SupportEvent* van **REGI ster-ObjectEvent** , **REGI ster-WmiEvent** en **REGI ster-EngineEvent**.</span><span class="sxs-lookup"><span data-stu-id="268f4-130">Cancels all event subscriptions, including subscriptions that were hidden by using the *SupportEvent* parameter of **Register-ObjectEvent** , **Register-WmiEvent** , and **Register-EngineEvent**.</span></span>

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

### <span data-ttu-id="268f4-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="268f4-131">-SourceIdentifier</span></span>
<span data-ttu-id="268f4-132">Hiermee geeft u een bron-id op die met deze cmdlet gebeurtenis abonnementen annuleert.</span><span class="sxs-lookup"><span data-stu-id="268f4-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="268f4-133">Een *SourceIdentifier* -of *SubscriptionId* -para meter moet worden opgenomen in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="268f4-133">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="268f4-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="268f4-134">-SubscriptionId</span></span>
<span data-ttu-id="268f4-135">Hiermee geeft u een bron-id-ID op die met deze cmdlet gebeurtenis abonnementen annuleert.</span><span class="sxs-lookup"><span data-stu-id="268f4-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="268f4-136">Een *SourceIdentifier* -of *SubscriptionId* -para meter moet worden opgenomen in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="268f4-136">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="268f4-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="268f4-137">-Confirm</span></span>
<span data-ttu-id="268f4-138">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="268f4-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="268f4-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="268f4-139">-WhatIf</span></span>
<span data-ttu-id="268f4-140">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="268f4-140">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="268f4-141">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="268f4-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="268f4-142">CommonParameters</span></span>
<span data-ttu-id="268f4-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="268f4-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="268f4-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="268f4-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="268f4-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="268f4-145">INPUTS</span></span>

### <span data-ttu-id="268f4-146">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="268f4-146">System.Management.Automation.PSEventSubscriber</span></span>
<span data-ttu-id="268f4-147">U kunt de uitvoer van Get-EventSubscriber voor het **opheffen van de registratie-gebeurtenis** door sluizen.</span><span class="sxs-lookup"><span data-stu-id="268f4-147">You can pipe the output from Get-EventSubscriber to **Unregister-Event**.</span></span>

## <span data-ttu-id="268f4-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="268f4-148">OUTPUTS</span></span>

### <span data-ttu-id="268f4-149">Geen</span><span class="sxs-lookup"><span data-stu-id="268f4-149">None</span></span>
<span data-ttu-id="268f4-150">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="268f4-151">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="268f4-151">NOTES</span></span>

* <span data-ttu-id="268f4-152">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="268f4-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="268f4-153">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="268f4-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="268f4-154">**Registratie ongedaan maken: gebeurtenis** kan geen gebeurtenissen verwijderen die zijn gemaakt met behulp van de cmdlet New-Event, tenzij u bent geabonneerd op de gebeurtenis met behulp van de cmdlet **REGI ster-EngineEvent** .</span><span class="sxs-lookup"><span data-stu-id="268f4-154">**Unregister-Event** cannot delete events created by using the New-Event cmdlet unless you have subscribed to the event by using the **Register-EngineEvent** cmdlet.</span></span>
<span data-ttu-id="268f4-155">Als u een aangepaste gebeurtenis uit de sessie wilt verwijderen, moet u deze programmatisch verwijderen of de sessie sluiten.</span><span class="sxs-lookup"><span data-stu-id="268f4-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

*

## <span data-ttu-id="268f4-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="268f4-156">RELATED LINKS</span></span>

[<span data-ttu-id="268f4-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="268f4-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="268f4-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="268f4-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="268f4-159">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="268f4-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="268f4-160">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="268f4-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="268f4-161">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="268f4-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="268f4-162">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="268f4-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="268f4-163">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="268f4-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="268f4-164">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="268f4-164">Wait-Event</span></span>](Wait-Event.md)