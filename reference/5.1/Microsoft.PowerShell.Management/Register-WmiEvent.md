---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/31/2020
ms.locfileid: "93251695"
---
# <span data-ttu-id="c690f-103">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="c690f-103">Register-WmiEvent</span></span>

## <span data-ttu-id="c690f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c690f-104">SYNOPSIS</span></span>
<span data-ttu-id="c690f-105">Abonneer u op een Windows Management Instrumentation-gebeurtenis (WMI).</span><span class="sxs-lookup"><span data-stu-id="c690f-105">Subscribes to a Windows Management Instrumentation (WMI) event.</span></span>

## <span data-ttu-id="c690f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c690f-106">SYNTAX</span></span>

### <span data-ttu-id="c690f-107">klasse (standaard)</span><span class="sxs-lookup"><span data-stu-id="c690f-107">class (Default)</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c690f-108">query</span><span class="sxs-lookup"><span data-stu-id="c690f-108">query</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="c690f-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c690f-109">DESCRIPTION</span></span>

<span data-ttu-id="c690f-110">De cmdlet meldt zich `Register-WmiEvent` aan Windows Management Instrumentation-gebeurtenissen (WMI) op de lokale computer of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c690f-110">The `Register-WmiEvent` cmdlet subscribes to Windows Management Instrumentation (WMI) events on the local computer or on a remote computer.</span></span>

<span data-ttu-id="c690f-111">Wanneer de WMI-gebeurtenis is gegenereerd, wordt deze toegevoegd aan de gebeurtenis wachtrij in uw lokale sessie, zelfs als de gebeurtenis zich voordoet op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c690f-111">When the subscribed WMI event is raised, it is added to the event queue in your local session even if the event occurs on a remote computer.</span></span> <span data-ttu-id="c690f-112">Gebruik de cmdlet om gebeurtenissen in de gebeurtenis wachtrij op te halen `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="c690f-112">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="c690f-113">U kunt de para meters van gebruiken om u te `Register-WmiEvent` Abonneren op gebeurtenissen op externe computers en om de eigenschapwaarden op te geven van de gebeurtenissen die u kunnen helpen bij het identificeren van de gebeurtenis in de wachtrij.</span><span class="sxs-lookup"><span data-stu-id="c690f-113">You can use the parameters of `Register-WmiEvent` to subscribe to events on remote computers and to specify the property values of the events that can help you identify the event in the queue.</span></span> <span data-ttu-id="c690f-114">U kunt ook de **actie** parameter gebruiken om op te geven welke acties moeten worden uitgevoerd wanneer een gebeurtenis waarop een abonnement is gegeven, wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-114">You can also use the **Action** parameter to specify actions to take when a subscribed event is raised.</span></span>

<span data-ttu-id="c690f-115">Wanneer u zich abonneert op een gebeurtenis, wordt een gebeurtenis abonnee toegevoegd aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="c690f-115">When you subscribe to an event, an event subscriber is added to your session.</span></span> <span data-ttu-id="c690f-116">Als u de gebeurtenis abonnees in de sessie wilt ophalen, gebruikt u de `Get-EventSubscriber` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c690f-116">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="c690f-117">Als u het abonnement wilt annuleren, gebruikt u de `Unregister-Event` cmdlet waarmee de gebeurtenis abonnee uit de sessie wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c690f-117">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

