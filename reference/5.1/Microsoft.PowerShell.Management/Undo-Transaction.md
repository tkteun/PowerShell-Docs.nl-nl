---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250528"
---
# <span data-ttu-id="2e693-103">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="2e693-103">Undo-Transaction</span></span>

## <span data-ttu-id="2e693-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2e693-104">SYNOPSIS</span></span>
<span data-ttu-id="2e693-105">Hiermee wordt de actieve trans actie teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="2e693-105">Rolls back the active transaction.</span></span>

## <span data-ttu-id="2e693-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2e693-106">SYNTAX</span></span>

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2e693-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2e693-107">DESCRIPTION</span></span>
<span data-ttu-id="2e693-108">Met de cmdlet **Undo-trans actie** wordt de actieve trans actie teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="2e693-108">The **Undo-Transaction** cmdlet rolls back the active transaction.</span></span>
<span data-ttu-id="2e693-109">Wanneer u een trans actie terugdraait, worden de wijzigingen die zijn aangebracht door de opdrachten in de trans actie, verwijderd en worden de gegevens hersteld naar het oorspronkelijke formulier.</span><span class="sxs-lookup"><span data-stu-id="2e693-109">When you roll back a transaction, the changes that were made by the commands in the transaction are discarded and the data is restored to its original form.</span></span>

<span data-ttu-id="2e693-110">Als de trans actie meerdere abonnees bevat, wordt met een opdracht voor **ongedaan maken** de gehele trans actie voor alle abonnees teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="2e693-110">If the transaction includes multiple subscribers, an **Undo-Transaction** command rolls back the whole transaction for all subscribers.</span></span>

<span data-ttu-id="2e693-111">Standaard worden trans acties automatisch teruggezet als een opdracht in de trans actie een fout genereert.</span><span class="sxs-lookup"><span data-stu-id="2e693-111">By default, transactions are rolled back automatically if any command in the transaction generates an error.</span></span>
<span data-ttu-id="2e693-112">Trans acties kunnen echter worden gestart met een andere terugdraai voorkeur en u kunt deze cmdlet gebruiken om de actieve trans actie op elk gewenst moment terug te draaien.</span><span class="sxs-lookup"><span data-stu-id="2e693-112">However, transactions can be started by using a different rollback preference and you can use this cmdlet to roll back the active transaction at any time.</span></span>

<span data-ttu-id="2e693-113">De cmdlet **Undo-trans actie** is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e693-113">The **Undo-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="2e693-114">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e693-114">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="2e693-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2e693-115">EXAMPLES</span></span>

### <span data-ttu-id="2e693-116">Voor beeld 1: de huidige trans actie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="2e693-116">Example 1: Roll back the current transaction</span></span>

```
PS C:\> Undo-Transaction
```

<span data-ttu-id="2e693-117">Met deze opdracht wordt de huidige, actieve trans actie teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="2e693-117">This command rolls back the current, active, transaction.</span></span>

### <span data-ttu-id="2e693-118">Voor beeld 2: een trans actie starten en terugdraaien</span><span class="sxs-lookup"><span data-stu-id="2e693-118">Example 2: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

<span data-ttu-id="2e693-119">In dit voor beeld wordt een trans actie gestart en vervolgens weer teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="2e693-119">This example starts a transaction and then rolls it back.</span></span>
<span data-ttu-id="2e693-120">Als gevolg hiervan worden er geen wijzigingen aangebracht in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="2e693-120">As a result, no changes are made to the registry.</span></span>

### <span data-ttu-id="2e693-121">Voor beeld 3: terugdraaien van een trans actie voor alle abonnees</span><span class="sxs-lookup"><span data-stu-id="2e693-121">Example 3: Roll back a transaction for all subscribers</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

<span data-ttu-id="2e693-122">In dit voor beeld wordt gedemonstreerd dat wanneer een abonnee een trans actie terugstuurt, de hele trans actie wordt teruggedraaid voor alle abonnees.</span><span class="sxs-lookup"><span data-stu-id="2e693-122">This example demonstrates that when any subscriber rolls back a transaction, the whole transaction is rolled back for all subscribers.</span></span>

<span data-ttu-id="2e693-123">Met de eerste opdracht wordt de locatie gewijzigd in de register sleutel HKCU: \ software.</span><span class="sxs-lookup"><span data-stu-id="2e693-123">The first command changes the location to the HKCU:\Software registry key.</span></span>

<span data-ttu-id="2e693-124">Met de tweede opdracht wordt een trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="2e693-124">The second command starts a transaction.</span></span>

<span data-ttu-id="2e693-125">De derde opdracht maakt gebruik van de New-Item cmdlet om een nieuwe register sleutel te maken.</span><span class="sxs-lookup"><span data-stu-id="2e693-125">The third command uses the New-Item cmdlet to create a new registry key.</span></span>
<span data-ttu-id="2e693-126">De opdracht maakt gebruik van de para meter *UseTransaction* om de wijziging in de trans actie op te neemt.</span><span class="sxs-lookup"><span data-stu-id="2e693-126">The command uses the *UseTransaction* parameter to include the change in the transaction.</span></span>

<span data-ttu-id="2e693-127">De vierde opdracht maakt gebruik van de cmdlet Get-Transaction om de actieve trans actie te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="2e693-127">The fourth command uses the Get-Transaction cmdlet to get the active transaction.</span></span>
<span data-ttu-id="2e693-128">U ziet dat de status actief is en dat het aantal abonnees 1 is.</span><span class="sxs-lookup"><span data-stu-id="2e693-128">Notice that the status is Active and the subscriber count is 1.</span></span>

