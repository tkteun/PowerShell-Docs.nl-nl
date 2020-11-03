---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: f8575c97c4279f285598e2b1bdf94786d92c841a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251155"
---
# <span data-ttu-id="33c92-103">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="33c92-103">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="33c92-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="33c92-104">SYNOPSIS</span></span>
<span data-ttu-id="33c92-105">Hiermee stelt u het Power shell-uitvoerings beleid voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="33c92-105">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="33c92-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="33c92-106">SYNTAX</span></span>

### <span data-ttu-id="33c92-107">Alles</span><span class="sxs-lookup"><span data-stu-id="33c92-107">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="33c92-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="33c92-108">DESCRIPTION</span></span>

<span data-ttu-id="33c92-109">De `Set-ExecutionPolicy` cmdlet wijzigt het Power shell-uitvoerings beleid voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="33c92-109">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="33c92-110">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="33c92-110">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="33c92-111">Vanaf Power shell 6,0 voor niet-Windows-computers is het standaard uitvoerings beleid **onbeperkt** en kan het niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="33c92-111">Beginning in PowerShell 6.0 for non-Windows computers, the default execution policy is **Unrestricted** and can't be changed.</span></span> <span data-ttu-id="33c92-112">De `Set-ExecutionPolicy` cmdlet is beschikbaar, maar in Power shell wordt een console bericht weer gegeven dat niet wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="33c92-112">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span>

<span data-ttu-id="33c92-113">Een uitvoerings beleid maakt deel uit van de Power shell-beveiligings strategie.</span><span class="sxs-lookup"><span data-stu-id="33c92-113">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="33c92-114">Uitvoerings beleid bepaalt of u configuratie bestanden kunt laden, zoals uw Power shell-profiel, of scripts moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="33c92-114">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="33c92-115">En, of scripts digitaal moeten worden ondertekend voordat ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="33c92-115">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="33c92-116">Het `Set-ExecutionPolicy` standaard bereik van de cmdlet is **LocalMachine** , wat van invloed is op iedereen die de computer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="33c92-116">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine** , which affects everyone who uses the computer.</span></span> <span data-ttu-id="33c92-117">Als u het uitvoerings beleid voor **LocalMachine** wilt wijzigen, start u Power shell met **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="33c92-117">To change the execution policy for **LocalMachine** , start PowerShell with **Run as Administrator**.</span></span>

<span data-ttu-id="33c92-118">Gebruik om het uitvoerings beleid voor elk bereik weer te geven in de volg orde van prioriteit `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="33c92-118">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="33c92-119">Om het effectief uitvoerings beleid voor uw Power shell-sessie gebruik `Get-ExecutionPolicy` zonder para meters te bekijken.</span><span class="sxs-lookup"><span data-stu-id="33c92-119">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="33c92-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="33c92-120">EXAMPLES</span></span>

### <span data-ttu-id="33c92-121">Voor beeld 1: een uitvoerings beleid instellen</span><span class="sxs-lookup"><span data-stu-id="33c92-121">Example 1: Set an execution policy</span></span>

<span data-ttu-id="33c92-122">In dit voor beeld ziet u hoe u het uitvoerings beleid voor de lokale computer instelt.</span><span class="sxs-lookup"><span data-stu-id="33c92-122">This example shows how to set the execution policy for the local computer.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="33c92-123">De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **RemoteSigned** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-123">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="33c92-124">De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="33c92-124">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="33c92-125">Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="33c92-125">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="33c92-126">Voor beeld 2: een uitvoerings beleid instellen dat in conflict is met een groepsbeleid</span><span class="sxs-lookup"><span data-stu-id="33c92-126">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="33c92-127">Met deze opdracht wordt geprobeerd het uitvoerings beleid van het **LocalMachine** -bereik in te stellen op **beperkt**.</span><span class="sxs-lookup"><span data-stu-id="33c92-127">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted**.</span></span>
<span data-ttu-id="33c92-128">**LocalMachine** is beperkter, maar is niet het effectief beleid omdat het een conflict veroorzaakt met een Groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="33c92-128">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="33c92-129">Het **beperkte** beleid wordt geschreven naar de register component **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="33c92-129">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

<span data-ttu-id="33c92-130">De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **beperkte** beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-130">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="33c92-131">De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="33c92-131">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span>
<span data-ttu-id="33c92-132">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** met de **HKLM** -provider om de register locatie op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-132">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="33c92-133">Voor beeld 3: het uitvoerings beleid van een externe computer Toep assen op een lokale computer</span><span class="sxs-lookup"><span data-stu-id="33c92-133">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="33c92-134">Met deze opdracht wordt het uitvoerings beleid-object opgehaald van een externe computer en wordt het beleid ingesteld op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="33c92-134">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="33c92-135">`Get-ExecutionPolicy` Hiermee verzendt u een **Microsoft.PowerShell.ExecutionPolicy** -object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="33c92-135">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="33c92-136">`Set-ExecutionPolicy` de invoer van de pijp lijn wordt geaccepteerd en de para meter **ExecutionPolicy** is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="33c92-136">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="33c92-137">De `Invoke-Command` cmdlet wordt uitgevoerd op de lokale computer en verzendt de **script Block** naar de externe computer.</span><span class="sxs-lookup"><span data-stu-id="33c92-137">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="33c92-138">De para meter **ComputerName** specificeert de externe computer, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="33c92-138">The **ComputerName** parameter specifies the remote computer, **Server01**.</span></span> <span data-ttu-id="33c92-139">De para meter **script Block** wordt uitgevoerd `Get-ExecutionPolicy` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="33c92-139">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="33c92-140">Het `Get-ExecutionPolicy` object wordt naar beneden verzonden in de pijp lijn `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="33c92-140">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="33c92-141">`Set-ExecutionPolicy` Hiermee wordt het uitvoerings beleid toegepast op het standaard bereik van de lokale computer, **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="33c92-141">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine**.</span></span>