<span data-ttu-id="c690f-118">Nieuwe Common Information Model (CIM)-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voert dezelfde taken uit als de WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c690f-118">New Common Information Model (CIM) cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="c690f-119">De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de CIM-standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van computers waarop het Windows-besturings systeem wordt uitgevoerd en die die andere besturings systemen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c690f-119">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those that run other operating systems.</span></span> <span data-ttu-id="c690f-120">In plaats van met kunt `Register-WmiEvent` u overwegen de cmdlet [REGI ster-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c690f-120">Instead of using `Register-WmiEvent`, consider using the [Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet.</span></span>

## <span data-ttu-id="c690f-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c690f-121">EXAMPLES</span></span>

### <span data-ttu-id="c690f-122">Voor beeld 1: abonneren op gebeurtenissen die door een klasse zijn gegenereerd</span><span class="sxs-lookup"><span data-stu-id="c690f-122">Example 1: Subscribe to events generated by a class</span></span>

<span data-ttu-id="c690f-123">Met deze opdracht wordt een abonnement genomen op de gebeurtenissen die worden gegenereerd door de **Win32_ProcessStartTrace** klasse.</span><span class="sxs-lookup"><span data-stu-id="c690f-123">This command subscribes to the events generated by the **Win32_ProcessStartTrace** class.</span></span> <span data-ttu-id="c690f-124">Deze klasse genereert een gebeurtenis wanneer een proces wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="c690f-124">This class raises an event whenever a process starts.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="c690f-125">Voor beeld 2: abonneren op het maken van gebeurtenissen voor een proces</span><span class="sxs-lookup"><span data-stu-id="c690f-125">Example 2: Subscribe to creation events for a process</span></span>

<span data-ttu-id="c690f-126">Met deze opdracht wordt een query gebruikt om u te abonneren op gebeurtenissen voor het maken van Win32_process instanties.</span><span class="sxs-lookup"><span data-stu-id="c690f-126">This command uses a query to subscribe to Win32_process instance creation events.</span></span>

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### <span data-ttu-id="c690f-127">Voor beeld 3: een actie gebruiken om te reageren op een gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="c690f-127">Example 3: Use an action to respond to an event</span></span>

<span data-ttu-id="c690f-128">In dit voor beeld ziet u hoe u een actie kunt gebruiken om te reageren op een gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="c690f-128">This example shows how to use an action to respond to an event.</span></span> <span data-ttu-id="c690f-129">In dit geval `Start-Process` worden alle opdrachten in de huidige sessie naar een XML-bestand geschreven wanneer een proces wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="c690f-129">In this case, when a process starts, any `Start-Process` commands in the current session are written to an XML file.</span></span>

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

<span data-ttu-id="c690f-130">Wanneer u de **actie** parameter gebruikt, `Register-WmiEvent` retourneert een achtergrond taak die de gebeurtenis actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c690f-130">When you use the **Action** parameter, `Register-WmiEvent` returns a background job that represents the event action.</span></span> <span data-ttu-id="c690f-131">U kunt de **taak** -cmdlets, zoals `Get-Job` en, gebruiken `Receive-Job` om de gebeurtenis taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="c690f-131">You can use the **Job** cmdlets, such as `Get-Job` and `Receive-Job`, to manage the event job.</span></span>

<span data-ttu-id="c690f-132">Zie About Jobs (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c690f-132">For more information, see about_Jobs.</span></span>

### <span data-ttu-id="c690f-133">Voor beeld 4: registreren voor gebeurtenissen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="c690f-133">Example 4: Register for events on a remote computer</span></span>

<span data-ttu-id="c690f-134">Dit voor beeld registreert voor gebeurtenissen op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="c690f-134">This example registers for events on the Server01 remote computer.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

<span data-ttu-id="c690f-135">WMI retourneert de gebeurtenissen naar de lokale computer en slaat deze op in de gebeurtenis wachtrij in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c690f-135">WMI returns the events to the local computer and stores them in the event queue in the current session.</span></span> <span data-ttu-id="c690f-136">Voer een lokale opdracht uit om de gebeurtenissen op te halen `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="c690f-136">To retrieve the events, run a local `Get-Event` command.</span></span>

## <span data-ttu-id="c690f-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c690f-137">PARAMETERS</span></span>

### <span data-ttu-id="c690f-138">-Actie</span><span class="sxs-lookup"><span data-stu-id="c690f-138">-Action</span></span>

<span data-ttu-id="c690f-139">Geeft opdrachten voor het verwerken van gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="c690f-139">Specifies commands that handle the events.</span></span> <span data-ttu-id="c690f-140">De opdrachten in de **actie** parameter worden uitgevoerd wanneer een gebeurtenis wordt gestart in plaats van de gebeurtenis naar de gebeurtenis wachtrij te verzenden.</span><span class="sxs-lookup"><span data-stu-id="c690f-140">The commands in the **Action** parameter run when an event is raised instead of sending the event to the event queue.</span></span> <span data-ttu-id="c690f-141">Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="c690f-141">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="c690f-142">De waarde van de **actie** kan de `$Event` `$EventSubscriber` variabelen,,, `$Sender` `$EventArgs` en `$Args` automatisch bevatten. deze bevatten informatie over de gebeurtenis in het blok **actie** script.</span><span class="sxs-lookup"><span data-stu-id="c690f-142">The value of **Action** can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables, which provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="c690f-143">Zie about_Automatic_Variables voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c690f-143">For more information, see about_Automatic_Variables.</span></span>

<span data-ttu-id="c690f-144">Wanneer u een actie opgeeft, `Register-WmiEvent` retourneert een gebeurtenis taak object dat die actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c690f-144">When you specify an action, `Register-WmiEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="c690f-145">U kunt de-cmdlets gebruiken die het zelfstandige **taak** onderdeel (de **taak** -cmdlets) bevatten om de gebeurtenis taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="c690f-145">You can use the cmdlets that contain the **Job** noun (the **Job** cmdlets) to manage the event job.</span></span>

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

### <span data-ttu-id="c690f-146">-Klasse</span><span class="sxs-lookup"><span data-stu-id="c690f-146">-Class</span></span>

<span data-ttu-id="c690f-147">Hiermee geeft u de gebeurtenis op waarop u bent geabonneerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-147">Specifies the event to which you are subscribing.</span></span> <span data-ttu-id="c690f-148">Geef de WMI-klasse op waarmee de gebeurtenissen worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-148">Enter the WMI class that generates the events.</span></span> <span data-ttu-id="c690f-149">Een **klasse** -of **query** parameter is vereist in elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="c690f-149">A **Class** or **Query** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c690f-150">-ComputerName</span></span>

<span data-ttu-id="c690f-151">Hiermee geeft u de naam op van de computer waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-151">Specifies the name of the computer on which the command runs.</span></span> <span data-ttu-id="c690f-152">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c690f-152">The default is the local computer.</span></span>

<span data-ttu-id="c690f-153">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van de computer.</span><span class="sxs-lookup"><span data-stu-id="c690f-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of the computer.</span></span> <span data-ttu-id="c690f-154">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ) of localhost.</span><span class="sxs-lookup"><span data-stu-id="c690f-154">To specify the local computer, type the computer name, a dot (`.`), or localhost.</span></span>

<span data-ttu-id="c690f-155">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c690f-155">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="c690f-156">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c690f-156">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="c690f-157">-Credential</span></span>

<span data-ttu-id="c690f-158">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c690f-158">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="c690f-159">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c690f-159">The default is the current user.</span></span>

<span data-ttu-id="c690f-160">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c690f-160">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c690f-161">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="c690f-161">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-162">-Voorwaarts</span><span class="sxs-lookup"><span data-stu-id="c690f-162">-Forward</span></span>

<span data-ttu-id="c690f-163">Geeft aan dat deze cmdlet gebeurtenissen voor dit abonnement naar de sessie op de lokale computer verzendt.</span><span class="sxs-lookup"><span data-stu-id="c690f-163">Indicates that this cmdlet sends events for this subscription to the session on the local computer.</span></span>
<span data-ttu-id="c690f-164">Gebruik deze para meter als u zich registreert voor gebeurtenissen op een externe computer of in een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="c690f-164">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="c690f-165">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="c690f-165">-MaxTriggerCount</span></span>

<span data-ttu-id="c690f-166">Hiermee geeft u het maximum aantal triggers op.</span><span class="sxs-lookup"><span data-stu-id="c690f-166">Specifies the maximum trigger count.</span></span>

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

### <span data-ttu-id="c690f-167">-MessageData</span><span class="sxs-lookup"><span data-stu-id="c690f-167">-MessageData</span></span>

<span data-ttu-id="c690f-168">Hiermee geeft u aanvullende gegevens op die moeten worden gekoppeld aan dit gebeurtenis abonnement.</span><span class="sxs-lookup"><span data-stu-id="c690f-168">Specifies any additional data to be associated with this event subscription.</span></span> <span data-ttu-id="c690f-169">De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van alle gebeurtenissen die aan dit abonnement zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="c690f-169">The value of this parameter appears in the **MessageData** property of all events associated with this subscription.</span></span>

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

### <span data-ttu-id="c690f-170">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="c690f-170">-Namespace</span></span>

<span data-ttu-id="c690f-171">Hiermee geeft u de naam ruimte van de WMI-klasse op.</span><span class="sxs-lookup"><span data-stu-id="c690f-171">Specifies the namespace of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-172">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c690f-172">-Query</span></span>

<span data-ttu-id="c690f-173">Hiermee geeft u een query in WMI Query Language (WQL) op waarmee de WMI-gebeurtenis klasse wordt geïdentificeerd, zoals: `select * from __InstanceDeletionEvent` .</span><span class="sxs-lookup"><span data-stu-id="c690f-173">Specifies a query in WMI Query Language (WQL) that identifies the WMI event class, such as: `select * from __InstanceDeletionEvent`.</span></span>

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-174">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="c690f-174">-SourceIdentifier</span></span>

<span data-ttu-id="c690f-175">Hiermee geeft u een naam op die u voor het abonnement selecteert.</span><span class="sxs-lookup"><span data-stu-id="c690f-175">Specifies a name that you select for the subscription.</span></span> <span data-ttu-id="c690f-176">De naam die u selecteert, moet uniek zijn in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c690f-176">The name that you select must be unique in the current session.</span></span> <span data-ttu-id="c690f-177">De standaard waarde is de GUID die Windows Power shell toewijst.</span><span class="sxs-lookup"><span data-stu-id="c690f-177">The default value is the GUID that Windows PowerShell assigns.</span></span>

<span data-ttu-id="c690f-178">De waarde van deze para meter wordt weer gegeven in de waarde van de eigenschap **SourceIdentifier** van het object Subscriber en alle gebeurtenis objecten die zijn gekoppeld aan dit abonnement.</span><span class="sxs-lookup"><span data-stu-id="c690f-178">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and of all event objects associated with this subscription.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-179">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="c690f-179">-SupportEvent</span></span>

<span data-ttu-id="c690f-180">Geeft aan dat met deze cmdlet het gebeurtenis abonnement wordt verborgen.</span><span class="sxs-lookup"><span data-stu-id="c690f-180">Indicates that this cmdlet hides the event subscription.</span></span> <span data-ttu-id="c690f-181">Gebruik deze para meter wanneer het huidige abonnement deel uitmaakt van een complexere gebeurtenis registratie mechanisme en niet onafhankelijk moet worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-181">Use this parameter when the current subscription is part of a more complex event registration mechanism and it should not be discovered independently.</span></span>

<span data-ttu-id="c690f-182">Als u een abonnement wilt bekijken of annuleren dat is gemaakt met behulp van de para meter **SupportEvent** , geeft u de para meter **Force** van de `Get-EventSubscriber` `Unregister-Event` cmdlets op.</span><span class="sxs-lookup"><span data-stu-id="c690f-182">To view or cancel a subscription that was created by using the **SupportEvent** parameter, specify the **Force** parameter of the `Get-EventSubscriber` and `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="c690f-183">-Time-out</span><span class="sxs-lookup"><span data-stu-id="c690f-183">-Timeout</span></span>

<span data-ttu-id="c690f-184">Hiermee geeft u op hoelang Windows Power shell wacht tot deze opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="c690f-184">Specifies how long Windows PowerShell waits for this command to finish.</span></span>

<span data-ttu-id="c690f-185">De standaard waarde, 0 (nul), houdt in dat er geen time-out is en zorgt ervoor dat Windows Power shell voor onbepaalde tijd wacht.</span><span class="sxs-lookup"><span data-stu-id="c690f-185">The default value, 0 (zero), means that there is no time-out, and it causes Windows PowerShell to wait indefinitely.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c690f-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c690f-186">CommonParameters</span></span>

<span data-ttu-id="c690f-187">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c690f-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c690f-188">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c690f-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c690f-189">INVOER</span><span class="sxs-lookup"><span data-stu-id="c690f-189">INPUTS</span></span>

### <span data-ttu-id="c690f-190">Geen</span><span class="sxs-lookup"><span data-stu-id="c690f-190">None</span></span>

<span data-ttu-id="c690f-191">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="c690f-191">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="c690f-192">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c690f-192">OUTPUTS</span></span>

### <span data-ttu-id="c690f-193">Geen</span><span class="sxs-lookup"><span data-stu-id="c690f-193">None</span></span>

<span data-ttu-id="c690f-194">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-194">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c690f-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c690f-195">NOTES</span></span>

<span data-ttu-id="c690f-196">Als u deze cmdlet wilt gebruiken in Windows Vista of een nieuwere versie van het Windows-besturings systeem, start u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c690f-196">To use this cmdlet in Windows Vista or a later version of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="c690f-197">Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c690f-197">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="c690f-198">Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="c690f-198">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="c690f-199">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c690f-199">RELATED LINKS</span></span>
