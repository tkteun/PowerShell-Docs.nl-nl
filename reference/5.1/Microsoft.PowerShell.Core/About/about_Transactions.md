---
description: Hierin wordt beschreven hoe u transactionele bewerkingen in Power shell beheert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252549"
---
# <a name="about-transactions"></a><span data-ttu-id="8c9b2-104">Over trans acties</span><span class="sxs-lookup"><span data-stu-id="8c9b2-104">About Transactions</span></span>

## <a name="short-description"></a><span data-ttu-id="8c9b2-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8c9b2-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="8c9b2-106">Hierin wordt beschreven hoe u transactionele bewerkingen in Power shell beheert.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-106">Describes how to manage transacted operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="8c9b2-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8c9b2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8c9b2-108">Trans acties worden ondersteund in Power shell vanaf Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-108">Transactions are supported in PowerShell beginning in PowerShell 2.0.</span></span> <span data-ttu-id="8c9b2-109">Met deze functie kunt u een trans actie starten, aangeven welke opdrachten deel uitmaken van de trans actie en een trans actie door voeren of terugdraaien.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-109">This feature enables you to start a transaction, to indicate which commands are part of the transaction, and to commit or roll back a transaction.</span></span>

## <a name="about-transactions"></a><span data-ttu-id="8c9b2-110">OVER TRANS ACTIES</span><span class="sxs-lookup"><span data-stu-id="8c9b2-110">ABOUT TRANSACTIONS</span></span>

<span data-ttu-id="8c9b2-111">In Power shell is een trans actie een set van een of meer opdrachten die als een logische eenheid worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-111">In PowerShell, a transaction is a set of one or more commands that are managed as a logical unit.</span></span> <span data-ttu-id="8c9b2-112">Een trans actie kan worden voltooid (' doorgevoerd '), waardoor gegevens worden gewijzigd die worden beïnvloed door de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-112">A transaction can be completed ("committed"), which changes data affected by the transaction.</span></span> <span data-ttu-id="8c9b2-113">Het is ook mogelijk dat een trans actie volledig ongedaan kan worden gemaakt (teruggedraaid), zodat de betrokken gegevens niet door de trans actie worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-113">Or, a transaction can be completely undone ("rolled back") so that the affected data is not changed by the transaction.</span></span>

<span data-ttu-id="8c9b2-114">Omdat de opdrachten in een trans actie als eenheid worden beheerd, worden alle opdrachten vastgelegd of worden alle opdrachten teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-114">Because the commands in a transaction are managed as a unit, either all commands are committed, or all commands are rolled back.</span></span>

<span data-ttu-id="8c9b2-115">Trans acties worden veel gebruikt bij het verwerken van gegevens, met name in database bewerkingen en voor financiële trans acties.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-115">Transactions are widely used in data processing, most notably in database operations and for financial transactions.</span></span> <span data-ttu-id="8c9b2-116">Trans acties worden meestal gebruikt wanneer het slechtste scenario voor een set opdrachten niet zo is dat ze allemaal mislukken, maar dat sommige opdrachten slagen terwijl anderen mislukken, waardoor het systeem in een beschadigde, onwaar of niet-onderhandel bare status staat die moeilijk te herstellen is.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-116">Transactions are most often used when the worst-case scenario for a set of commands is not that they all fail, but that some commands succeed while others fail, leaving the system in a damaged, false, or uninterpretable state that is difficult to repair.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="8c9b2-117">TRANS ACTIE-CMDLETS</span><span class="sxs-lookup"><span data-stu-id="8c9b2-117">TRANSACTION CMDLETS</span></span>

<span data-ttu-id="8c9b2-118">Power shell bevat verschillende cmdlets die zijn ontworpen voor het beheren van trans acties.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-118">PowerShell includes several cmdlets designed for managing transactions.</span></span>

- <span data-ttu-id="8c9b2-119">Start-trans actie: start een nieuwe trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-119">Start-Transaction: Starts a new transaction.</span></span>
- <span data-ttu-id="8c9b2-120">Use-Trans Action: voegt een opdracht of expressie toe aan de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-120">Use-Transaction: Adds a command or expression to the transaction.</span></span> <span data-ttu-id="8c9b2-121">De opdracht moet objecten gebruiken waarvoor trans acties zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-121">The command must use transaction-enabled objects.</span></span>
- <span data-ttu-id="8c9b2-122">Ongedaan maken-trans actie: Hiermee wordt de trans actie teruggedraaid zodat er geen gegevens door de trans actie worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-122">Undo-Transaction: Rolls back the transaction so that no data is changed by the transaction.</span></span>
- <span data-ttu-id="8c9b2-123">Volt ooien: de trans actie wordt door doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-123">Complete-Transaction: Commits the transaction.</span></span> <span data-ttu-id="8c9b2-124">De gegevens die worden beïnvloed door de trans actie, worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-124">The data affected by the transaction is changed.</span></span>
- <span data-ttu-id="8c9b2-125">Get-trans actie: haalt informatie op over de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-125">Get-Transaction: Gets information about the active transaction.</span></span>

<span data-ttu-id="8c9b2-126">Voor een lijst met trans actie-cmdlets typt u:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-126">For a list of transaction cmdlets, type:</span></span>

```powershell
get-command *transaction
```

<span data-ttu-id="8c9b2-127">Voor gedetailleerde informatie over de cmdlets typt u:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-127">For detailed information about the cmdlets, type:</span></span>

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a><span data-ttu-id="8c9b2-128">ELEMENTEN WAARVOOR TRANS ACTIES ZIJN INGESCHAKELD</span><span class="sxs-lookup"><span data-stu-id="8c9b2-128">TRANSACTION-ENABLED ELEMENTS</span></span>

<span data-ttu-id="8c9b2-129">Om deel te nemen aan een trans actie, moeten de cmdlet en de provider trans acties ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-129">To participate in a transaction, both the cmdlet and the provider must support transactions.</span></span> <span data-ttu-id="8c9b2-130">Deze functie is ingebouwd in de objecten die worden beïnvloed door de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-130">This feature is built in to the objects that are affected by the transaction.</span></span>

