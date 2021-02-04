---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: 64d927907f995613d3e2260e5476b406949bc1aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706020"
---
# <span data-ttu-id="8ddb1-102">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="8ddb1-102">Register-EngineEvent</span></span>

## <span data-ttu-id="8ddb1-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8ddb1-103">SYNOPSIS</span></span>
<span data-ttu-id="8ddb1-104">Abonneren op gebeurtenissen die worden gegenereerd door de Power shell-engine en door de `New-Event` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-104">Subscribes to events that are generated by the PowerShell engine and by the `New-Event` cmdlet.</span></span>

## <span data-ttu-id="8ddb1-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8ddb1-105">SYNTAX</span></span>

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="8ddb1-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8ddb1-106">DESCRIPTION</span></span>

<span data-ttu-id="8ddb1-107">De `Register-EngineEvent` cmdlet abonneert zich op gebeurtenissen die worden gegenereerd door de Power shell-engine en de `New-Event` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-107">The `Register-EngineEvent` cmdlet subscribes to events that are generated by the PowerShell engine and the `New-Event` cmdlet.</span></span> <span data-ttu-id="8ddb1-108">Gebruik de para meter **SourceIdentifier** om de gebeurtenis op te geven.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-108">Use the **SourceIdentifier** parameter to specify the event.</span></span>

<span data-ttu-id="8ddb1-109">U kunt deze cmdlet gebruiken om u te abonneren op de gebeurtenis van de **afsluit** engine en de gebeurtenissen die door de cmdlet worden gegenereerd `New-Event` .</span><span class="sxs-lookup"><span data-stu-id="8ddb1-109">You can use this cmdlet to subscribe to the **Exiting** engine event and events generated by the `New-Event` cmdlet.</span></span> <span data-ttu-id="8ddb1-110">Deze gebeurtenissen worden automatisch toegevoegd aan uw gebeurtenis wachtrij in uw sessie zonder dat u zich abonneert.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-110">These events are automatically added to your event queue in your session without subscribing.</span></span> <span data-ttu-id="8ddb1-111">Met abonneren kunt u de gebeurtenissen echter door sturen, een actie opgeven die op de gebeurtenissen reageert en het abonnement annuleren.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-111">However, subscribing lets you forward the events, specify an action to respond to the events, and cancel the subscription.</span></span>

<span data-ttu-id="8ddb1-112">Wanneer de geabonneerde gebeurtenis is gegenereerd, wordt deze toegevoegd aan de gebeurtenis wachtrij in uw sessie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-112">When the subscribed event is raised, it is added to the event queue in your session.</span></span> <span data-ttu-id="8ddb1-113">Gebruik de cmdlet om gebeurtenissen in de gebeurtenis wachtrij op te halen `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="8ddb1-113">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="8ddb1-114">Wanneer u zich abonneert op een gebeurtenis, wordt een gebeurtenis abonnee toegevoegd aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-114">When you subscribe to a event, an event subscriber is added to your session.</span></span> <span data-ttu-id="8ddb1-115">Als u de gebeurtenis abonnees in de sessie wilt ophalen, gebruikt u de `Get-EventSubscriber` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-115">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="8ddb1-116">Als u het abonnement wilt annuleren, gebruikt u de `Unregister-Event` cmdlet waarmee de gebeurtenis abonnee uit de sessie wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-116">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

## <span data-ttu-id="8ddb1-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8ddb1-117">EXAMPLES</span></span>

### <span data-ttu-id="8ddb1-118">Voor beeld 1: een Power shell-engine gebeurtenis op externe computers registreren</span><span class="sxs-lookup"><span data-stu-id="8ddb1-118">Example 1: Register a PowerShell engine event on remote computers</span></span>