### <span data-ttu-id="33c92-142">Voor beeld 4: het bereik instellen voor een uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="33c92-142">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="33c92-143">In dit voor beeld ziet u hoe u een uitvoerings beleid instelt voor een opgegeven bereik, **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="33c92-143">This example shows how to set an execution policy for a specified scope, **CurrentUser**.</span></span> <span data-ttu-id="33c92-144">Het bereik van **CurrentUser** is alleen van invloed op de gebruiker die dit bereik instelt.</span><span class="sxs-lookup"><span data-stu-id="33c92-144">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="33c92-145">`Set-ExecutionPolicy` maakt gebruik van de para meter **ExecutionPolicy** om het **Alles ondertekend** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-145">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="33c92-146">De para meter **Scope** geeft de eigenschap **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="33c92-146">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="33c92-147">Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="33c92-147">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="33c92-148">Het effectief uitvoerings beleid voor de gebruiker wordt **Alles ondertekend**.</span><span class="sxs-lookup"><span data-stu-id="33c92-148">The effective execution policy for the user becomes **AllSigned**.</span></span>

### <span data-ttu-id="33c92-149">Voor beeld 5: het uitvoerings beleid voor de huidige gebruiker verwijderen</span><span class="sxs-lookup"><span data-stu-id="33c92-149">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="33c92-150">Dit voor beeld laat zien hoe u het niet- **gedefinieerde** uitvoerings beleid gebruikt voor het verwijderen van een uitvoerings beleid voor een opgegeven bereik.</span><span class="sxs-lookup"><span data-stu-id="33c92-150">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

<span data-ttu-id="33c92-151">`Set-ExecutionPolicy` maakt gebruik van de para meter **ExecutionPolicy** om het niet- **gedefinieerde** beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-151">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="33c92-152">De para meter **Scope** geeft de eigenschap **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="33c92-152">The **Scope** parameter specifies the **CurrentUser**.</span></span> <span data-ttu-id="33c92-153">Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="33c92-153">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="33c92-154">Voor beeld 6: het uitvoerings beleid voor de huidige Power shell-sessie instellen</span><span class="sxs-lookup"><span data-stu-id="33c92-154">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="33c92-155">Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="33c92-155">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="33c92-156">Het uitvoerings beleid wordt opgeslagen in de omgevings variabele `$env:PSExecutionPolicyPreference` en wordt verwijderd wanneer de sessie wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="33c92-156">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="33c92-157">De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **Alles ondertekend** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-157">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="33c92-158">De **bereik** parameter geeft u het **waardeproces** op.</span><span class="sxs-lookup"><span data-stu-id="33c92-158">The **Scope** parameter specifies the value **Process**.</span></span> <span data-ttu-id="33c92-159">Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="33c92-159">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="33c92-160">Voor beeld 7: een script blok keren om het uit te voeren zonder het uitvoerings beleid te wijzigen</span><span class="sxs-lookup"><span data-stu-id="33c92-160">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="33c92-161">Dit voor beeld laat zien hoe u met het beleid voor het uitvoeren van **RemoteSigned** geen niet-ondertekende scripts kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="33c92-161">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="33c92-162">Een best practice is de code van het script te lezen en te controleren of het veilig is **voordat** u de `Unblock-File` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="33c92-162">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="33c92-163">De `Unblock-File` cmdlet verwijdert scripts zodat ze kunnen worden uitgevoerd, maar het uitvoerings beleid wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="33c92-163">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