<span data-ttu-id="8c9b2-131">De Power shell-register provider ondersteunt trans acties in Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-131">The PowerShell Registry provider supports transactions in Windows Vista.</span></span> <span data-ttu-id="8c9b2-132">Het TransactedString-object (Microsoft. Power shell. commands. Management. TransactedString) werkt met elk besturings systeem dat Power shell uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-132">The TransactedString object (Microsoft.PowerShell.Commands.Management.TransactedString) works with any operating system that runs PowerShell.</span></span>

<span data-ttu-id="8c9b2-133">Andere Power shell-providers kunnen trans acties ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-133">Other PowerShell providers can support transactions.</span></span> <span data-ttu-id="8c9b2-134">Als u de Power shell-providers in uw sessie wilt vinden die trans acties ondersteunen, gebruikt u de volgende opdracht om de waarde voor ' trans acties ' te vinden in de eigenschap Capabilities van providers:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-134">To find the PowerShell providers in your session that support transactions, use the following command to find the "Transactions" value in the Capabilities property of providers:</span></span>

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

<span data-ttu-id="8c9b2-135">Zie de Help bij de provider voor meer informatie over een provider.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-135">For more information about a provider, see the Help for the provider.</span></span> <span data-ttu-id="8c9b2-136">Voor hulp bij de provider, typt u:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-136">To get provider Help, type:</span></span>

```
get-help <provider-name>
```

<span data-ttu-id="8c9b2-137">Als u bijvoorbeeld hulp wilt krijgen voor de register provider, typt u:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-137">For example, to get Help for the Registry provider, type:</span></span>

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a><span data-ttu-id="8c9b2-138">DE USETRANSACTION-PARA METER</span><span class="sxs-lookup"><span data-stu-id="8c9b2-138">THE USETRANSACTION PARAMETER</span></span>

<span data-ttu-id="8c9b2-139">Cmdlets die trans acties kunnen ondersteunen, hebben een UseTransaction-para meter.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-139">Cmdlets that can support transactions have a UseTransaction parameter.</span></span> <span data-ttu-id="8c9b2-140">Deze para meter bevat de opdracht in de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-140">This parameter includes the command in the active transaction.</span></span> <span data-ttu-id="8c9b2-141">U kunt de volledige parameter naam of de alias ervan gebruiken, ' usetx '.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-141">You can use the full parameter name or its alias, "usetx".</span></span>

<span data-ttu-id="8c9b2-142">De para meter kan alleen worden gebruikt als de sessie een actieve trans actie bevat.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-142">The parameter can be used only when the session contains an active transaction.</span></span> <span data-ttu-id="8c9b2-143">Als u een opdracht met de para meter UseTransaction opgeeft wanneer er geen actieve trans actie is, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-143">If you enter a command with the UseTransaction parameter when there is no active transaction, the command fails.</span></span>

<span data-ttu-id="8c9b2-144">Als u cmdlets wilt zoeken met de para meter UseTransaction, typt u:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-144">To find cmdlets with the UseTransaction parameter, type:</span></span>

```powershell
get-help * -parameter UseTransaction
```

<span data-ttu-id="8c9b2-145">In Power shell core hebben alle cmdlets die zijn ontworpen om te werken met Power shell-providers ondersteunings transacties.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-145">In PowerShell core, all of the cmdlets designed to work with PowerShell providers support transactions.</span></span> <span data-ttu-id="8c9b2-146">Als gevolg hiervan kunt u de provider-cmdlets gebruiken voor het beheren van trans acties.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-146">As a result, you can use the provider cmdlets to manage transactions.</span></span>

<span data-ttu-id="8c9b2-147">Zie [about_Providers](about_Providers.md)voor meer informatie over Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-147">For more information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

## <a name="the-transaction-object"></a><span data-ttu-id="8c9b2-148">HET TRANSACTIE OBJECT</span><span class="sxs-lookup"><span data-stu-id="8c9b2-148">THE TRANSACTION OBJECT</span></span>

<span data-ttu-id="8c9b2-149">Trans acties worden weer gegeven in Power shell door een transactie object, System. Management. Automation. Trans Action.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-149">Transactions are represented in PowerShell by a transaction object, System.Management.Automation.Transaction.</span></span>

<span data-ttu-id="8c9b2-150">Het object heeft de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-150">The object has the following properties:</span></span>

- <span data-ttu-id="8c9b2-151">RollbackPreference: bevat de voor keuren voor terugdraai bewerking die zijn ingesteld voor de huidige trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-151">RollbackPreference: Contains the rollback preference set for the current transaction.</span></span> <span data-ttu-id="8c9b2-152">U kunt de terugdraai voorkeur instellen wanneer u Start-Transaction gebruikt om de trans actie te starten.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-152">You can set the rollback preference when you use Start-Transaction to start the transaction.</span></span>

  <span data-ttu-id="8c9b2-153">De terugdraai voorkeur bepaalt de voor waarden waaronder de trans actie automatisch wordt teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-153">The rollback preference determines the conditions under which the transaction is rolled back automatically.</span></span> <span data-ttu-id="8c9b2-154">Geldige waarden zijn error, TerminatingError en Never.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-154">Valid values are Error, TerminatingError, and Never.</span></span> <span data-ttu-id="8c9b2-155">De standaard waarde is fout.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-155">The default value is Error.</span></span>

- <span data-ttu-id="8c9b2-156">Status: bevat de huidige status van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-156">Status: Contains the current status of the transaction.</span></span> <span data-ttu-id="8c9b2-157">Geldige waarden zijn actief, doorgevoerd en teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-157">Valid values are Active, Committed, and RolledBack.</span></span>

- <span data-ttu-id="8c9b2-158">SubscriberCount: bevat het aantal abonnees van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-158">SubscriberCount: Contains the number of subscribers to the transaction.</span></span> <span data-ttu-id="8c9b2-159">Een abonnee wordt toegevoegd aan een trans actie wanneer u een trans actie start terwijl er een andere trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-159">A subscriber is added to a transaction when you start a transaction while another transaction is in progress.</span></span> <span data-ttu-id="8c9b2-160">Het aantal abonnees wordt verlaagd wanneer een abonnee de trans actie doorvoert.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-160">The subscriber count is decremented when a subscriber commits the transaction.</span></span>

