---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250830"
---
# <span data-ttu-id="b1c2d-103">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="b1c2d-103">Complete-Transaction</span></span>

## <span data-ttu-id="b1c2d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b1c2d-104">SYNOPSIS</span></span>
<span data-ttu-id="b1c2d-105">Hiermee wordt de actieve trans actie doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-105">Commits the active transaction.</span></span>

## <span data-ttu-id="b1c2d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b1c2d-106">SYNTAX</span></span>

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b1c2d-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b1c2d-107">DESCRIPTION</span></span>
<span data-ttu-id="b1c2d-108">De **volledige-trans actie-** cmdlet voert een actieve trans actie door.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-108">The **Complete-Transaction** cmdlet commits an active transaction.</span></span>
<span data-ttu-id="b1c2d-109">Wanneer u een trans actie doorvoert, worden de opdrachten in de trans actie voltooid en worden de gegevens die worden beïnvloed door de opdrachten, gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-109">When you commit a transaction, the commands in the transaction are finalized and the data affected by the commands is changed.</span></span>

<span data-ttu-id="b1c2d-110">Als de trans actie meerdere abonnees bevat, moet u voor elke Start-Transaction-opdracht één opdracht voor **volt ooien van trans acties** invoeren.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-110">If the transaction includes multiple subscribers, to commit the transaction, you must enter one **Complete-Transaction** command for every Start-Transaction command.</span></span>

<span data-ttu-id="b1c2d-111">De **volledige-trans actie-** cmdlet is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-111">The **Complete-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="b1c2d-112">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-112">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="b1c2d-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b1c2d-113">EXAMPLES</span></span>

### <span data-ttu-id="b1c2d-114">Voor beeld 1: een trans actie door voeren</span><span class="sxs-lookup"><span data-stu-id="b1c2d-114">Example 1: Commit a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

<span data-ttu-id="b1c2d-115">In dit voor beeld ziet u wat er gebeurt wanneer u de cmdlet **complete-trans** actie gebruikt om een trans actie door te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-115">This example shows what happens when you use the **Complete-Transaction** cmdlet to commit a transaction.</span></span>

<span data-ttu-id="b1c2d-116">De trans actie wordt gestart met de opdracht **Start-trans actie** .</span><span class="sxs-lookup"><span data-stu-id="b1c2d-116">The **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="b1c2d-117">De New-Item opdracht gebruikt de para meter *UseTransaction* om de opdracht in de trans actie op te neemt.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-117">The New-Item command uses the *UseTransaction* parameter to include the command in the transaction.</span></span>

<span data-ttu-id="b1c2d-118">De eerste dir-opdracht (Get-Child item) laat zien dat het nieuwe item nog niet is toegevoegd aan het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-118">The first dir (Get-ChildItem) command shows that the new item has not yet been added to the registry.</span></span>

<span data-ttu-id="b1c2d-119">De opdracht **volt ooien-trans actie** voert de trans actie door, waardoor de wijziging van het REGI ster effectief wordt.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-119">The **Complete-Transaction** command commits the transaction, which makes the registry change effective.</span></span>
<span data-ttu-id="b1c2d-120">Als gevolg hiervan wordt met de tweede opdracht dir aangegeven dat het REGI ster is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-120">As a result, the second dir command shows that the registry is changed.</span></span>

### <span data-ttu-id="b1c2d-121">Voor beeld 2: een trans actie met meer dan één abonnee vastleggen</span><span class="sxs-lookup"><span data-stu-id="b1c2d-121">Example 2: Commit a transaction that has more than one subscriber</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

<span data-ttu-id="b1c2d-122">In dit voor beeld ziet u hoe u met **volledige trans actie** een trans actie met meer dan één abonnee kunt door voeren.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-122">This example shows how to use **Complete-Transaction** to commit a transaction that has more than one subscriber.</span></span>

<span data-ttu-id="b1c2d-123">Als u een trans actie met meerdere abonnees wilt door voeren, moet u één opdracht voor **volt ooien van trans** acties invoeren voor elke opdracht voor **het starten van de trans actie** .</span><span class="sxs-lookup"><span data-stu-id="b1c2d-123">To commit a multi-subscriber transaction, you must enter one **Complete-Transaction** command for every **Start-Transaction** command.</span></span>
<span data-ttu-id="b1c2d-124">De gegevens worden alleen gewijzigd wanneer de laatste **voltooide-trans actie-** opdracht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-124">The data is changed only when the final **Complete-Transaction** command is submitted.</span></span>

