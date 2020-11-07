---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 45d9e45bfbbeba7b9467985dc6abf3a28cd8702b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342345"
---
# <span data-ttu-id="ce30a-103">Get-Event</span><span class="sxs-lookup"><span data-stu-id="ce30a-103">Get-Event</span></span>

## <span data-ttu-id="ce30a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ce30a-104">SYNOPSIS</span></span>
<span data-ttu-id="ce30a-105">Hiermee haalt u de gebeurtenissen in de wachtrij van de gebeurtenis op.</span><span class="sxs-lookup"><span data-stu-id="ce30a-105">Gets the events in the event queue.</span></span>

## <span data-ttu-id="ce30a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ce30a-106">SYNTAX</span></span>

### <span data-ttu-id="ce30a-107">BySource (standaard)</span><span class="sxs-lookup"><span data-stu-id="ce30a-107">BySource (Default)</span></span>

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### <span data-ttu-id="ce30a-108">ById</span><span class="sxs-lookup"><span data-stu-id="ce30a-108">ById</span></span>

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## <span data-ttu-id="ce30a-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ce30a-109">DESCRIPTION</span></span>

<span data-ttu-id="ce30a-110">De `Get-Event` cmdlet haalt gebeurtenissen op in de Power shell-gebeurtenis wachtrij voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ce30a-110">The `Get-Event` cmdlet gets events in the PowerShell event queue for the current session.</span></span> <span data-ttu-id="ce30a-111">U kunt alle gebeurtenissen ophalen of de para meter **EventIdentifier** of **SourceIdentifier** gebruiken om de gebeurtenissen op te geven.</span><span class="sxs-lookup"><span data-stu-id="ce30a-111">You can get all events or use the **EventIdentifier** or **SourceIdentifier** parameter to specify the events.</span></span>

<span data-ttu-id="ce30a-112">Wanneer er een gebeurtenis optreedt, wordt deze toegevoegd aan de gebeurtenis wachtrij.</span><span class="sxs-lookup"><span data-stu-id="ce30a-112">When an event occurs, it is added to the event queue.</span></span> <span data-ttu-id="ce30a-113">De gebeurtenissen wachtrij bevat gebeurtenissen waarvoor u bent geregistreerd, gebeurtenissen die zijn gemaakt met behulp van de `New-Event` cmdlet en de gebeurtenis die optreedt wanneer Power shell wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="ce30a-113">The event queue includes events for which you have registered, events created by using the `New-Event` cmdlet, and the event that is raised when PowerShell exits.</span></span> <span data-ttu-id="ce30a-114">U kunt `Get-Event` of gebruiken `Wait-Event` om de gebeurtenissen op te halen.</span><span class="sxs-lookup"><span data-stu-id="ce30a-114">You can use `Get-Event` or `Wait-Event` to get the events.</span></span>

<span data-ttu-id="ce30a-115">Met deze cmdlet worden geen gebeurtenissen uit de Logboeken Logboeken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ce30a-115">This cmdlet does not get events from the Event Viewer logs.</span></span> <span data-ttu-id="ce30a-116">Gebruik of om deze gebeurtenissen op te halen `Get-WinEvent` `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="ce30a-116">To get those events, use `Get-WinEvent` or `Get-EventLog`.</span></span>

## <span data-ttu-id="ce30a-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ce30a-117">EXAMPLES</span></span>

### <span data-ttu-id="ce30a-118">Voor beeld 1: alle gebeurtenissen ophalen</span><span class="sxs-lookup"><span data-stu-id="ce30a-118">Example 1: Get all events</span></span>

```
PS C:\> Get-Event
```

<span data-ttu-id="ce30a-119">Met deze opdracht worden alle gebeurtenissen in de wachtrij van de gebeurtenis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ce30a-119">This command gets all events in the event queue.</span></span>

### <span data-ttu-id="ce30a-120">Voor beeld 2: gebeurtenissen ophalen op bron-id</span><span class="sxs-lookup"><span data-stu-id="ce30a-120">Example 2: Get events by source identifier</span></span>

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

<span data-ttu-id="ce30a-121">Met deze opdracht worden gebeurtenissen opgehaald waarin de waarde van de eigenschap SourceIdentifier Power shell. ProcessCreated is.</span><span class="sxs-lookup"><span data-stu-id="ce30a-121">This command gets events in which the value of the SourceIdentifier property is PowerShell.ProcessCreated.</span></span>