## <a name="active-transactions"></a><span data-ttu-id="8c9b2-161">ACTIEVE TRANS ACTIES</span><span class="sxs-lookup"><span data-stu-id="8c9b2-161">ACTIVE TRANSACTIONS</span></span>

<span data-ttu-id="8c9b2-162">In Power shell is slechts één trans actie tegelijk actief, en u kunt alleen de actieve trans actie beheren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-162">In PowerShell, only one transaction is active at a time, and you can manage only the active transaction.</span></span> <span data-ttu-id="8c9b2-163">In dezelfde sessie kunnen meerdere trans acties tegelijk worden uitgevoerd, maar alleen de meest recent gestarte trans actie is actief.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-163">Multiple transactions can be in progress in the same session at the same time, but only the most-recently started transaction is active.</span></span>

<span data-ttu-id="8c9b2-164">Als gevolg hiervan kunt u een bepaalde trans actie niet opgeven wanneer u de Trans Action-cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-164">As a result, you cannot specify a particular transaction when using the transaction cmdlets.</span></span> <span data-ttu-id="8c9b2-165">Opdrachten zijn altijd van toepassing op de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-165">Commands always apply to the active transaction.</span></span>

<span data-ttu-id="8c9b2-166">Dit wordt het meest duidelijk in het gedrag van de cmdlet Get-Transaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-166">This is most evident in the behavior of the Get-Transaction cmdlet.</span></span> <span data-ttu-id="8c9b2-167">Wanneer u een Get-Transaction opdracht invoert, wordt door Get-Transaction altijd slechts één transactie object opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-167">When you enter a Get-Transaction command, Get-Transaction always gets only one transaction object.</span></span> <span data-ttu-id="8c9b2-168">Dit object is het object dat de actieve trans actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-168">This object is the object that represents the active transaction.</span></span>

<span data-ttu-id="8c9b2-169">Als u een andere trans actie wilt beheren, moet u eerst de actieve trans actie volt ooien, hetzij door deze door te voeren of terug te draaien.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-169">To manage a different transaction, you must first finish the active transaction, either by committing it or rolling it back.</span></span> <span data-ttu-id="8c9b2-170">Wanneer u dit doet, wordt de vorige trans actie automatisch actief.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-170">When you do this, the previous transaction becomes active automatically.</span></span> <span data-ttu-id="8c9b2-171">Trans acties worden actief bij het terugdraaien van de volg orde waarin ze worden gestart, zodat de meest recent gestarte trans actie altijd actief is.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-171">Transactions become active in the reverse of order of which they are started, so that the most recently started transaction is always active.</span></span>

## <a name="subscribers-and-independent-transactions"></a><span data-ttu-id="8c9b2-172">ABONNEES EN ONAFHANKELIJKE TRANS ACTIES</span><span class="sxs-lookup"><span data-stu-id="8c9b2-172">SUBSCRIBERS AND INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="8c9b2-173">Als u een trans actie start terwijl een andere trans actie wordt uitgevoerd, start Power shell niet standaard een nieuwe trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-173">If you start a transaction while another transaction is in progress, by default, PowerShell does not start a new transaction.</span></span> <span data-ttu-id="8c9b2-174">In plaats daarvan wordt een abonnee toegevoegd aan de huidige trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-174">Instead, it adds a "subscriber" to the current transaction.</span></span>

<span data-ttu-id="8c9b2-175">Wanneer een trans actie meerdere abonnees heeft, wordt een enkele Undo-Transaction-opdracht op een wille keurig punt de volledige trans actie teruggedraaid voor alle abonnees.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-175">When a transaction has multiple subscribers, a single Undo-Transaction command at any point rolls back the entire transaction for all subscribers.</span></span> <span data-ttu-id="8c9b2-176">Als u de trans actie wilt door voeren, moet u voor elke abonnee een Complete-Transaction-opdracht invoeren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-176">However, to commit the transaction, you must enter a Complete-Transaction command for every subscriber.</span></span>

<span data-ttu-id="8c9b2-177">Als u het aantal abonnees voor een trans actie wilt vinden, controleert u de eigenschap SubscriberCount van het transactie object.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-177">To find the number of subscribers to a transaction, check the SubscriberCount property of the transaction object.</span></span> <span data-ttu-id="8c9b2-178">De volgende opdracht gebruikt bijvoorbeeld de cmdlet Get-Transaction om de waarde van de eigenschap SubscriberCount van de actieve trans actie op te halen:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-178">For example, the following command uses the Get-Transaction cmdlet to get the value of the SubscriberCount property of the active transaction:</span></span>

```powershell
(Get-Transaction).SubscriberCount
```

<span data-ttu-id="8c9b2-179">Het toevoegen van een abonnee is het standaard gedrag omdat de meeste trans acties die worden gestart terwijl een andere trans actie wordt uitgevoerd, betrekking hebben op de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-179">Adding a subscriber is the default behavior because most transactions that are started while another transaction is in progress are related to the original transaction.</span></span> <span data-ttu-id="8c9b2-180">In het typische model roept een script dat een trans actie bevat een hulp script aan dat een eigen trans actie bevat.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-180">In the typical model, a script that contains a transaction calls a helper script that contains its own transaction.</span></span> <span data-ttu-id="8c9b2-181">Omdat de trans acties gerelateerd zijn, moeten ze worden teruggedraaid of als een eenheid worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-181">Because the transactions are related, they should be rolled back or committed as a unit.</span></span>

<span data-ttu-id="8c9b2-182">U kunt echter een trans actie starten die onafhankelijk is van de huidige trans actie door gebruik te maken van de onafhankelijke para meter van de cmdlet Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-182">However, you can start a transaction that is independent of the current transaction by using the Independent parameter of the Start-Transaction cmdlet.</span></span>

<span data-ttu-id="8c9b2-183">Wanneer u een onafhankelijke trans actie start, wordt er Start-Transaction een nieuw transactie object gemaakt en de nieuwe trans actie wordt de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-183">When you start an independent transaction, Start-Transaction creates a new transaction object, and the new transaction becomes the active transaction.</span></span>
<span data-ttu-id="8c9b2-184">De onafhankelijke trans actie kan worden doorgevoerd of teruggedraaid zonder dat dit van invloed is op de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-184">The independent transaction can be committed or rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="8c9b2-185">Wanneer de onafhankelijke trans actie is voltooid (doorgevoerd of teruggedraaid), wordt de oorspronkelijke trans actie opnieuw de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-185">When the independent transaction is finished (committed or rolled back), the original transaction becomes the active transaction again.</span></span>

