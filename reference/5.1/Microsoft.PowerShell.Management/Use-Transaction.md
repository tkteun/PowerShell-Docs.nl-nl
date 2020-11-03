---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250532"
---
# <span data-ttu-id="4346b-103">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="4346b-103">Use-Transaction</span></span>

## <span data-ttu-id="4346b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4346b-104">SYNOPSIS</span></span>
<span data-ttu-id="4346b-105">Voegt het script blok toe aan de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-105">Adds the script block to the active transaction.</span></span>

## <span data-ttu-id="4346b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4346b-106">SYNTAX</span></span>

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="4346b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4346b-107">DESCRIPTION</span></span>
<span data-ttu-id="4346b-108">Met de cmdlet **use-trans actie** wordt een script blok toegevoegd aan een actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-108">The **Use-Transaction** cmdlet adds a script block to an active transaction.</span></span>
<span data-ttu-id="4346b-109">Hiermee kunt u scripts transactioneel uitvoeren met behulp van Microsoft .NET Framework-objecten met trans acties.</span><span class="sxs-lookup"><span data-stu-id="4346b-109">This enables you to do transacted scripting by using transaction-enabled Microsoft .NET Framework objects.</span></span>
<span data-ttu-id="4346b-110">Het script blok kan alleen objecten bevatten waarvoor trans acties zijn ingeschakeld .NET Framework, zoals exemplaren van de klasse micro soft. Power shell. commands. Management. TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-110">The script block can contain only transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="4346b-111">De para meter *UseTransaction* , die optioneel is voor de meeste cmdlets, is vereist wanneer u deze cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4346b-111">The *UseTransaction* parameter, which is optional for most cmdlets, is required when you use this cmdlet.</span></span>

<span data-ttu-id="4346b-112">**Use-Trans Action** is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4346b-112">**Use-Transaction** is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="4346b-113">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4346b-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="4346b-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4346b-114">EXAMPLES</span></span>

### <span data-ttu-id="4346b-115">Voor beeld 1: script met behulp van een object waarvoor trans acties zijn ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="4346b-115">Example 1: Script by using a transaction-enabled object</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

<span data-ttu-id="4346b-116">In dit voor beeld ziet u hoe u **met behulp van-trans actie** script kunt gebruiken voor een .NET Framework object waarvoor een trans actie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="4346b-116">This example shows how to use **Use-Transaction** to script against a transaction-enabled .NET Framework object.</span></span>
<span data-ttu-id="4346b-117">In dit geval is het object een **TransactedString** -object.</span><span class="sxs-lookup"><span data-stu-id="4346b-117">In this case, the object is a **TransactedString** object.</span></span>

<span data-ttu-id="4346b-118">De eerste opdracht gebruikt de cmdlet Start-Transaction om een trans actie te starten.</span><span class="sxs-lookup"><span data-stu-id="4346b-118">The first command uses the Start-Transaction cmdlet to start a transaction.</span></span>

<span data-ttu-id="4346b-119">De tweede opdracht maakt gebruik van de New-Object opdracht voor het maken van een **TransactedString** -object.</span><span class="sxs-lookup"><span data-stu-id="4346b-119">The second command uses the New-Object command to create a **TransactedString** object.</span></span>
<span data-ttu-id="4346b-120">Het object wordt opgeslagen in de variabele $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-120">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="4346b-121">De derde en vierde opdracht gebruiken beide de methode **Append** van het object **TransactedString** om tekst toe te voegen aan de waarde van $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-121">The third and fourth commands both use the **Append** method of the **TransactedString** object to add text to the value of $TransactedString.</span></span>
<span data-ttu-id="4346b-122">Eén opdracht maakt deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-122">One command is part of the transaction.</span></span>
<span data-ttu-id="4346b-123">De andere opdracht is niet.</span><span class="sxs-lookup"><span data-stu-id="4346b-123">The other command is not.</span></span>

<span data-ttu-id="4346b-124">De derde opdracht maakt gebruik van de methode **Append** van de transactionele teken reeks om Hello toe te voegen aan de waarde van $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-124">The third command uses the **Append** method of the transacted string to add Hello to the value of $TransactedString.</span></span>
<span data-ttu-id="4346b-125">Omdat de opdracht geen deel uitmaakt van de trans actie, wordt de wijziging onmiddellijk toegepast.</span><span class="sxs-lookup"><span data-stu-id="4346b-125">Because the command is not part of the transaction, the change is applied immediately.</span></span>

