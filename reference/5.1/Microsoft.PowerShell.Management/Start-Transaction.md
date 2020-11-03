---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250541"
---
# <span data-ttu-id="78580-103">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="78580-103">Start-Transaction</span></span>

## <span data-ttu-id="78580-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="78580-104">SYNOPSIS</span></span>
<span data-ttu-id="78580-105">Start een trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-105">Starts a transaction.</span></span>

## <span data-ttu-id="78580-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="78580-106">SYNTAX</span></span>

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="78580-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="78580-107">DESCRIPTION</span></span>
<span data-ttu-id="78580-108">Met de cmdlet **Start-trans actie** wordt een trans actie gestart. Dit is een reeks opdrachten die als een eenheid worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="78580-108">The **Start-Transaction** cmdlet starts a transaction, which is a series of commands that are managed as a unit.</span></span>
<span data-ttu-id="78580-109">Een trans actie kan worden voltooid of worden doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-109">A transaction can be completed, or committed.</span></span>
<span data-ttu-id="78580-110">Het kan ook volledig ongedaan worden gemaakt of teruggedraaid, zodat alle gegevens die door de trans actie worden gewijzigd naar de oorspronkelijke status worden teruggezet.</span><span class="sxs-lookup"><span data-stu-id="78580-110">Alternatively, it can be completely undone, or rolled back, so that any data changed by the transaction is restored to its original state.</span></span>
<span data-ttu-id="78580-111">Omdat de opdrachten in een trans actie als eenheid worden beheerd, worden alle opdrachten vastgelegd of worden alle opdrachten teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="78580-111">Because the commands in a transaction are managed as a unit, either all commands are committed or all commands are rolled back.</span></span>

<span data-ttu-id="78580-112">Standaard worden trans acties automatisch teruggedraaid als een opdracht in de trans actie een fout genereert.</span><span class="sxs-lookup"><span data-stu-id="78580-112">By default, if any command in the transaction generates an error, transactions are rolled back automatically.</span></span>
<span data-ttu-id="78580-113">U kunt de para meter *RollbackPreference* gebruiken om dit gedrag te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="78580-113">You can use the *RollbackPreference* parameter to change this behavior.</span></span>

<span data-ttu-id="78580-114">De cmdlets die in een trans actie worden gebruikt, moeten zijn ontworpen ter ondersteuning van trans acties.</span><span class="sxs-lookup"><span data-stu-id="78580-114">The cmdlets used in a transaction must be designed to support transactions.</span></span>
<span data-ttu-id="78580-115">Cmdlets die trans acties ondersteunen, hebben een *UseTransaction* -para meter.</span><span class="sxs-lookup"><span data-stu-id="78580-115">Cmdlets that support transactions have a *UseTransaction* parameter.</span></span>
<span data-ttu-id="78580-116">Voor het uitvoeren van trans acties in een provider moet de provider trans acties ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="78580-116">To perform transactions in a provider, the provider must support transactions.</span></span>
<span data-ttu-id="78580-117">De Windows Power shell-register provider in Windows Vista en latere versies van het Windows-besturings systeem ondersteunt trans acties.</span><span class="sxs-lookup"><span data-stu-id="78580-117">The Windows PowerShell Registry provider in Windows Vista and later versions of the Windows operating system supports transactions.</span></span>
<span data-ttu-id="78580-118">U kunt ook de klasse **micro soft. Power shell. commands. Management. TransactedString** gebruiken om expressies op te genomen in trans acties op elke versie van het Windows-systeem dat Windows Power shell ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="78580-118">You can also use the **Microsoft.PowerShell.Commands.Management.TransactedString** class to include expressions in transactions on any version of the Windows system that supports Windows PowerShell.</span></span>
<span data-ttu-id="78580-119">Andere Windows Power shell-providers kunnen ook trans acties ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="78580-119">Other Windows PowerShell providers can also support transactions.</span></span>

<span data-ttu-id="78580-120">Er kan slechts één trans actie tegelijk actief zijn.</span><span class="sxs-lookup"><span data-stu-id="78580-120">Only one transaction can be active at a time.</span></span>
<span data-ttu-id="78580-121">Als u een nieuwe, onafhankelijke trans actie start terwijl een trans actie wordt uitgevoerd, wordt de nieuwe trans actie de actieve trans actie en moet u de nieuwe trans actie door voeren of terugdraaien voordat u wijzigingen aanbrengt in de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-121">If you start a new, independent transaction while a transaction is in progress, the new transaction becomes the active transaction, and you must commit or roll back the new transaction before you make any changes to the original transaction.</span></span>

