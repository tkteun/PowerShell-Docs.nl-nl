---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93247175"
---
# <span data-ttu-id="66a7b-103">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="66a7b-103">Get-Transaction</span></span>

## <span data-ttu-id="66a7b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="66a7b-104">SYNOPSIS</span></span>
<span data-ttu-id="66a7b-105">Hiermee wordt de huidige (actieve) trans actie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="66a7b-105">Gets the current (active) transaction.</span></span>

## <span data-ttu-id="66a7b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="66a7b-106">SYNTAX</span></span>

```
Get-Transaction [<CommonParameters>]
```

## <span data-ttu-id="66a7b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="66a7b-107">DESCRIPTION</span></span>
<span data-ttu-id="66a7b-108">De cmdlet **Get-trans actie** haalt een object op dat de huidige trans actie in de sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="66a7b-108">The **Get-Transaction** cmdlet gets an object that represents the current transaction in the session.</span></span>

<span data-ttu-id="66a7b-109">Deze cmdlet retourneert nooit meer dan één object, omdat er slechts één trans actie tegelijk actief is.</span><span class="sxs-lookup"><span data-stu-id="66a7b-109">This cmdlet never returns more than one object, because only one transaction is active at a time.</span></span>
<span data-ttu-id="66a7b-110">Als u een of meer onafhankelijke trans acties start (met behulp van de onafhankelijke para meter van de start-trans actie), is de laatst gestarte trans actie actief en is de trans actie die wordt **opgehaald-trans actie** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="66a7b-110">If you start one or more independent transactions (by using the Independent parameter of Start-Transaction), the most recently started transaction is active, and that is the transaction that **Get-Transaction** returns.</span></span>

<span data-ttu-id="66a7b-111">Wanneer alle actieve trans acties zijn teruggedraaid of doorgevoerd, wordt in deze cmdlet de trans actie weer gegeven die het meest recent actief was in de sessie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-111">When all active transactions have either been rolled back or committed, this cmdlet shows the transaction that was most recently active in the session.</span></span>

<span data-ttu-id="66a7b-112">Deze cmdlet is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="66a7b-112">This cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="66a7b-113">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="66a7b-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="66a7b-114">EXAMPLES</span></span>

### <span data-ttu-id="66a7b-115">Voor beeld 1: de huidige trans actie ophalen</span><span class="sxs-lookup"><span data-stu-id="66a7b-115">Example 1: Get the current transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="66a7b-116">Met deze opdracht wordt de cmdlet Get-Transaction gebruikt om de huidige trans actie op te halen.</span><span class="sxs-lookup"><span data-stu-id="66a7b-116">This command uses the Get-Transaction cmdlet to get the current transaction.</span></span>

### <span data-ttu-id="66a7b-117">Voor beeld 2: de eigenschappen en methoden van het transactie object weer geven</span><span class="sxs-lookup"><span data-stu-id="66a7b-117">Example 2: Show the properties and methods of the transaction object</span></span>

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

<span data-ttu-id="66a7b-118">Met deze opdracht wordt de Get-Member-cmdlet gebruikt om de eigenschappen en methoden van het transactie object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="66a7b-118">This command uses the Get-Member cmdlet to show the properties and methods of the transaction object.</span></span>

### <span data-ttu-id="66a7b-119">Voor beeld 3: de eigenschaps waarden van een teruggedraaide trans actie weer geven</span><span class="sxs-lookup"><span data-stu-id="66a7b-119">Example 3: Show the property values of a rolled back transaction</span></span>

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

<span data-ttu-id="66a7b-120">Met deze opdracht worden de eigenschaps waarden weer gegeven van een transactie object voor een trans actie die is teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="66a7b-120">This command shows the property values of a transaction object for a transaction that has been rolled back.</span></span>

### <span data-ttu-id="66a7b-121">Voor beeld 4: de eigenschaps waarden van een vastgelegde trans actie weer geven</span><span class="sxs-lookup"><span data-stu-id="66a7b-121">Example 4: Show the property values of a committed transaction</span></span>

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

<span data-ttu-id="66a7b-122">Met deze opdracht worden de eigenschaps waarden van een transactie object weer gegeven voor een trans actie die is doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="66a7b-122">This command shows the property values of a transaction object for a transaction that has been committed.</span></span>

### <span data-ttu-id="66a7b-123">Voor beeld 5: een trans actie starten terwijl een andere wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="66a7b-123">Example 5: Start a transaction while another is in progress</span></span>

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

<span data-ttu-id="66a7b-124">In dit voor beeld ziet u het effect van het transactie object van het starten van een trans actie terwijl er een andere trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="66a7b-124">This example shows the effect on the transaction object of starting a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="66a7b-125">Dit gebeurt meestal wanneer een script dat een trans actie uitvoert een functie bevat of een script aanroept dat een andere volledige trans actie bevat.</span><span class="sxs-lookup"><span data-stu-id="66a7b-125">Typically, this happens when a script that runs a transaction includes a function or calls a script that contains another complete transaction.</span></span>

<span data-ttu-id="66a7b-126">Tenzij de tweede **Start-trans actie** opdracht de *onafhankelijke* para meter bevat, wordt door **Start-trans actie** geen nieuwe trans actie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="66a7b-126">Unless the second **Start-Transaction** command includes the *Independent* parameter, **Start-Transaction** does not create a new transaction.</span></span>
<span data-ttu-id="66a7b-127">In plaats daarvan wordt een tweede abonnee toegevoegd aan de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-127">Instead, it adds a second subscriber to the original transaction.</span></span>