## <a name="changing-data"></a><span data-ttu-id="8c9b2-186">GEGEVENS WIJZIGEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-186">CHANGING DATA</span></span>

<span data-ttu-id="8c9b2-187">Wanneer u trans acties gebruikt om gegevens te wijzigen, worden de gegevens die worden beïnvloed door de trans actie, pas gewijzigd nadat u de trans actie hebt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-187">When you use transactions to change data, the data that is affected by the transaction is not changed until you commit the transaction.</span></span> <span data-ttu-id="8c9b2-188">Dezelfde gegevens kunnen echter worden gewijzigd door opdrachten die geen deel uitmaken van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-188">However, the same data can be changed by commands that are not part of the transaction.</span></span>

<span data-ttu-id="8c9b2-189">Houd dit in acht wanneer u trans acties gebruikt om gedeelde gegevens te beheren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-189">Keep this in mind when you are using transactions to manage shared data.</span></span>
<span data-ttu-id="8c9b2-190">Data bases hebben doorgaans mechanismen waarmee de gegevens worden vergrendeld terwijl u aan het werk bent, zodat andere gebruikers en andere opdrachten, scripts en functies deze niet kunnen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-190">Typically, databases have mechanisms that lock the data while you are working on it, preventing other users, and other commands, scripts, and functions, from changing it.</span></span>

<span data-ttu-id="8c9b2-191">De vergren deling is echter een functie van de-data base.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-191">However, the lock is a feature of the database.</span></span> <span data-ttu-id="8c9b2-192">Het is niet gerelateerd aan trans acties.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-192">It is not related to transactions.</span></span> <span data-ttu-id="8c9b2-193">Als u werkt met een bestands systeem dat is ingeschakeld voor trans acties of een ander gegevens archief, kunnen de gegevens worden gewijzigd terwijl de trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-193">If you are working in a transaction-enabled file system or other data store, the data can be changed while the transaction is in progress.</span></span>

## <a name="examples"></a><span data-ttu-id="8c9b2-194">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-194">EXAMPLES</span></span>

<span data-ttu-id="8c9b2-195">In de voor beelden in deze sectie wordt de Power shell-register provider gebruikt en wordt ervan uitgegaan dat u ermee vertrouwd bent.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-195">The examples in this section use the PowerShell Registry provider and assume that you are familiar with it.</span></span> <span data-ttu-id="8c9b2-196">Typ "Get-Help Registry" voor meer informatie over de register provider.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-196">For information about the Registry provider, type "get-help registry".</span></span>

### <a name="example-1-committing-a-transaction"></a><span data-ttu-id="8c9b2-197">VOOR BEELD 1: EEN TRANS ACTIE DOOR VOEREN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-197">EXAMPLE 1: COMMITTING A TRANSACTION</span></span>

<span data-ttu-id="8c9b2-198">Als u een trans actie wilt maken, gebruikt u de cmdlet Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-198">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="8c9b2-199">Met de volgende opdracht wordt een trans actie gestart met de standaard instellingen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-199">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-200">Als u opdrachten in de trans actie wilt toevoegen, gebruikt u de para meter UseTransaction van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-200">To include commands in the transaction, use the UseTransaction parameter of the cmdlet.</span></span> <span data-ttu-id="8c9b2-201">Standaard worden opdrachten niet in de trans actie opgenomen,</span><span class="sxs-lookup"><span data-stu-id="8c9b2-201">By default, commands are not included in the transaction,</span></span>

<span data-ttu-id="8c9b2-202">De volgende opdracht, waarmee de huidige locatie in de software sleutel van de HKCU: station, wordt ingesteld, is niet opgenomen in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-202">For example, the following command, which sets the current location in the Software key of the HKCU: drive, is not included in the transaction.</span></span>

```powershell
cd hkcu:\Software
```

<span data-ttu-id="8c9b2-203">Met de volgende opdracht, die de sleutel mijn bedrijf maakt, gebruikt de para meter UseTransaction van de cmdlet New-Item om de opdracht in de actieve trans actie op te neemt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-203">The following command, which creates the MyCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="8c9b2-204">De opdracht retourneert een object dat de nieuwe sleutel vertegenwoordigt, maar omdat de opdracht deel uitmaakt van de trans actie, is het REGI ster nog niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-204">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

<span data-ttu-id="8c9b2-205">Gebruik de cmdlet Complete-Transaction om de trans actie door te voeren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-205">To commit the transaction, use the Complete-Transaction cmdlet.</span></span> <span data-ttu-id="8c9b2-206">Omdat deze altijd van invloed is op de actieve trans actie, kunt u de trans actie niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-206">Because it always affects the active transaction, you cannot specify the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="8c9b2-207">Als gevolg hiervan wordt de sleutel mijn bedrijf toegevoegd aan het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-207">As a result, the MyCompany key is added to the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a><span data-ttu-id="8c9b2-208">VOOR BEELD 2: EEN TRANS ACTIE TERUGDRAAIEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-208">EXAMPLE 2: ROLLING BACK A TRANSACTION</span></span>