<span data-ttu-id="78580-122">De cmdlet **Start-Trans Action** is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="78580-122">**Start-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="78580-123">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="78580-123">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="78580-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="78580-124">EXAMPLES</span></span>

### <span data-ttu-id="78580-125">Voor beeld 1: een trans actie starten en terugdraaien</span><span class="sxs-lookup"><span data-stu-id="78580-125">Example 1: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

<span data-ttu-id="78580-126">Deze opdrachten worden gestart en de trans actie wordt teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="78580-126">These commands start and then roll back a transaction.</span></span>
<span data-ttu-id="78580-127">Omdat de trans actie ongedaan wordt gemaakt, worden er geen wijzigingen in het REGI ster aangebracht.</span><span class="sxs-lookup"><span data-stu-id="78580-127">Because the transaction is rolled back, no changes are made to the registry.</span></span>

### <span data-ttu-id="78580-128">Voor beeld 2: een trans actie starten en volt ooien</span><span class="sxs-lookup"><span data-stu-id="78580-128">Example 2: Start and complete a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="78580-129">Deze opdrachten beginnen en volt ooien een trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-129">These commands start and then complete a transaction.</span></span>
<span data-ttu-id="78580-130">Er worden geen wijzigingen aangebracht in het REGI ster tot de opdracht **volt ooien-trans actie** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="78580-130">No changes are made to the registry until the **Complete-Transaction** command is used.</span></span>

### <span data-ttu-id="78580-131">Voor beeld 3: verschillende terugdraai voorkeuren gebruiken</span><span class="sxs-lookup"><span data-stu-id="78580-131">Example 3: Use different rollback preferences</span></span>

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

<span data-ttu-id="78580-132">Dit voor beeld toont het effect van het wijzigen van de waarde van de para meter *RollbackPreference* .</span><span class="sxs-lookup"><span data-stu-id="78580-132">This example demonstrates the effect of changing the *RollbackPreference* parameter value.</span></span>

<span data-ttu-id="78580-133">In de eerste set met opdrachten maakt **Start-trans actie** geen gebruik van *RollbackPreference*.</span><span class="sxs-lookup"><span data-stu-id="78580-133">In the first set of commands, **Start-Transaction** does not use *RollbackPreference*.</span></span>
<span data-ttu-id="78580-134">Als gevolg hiervan wordt de standaard waarde (fout) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="78580-134">As a result, the default value (Error) is used.</span></span>
<span data-ttu-id="78580-135">Als er een fout optreedt in een trans actie-opdracht, dat wil zeggen dat het opgegeven pad niet bestaat, wordt de trans actie automatisch teruggezet.</span><span class="sxs-lookup"><span data-stu-id="78580-135">When an error occurs in a transaction command, that is, the specified path does not exist, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="78580-136">In de tweede set opdrachten maakt **Start-trans actie** gebruik van *RollbackPreference* met de waarde nooit.</span><span class="sxs-lookup"><span data-stu-id="78580-136">In the second set of commands, **Start-Transaction** uses *RollbackPreference* with a value of Never.</span></span>
<span data-ttu-id="78580-137">Als er een fout optreedt in een trans actie-opdracht, is de trans actie dus nog actief en kan deze worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="78580-137">As a result, when an error occurs in a transaction command, the transaction is still active and can be completed successfully.</span></span>

<span data-ttu-id="78580-138">Omdat de meeste trans acties zonder fouten moeten worden uitgevoerd, is de standaard waarde van *RollbackPreference* doorgaans de voor keur.</span><span class="sxs-lookup"><span data-stu-id="78580-138">Because most transactions must be performed without error, the default value of *RollbackPreference* is typically preferred.</span></span>

### <span data-ttu-id="78580-139">Voor beeld 4: deze cmdlet gebruiken terwijl een trans actie wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="78580-139">Example 4: Use this cmdlet while a transaction is in progress</span></span>

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="78580-140">Dit voor beeld toont het effect van het gebruik van **Start-trans actie** terwijl een trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-140">This example shows the effect of using **Start-Transaction** while a transaction is in progress.</span></span>
<span data-ttu-id="78580-141">Het effect is vergelijkbaar met het samen voegen van de trans actie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-141">The effect is much like joining the transaction in progress.</span></span>