<span data-ttu-id="33c92-164">De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **RemoteSigned** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="33c92-164">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="33c92-165">Het beleid wordt ingesteld voor het standaard bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="33c92-165">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="33c92-166">De `Get-ExecutionPolicy` cmdlet geeft aan dat **RemoteSigned** het effectief uitvoerings beleid voor de huidige Power shell-sessie is.</span><span class="sxs-lookup"><span data-stu-id="33c92-166">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="33c92-167">Het **Start-ActivityTracker.ps1** script wordt uitgevoerd vanuit de huidige map.</span><span class="sxs-lookup"><span data-stu-id="33c92-167">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="33c92-168">Het script wordt geblokkeerd door **RemoteSigned** omdat het script geen digitale hand tekening heeft.</span><span class="sxs-lookup"><span data-stu-id="33c92-168">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="33c92-169">Voor dit voor beeld is de code van het script beoordeeld en geverifieerd als veilig om uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="33c92-169">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="33c92-170">De `Unblock-File` cmdlet gebruikt de para meter **Path** om het script uit te blok keren.</span><span class="sxs-lookup"><span data-stu-id="33c92-170">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="33c92-171">Als u wilt controleren of `Unblock-File` het uitvoerings beleid niet is gewijzigd, `Get-ExecutionPolicy` wordt het effectief uitvoerings beleid, **RemoteSigned** , weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="33c92-171">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="33c92-172">Het script **Start-ActivityTracker.ps1** wordt uitgevoerd vanuit de huidige map.</span><span class="sxs-lookup"><span data-stu-id="33c92-172">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="33c92-173">Het script wordt uitgevoerd, omdat het is gedeblokkeerd door de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33c92-173">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="33c92-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="33c92-174">PARAMETERS</span></span>

### <span data-ttu-id="33c92-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="33c92-175">-Confirm</span></span>

<span data-ttu-id="33c92-176">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="33c92-176">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="33c92-177">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="33c92-177">-ExecutionPolicy</span></span>

