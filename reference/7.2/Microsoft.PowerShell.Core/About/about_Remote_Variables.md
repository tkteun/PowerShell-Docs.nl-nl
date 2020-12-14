---
description: Hierin wordt uitgelegd hoe u lokale en externe variabelen gebruikt in externe opdrachten.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 1cd6d0c4562fcd63fc56f103ec41aa6f0bb4c01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705791"
---
# <a name="about-remote-variables"></a><span data-ttu-id="8d341-103">Over externe variabelen</span><span class="sxs-lookup"><span data-stu-id="8d341-103">About Remote Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="8d341-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="8d341-104">Short description</span></span>

<span data-ttu-id="8d341-105">Hierin wordt uitgelegd hoe u lokale en externe variabelen gebruikt in externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="8d341-105">Explains how to use local and remote variables in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="8d341-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="8d341-106">Long description</span></span>

<span data-ttu-id="8d341-107">U kunt variabelen gebruiken in opdrachten die u uitvoert op externe computers.</span><span class="sxs-lookup"><span data-stu-id="8d341-107">You can use variables in commands that you run on remote computers.</span></span> <span data-ttu-id="8d341-108">Wijs een waarde toe aan de variabele en gebruik vervolgens de variabele in plaats van de waarde.</span><span class="sxs-lookup"><span data-stu-id="8d341-108">Assign a value to the variable and then use the variable in place of the value.</span></span>

<span data-ttu-id="8d341-109">Standaard worden de variabelen in externe opdrachten geacht te zijn gedefinieerd in de sessie die de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8d341-109">By default, the variables in remote commands are assumed to be defined in the session that runs the command.</span></span> <span data-ttu-id="8d341-110">Variabelen die in een lokale sessie worden gedefinieerd, moeten worden aangeduid als lokale variabelen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d341-110">Variables that are defined in a local session, must be identified as local variables in the command.</span></span>

## <a name="using-remote-variables"></a><span data-ttu-id="8d341-111">Externe variabelen gebruiken</span><span class="sxs-lookup"><span data-stu-id="8d341-111">Using remote variables</span></span>

<span data-ttu-id="8d341-112">In Power shell wordt ervan uitgegaan dat de variabelen die worden gebruikt in externe opdrachten worden gedefinieerd in de sessie waarin de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-112">PowerShell assumes that the variables used in remote commands are defined in the session in which the command runs.</span></span>

<span data-ttu-id="8d341-113">In dit voor beeld `$ps` wordt de variabele gedefinieerd in de tijdelijke sessie waarin de `Get-WinEvent` opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-113">In this example, the `$ps` variable is defined in the temporary session in which the `Get-WinEvent` command runs.</span></span>

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

<span data-ttu-id="8d341-114">Wanneer de opdracht wordt uitgevoerd in een permanente sessie, **PSSession**, moet de externe variabele in die sessie worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-114">When the command runs in a persistent session, **PSSession**, the remote variable must be defined in that session.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a><span data-ttu-id="8d341-115">Lokale variabelen gebruiken</span><span class="sxs-lookup"><span data-stu-id="8d341-115">Using local variables</span></span>

<span data-ttu-id="8d341-116">U kunt lokale variabelen gebruiken in externe opdrachten, maar de variabele moet in de lokale sessie worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-116">You can use local variables in remote commands, but the variable must be defined in the local session.</span></span>

<span data-ttu-id="8d341-117">Vanaf Power Shell 3,0 kunt u de `Using` Scope modificator gebruiken om een lokale variabele te identificeren in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d341-117">Beginning in PowerShell 3.0, you can use the `Using` scope modifier to identify a local variable in a remote command.</span></span>

<span data-ttu-id="8d341-118">De syntaxis van `Using` is als volgt:</span><span class="sxs-lookup"><span data-stu-id="8d341-118">The syntax of `Using` is as follows:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="8d341-119">In het volgende voor beeld `$ps` wordt de variabele in de lokale sessie gemaakt, maar wordt deze gebruikt in de sessie waarin de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-119">In the following example, the `$ps` variable is created in the local session, but is used in the session in which the command runs.</span></span> <span data-ttu-id="8d341-120">De `Using` wijzigings functie van het bereik identificeert `$ps` als een lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="8d341-120">The `Using` scope modifier identifies `$ps` as a local variable.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

<span data-ttu-id="8d341-121">De `Using` aanpassings functie voor bereik kan worden gebruikt in een **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="8d341-121">The `Using` scope modifier can be used in a **PSSession**.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