<span data-ttu-id="78580-142">Hoewel dit een vereenvoudigde opdracht is, treedt dit scenario vaak op wanneer de trans actie een script uitvoert dat een volledige trans actie bevat.</span><span class="sxs-lookup"><span data-stu-id="78580-142">Although this is a simplified command, this scenario frequently occurs when the transaction involves running a script that includes a complete transaction.</span></span>

<span data-ttu-id="78580-143">Met de eerste **Start-trans actie** opdracht wordt de trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="78580-143">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="78580-144">De eerste opdracht **Nieuw item** maakt deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-144">The first **New-Item** command is part of the transaction.</span></span>

<span data-ttu-id="78580-145">Met de tweede **Start-trans actie** opdracht wordt een nieuwe abonnee toegevoegd aan de trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-145">The second **Start-Transaction** command adds a new subscriber to the transaction.</span></span>
<span data-ttu-id="78580-146">De opdracht **Get-trans actie** retourneert nu een trans actie met het aantal abonnee 2.</span><span class="sxs-lookup"><span data-stu-id="78580-146">The **Get-Transaction** command now returns a transaction with a subscriber count of 2.</span></span>
<span data-ttu-id="78580-147">De tweede opdracht **Nieuw item** maakt deel uit van dezelfde trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-147">The second **New-Item** command is part of the same transaction.</span></span>

<span data-ttu-id="78580-148">Er worden geen wijzigingen aangebracht in het REGI ster tot de hele trans actie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="78580-148">No changes are made to the registry until the whole transaction is completed.</span></span>
<span data-ttu-id="78580-149">Als u de trans actie wilt volt ooien, moet u twee opdrachten voor **volt ooien van trans acties** invoeren, één voor elke abonnee.</span><span class="sxs-lookup"><span data-stu-id="78580-149">To complete the transaction, you must enter two **Complete-Transaction** commands, one for each subscriber.</span></span>
<span data-ttu-id="78580-150">Als u de trans actie op elk gewenst moment terugdraait, wordt de trans actie teruggedraaid voor beide abonnees.</span><span class="sxs-lookup"><span data-stu-id="78580-150">If you were to roll back the transaction at any point, all the transaction would be rolled back for both subscribers.</span></span>

### <span data-ttu-id="78580-151">Voor beeld 5: een onafhankelijke trans actie starten terwijl er een wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="78580-151">Example 5: Start an independent transaction while one is in progress</span></span>

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

<span data-ttu-id="78580-152">Dit voor beeld toont het effect van het gebruik van de *onafhankelijke* para meter van de **Start-trans actie** om een trans actie te starten terwijl een andere trans actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-152">This example shows the effect of using the *Independent* parameter of **Start-Transaction** to start a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="78580-153">In dit geval wordt de nieuwe trans actie teruggedraaid zonder dat dit van invloed is op de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-153">In this case, the new transaction is rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="78580-154">Hoewel de trans acties logisch onafhankelijk zijn, omdat er slechts één trans actie tegelijk actief kan zijn, moet u de nieuwste trans actie terugdraaien of door voeren voordat u de oorspronkelijke trans actie opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="78580-154">Although the transactions are logically independent, because only one transaction can be active at a time, you must roll back or commit the newest transaction before resuming work on the original transaction.</span></span>

<span data-ttu-id="78580-155">Met de eerste set opdrachten wordt een trans actie gestart.</span><span class="sxs-lookup"><span data-stu-id="78580-155">The first set of commands starts a transaction.</span></span>
<span data-ttu-id="78580-156">De opdracht **Nieuw item** maakt deel uit van de eerste trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-156">The **New-Item** command is part of the first transaction.</span></span>

<span data-ttu-id="78580-157">In de tweede set met opdrachten maakt de **Start-trans actie** opdracht gebruik van de *onafhankelijke* para meter.</span><span class="sxs-lookup"><span data-stu-id="78580-157">In the second set of commands, the **Start-Transaction** command uses the *Independent* parameter.</span></span>
<span data-ttu-id="78580-158">Met de opdracht **Get-trans actie** die volgt, wordt het transactie object voor de actieve trans actie weer gegeven. Dit is de nieuwste.</span><span class="sxs-lookup"><span data-stu-id="78580-158">The **Get-Transaction** command that follows shows the transaction object for the active transaction, which is the newest one.</span></span>
<span data-ttu-id="78580-159">Het aantal abonnees is gelijk aan 1, waarmee wordt aangegeven dat de trans acties niet gerelateerd zijn.</span><span class="sxs-lookup"><span data-stu-id="78580-159">The subscriber count is equal to 1, that shows that the transactions are unrelated.</span></span>