<span data-ttu-id="33c92-178">Hiermee geeft u het uitvoerings beleid op.</span><span class="sxs-lookup"><span data-stu-id="33c92-178">Specifies the execution policy.</span></span> <span data-ttu-id="33c92-179">Als er geen groeps beleid is en het uitvoerings beleid van elke scope is ingesteld op niet **gedefinieerd** , wordt het **beperkte** beleid voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="33c92-179">If there are no Group Policies and each scope's execution policy is set to **Undefined** , then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="33c92-180">De acceptabele waarden voor het uitvoerings beleid zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="33c92-180">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="33c92-181">**Alles ondertekend**.</span><span class="sxs-lookup"><span data-stu-id="33c92-181">**AllSigned**.</span></span> <span data-ttu-id="33c92-182">Vereist dat alle scripts en configuratie bestanden zijn ondertekend door een vertrouwde uitgever, met inbegrip van scripts die op de lokale computer zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="33c92-182">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="33c92-183">**Overs Laan**.</span><span class="sxs-lookup"><span data-stu-id="33c92-183">**Bypass**.</span></span> <span data-ttu-id="33c92-184">Er is niets geblokkeerd en er zijn geen waarschuwingen of prompts.</span><span class="sxs-lookup"><span data-stu-id="33c92-184">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="33c92-185">**Standaard instelling**.</span><span class="sxs-lookup"><span data-stu-id="33c92-185">**Default**.</span></span> <span data-ttu-id="33c92-186">Hiermee stelt u het standaard uitvoerings beleid in.</span><span class="sxs-lookup"><span data-stu-id="33c92-186">Sets the default execution policy.</span></span> <span data-ttu-id="33c92-187">**Beperkt** voor Windows-clients of **RemoteSigned** voor Windows-servers.</span><span class="sxs-lookup"><span data-stu-id="33c92-187">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="33c92-188">**RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="33c92-188">**RemoteSigned**.</span></span> <span data-ttu-id="33c92-189">Vereist dat alle scripts en configuratie bestanden van het Internet worden ondertekend door een vertrouwde uitgever.</span><span class="sxs-lookup"><span data-stu-id="33c92-189">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="33c92-190">Het standaard uitvoerings beleid voor Windows Server-computers.</span><span class="sxs-lookup"><span data-stu-id="33c92-190">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="33c92-191">**Beperkt**.</span><span class="sxs-lookup"><span data-stu-id="33c92-191">**Restricted**.</span></span> <span data-ttu-id="33c92-192">Laadt geen configuratie bestanden of voert scripts uit.</span><span class="sxs-lookup"><span data-stu-id="33c92-192">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="33c92-193">Het standaard beleid voor het uitvoeren van Windows-client computers.</span><span class="sxs-lookup"><span data-stu-id="33c92-193">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="33c92-194">Niet **gedefinieerd**.</span><span class="sxs-lookup"><span data-stu-id="33c92-194">**Undefined**.</span></span> <span data-ttu-id="33c92-195">Er is geen uitvoerings beleid ingesteld voor het bereik.</span><span class="sxs-lookup"><span data-stu-id="33c92-195">No execution policy is set for the scope.</span></span> <span data-ttu-id="33c92-196">Hiermee wordt een toegewezen uitvoerings beleid verwijderd uit een bereik dat niet is ingesteld door een groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="33c92-196">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="33c92-197">Als het uitvoerings beleid in alle bereiken niet is **gedefinieerd** , wordt het effectief uitvoerings beleid **beperkt**.</span><span class="sxs-lookup"><span data-stu-id="33c92-197">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted**.</span></span>
- <span data-ttu-id="33c92-198">**Onbeperkt**.</span><span class="sxs-lookup"><span data-stu-id="33c92-198">**Unrestricted**.</span></span> <span data-ttu-id="33c92-199">Vanaf Power shell 6,0 is dit het standaard uitvoerings beleid voor niet-Windows-computers en kan het niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="33c92-199">Beginning in PowerShell 6.0, this is the default execution policy for non-Windows computers and can't be changed.</span></span> <span data-ttu-id="33c92-200">Laadt alle configuratie bestanden en voert alle scripts uit.</span><span class="sxs-lookup"><span data-stu-id="33c92-200">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="33c92-201">Als u een niet-ondertekend script uitvoert dat van Internet is gedownload, wordt u gevraagd om toestemming voordat het wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="33c92-201">If you run an unsigned script that was downloaded from the internet, you're prompted for permission before it runs.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="33c92-202">-Force</span><span class="sxs-lookup"><span data-stu-id="33c92-202">-Force</span></span>

<span data-ttu-id="33c92-203">Onderdrukt alle bevestigings prompts.</span><span class="sxs-lookup"><span data-stu-id="33c92-203">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="33c92-204">Wees voorzichtig met deze para meter om onverwachte resultaten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="33c92-204">Use caution with this parameter to avoid unexpected results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33c92-205">-Bereik</span><span class="sxs-lookup"><span data-stu-id="33c92-205">-Scope</span></span>

<span data-ttu-id="33c92-206">Hiermee geeft u het bereik op dat wordt beïnvloed door een uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="33c92-206">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="33c92-207">Het standaard bereik is **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="33c92-207">The default scope is **LocalMachine**.</span></span>