<span data-ttu-id="4346b-126">De vierde opdracht maakt **gebruik van een trans actie** om tekst toe te voegen aan de teken reeks in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-126">The fourth command uses **Use-Transaction** to add text to the string in the transaction.</span></span>
<span data-ttu-id="4346b-127">De opdracht gebruikt de methode **Append** om ', World ' toe te voegen aan de waarde van $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-127">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>
<span data-ttu-id="4346b-128">De opdracht bevindt zich tussen accolades ( {} ) om het een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="4346b-128">The command is enclosed in braces ( {} ) to make it a script block.</span></span>
<span data-ttu-id="4346b-129">De para meter *UseTransaction* is vereist in deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="4346b-129">The *UseTransaction* parameter is required in this command.</span></span>

<span data-ttu-id="4346b-130">De vijfde en zesde opdrachten gebruiken de **toString** -methode van het object **TransactedString** om de waarde van de **TransactedString** als een teken reeks weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4346b-130">The fifth and sixth commands use the **ToString** method of the **TransactedString** object to display the value of the **TransactedString** as a string.</span></span>
<span data-ttu-id="4346b-131">De ene opdracht maakt deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-131">Again, one command is part of the transaction.</span></span>
<span data-ttu-id="4346b-132">De andere trans actie is niet.</span><span class="sxs-lookup"><span data-stu-id="4346b-132">The other transaction is not.</span></span>

<span data-ttu-id="4346b-133">De vijfde opdracht maakt gebruik van de **toString** -methode om de huidige waarde van de variabele $TransactedString weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4346b-133">The fifth command uses the **ToString** method to display the current value of the $TransactedString variable.</span></span>
<span data-ttu-id="4346b-134">Omdat deze geen deel uitmaakt van de trans actie, wordt alleen de huidige status van de teken reeks weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4346b-134">Because it is not part of the transaction, it displays only the current state of the string.</span></span>

<span data-ttu-id="4346b-135">De zesde opdracht gebruikt **gebruik-trans actie** om dezelfde opdracht uit te voeren in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-135">The sixth command uses **Use-Transaction** to run the same command in the transaction.</span></span>
<span data-ttu-id="4346b-136">Omdat de opdracht deel uitmaakt van de trans actie, wordt de huidige waarde van de teken reeks in de trans actie weer gegeven, net zoals een voor beeld van de trans actie wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4346b-136">Because the command is part of the transaction, it displays the current value of the string in the transaction, much like a preview of the transaction changes.</span></span>

<span data-ttu-id="4346b-137">De zevende opdracht maakt gebruik van de Complete-Transaction cmdlet om de trans actie door te voeren.</span><span class="sxs-lookup"><span data-stu-id="4346b-137">The seventh command uses the Complete-Transaction cmdlet to commit the transaction.</span></span>

<span data-ttu-id="4346b-138">De laatste opdracht gebruikt de **toString** -methode om de resulterende waarde van de variabele als een teken reeks weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4346b-138">The final command uses the **ToString** method to display the resulting value of the variable as a string.</span></span>

### <span data-ttu-id="4346b-139">Voor beeld 2: terugdraaien van een trans actie</span><span class="sxs-lookup"><span data-stu-id="4346b-139">Example 2: Roll back a transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

<span data-ttu-id="4346b-140">In dit voor beeld ziet u het effect van het terugdraaien van een trans actie met de opdrachten voor **gebruik van trans acties** .</span><span class="sxs-lookup"><span data-stu-id="4346b-140">This example shows the effect of rolling back a transaction that includes **Use-Transaction** commands.</span></span>
<span data-ttu-id="4346b-141">Net als bij alle opdrachten in een trans actie, worden de transactionele wijzigingen genegeerd en blijven de gegevens ongewijzigd wanneer de trans actie wordt teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="4346b-141">Like all commands in a transaction, when the transaction is rolled back, the transacted changes are discarded and the data is unchanged.</span></span>

<span data-ttu-id="4346b-142">De eerste opdracht maakt gebruik van **Start-trans actie** om een trans actie te starten.</span><span class="sxs-lookup"><span data-stu-id="4346b-142">The first command uses **Start-Transaction** to start a transaction.</span></span>

<span data-ttu-id="4346b-143">De tweede opdracht maakt gebruik van **New-object** om een **TransactedString** -object te maken.</span><span class="sxs-lookup"><span data-stu-id="4346b-143">The second command uses **New-Object** to create a **TransactedString** object.</span></span>
<span data-ttu-id="4346b-144">Het object wordt opgeslagen in de variabele $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-144">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="4346b-145">De derde opdracht, die geen deel uitmaakt van de trans actie, gebruikt de methode **Append** om ' Hello ' toe te voegen aan de waarde van $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-145">The third command, which is not part of the transaction, uses the **Append** method to add "Hello" to the value of $TransactedString.</span></span>

