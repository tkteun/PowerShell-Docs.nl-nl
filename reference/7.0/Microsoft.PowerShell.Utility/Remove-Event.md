---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 2730e413a79b2af5355cd2ece7c1e8a6d219d708
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249534"
---
# <span data-ttu-id="40876-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="40876-103">Remove-Event</span></span>

## <span data-ttu-id="40876-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="40876-104">SYNOPSIS</span></span>
<span data-ttu-id="40876-105">Hiermee verwijdert u gebeurtenissen uit de wachtrij van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="40876-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="40876-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="40876-106">SYNTAX</span></span>

### <span data-ttu-id="40876-107">BySource (standaard)</span><span class="sxs-lookup"><span data-stu-id="40876-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="40876-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="40876-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="40876-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="40876-109">DESCRIPTION</span></span>
<span data-ttu-id="40876-110">Met de cmdlet **Remove-Event** worden gebeurtenissen uit de gebeurtenis wachtrij in de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40876-110">The **Remove-Event** cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="40876-111">Met deze cmdlet worden alleen de gebeurtenissen uit de wachtrij verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40876-111">This cmdlet deletes only the events currently in the queue.</span></span>
<span data-ttu-id="40876-112">Als u gebeurtenis registraties wilt annuleren of zich wilt afmelden, gebruikt u de Unregister-Event-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40876-112">To cancel event registrations or unsubscribe, use the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="40876-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="40876-113">EXAMPLES</span></span>

### <span data-ttu-id="40876-114">Voor beeld 1: een gebeurtenis verwijderen op bron-id</span><span class="sxs-lookup"><span data-stu-id="40876-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="40876-115">Met deze opdracht worden gebeurtenissen verwijderd met een bron-id van het proces dat is gestart vanuit de gebeurtenis wachtrij.</span><span class="sxs-lookup"><span data-stu-id="40876-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="40876-116">Voor beeld 2: een gebeurtenis verwijderen op gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="40876-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="40876-117">Met deze opdracht wordt de gebeurtenis met gebeurtenis-ID 30 uit de gebeurtenis wachtrij verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40876-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="40876-118">Voor beeld 3: alle gebeurtenissen verwijderen</span><span class="sxs-lookup"><span data-stu-id="40876-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="40876-119">Met deze opdracht worden alle gebeurtenissen uit de gebeurtenis wachtrij verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40876-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="40876-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="40876-120">PARAMETERS</span></span>

### <span data-ttu-id="40876-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="40876-121">-EventIdentifier</span></span>
<span data-ttu-id="40876-122">Hiermee geeft u de gebeurtenis-id op waarvoor de cmdlet wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40876-122">Specifies the event identifier for which the cmdlet deletes.</span></span>
<span data-ttu-id="40876-123">Een *EventIdentifier* -of *SourceIdentifier* -para meter is vereist in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="40876-123">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40876-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="40876-124">-SourceIdentifier</span></span>
<span data-ttu-id="40876-125">Hiermee geeft u de bron-id op waarvoor met deze cmdlet gebeurtenissen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40876-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span>
<span data-ttu-id="40876-126">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="40876-126">Wildcards are not permitted.</span></span>
<span data-ttu-id="40876-127">Een *EventIdentifier* -of *SourceIdentifier* -para meter is vereist in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="40876-127">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40876-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="40876-128">-Confirm</span></span>
<span data-ttu-id="40876-129">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="40876-129">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="40876-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="40876-130">-WhatIf</span></span>
<span data-ttu-id="40876-131">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="40876-131">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="40876-132">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="40876-132">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="40876-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40876-133">CommonParameters</span></span>
<span data-ttu-id="40876-134">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40876-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40876-135">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40876-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40876-136">INVOER</span><span class="sxs-lookup"><span data-stu-id="40876-136">INPUTS</span></span>

### <span data-ttu-id="40876-137">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="40876-137">System.Management.Automation.PSEventArgs</span></span>
<span data-ttu-id="40876-138">U kunt gebeurtenissen van Get-Event naar **Remove-Event** door sluizen.</span><span class="sxs-lookup"><span data-stu-id="40876-138">You can pipe events from Get-Event to **Remove-Event**.</span></span>

## <span data-ttu-id="40876-139">UITVOER</span><span class="sxs-lookup"><span data-stu-id="40876-139">OUTPUTS</span></span>

### <span data-ttu-id="40876-140">Geen</span><span class="sxs-lookup"><span data-stu-id="40876-140">None</span></span>
<span data-ttu-id="40876-141">De cmdlet genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="40876-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="40876-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="40876-142">NOTES</span></span>

* <span data-ttu-id="40876-143">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="40876-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="40876-144">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="40876-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="40876-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="40876-145">RELATED LINKS</span></span>

[<span data-ttu-id="40876-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="40876-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="40876-147">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="40876-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="40876-148">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="40876-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="40876-149">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="40876-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="40876-150">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="40876-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="40876-151">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="40876-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="40876-152">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="40876-152">Wait-Event</span></span>](Wait-Event.md)