<span data-ttu-id="8ddb1-119">Dit voor beeld registreert voor een Power shell-engine gebeurtenis op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-119">This example registers for a PowerShell engine event on two remote computers.</span></span>

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S {
Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward
}
```

<span data-ttu-id="8ddb1-120">`New-PSSession` Hiermee maakt u een door de gebruiker beheerde sessie (PSSession) op elke externe computer. De `Invoke-Command` cmdlet voert de `Register-EngineEvent` opdracht uit in de externe sessies.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-120">`New-PSSession` creates a user-managed session (PSSession) on each of the remote computers.The `Invoke-Command` cmdlet runs the `Register-EngineEvent` command in the remote sessions.</span></span>
<span data-ttu-id="8ddb1-121">`Register-EngineEvent` maakt gebruik van de para meter **SourceIdentifier** om de gebeurtenis te identificeren.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-121">`Register-EngineEvent` uses the **SourceIdentifier** parameter to identify the event.</span></span> <span data-ttu-id="8ddb1-122">Met de para meter **Forward** wordt de engine verteld om de gebeurtenissen van de externe sessie door te sturen naar de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-122">The **Forward** parameter tell the engine to forward the events from the remote session to the local session.</span></span>

### <span data-ttu-id="8ddb1-123">Voor beeld 2: een opgegeven actie uitvoeren wanneer de gebeurtenis afsluiten plaatsvindt</span><span class="sxs-lookup"><span data-stu-id="8ddb1-123">Example 2: Take a specified action when the Exiting event occurs</span></span>

<span data-ttu-id="8ddb1-124">Dit voor beeld laat zien hoe u `Register-EngineEvent` kunt uitvoeren om een specifieke actie uit te voeren wanneer de **Power shell. exiting** -gebeurtenis plaatsvindt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-124">This example shows how to run `Register-EngineEvent` to take a specific action when the **PowerShell.Exiting** event occurs.</span></span>

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

<span data-ttu-id="8ddb1-125">De para meter **SupportEvent** wordt toegevoegd om het gebeurtenis abonnement te verbergen.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-125">The **SupportEvent** parameter is added to hide the event subscription.</span></span> <span data-ttu-id="8ddb1-126">Wanneer Power shell wordt afgesloten, wordt in dit geval de opdracht geschiedenis van de afsluit sessie een XML-bestand in de map van de gebruiker geëxporteerd `$Home` .</span><span class="sxs-lookup"><span data-stu-id="8ddb1-126">When PowerShell exits, in this case, the command history from the exiting session is exported an XML file in the user's `$Home` directory.</span></span>

### <span data-ttu-id="8ddb1-127">Voor beeld 3: een door de gebruiker gedefinieerde gebeurtenis maken en abonneren</span><span class="sxs-lookup"><span data-stu-id="8ddb1-127">Example 3: Create and subscribe to a user-defined event</span></span>

<span data-ttu-id="8ddb1-128">In dit voor beeld wordt een abonnement gemaakt voor gebeurtenissen uit de bron- **MyEventSource**.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-128">This example creates a subscription for events from the source **MyEventSource**.</span></span> <span data-ttu-id="8ddb1-129">Dit is een wille keurige bron die we gaan gebruiken om de voortgang van een taak te bewaken.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-129">This is an arbitrary source that we are going to use to monitor the progress of a job.</span></span> <span data-ttu-id="8ddb1-130">`Register-EngineEvent` wordt gebruikt om het abonnement te maken.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-130">`Register-EngineEvent` is used to create the subscription.</span></span> <span data-ttu-id="8ddb1-131">Het script blok voor de **actie** parameter registreert de gebeurtenis gegevens in een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-131">The script block for the **Action** parameter logs the event data to a text file.</span></span>

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

<span data-ttu-id="8ddb1-132">`Register-EngineEvent` Taak-id 18 gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-132">`Register-EngineEvent` created Job Id 18.</span></span> <span data-ttu-id="8ddb1-133">`Start-Job` Er is een taak-id 19 gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-133">`Start-Job` created Job Id 19.</span></span> <span data-ttu-id="8ddb1-134">In voor beeld #4 worden het gebeurtenis abonnement en de taken verwijderd, waarna het logboek bestand wordt gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-134">In Example #4, we remove the event subscription and the jobs, then inspect the log file.</span></span>

### <span data-ttu-id="8ddb1-135">Voor beeld 4: registratie van gebeurtenissen opheffen en taken opschonen</span><span class="sxs-lookup"><span data-stu-id="8ddb1-135">Example 4: Unregister events and clean up jobs</span></span>

<span data-ttu-id="8ddb1-136">Dit is een voortzetting van voor beeld 3.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-136">This is a continuation of Example 3.</span></span> <span data-ttu-id="8ddb1-137">In dit voor beeld wachten we tien seconden om verschillende gebeurtenissen te laten optreden.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-137">In this example we wait for 10 seconds to let several events occur.</span></span> <span data-ttu-id="8ddb1-138">Vervolgens wordt de registratie van het gebeurtenis abonnement ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-138">Then we unregister the event subscription.</span></span>

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

<span data-ttu-id="8ddb1-139">De `Unregister-Event` cmdlet stopt de taak die is gekoppeld aan het gebeurtenis abonnement (taak-id 18).</span><span class="sxs-lookup"><span data-stu-id="8ddb1-139">The `Unregister-Event` cmdlet stops the job associated with the event subscription (Job Id 18).</span></span> <span data-ttu-id="8ddb1-140">Taak-id 19 wordt nog steeds uitgevoerd en er worden nieuwe gebeurtenissen gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-140">Job Id 19 is still running and creating new events.</span></span> <span data-ttu-id="8ddb1-141">We gebruiken de **taak** -cmdlets om de taak te stoppen en de overbodige taak objecten te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-141">We use the **Job** cmdlets stop the job and remove the unneeded job objects.</span></span> <span data-ttu-id="8ddb1-142">`Get-Content` Hiermee wordt de inhoud van het logboek bestand weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-142">`Get-Content` displays the contents of the log file.</span></span>

## <span data-ttu-id="8ddb1-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ddb1-143">PARAMETERS</span></span>

### <span data-ttu-id="8ddb1-144">-Actie</span><span class="sxs-lookup"><span data-stu-id="8ddb1-144">-Action</span></span>

<span data-ttu-id="8ddb1-145">Geeft opdrachten voor het afhandelen van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-145">Specifies commands to handle the events.</span></span> <span data-ttu-id="8ddb1-146">De opdrachten in de **actie** worden uitgevoerd wanneer een gebeurtenis wordt gegenereerd, in plaats van de gebeurtenis naar de gebeurtenis wachtrij te verzenden.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-146">The commands in the **Action** run when an event is raised, instead of sending the event to the event queue.</span></span> <span data-ttu-id="8ddb1-147">Plaats de opdrachten tussen accolades ({}) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-147">Enclose the commands in braces ( { } ) to create a script block.</span></span>

<span data-ttu-id="8ddb1-148">De waarde van de **actie** parameter kan de `$Event` variabelen, `$EventSubscriber` , `$Sender` , `$EventArgs` en `$Args` automatisch bevatten, die informatie geven over de gebeurtenis in het **actie** script blok.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-148">The value of the **Action** parameter can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables, which provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="8ddb1-149">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-149">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="8ddb1-150">Wanneer u een actie opgeeft, `Register-EngineEvent` retourneert een gebeurtenis taak object dat die actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-150">When you specify an action, `Register-EngineEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="8ddb1-151">U kunt de taak-cmdlets gebruiken om de gebeurtenis taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-151">You can use the Job cmdlets to manage the event job.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ddb1-152">-Voorwaarts</span><span class="sxs-lookup"><span data-stu-id="8ddb1-152">-Forward</span></span>