<span data-ttu-id="8d341-122">Een verwijzing naar een variabele, zoals wordt `$using:var` uitgebreid naar de waarde van de variabele `$var` van de context van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="8d341-122">A variable reference such as `$using:var` expands to the value of variable `$var` from the caller's context.</span></span> <span data-ttu-id="8d341-123">U krijgt geen toegang tot het object variable van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="8d341-123">You do not get access to the caller's variable object.</span></span>
<span data-ttu-id="8d341-124">De `Using` aanpassings functie voor bereik kan niet worden gebruikt voor het wijzigen van een lokale variabele in de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="8d341-124">The `Using` scope modifier cannot be used to modify a local variable within the **PSSession**.</span></span> <span data-ttu-id="8d341-125">De volgende code werkt bijvoorbeeld niet:</span><span class="sxs-lookup"><span data-stu-id="8d341-125">For example, the following code does not work:</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

<span data-ttu-id="8d341-126">`Using`Zie [about_Scopes](./about_Scopes.md) voor meer informatie over</span><span class="sxs-lookup"><span data-stu-id="8d341-126">For more information about `Using`, see [about_Scopes](./about_Scopes.md)</span></span>

### <a name="using-splatting"></a><span data-ttu-id="8d341-127">Splatting gebruiken</span><span class="sxs-lookup"><span data-stu-id="8d341-127">Using splatting</span></span>

<span data-ttu-id="8d341-128">Power shell splatting geeft een verzameling parameter namen en waarden door aan een opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d341-128">PowerShell splatting passes a collection of parameter names and values to a command.</span></span> <span data-ttu-id="8d341-129">Zie [about_Splatting](about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8d341-129">For more information, see [about_Splatting](about_Splatting.md).</span></span>

<span data-ttu-id="8d341-130">In dit voor beeld is de variabele splatting `$Splat` een hash-tabel die is ingesteld op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="8d341-130">In this example, the splatting variable, `$Splat` is a hash table that is set up on the local computer.</span></span> <span data-ttu-id="8d341-131">De `Invoke-Command` verbinding met een externe computer sessie maken.</span><span class="sxs-lookup"><span data-stu-id="8d341-131">The `Invoke-Command` connects to a remote computer session.</span></span> <span data-ttu-id="8d341-132">De **script Block** gebruikt de `Using` aanpassings functie van het bereik met het symbool at ( `@` ) om de splatted-variabele weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8d341-132">The **ScriptBlock** uses the `Using` scope modifier with the At (`@`) symbol to represent the splatted variable.</span></span>

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a><span data-ttu-id="8d341-133">Andere situaties waarin de aanpassings functie voor het gebruik van het bereik is vereist</span><span class="sxs-lookup"><span data-stu-id="8d341-133">Other situations where the 'Using' scope modifier is needed</span></span>

<span data-ttu-id="8d341-134">Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="8d341-134">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="8d341-135">De `Using` aanpassing van het bereik wordt ondersteund in de volgende contexten:</span><span class="sxs-lookup"><span data-stu-id="8d341-135">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="8d341-136">Extern uitgevoerde opdrachten, begonnen met `Invoke-Command` het gebruik van **ComputerName**, **hostname**, **SSHConnection** of **Session** para meters (externe sessie)</span><span class="sxs-lookup"><span data-stu-id="8d341-136">Remotely executed commands, started with `Invoke-Command` using the **ComputerName**, **HostName**, **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="8d341-137">Achtergrond taken, begonnen met `Start-Job` (out-of-process-sessie)</span><span class="sxs-lookup"><span data-stu-id="8d341-137">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="8d341-138">Thread taken, gestart via `Start-ThreadJob` of `ForEach-Object -Parallel` (afzonderlijke thread sessie)</span><span class="sxs-lookup"><span data-stu-id="8d341-138">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="8d341-139">Afhankelijk van de context, zijn Inge sloten variabelen waarden ofwel onafhankelijke kopieën van de gegevens in het bereik of verwijzingen naar de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="8d341-139">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="8d341-140">In externe en out-of-process-sessies zijn ze altijd onafhankelijke kopieën.</span><span class="sxs-lookup"><span data-stu-id="8d341-140">In remote and out-of-process sessions, they are always independent copies.</span></span> <span data-ttu-id="8d341-141">In thread sessies worden ze door gegeven door verwijzing.</span><span class="sxs-lookup"><span data-stu-id="8d341-141">In thread sessions, they are passed by reference.</span></span>

## <a name="serialization-of-variable-values"></a><span data-ttu-id="8d341-142">Serialisatie van variabele waarden</span><span class="sxs-lookup"><span data-stu-id="8d341-142">Serialization of variable values</span></span>