<span data-ttu-id="78580-160">Wanneer de actieve trans actie wordt teruggedraaid met een opdracht voor **ongedaan maken** van de trans actie, wordt de oorspronkelijke trans actie weer actief.</span><span class="sxs-lookup"><span data-stu-id="78580-160">When the active transaction is rolled back by using an **Undo-Transaction** command, the original transaction becomes active again.</span></span>

<span data-ttu-id="78580-161">De opdracht **Nieuw-item Property** , die deel uitmaakt van de oorspronkelijke trans actie, eindigt zonder fout en de oorspronkelijke trans actie kan worden voltooid met behulp van de opdracht **volt ooien trans actie** .</span><span class="sxs-lookup"><span data-stu-id="78580-161">The **New-ItemProperty** command, which is part of the original transaction, finishes without error, and the original transaction can be completed by using the **Complete-Transaction** command.</span></span>
<span data-ttu-id="78580-162">Als gevolg hiervan wordt het REGI ster gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="78580-162">As a result, the registry is changed.</span></span>

### <span data-ttu-id="78580-163">Voor beeld 6: opdrachten uitvoeren die geen deel uitmaken van een trans actie</span><span class="sxs-lookup"><span data-stu-id="78580-163">Example 6: Run commands that are not part of a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

<span data-ttu-id="78580-164">In dit voor beeld ziet u dat opdrachten die worden verzonden terwijl een trans actie wordt uitgevoerd, kunnen worden opgenomen in de trans actie of niet worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="78580-164">This example demonstrates that commands that are submitted while a transaction is in progress can be included in the transaction or not included.</span></span>
<span data-ttu-id="78580-165">Alleen opdrachten die gebruikmaken van de para meter *UseTransaction* , maken deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-165">Only commands that use the *UseTransaction* parameter are part of the transaction.</span></span>

<span data-ttu-id="78580-166">De eerste en derde opdracht voor **nieuwe items** gebruiken de para meter *UseTransaction* .</span><span class="sxs-lookup"><span data-stu-id="78580-166">The first and third **New-Item** commands use the *UseTransaction* parameter.</span></span>
<span data-ttu-id="78580-167">Deze opdrachten maken deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-167">These commands are part of the transaction.</span></span>
<span data-ttu-id="78580-168">Omdat de tweede opdracht **Nieuw item** geen gebruikmaakt van de para meter *UseTransaction* , maakt deze geen deel uit van de trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-168">Because the second **New-Item** command does not use the *UseTransaction* parameter, it is not part of the transaction.</span></span>

<span data-ttu-id="78580-169">Met de eerste opdracht dir wordt het effect weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="78580-169">The first dir command shows the effect.</span></span>
<span data-ttu-id="78580-170">De tweede opdracht **Nieuw item** wordt onmiddellijk voltooid, maar de eerste en derde opdrachten voor **Nieuw item** zijn pas van kracht als de trans actie is doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-170">The second **New-Item** command is completed immediately, but the first and third **New-Item** commands are not effective until the transaction is committed.</span></span>

<span data-ttu-id="78580-171">Met de opdracht **volt ooien-trans actie** wordt de trans actie doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-171">The **Complete-Transaction** command commits the transaction.</span></span>
<span data-ttu-id="78580-172">Als gevolg hiervan wordt met de tweede opdracht dir aangegeven dat alle nieuwe items aan het REGI ster worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="78580-172">As a result, the second dir command shows that all of the new items are added to the registry.</span></span>

### <span data-ttu-id="78580-173">Voor beeld 7: terugdraaien van een trans actie die niet binnen een opgegeven tijd eindigt</span><span class="sxs-lookup"><span data-stu-id="78580-173">Example 7: Roll back a transaction that does not finish in a specified time</span></span>

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

