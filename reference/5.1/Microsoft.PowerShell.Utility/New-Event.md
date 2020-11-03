---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 9ab8ff192b150811b3cef7035c60f509e1fb5570
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250400"
---
# <span data-ttu-id="62937-103">New-Event</span><span class="sxs-lookup"><span data-stu-id="62937-103">New-Event</span></span>

## <span data-ttu-id="62937-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="62937-104">SYNOPSIS</span></span>
<span data-ttu-id="62937-105">Hiermee maakt u een nieuwe gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-105">Creates a new event.</span></span>

## <span data-ttu-id="62937-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="62937-106">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="62937-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="62937-107">DESCRIPTION</span></span>
<span data-ttu-id="62937-108">Met de cmdlet **New-Event** maakt u een nieuwe aangepaste gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-108">The **New-Event** cmdlet creates a new custom event.</span></span>

<span data-ttu-id="62937-109">U kunt aangepaste gebeurtenissen gebruiken om gebruikers op de hoogte te stellen van status wijzigingen in uw programma en elke wijziging die uw programma kan detecteren, waaronder de hardware-of systeem voorwaarden, de toepassings status, de status van het netwerk of het volt ooien van een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="62937-109">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="62937-110">Aangepaste gebeurtenissen worden automatisch toegevoegd aan de gebeurtenis wachtrij in uw sessie wanneer deze worden gegenereerd. u hoeft zich niet aan te melden.</span><span class="sxs-lookup"><span data-stu-id="62937-110">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span>
<span data-ttu-id="62937-111">Als u echter een gebeurtenis wilt door sturen naar de lokale sessie of een actie wilt opgeven om te reageren op de gebeurtenis, gebruikt u de Register-EngineEvent cmdlet om u te abonneren op de aangepaste gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-111">However, if you want to forward an event to the local session or specify an action to respond to the event, use the Register-EngineEvent cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="62937-112">Wanneer u zich abonneert op een aangepaste gebeurtenis, wordt de gebeurtenis abonnee toegevoegd aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="62937-112">When you subscribe to a custom event, the event subscriber is added to your session.</span></span>
<span data-ttu-id="62937-113">Als u het gebeurtenis abonnement annuleert met behulp van de cmdlet Unregister-Event, worden de gebeurtenis abonnee en de aangepaste gebeurtenis verwijderd uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="62937-113">If you cancel the event subscription by using the Unregister-Event cmdlet, the event subscriber and custom event are deleted from the session.</span></span>
<span data-ttu-id="62937-114">Als u zich niet hebt geabonneerd op de aangepaste gebeurtenis, moet u de programma voorwaarden wijzigen of de Windows Power shell-sessie sluiten om de gebeurtenis te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="62937-114">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the Windows PowerShell session.</span></span>

## <span data-ttu-id="62937-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="62937-115">EXAMPLES</span></span>

### <span data-ttu-id="62937-116">Voor beeld 1: een nieuwe gebeurtenis in de wachtrij voor gebeurtenissen maken</span><span class="sxs-lookup"><span data-stu-id="62937-116">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="62937-117">Met deze opdracht maakt u een nieuwe gebeurtenis in de gebeurtenis wachtrij van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="62937-117">This command creates a new event in the Windows PowerShell event queue.</span></span>
<span data-ttu-id="62937-118">Er wordt gebruikgemaakt van een **Windows. timer** -object voor het verzenden van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-118">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="62937-119">Voor beeld 2: een gebeurtenis activeren als reactie op een andere gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="62937-119">Example 2: Raise an event in response to another event</span></span>

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

<span data-ttu-id="62937-120">Deze voorbeeld functie maakt gebruik van de cmdlet **New-Event** om een gebeurtenis te genereren als reactie op een andere gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-120">This sample function uses the **New-Event** cmdlet to raise an event in response to another event.</span></span>
<span data-ttu-id="62937-121">De opdracht gebruikt de cmdlet Register-ObjectEvent om u te abonneren op de gebeurtenis Windows Management Instrumentation (WMI) die wordt geactiveerd wanneer een nieuw proces wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="62937-121">The command uses the Register-ObjectEvent cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span>
<span data-ttu-id="62937-122">De opdracht gebruikt de *actie* parameter van de cmdlet voor het aanroepen van de **nieuwe-gebeurtenis-** cmdlet, waardoor de nieuwe gebeurtenis wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="62937-122">The command uses the *Action* parameter of the cmdlet to call the **New-Event** cmdlet, which creates the new event.</span></span>

<span data-ttu-id="62937-123">Omdat de gebeurtenissen die worden gegenereerd door **nieuwe gebeurtenissen** automatisch worden toegevoegd aan de Windows PowerShellevent-wachtrij, hoeft u zich niet te registreren voor die gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-123">Because the events that **New-Event** raises are automatically added to the Windows PowerShellevent queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="62937-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62937-124">PARAMETERS</span></span>

### <span data-ttu-id="62937-125">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="62937-125">-EventArguments</span></span>
<span data-ttu-id="62937-126">Hiermee geeft u een object op dat opties bevat voor de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-126">Specifies an object that contains options for the event.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62937-127">-MessageData</span><span class="sxs-lookup"><span data-stu-id="62937-127">-MessageData</span></span>
<span data-ttu-id="62937-128">Hiermee geeft u aanvullende gegevens op die zijn gekoppeld aan de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-128">Specifies additional data associated with the event.</span></span>
<span data-ttu-id="62937-129">De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van het object Event.</span><span class="sxs-lookup"><span data-stu-id="62937-129">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62937-130">-Sender</span><span class="sxs-lookup"><span data-stu-id="62937-130">-Sender</span></span>
<span data-ttu-id="62937-131">Hiermee geeft u het object op waarmee de gebeurtenis wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="62937-131">Specifies the object that raises the event.</span></span>
<span data-ttu-id="62937-132">De standaard waarde is de Windows Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="62937-132">The default is the Windows PowerShell engine.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62937-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="62937-133">-SourceIdentifier</span></span>
<span data-ttu-id="62937-134">Hiermee geeft u een naam op voor de nieuwe gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="62937-134">Specifies a name for the new event.</span></span>
<span data-ttu-id="62937-135">Deze para meter is vereist en moet uniek zijn in de sessie.</span><span class="sxs-lookup"><span data-stu-id="62937-135">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="62937-136">De waarde van deze para meter wordt weer gegeven in de eigenschap **SourceIdentifier** van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="62937-136">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62937-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="62937-137">CommonParameters</span></span>
<span data-ttu-id="62937-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="62937-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="62937-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62937-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="62937-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="62937-140">INPUTS</span></span>

### <span data-ttu-id="62937-141">Geen</span><span class="sxs-lookup"><span data-stu-id="62937-141">None</span></span>
<span data-ttu-id="62937-142">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62937-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="62937-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="62937-143">OUTPUTS</span></span>

### <span data-ttu-id="62937-144">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="62937-144">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="62937-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="62937-145">NOTES</span></span>

<span data-ttu-id="62937-146">De nieuwe aangepaste gebeurtenis, het gebeurtenis abonnement en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="62937-146">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span> <span data-ttu-id="62937-147">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="62937-147">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="62937-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="62937-148">RELATED LINKS</span></span>

[<span data-ttu-id="62937-149">Get-Event</span><span class="sxs-lookup"><span data-stu-id="62937-149">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="62937-150">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="62937-150">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="62937-151">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="62937-151">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="62937-152">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="62937-152">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="62937-153">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="62937-153">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="62937-154">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="62937-154">Wait-Event</span></span>](Wait-Event.md)