<span data-ttu-id="8c9b2-209">Als u een trans actie wilt maken, gebruikt u de cmdlet Start-Transaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-209">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="8c9b2-210">Met de volgende opdracht wordt een trans actie gestart met de standaard instellingen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-210">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-211">Met de volgende opdracht, die de sleutel MyOtherCompany maakt, gebruikt de para meter UseTransaction van de cmdlet New-Item om de opdracht in de actieve trans actie op te neemt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-211">The following command, which creates the MyOtherCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -UseTransaction
```

<span data-ttu-id="8c9b2-212">De opdracht retourneert een object dat de nieuwe sleutel vertegenwoordigt, maar omdat de opdracht deel uitmaakt van de trans actie, is het REGI ster nog niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-212">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

<span data-ttu-id="8c9b2-213">Gebruik de cmdlet Undo-Transaction om de trans actie terug te draaien.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-213">To roll back the transaction, use the Undo-Transaction cmdlet.</span></span> <span data-ttu-id="8c9b2-214">Omdat deze altijd van invloed is op de actieve trans actie, geeft u de trans actie niet op.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-214">Because it always affects the active transaction, you do not specify the transaction.</span></span>

```powershell
Undo-transaction
```

<span data-ttu-id="8c9b2-215">Het resultaat is dat de MyOtherCompany-sleutel niet aan het REGI ster is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-215">The result is that the MyOtherCompany key is not added to the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a><span data-ttu-id="8c9b2-216">VOOR BEELD 3: EEN VOOR BEELD VAN EEN TRANS ACTIE BEKIJKEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-216">EXAMPLE 3: PREVIEWING A TRANSACTION</span></span>

<span data-ttu-id="8c9b2-217">Normaal gesp roken worden de opdrachten die worden gebruikt in een wijzigings gegevens van trans acties.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-217">Typically, the commands used in a transaction change data.</span></span> <span data-ttu-id="8c9b2-218">De opdrachten voor het ophalen van gegevens zijn echter handig in een trans actie, omdat deze gegevens in de trans actie worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-218">However, the commands that get data are useful in a transaction, too, because they get data inside of the transaction.</span></span> <span data-ttu-id="8c9b2-219">Dit geeft een voor beeld van de wijzigingen die de trans actie door voeren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-219">This provides a preview of the changes that committing the transaction would cause.</span></span>

<span data-ttu-id="8c9b2-220">In het volgende voor beeld ziet u hoe u de Get-ChildItem-opdracht (de alias is ' dir ') gebruikt om de wijzigingen in een trans actie te bekijken.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-220">The following example shows how to use the Get-ChildItem command (the alias is "dir") to preview the changes in a transaction.</span></span>

<span data-ttu-id="8c9b2-221">Met de volgende opdracht wordt een trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-221">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-222">De volgende opdracht maakt gebruik van de cmdlet New-ItemProperty om de register vermelding MyKey toe te voegen aan de mijn bedrijf-sleutel.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-222">The following command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="8c9b2-223">De opdracht gebruikt de para meter UseTransaction voor het toevoegen van de opdracht in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-223">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

<span data-ttu-id="8c9b2-224">De opdracht retourneert een object dat de nieuwe register vermelding vertegenwoordigt, maar de register vermelding is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-224">The command returns an object representing the new registry entry, but the registry entry is not changed.</span></span>

```
MyKey
-----
123
```

<span data-ttu-id="8c9b2-225">Als u de items wilt ophalen die zich momenteel in het REGI ster bevinden, gebruikt u een Get-ChildItem opdracht (' dir ') zonder de para meter UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-225">To get the items that are currently in the registry, use a Get-ChildItem command ("dir") without the UseTransaction parameter.</span></span> <span data-ttu-id="8c9b2-226">Met de volgende opdracht worden items opgehaald die beginnen met ' M '.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-226">The following command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="8c9b2-227">Het resultaat geeft aan dat er nog geen items zijn toegevoegd aan de mijn bedrijf-sleutel.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-227">The result shows that no entries have yet been added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

<span data-ttu-id="8c9b2-228">Als u een voor beeld wilt zien van het effect van het door voeren van de trans actie, voert u de opdracht Get-ChildItem ("dir") in met de para meter UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-228">To preview the effect of committing the transaction, enter a Get-ChildItem ("dir") command with the UseTransaction parameter.</span></span> <span data-ttu-id="8c9b2-229">Met deze opdracht wordt een overzicht gegeven van de gegevens in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-229">This command has a view of the data from within the transaction.</span></span>

```powershell
dir m* -useTransaction
```

<span data-ttu-id="8c9b2-230">Het resultaat geeft aan dat, als de trans actie is doorgevoerd, de vermelding MyKey wordt toegevoegd aan de sleutel mijn bedrijf.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-230">The result shows that, if the transaction is committed, the MyKey entry will be added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a><span data-ttu-id="8c9b2-231">VOOR BEELD 4: TRANSACTIONELE EN NIET-TRANSACTIONELE OPDRACHTEN COMBI NEREN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-231">EXAMPLE 4: COMBINING TRANSACTED AND NON-TRANSACTED COMMANDS</span></span>

<span data-ttu-id="8c9b2-232">U kunt niet-transactionele opdrachten opgeven tijdens een trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-232">You can enter non-transacted commands during a transaction.</span></span> <span data-ttu-id="8c9b2-233">De niet-transactionele opdrachten beïnvloeden de gegevens onmiddellijk, maar ze hebben geen invloed op de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-233">The non-transacted commands affect the data immediately, but they do not affect the transaction.</span></span>
<span data-ttu-id="8c9b2-234">Met de volgende opdracht wordt een trans actie gestart in de register sleutel HKCU: \ software.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-234">The following command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-235">De volgende drie opdrachten gebruiken de New-Item cmdlet om sleutels aan het REGI ster toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-235">The next three commands use the New-Item cmdlet to add keys to the registry.</span></span>
<span data-ttu-id="8c9b2-236">De eerste en derde opdracht gebruiken de para meter UseTransaction om de opdrachten in de trans actie op te genomen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-236">The first and third commands use the UseTransaction parameter to include the commands in the transaction.</span></span> <span data-ttu-id="8c9b2-237">Met de tweede opdracht wordt de para meter wegge laten.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-237">The second command omits the parameter.</span></span> <span data-ttu-id="8c9b2-238">Omdat de tweede opdracht niet in de trans actie is opgenomen, is deze onmiddellijk van kracht.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-238">Because the second command is not included in the transaction, it is effective immediately.</span></span>

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

<span data-ttu-id="8c9b2-239">Als u de huidige status van het REGI ster wilt weer geven, gebruikt u de opdracht Get-ChildItem ("dir") zonder de para meter UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-239">To view the current state of the registry, use a Get-ChildItem ("dir") command without the UseTransaction parameter.</span></span> <span data-ttu-id="8c9b2-240">Met deze opdracht worden items opgehaald die beginnen met ' M '.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-240">This command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="8c9b2-241">Het resultaat toont aan dat de sleutel MyCompany2 is toegevoegd aan het REGI ster, maar de MyCompany1-en MyCompany3-sleutels, die deel uitmaken van de trans actie, worden niet toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-241">The result shows that the MyCompany2 key is added to the registry, but the MyCompany1 and MyCompany3 keys, which are part of the transaction, are not added.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

<span data-ttu-id="8c9b2-242">Met de volgende opdracht wordt de trans actie door doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-242">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="8c9b2-243">Nu worden de sleutels die als onderdeel van de trans actie zijn toegevoegd, weer gegeven in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-243">Now, the keys that were added as part of the transaction appear in the registry.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a><span data-ttu-id="8c9b2-244">VOOR BEELD 5: AUTOMATISCH TERUGDRAAIEN GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-244">EXAMPLE 5: USING AUTOMATIC ROLLBACK</span></span>

<span data-ttu-id="8c9b2-245">Wanneer een opdracht in een trans actie een fout genereert, wordt de trans actie automatisch teruggezet.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-245">When a command in a transaction generates an error of any kind, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="8c9b2-246">Dit standaard gedrag is bedoeld voor scripts die trans acties uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-246">This default behavior is designed for scripts that run transactions.</span></span> <span data-ttu-id="8c9b2-247">Scripts zijn doorgaans goed getest en bevatten logica voor fout afhandeling, waardoor fouten niet worden verwacht en de trans actie moet worden beëindigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-247">Scripts are typically well tested and include error-handling logic, so errors are not expected and should terminate the transaction.</span></span>

<span data-ttu-id="8c9b2-248">Met de eerste opdracht wordt een trans actie gestart in de register sleutel HKCU: \ software.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-248">The first command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-249">De volgende opdracht maakt gebruik van de cmdlet New-Item om de sleutel mijn bedrijf toe te voegen aan het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-249">The following command uses the New-Item cmdlet to add the MyCompany key to the registry.</span></span> <span data-ttu-id="8c9b2-250">De opdracht maakt gebruik van de para meter UseTransaction (de alias is ' usetx ') om de opdracht in de trans actie op te neemt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-250">The command uses the UseTransaction parameter (the alias is "usetx") to include the command in the transaction.</span></span>

```powershell
New-Item MyCompany -UseTX
```

<span data-ttu-id="8c9b2-251">Omdat de mijn bedrijf-sleutel al in het REGI ster bestaat, mislukt de opdracht en wordt de trans actie teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-251">Because the MyCompany key already exists in the registry, the command fails, and the transaction is rolled back.</span></span>

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="8c9b2-252">Met een Get-Transaction-opdracht wordt bevestigd dat de trans actie is teruggedraaid en dat de SubscriberCount 0 is.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-252">A Get-Transaction command confirms that the transaction has been rolled back and that the SubscriberCount is 0.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a><span data-ttu-id="8c9b2-253">VOOR BEELD 6: DE TERUGDRAAI VOORKEUR WIJZIGEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-253">EXAMPLE 6: CHANGING THE ROLLBACK PREFERENCE</span></span>

<span data-ttu-id="8c9b2-254">Als u wilt dat de trans actie meer fout tolerant is, kunt u de para meter RollbackPreference van Start-Transaction gebruiken om de voor keur te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-254">If you want the transaction to be more error tolerant, you can use the RollbackPreference parameter of Start-Transaction to change the preference.</span></span>

<span data-ttu-id="8c9b2-255">Met de volgende opdracht wordt een trans actie gestart met de voor keur voor ongedaan maken van ' Never '.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-255">The following command starts a transaction with a rollback preference of "Never".</span></span>

```powershell
start-transaction -rollbackpreference Never
```

<span data-ttu-id="8c9b2-256">In dit geval wordt de trans actie niet automatisch teruggezet wanneer de opdracht mislukt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-256">In this case, when the command fails, the transaction is not automatically rolled back.</span></span>

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="8c9b2-257">Omdat de trans actie nog steeds actief is, kunt u de opdracht opnieuw verzenden als onderdeel van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-257">Because the transaction is still active, you can resubmit the command as part of the transaction.</span></span>

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a><span data-ttu-id="8c9b2-258">VOOR BEELD 7: DE CMDLET USE-TRANS ACTION GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-258">EXAMPLE 7: USING THE USE-TRANSACTION CMDLET</span></span>

<span data-ttu-id="8c9b2-259">Met de cmdlet Use-Transaction kunt u direct scripts uitvoeren op Microsoft .NET Framework-objecten die trans acties ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-259">The Use-Transaction cmdlet enables you to do direct scripting against transaction-enabled Microsoft .NET Framework objects.</span></span> <span data-ttu-id="8c9b2-260">Use-Transaction neemt een script blok dat alleen opdrachten en expressies kan bevatten die gebruikmaken van .NET Framework objecten waarvoor trans acties zijn ingeschakeld, zoals exemplaren van de klasse micro soft. Power shell. commands. Management. TransactedString.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-260">Use-Transaction takes a script block that can only contain commands and expressions that use transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="8c9b2-261">Met de volgende opdracht wordt een trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-261">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-262">Met de volgende New-Object opdracht maakt u een instantie van de klasse TransactedString en slaat u deze op in de $t variabele.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-262">The following New-Object command creates an instance of the TransactedString class and saves it in the $t variable.</span></span>

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

<span data-ttu-id="8c9b2-263">Met de volgende opdracht wordt de methode Append van het object TransactedString gebruikt om tekst toe te voegen aan de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-263">The following command uses the Append method of the TransactedString object to add text to the string.</span></span> <span data-ttu-id="8c9b2-264">Omdat de opdracht geen deel uitmaakt van de trans actie, is de wijziging direct van kracht.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-264">Because the command is not part of the transaction, the change is effective immediately.</span></span>

```powershell
$t.append("Windows")
```

<span data-ttu-id="8c9b2-265">De volgende opdracht maakt gebruik van dezelfde toevoeg methode om tekst toe te voegen, maar voegt de tekst toe als onderdeel van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-265">The following command uses the same Append method to add text, but it adds the text as part of the transaction.</span></span> <span data-ttu-id="8c9b2-266">De opdracht bevindt zich tussen accolades en wordt ingesteld als de waarde van de para meter script Block van use-Trans Action.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-266">The command is enclosed in braces, and it is set as the value of the ScriptBlock parameter of Use-Transaction.</span></span> <span data-ttu-id="8c9b2-267">De para meter UseTransaction (UseTx) is vereist.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-267">The UseTransaction parameter (UseTx) is required.</span></span>

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

<span data-ttu-id="8c9b2-268">Als u de huidige inhoud van de transactie teken reeks in $t wilt zien, gebruikt u de methode ToString van het object TransactedString.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-268">To see the current content of the transacted string in $t, use the ToString method of the TransactedString object.</span></span>

```powershell
$t.tostring()
```

<span data-ttu-id="8c9b2-269">In de uitvoer ziet u dat alleen de niet-transactionele wijzigingen van kracht zijn.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-269">The output shows that only the non-transacted changes are effective.</span></span>

```output
Windows
```

<span data-ttu-id="8c9b2-270">Als u de huidige inhoud van de transactionele teken reeks in $t vanuit de trans actie wilt zien, sluit u de expressie in een Use-Transaction opdracht.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-270">To see the current content of the transacted string in $t from within the transaction, embed the expression in a Use-Transaction command.</span></span>

```powershell
use-transaction {$s.tostring()} -usetx
```

<span data-ttu-id="8c9b2-271">De weer gave van de trans actie wordt weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-271">The output shows the transaction view.</span></span>

```output
PowerShell
```

<span data-ttu-id="8c9b2-272">Met de volgende opdracht wordt de trans actie door doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-272">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="8c9b2-273">De laatste teken reeks weer geven:</span><span class="sxs-lookup"><span data-stu-id="8c9b2-273">To see the final string:</span></span>

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a><span data-ttu-id="8c9b2-274">VOOR BEELD 8: MEERDERE ABONNEE TRANSACTIES BEHEREN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-274">EXAMPLE 8: MANAGING MULTI-SUBSCRIBER TRANSACTIONS</span></span>

<span data-ttu-id="8c9b2-275">Wanneer u een trans actie start terwijl een andere trans actie wordt uitgevoerd, maakt Power Shell standaard geen tweede trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-275">When you start a transaction while another transaction is in progress, PowerShell does not create a second transaction by default.</span></span> <span data-ttu-id="8c9b2-276">In plaats daarvan wordt een abonnee toegevoegd aan de huidige trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-276">Instead, it adds a subscriber to the current transaction.</span></span>

<span data-ttu-id="8c9b2-277">In dit voor beeld ziet u hoe u een trans actie met meerdere abonnees kunt weer geven en beheren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-277">This example shows how to view and manage a multi-subscriber transaction.</span></span>

<span data-ttu-id="8c9b2-278">Begin met het starten van een trans actie in de sleutel HKCU: \ software.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-278">Begin by starting a transaction in the HKCU:\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-279">De volgende opdracht maakt gebruik van de Get-Transaction-opdracht voor het ophalen van de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-279">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="8c9b2-280">Het resultaat toont het object dat de actieve trans actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-280">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="8c9b2-281">Met de volgende opdracht wordt de sleutel mijn bedrijf toegevoegd aan het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-281">The following command adds the MyCompany key to the registry.</span></span> <span data-ttu-id="8c9b2-282">De opdracht gebruikt de para meter UseTransaction voor het toevoegen van de opdracht in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-282">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="8c9b2-283">De volgende opdracht maakt gebruik van de Start-Transaction-opdracht voor het starten van een trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-283">The following command uses the Start-Transaction command to start a transaction.</span></span> <span data-ttu-id="8c9b2-284">Hoewel deze opdracht bij de opdracht prompt wordt getypt, is dit scenario waarschijnlijker wanneer u een script uitvoert dat een trans actie bevat.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-284">Although this command is typed at the command prompt, this scenario is more likely to happen when you run a script that contains a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-285">Een Get-Transaction opdracht geeft aan dat het aantal abonnees van het transactie object wordt verhoogd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-285">A Get-Transaction command shows that the subscriber count on the transaction object is incremented.</span></span> <span data-ttu-id="8c9b2-286">De waarde is nu 2.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-286">The value is now 2.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="8c9b2-287">De volgende opdracht maakt gebruik van de cmdlet New-ItemProperty om de register vermelding MyKey toe te voegen aan de mijn bedrijf-sleutel.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-287">The next command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="8c9b2-288">De para meter UseTransaction wordt gebruikt voor het toevoegen van de opdracht in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-288">It uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

<span data-ttu-id="8c9b2-289">De mijn bedrijf-sleutel bestaat niet in het REGI ster, maar deze opdracht is geslaagd omdat de twee opdrachten deel uitmaken van dezelfde trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-289">The MyCompany key does not exist in the registry, but this command succeeds because the two commands are part of the same transaction.</span></span>

<span data-ttu-id="8c9b2-290">Met de volgende opdracht wordt de trans actie door doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-290">The following command commits the transaction.</span></span> <span data-ttu-id="8c9b2-291">Als de trans actie wordt teruggedraaid, wordt de trans actie teruggedraaid voor alle abonnees.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-291">If it rolled back the transaction, the transaction would be rolled back for all the subscribers.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="8c9b2-292">Een Get-Transaction-opdracht laat zien dat het aantal abonnees van het transactie object 1 is, maar dat de waarde van status nog steeds actief is (niet doorgevoerd).</span><span class="sxs-lookup"><span data-stu-id="8c9b2-292">A Get-Transaction command shows that the subscriber count on the transaction object is 1, but the value of Status is still Active (not Committed).</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="8c9b2-293">Voer een tweede volledige-trans actie-opdracht in om het door voeren van de trans actie te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-293">To finish committing the transaction, enter a second Complete- Transaction command.</span></span> <span data-ttu-id="8c9b2-294">Als u een trans actie met meerdere abonnees wilt door voeren, moet u voor elke Start-Transaction opdracht een Complete-Transaction-opdracht invoeren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-294">To commit a multi-subscriber transaction, you must enter one Complete-Transaction command for each Start-Transaction command.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="8c9b2-295">Een andere Get-Transaction-opdracht laat zien dat de trans actie is doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-295">Another Get-Transaction command shows that the transaction has been committed.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a><span data-ttu-id="8c9b2-296">VOOR BEELD 9: ONAFHANKELIJKE TRANS ACTIES BEHEREN</span><span class="sxs-lookup"><span data-stu-id="8c9b2-296">EXAMPLE 9: MANAGING INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="8c9b2-297">Wanneer u een trans actie start terwijl er een andere trans actie wordt uitgevoerd, kunt u de onafhankelijke para meter van Start-Transaction gebruiken om de nieuwe trans actie onafhankelijk van de oorspronkelijke trans actie te maken.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-297">When you start a transaction while another transaction is in progress, you can use the Independent parameter of Start-Transaction to make the new transaction independent of the original transaction.</span></span>

<span data-ttu-id="8c9b2-298">Wanneer u dit doet, wordt door Start-Transaction een nieuw transactie object gemaakt en wordt de actieve trans actie door de nieuwe trans acties uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-298">When you do, Start-Transaction creates a new transaction object and makes the new transaction the active transaction.</span></span>

<span data-ttu-id="8c9b2-299">Begin met het starten van een trans actie in de sleutel HKCU: \\ software.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-299">Begin by starting a transaction in the HKCU:\\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="8c9b2-300">De volgende opdracht maakt gebruik van de Get-Transaction-opdracht voor het ophalen van de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-300">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="8c9b2-301">Het resultaat toont het object dat de actieve trans actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-301">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="8c9b2-302">Met de volgende opdracht wordt de register sleutel mijn bedrijf toegevoegd als onderdeel van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-302">The following command adds the MyCompany registry key as part of the transaction.</span></span> <span data-ttu-id="8c9b2-303">De para meter UseTransaction (UseTx) wordt gebruikt voor het toevoegen van de opdracht in de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-303">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -use
```