<span data-ttu-id="2e693-129">De vijfde opdracht maakt gebruik van de Start-Transaction opdracht opnieuw.</span><span class="sxs-lookup"><span data-stu-id="2e693-129">The fifth command uses the Start-Transaction command again.</span></span>
<span data-ttu-id="2e693-130">Normaal gesp roken wordt een trans actie gestart terwijl er een andere trans actie wordt uitgevoerd wanneer een script dat wordt gebruikt door de hoofd transactie een eigen volledige trans actie bevat.</span><span class="sxs-lookup"><span data-stu-id="2e693-130">Typically, starting a transaction while another transaction is in progress occurs when a script that is used by the main transaction includes its own complete transaction.</span></span>
<span data-ttu-id="2e693-131">Dit voor beeld wordt interactief uitgevoerd, zodat u het in fasen kunt onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="2e693-131">This example is performed interactively so that you can examine it in stages.</span></span>
<span data-ttu-id="2e693-132">Wanneer u een **Start-trans actie-** opdracht uitvoert terwijl er een andere trans actie wordt uitgevoerd, worden de opdrachten toegevoegd aan de bestaande trans actie als een nieuwe abonnee en wordt het aantal abonnees verhoogd.</span><span class="sxs-lookup"><span data-stu-id="2e693-132">When you run a **Start-Transaction** command while another transaction is in progress, the commands join the existing transaction as a new subscriber and the subscriber count is incremented.</span></span>

<span data-ttu-id="2e693-133">De zesde opdracht maakt gebruik van de cmdlet **Get-trans actie** om de actieve trans actie op te halen.</span><span class="sxs-lookup"><span data-stu-id="2e693-133">The sixth command uses the **Get-Transaction** cmdlet to get the active transaction.</span></span>
<span data-ttu-id="2e693-134">U ziet dat het aantal abonnees nu 2 is.</span><span class="sxs-lookup"><span data-stu-id="2e693-134">Notice that the subscriber count is now 2.</span></span>

<span data-ttu-id="2e693-135">De zevende opdracht maakt gebruik van **ongedaan maken-trans** actie voor het terugdraaien van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="2e693-135">The seventh command uses **Undo-Transaction** to roll back the transaction.</span></span>
<span data-ttu-id="2e693-136">Met deze opdracht worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2e693-136">This command does not return any objects.</span></span>

<span data-ttu-id="2e693-137">De laatste opdracht is een **Get-trans actie** opdracht die de actieve, of in dit geval de meest recent actieve trans actie haalt.</span><span class="sxs-lookup"><span data-stu-id="2e693-137">The final command is a **Get-Transaction** command that gets the active, or in this case, the most recently active, transaction.</span></span>
<span data-ttu-id="2e693-138">De resultaten geven aan dat de trans actie wordt teruggedraaid en dat het aantal abonnees 0 is, wat aangeeft dat de trans actie is teruggedraaid voor alle abonnees.</span><span class="sxs-lookup"><span data-stu-id="2e693-138">The results show that the transaction is rolled back, and that the subscriber count is 0, showing that the transaction was rolled back for all subscribers.</span></span>

## <span data-ttu-id="2e693-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e693-139">PARAMETERS</span></span>

### <span data-ttu-id="2e693-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2e693-140">-Confirm</span></span>
<span data-ttu-id="2e693-141">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2e693-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2e693-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2e693-142">-WhatIf</span></span>
<span data-ttu-id="2e693-143">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2e693-143">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2e693-144">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2e693-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2e693-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e693-145">CommonParameters</span></span>
<span data-ttu-id="2e693-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e693-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e693-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e693-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e693-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="2e693-148">INPUTS</span></span>

### <span data-ttu-id="2e693-149">Geen</span><span class="sxs-lookup"><span data-stu-id="2e693-149">None</span></span>
<span data-ttu-id="2e693-150">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2e693-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="2e693-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2e693-151">OUTPUTS</span></span>

### <span data-ttu-id="2e693-152">Geen</span><span class="sxs-lookup"><span data-stu-id="2e693-152">None</span></span>
<span data-ttu-id="2e693-153">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2e693-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="2e693-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2e693-154">NOTES</span></span>

* <span data-ttu-id="2e693-155">U kunt een doorgevoerde trans actie niet terugdraaien.</span><span class="sxs-lookup"><span data-stu-id="2e693-155">You cannot roll back a transaction that has been committed.</span></span>

  <span data-ttu-id="2e693-156">U kunt geen andere trans actie terugdraaien dan de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="2e693-156">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="2e693-157">Als u een andere, onafhankelijke trans actie wilt terugdraaien, moet u eerst de actieve trans actie door voeren of terugdraaien.</span><span class="sxs-lookup"><span data-stu-id="2e693-157">To roll back a different, independent transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="2e693-158">Als de trans actie wordt teruggedraaid, wordt de trans actie beëindigd.</span><span class="sxs-lookup"><span data-stu-id="2e693-158">Rolling back the transaction ends the transaction.</span></span>
<span data-ttu-id="2e693-159">Als u een trans actie opnieuw wilt gebruiken, moet u een nieuwe trans actie starten.</span><span class="sxs-lookup"><span data-stu-id="2e693-159">To use a transaction again, you must start a new transaction.</span></span>

## <span data-ttu-id="2e693-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2e693-160">RELATED LINKS</span></span>

[<span data-ttu-id="2e693-161">Volt ooien-trans actie</span><span class="sxs-lookup"><span data-stu-id="2e693-161">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="2e693-162">Get-trans actie</span><span class="sxs-lookup"><span data-stu-id="2e693-162">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="2e693-163">Start-trans actie</span><span class="sxs-lookup"><span data-stu-id="2e693-163">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="2e693-164">Gebruik-trans actie</span><span class="sxs-lookup"><span data-stu-id="2e693-164">Use-Transaction</span></span>](Use-Transaction.md)
