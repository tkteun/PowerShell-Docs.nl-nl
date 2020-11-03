---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: c621ef5b76d4e282f4108094a79c8617bf6bb817
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250440"
---
# <span data-ttu-id="eae54-103">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="eae54-103">Get-EventSubscriber</span></span>

## <span data-ttu-id="eae54-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="eae54-104">SYNOPSIS</span></span>
<span data-ttu-id="eae54-105">Hiermee haalt u de gebeurtenis abonnees op in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eae54-105">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="eae54-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="eae54-106">SYNTAX</span></span>

### <span data-ttu-id="eae54-107">BySource (standaard)</span><span class="sxs-lookup"><span data-stu-id="eae54-107">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="eae54-108">ById</span><span class="sxs-lookup"><span data-stu-id="eae54-108">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="eae54-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="eae54-109">DESCRIPTION</span></span>
<span data-ttu-id="eae54-110">De cmdlet **Get-EventSubscriber** haalt de gebeurtenis abonnees op in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eae54-110">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="eae54-111">Wanneer u zich abonneert op een gebeurtenis met behulp van een gebeurtenis-cmdlet registreren, wordt een gebeurtenis abonnee toegevoegd aan uw Windows Power shell-sessie en worden de gebeurtenissen waarop u bent geabonneerd aan uw gebeurtenis wachtrij toegevoegd wanneer deze worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-111">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your Windows PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="eae54-112">Als u een gebeurtenis abonnement wilt annuleren, verwijdert u de Event Subscriber met behulp van de cmdlet Unregister-Event.</span><span class="sxs-lookup"><span data-stu-id="eae54-112">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="eae54-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="eae54-113">EXAMPLES</span></span>

### <span data-ttu-id="eae54-114">Voor beeld 1: de gebeurtenis abonnee voor een timer gebeurtenis ophalen</span><span class="sxs-lookup"><span data-stu-id="eae54-114">Example 1: Get the event subscriber for a timer event</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

<span data-ttu-id="eae54-115">In dit voor beeld wordt de opdracht **Get-EventSubscriber** gebruikt om de Event Subscriber voor een timer gebeurtenis op te halen.</span><span class="sxs-lookup"><span data-stu-id="eae54-115">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="eae54-116">De eerste opdracht gebruikt de cmdlet New-Object om een exemplaar van een timer object te maken.</span><span class="sxs-lookup"><span data-stu-id="eae54-116">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="eae54-117">Het nieuwe timer object wordt opgeslagen in de variabele $Timer.</span><span class="sxs-lookup"><span data-stu-id="eae54-117">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="eae54-118">De tweede opdracht maakt gebruik van de cmdlet Get-Member om de gebeurtenissen weer te geven die beschikbaar zijn voor timer-objecten.</span><span class="sxs-lookup"><span data-stu-id="eae54-118">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="eae54-119">De opdracht maakt gebruik van de para meter type van de cmdlet **Get-member** met de waarde Event.</span><span class="sxs-lookup"><span data-stu-id="eae54-119">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="eae54-120">De derde opdracht gebruikt de cmdlet Register-ObjectEvent om u te registreren voor de verstreken gebeurtenis van het object Timer.</span><span class="sxs-lookup"><span data-stu-id="eae54-120">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="eae54-121">De vierde opdracht maakt gebruik van de cmdlet **Get-EventSubscriber** om de gebeurtenis abonnee voor de verstreken gebeurtenis op te halen.</span><span class="sxs-lookup"><span data-stu-id="eae54-121">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="eae54-122">Voor beeld 2: de dynamische module in PSEventJob gebruiken in de eigenschap Action van de abonnee van de gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="eae54-122">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

<span data-ttu-id="eae54-123">In dit voor beeld ziet u hoe u de dynamische module gebruikt in het object **PSEventJob** in de eigenschap Action van de abonnee van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="eae54-123">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="eae54-124">De eerste opdracht maakt gebruik van de cmdlet New-Object om een timer object te maken.</span><span class="sxs-lookup"><span data-stu-id="eae54-124">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="eae54-125">Met de tweede opdracht wordt het interval van de timer ingesteld op 500 (milliseconden).</span><span class="sxs-lookup"><span data-stu-id="eae54-125">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="eae54-126">De derde opdracht gebruikt de cmdlet Register-ObjectEvent om de verstreken gebeurtenis van het object Timer te registreren.</span><span class="sxs-lookup"><span data-stu-id="eae54-126">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="eae54-127">De opdracht bevat een actie waarmee de gebeurtenis wordt afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="eae54-127">The command includes an action that handles the event.</span></span>
<span data-ttu-id="eae54-128">Wanneer het timer interval is verstreken, wordt een gebeurtenis gegenereerd en worden de opdrachten in de actie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-128">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="eae54-129">In dit geval genereert de cmdlet Get-Random een wille keurig getal tussen 0 en 100 en slaat dit op in de $Random variabele.</span><span class="sxs-lookup"><span data-stu-id="eae54-129">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="eae54-130">De bron-id van de gebeurtenis is timer. wille keurig.</span><span class="sxs-lookup"><span data-stu-id="eae54-130">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="eae54-131">Wanneer u een *actie* parameter gebruikt in een **REGI ster-ObjectEvent** opdracht, retourneert de opdracht een **PSEventJob** -object dat de actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="eae54-131">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="eae54-132">Met de vierde opdracht wordt de timer ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="eae54-132">The fourth command enables the timer.</span></span>