<span data-ttu-id="8c9b2-304">Met de volgende opdracht wordt een nieuwe trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-304">The following command starts a new transaction.</span></span> <span data-ttu-id="8c9b2-305">De opdracht gebruikt de onafhankelijke para meter om aan te geven dat deze trans actie geen abonnee van de actieve trans actie is.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-305">The command uses the Independent parameter to indicate that this transaction is not a subscriber to the active transaction.</span></span>

```powershell
start-transaction -independent
```

<span data-ttu-id="8c9b2-306">Wanneer u een onafhankelijke trans actie maakt, wordt de nieuwe (meest recent gemaakte) trans actie de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-306">When you create an independent transaction, the new (most-recently created) transaction becomes the active transaction.</span></span> <span data-ttu-id="8c9b2-307">U kunt een Get-Transaction opdracht gebruiken om de actieve trans actie op te halen.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-307">You can use a Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="8c9b2-308">Houd er rekening mee dat de SubscriberCount van de trans actie 1 is, wat aangeeft dat er geen andere abonnees zijn en dat de trans actie nieuw is.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-308">Note that the SubscriberCount of the transaction is 1, indicating that there are no other subscribers and that the transaction is new.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="8c9b2-309">De nieuwe trans actie moet worden voltooid (doorgevoerd of teruggedraaid) voordat u de oorspronkelijke trans actie kunt beheren.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-309">The new transaction must be finished (either committed or rolled back) before you can manage the original transaction.</span></span>