<span data-ttu-id="b1c2d-125">In het volgende voor beeld ziet u een reeks opdrachten die zijn ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-125">For demonstration purposes, this example shows a series of commands entered at the command line.</span></span>
<span data-ttu-id="b1c2d-126">In de praktijk worden trans acties waarschijnlijk uitgevoerd in scripts, waarbij de secundaire trans actie wordt uitgevoerd door een functie of hulp script dat wordt aangeroepen door het hoofd script.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-126">In practice, transactions are likely to be run in scripts, with the secondary transaction being run by a function or helper script that is called by the main script.</span></span>

<span data-ttu-id="b1c2d-127">In dit voor beeld wordt met een **Start-trans actie-** opdracht de trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-127">In this example, a **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="b1c2d-128">Met de opdracht **Nieuw item** met de para meter *UseTransaction* wordt de sleutel mijn bedrijf toegevoegd aan de software sleutel.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-128">A **New-Item** command with the *UseTransaction* parameter adds the MyCompany key to the Software key.</span></span>
<span data-ttu-id="b1c2d-129">Hoewel met de cmdlet **New-item** een sleutel object wordt geretourneerd, zijn de gegevens in het REGI ster nog niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-129">Although the **New-Item** cmdlet returns a key object, the data in the registry is not yet changed.</span></span>

<span data-ttu-id="b1c2d-130">Een tweede **Start-trans actie-** opdracht voegt een tweede abonnee toe aan de bestaande trans actie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-130">A second **Start-Transaction** command adds a second subscriber to the existing transaction.</span></span>
<span data-ttu-id="b1c2d-131">Met de cmdlet **Get-trans actie** wordt bevestigd dat het aantal abonnees 2 is.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-131">The **Get-Transaction** cmdlet confirms that the subscriber count is 2.</span></span>
<span data-ttu-id="b1c2d-132">Een New-ItemProperty opdracht met de para meter *UseTransaction* voegt een register vermelding toe aan de nieuwe mijn bedrijf-sleutel.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-132">A New-ItemProperty command with the *UseTransaction* parameter adds a registry entry to the new MyCompany key.</span></span>
<span data-ttu-id="b1c2d-133">Opnieuw, de opdracht retourneert een waarde, maar het REGI ster wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-133">Again, the command returns a value, but the registry is not changed.</span></span>

<span data-ttu-id="b1c2d-134">Met de eerste opdracht **volt ooien-trans actie** wordt het aantal abonnees verminderd met 1.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-134">The first **Complete-Transaction** command reduces the subscriber count by 1.</span></span>
<span data-ttu-id="b1c2d-135">Dit wordt bevestigd door de opdracht **Get-trans actie** .</span><span class="sxs-lookup"><span data-stu-id="b1c2d-135">This is confirmed by a **Get-Transaction** command.</span></span>
<span data-ttu-id="b1c2d-136">Er worden echter geen gegevens gewijzigd, zoals wordt weer gegeven door een dir m \* ( **Get-Child item** ) opdracht.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-136">However, no data is changed, as evidenced by a dir m\* ( **Get-ChildItem** ) command.</span></span>

<span data-ttu-id="b1c2d-137">Met de tweede opdracht **volt ooien-trans actie** wordt de hele trans actie door gegeven en worden de gegevens in het REGI ster gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-137">The second **Complete-Transaction** command commits the entire transaction and changes the data in the registry.</span></span>
<span data-ttu-id="b1c2d-138">Dit wordt bevestigd door een tweede dir m \* opdracht, waarin de wijzigingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-138">This is confirmed by a second dir m\* command, which shows the changes.</span></span>

### <span data-ttu-id="b1c2d-139">Voor beeld 3: een trans actie uitvoeren waarbij geen gegevens worden gewijzigd</span><span class="sxs-lookup"><span data-stu-id="b1c2d-139">Example 3: Perform a transaction that does not change any data</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="b1c2d-140">Dit voor beeld toont de waarde van het gebruik van Get- \* opdrachten en andere opdrachten die geen gegevens wijzigen in een trans actie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-140">This example shows the value of using Get-\* commands, and other commands that do not change data, in a transaction.</span></span>
<span data-ttu-id="b1c2d-141">Wanneer een Get- \* opdracht wordt gebruikt in een trans actie, worden de objecten opgehaald die deel uitmaken van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-141">When a Get-\* command is used in a transaction, it gets the objects that are part of the transaction.</span></span>
<span data-ttu-id="b1c2d-142">Zo kunt u een voor beeld van de wijzigingen in de trans actie bekijken voordat de wijzigingen worden doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-142">This allows you to preview the changes in the transaction before the changes are committed.</span></span>