<span data-ttu-id="78580-174">Met deze opdracht wordt de para meter *time-out* van de **Start-trans actie** gebruikt om een trans actie te starten die binnen twee minuten moet worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="78580-174">This command uses the *Timeout* parameter of **Start-Transaction** to start a transaction that must be completed within two minutes.</span></span>
<span data-ttu-id="78580-175">Als de trans actie niet is voltooid wanneer de time-outperiode is verlopen, wordt deze automatisch teruggezet.</span><span class="sxs-lookup"><span data-stu-id="78580-175">If the transaction is not finished when the time-out expires, it is rolled back automatically.</span></span>

<span data-ttu-id="78580-176">Wanneer de time-out is verlopen, wordt u niet gewaarschuwd, maar de eigenschap **status** van het transactie object wordt ingesteld op teruggedraaid en opdrachten die de para meter *UseTransaction* gebruiken mislukken.</span><span class="sxs-lookup"><span data-stu-id="78580-176">When the time-out expires, you are not notified, but the **Status** property of the transaction object is set to RolledBack and commands that use the *UseTransaction* parameter fail.</span></span>

## <span data-ttu-id="78580-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="78580-177">PARAMETERS</span></span>

### <span data-ttu-id="78580-178">-Onafhankelijk</span><span class="sxs-lookup"><span data-stu-id="78580-178">-Independent</span></span>
<span data-ttu-id="78580-179">Geeft aan dat deze cmdlet een trans actie start die onafhankelijk is van trans acties die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-179">Indicates that this cmdlet starts a transaction that is independent of any transactions in progress.</span></span>
<span data-ttu-id="78580-180">Als u **Start-trans actie** gebruikt terwijl er een andere trans actie wordt uitgevoerd, wordt standaard een nieuwe abonnee toegevoegd aan de trans actie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-180">By default, if you use **Start-Transaction** while another transaction is in progress, a new subscriber is added to the transaction in progress.</span></span>
<span data-ttu-id="78580-181">Deze para meter heeft alleen effect wanneer er al een trans actie in de sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-181">This parameter has an effect only when a transaction is already in progress in the session.</span></span>

<span data-ttu-id="78580-182">Als u **Start-trans actie** gebruikt terwijl een trans actie wordt uitgevoerd, wordt standaard het bestaande transactie object opnieuw gebruikt en wordt het aantal abonnees verhoogd.</span><span class="sxs-lookup"><span data-stu-id="78580-182">By default, if you use **Start-Transaction** while a transaction is in progress, the existing transaction object is reused and the subscriber count is incremented.</span></span>
<span data-ttu-id="78580-183">Het effect is vergelijkbaar met het samen voegen van de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-183">The effect is much like joining the original transaction.</span></span>
<span data-ttu-id="78580-184">Met een Undo-Transaction-opdracht wordt de hele trans actie teruggedraaid.</span><span class="sxs-lookup"><span data-stu-id="78580-184">An Undo-Transaction command rolls back the whole the transaction.</span></span>
<span data-ttu-id="78580-185">Als u de trans actie wilt volt ooien, moet u een Complete-Transaction-opdracht voor elke abonnee opgeven.</span><span class="sxs-lookup"><span data-stu-id="78580-185">To complete the transaction, you must enter a Complete-Transaction command for each subscriber.</span></span>
<span data-ttu-id="78580-186">Omdat de meeste trans acties die op hetzelfde moment worden uitgevoerd, aan elkaar zijn gerelateerd, is de standaard waarde voldoende voor het meest gebruik.</span><span class="sxs-lookup"><span data-stu-id="78580-186">Because most transactions that are in progress at the same time are related, the default is sufficient for most uses.</span></span>

<span data-ttu-id="78580-187">Als u de *onafhankelijke* para meter opgeeft, maakt deze cmdlet een nieuwe trans actie die kan worden voltooid of ongedaan worden gemaakt zonder dat dit van invloed is op de oorspronkelijke trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-187">If you specify the *Independent* parameter, this cmdlet creates a new transaction that can be completed or undone without affecting the original transaction.</span></span>
<span data-ttu-id="78580-188">Omdat echter slechts één trans actie tegelijk actief kan zijn, moet u de nieuwe trans actie volt ooien of terugdraaien voordat u het werk voor de oorspronkelijke trans actie hervat.</span><span class="sxs-lookup"><span data-stu-id="78580-188">However, because only one transaction can be active at a time, you must complete or roll back the new transaction before resuming work on the original transaction.</span></span>

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

