---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExecutionPolicy
ms.openlocfilehash: f798aaef7032db450a13d79589eb7dd0ca762cd6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344827"
---
# <span data-ttu-id="0c3f8-103">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0c3f8-103">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="0c3f8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0c3f8-104">SYNOPSIS</span></span>
<span data-ttu-id="0c3f8-105">Hiermee haalt u het uitvoerings beleid voor de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-105">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="0c3f8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0c3f8-106">SYNTAX</span></span>

### <span data-ttu-id="0c3f8-107">Alles</span><span class="sxs-lookup"><span data-stu-id="0c3f8-107">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="0c3f8-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0c3f8-108">DESCRIPTION</span></span>

<span data-ttu-id="0c3f8-109">Gebruik om het uitvoerings beleid voor elk bereik weer te geven in de volg orde van prioriteit `Get-ExecutionPolicy -List` .</span><span class="sxs-lookup"><span data-stu-id="0c3f8-109">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="0c3f8-110">Om het effectief uitvoerings beleid voor uw Power shell-sessie gebruik `Get-ExecutionPolicy` zonder para meters te bekijken.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-110">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="0c3f8-111">Het effectief uitvoerings beleid wordt bepaald door uitvoerings beleid dat is ingesteld door `Set-ExecutionPolicy` en Groepsbeleid instellingen.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-111">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="0c3f8-112">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-112">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="0c3f8-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0c3f8-113">EXAMPLES</span></span>

### <span data-ttu-id="0c3f8-114">Voor beeld 1: alle uitvoerings beleidsregels ophalen</span><span class="sxs-lookup"><span data-stu-id="0c3f8-114">Example 1: Get all execution policies</span></span>

<span data-ttu-id="0c3f8-115">Met deze opdracht wordt het uitvoerings beleid voor elk bereik weer gegeven in de volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-115">This command displays the execution policies for each scope in the order of precedence.</span></span>

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

<span data-ttu-id="0c3f8-116">De `Get-ExecutionPolicy` cmdlet gebruikt de **List** -para meter om het uitvoerings beleid van elke scope weer te geven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-116">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="0c3f8-117">Voor beeld 2: een uitvoerings beleid instellen</span><span class="sxs-lookup"><span data-stu-id="0c3f8-117">Example 2: Set an execution policy</span></span>

<span data-ttu-id="0c3f8-118">In dit voor beeld ziet u hoe u een uitvoerings beleid instelt voor de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-118">This example shows how to set an execution policy for the local computer.</span></span>

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

<span data-ttu-id="0c3f8-119">De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **RemoteSigned** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-119">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="0c3f8-120">De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-120">The **Scope** parameter specifies the default scope value, **LocalMachine**.</span></span> <span data-ttu-id="0c3f8-121">Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-121">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="0c3f8-122">Voor beeld 3: het effectief uitvoerings beleid ophalen</span><span class="sxs-lookup"><span data-stu-id="0c3f8-122">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="0c3f8-123">In dit voor beeld ziet u hoe het effectief uitvoerings beleid voor een Power shell-sessie wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-123">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

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

<span data-ttu-id="0c3f8-124">De `Get-ExecutionPolicy` cmdlet gebruikt de **List** -para meter om het uitvoerings beleid van elke scope weer te geven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-124">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="0c3f8-125">De `Get-ExecutionPolicy` cmdlet wordt uitgevoerd zonder para meter om het effectief uitvoerings beleid, **Alles ondertekend** , weer te geven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-125">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned**.</span></span>

### <span data-ttu-id="0c3f8-126">Voor beeld 4: een script blok keren om het uit te voeren zonder het uitvoerings beleid te wijzigen</span><span class="sxs-lookup"><span data-stu-id="0c3f8-126">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="0c3f8-127">Dit voor beeld laat zien hoe u met het beleid voor het uitvoeren van **RemoteSigned** geen niet-ondertekende scripts kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-127">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="0c3f8-128">Een best practice is de code van het script te lezen en te controleren of het veilig is **voordat** u de `Unblock-File` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-128">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="0c3f8-129">De `Unblock-File` cmdlet verwijdert scripts zodat ze kunnen worden uitgevoerd, maar het uitvoerings beleid wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-129">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="0c3f8-130">De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **RemoteSigned** -beleid op te geven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-130">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="0c3f8-131">Het beleid wordt ingesteld voor het standaard bereik **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-131">The policy is set for the default scope, **LocalMachine**.</span></span>