### <span data-ttu-id="ce30a-122">Voor beeld 3: een gebeurtenis ophalen op basis van de tijd dat deze is gegenereerd</span><span class="sxs-lookup"><span data-stu-id="ce30a-122">Example 3: Get an event based on the time it was generated</span></span>

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

<span data-ttu-id="ce30a-123">In dit voor beeld ziet u hoe u gebeurtenissen kunt ophalen met behulp van andere eigenschappen dan SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ce30a-123">This example shows how to get events by using properties other than SourceIdentifier.</span></span>

<span data-ttu-id="ce30a-124">Met de eerste opdracht worden alle gebeurtenissen in de gebeurtenis wachtrij opgehaald en opgeslagen in de `$Events` variabele.</span><span class="sxs-lookup"><span data-stu-id="ce30a-124">The first command gets all events in the event queue and saves them in the `$Events` variable.</span></span>

<span data-ttu-id="ce30a-125">De tweede opdracht maakt gebruik van de matrix notatie om de eerste (0-index) gebeurtenis op te halen in de matrix in de `$Events` variabele.</span><span class="sxs-lookup"><span data-stu-id="ce30a-125">The second command uses array notation to get the first (0-index) event in the array in the `$Events` variable.</span></span> <span data-ttu-id="ce30a-126">De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de gebeurtenis naar de `Format-List` opdracht te verzenden, waarin alle eigenschappen van de gebeurtenis in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ce30a-126">The command uses a pipeline operator (`|`) to send the event to the `Format-List` command, which displays all properties of the event in a list.</span></span> <span data-ttu-id="ce30a-127">Hiermee kunt u de eigenschappen van het gebeurtenis object controleren.</span><span class="sxs-lookup"><span data-stu-id="ce30a-127">This allows you to examine the properties of the event object.</span></span>

<span data-ttu-id="ce30a-128">De derde opdracht laat zien hoe u de `Where-Object` cmdlet gebruikt om een gebeurtenis op te halen op basis van de tijd dat deze is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ce30a-128">The third command shows how to use the `Where-Object` cmdlet to get an event based on the time that it was generated.</span></span>

### <span data-ttu-id="ce30a-129">Voor beeld 4: een gebeurtenis op basis van de id ophalen</span><span class="sxs-lookup"><span data-stu-id="ce30a-129">Example 4: Get an event by its identifier</span></span>

```
PS C:\> Get-Event -EventIdentifier 2
```

<span data-ttu-id="ce30a-130">Met deze opdracht wordt de gebeurtenis met de gebeurtenis-id 2 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ce30a-130">This command gets the event with an event identifier of 2.</span></span>

## <span data-ttu-id="ce30a-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ce30a-131">PARAMETERS</span></span>

### <span data-ttu-id="ce30a-132">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="ce30a-132">-EventIdentifier</span></span>

<span data-ttu-id="ce30a-133">Hiermee geeft u de gebeurtenis-id's op waarvoor deze cmdlet gebeurtenissen ontvangt.</span><span class="sxs-lookup"><span data-stu-id="ce30a-133">Specifies the event identifiers for which this cmdlet gets events.</span></span>

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

### <span data-ttu-id="ce30a-134">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="ce30a-134">-SourceIdentifier</span></span>

<span data-ttu-id="ce30a-135">Hiermee geeft u de bron-id's op waarvoor deze cmdlet gebeurtenissen ontvangt.</span><span class="sxs-lookup"><span data-stu-id="ce30a-135">Specifies source identifiers for which this cmdlet gets events.</span></span> <span data-ttu-id="ce30a-136">De standaard instelling is alle gebeurtenissen in de wachtrij van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="ce30a-136">The default is all events in the event queue.</span></span> <span data-ttu-id="ce30a-137">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ce30a-137">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="ce30a-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce30a-138">CommonParameters</span></span>

<span data-ttu-id="ce30a-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce30a-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce30a-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ce30a-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ce30a-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="ce30a-141">INPUTS</span></span>

### <span data-ttu-id="ce30a-142">Geen</span><span class="sxs-lookup"><span data-stu-id="ce30a-142">None</span></span>

<span data-ttu-id="ce30a-143">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce30a-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ce30a-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ce30a-144">OUTPUTS</span></span>