<span data-ttu-id="eae54-133">De vijfde opdracht maakt gebruik van de cmdlet **Get-EventSubscriber** om de gebeurtenis abonnee van de timer. wille keurige gebeurtenis op te halen.</span><span class="sxs-lookup"><span data-stu-id="eae54-133">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="eae54-134">Het event Subscriber-object wordt opgeslagen in de variabele $Subscriber.</span><span class="sxs-lookup"><span data-stu-id="eae54-134">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="eae54-135">De zesde opdracht geeft aan dat de eigenschap Action van het object Event Subscriber een **PSEventJob** -object bevat.</span><span class="sxs-lookup"><span data-stu-id="eae54-135">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="eae54-136">Het bevat eigenlijk hetzelfde **PSEventJob** -object dat de opdracht **REGI ster-ObjectEvent** heeft geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-136">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="eae54-137">De zevende opdracht maakt gebruik van de cmdlet Format-List om alle eigenschappen van het object **PSEventJob** in de eigenschap Action in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="eae54-137">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="eae54-138">Het resultaat blijkt dat het object **PSEventJob** een module-eigenschap heeft die een dynamische script module bevat waarmee de actie wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-138">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="eae54-139">De overige opdrachten gebruiken de aanroep operator (&) om de opdracht in de module aan te roepen en de waarde van de $Random variabele weer te geven.</span><span class="sxs-lookup"><span data-stu-id="eae54-139">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="eae54-140">U kunt de aanroep operator gebruiken om een wille keurige opdracht aan te roepen in een module, met inbegrip van opdrachten die niet worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-140">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="eae54-141">In dit geval geven de opdrachten het wille keurig getal weer dat wordt gegenereerd wanneer de verstreken gebeurtenis optreedt.</span><span class="sxs-lookup"><span data-stu-id="eae54-141">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="eae54-142">Zie [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="eae54-142">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="eae54-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eae54-143">PARAMETERS</span></span>

### <span data-ttu-id="eae54-144">-Force</span><span class="sxs-lookup"><span data-stu-id="eae54-144">-Force</span></span>
<span data-ttu-id="eae54-145">Hiermee wordt aangegeven dat met deze cmdlet alle gebeurtenis abonnees worden opgehaald, waaronder abonnees voor gebeurtenissen die zijn verborgen met de para meter *SupportEvent* van Regi ster-ObjectEvent, REGI ster-WmiEvent en REGI ster-EngineEvent.</span><span class="sxs-lookup"><span data-stu-id="eae54-145">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eae54-146">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="eae54-146">-SourceIdentifier</span></span>
<span data-ttu-id="eae54-147">Hiermee wordt de waarde van de eigenschap **SourceIdentifier** opgegeven waarmee alleen de gebeurtenis abonnees worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eae54-147">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="eae54-148">**Get-EventSubscriber** haalt standaard alle gebeurtenis abonnees op in de sessie.</span><span class="sxs-lookup"><span data-stu-id="eae54-148">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="eae54-149">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="eae54-149">Wildcards are not permitted.</span></span>
<span data-ttu-id="eae54-150">Deze para meter is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="eae54-150">This parameter is case-sensitive.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eae54-151">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="eae54-151">-SubscriptionId</span></span>
<span data-ttu-id="eae54-152">Hiermee geeft u de abonnements-id op die met deze cmdlet wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eae54-152">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="eae54-153">**Get-EventSubscriber** haalt standaard alle gebeurtenis abonnees op in de sessie.</span><span class="sxs-lookup"><span data-stu-id="eae54-153">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="eae54-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eae54-154">CommonParameters</span></span>
<span data-ttu-id="eae54-155">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eae54-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eae54-156">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eae54-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eae54-157">INVOER</span><span class="sxs-lookup"><span data-stu-id="eae54-157">INPUTS</span></span>

### <span data-ttu-id="eae54-158">Geen</span><span class="sxs-lookup"><span data-stu-id="eae54-158">None</span></span>
<span data-ttu-id="eae54-159">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eae54-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="eae54-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="eae54-160">OUTPUTS</span></span>

### <span data-ttu-id="eae54-161">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="eae54-161">System.Management.Automation.PSEventSubscriber</span></span>
<span data-ttu-id="eae54-162">**Get-EventSubscriber** retourneert een-object dat elke gebeurtenis abonnee vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="eae54-162">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="eae54-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="eae54-163">NOTES</span></span>

* <span data-ttu-id="eae54-164">Met de cmdlet New-Event, die een aangepaste gebeurtenis maakt, wordt er geen abonnee gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-164">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="eae54-165">Daarom kan de cmdlet **Get-EventSubscriber** geen Subscriber-object vinden voor deze gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="eae54-165">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="eae54-166">Als u echter de Register-EngineEvent cmdlet gebruikt om u te abonneren op een aangepaste gebeurtenis (als u de gebeurtenis wilt door sturen of als u een actie wilt opgeven), wordt met **Get-EventSubscriber** de abonnee gezocht die door **REGI ster-EngineEvent** wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-166">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="eae54-167">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eae54-167">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="eae54-168">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="eae54-168">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="eae54-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="eae54-169">RELATED LINKS</span></span>

[<span data-ttu-id="eae54-170">Get-Event</span><span class="sxs-lookup"><span data-stu-id="eae54-170">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="eae54-171">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="eae54-171">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="eae54-172">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="eae54-172">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="eae54-173">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="eae54-173">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="eae54-174">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="eae54-174">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="eae54-175">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="eae54-175">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="eae54-176">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="eae54-176">Wait-Event</span></span>](Wait-Event.md)