<span data-ttu-id="4346b-146">De vierde opdracht gebruikt **gebruik-trans actie** om een andere opdracht uit te voeren die gebruikmaakt van de methode **Append** in de trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-146">The fourth command uses **Use-Transaction** to run another command that uses the **Append** method in the transaction.</span></span>
<span data-ttu-id="4346b-147">De opdracht gebruikt de methode **Append** om ', World ' toe te voegen aan de waarde van $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4346b-147">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>

<span data-ttu-id="4346b-148">De vijfde opdracht maakt gebruik van de cmdlet Undo-Transaction om de trans actie terug te draaien.</span><span class="sxs-lookup"><span data-stu-id="4346b-148">The fifth command uses the Undo-Transaction cmdlet to roll back the transaction.</span></span>
<span data-ttu-id="4346b-149">Als gevolg hiervan worden alle opdrachten die in de trans actie worden uitgevoerd, omgekeerd.</span><span class="sxs-lookup"><span data-stu-id="4346b-149">As a result, all commands performed in the transaction are reversed.</span></span>

<span data-ttu-id="4346b-150">De laatste opdracht gebruikt de **toString** -methode om de resulterende waarde van $TransactedString als een teken reeks weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4346b-150">The final command uses the **ToString** method to display the resulting value of $TransactedString as a string.</span></span>
<span data-ttu-id="4346b-151">De resultaten geven aan dat alleen de wijzigingen die buiten de trans actie zijn aangebracht, zijn toegepast op het object.</span><span class="sxs-lookup"><span data-stu-id="4346b-151">The results show that only the changes that were made outside the transaction were applied to the object.</span></span>

## <span data-ttu-id="4346b-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4346b-152">PARAMETERS</span></span>

### <span data-ttu-id="4346b-153">-TransactedScript</span><span class="sxs-lookup"><span data-stu-id="4346b-153">-TransactedScript</span></span>
<span data-ttu-id="4346b-154">Hiermee geeft u het script blok op dat in de trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4346b-154">Specifies the script block that is run in the transaction.</span></span>
<span data-ttu-id="4346b-155">Voer een geldig script blok in tussen accolades ({}).</span><span class="sxs-lookup"><span data-stu-id="4346b-155">Enter any valid script block enclosed in braces ( { } ).</span></span>
<span data-ttu-id="4346b-156">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="4346b-156">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4346b-157">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="4346b-157">-UseTransaction</span></span>
<span data-ttu-id="4346b-158">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="4346b-158">Includes the command in the active transaction.</span></span>
<span data-ttu-id="4346b-159">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4346b-159">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="4346b-160">Zie about_transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4346b-160">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4346b-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4346b-161">CommonParameters</span></span>
<span data-ttu-id="4346b-162">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4346b-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4346b-163">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4346b-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4346b-164">INVOER</span><span class="sxs-lookup"><span data-stu-id="4346b-164">INPUTS</span></span>

### <span data-ttu-id="4346b-165">Geen</span><span class="sxs-lookup"><span data-stu-id="4346b-165">None</span></span>
<span data-ttu-id="4346b-166">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4346b-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4346b-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4346b-167">OUTPUTS</span></span>

### <span data-ttu-id="4346b-168">PSObject</span><span class="sxs-lookup"><span data-stu-id="4346b-168">PSObject</span></span>
<span data-ttu-id="4346b-169">Met deze cmdlet wordt het resultaat van de trans actie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4346b-169">This cmdlet returns the result of the transaction.</span></span>

## <span data-ttu-id="4346b-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4346b-170">NOTES</span></span>

* <span data-ttu-id="4346b-171">De para meter *UseTransaction* bevat de opdracht in de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="4346b-171">The *UseTransaction* parameter includes the command in the active transaction.</span></span> <span data-ttu-id="4346b-172">Omdat de cmdlet **use-Trans Action** altijd wordt gebruikt in trans acties, is deze para meter vereist om een **use-trans actie-** opdracht van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="4346b-172">Because the **Use-Transaction** cmdlet is always used in transactions, this parameter is required to make any **Use-Transaction** command effective.</span></span>

*

## <span data-ttu-id="4346b-173">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4346b-173">RELATED LINKS</span></span>

[<span data-ttu-id="4346b-174">Volt ooien-trans actie</span><span class="sxs-lookup"><span data-stu-id="4346b-174">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="4346b-175">Get-trans actie</span><span class="sxs-lookup"><span data-stu-id="4346b-175">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="4346b-176">Start-trans actie</span><span class="sxs-lookup"><span data-stu-id="4346b-176">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="4346b-177">Ongedaan maken-trans actie</span><span class="sxs-lookup"><span data-stu-id="4346b-177">Undo-Transaction</span></span>](Undo-Transaction.md)