<span data-ttu-id="8ddb1-153">Geeft aan dat de cmdlet gebeurtenissen voor dit abonnement naar de sessie op de lokale computer verzendt.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-153">Indicates that the cmdlet sends events for this subscription to the session on the local computer.</span></span>
<span data-ttu-id="8ddb1-154">Gebruik deze para meter als u zich registreert voor gebeurtenissen op een externe computer of in een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-154">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="8ddb1-155">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="8ddb1-155">-MaxTriggerCount</span></span>

<span data-ttu-id="8ddb1-156">Hiermee geeft u het maximum aantal keer op dat de actie voor het gebeurtenis abonnement wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-156">Specifies the maximum number of times that the action will be executed for the event subscription.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ddb1-157">-MessageData</span><span class="sxs-lookup"><span data-stu-id="8ddb1-157">-MessageData</span></span>

<span data-ttu-id="8ddb1-158">Hiermee geeft u aanvullende gegevens op die zijn gekoppeld aan de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-158">Specifies additional data associated with the event.</span></span> <span data-ttu-id="8ddb1-159">De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van het object Event.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-159">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ddb1-160">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="8ddb1-160">-SourceIdentifier</span></span>

<span data-ttu-id="8ddb1-161">Hiermee geeft u de bron-id op van de gebeurtenis waarop u bent geabonneerd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-161">Specifies the source identifier of the event to which you are subscribing.</span></span> <span data-ttu-id="8ddb1-162">De bron-id moet uniek zijn in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-162">The source identifier must be unique in the current session.</span></span> <span data-ttu-id="8ddb1-163">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-163">This parameter is required.</span></span>