### <span data-ttu-id="ce30a-145">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="ce30a-145">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="ce30a-146">`Get-Event` retourneert een **PSEventArgs** -object voor elke gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="ce30a-146">`Get-Event` returns a **PSEventArgs** object for each event.</span></span> <span data-ttu-id="ce30a-147">Als u een beschrijving van dit object wilt weer geven, typt `Get-Help Get-Event -Full` en raadpleegt u de sectie Notities van het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="ce30a-147">To see a description of this object, type `Get-Help Get-Event -Full` and see the Notes section of the help topic.</span></span>

## <span data-ttu-id="ce30a-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ce30a-148">NOTES</span></span>

<span data-ttu-id="ce30a-149">Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.</span><span class="sxs-lookup"><span data-stu-id="ce30a-149">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="ce30a-150">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ce30a-150">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="ce30a-151">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="ce30a-151">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="ce30a-152">De `Get-Event` cmdlet retourneert een **PSEventArgs** -object ( **System. Management. Automation. PSEventArgs** ) met de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="ce30a-152">The `Get-Event` cmdlet returns a **PSEventArgs** object ( **System.Management.Automation.PSEventArgs** ) with the following properties:</span></span>

- <span data-ttu-id="ce30a-153">ComputerName.</span><span class="sxs-lookup"><span data-stu-id="ce30a-153">ComputerName.</span></span> <span data-ttu-id="ce30a-154">De naam van de computer waarop de gebeurtenis heeft plaatsgevonden.</span><span class="sxs-lookup"><span data-stu-id="ce30a-154">The name of the computer on which the event occurred.</span></span> <span data-ttu-id="ce30a-155">Deze eigenschaps waarde wordt alleen ingevuld wanneer de gebeurtenis wordt doorgestuurd vanaf een externe computer.</span><span class="sxs-lookup"><span data-stu-id="ce30a-155">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="ce30a-156">RunspaceId.</span><span class="sxs-lookup"><span data-stu-id="ce30a-156">RunspaceId.</span></span> <span data-ttu-id="ce30a-157">Een GUID die een unieke identificatie vormt van de sessie waarin de gebeurtenis heeft plaatsgevonden.</span><span class="sxs-lookup"><span data-stu-id="ce30a-157">A GUID that uniquely identifies the session in which the event occurred.</span></span> <span data-ttu-id="ce30a-158">Deze eigenschaps waarde wordt alleen ingevuld wanneer de gebeurtenis wordt doorgestuurd vanaf een externe computer.</span><span class="sxs-lookup"><span data-stu-id="ce30a-158">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="ce30a-159">EventIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ce30a-159">EventIdentifier.</span></span> <span data-ttu-id="ce30a-160">Een geheel getal (INT32) waarmee de gebeurtenis melding in de huidige sessie op unieke wijze wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="ce30a-160">An integer (Int32) that uniquely identifies the event notification in the current session.</span></span>

- <span data-ttu-id="ce30a-161">SenderName.</span><span class="sxs-lookup"><span data-stu-id="ce30a-161">Sender.</span></span> <span data-ttu-id="ce30a-162">Het object dat de gebeurtenis heeft gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ce30a-162">The object that generated the event.</span></span> <span data-ttu-id="ce30a-163">In de waarde van de **actie** parameter bevat de `$Sender` Automatische variabele het object Sender.</span><span class="sxs-lookup"><span data-stu-id="ce30a-163">In the value of the **Action** parameter, the `$Sender` automatic variable contains the sender object.</span></span>

- <span data-ttu-id="ce30a-164">SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="ce30a-164">SourceEventArgs.</span></span> <span data-ttu-id="ce30a-165">De eerste para meter die is afgeleid van EventArgs, als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="ce30a-165">The first parameter that derives from EventArgs, if it exists.</span></span> <span data-ttu-id="ce30a-166">In een verstreken timer gebeurtenis waarbij de hand tekening de afzender van het formulier object, **timers. ElapsedEventArgs** e heeft, bevat de eigenschap **SourceEventArgs** de **timers. ElapsedEventArgs**.</span><span class="sxs-lookup"><span data-stu-id="ce30a-166">For example, in a timer elapsed event in which the signature has the form Object sender, **Timers.ElapsedEventArgs** e, the **SourceEventArgs** property would contain the **Timers.ElapsedEventArgs**.</span></span> <span data-ttu-id="ce30a-167">In de waarde van de **actie** parameter bevat de `$EventArgs` Automatische variabele deze waarde.</span><span class="sxs-lookup"><span data-stu-id="ce30a-167">In the value of the **Action** parameter, the `$EventArgs` automatic variable contains this value.</span></span>