<span data-ttu-id="33c92-208">Het effectief uitvoerings beleid wordt als volgt bepaald door de volg orde van prioriteit:</span><span class="sxs-lookup"><span data-stu-id="33c92-208">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="33c92-209">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="33c92-209">**MachinePolicy**.</span></span> <span data-ttu-id="33c92-210">Ingesteld door een groepsbeleid voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="33c92-210">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="33c92-211">**User Policy**.</span><span class="sxs-lookup"><span data-stu-id="33c92-211">**UserPolicy**.</span></span> <span data-ttu-id="33c92-212">Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="33c92-212">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="33c92-213">**Proces**.</span><span class="sxs-lookup"><span data-stu-id="33c92-213">**Process**.</span></span> <span data-ttu-id="33c92-214">Alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="33c92-214">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="33c92-215">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="33c92-215">**CurrentUser**.</span></span> <span data-ttu-id="33c92-216">Alleen van invloed op de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="33c92-216">Affects only the current user.</span></span>
- <span data-ttu-id="33c92-217">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="33c92-217">**LocalMachine**.</span></span> <span data-ttu-id="33c92-218">Het standaard bereik dat van invloed is op alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="33c92-218">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="33c92-219">Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="33c92-219">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="33c92-220">Het uitvoerings beleid wordt opgeslagen in de omgevings variabele in `$env:PSExecutionPolicyPreference` plaats van het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="33c92-220">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="33c92-221">Wanneer de Power shell-sessie wordt gesloten, worden de variabele en de waarde verwijderd.</span><span class="sxs-lookup"><span data-stu-id="33c92-221">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="33c92-222">Uitvoerings beleid voor het bereik van **CurrentUser** wordt geschreven naar de register component **HKEY_LOCAL_USER**.</span><span class="sxs-lookup"><span data-stu-id="33c92-222">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER**.</span></span>

<span data-ttu-id="33c92-223">Uitvoerings beleid voor het **LocalMachine** -bereik wordt geschreven naar de register component **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="33c92-223">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE**.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33c92-224">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="33c92-224">-WhatIf</span></span>

<span data-ttu-id="33c92-225">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="33c92-225">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="33c92-226">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="33c92-226">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="33c92-227">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33c92-227">CommonParameters</span></span>

<span data-ttu-id="33c92-228">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33c92-228">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33c92-229">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="33c92-229">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33c92-230">INVOER</span><span class="sxs-lookup"><span data-stu-id="33c92-230">INPUTS</span></span>

### <span data-ttu-id="33c92-231">Microsoft.PowerShell.ExecutionPolicy, System. String</span><span class="sxs-lookup"><span data-stu-id="33c92-231">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="33c92-232">U kunt een uitvoerings beleid of een teken reeks die de naam van een uitvoerings beleid bevat, door sluizen naar `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="33c92-232">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="33c92-233">UITVOER</span><span class="sxs-lookup"><span data-stu-id="33c92-233">OUTPUTS</span></span>

### <span data-ttu-id="33c92-234">Geen</span><span class="sxs-lookup"><span data-stu-id="33c92-234">None</span></span>

<span data-ttu-id="33c92-235">`Set-ExecutionPolicy` retourneert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="33c92-235">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="33c92-236">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="33c92-236">NOTES</span></span>

<span data-ttu-id="33c92-237">`Set-ExecutionPolicy` de **MachinePolicy** -en **User Policy** -scopes worden niet gewijzigd, omdat deze zijn ingesteld door groeps beleid.</span><span class="sxs-lookup"><span data-stu-id="33c92-237">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="33c92-238">`Set-ExecutionPolicy` overschrijft een groepsbeleid, zelfs niet als de gebruikers voorkeur meer beperkend is dan het beleid.</span><span class="sxs-lookup"><span data-stu-id="33c92-238">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="33c92-239">Als de groepsbeleid **script uitvoering inschakelen** is ingeschakeld voor de computer of gebruiker, wordt de gebruikers voorkeur opgeslagen, maar dit is niet effectief.</span><span class="sxs-lookup"><span data-stu-id="33c92-239">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="33c92-240">In Power shell wordt een bericht weer gegeven waarin het conflict wordt uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="33c92-240">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="33c92-241">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="33c92-241">RELATED LINKS</span></span>

[<span data-ttu-id="33c92-242">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="33c92-242">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="33c92-243">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="33c92-243">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="33c92-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="33c92-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="33c92-245">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="33c92-245">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="33c92-246">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="33c92-246">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="33c92-247">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="33c92-247">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="33c92-248">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="33c92-248">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="33c92-249">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="33c92-249">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="33c92-250">Blok kering van bestand opheffen</span><span class="sxs-lookup"><span data-stu-id="33c92-250">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)