<span data-ttu-id="8c9b2-310">Met de volgende opdracht wordt de sleutel MyOtherCompany toegevoegd aan het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-310">The following command adds the MyOtherCompany key to the registry.</span></span> <span data-ttu-id="8c9b2-311">De para meter UseTransaction (UseTx) wordt gebruikt voor het toevoegen van de opdracht in de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-311">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -usetx
```

<span data-ttu-id="8c9b2-312">Ga nu terug naar de trans actie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-312">Now, roll back the transaction.</span></span> <span data-ttu-id="8c9b2-313">Als er sprake is van een enkele trans actie met twee abonnees, wordt de trans actie teruggedraaid voor alle abonnees.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-313">If there were a single transaction with two subscribers, rolling back the transaction would roll back the entire transaction for all the subscribers.</span></span>

<span data-ttu-id="8c9b2-314">Omdat deze trans acties echter onafhankelijk zijn, wordt de nieuwste trans actie teruggedraaid, worden de wijzigingen in het REGI ster geannuleerd en wordt de oorspronkelijke trans actie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-314">However, because these transactions are independent, rolling back the newest transaction cancels the registry changes and makes the original transaction the active transaction.</span></span>

```powershell
undo-transaction
```

<span data-ttu-id="8c9b2-315">Met een Get-Transaction-opdracht wordt bevestigd dat de oorspronkelijke trans actie nog steeds actief is in de sessie.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-315">A Get-Transaction command confirms that the original transaction is still active in the session.</span></span>

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="8c9b2-316">Met de volgende opdracht wordt de actieve trans actie doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-316">The following command commits the active transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="8c9b2-317">Een Get-ChildItem-opdracht laat zien dat het REGI ster is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8c9b2-317">A Get-ChildItem command shows that the registry has been changed.</span></span>

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a><span data-ttu-id="8c9b2-318">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="8c9b2-318">SEE ALSO</span></span>

[<span data-ttu-id="8c9b2-319">Start-trans actie</span><span class="sxs-lookup"><span data-stu-id="8c9b2-319">Start-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Start-Transaction)

[<span data-ttu-id="8c9b2-320">Get-trans actie</span><span class="sxs-lookup"><span data-stu-id="8c9b2-320">Get-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Get-Transaction)

[<span data-ttu-id="8c9b2-321">Volt ooien-trans actie</span><span class="sxs-lookup"><span data-stu-id="8c9b2-321">Complete-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[<span data-ttu-id="8c9b2-322">Ongedaan maken-trans actie</span><span class="sxs-lookup"><span data-stu-id="8c9b2-322">Undo-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[<span data-ttu-id="8c9b2-323">Gebruik-trans actie</span><span class="sxs-lookup"><span data-stu-id="8c9b2-323">Use-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Use-Transaction)

[<span data-ttu-id="8c9b2-324">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8c9b2-324">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[<span data-ttu-id="8c9b2-325">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="8c9b2-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[<span data-ttu-id="8c9b2-326">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8c9b2-326">about_Providers</span></span>](about_Providers.md)