- <span data-ttu-id="ce30a-168">SourceArgs.</span><span class="sxs-lookup"><span data-stu-id="ce30a-168">SourceArgs.</span></span> <span data-ttu-id="ce30a-169">Alle para meters van de oorspronkelijke gebeurtenis handtekening.</span><span class="sxs-lookup"><span data-stu-id="ce30a-169">All parameters of the original event signature.</span></span> <span data-ttu-id="ce30a-170">Voor een standaard gebeurtenis handtekening `$Args[0]` vertegenwoordigt de afzender en `$Args[1]` vertegenwoordigt het **SourceEventArgs**.</span><span class="sxs-lookup"><span data-stu-id="ce30a-170">For a standard event signature, `$Args[0]` represents the sender, and `$Args[1]` represents the **SourceEventArgs**.</span></span> <span data-ttu-id="ce30a-171">In de waarde van de **actie** parameter bevat de `$Args` Automatische variabele deze waarde.</span><span class="sxs-lookup"><span data-stu-id="ce30a-171">In the value of the **Action** parameter, the `$Args` automatic variable contains this value.</span></span>

- <span data-ttu-id="ce30a-172">SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ce30a-172">SourceIdentifier.</span></span> <span data-ttu-id="ce30a-173">Een teken reeks waarmee het gebeurtenis abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="ce30a-173">A string that identifies the event subscription.</span></span> <span data-ttu-id="ce30a-174">In de waarde van de **actie** parameter bevat de eigenschap **SourceIdentifier** van de `$Event` Automatische variabele deze waarde.</span><span class="sxs-lookup"><span data-stu-id="ce30a-174">In the value of the **Action** parameter, the **SourceIdentifier** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="ce30a-175">TimeGenerated.</span><span class="sxs-lookup"><span data-stu-id="ce30a-175">TimeGenerated.</span></span> <span data-ttu-id="ce30a-176">Een **DateTime** -object dat het tijdstip vertegenwoordigt waarop de gebeurtenis is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ce30a-176">A **DateTime** object that represents the time at which the event was generated.</span></span>
  <span data-ttu-id="ce30a-177">In de waarde van de **actie** parameter bevat de eigenschap **TimeGenerated** van de `$Event` Automatische variabele deze waarde.</span><span class="sxs-lookup"><span data-stu-id="ce30a-177">In the value of the **Action** parameter, the **TimeGenerated** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="ce30a-178">MessageData.</span><span class="sxs-lookup"><span data-stu-id="ce30a-178">MessageData.</span></span> <span data-ttu-id="ce30a-179">Gegevens die zijn gekoppeld aan het gebeurtenis abonnement.</span><span class="sxs-lookup"><span data-stu-id="ce30a-179">Data associated with the event subscription.</span></span> <span data-ttu-id="ce30a-180">Gebruikers geven deze gegevens op wanneer ze een gebeurtenis registreren.</span><span class="sxs-lookup"><span data-stu-id="ce30a-180">Users specify this data when they register an event.</span></span> <span data-ttu-id="ce30a-181">In de waarde van de **actie** parameter bevat de eigenschap **MessageData** van de `$Event` Automatische variabele deze waarde.</span><span class="sxs-lookup"><span data-stu-id="ce30a-181">In the value of the **Action** parameter, the **MessageData** property of the `$Event` automatic variable contains this value.</span></span>

## <span data-ttu-id="ce30a-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ce30a-182">RELATED LINKS</span></span>

[<span data-ttu-id="ce30a-183">Nieuw-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="ce30a-183">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="ce30a-184">REGI ster-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="ce30a-184">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="ce30a-185">REGI ster-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="ce30a-185">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="ce30a-186">Remove-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="ce30a-186">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="ce30a-187">Registratie ongedaan maken-gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="ce30a-187">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="ce30a-188">Wachten gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="ce30a-188">Wait-Event</span></span>](Wait-Event.md)