### <span data-ttu-id="78580-189">-RollbackPreference</span><span class="sxs-lookup"><span data-stu-id="78580-189">-RollbackPreference</span></span>
<span data-ttu-id="78580-190">Hiermee geeft u de voor waarden voor het automatisch terugdraaien van een trans actie.</span><span class="sxs-lookup"><span data-stu-id="78580-190">Specifies the conditions under which a transaction is automatically rolled back.</span></span>
<span data-ttu-id="78580-191">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="78580-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="78580-192">Fout.</span><span class="sxs-lookup"><span data-stu-id="78580-192">Error.</span></span>
<span data-ttu-id="78580-193">De trans actie wordt automatisch teruggedraaid als er sprake is van een afsluitende of niet-afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="78580-193">The transaction is rolled back automatically if a terminating or non-terminating error occurs.</span></span>
- <span data-ttu-id="78580-194">TerminatingError.</span><span class="sxs-lookup"><span data-stu-id="78580-194">TerminatingError.</span></span>
<span data-ttu-id="78580-195">De trans actie wordt automatisch teruggezet als er een afsluit fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="78580-195">The transaction is rolled back automatically if a terminating error occurs.</span></span>
- <span data-ttu-id="78580-196">Schreven.</span><span class="sxs-lookup"><span data-stu-id="78580-196">Never.</span></span>
<span data-ttu-id="78580-197">De trans actie wordt nooit automatisch hersteld.</span><span class="sxs-lookup"><span data-stu-id="78580-197">The transaction is never rolled back automatically.</span></span>

<span data-ttu-id="78580-198">De standaard waarde is fout.</span><span class="sxs-lookup"><span data-stu-id="78580-198">The default value is Error.</span></span>

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78580-199">-Time-out</span><span class="sxs-lookup"><span data-stu-id="78580-199">-Timeout</span></span>
<span data-ttu-id="78580-200">Hiermee wordt de maximale tijds duur, in minuten, opgegeven dat de trans actie actief is.</span><span class="sxs-lookup"><span data-stu-id="78580-200">Specifies the maximum time, in minutes, that the transaction is active.</span></span>
<span data-ttu-id="78580-201">Wanneer de time-outperiode is verlopen, wordt de trans actie automatisch teruggezet.</span><span class="sxs-lookup"><span data-stu-id="78580-201">When the time-out expires, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="78580-202">Standaard is er geen time-out voor trans acties die worden gestart op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="78580-202">By default, there is no time-out for transactions that are started at the command line.</span></span>
<span data-ttu-id="78580-203">Wanneer trans acties door een script worden gestart, is de standaard time-out 30 minuten.</span><span class="sxs-lookup"><span data-stu-id="78580-203">When transactions are started by a script, the default time-out is 30 minutes.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78580-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="78580-204">-Confirm</span></span>
<span data-ttu-id="78580-205">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="78580-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="78580-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="78580-206">-WhatIf</span></span>
<span data-ttu-id="78580-207">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="78580-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="78580-208">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78580-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="78580-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78580-209">CommonParameters</span></span>
<span data-ttu-id="78580-210">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="78580-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78580-211">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="78580-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78580-212">INVOER</span><span class="sxs-lookup"><span data-stu-id="78580-212">INPUTS</span></span>

### <span data-ttu-id="78580-213">Geen</span><span class="sxs-lookup"><span data-stu-id="78580-213">None</span></span>
<span data-ttu-id="78580-214">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78580-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="78580-215">UITVOER</span><span class="sxs-lookup"><span data-stu-id="78580-215">OUTPUTS</span></span>

### <span data-ttu-id="78580-216">Geen</span><span class="sxs-lookup"><span data-stu-id="78580-216">None</span></span>
<span data-ttu-id="78580-217">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="78580-217">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="78580-218">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="78580-218">NOTES</span></span>

## <span data-ttu-id="78580-219">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="78580-219">RELATED LINKS</span></span>

[<span data-ttu-id="78580-220">Volt ooien-trans actie</span><span class="sxs-lookup"><span data-stu-id="78580-220">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="78580-221">Get-trans actie</span><span class="sxs-lookup"><span data-stu-id="78580-221">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="78580-222">Ongedaan maken-trans actie</span><span class="sxs-lookup"><span data-stu-id="78580-222">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="78580-223">Gebruik-trans actie</span><span class="sxs-lookup"><span data-stu-id="78580-223">Use-Transaction</span></span>](Use-Transaction.md)
