---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: a846c3605c4adf469b12bfadaa3f90e585558dea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251169"
---
# <span data-ttu-id="bb6f2-103">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="bb6f2-103">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="bb6f2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bb6f2-104">SYNOPSIS</span></span>
<span data-ttu-id="bb6f2-105">Hiermee haalt u het uitvoerings beleid voor de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-105">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="bb6f2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bb6f2-106">SYNTAX</span></span>

### <span data-ttu-id="bb6f2-107">Alles</span><span class="sxs-lookup"><span data-stu-id="bb6f2-107">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="bb6f2-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bb6f2-108">DESCRIPTION</span></span>

<span data-ttu-id="bb6f2-109">Gebruik om het uitvoerings beleid voor elk bereik weer te geven in de volg orde van prioriteit `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="bb6f2-109">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="bb6f2-110">Om het effectief uitvoerings beleid voor uw Power shell-sessie gebruik `Get-ExecutionPolicy` zonder para meters te bekijken.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-110">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="bb6f2-111">Het effectief uitvoerings beleid wordt bepaald door uitvoerings beleid dat is ingesteld door `Set-ExecutionPolicy` en Groepsbeleid instellingen.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-111">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="bb6f2-112">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-112">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="bb6f2-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bb6f2-113">EXAMPLES</span></span>

### <span data-ttu-id="bb6f2-114">Voor beeld 1: alle uitvoerings beleidsregels ophalen</span><span class="sxs-lookup"><span data-stu-id="bb6f2-114">Example 1: Get all execution policies</span></span>

<span data-ttu-id="bb6f2-115">Met deze opdracht wordt het uitvoerings beleid voor elk bereik weer gegeven in de volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-115">This command displays the execution policies for each scope in the order of precedence.</span></span>

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

<span data-ttu-id="bb6f2-116">De `Get-ExecutionPolicy` cmdlet gebruikt de **List** -para meter om het uitvoerings beleid van elke scope weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-116">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="bb6f2-117">Voor beeld 2: een uitvoerings beleid instellen</span><span class="sxs-lookup"><span data-stu-id="bb6f2-117">Example 2: Set an execution policy</span></span>

<span data-ttu-id="bb6f2-118">In dit voor beeld ziet u hoe u een uitvoerings beleid instelt voor de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-118">This example shows how to set an execution policy for the local computer.</span></span>

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
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="bb6f2-119">De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **RemoteSigned** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-119">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="bb6f2-120">De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-120">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="bb6f2-121">Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-121">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="bb6f2-122">Voor beeld 3: het effectief uitvoerings beleid ophalen</span><span class="sxs-lookup"><span data-stu-id="bb6f2-122">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="bb6f2-123">In dit voor beeld ziet u hoe het effectief uitvoerings beleid voor een Power shell-sessie wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-123">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

<span data-ttu-id="bb6f2-124">De `Get-ExecutionPolicy` cmdlet gebruikt de **List** -para meter om het uitvoerings beleid van elke scope weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-124">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="bb6f2-125">De `Get-ExecutionPolicy` cmdlet wordt uitgevoerd zonder para meter om het effectief uitvoerings beleid, **Alles ondertekend** , weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-125">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="bb6f2-126">Voor beeld 4: een script blok keren om het uit te voeren zonder het uitvoerings beleid te wijzigen</span><span class="sxs-lookup"><span data-stu-id="bb6f2-126">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="bb6f2-127">Dit voor beeld laat zien hoe u met het beleid voor het uitvoeren van **RemoteSigned** geen niet-ondertekende scripts kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-127">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="bb6f2-128">Een best practice is de code van het script te lezen en te controleren of het veilig is **voordat** u de `Unblock-File` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-128">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="bb6f2-129">De `Unblock-File` cmdlet verwijdert scripts zodat ze kunnen worden uitgevoerd, maar het uitvoerings beleid wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-129">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="bb6f2-130">De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **RemoteSigned** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-130">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="bb6f2-131">Het beleid wordt ingesteld voor het standaard bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-131">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="bb6f2-132">De `Get-ExecutionPolicy` cmdlet geeft aan dat **RemoteSigned** het effectief uitvoerings beleid voor de huidige Power shell-sessie is.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-132">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="bb6f2-133">Het **Start-ActivityTracker.ps1** script wordt uitgevoerd vanuit de huidige map.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-133">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="bb6f2-134">Het script wordt geblokkeerd door **RemoteSigned** omdat het script geen digitale hand tekening heeft.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-134">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="bb6f2-135">Voor dit voor beeld is de code van het script beoordeeld en geverifieerd als veilig om uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-135">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="bb6f2-136">De `Unblock-File` cmdlet gebruikt de para meter **Path** om het script uit te blok keren.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-136">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="bb6f2-137">Als u wilt controleren of `Unblock-File` het uitvoerings beleid niet is gewijzigd, `Get-ExecutionPolicy` wordt het effectief uitvoerings beleid, **RemoteSigned** , weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-137">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="bb6f2-138">Het script **Start-ActivityTracker.ps1** wordt uitgevoerd vanuit de huidige map.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-138">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="bb6f2-139">Het script wordt uitgevoerd, omdat het is gedeblokkeerd door de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-139">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="bb6f2-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb6f2-140">PARAMETERS</span></span>

### <span data-ttu-id="bb6f2-141">-Lijst</span><span class="sxs-lookup"><span data-stu-id="bb6f2-141">-List</span></span>

<span data-ttu-id="bb6f2-142">Hiermee worden alle uitvoerings beleids waarden opgehaald voor de sessie die in volg orde van prioriteit wordt vermeld.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-142">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="bb6f2-143">`Get-ExecutionPolicy`Hiermee wordt standaard alleen het effectief uitvoerings beleid opgehaald.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-143">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

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

### <span data-ttu-id="bb6f2-144">-Bereik</span><span class="sxs-lookup"><span data-stu-id="bb6f2-144">-Scope</span></span>

<span data-ttu-id="bb6f2-145">Hiermee geeft u het bereik op dat wordt beïnvloed door een uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-145">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="bb6f2-146">Het effectief uitvoerings beleid wordt als volgt bepaald door de volg orde van prioriteit:</span><span class="sxs-lookup"><span data-stu-id="bb6f2-146">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="bb6f2-147">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-147">**MachinePolicy**.</span></span> <span data-ttu-id="bb6f2-148">Ingesteld door een groepsbeleid voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-148">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="bb6f2-149">**User Policy**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-149">**UserPolicy**.</span></span> <span data-ttu-id="bb6f2-150">Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-150">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="bb6f2-151">**Proces**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-151">**Process**.</span></span> <span data-ttu-id="bb6f2-152">Alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-152">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="bb6f2-153">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-153">**CurrentUser**.</span></span> <span data-ttu-id="bb6f2-154">Alleen van invloed op de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-154">Affects only the current user.</span></span>
- <span data-ttu-id="bb6f2-155">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-155">**LocalMachine**.</span></span> <span data-ttu-id="bb6f2-156">Het standaard bereik dat van invloed is op alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-156">Default scope that affects all users of the computer.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb6f2-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb6f2-157">CommonParameters</span></span>

<span data-ttu-id="bb6f2-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb6f2-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb6f2-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="bb6f2-160">INPUTS</span></span>

### <span data-ttu-id="bb6f2-161">Geen</span><span class="sxs-lookup"><span data-stu-id="bb6f2-161">None</span></span>

<span data-ttu-id="bb6f2-162">`Get-ExecutionPolicy` invoer van de pijp lijn wordt niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-162">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="bb6f2-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bb6f2-163">OUTPUTS</span></span>

### <span data-ttu-id="bb6f2-164">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="bb6f2-164">Microsoft.PowerShell.ExecutionPolicy</span></span>

## <span data-ttu-id="bb6f2-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bb6f2-165">NOTES</span></span>

<span data-ttu-id="bb6f2-166">Een uitvoerings beleid maakt deel uit van de Power shell-beveiligings strategie.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-166">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="bb6f2-167">Uitvoerings beleid bepaalt of u configuratie bestanden kunt laden, zoals uw Power shell-profiel, of scripts moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-167">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="bb6f2-168">En, of scripts digitaal moeten worden ondertekend voordat ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bb6f2-168">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="bb6f2-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bb6f2-169">RELATED LINKS</span></span>

[<span data-ttu-id="bb6f2-170">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="bb6f2-170">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="bb6f2-171">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="bb6f2-171">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="bb6f2-172">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="bb6f2-172">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="bb6f2-173">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="bb6f2-173">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="bb6f2-174">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="bb6f2-174">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