<span data-ttu-id="66a7b-128">Met de eerste **Start-trans actie** opdracht wordt de trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="66a7b-128">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="66a7b-129">Een New-Item opdracht met de para meter *UseTransaction* maakt deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-129">A New-Item command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="66a7b-130">Een tweede **Start-trans actie-** opdracht voegt een abonnee aan de trans actie toe.</span><span class="sxs-lookup"><span data-stu-id="66a7b-130">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="66a7b-131">De volgende New-Item-opdracht maakt ook deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-131">The next New-Item command is also part of the transaction.</span></span>

<span data-ttu-id="66a7b-132">Met de eerste **Get-trans** actie opdracht wordt de trans actie met meerdere abonnees weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="66a7b-132">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="66a7b-133">U ziet dat het aantal abonnees 2 is.</span><span class="sxs-lookup"><span data-stu-id="66a7b-133">Notice that the subscriber count is 2.</span></span>

<span data-ttu-id="66a7b-134">Met de eerste Complete-Transaction opdracht wordt de trans actie niet door voeren, maar het aantal abonnees wordt beperkt tot 1.</span><span class="sxs-lookup"><span data-stu-id="66a7b-134">The first Complete-Transaction command does not commit the transaction, but it reduces the subscriber count to 1.</span></span>

<span data-ttu-id="66a7b-135">De tweede opdracht **volt ooien trans** actie voert de trans actie door.</span><span class="sxs-lookup"><span data-stu-id="66a7b-135">The second **Complete-Transaction** command commits the transaction.</span></span>

### <span data-ttu-id="66a7b-136">Voor beeld 6: een onafhankelijke trans actie starten terwijl een andere wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="66a7b-136">Example 6: Start an independent transaction while another is in progress</span></span>

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

<span data-ttu-id="66a7b-137">In dit voor beeld ziet u het effect van het transactie object van het starten van een onafhankelijke trans actie terwijl een andere trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="66a7b-137">This example shows the effect on the transaction object of starting an independent transaction while another transaction is in progress.</span></span>

<span data-ttu-id="66a7b-138">Met de eerste **Start-trans actie** opdracht wordt de trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="66a7b-138">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="66a7b-139">Een **nieuwe item** opdracht met de para meter *UseTransaction* maakt deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-139">A **New-Item** command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="66a7b-140">Een tweede **Start-trans actie-** opdracht voegt een abonnee aan de trans actie toe.</span><span class="sxs-lookup"><span data-stu-id="66a7b-140">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="66a7b-141">De volgende opdracht voor het **nieuwe item** maakt ook deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-141">The next **New-Item** command is also part of the transaction.</span></span>

<span data-ttu-id="66a7b-142">Met de eerste **Get-trans** actie opdracht wordt de trans actie met meerdere abonnees weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="66a7b-142">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="66a7b-143">Houd er rekening mee dat het aantal abonnees 2 is.</span><span class="sxs-lookup"><span data-stu-id="66a7b-143">Note that the subscriber count is 2.</span></span>

<span data-ttu-id="66a7b-144">De opdracht **volt ooien-trans actie** reduceert het aantal abonnees tot 1, maar voert de trans actie niet door.</span><span class="sxs-lookup"><span data-stu-id="66a7b-144">The **Complete-Transaction** command reduces the subscriber count to 1, but it does not commit the transaction.</span></span>

<span data-ttu-id="66a7b-145">De tweede opdracht **volt ooien trans** actie voert de trans actie door.</span><span class="sxs-lookup"><span data-stu-id="66a7b-145">The second **Complete-Transaction** command commits the transaction.</span></span>

## <span data-ttu-id="66a7b-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="66a7b-146">PARAMETERS</span></span>

### <span data-ttu-id="66a7b-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="66a7b-147">CommonParameters</span></span>
<span data-ttu-id="66a7b-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="66a7b-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="66a7b-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="66a7b-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="66a7b-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="66a7b-150">INPUTS</span></span>

### <span data-ttu-id="66a7b-151">Geen</span><span class="sxs-lookup"><span data-stu-id="66a7b-151">None</span></span>
<span data-ttu-id="66a7b-152">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="66a7b-152">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="66a7b-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="66a7b-153">OUTPUTS</span></span>

### <span data-ttu-id="66a7b-154">System. Management. Automation. PSTransaction</span><span class="sxs-lookup"><span data-stu-id="66a7b-154">System.Management.Automation.PSTransaction</span></span>
<span data-ttu-id="66a7b-155">Met deze cmdlet wordt een object geretourneerd dat de huidige trans actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="66a7b-155">This cmdlet returns an object that represents the current transaction.</span></span>

## <span data-ttu-id="66a7b-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="66a7b-156">NOTES</span></span>

## <span data-ttu-id="66a7b-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="66a7b-157">RELATED LINKS</span></span>

[<span data-ttu-id="66a7b-158">Volt ooien-trans actie</span><span class="sxs-lookup"><span data-stu-id="66a7b-158">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="66a7b-159">Start-trans actie</span><span class="sxs-lookup"><span data-stu-id="66a7b-159">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="66a7b-160">Ongedaan maken-trans actie</span><span class="sxs-lookup"><span data-stu-id="66a7b-160">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="66a7b-161">Gebruik-trans actie</span><span class="sxs-lookup"><span data-stu-id="66a7b-161">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="66a7b-162">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="66a7b-162">New-Item</span></span>](New-Item.md)