<span data-ttu-id="b1c2d-143">In dit voor beeld wordt een trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-143">In this example, a transaction is started.</span></span>
<span data-ttu-id="b1c2d-144">Een New-Item opdracht met de para meter *UseTransaction* voegt een nieuwe sleutel toe aan het REGI ster als onderdeel van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-144">A New-Item command with the *UseTransaction* parameter adds a new key to the registry as part of the transaction.</span></span>

<span data-ttu-id="b1c2d-145">Omdat de nieuwe register sleutel pas wordt toegevoegd aan het REGI ster als de opdracht **volt ooien-trans actie** is uitgevoerd, wordt in een eenvoudige dir-opdracht ( **Get-Child item** ) het REGI ster zonder de nieuwe sleutel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-145">Because the new registry key is not added to the registry until the **Complete-Transaction** command is run, a simple dir ( **Get-ChildItem** ) command shows the registry without the new key.</span></span>

<span data-ttu-id="b1c2d-146">Wanneer u echter de para meter *UseTransaction* toevoegt aan de opdracht dir, wordt de opdracht onderdeel van de trans actie en worden de items in de trans actie opgehaald, zelfs als ze nog niet zijn toegevoegd aan de gegevens.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-146">However, when you add the *UseTransaction* parameter to the dir command, the command becomes part of the transaction, and it gets the items in the transaction even if they are not yet added to the data.</span></span>

## <span data-ttu-id="b1c2d-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b1c2d-147">PARAMETERS</span></span>

### <span data-ttu-id="b1c2d-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b1c2d-148">-Confirm</span></span>
<span data-ttu-id="b1c2d-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b1c2d-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b1c2d-150">-WhatIf</span></span>
<span data-ttu-id="b1c2d-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b1c2d-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b1c2d-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1c2d-153">CommonParameters</span></span>
<span data-ttu-id="b1c2d-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1c2d-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b1c2d-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="b1c2d-156">INPUTS</span></span>

### <span data-ttu-id="b1c2d-157">Geen</span><span class="sxs-lookup"><span data-stu-id="b1c2d-157">None</span></span>
<span data-ttu-id="b1c2d-158">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-158">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b1c2d-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b1c2d-159">OUTPUTS</span></span>

### <span data-ttu-id="b1c2d-160">Geen</span><span class="sxs-lookup"><span data-stu-id="b1c2d-160">None</span></span>
<span data-ttu-id="b1c2d-161">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b1c2d-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b1c2d-162">NOTES</span></span>

* <span data-ttu-id="b1c2d-163">U kunt een trans actie die is doorgevoerd, niet terugdraaien of een trans actie die is teruggedraaid door voeren.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-163">You cannot roll back a transaction that has been committed, or commit a transaction that has been rolled back.</span></span>

  <span data-ttu-id="b1c2d-164">U kunt geen andere trans actie terugdraaien dan de actieve trans actie.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-164">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="b1c2d-165">Als u een andere trans actie wilt terugdraaien, moet u eerst de actieve trans actie door voeren of terugdraaien.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-165">To roll back a different transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="b1c2d-166">Als een deel van een trans actie niet kan worden doorgevoerd, bijvoorbeeld wanneer een opdracht in de trans actie resulteert in een fout, wordt de hele trans actie teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="b1c2d-166">By default, if any part of a transaction cannot be committed, such as when a command in the transaction results in an error, the entire transaction is rolled back.</span></span>

*

## <span data-ttu-id="b1c2d-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b1c2d-167">RELATED LINKS</span></span>

[<span data-ttu-id="b1c2d-168">Get-trans actie</span><span class="sxs-lookup"><span data-stu-id="b1c2d-168">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="b1c2d-169">Start-trans actie</span><span class="sxs-lookup"><span data-stu-id="b1c2d-169">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="b1c2d-170">Ongedaan maken-trans actie</span><span class="sxs-lookup"><span data-stu-id="b1c2d-170">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="b1c2d-171">Gebruik-trans actie</span><span class="sxs-lookup"><span data-stu-id="b1c2d-171">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="b1c2d-172">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="b1c2d-172">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="b1c2d-173">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="b1c2d-173">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="b1c2d-174">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="b1c2d-174">New-ItemProperty</span></span>](New-ItemProperty.md)