<span data-ttu-id="0c3f8-132">De `Get-ExecutionPolicy` cmdlet geeft aan dat **RemoteSigned** het effectief uitvoerings beleid voor de huidige Power shell-sessie is.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-132">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="0c3f8-133">Het **Start-ActivityTracker.ps1** script wordt uitgevoerd vanuit de huidige map.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-133">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="0c3f8-134">Het script wordt geblokkeerd door **RemoteSigned** omdat het script geen digitale hand tekening heeft.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-134">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="0c3f8-135">Voor dit voor beeld is de code van het script beoordeeld en geverifieerd als veilig om uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-135">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="0c3f8-136">De `Unblock-File` cmdlet gebruikt de para meter **Path** om het script uit te blok keren.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-136">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="0c3f8-137">Als u wilt controleren of `Unblock-File` het uitvoerings beleid niet is gewijzigd, `Get-ExecutionPolicy` wordt het effectief uitvoerings beleid, **RemoteSigned** , weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-137">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned**.</span></span>

<span data-ttu-id="0c3f8-138">Het script **Start-ActivityTracker.ps1** wordt uitgevoerd vanuit de huidige map.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-138">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="0c3f8-139">Het script wordt uitgevoerd, omdat het is gedeblokkeerd door de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-139">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="0c3f8-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c3f8-140">PARAMETERS</span></span>

### <span data-ttu-id="0c3f8-141">-Lijst</span><span class="sxs-lookup"><span data-stu-id="0c3f8-141">-List</span></span>

<span data-ttu-id="0c3f8-142">Hiermee worden alle uitvoerings beleids waarden opgehaald voor de sessie die in volg orde van prioriteit wordt vermeld.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-142">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="0c3f8-143">`Get-ExecutionPolicy`Hiermee wordt standaard alleen het effectief uitvoerings beleid opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-143">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

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

### <span data-ttu-id="0c3f8-144">-Bereik</span><span class="sxs-lookup"><span data-stu-id="0c3f8-144">-Scope</span></span>

<span data-ttu-id="0c3f8-145">Hiermee geeft u het bereik op dat wordt beïnvloed door een uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-145">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="0c3f8-146">Het effectief uitvoerings beleid wordt als volgt bepaald door de volg orde van prioriteit:</span><span class="sxs-lookup"><span data-stu-id="0c3f8-146">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="0c3f8-147">**MachinePolicy**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-147">**MachinePolicy**.</span></span> <span data-ttu-id="0c3f8-148">Ingesteld door een groepsbeleid voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-148">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="0c3f8-149">**User Policy**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-149">**UserPolicy**.</span></span> <span data-ttu-id="0c3f8-150">Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-150">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="0c3f8-151">**Proces**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-151">**Process**.</span></span> <span data-ttu-id="0c3f8-152">Alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-152">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="0c3f8-153">**CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-153">**CurrentUser**.</span></span> <span data-ttu-id="0c3f8-154">Alleen van invloed op de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-154">Affects only the current user.</span></span>
- <span data-ttu-id="0c3f8-155">**LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-155">**LocalMachine**.</span></span> <span data-ttu-id="0c3f8-156">Het standaard bereik dat van invloed is op alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-156">Default scope that affects all users of the computer.</span></span>

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

### <span data-ttu-id="0c3f8-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c3f8-157">CommonParameters</span></span>

<span data-ttu-id="0c3f8-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c3f8-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c3f8-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="0c3f8-160">INPUTS</span></span>

### <span data-ttu-id="0c3f8-161">Geen</span><span class="sxs-lookup"><span data-stu-id="0c3f8-161">None</span></span>

<span data-ttu-id="0c3f8-162">`Get-ExecutionPolicy` invoer van de pijp lijn wordt niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-162">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="0c3f8-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0c3f8-163">OUTPUTS</span></span>

### <span data-ttu-id="0c3f8-164">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0c3f8-164">Microsoft.PowerShell.ExecutionPolicy</span></span>

<span data-ttu-id="0c3f8-165">De cmdlet retourneert altijd **onbeperkt** op Linux-en macOS-platforms.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-165">The cmdlet always returns **Unrestricted** on Linux and macOS platforms.</span></span>

## <span data-ttu-id="0c3f8-166">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0c3f8-166">NOTES</span></span>

<span data-ttu-id="0c3f8-167">Een uitvoerings beleid maakt deel uit van de Power shell-beveiligings strategie.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-167">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="0c3f8-168">Uitvoerings beleid bepaalt of u configuratie bestanden kunt laden, zoals uw Power shell-profiel, of scripts moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-168">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="0c3f8-169">En, of scripts digitaal moeten worden ondertekend voordat ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0c3f8-169">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="0c3f8-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0c3f8-170">RELATED LINKS</span></span>

[<span data-ttu-id="0c3f8-171">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="0c3f8-171">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="0c3f8-172">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="0c3f8-172">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="0c3f8-173">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="0c3f8-173">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="0c3f8-174">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="0c3f8-174">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="0c3f8-175">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="0c3f8-175">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
