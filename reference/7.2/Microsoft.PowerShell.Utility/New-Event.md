---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 86a4370caccb43edf62af75337afb15f3fb63d7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705928"
---
# <span data-ttu-id="a21d7-102">New-Event</span><span class="sxs-lookup"><span data-stu-id="a21d7-102">New-Event</span></span>

## <span data-ttu-id="a21d7-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a21d7-103">SYNOPSIS</span></span>
<span data-ttu-id="a21d7-104">Hiermee maakt u een nieuwe gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-104">Creates a new event.</span></span>

## <span data-ttu-id="a21d7-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a21d7-105">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="a21d7-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a21d7-106">DESCRIPTION</span></span>

<span data-ttu-id="a21d7-107">Met de `New-Event` cmdlet maakt u een nieuwe aangepaste gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-107">The `New-Event` cmdlet creates a new custom event.</span></span>

<span data-ttu-id="a21d7-108">U kunt aangepaste gebeurtenissen gebruiken om gebruikers op de hoogte te stellen van status wijzigingen in uw programma en elke wijziging die uw programma kan detecteren, waaronder de hardware-of systeem voorwaarden, de toepassings status, de status van het netwerk of het volt ooien van een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a21d7-108">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="a21d7-109">Aangepaste gebeurtenissen worden automatisch toegevoegd aan de gebeurtenis wachtrij in uw sessie wanneer deze worden gegenereerd. u hoeft zich niet aan te melden.</span><span class="sxs-lookup"><span data-stu-id="a21d7-109">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span> <span data-ttu-id="a21d7-110">Als u echter een gebeurtenis wilt door sturen naar de lokale sessie of een actie wilt opgeven om te reageren op de gebeurtenis, gebruikt u de `Register-EngineEvent` cmdlet om u te abonneren op de aangepaste gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-110">However, if you want to forward an event to the local session or specify an action to respond to the event, use the `Register-EngineEvent` cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="a21d7-111">Wanneer u zich abonneert op een aangepaste gebeurtenis, wordt de gebeurtenis abonnee toegevoegd aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="a21d7-111">When you subscribe to a custom event, the event subscriber is added to your session.</span></span> <span data-ttu-id="a21d7-112">Als u het gebeurtenis abonnement met behulp van de cmdlet annuleert `Unregister-Event` , worden de gebeurtenis abonnee en de aangepaste gebeurtenis verwijderd uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="a21d7-112">If you cancel the event subscription by using the `Unregister-Event` cmdlet, the event subscriber and custom event are deleted from the session.</span></span> <span data-ttu-id="a21d7-113">Als u zich niet hebt geabonneerd op de aangepaste gebeurtenis, moet u de programma voorwaarden wijzigen of de Power shell-sessie sluiten om de gebeurtenis te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a21d7-113">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="a21d7-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a21d7-114">EXAMPLES</span></span>

### <span data-ttu-id="a21d7-115">Voor beeld 1: een nieuwe gebeurtenis in de wachtrij voor gebeurtenissen maken</span><span class="sxs-lookup"><span data-stu-id="a21d7-115">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="a21d7-116">Met deze opdracht maakt u een nieuwe gebeurtenis in de Power shell-gebeurtenis wachtrij.</span><span class="sxs-lookup"><span data-stu-id="a21d7-116">This command creates a new event in the PowerShell event queue.</span></span> <span data-ttu-id="a21d7-117">Er wordt gebruikgemaakt van een **Windows. timer** -object voor het verzenden van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-117">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="a21d7-118">Voor beeld 2: een gebeurtenis activeren als reactie op een andere gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="a21d7-118">Example 2: Raise an event in response to another event</span></span>

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