<span data-ttu-id="8d341-143">Extern uitgevoerde opdrachten en achtergrond taken worden out-of-process uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-143">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="8d341-144">Out-of-process-sessies gebruiken op XML gebaseerde serialisatie en deserialisatie om de waarden van variabelen beschikbaar te maken voor de grenzen van het proces.</span><span class="sxs-lookup"><span data-stu-id="8d341-144">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="8d341-145">Het serialization-proces converteert objecten naar een **PSObject** die de eigenschappen van de oorspronkelijke objecten bevat, maar niet de methoden ervan.</span><span class="sxs-lookup"><span data-stu-id="8d341-145">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="8d341-146">Voor een beperkte set typen worden objecten door deserialisatie opnieuw naar het oorspronkelijke type gehydrateerd.</span><span class="sxs-lookup"><span data-stu-id="8d341-146">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="8d341-147">Het opnieuw gehydrateerde object is een kopie van het oorspronkelijke object exemplaar.</span><span class="sxs-lookup"><span data-stu-id="8d341-147">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="8d341-148">Deze bevat de type-eigenschappen en-methoden.</span><span class="sxs-lookup"><span data-stu-id="8d341-148">It has the type properties and methods.</span></span> <span data-ttu-id="8d341-149">Voor eenvoudige typen, zoals **System. versie**, is de kopie gelijk.</span><span class="sxs-lookup"><span data-stu-id="8d341-149">For simple types, such as **System.Version**, the copy is exact.</span></span> <span data-ttu-id="8d341-150">Voor complexe typen is de kopie niet perfect.</span><span class="sxs-lookup"><span data-stu-id="8d341-150">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="8d341-151">Bijvoorbeeld: opnieuw gehydrateerde certificaat objecten bevatten niet de persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="8d341-151">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="8d341-152">Exemplaren van alle andere typen zijn **PSObject** -exemplaren.</span><span class="sxs-lookup"><span data-stu-id="8d341-152">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="8d341-153">De eigenschap **PSTypeNames** bevat de oorspronkelijke type naam, voorafgegaan door een **gedeserialiseerd**, bijvoorbeeld **Deserialized.System. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="8d341-153">The **PSTypeNames** property contains the original type name prefixed with **Deserialized**, for example, **Deserialized.System.Data.DataTable**</span></span>

## <a name="using-local-variables-with-argumentlist-parameter"></a><span data-ttu-id="8d341-154">Lokale variabelen gebruiken met de para meter **argument List**</span><span class="sxs-lookup"><span data-stu-id="8d341-154">Using local variables with **ArgumentList** parameter</span></span>

<span data-ttu-id="8d341-155">U kunt lokale variabelen gebruiken in een externe opdracht door para meters voor de externe opdracht te definiëren en de para meter **argument List** van de `Invoke-Command` cmdlet te gebruiken om de lokale variabele als de parameter waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="8d341-155">You can use local variables in a remote command by defining parameters for the remote command and using the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

- <span data-ttu-id="8d341-156">Gebruik het `param` sleutel woord om para meters te definiëren voor de externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d341-156">Use the `param` keyword to define parameters for the remote command.</span></span> <span data-ttu-id="8d341-157">De parameter namen zijn tijdelijke aanduidingen die niet moeten overeenkomen met de naam van de lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="8d341-157">The parameter names are placeholders that don't need to match the local variable's name.</span></span>

- <span data-ttu-id="8d341-158">Gebruik de para meters die zijn gedefinieerd door het `param` sleutel woord in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d341-158">Use the parameters defined by the `param` keyword in the command.</span></span>

- <span data-ttu-id="8d341-159">Gebruik de para meter **argument List** van de `Invoke-Command` cmdlet om de lokale variabele op te geven als de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="8d341-159">Use the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

<span data-ttu-id="8d341-160">De volgende opdrachten definiëren bijvoorbeeld de `$ps` variabele in de lokale sessie en gebruiken deze vervolgens in een externe opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d341-160">For example, the following commands define the `$ps` variable in the local session and then use it in a remote command.</span></span> <span data-ttu-id="8d341-161">De opdracht wordt gebruikt `$log` als de parameter naam en de lokale variabele, `$ps` als waarde.</span><span class="sxs-lookup"><span data-stu-id="8d341-161">The command uses `$log` as the parameter name and the local variable, `$ps`, as its value.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a><span data-ttu-id="8d341-162">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8d341-162">See also</span></span>

[<span data-ttu-id="8d341-163">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8d341-163">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="8d341-164">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8d341-164">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="8d341-165">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="8d341-165">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="8d341-166">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="8d341-166">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="8d341-167">about_Variables</span><span class="sxs-lookup"><span data-stu-id="8d341-167">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="8d341-168">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="8d341-168">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="8d341-169">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="8d341-169">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="8d341-170">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8d341-170">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="8d341-171">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="8d341-171">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

@Microsoft.PowerShell.Core.ForEach-Object