<span data-ttu-id="8ddb1-164">De waarde van deze para meter wordt weer gegeven in de waarde van de eigenschap **SourceIdentifier** van het object Subscriber en alle gebeurtenis objecten die zijn gekoppeld aan dit abonnement.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-164">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and of all event objects associated with this subscription.</span></span>

<span data-ttu-id="8ddb1-165">De waarde is specifiek voor de bron van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-165">The value is specific to the source of the event.</span></span> <span data-ttu-id="8ddb1-166">Dit kan een wille keurige waarde zijn die u hebt gemaakt voor gebruik met de `New-Event` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-166">This can be an arbitrary value you created to use with the `New-Event` cmdlet.</span></span> <span data-ttu-id="8ddb1-167">De Power shell-Engine ondersteunt de **EngineEvent** -waarden **Power shell. exiting** en **Power shell. OnIdle**.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-167">The PowerShell engine supports the **EngineEvent** values **PowerShell.Exiting** and **PowerShell.OnIdle**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ddb1-168">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="8ddb1-168">-SupportEvent</span></span>

<span data-ttu-id="8ddb1-169">Hiermee wordt aangegeven dat het gebeurtenis abonnement wordt verborgen met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-169">Indicates that the cmdlet hides the event subscription.</span></span> <span data-ttu-id="8ddb1-170">Voeg deze para meter toe wanneer het huidige abonnement deel uitmaakt van een complexere gebeurtenis registratie mechanisme en niet onafhankelijk moet worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-170">Add this parameter when the current subscription is part of a more complex event registration mechanism and it should not be discovered independently.</span></span>

<span data-ttu-id="8ddb1-171">Als u een abonnement wilt bekijken of annuleren dat is gemaakt met de para meter **SupportEvent** , voegt u de para meter **Force** toe aan de `Get-EventSubscriber` `Unregister-Event` cmdlets of.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-171">To view or cancel a subscription that was created with the **SupportEvent** parameter, add the **Force** parameter to the `Get-EventSubscriber` or `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="8ddb1-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ddb1-172">CommonParameters</span></span>

<span data-ttu-id="8ddb1-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ddb1-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ddb1-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="8ddb1-175">INPUTS</span></span>

### <span data-ttu-id="8ddb1-176">Geen</span><span class="sxs-lookup"><span data-stu-id="8ddb1-176">None</span></span>

<span data-ttu-id="8ddb1-177">U kunt geen pipe invoer naar `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="8ddb1-177">You cannot pipe input to `Register-EngineEvent`.</span></span>

## <span data-ttu-id="8ddb1-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8ddb1-178">OUTPUTS</span></span>

### <span data-ttu-id="8ddb1-179">Geen of System. Management. Automation. PSEventJob</span><span class="sxs-lookup"><span data-stu-id="8ddb1-179">None or System.Management.Automation.PSEventJob</span></span>

<span data-ttu-id="8ddb1-180">Als u de **actie** parameter gebruikt, `Register-EngineEvent` retourneert een **System. Management. Automation. PSEventJob** -object.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-180">If you use the **Action** parameter, `Register-EngineEvent` returns a **System.Management.Automation.PSEventJob** object.</span></span> <span data-ttu-id="8ddb1-181">Anders wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-181">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="8ddb1-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8ddb1-182">NOTES</span></span>

<span data-ttu-id="8ddb1-183">Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-183">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="8ddb1-184">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-184">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="8ddb1-185">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="8ddb1-185">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="8ddb1-186">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8ddb1-186">RELATED LINKS</span></span>

[<span data-ttu-id="8ddb1-187">Get-Event</span><span class="sxs-lookup"><span data-stu-id="8ddb1-187">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="8ddb1-188">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="8ddb1-188">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="8ddb1-189">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="8ddb1-189">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="8ddb1-190">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="8ddb1-190">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="8ddb1-191">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="8ddb1-191">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="8ddb1-192">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="8ddb1-192">Wait-Event</span></span>](Wait-Event.md)