<span data-ttu-id="a21d7-119">Deze voorbeeld functie maakt gebruik `New-Event` van de cmdlet om een gebeurtenis te genereren als reactie op een andere gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-119">This sample function uses the `New-Event` cmdlet to raise an event in response to another event.</span></span> <span data-ttu-id="a21d7-120">De opdracht gebruikt de `Register-ObjectEvent` cmdlet om u te abonneren op de gebeurtenis Windows Management Instrumentation (WMI) die wordt geactiveerd wanneer een nieuw proces wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a21d7-120">The command uses the `Register-ObjectEvent` cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span> <span data-ttu-id="a21d7-121">De opdracht gebruikt de **actie** parameter van de cmdlet om de cmdlet aan te roepen `New-Event` , waardoor de nieuwe gebeurtenis wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a21d7-121">The command uses the **Action** parameter of the cmdlet to call the `New-Event` cmdlet, which creates the new event.</span></span>

<span data-ttu-id="a21d7-122">Omdat de gebeurtenissen die `New-Event` worden gegenereerd automatisch worden toegevoegd aan de Power shell-gebeurtenis wachtrij, hoeft u zich niet te registreren voor die gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-122">Because the events that `New-Event` raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="a21d7-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a21d7-123">PARAMETERS</span></span>

### <span data-ttu-id="a21d7-124">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="a21d7-124">-EventArguments</span></span>

<span data-ttu-id="a21d7-125">Hiermee geeft u een object op dat opties bevat voor de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-125">Specifies an object that contains options for the event.</span></span>

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

### <span data-ttu-id="a21d7-126">-MessageData</span><span class="sxs-lookup"><span data-stu-id="a21d7-126">-MessageData</span></span>

<span data-ttu-id="a21d7-127">Hiermee geeft u aanvullende gegevens op die zijn gekoppeld aan de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-127">Specifies additional data associated with the event.</span></span> <span data-ttu-id="a21d7-128">De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van het object Event.</span><span class="sxs-lookup"><span data-stu-id="a21d7-128">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

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

### <span data-ttu-id="a21d7-129">-Sender</span><span class="sxs-lookup"><span data-stu-id="a21d7-129">-Sender</span></span>

<span data-ttu-id="a21d7-130">Hiermee geeft u het object op waarmee de gebeurtenis wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a21d7-130">Specifies the object that raises the event.</span></span> <span data-ttu-id="a21d7-131">De standaard waarde is de Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="a21d7-131">The default is the PowerShell engine.</span></span>

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

### <span data-ttu-id="a21d7-132">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="a21d7-132">-SourceIdentifier</span></span>

<span data-ttu-id="a21d7-133">Hiermee geeft u een naam op voor de nieuwe gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="a21d7-133">Specifies a name for the new event.</span></span> <span data-ttu-id="a21d7-134">Deze para meter is vereist en moet uniek zijn in de sessie.</span><span class="sxs-lookup"><span data-stu-id="a21d7-134">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="a21d7-135">De waarde van deze para meter wordt weer gegeven in de eigenschap **SourceIdentifier** van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="a21d7-135">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

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

### <span data-ttu-id="a21d7-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a21d7-136">CommonParameters</span></span>

<span data-ttu-id="a21d7-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a21d7-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a21d7-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a21d7-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a21d7-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="a21d7-139">INPUTS</span></span>

### <span data-ttu-id="a21d7-140">Geen</span><span class="sxs-lookup"><span data-stu-id="a21d7-140">None</span></span>

<span data-ttu-id="a21d7-141">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a21d7-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a21d7-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a21d7-142">OUTPUTS</span></span>

### <span data-ttu-id="a21d7-143">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="a21d7-143">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="a21d7-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a21d7-144">NOTES</span></span>

<span data-ttu-id="a21d7-145">Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.</span><span class="sxs-lookup"><span data-stu-id="a21d7-145">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="a21d7-146">De nieuwe aangepaste gebeurtenis, het gebeurtenis abonnement en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a21d7-146">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="a21d7-147">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="a21d7-147">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="a21d7-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a21d7-148">RELATED LINKS</span></span>

[<span data-ttu-id="a21d7-149">Get-Event</span><span class="sxs-lookup"><span data-stu-id="a21d7-149">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="a21d7-150">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="a21d7-150">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="a21d7-151">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="a21d7-151">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="a21d7-152">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="a21d7-152">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="a21d7-153">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="a21d7-153">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="a21d7-154">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="a21d7-154">Wait-Event</span></span>](Wait-Event.md)
