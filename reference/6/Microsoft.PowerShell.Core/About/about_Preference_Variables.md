---
description: Variabelen waarmee het gedrag van Power shell wordt aangepast.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 6f23e016131901ed78b223a4d23dfa12416d970b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252272"
---
# <a name="about-preference-variables"></a><span data-ttu-id="be860-104">Over voorkeurs variabelen</span><span class="sxs-lookup"><span data-stu-id="be860-104">About Preference Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="be860-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="be860-105">Short description</span></span>

<span data-ttu-id="be860-106">Variabelen waarmee het gedrag van Power shell wordt aangepast.</span><span class="sxs-lookup"><span data-stu-id="be860-106">Variables that customize the behavior of PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="be860-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="be860-107">Long description</span></span>

<span data-ttu-id="be860-108">Power shell bevat een set variabelen waarmee u het gedrag ervan kunt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="be860-108">PowerShell includes a set of variables that enable you to customize its behavior.</span></span> <span data-ttu-id="be860-109">Deze voorkeurs variabelen werken zoals de opties in op GUI gebaseerde systemen.</span><span class="sxs-lookup"><span data-stu-id="be860-109">These preference variables work like the options in GUI-based systems.</span></span>

<span data-ttu-id="be860-110">De voorkeurs variabelen zijn van invloed op de Power shell-besturings omgeving en alle opdrachten die in de omgeving worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-110">The preference variables affect the PowerShell operating environment and all commands run in the environment.</span></span> <span data-ttu-id="be860-111">In veel gevallen hebben de-cmdlets para meters die u kunt gebruiken om het voorkeurs gedrag voor een specifieke opdracht te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-111">In many cases, the cmdlets have parameters that you can use to override the preference behavior for a specific command.</span></span>

<span data-ttu-id="be860-112">De volgende tabel bevat de voorkeurs variabelen en hun standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="be860-112">The following table lists the preference variables and their default values.</span></span>

|             <span data-ttu-id="be860-113">Variabele</span><span class="sxs-lookup"><span data-stu-id="be860-113">Variable</span></span>             |       <span data-ttu-id="be860-114">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="be860-114">Default Value</span></span>       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | <span data-ttu-id="be860-115">Hoog</span><span class="sxs-lookup"><span data-stu-id="be860-115">High</span></span>                      |
| `$DebugPreference`               | <span data-ttu-id="be860-116">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="be860-116">SilentlyContinue</span></span>          |
| `$ErrorActionPreference`         | <span data-ttu-id="be860-117">Doorgaan</span><span class="sxs-lookup"><span data-stu-id="be860-117">Continue</span></span>                  |
| `$ErrorView`                     | <span data-ttu-id="be860-118">NormalView</span><span class="sxs-lookup"><span data-stu-id="be860-118">NormalView</span></span>                |
| `$FormatEnumerationLimit`        | <span data-ttu-id="be860-119">4</span><span class="sxs-lookup"><span data-stu-id="be860-119">4</span></span>                         |
| `$InformationPreference`         | <span data-ttu-id="be860-120">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="be860-120">SilentlyContinue</span></span>          |
| `$LogCommandHealthEvent`         | <span data-ttu-id="be860-121">ONWAAR (niet geregistreerd)</span><span class="sxs-lookup"><span data-stu-id="be860-121">False (not logged)</span></span>        |
| `$LogCommandLifecycleEvent`      | <span data-ttu-id="be860-122">ONWAAR (niet geregistreerd)</span><span class="sxs-lookup"><span data-stu-id="be860-122">False (not logged)</span></span>        |
| `$LogEngineHealthEvent`          | <span data-ttu-id="be860-123">Waar (geregistreerd)</span><span class="sxs-lookup"><span data-stu-id="be860-123">True (logged)</span></span>             |
| `$LogEngineLifecycleEvent`       | <span data-ttu-id="be860-124">Waar (geregistreerd)</span><span class="sxs-lookup"><span data-stu-id="be860-124">True (logged)</span></span>             |
| `$LogProviderLifecycleEvent`     | <span data-ttu-id="be860-125">Waar (geregistreerd)</span><span class="sxs-lookup"><span data-stu-id="be860-125">True (logged)</span></span>             |
| `$LogProviderHealthEvent`        | <span data-ttu-id="be860-126">Waar (geregistreerd)</span><span class="sxs-lookup"><span data-stu-id="be860-126">True (logged)</span></span>             |
| `$MaximumHistoryCount`           | <span data-ttu-id="be860-127">4096</span><span class="sxs-lookup"><span data-stu-id="be860-127">4096</span></span>                      |
| `$OFS`                           | <span data-ttu-id="be860-128">(Spatie teken ( `" "` ))</span><span class="sxs-lookup"><span data-stu-id="be860-128">(Space character (`" "`))</span></span> |
| `$OutputEncoding`                | <span data-ttu-id="be860-129">**UTF8Encoding** -object</span><span class="sxs-lookup"><span data-stu-id="be860-129">**UTF8Encoding** object</span></span>   |
| `$ProgressPreference`            | <span data-ttu-id="be860-130">Doorgaan</span><span class="sxs-lookup"><span data-stu-id="be860-130">Continue</span></span>                  |
| `$PSDefaultParameterValues`      | <span data-ttu-id="be860-131">(Geen-lege hash-tabel)</span><span class="sxs-lookup"><span data-stu-id="be860-131">(None - empty hash table)</span></span> |
| `$PSEmailServer`                 | <span data-ttu-id="be860-132">(Geen)</span><span class="sxs-lookup"><span data-stu-id="be860-132">(None)</span></span>                    |
| `$PSModuleAutoLoadingPreference` | <span data-ttu-id="be860-133">Alles</span><span class="sxs-lookup"><span data-stu-id="be860-133">All</span></span>                       |
| `$PSSessionApplicationName`      | <span data-ttu-id="be860-134">wsman</span><span class="sxs-lookup"><span data-stu-id="be860-134">wsman</span></span>                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | <span data-ttu-id="be860-135">Zie [$PSSessionOption](#pssessionoption)</span><span class="sxs-lookup"><span data-stu-id="be860-135">See [$PSSessionOption](#pssessionoption)</span></span> |
| `$Transcript`                    | <span data-ttu-id="be860-136">(geen)</span><span class="sxs-lookup"><span data-stu-id="be860-136">(none)</span></span>                    |
| `$VerbosePreference`             | <span data-ttu-id="be860-137">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="be860-137">SilentlyContinue</span></span>          |
| `$WarningPreference`             | <span data-ttu-id="be860-138">Doorgaan</span><span class="sxs-lookup"><span data-stu-id="be860-138">Continue</span></span>                  |
| `$WhatIfPreference`              | <span data-ttu-id="be860-139">Niet waar</span><span class="sxs-lookup"><span data-stu-id="be860-139">False</span></span>                     |

<span data-ttu-id="be860-140">Power shell bevat de volgende omgevings variabelen waarmee gebruikers voorkeuren worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="be860-140">PowerShell includes the following environment variables that store user preferences.</span></span> <span data-ttu-id="be860-141">Zie [about_Environment_Variables](about_Environment_Variables.md)voor meer informatie over deze omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="be860-141">For more information about these environment variables, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> <span data-ttu-id="be860-142">Wijzigingen in de voorkeurs variabele worden alleen doorgevoerd in scripts en functies als deze scripts of functies in hetzelfde bereik zijn gedefinieerd als het bereik waarin de voor keur is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="be860-142">Changes to preference variable only take effect in scripts and functions if those scripts or functions are defined in the same scope as the scope in which preference was used.</span></span> <span data-ttu-id="be860-143">Zie [about_Scopes](about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-143">For more information, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="working-with-preference-variables"></a><span data-ttu-id="be860-144">Werken met voorkeurs variabelen</span><span class="sxs-lookup"><span data-stu-id="be860-144">Working with preference variables</span></span>

<span data-ttu-id="be860-145">In dit document worden alle voorkeurs variabelen beschreven.</span><span class="sxs-lookup"><span data-stu-id="be860-145">This document describes each of the preference variables.</span></span>

<span data-ttu-id="be860-146">Als u de huidige waarde van een specifieke voorkeurs variabele wilt weer geven, typt u de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-146">To display the current value of a specific preference variable, type the variable's name.</span></span> <span data-ttu-id="be860-147">Met de volgende opdracht wordt bijvoorbeeld de `$ConfirmPreference` waarde van de variabele weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-147">For example, the following command displays the `$ConfirmPreference` variable's value.</span></span>

```powershell
 $ConfirmPreference
```

```Output
High
```

<span data-ttu-id="be860-148">Gebruik een toewijzings instructie om de waarde van een variabele te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="be860-148">To change a variable's value, use an assignment statement.</span></span> <span data-ttu-id="be860-149">De volgende instructie wijzigt bijvoorbeeld de `$ConfirmPreference` waarde van de para meter in **gemiddeld**.</span><span class="sxs-lookup"><span data-stu-id="be860-149">For example, the following statement changes the `$ConfirmPreference` parameter's value to **Medium**.</span></span>

```powershell
$ConfirmPreference = "Medium"
```

<span data-ttu-id="be860-150">De waarden die u instelt, zijn specifiek voor de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-150">The values that you set are specific to the current PowerShell session.</span></span> <span data-ttu-id="be860-151">Als u variabelen effectief wilt maken in alle Power shell-sessies, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="be860-151">To make variables effective in all PowerShell sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="be860-152">Zie [about_Profiles](about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-152">For more information, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="working-remotely"></a><span data-ttu-id="be860-153">Op afstand werken</span><span class="sxs-lookup"><span data-stu-id="be860-153">Working remotely</span></span>

<span data-ttu-id="be860-154">Wanneer u opdrachten uitvoert op een externe computer, worden de externe opdrachten alleen onderhevig aan de voor keuren die zijn ingesteld in de Power shell-client van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be860-154">When you run commands on a remote computer, the remote commands are only subject to the preferences set in the remote computer's PowerShell client.</span></span> <span data-ttu-id="be860-155">Wanneer u bijvoorbeeld een externe opdracht uitvoert, bepaalt de waarde van de variabele van de externe computer `$DebugPreference` hoe Power shell reageert op fout opsporing van berichten.</span><span class="sxs-lookup"><span data-stu-id="be860-155">For example, when you run a remote command, the value of the remote computer's `$DebugPreference` variable determines how PowerShell responds to debugging messages.</span></span>

<span data-ttu-id="be860-156">Zie [about_Remote](about_Remote.md)voor meer informatie over externe opdrachten.</span><span class="sxs-lookup"><span data-stu-id="be860-156">For more information about remote commands, see [about_Remote](about_Remote.md).</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="be860-157">\$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="be860-157">\$ConfirmPreference</span></span>

<span data-ttu-id="be860-158">Hiermee wordt bepaald of Power shell automatisch om bevestiging wordt gevraagd voordat een cmdlet of functie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-158">Determines whether PowerShell automatically prompts you for confirmation before running a cmdlet or function.</span></span>

<span data-ttu-id="be860-159">De `$ConfirmPreference` geldige waarden voor de variabele zijn **hoog** , **gemiddeld** of **laag**.</span><span class="sxs-lookup"><span data-stu-id="be860-159">The `$ConfirmPreference` variable's valid values are **High** , **Medium** , or **Low**.</span></span> <span data-ttu-id="be860-160">Cmdlets en functions krijgen een risico van **hoog** , **gemiddeld** of **laag**.</span><span class="sxs-lookup"><span data-stu-id="be860-160">Cmdlets and functions are assigned a risk of **High** , **Medium** , or **Low**.</span></span> <span data-ttu-id="be860-161">Wanneer de waarde van de `$ConfirmPreference` variabele kleiner is dan of gelijk is aan het risico dat is toegewezen aan een cmdlet of functie, wordt u door Power shell automatisch gevraagd om bevestiging voordat de cmdlet of functie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-161">When the value of the `$ConfirmPreference` variable is less than or equal to the risk assigned to a cmdlet or function, PowerShell automatically prompts you for confirmation before running the cmdlet or function.</span></span>

<span data-ttu-id="be860-162">Als de waarde van de `$ConfirmPreference` variabele **geen** is, wordt u door Power Shell nooit automatisch gevraagd voordat een cmdlet of functie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-162">If the value of the `$ConfirmPreference` variable is **None** , PowerShell never automatically prompts you before running a cmdlet or function.</span></span>

<span data-ttu-id="be860-163">Als u het bevestigings gedrag voor alle cmdlets en functies in de sessie wilt wijzigen, wijzigt u de `$ConfirmPreference` waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-163">To change the confirming behavior for all cmdlets and functions in the session, change `$ConfirmPreference` variable's value.</span></span>

<span data-ttu-id="be860-164">Als u de `$ConfirmPreference` voor één opdracht wilt overschrijven, gebruikt u de para meter **confirm** van de cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="be860-164">To override the `$ConfirmPreference` for a single command, use a cmdlet's or function's **Confirm** parameter.</span></span> <span data-ttu-id="be860-165">Als u een bevestiging wilt aanvragen, gebruikt u `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="be860-165">To request confirmation, use `-Confirm`.</span></span> <span data-ttu-id="be860-166">Gebruik om de bevestiging te onderdrukken `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="be860-166">To suppress confirmation, use `-Confirm:$false`.</span></span>

<span data-ttu-id="be860-167">Geldige waarden voor `$ConfirmPreference` :</span><span class="sxs-lookup"><span data-stu-id="be860-167">Valid values of `$ConfirmPreference`:</span></span>

- <span data-ttu-id="be860-168">**Geen** : er wordt niet automatisch om Power shell gevraagd.</span><span class="sxs-lookup"><span data-stu-id="be860-168">**None** : PowerShell doesn't prompt automatically.</span></span> <span data-ttu-id="be860-169">Als u een bevestiging van een bepaalde opdracht wilt aanvragen, gebruikt u de para meter **confirm** van de cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="be860-169">To request confirmation of a particular command, use the **Confirm** parameter of the cmdlet or function.</span></span>
- <span data-ttu-id="be860-170">**Laag** : Power shell vraagt om bevestiging voordat cmdlets of functies met een laag, gemiddeld of hoog risico worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-170">**Low** : PowerShell prompts for confirmation before running cmdlets or functions with a low, medium, or high risk.</span></span>
- <span data-ttu-id="be860-171">**Gemiddeld** : Power shell vraagt om bevestiging voordat cmdlets of functies met een gemiddeld of hoog risico worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-171">**Medium** : PowerShell prompts for confirmation before running cmdlets or functions with a medium, or high risk.</span></span>
- <span data-ttu-id="be860-172">**Hoog** : Power shell vraagt om bevestiging voordat cmdlets of functions met een hoog risico worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-172">**High** : PowerShell prompts for confirmation before running cmdlets or functions with a high risk.</span></span>

#### <a name="detailed-explanation"></a><span data-ttu-id="be860-173">Gedetailleerde uitleg</span><span class="sxs-lookup"><span data-stu-id="be860-173">Detailed explanation</span></span>

<span data-ttu-id="be860-174">Power shell kan u automatisch om bevestiging vragen voordat een actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be860-174">PowerShell can automatically prompt you for confirmation before doing an action.</span></span> <span data-ttu-id="be860-175">Als cmdlet of function bijvoorbeeld aanzienlijk van invloed is op het systeem om gegevens te verwijderen of een aanzienlijke hoeveelheid systeem bronnen te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="be860-175">For example, when cmdlet or function significantly affects the system to delete data or use a significant amount of system resources.</span></span>

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

<span data-ttu-id="be860-176">De schatting van het risico is een kenmerk van de cmdlet of functie die de **ConfirmImpact** heet.</span><span class="sxs-lookup"><span data-stu-id="be860-176">The estimate of the risk is an attribute of the cmdlet or function known as its **ConfirmImpact**.</span></span> <span data-ttu-id="be860-177">Gebruikers kunnen dit niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="be860-177">Users can't change it.</span></span>

<span data-ttu-id="be860-178">Cmdlets en functies die mogelijk een risico vormen voor het systeem, hebben een **bevestigings** parameter die u kunt gebruiken om de bevestiging van één opdracht aan te vragen of te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-178">Cmdlets and functions that might pose a risk to the system have a **Confirm** parameter that you can use to request or suppress confirmation for a single command.</span></span>

<span data-ttu-id="be860-179">Omdat de meeste cmdlets en functies gebruikmaken van de standaard risico waarde, **ConfirmImpact** , van **medium** en de standaard waarde van `$ConfirmPreference` is **hoog** , wordt er zelden een automatische bevestiging weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-179">Because most cmdlets and functions use the default risk value, **ConfirmImpact** , of **Medium** , and the default value of `$ConfirmPreference` is **High** , automatic confirmation rarely occurs.</span></span> <span data-ttu-id="be860-180">U kunt de automatische bevestiging echter activeren door de waarde te wijzigen van `$ConfirmPreference` op **gemiddeld** of **laag**.</span><span class="sxs-lookup"><span data-stu-id="be860-180">However, you can activate automatic confirmation by changing the value of `$ConfirmPreference` to **Medium** or **Low**.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-181">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-181">Examples</span></span>

<span data-ttu-id="be860-182">In dit voor beeld ziet u het effect van de `$ConfirmPreference` standaard waarde van de variabele, **hoog**.</span><span class="sxs-lookup"><span data-stu-id="be860-182">This example shows the effect of the `$ConfirmPreference` variable's default value, **High**.</span></span> <span data-ttu-id="be860-183">Met de **hoge** waarde worden alleen cmdlets en functies met een hoog risico bevestigd.</span><span class="sxs-lookup"><span data-stu-id="be860-183">The **High** value only confirms high-risk cmdlets and functions.</span></span> <span data-ttu-id="be860-184">Aangezien de meeste cmdlets en functies gemiddeld risico lopen, worden ze niet automatisch bevestigd en wordt `Remove-Item` het bestand verwijderd.</span><span class="sxs-lookup"><span data-stu-id="be860-184">Since most cmdlets and functions are medium risk, they aren't automatically confirmed and `Remove-Item` deletes the file.</span></span> <span data-ttu-id="be860-185">`-Confirm`Als u toevoegt aan de opdracht, wordt de gebruiker gevraagd om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="be860-185">Adding `-Confirm` to the command prompts the user for confirmation.</span></span>

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

<span data-ttu-id="be860-186">Gebruiken `-Confirm` om een bevestiging aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="be860-186">Use `-Confirm` to request confirmation.</span></span>

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

<span data-ttu-id="be860-187">In het volgende voor beeld ziet u het effect van het wijzigen van de waarde van `$ConfirmPreference` op **gemiddeld**.</span><span class="sxs-lookup"><span data-stu-id="be860-187">The following example shows the effect of changing the value of `$ConfirmPreference` to **Medium**.</span></span> <span data-ttu-id="be860-188">Omdat de meeste cmdlets en functies gemiddeld risico lopen, worden ze automatisch bevestigd.</span><span class="sxs-lookup"><span data-stu-id="be860-188">Because most cmdlets and function are medium risk, they're automatically confirmed.</span></span> <span data-ttu-id="be860-189">Als u de bevestigings prompt voor één opdracht wilt onderdrukken, gebruikt u de para meter **confirm** met de waarde `$false` .</span><span class="sxs-lookup"><span data-stu-id="be860-189">To suppress the confirmation prompt for a single command, use the **Confirm** parameter with a value of `$false`.</span></span>

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a><span data-ttu-id="be860-190">\$DebugPreference</span><span class="sxs-lookup"><span data-stu-id="be860-190">\$DebugPreference</span></span>

<span data-ttu-id="be860-191">Bepaalt hoe Power shell reageert op fout opsporing van berichten die zijn gegenereerd door een script, cmdlet of provider, of door een `Write-Debug` opdracht op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="be860-191">Determines how PowerShell responds to debugging messages generated by a script, cmdlet or provider, or by a `Write-Debug` command at the command line.</span></span>

<span data-ttu-id="be860-192">Sommige cmdlets tonen fout opsporingsgegevens, meestal technische berichten die zijn bedoeld voor programmeurs en technische ondersteunings medewerkers.</span><span class="sxs-lookup"><span data-stu-id="be860-192">Some cmdlets display debugging messages, which are typically technical messages designed for programmers and technical support professionals.</span></span> <span data-ttu-id="be860-193">Standaard worden fout opsporings berichten niet weer gegeven, maar u kunt fout opsporingsgegevens weer geven door de waarde van te wijzigen `$DebugPreference` .</span><span class="sxs-lookup"><span data-stu-id="be860-193">By default, debugging messages aren't displayed, but you can display debugging messages by changing the value of `$DebugPreference`.</span></span>

<span data-ttu-id="be860-194">U kunt de para meter common **debug** van een cmdlet gebruiken om de fout opsporingsgegevens voor een specifieke opdracht weer te geven of te verbergen.</span><span class="sxs-lookup"><span data-stu-id="be860-194">You can use the **Debug** common parameter of a cmdlet to display or hide the debugging messages for a specific command.</span></span> <span data-ttu-id="be860-195">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-195">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="be860-196">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-196">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-197">**Stop** : geeft het debug-bericht weer en stopt de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="be860-197">**Stop** : Displays the debug message and stops executing.</span></span> <span data-ttu-id="be860-198">Hiermee schrijft u een fout naar de-console.</span><span class="sxs-lookup"><span data-stu-id="be860-198">Writes an error to the console.</span></span>
- <span data-ttu-id="be860-199">**Query** : Hiermee wordt het fout bericht over fouten weer gegeven en wordt u gevraagd of u wilt door gaan.</span><span class="sxs-lookup"><span data-stu-id="be860-199">**Inquire** : Displays the debug message and asks you whether you want to continue.</span></span> <span data-ttu-id="be860-200">Het toevoegen van de para meter common **debug** voor een opdracht, als de opdracht is geconfigureerd voor het genereren van een fout opsporingsgegevens, wijzigt u de waarde van de `$DebugPreference` variabele om op te **vragen**.</span><span class="sxs-lookup"><span data-stu-id="be860-200">Adding the **Debug** common parameter to a command, when the command is configured to generate a debugging message, changes the value of the `$DebugPreference` variable to **Inquire**.</span></span>
- <span data-ttu-id="be860-201">**Door gaan** : Hiermee geeft u het fout bericht bij de uitvoering weer en gaat u verder met uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="be860-201">**Continue** : Displays the debug message and continues with execution.</span></span>
- <span data-ttu-id="be860-202">**SilentlyContinue** : (standaard) geen effect.</span><span class="sxs-lookup"><span data-stu-id="be860-202">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="be860-203">Het bericht fout opsporing wordt niet weer gegeven en de uitvoering wordt zonder onderbreking voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-203">The debug message isn't displayed and execution continues without interruption.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-204">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-204">Examples</span></span>

<span data-ttu-id="be860-205">In de volgende voor beelden ziet u het effect van het wijzigen van de waarden van `$DebugPreference` Wanneer een `Write-Debug` opdracht wordt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="be860-205">The following examples show the effect of changing the values of `$DebugPreference` when a `Write-Debug` command is entered at the command line.</span></span>
<span data-ttu-id="be860-206">De wijziging is van invloed op alle fout opsporingsgegevens, met inbegrip van berichten die worden gegenereerd door cmdlets en scripts.</span><span class="sxs-lookup"><span data-stu-id="be860-206">The change affects all debugging messages, including messages generated by cmdlets and scripts.</span></span> <span data-ttu-id="be860-207">In de voor beelden wordt de para meter **debug** weer gegeven, waarin de fout opsporingsgegevens die betrekking hebben op één opdracht, worden weer geven of verborgen.</span><span class="sxs-lookup"><span data-stu-id="be860-207">The examples show the **Debug** parameter, which displays or hides the debugging messages related to a single command.</span></span>

<span data-ttu-id="be860-208">In dit voor beeld ziet u het effect van de `$DebugPreference` standaard waarde van de variabele **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="be860-208">This example shows the effect of the `$DebugPreference` variable's default value, **SilentlyContinue**.</span></span> <span data-ttu-id="be860-209">Standaard wordt het `Write-Debug` debug-bericht van de cmdlet niet weer gegeven en wordt de verwerking voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-209">By default, the `Write-Debug` cmdlet's debug message isn't displayed and processing continues.</span></span> <span data-ttu-id="be860-210">Wanneer de **debug** -para meter wordt gebruikt, wordt de voor keur voor één opdracht overschreven.</span><span class="sxs-lookup"><span data-stu-id="be860-210">When the **Debug** parameter is used, it overrides the preference for a single command.</span></span> <span data-ttu-id="be860-211">Het bericht fout opsporing wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-211">The debug message is displayed.</span></span>

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="be860-212">In dit voor beeld ziet u het effect van `$DebugPreference` met de waarde **continue** .</span><span class="sxs-lookup"><span data-stu-id="be860-212">This example shows the effect of `$DebugPreference` with the **Continue** value.</span></span> <span data-ttu-id="be860-213">Het bericht fout opsporing wordt weer gegeven en de opdracht blijft verwerken.</span><span class="sxs-lookup"><span data-stu-id="be860-213">The debug message is displayed and the command continues to process.</span></span>

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="be860-214">In dit voor beeld wordt de para meter **debug** gebruikt met de waarde `$false` om het bericht voor één opdracht te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-214">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="be860-215">Het bericht fout opsporing wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-215">The debug message isn't displayed.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="be860-216">Dit voor beeld laat zien hoe het effect is van `$DebugPreference` het instellen op de waarde **Stop** .</span><span class="sxs-lookup"><span data-stu-id="be860-216">This example shows the effect of `$DebugPreference` being set to the **Stop** value.</span></span> <span data-ttu-id="be860-217">Het bericht fout opsporing wordt weer gegeven en de opdracht is gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-217">The debug message is displayed and the command is stopped.</span></span>

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

<span data-ttu-id="be860-218">In dit voor beeld wordt de para meter **debug** gebruikt met de waarde `$false` om het bericht voor één opdracht te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-218">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="be860-219">Het bericht fout opsporing wordt niet weer gegeven en de verwerking is niet gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-219">The debug message isn't displayed and processing isn't stopped.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="be860-220">Dit voor beeld laat zien hoe het effect is van `$DebugPreference` het instellen op de **query** waarde.</span><span class="sxs-lookup"><span data-stu-id="be860-220">This example shows the effect of `$DebugPreference` being set to the **Inquire** value.</span></span> <span data-ttu-id="be860-221">Het bericht fout opsporing wordt weer gegeven en de gebruiker wordt om bevestiging gevraagd.</span><span class="sxs-lookup"><span data-stu-id="be860-221">The debug message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="be860-222">In dit voor beeld wordt de para meter **debug** gebruikt met de waarde `$false` om het bericht voor één opdracht te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-222">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="be860-223">Het bericht fout opsporing wordt niet weer gegeven en de verwerking wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-223">The debug message isn't displayed and processing continues.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a><span data-ttu-id="be860-224">\$ErrorActionPreference</span><span class="sxs-lookup"><span data-stu-id="be860-224">\$ErrorActionPreference</span></span>

<span data-ttu-id="be860-225">Bepaalt hoe Power shell reageert op een niet-afsluit fout, een fout die de verwerking van de cmdlet niet stopt.</span><span class="sxs-lookup"><span data-stu-id="be860-225">Determines how PowerShell responds to a non-terminating error, an error that doesn't stop the cmdlet processing.</span></span> <span data-ttu-id="be860-226">Bijvoorbeeld op de opdracht regel of in een script, cmdlet of provider, zoals de fouten die zijn gegenereerd door de `Write-Error` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be860-226">For example, at the command line or in a script, cmdlet, or provider, such as the errors generated by the `Write-Error` cmdlet.</span></span>

<span data-ttu-id="be860-227">U kunt de gemeen schappelijke para meter **Error Action** van de cmdlet gebruiken om de voor keur voor een specifieke opdracht te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-227">You can use a cmdlet's **ErrorAction** common parameter to override the preference for a specific command.</span></span>

<span data-ttu-id="be860-228">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-228">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-229">**Door gaan** : (standaard) Hiermee wordt het fout bericht weer gegeven en wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-229">**Continue** : (Default) Displays the error message and continues executing.</span></span>
- <span data-ttu-id="be860-230">**Negeren** : onderdrukt het fout bericht en gaat verder met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="be860-230">**Ignore** : Suppresses the error message and continues to execute the command.</span></span> <span data-ttu-id="be860-231">De waarde voor **negeren** is bedoeld voor gebruik per opdracht, niet voor gebruik als opgeslagen voor keur.</span><span class="sxs-lookup"><span data-stu-id="be860-231">The **Ignore** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="be860-232">**Ignore** is geen geldige waarde voor de `$ErrorActionPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-232">**Ignore** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>
- <span data-ttu-id="be860-233">**Query** : Hiermee wordt het fout bericht weer gegeven en wordt u gevraagd of u wilt door gaan.</span><span class="sxs-lookup"><span data-stu-id="be860-233">**Inquire** : Displays the error message and asks you whether you want to continue.</span></span>
- <span data-ttu-id="be860-234">**SilentlyContinue** : geen effect.</span><span class="sxs-lookup"><span data-stu-id="be860-234">**SilentlyContinue** : No effect.</span></span> <span data-ttu-id="be860-235">Het fout bericht wordt niet weer gegeven en de uitvoering wordt zonder onderbreking voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-235">The error message isn't displayed and execution continues without interruption.</span></span>
- <span data-ttu-id="be860-236">**Stop** : geeft het fout bericht weer en stopt de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="be860-236">**Stop** : Displays the error message and stops executing.</span></span> <span data-ttu-id="be860-237">Naast de fout die wordt gegenereerd, genereert de **Stop** waarde een ActionPreferenceStopException-object in de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="be860-237">In addition to the error generated, the **Stop** value generates an ActionPreferenceStopException object to the error stream.</span></span>
  <span data-ttu-id="be860-238">gegevensstroom</span><span class="sxs-lookup"><span data-stu-id="be860-238">stream</span></span>
- <span data-ttu-id="be860-239">**Suspend** : Hiermee wordt een werk stroom taak automatisch opgeschort zodat deze verder kan worden onderzocht.</span><span class="sxs-lookup"><span data-stu-id="be860-239">**Suspend** : Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="be860-240">Na onderzoek kan de werk stroom worden hervat.</span><span class="sxs-lookup"><span data-stu-id="be860-240">After investigation, the workflow can be resumed.</span></span> <span data-ttu-id="be860-241">De **suspend** -waarde is bedoeld voor gebruik per opdracht en niet voor gebruik als opgeslagen voor keur.</span><span class="sxs-lookup"><span data-stu-id="be860-241">The **Suspend** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="be860-242">**Suspend** is geen geldige waarde voor de `$ErrorActionPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-242">**Suspend** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="be860-243">`$ErrorActionPreference` en de para meter **Error Action** hebben geen invloed op de manier waarop Power shell reageert op beëindigings fouten die de verwerking van de cmdlet stoppen.</span><span class="sxs-lookup"><span data-stu-id="be860-243">`$ErrorActionPreference` and the **ErrorAction** parameter don't affect how PowerShell responds to terminating errors that stop cmdlet processing.</span></span> <span data-ttu-id="be860-244">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over de algemene para meter **Error Action** .</span><span class="sxs-lookup"><span data-stu-id="be860-244">For more information about the **ErrorAction** common parameter, see [about_CommonParameters](about_CommonParameters.md).</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-245">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-245">Examples</span></span>

<span data-ttu-id="be860-246">In deze voor beelden ziet u het effect van de verschillende waarden van de `$ErrorActionPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-246">These examples show the effect of the different values of the `$ErrorActionPreference` variable.</span></span> <span data-ttu-id="be860-247">De para meter **Error Action** wordt gebruikt om de `$ErrorActionPreference` waarde te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="be860-247">The **ErrorAction** parameter is used to override the `$ErrorActionPreference` value.</span></span>

<span data-ttu-id="be860-248">In dit voor beeld wordt de `$ErrorActionPreference` standaard waarde weer gegeven, **door gaan**.</span><span class="sxs-lookup"><span data-stu-id="be860-248">This example shows the `$ErrorActionPreference` default value, **Continue**.</span></span> <span data-ttu-id="be860-249">Er wordt een niet-afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="be860-249">A non-terminating error is generated.</span></span> <span data-ttu-id="be860-250">Het bericht wordt weer gegeven en de verwerking wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-250">The message is displayed and processing continues.</span></span>

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error -Message  'Test Error' ; Write-Host 'Hello World' : Test Error
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

Hello World
```

<span data-ttu-id="be860-251">In dit voor beeld ziet u de `$ErrorActionPreference` standaard waarde, **query's**.</span><span class="sxs-lookup"><span data-stu-id="be860-251">This example shows the `$ErrorActionPreference` default value, **Inquire**.</span></span> <span data-ttu-id="be860-252">Er wordt een fout gegenereerd en er wordt een prompt voor de actie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-252">An error is generated and a prompt for action is shown.</span></span>

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="be860-253">In dit voor beeld wordt de `$ErrorActionPreference` ingesteld op **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="be860-253">This example shows the `$ErrorActionPreference` set to **SilentlyContinue**.</span></span>
<span data-ttu-id="be860-254">Het fout bericht wordt onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="be860-254">The error message is suppressed.</span></span>

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

<span data-ttu-id="be860-255">In dit voor beeld ziet `$ErrorActionPreference` u de set die moet worden **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="be860-255">This example shows the `$ErrorActionPreference` set to **Stop**.</span></span> <span data-ttu-id="be860-256">Ook wordt het extra object weer gegeven dat is gegenereerd voor de `$Error` variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-256">It also shows the extra object generated to the `$Error` variable.</span></span>

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

The running command stopped because the preference variable "ErrorActionPreference"
or common parameter is set to Stop: Test Error

Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

### <a name="errorview"></a><span data-ttu-id="be860-257">\$ErrorView</span><span class="sxs-lookup"><span data-stu-id="be860-257">\$ErrorView</span></span>

<span data-ttu-id="be860-258">Bepaalt de weergave notatie van fout berichten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="be860-258">Determines the display format of error messages in PowerShell.</span></span>

<span data-ttu-id="be860-259">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-259">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-260">**NormalView** : (standaard) een gedetailleerde weer gave die is ontworpen voor de meeste gebruikers.</span><span class="sxs-lookup"><span data-stu-id="be860-260">**NormalView** : (Default) A detailed view designed for most users.</span></span> <span data-ttu-id="be860-261">Bevat een beschrijving van de fout en de naam van het object dat bij de fout betrokken is.</span><span class="sxs-lookup"><span data-stu-id="be860-261">Consists of a description of the error and the name of the object involved in the error.</span></span>
- <span data-ttu-id="be860-262">**CategoryView** : een beknopte, gestructureerde weer gave die is ontworpen voor productie omgevingen.</span><span class="sxs-lookup"><span data-stu-id="be860-262">**CategoryView** : A succinct, structured view designed for production environments.</span></span> <span data-ttu-id="be860-263">De indeling is als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-263">The format is as follows:</span></span>

  <span data-ttu-id="be860-264">{Category}: ({TargetName}: {target type}): [{Activity}], {Reason}</span><span class="sxs-lookup"><span data-stu-id="be860-264">{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}</span></span>

<span data-ttu-id="be860-265">Zie [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) -klasse voor meer informatie over de velden in **CategoryView**.</span><span class="sxs-lookup"><span data-stu-id="be860-265">For more information about the fields in **CategoryView** , see [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) class.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-266">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-266">Examples</span></span>

<span data-ttu-id="be860-267">In dit voor beeld ziet u hoe een fout wordt weer gegeven wanneer de waarde `$ErrorView` is ingesteld op de standaard **NormalView**.</span><span class="sxs-lookup"><span data-stu-id="be860-267">This example shows how an error appears when the value of `$ErrorView` is the default, **NormalView**.</span></span> <span data-ttu-id="be860-268">`Get-ChildItem` wordt gebruikt om een niet-bestaand bestand te zoeken.</span><span class="sxs-lookup"><span data-stu-id="be860-268">`Get-ChildItem` is used to find a non-existent file.</span></span>

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

<span data-ttu-id="be860-269">In dit voor beeld ziet u hoe dezelfde fout optreedt wanneer de waarde van `$ErrorView` wordt gewijzigd in **CategoryView**.</span><span class="sxs-lookup"><span data-stu-id="be860-269">This example shows how the same error appears when the value of `$ErrorView` is changed to **CategoryView**.</span></span>

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

<span data-ttu-id="be860-270">In dit voor beeld wordt gedemonstreerd dat de waarde van `$ErrorView` alleen invloed heeft op de fout weergave.</span><span class="sxs-lookup"><span data-stu-id="be860-270">This example demonstrates that the value of `$ErrorView` only affects the error display.</span></span> <span data-ttu-id="be860-271">De structuur van het fout object dat is opgeslagen in de automatische variabele wordt niet gewijzigd `$Error` .</span><span class="sxs-lookup"><span data-stu-id="be860-271">It doesn't change the structure of the error object that is stored in the `$Error` automatic variable.</span></span> <span data-ttu-id="be860-272">Zie about_automatic_variables voor meer informatie over de `$Error` automatische [about_automatic_variables](about_Automatic_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-272">For information about the `$Error` automatic variable, see [about_automatic_variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="be860-273">Met de volgende opdracht wordt het **ErrorRecord** -object dat is gekoppeld aan de meest recente fout in de fout matrix, **element 0** , gebruikt en worden alle eigenschappen van het object Error in een lijst opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="be860-273">The following command takes the **ErrorRecord** object associated with the most recent error in the error array, **element 0** , and formats all the error object's properties in a list.</span></span>

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a><span data-ttu-id="be860-274">\$FormatEnumerationLimit</span><span class="sxs-lookup"><span data-stu-id="be860-274">\$FormatEnumerationLimit</span></span>

<span data-ttu-id="be860-275">Hiermee wordt bepaald hoeveel opgesomde items in een weer gave worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="be860-275">Determines how many enumerated items are included in a display.</span></span> <span data-ttu-id="be860-276">Deze variabele heeft geen invloed op de onderliggende objecten, alleen de weer gave.</span><span class="sxs-lookup"><span data-stu-id="be860-276">This variable doesn't affect the underlying objects, only the display.</span></span> <span data-ttu-id="be860-277">Wanneer de waarde van `$FormatEnumerationLimit` kleiner is dan het aantal opgesomde items, voegt Power shell een weglatings teken ( `...` ) toe om items aan te geven die niet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-277">When the value of `$FormatEnumerationLimit` is fewer than the number of enumerated items, PowerShell adds an ellipsis (`...`) to indicate items not shown.</span></span>

<span data-ttu-id="be860-278">**Geldige waarden** : integers ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="be860-278">**Valid values** : Integers (`Int32`)</span></span>

<span data-ttu-id="be860-279">**Standaard waarde** : 4</span><span class="sxs-lookup"><span data-stu-id="be860-279">**Default value** : 4</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-280">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-280">Examples</span></span>

<span data-ttu-id="be860-281">In dit voor beeld ziet u hoe u de `$FormatEnumerationLimit` variabele gebruikt om de weer gave van opgesomde items te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="be860-281">This example shows how to use the `$FormatEnumerationLimit` variable to improve the display of enumerated items.</span></span>

<span data-ttu-id="be860-282">Met de opdracht in dit voor beeld wordt een tabel gegenereerd met een lijst met alle services die worden uitgevoerd op de computer in twee groepen: één voor het **uitvoeren** van services en één voor **gestopt** Services.</span><span class="sxs-lookup"><span data-stu-id="be860-282">The command in this example generates a table that lists all the services running on the computer in two groups: one for **running** services and one for **stopped** services.</span></span> <span data-ttu-id="be860-283">Er wordt een `Get-Service` opdracht gebruikt om alle services op te halen en vervolgens worden de resultaten via de pijp lijn naar de `Group-Object` cmdlet verzonden, waarmee de resultaten worden gegroepeerd op basis van de status van de service.</span><span class="sxs-lookup"><span data-stu-id="be860-283">It uses a `Get-Service` command to get all the services, and then sends the results through the pipeline to the `Group-Object` cmdlet, which groups the results by the service status.</span></span>

<span data-ttu-id="be860-284">Het resultaat is een tabel met een lijst met de status in de kolom **naam** en de processen in de kolom **groep** .</span><span class="sxs-lookup"><span data-stu-id="be860-284">The result is a table that lists the status in the **Name** column, and the processes in the **Group** column.</span></span> <span data-ttu-id="be860-285">Als u de kolomlabels wilt wijzigen, gebruikt u een hash-tabel, Zie [about_Hash_Tables](about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="be860-285">To change the column labels, use a hash table, see [about_Hash_Tables](about_Hash_Tables.md).</span></span> <span data-ttu-id="be860-286">Zie de voor beelden in de [indelings tabel](xref:Microsoft.PowerShell.Utility.Format-Table)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-286">For more information, see the examples in [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

<span data-ttu-id="be860-287">Zoek de huidige waarde van `$FormatEnumerationLimit` .</span><span class="sxs-lookup"><span data-stu-id="be860-287">Find the current value of `$FormatEnumerationLimit`.</span></span>

```powershell
$FormatEnumerationLimit
```

```Output
4
```

<span data-ttu-id="be860-288">Alle services gegroepeerd op **status** weer geven.</span><span class="sxs-lookup"><span data-stu-id="be860-288">List all services grouped by **Status**.</span></span> <span data-ttu-id="be860-289">Er zijn Maxi maal vier services die worden vermeld in de kolom **groep** voor elke status, omdat de `$FormatEnumerationLimit` waarde **4** heeft.</span><span class="sxs-lookup"><span data-stu-id="be860-289">There are a maximum of four services listed in the **Group** column for each status because `$FormatEnumerationLimit` has a value of **4**.</span></span>

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

<span data-ttu-id="be860-290">Verhoog het aantal items in de lijst door de waarde te verhogen `$FormatEnumerationLimit` van **1000**.</span><span class="sxs-lookup"><span data-stu-id="be860-290">To increase the number of items listed, increase the value of `$FormatEnumerationLimit` to **1000**.</span></span> <span data-ttu-id="be860-291">Gebruik `Get-Service` en `Group-Object` om de services weer te geven.</span><span class="sxs-lookup"><span data-stu-id="be860-291">Use `Get-Service` and `Group-Object` to display the services.</span></span>

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

<span data-ttu-id="be860-292">Gebruik `Format-Table` met de para meter **wrap** om de lijst met services weer te geven.</span><span class="sxs-lookup"><span data-stu-id="be860-292">Use `Format-Table` with the **Wrap** parameter to display the list of services.</span></span>

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a><span data-ttu-id="be860-293">\$InformationPreference</span><span class="sxs-lookup"><span data-stu-id="be860-293">\$InformationPreference</span></span>

<span data-ttu-id="be860-294">Met de `$InformationPreference` variabele kunt u voor keuren voor de informatie stroom instellen die u wilt weer geven voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="be860-294">The `$InformationPreference` variable lets you set information stream preferences that you want displayed to users.</span></span> <span data-ttu-id="be860-295">Met name informatie berichten die u hebt toegevoegd aan opdrachten of scripts door de cmdlet [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="be860-295">Specifically, informational messages that you added to commands or scripts by adding the [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet.</span></span> <span data-ttu-id="be860-296">Als de para meter **Information Action** wordt gebruikt, overschrijft de waarde de waarde van de `$InformationPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-296">If the **InformationAction** parameter is used, its value overrides the value of the `$InformationPreference` variable.</span></span> <span data-ttu-id="be860-297">`Write-Information` is geïntroduceerd in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="be860-297">`Write-Information` was introduced in PowerShell 5.0.</span></span>

<span data-ttu-id="be860-298">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-298">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-299">**Stoppen** : Hiermee stopt u een opdracht of script bij een exemplaar van de `Write-Information` opdracht.</span><span class="sxs-lookup"><span data-stu-id="be860-299">**Stop** : Stops a command or script at an occurrence of the `Write-Information` command.</span></span>
- <span data-ttu-id="be860-300">**Query** : geeft het informatieve bericht weer dat u in een opdracht opgeeft `Write-Information` . vervolgens wordt u gevraagd of u wilt door gaan.</span><span class="sxs-lookup"><span data-stu-id="be860-300">**Inquire** : Displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>
- <span data-ttu-id="be860-301">**Door gaan** : geeft het informatieve bericht weer en blijft actief.</span><span class="sxs-lookup"><span data-stu-id="be860-301">**Continue** : Displays the informational message, and continues running.</span></span>
- <span data-ttu-id="be860-302">**Suspend** is alleen beschikbaar voor werk stromen die niet worden ondersteund in Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="be860-302">**Suspend** is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>
- <span data-ttu-id="be860-303">**SilentlyContinue** : (standaard) geen effect.</span><span class="sxs-lookup"><span data-stu-id="be860-303">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="be860-304">De informatieve berichten worden niet weer gegeven en het script wordt zonder onderbreking voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-304">The informational messages aren't displayed, and the script continues without interruption.</span></span>

### <a name="logevent"></a><span data-ttu-id="be860-305">\$Logboek \* gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="be860-305">\$Log\*Event</span></span>

<span data-ttu-id="be860-306">Het **logboek \* gebeurtenis** voorkeurs variabelen bepalen welke typen gebeurtenissen worden geschreven naar het Power shell-gebeurtenis logboek in Logboeken.</span><span class="sxs-lookup"><span data-stu-id="be860-306">The **Log\*Event** preference variables determine which types of events are written to the PowerShell event log in Event Viewer.</span></span> <span data-ttu-id="be860-307">Standaard worden alleen engine-en provider gebeurtenissen vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="be860-307">By default, only engine and provider events are logged.</span></span> <span data-ttu-id="be860-308">Maar u kunt het logboek \*\*\* gebeurtenis\*\* voorkeurs variabelen gebruiken om uw logboek aan te passen, zoals logboek gebeurtenissen over opdrachten.</span><span class="sxs-lookup"><span data-stu-id="be860-308">But, you can use the **Log\*Event** preference variables to customize your log, such as logging events about commands.</span></span>

<span data-ttu-id="be860-309">Het **logboek \* gebeurtenis** voorkeurs variabelen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-309">The **Log\*Event** preference variables are as follows:</span></span>

- <span data-ttu-id="be860-310">`$LogCommandHealthEvent`: Registreert fouten en uitzonde ringen in de opdracht initialisatie en-verwerking.</span><span class="sxs-lookup"><span data-stu-id="be860-310">`$LogCommandHealthEvent`: Logs errors and exceptions in command initialization and processing.</span></span> <span data-ttu-id="be860-311">De standaard instelling is `$false` (niet geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="be860-311">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="be860-312">`$LogCommandLifecycleEvent`: Registreert het starten en stoppen van opdrachten en opdracht pijplijnen en beveiligings uitzonderingen in opdracht detectie.</span><span class="sxs-lookup"><span data-stu-id="be860-312">`$LogCommandLifecycleEvent`: Logs the starting and stopping of commands and command pipelines and security exceptions in command discovery.</span></span> <span data-ttu-id="be860-313">De standaard instelling is `$false` (niet geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="be860-313">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="be860-314">`$LogEngineHealthEvent`: Registreert fouten en fouten van sessies.</span><span class="sxs-lookup"><span data-stu-id="be860-314">`$LogEngineHealthEvent`: Logs errors and failures of sessions.</span></span> <span data-ttu-id="be860-315">De standaard instelling is `$true` (geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="be860-315">The default is `$true` (logged).</span></span>
- <span data-ttu-id="be860-316">`$LogEngineLifecycleEvent`: Hiermee wordt het openen en sluiten van sessies geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="be860-316">`$LogEngineLifecycleEvent`: Logs the opening and closing of sessions.</span></span> <span data-ttu-id="be860-317">De standaard instelling is `$true` (geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="be860-317">The default is `$true` (logged).</span></span>
- <span data-ttu-id="be860-318">`$LogProviderHealthEvent`: Registreert provider fouten, zoals lees-en schrijf fouten, zoek fouten en aanroep fouten.</span><span class="sxs-lookup"><span data-stu-id="be860-318">`$LogProviderHealthEvent`: Logs provider errors, such as read and write errors, lookup errors, and invocation errors.</span></span> <span data-ttu-id="be860-319">De standaard instelling is `$true` (geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="be860-319">The default is `$true` (logged).</span></span>
- <span data-ttu-id="be860-320">`$LogProviderLifecycleEvent`: Logboeken voor het toevoegen en verwijderen van Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="be860-320">`$LogProviderLifecycleEvent`: Logs adding and removing of PowerShell providers.</span></span> <span data-ttu-id="be860-321">De standaard instelling is `$true` (geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="be860-321">The default is `$true` (logged).</span></span> <span data-ttu-id="be860-322">Zie [about_Providers](about_Providers.md)voor meer informatie over Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="be860-322">For information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

<span data-ttu-id="be860-323">Als u een **logboek \* gebeurtenis** wilt inschakelen, typt u de variabele met een waarde van `$true` , bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="be860-323">To enable a **Log\*Event** , type the variable with a value of `$true`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="be860-324">Als u een gebeurtenis type wilt uitschakelen, typt u de variabele met een waarde van `$false` , bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="be860-324">To disable an event type, type the variable with a value of `$false`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $false
```

<span data-ttu-id="be860-325">De gebeurtenissen die u inschakelt, zijn alleen geldig voor de huidige Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="be860-325">The events that you enable are effective only for the current PowerShell console.</span></span> <span data-ttu-id="be860-326">Sla de instellingen van de variabele op in uw Power shell-profiel om de configuratie toe te passen op alle-consoles.</span><span class="sxs-lookup"><span data-stu-id="be860-326">To apply the configuration to all consoles, save the variable settings in your PowerShell profile.</span></span> <span data-ttu-id="be860-327">Zie [about_Profiles](about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-327">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="be860-328">\$MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="be860-328">\$MaximumHistoryCount</span></span>

<span data-ttu-id="be860-329">Hiermee wordt bepaald hoeveel opdrachten worden opgeslagen in de opdracht geschiedenis van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-329">Determines how many commands are saved in the command history for the current session.</span></span>

<span data-ttu-id="be860-330">**Geldige waarden** : 1-32768 ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="be860-330">**Valid values** : 1 - 32768 (`Int32`)</span></span>

<span data-ttu-id="be860-331">**Standaard** : 4096</span><span class="sxs-lookup"><span data-stu-id="be860-331">**Default** : 4096</span></span>

<span data-ttu-id="be860-332">Om het aantal opdrachten te bepalen dat op het moment van de opdracht geschiedenis is opgeslagen, typt u:</span><span class="sxs-lookup"><span data-stu-id="be860-332">To determine the number of commands current saved in the command history, type:</span></span>

```powershell
(Get-History).Count
```

<span data-ttu-id="be860-333">Voor een overzicht van de opdrachten die zijn opgeslagen in de sessie geschiedenis, gebruikt u de `Get-History` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be860-333">To see the commands saved in your session history, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="be860-334">Zie [about_History](about_History.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-334">For more information, see [about_History](about_History.md).</span></span>

### <a name="ofs"></a><span data-ttu-id="be860-335">\$OFS</span><span class="sxs-lookup"><span data-stu-id="be860-335">\$OFS</span></span>

<span data-ttu-id="be860-336">Het OFS (output field separator) geeft het teken aan waarmee de elementen van een matrix worden gescheiden die naar een teken reeks worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="be860-336">The Output Field Separator (OFS) specifies the character that separates the elements of an array that is converted to a string.</span></span>

<span data-ttu-id="be860-337">**Geldige waarden** : een wille keurige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="be860-337">**Valid values** : Any string.</span></span>

<span data-ttu-id="be860-338">**Standaard** : ruimte</span><span class="sxs-lookup"><span data-stu-id="be860-338">**Default** : Space</span></span>

<span data-ttu-id="be860-339">De `$OFS` variabele bestaat standaard niet en het scheidings teken van het uitvoer bestand is een spatie, maar u kunt deze variabele toevoegen en instellen op een wille keurige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="be860-339">By default, the `$OFS` variable doesn't exist and the output file separator is a space, but you can add this variable and set it to any string.</span></span> <span data-ttu-id="be860-340">U kunt de waarde van `$OFS` in uw sessie wijzigen door te typen `$OFS="<value>"` .</span><span class="sxs-lookup"><span data-stu-id="be860-340">You can change the value of `$OFS` in your session, by typing `$OFS="<value>"`.</span></span>

> [!NOTE]
> <span data-ttu-id="be860-341">Als u de standaard waarde van een spatie ( `" "` ) in uw script, module of configuratie-uitvoer verwacht, moet u ervoor zorgen dat de `$OFS` standaard waarde niet elders in de code is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="be860-341">If you're expecting the default value of a space (`" "`) in your script, module, or configuration output, be careful that the `$OFS` default value hasn't been changed elsewhere in your code.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-342">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-342">Examples</span></span>

<span data-ttu-id="be860-343">In dit voor beeld ziet u dat er een spatie wordt gebruikt om de waarden te scheiden wanneer een matrix wordt geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="be860-343">This example shows that a space is used to separate the values when an array is converted to a string.</span></span> <span data-ttu-id="be860-344">In dit geval wordt een matrix met gehele getallen in een variabele opgeslagen en vervolgens wordt de variabele als een teken reeks gecast.</span><span class="sxs-lookup"><span data-stu-id="be860-344">In this case, an array of integers is stored in a variable and then the variable is cast as a string.</span></span>

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

<span data-ttu-id="be860-345">Als u het scheidings teken wilt wijzigen, voegt `$OFS` u de variabele toe door er een waarde aan toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="be860-345">To change the separator, add the `$OFS` variable by assigning a value to it.</span></span>
<span data-ttu-id="be860-346">De variabele moet een naam hebben `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="be860-346">The variable must be named `$OFS`.</span></span>

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

<span data-ttu-id="be860-347">Als u het standaard gedrag wilt herstellen, kunt u een spatie ( `" "` ) toewijzen aan de waarde van `$OFS` of de variabele verwijderen.</span><span class="sxs-lookup"><span data-stu-id="be860-347">To restore the default behavior, you can assign a space (`" "`) to the value of `$OFS` or delete the variable.</span></span> <span data-ttu-id="be860-348">Met de volgende opdrachten verwijdert u de variabele en controleert u of het scheidings teken een spatie is.</span><span class="sxs-lookup"><span data-stu-id="be860-348">The following commands delete the variable and then verify that the separator is a space.</span></span>

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a><span data-ttu-id="be860-349">\$OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="be860-349">\$OutputEncoding</span></span>

<span data-ttu-id="be860-350">Bepaalt de teken coderings methode die Power shell gebruikt bij het verzenden van tekst naar andere toepassingen.</span><span class="sxs-lookup"><span data-stu-id="be860-350">Determines the character encoding method that PowerShell uses when it sends text to other applications.</span></span>

<span data-ttu-id="be860-351">Als een toepassing bijvoorbeeld Unicode-teken reeksen retourneert naar Power shell, moet u de waarde mogelijk wijzigen in **UnicodeEncoding** om de tekens correct te verzenden.</span><span class="sxs-lookup"><span data-stu-id="be860-351">For example, if an application returns Unicode strings to PowerShell, you might need to change the value to **UnicodeEncoding** to send the characters correctly.</span></span>

<span data-ttu-id="be860-352">De geldige waarden zijn als volgt: objecten die zijn afgeleid van een coderings klasse, zoals **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** en **UnicodeEncoding**.</span><span class="sxs-lookup"><span data-stu-id="be860-352">The valid values are as follows: Objects derived from an Encoding class, such as **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** , and **UnicodeEncoding**.</span></span>

<span data-ttu-id="be860-353">**Standaard** : UTF8Encoding-object (System. Text. UTF8Encoding)</span><span class="sxs-lookup"><span data-stu-id="be860-353">**Default** : UTF8Encoding object (System.Text.UTF8Encoding)</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-354">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-354">Examples</span></span>

<span data-ttu-id="be860-355">In dit voor beeld ziet u hoe u de Windows **findstr.exe** -opdracht in Power shell kunt gebruiken op een computer die is gelokaliseerd voor een taal die gebruikmaakt van Unicode-tekens, zoals Chinees.</span><span class="sxs-lookup"><span data-stu-id="be860-355">This example shows how to make the Windows **findstr.exe** command work in PowerShell on a computer that is localized for a language that uses Unicode characters, such as Chinese.</span></span>

<span data-ttu-id="be860-356">De eerste opdracht zoekt de waarde van `$OutputEncoding` .</span><span class="sxs-lookup"><span data-stu-id="be860-356">The first command finds the value of `$OutputEncoding`.</span></span> <span data-ttu-id="be860-357">Omdat de waarde een encoding-object is, wordt alleen de eigenschap **Encoding** naam weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-357">Because the value is an encoding object, display only its **EncodingName** property.</span></span>

```powershell
$OutputEncoding.EncodingName
```

<span data-ttu-id="be860-358">In dit voor beeld wordt een **findstr.exe** -opdracht gebruikt om te zoeken naar twee Chinese tekens die aanwezig zijn in het `Test.txt` bestand.</span><span class="sxs-lookup"><span data-stu-id="be860-358">In this example, a **findstr.exe** command is used to search for two Chinese characters that are present in the `Test.txt` file.</span></span> <span data-ttu-id="be860-359">Wanneer deze **findstr.exe** opdracht wordt uitgevoerd in de Windows-opdracht Prompt ( **cmd.exe** ), wordt in **findstr.exe** de tekens in het tekst bestand gevonden.</span><span class="sxs-lookup"><span data-stu-id="be860-359">When this **findstr.exe** command is run in the Windows Command Prompt ( **cmd.exe** ), **findstr.exe** finds the characters in the text file.</span></span> <span data-ttu-id="be860-360">Wanneer u echter dezelfde **findstr.exe** -opdracht uitvoert in Power shell, worden de tekens niet gevonden omdat de Power shell deze verzendt naar **findstr.exe** in ASCII-tekst, in plaats van in Unicode-tekst.</span><span class="sxs-lookup"><span data-stu-id="be860-360">However, when you run the same **findstr.exe** command in PowerShell, the characters aren't found because the PowerShell sends them to **findstr.exe** in ASCII text, instead of in Unicode text.</span></span>

```powershell
findstr <Unicode-characters>
```

<span data-ttu-id="be860-361">Als u de opdracht in Power shell wilt gebruiken, stelt u de waarde van `$OutputEncoding` in op de waarde van de eigenschap **OutputEncoding** van de-console, die is gebaseerd op de land instelling die voor Windows is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="be860-361">To make the command work in PowerShell, set the value of `$OutputEncoding` to the value of the **OutputEncoding** property of the console, that is based on the locale selected for Windows.</span></span> <span data-ttu-id="be860-362">Omdat **OutputEncoding** een statische eigenschap van de console is, gebruikt u dubbele punten ( `::` ) in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="be860-362">Because **OutputEncoding** is a static property of the console, use double-colons (`::`) in the command.</span></span>

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

<span data-ttu-id="be860-363">Nadat de code ring is gewijzigd, vindt de **findstr.exe** opdracht de Unicode-tekens.</span><span class="sxs-lookup"><span data-stu-id="be860-363">After the encoding change, the **findstr.exe** command finds the Unicode characters.</span></span>

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a><span data-ttu-id="be860-364">\$ProgressPreference</span><span class="sxs-lookup"><span data-stu-id="be860-364">\$ProgressPreference</span></span>

<span data-ttu-id="be860-365">Bepaalt hoe Power shell reageert op de voortgangs updates die zijn gegenereerd door een script, cmdlet of provider, zoals de voortgangs balken die worden gegenereerd door de cmdlet [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) .</span><span class="sxs-lookup"><span data-stu-id="be860-365">Determines how PowerShell responds to progress updates generated by a script, cmdlet, or provider, such as the progress bars generated by the [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet.</span></span>
<span data-ttu-id="be860-366">`Write-Progress`Met de cmdlet worden voortgangs balken gemaakt waarin de status van een opdracht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-366">The `Write-Progress` cmdlet creates progress bars that show a command's status.</span></span>

<span data-ttu-id="be860-367">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-367">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-368">**Stop** : de voortgangs balk wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-368">**Stop** : Doesn't display the progress bar.</span></span> <span data-ttu-id="be860-369">In plaats daarvan wordt er een fout bericht weer gegeven en wordt de uitvoering gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-369">Instead, it displays an error message and stops executing.</span></span>
- <span data-ttu-id="be860-370">**Query** : de voortgangs balk wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-370">**Inquire** : Doesn't display the progress bar.</span></span> <span data-ttu-id="be860-371">Vraagt om toestemming om door te gaan.</span><span class="sxs-lookup"><span data-stu-id="be860-371">Prompts for permission to continue.</span></span> <span data-ttu-id="be860-372">Als u met `Y` of beantwoordt `A` , wordt de voortgangs balk weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-372">If you reply with `Y` or `A`, it displays the progress bar.</span></span>
- <span data-ttu-id="be860-373">**Door gaan** : (standaard) Hiermee wordt de voortgangs balk weer gegeven en wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-373">**Continue** : (Default) Displays the progress bar and continues with execution.</span></span>
- <span data-ttu-id="be860-374">**SilentlyContinue** : de opdracht wordt uitgevoerd, maar de voortgangs balk wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-374">**SilentlyContinue** : Executes the command, but doesn't display the progress bar.</span></span>

### <a name="psemailserver"></a><span data-ttu-id="be860-375">\$PSEmailServer</span><span class="sxs-lookup"><span data-stu-id="be860-375">\$PSEmailServer</span></span>

<span data-ttu-id="be860-376">Hiermee geeft u de standaard-e-mail server op die wordt gebruikt voor het verzenden van e-mail berichten.</span><span class="sxs-lookup"><span data-stu-id="be860-376">Specifies the default e-mail server that is used to send email messages.</span></span> <span data-ttu-id="be860-377">Deze voorkeurs variabele wordt gebruikt door cmdlets die e-mail verzenden, zoals de cmdlet [Send-mail Message](xref:Microsoft.PowerShell.Utility.Send-MailMessage) .</span><span class="sxs-lookup"><span data-stu-id="be860-377">This preference variable is used by cmdlets that send email, such as the [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="be860-378">\$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="be860-378">\$PSDefaultParameterValues</span></span>

<span data-ttu-id="be860-379">Hiermee geeft u de standaard waarden voor de para meters van cmdlets en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="be860-379">Specifies default values for the parameters of cmdlets and advanced functions.</span></span>
<span data-ttu-id="be860-380">De waarde van `$PSDefaultParameterValues` is een hash-tabel waarbij de sleutel bestaat uit de naam van de cmdlet en de naam van de para meter, gescheiden door een dubbele punt ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="be860-380">The value of `$PSDefaultParameterValues` is a hash table where the key consists of the cmdlet name and parameter name separated by a colon (`:`).</span></span> <span data-ttu-id="be860-381">De waarde is een aangepaste standaard waarde die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="be860-381">The value is a custom default value that you specify.</span></span>

<span data-ttu-id="be860-382">`$PSDefaultParameterValues` is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be860-382">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="be860-383">Zie [about_Parameters_Default_Values](about_Parameters_Default_Values.md)voor meer informatie over deze voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-383">For more information about this preference variable, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="psmoduleautoloadingpreference"></a><span data-ttu-id="be860-384">\$PSModuleAutoloadingPreference</span><span class="sxs-lookup"><span data-stu-id="be860-384">\$PSModuleAutoloadingPreference</span></span>

<span data-ttu-id="be860-385">Hiermee wordt het automatisch importeren van modules in de sessie in-en uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be860-385">Enables and disables automatic importing of modules in the session.</span></span> <span data-ttu-id="be860-386">Dit **is de** standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="be860-386">**All** is the default.</span></span> <span data-ttu-id="be860-387">Ongeacht de waarde van de variabele kunt u [import-module](xref:Microsoft.PowerShell.Core.Import-Module) gebruiken om een module te importeren.</span><span class="sxs-lookup"><span data-stu-id="be860-387">Regardless of the variable's value, you can use [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) to import a module.</span></span>

<span data-ttu-id="be860-388">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="be860-388">Valid values are:</span></span>

- <span data-ttu-id="be860-389">**Alle** : modules worden automatisch geïmporteerd bij het eerste gebruik.</span><span class="sxs-lookup"><span data-stu-id="be860-389">**All** : Modules are imported automatically on first-use.</span></span> <span data-ttu-id="be860-390">Als u een module wilt importeren, kunt u elke opdracht in de module ophalen of gebruiken.</span><span class="sxs-lookup"><span data-stu-id="be860-390">To import a module, get or use any command in the module.</span></span> <span data-ttu-id="be860-391">Gebruik bijvoorbeeld `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="be860-391">For example, use `Get-Command`.</span></span>
- <span data-ttu-id="be860-392">**ModuleQualified** : modules worden alleen automatisch geïmporteerd wanneer een gebruiker de module-gekwalificeerde naam van een opdracht in de module gebruikt.</span><span class="sxs-lookup"><span data-stu-id="be860-392">**ModuleQualified** : Modules are imported automatically only when a user uses the module-qualified name of a command in the module.</span></span> <span data-ttu-id="be860-393">Als de gebruiker bijvoorbeeld typt, wordt `MyModule\MyCommand` de **MyModule** -module door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be860-393">For example, if the user types `MyModule\MyCommand`, PowerShell imports the **MyModule** module.</span></span>
- <span data-ttu-id="be860-394">**Geen** : het automatisch importeren van modules is uitgeschakeld in de sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-394">**None** : Automatic importing of modules is disabled in the session.</span></span> <span data-ttu-id="be860-395">Als u een module wilt importeren, gebruikt u de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be860-395">To import a module, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="be860-396">Zie [about_Modules](about_Modules.md)voor meer informatie over het automatisch importeren van modules.</span><span class="sxs-lookup"><span data-stu-id="be860-396">For more information about automatic importing of modules, see [about_Modules](about_Modules.md).</span></span>

### <a name="pssessionapplicationname"></a><span data-ttu-id="be860-397">\$PSSessionApplicationName</span><span class="sxs-lookup"><span data-stu-id="be860-397">\$PSSessionApplicationName</span></span>

<span data-ttu-id="be860-398">Hiermee geeft u de standaard toepassings naam voor een externe opdracht die gebruikmaakt van webservices voor beheer (WS-Management)-technologie.</span><span class="sxs-lookup"><span data-stu-id="be860-398">Specifies the default application name for a remote command that uses Web Services for Management (WS-Management) technology.</span></span> <span data-ttu-id="be860-399">Zie [about Windows Remote Management](/windows/win32/winrm/about-windows-remote-management)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-399">For more information, see [About Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span></span>

<span data-ttu-id="be860-400">De standaard naam van de systeem toepassing is `WSMAN` , maar u kunt deze voorkeurs variabele gebruiken om de standaard waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="be860-400">The system default application name is `WSMAN`, but you can use this preference variable to change the default.</span></span>

<span data-ttu-id="be860-401">De naam van de toepassing is het laatste knoop punt in een verbindings-URI.</span><span class="sxs-lookup"><span data-stu-id="be860-401">The application name is the last node in a connection URI.</span></span> <span data-ttu-id="be860-402">Bijvoorbeeld, de naam van de toepassing in de volgende voor beeld-URI is `WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="be860-402">For example, the application name in the following sample URI is `WSMAN`.</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="be860-403">De standaard naam van de toepassing wordt gebruikt wanneer met de externe opdracht geen verbindings-URI of een toepassings naam wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-403">The default application name is used when the remote command doesn't specify a connection URI or an application name.</span></span>

<span data-ttu-id="be860-404">De **WinRM** -service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="be860-404">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="be860-405">De waarde van de para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be860-405">The parameter's value should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

<span data-ttu-id="be860-406">Als u de standaard waarden van het systeem en de waarde van deze variabele wilt negeren en een andere toepassings naam voor een bepaalde sessie wilt selecteren, gebruikt u de para meters **ConnectionURI** of **ApplicationName** van de cmdlets [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)of [invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="be860-406">To override the system default and the value of this variable, and select a different application name for a particular session, use the **ConnectionURI** or **ApplicationName** parameters of the [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession), or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlets.</span></span>

<span data-ttu-id="be860-407">De `$PSSessionApplicationName` Voorkeurs variabele is ingesteld op de lokale computer, maar Hiermee wordt een listener op de externe computer opgegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-407">The `$PSSessionApplicationName` preference variable is set on the local computer, but it specifies a listener on the remote computer.</span></span> <span data-ttu-id="be860-408">Als de naam van de toepassing die u opgeeft niet bestaat op de externe computer, mislukt de opdracht voor het instellen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-408">If the application name that you specify doesn't exist on the remote computer, the command to establish the session fails.</span></span>

### <a name="pssessionconfigurationname"></a><span data-ttu-id="be860-409">\$PSSessionConfigurationName</span><span class="sxs-lookup"><span data-stu-id="be860-409">\$PSSessionConfigurationName</span></span>

<span data-ttu-id="be860-410">Hiermee geeft u de standaard sessie configuratie op die wordt gebruikt voor **PSSessions** die zijn gemaakt in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-410">Specifies the default session configuration that is used for **PSSessions** created in the current session.</span></span>

<span data-ttu-id="be860-411">Deze voorkeurs variabele is ingesteld op de lokale computer, maar Hiermee geeft u een sessie configuratie op die zich op de externe computer bevindt.</span><span class="sxs-lookup"><span data-stu-id="be860-411">This preference variable is set on the local computer, but it specifies a session configuration that's located on the remote computer.</span></span>

<span data-ttu-id="be860-412">De waarde van de `$PSSessionConfigurationName` variabele is een volledig gekwalificeerde resource-URI.</span><span class="sxs-lookup"><span data-stu-id="be860-412">The value of the `$PSSessionConfigurationName` variable is a fully qualified resource URI.</span></span>

<span data-ttu-id="be860-413">De standaard waarde `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` geeft de configuratie van de **micro soft. Power shell** -sessie op de externe computer aan.</span><span class="sxs-lookup"><span data-stu-id="be860-413">The default value `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indicates the **Microsoft.PowerShell** session configuration on the remote computer.</span></span>

<span data-ttu-id="be860-414">Als u alleen een configuratie naam opgeeft, wordt de volgende schema-URI voor het voor voegsel geplaatst:</span><span class="sxs-lookup"><span data-stu-id="be860-414">If you specify only a configuration name, the following schema URI is prepended:</span></span>

`http://schemas.microsoft.com/PowerShell/`

<span data-ttu-id="be860-415">U kunt de standaard instelling onderdrukken en een andere sessie configuratie voor een bepaalde sessie selecteren met behulp van de para meter **configuratiepad** van de `New-PSSession` `Enter-PSSession` `Invoke-Command` cmdlets, of.</span><span class="sxs-lookup"><span data-stu-id="be860-415">You can override the default and select a different session configuration for a particular session by using the **ConfigurationName** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="be860-416">U kunt de waarde van deze variabele op elk gewenst moment wijzigen.</span><span class="sxs-lookup"><span data-stu-id="be860-416">You can change the value of this variable at any time.</span></span> <span data-ttu-id="be860-417">Houd er rekening mee dat de door u geselecteerde sessie configuratie op de externe computer moet bestaan.</span><span class="sxs-lookup"><span data-stu-id="be860-417">When you do, remember that the session configuration that you select must exist on the remote computer.</span></span> <span data-ttu-id="be860-418">Als dat niet het geval is, mislukt de opdracht voor het maken van een sessie die gebruikmaakt van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="be860-418">If it doesn't, the command to create a session that uses the session configuration fails.</span></span>

<span data-ttu-id="be860-419">Met deze voorkeurs variabele kunt u niet bepalen welke lokale sessie configuraties worden gebruikt wanneer externe gebruikers een sessie maken die verbinding maakt met deze computer.</span><span class="sxs-lookup"><span data-stu-id="be860-419">This preference variable doesn't determine which local session configurations are used when remote users create a session that connects to this computer.</span></span>
<span data-ttu-id="be860-420">U kunt echter de machtigingen voor de lokale sessie configuraties gebruiken om te bepalen welke gebruikers ze mogen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="be860-420">However, you can use the permissions for the local session configurations to determine which users may use them.</span></span>

### <a name="pssessionoption"></a><span data-ttu-id="be860-421">\$PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="be860-421">\$PSSessionOption</span></span>

<span data-ttu-id="be860-422">Hiermee worden de standaard waarden voor geavanceerde gebruikers opties ingesteld in een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-422">Establishes the default values for advanced user options in a remote session.</span></span>
<span data-ttu-id="be860-423">Met deze optie Voorkeuren worden de standaard waarden van het systeem voor sessie opties genegeerd.</span><span class="sxs-lookup"><span data-stu-id="be860-423">These option preferences override the system default values for session options.</span></span>

<span data-ttu-id="be860-424">De `$PSSessionOption` variabele bevat een **PSSessionOption** -object.</span><span class="sxs-lookup"><span data-stu-id="be860-424">The `$PSSessionOption` variable contains a **PSSessionOption** object.</span></span> <span data-ttu-id="be860-425">Zie [System. Management. Automation. Remoting. PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-425">For more information, see [System.Management.Automation.Remoting.PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span></span>
<span data-ttu-id="be860-426">Elke eigenschap van het object vertegenwoordigt een sessie optie.</span><span class="sxs-lookup"><span data-stu-id="be860-426">Each property of the object represents a session option.</span></span> <span data-ttu-id="be860-427">De eigenschap ' niet **comprimeren** ' wordt bijvoorbeeld tijdens de sessie van gegevens compressie ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be860-427">For example, the **NoCompression** property turns of data compression during the session.</span></span>

<span data-ttu-id="be860-428">De `$PSSessionOption` variabele bevat standaard een **PSSessionOption** -object met de standaard waarden voor alle opties, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-428">By default, the `$PSSessionOption` variable contains a **PSSessionOption** object with the default values for all options, as shown below.</span></span>

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

<span data-ttu-id="be860-429">Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor een beschrijving van deze opties en meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-429">For descriptions of these options and more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span> <span data-ttu-id="be860-430">Zie [about_Remote](about_Remote.md) en [about_PSSessions](about_PSSessions.md)voor meer informatie over externe opdrachten en sessies.</span><span class="sxs-lookup"><span data-stu-id="be860-430">For more information about remote commands and sessions, see [about_Remote](about_Remote.md) and [about_PSSessions](about_PSSessions.md).</span></span>

<span data-ttu-id="be860-431">Als u de waarde van de `$PSSessionOption` Voorkeurs variabele wilt wijzigen, gebruikt `New-PSSessionOption` u de cmdlet om een **PSSessionOption** -object te maken met de optie waarden die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="be860-431">To change the value of the `$PSSessionOption` preference variable, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object with the option values you prefer.</span></span> <span data-ttu-id="be860-432">Sla de uitvoer op in een variabele met de naam `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="be860-432">Save the output in a variable called `$PSSessionOption`.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

<span data-ttu-id="be860-433">Als u de `$PSSessionOption` Voorkeurs variabele in elke Power shell-sessie wilt gebruiken, voegt u een `New-PSSessionOption` opdracht toe waarmee de variabele wordt gemaakt in `$PSSessionOption` uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="be860-433">To use the `$PSSessionOption` preference variable in every PowerShell session, add a `New-PSSessionOption` command that creates the `$PSSessionOption` variable to your PowerShell profile.</span></span> <span data-ttu-id="be860-434">Zie [about_Profiles](about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-434">For more information, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="be860-435">U kunt aangepaste opties instellen voor een bepaalde externe sessie.</span><span class="sxs-lookup"><span data-stu-id="be860-435">You can set custom options for a particular remote session.</span></span> <span data-ttu-id="be860-436">De opties die u instelt, hebben voor rang op de standaard waarden van het systeem en de waarde van de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-436">The options that you set take precedence over the system defaults and the value of the `$PSSessionOption` preference variable.</span></span>

<span data-ttu-id="be860-437">Als u aangepaste sessie opties wilt instellen, gebruikt u de `New-PSSessionOption` cmdlet om een **PSSessionOption** -object te maken.</span><span class="sxs-lookup"><span data-stu-id="be860-437">To set custom session options, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object.</span></span> <span data-ttu-id="be860-438">Gebruik vervolgens het object **PSSessionOption** als de waarde van de para meter **SessionOption** in cmdlets die een sessie maken, zoals `New-PSSession` , `Enter-PSSession` , en `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="be860-438">Then, use the **PSSessionOption** object as the value of the **SessionOption** parameter in cmdlets that create a session, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

### <a name="transcript"></a><span data-ttu-id="be860-439">$Transcript</span><span class="sxs-lookup"><span data-stu-id="be860-439">$Transcript</span></span>

<span data-ttu-id="be860-440">Wordt gebruikt door `Start-Transcript` om de naam en locatie van het transcript-bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="be860-440">Used by `Start-Transcript` to specify the name and location of the transcript file.</span></span> <span data-ttu-id="be860-441">Als u geen waarde opgeeft voor de para meter **Path** , `Start-Transcript` wordt het pad gebruikt in de waarde van de `$Transcript` globale variabele.</span><span class="sxs-lookup"><span data-stu-id="be860-441">If you do not specify a value for the **Path** parameter, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="be860-442">Als u deze variabele niet hebt gemaakt, `Start-Transcript` slaat de transcripten in de `$Home\My Documents` map op als `\PowerShell_transcript.<time-stamp>.txt` bestanden.</span><span class="sxs-lookup"><span data-stu-id="be860-442">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents` directory as `\PowerShell_transcript.<time-stamp>.txt` files.</span></span>

### <a name="verbosepreference"></a><span data-ttu-id="be860-443">\$VerbosePreference</span><span class="sxs-lookup"><span data-stu-id="be860-443">\$VerbosePreference</span></span>

<span data-ttu-id="be860-444">Bepaalt hoe Power shell reageert op uitgebreide berichten die zijn gegenereerd door een script, cmdlet of provider, zoals de berichten die door de cmdlet [Write-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="be860-444">Determines how PowerShell responds to verbose messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet.</span></span>
<span data-ttu-id="be860-445">Uitgebreide berichten beschrijven de acties die worden uitgevoerd om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="be860-445">Verbose messages describe the actions performed to execute a command.</span></span>

<span data-ttu-id="be860-446">Standaard worden uitgebreide berichten niet weer gegeven, maar u kunt dit gedrag wijzigen door de waarde van te wijzigen `$VerbosePreference` .</span><span class="sxs-lookup"><span data-stu-id="be860-446">By default, verbose messages aren't displayed, but you can change this behavior by changing the value of `$VerbosePreference`.</span></span>

<span data-ttu-id="be860-447">U kunt de **uitgebreide** algemene para meter van een cmdlet gebruiken om de uitgebreide berichten voor een specifieke opdracht weer te geven of te verbergen.</span><span class="sxs-lookup"><span data-stu-id="be860-447">You can use the **Verbose** common parameter of a cmdlet to display or hide the verbose messages for a specific command.</span></span> <span data-ttu-id="be860-448">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-448">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="be860-449">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-449">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-450">**Stoppen** : Hiermee wordt het uitgebreide bericht en een fout bericht weer gegeven en wordt de uitvoering gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-450">**Stop** : Displays the verbose message and an error message and then stops executing.</span></span>
- <span data-ttu-id="be860-451">**Query** : Hiermee wordt het uitgebreide bericht weer gegeven en wordt er een prompt weer gegeven waarin u wordt gevraagd of u wilt door gaan.</span><span class="sxs-lookup"><span data-stu-id="be860-451">**Inquire** : Displays the verbose message and then displays a prompt that asks you whether you want to continue.</span></span>
- <span data-ttu-id="be860-452">**Door gaan** : Hiermee wordt het uitgebreide bericht weer gegeven en wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-452">**Continue** : Displays the verbose message and then continues with execution.</span></span>
- <span data-ttu-id="be860-453">**SilentlyContinue** : (standaard) geeft het uitgebreide bericht niet weer.</span><span class="sxs-lookup"><span data-stu-id="be860-453">**SilentlyContinue** : (Default) Doesn't display the verbose message.</span></span> <span data-ttu-id="be860-454">Gaat verder met uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="be860-454">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-455">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-455">Examples</span></span>

<span data-ttu-id="be860-456">In deze voor beelden ziet u het effect van de verschillende waarden van `$VerbosePreference` en de **uitgebreide** para meter om de voorkeurs waarde te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="be860-456">These examples show the effect of the different values of `$VerbosePreference` and the **Verbose** parameter to override the preference value.</span></span>

<span data-ttu-id="be860-457">In dit voor beeld ziet u het effect van de **SilentlyContinue** -waarde. Dit is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="be860-457">This example shows the effect of the **SilentlyContinue** value, that is the default.</span></span> <span data-ttu-id="be860-458">De opdracht gebruikt de para meter **bericht** , maar schrijft geen bericht naar de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="be860-458">The command uses the **Message** parameter, but doesn't write a message to the PowerShell console.</span></span>

```powershell
Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="be860-459">Wanneer de **uitgebreide** para meter wordt gebruikt, wordt het bericht geschreven.</span><span class="sxs-lookup"><span data-stu-id="be860-459">When the **Verbose** parameter is used, the message is written.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="be860-460">In dit voor beeld ziet u het effect van de waarde **continue** .</span><span class="sxs-lookup"><span data-stu-id="be860-460">This example shows the effect of the **Continue** value.</span></span> <span data-ttu-id="be860-461">De `$VerbosePreference` variabele is ingesteld om **door te gaan** en het bericht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-461">The `$VerbosePreference` variable is set to **Continue** and the message is displayed.</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="be860-462">In dit voor beeld wordt de **uitgebreide** para meter met de waarde van `$false` vervangen door de waarde **continue** .</span><span class="sxs-lookup"><span data-stu-id="be860-462">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Continue** value.</span></span> <span data-ttu-id="be860-463">Het bericht wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-463">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="be860-464">In dit voor beeld wordt het effect van de waarde **Stop** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-464">This example shows the effect of the **Stop** value.</span></span> <span data-ttu-id="be860-465">De `$VerbosePreference` variabele wordt ingesteld op **stoppen** en het bericht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-465">The `$VerbosePreference` variable is set to **Stop** and the message is displayed.</span></span> <span data-ttu-id="be860-466">De opdracht is gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-466">The command is stopped.</span></span>

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="be860-467">In dit voor beeld wordt de para meter **uitgebreid** gebruikt met de waarde `$false` die de **Stop** waarde overschrijft.</span><span class="sxs-lookup"><span data-stu-id="be860-467">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Stop** value.</span></span> <span data-ttu-id="be860-468">Het bericht wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-468">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="be860-469">In dit voor beeld ziet u het effect van de waarde van de **query** .</span><span class="sxs-lookup"><span data-stu-id="be860-469">This example shows the effect of the **Inquire** value.</span></span> <span data-ttu-id="be860-470">De `$VerbosePreference` variabele is ingesteld op **query's**.</span><span class="sxs-lookup"><span data-stu-id="be860-470">The `$VerbosePreference` variable is set to **Inquire**.</span></span> <span data-ttu-id="be860-471">Het bericht wordt weer gegeven en de gebruiker wordt om bevestiging gevraagd.</span><span class="sxs-lookup"><span data-stu-id="be860-471">The message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="be860-472">In dit voor beeld wordt de **uitgebreide** para meter met de waarde van `$false` vervangen door de waarde van de **query** .</span><span class="sxs-lookup"><span data-stu-id="be860-472">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Inquire** value.</span></span> <span data-ttu-id="be860-473">De gebruiker wordt niet gevraagd en het bericht wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-473">The user isn't prompted and the message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a><span data-ttu-id="be860-474">\$WarningPreference</span><span class="sxs-lookup"><span data-stu-id="be860-474">\$WarningPreference</span></span>

<span data-ttu-id="be860-475">Bepaalt hoe Power shell reageert op waarschuwings berichten die worden gegenereerd door een script, cmdlet of provider, zoals de berichten die worden gegenereerd door de cmdlet [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) .</span><span class="sxs-lookup"><span data-stu-id="be860-475">Determines how PowerShell responds to warning messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet.</span></span>

<span data-ttu-id="be860-476">Standaard worden waarschuwings berichten weer gegeven en de uitvoering wordt voortgezet, maar u kunt dit gedrag wijzigen door de waarde van te wijzigen `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="be860-476">By default, warning messages are displayed and execution continues, but you can change this behavior by changing the value of `$WarningPreference`.</span></span>

<span data-ttu-id="be860-477">U kunt de algemene para meter **WarningAction** van een cmdlet gebruiken om te bepalen hoe Power shell reageert op waarschuwingen van een bepaalde opdracht.</span><span class="sxs-lookup"><span data-stu-id="be860-477">You can use the **WarningAction** common parameter of a cmdlet to determine how PowerShell responds to warnings from a particular command.</span></span> <span data-ttu-id="be860-478">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be860-478">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="be860-479">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-479">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-480">**Stoppen** : Hiermee wordt het waarschuwings bericht en een fout bericht weer gegeven en wordt de uitvoering gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-480">**Stop** : Displays the warning message and an error message and then stops executing.</span></span>
- <span data-ttu-id="be860-481">**Query** : geeft het waarschuwings bericht weer en vraagt om toestemming om door te gaan.</span><span class="sxs-lookup"><span data-stu-id="be860-481">**Inquire** : Displays the warning message and then prompts for permission to continue.</span></span>
- <span data-ttu-id="be860-482">**Door gaan** : (standaard) Hiermee wordt het waarschuwings bericht weer gegeven en wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="be860-482">**Continue** : (Default) Displays the warning message and then continues executing.</span></span>
- <span data-ttu-id="be860-483">**SilentlyContinue** : het waarschuwings bericht wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-483">**SilentlyContinue** : Doesn't display the warning message.</span></span> <span data-ttu-id="be860-484">Gaat verder met uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="be860-484">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-485">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-485">Examples</span></span>

<span data-ttu-id="be860-486">In deze voor beelden ziet u het effect van de verschillende waarden van `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="be860-486">These examples show the effect of the different values of `$WarningPreference`.</span></span>
<span data-ttu-id="be860-487">De para meter **WarningAction** overschrijft de voorkeurs waarde.</span><span class="sxs-lookup"><span data-stu-id="be860-487">The **WarningAction** parameter overrides the preference value.</span></span>

<span data-ttu-id="be860-488">In dit voor **beeld wordt het** effect van de standaard waarde weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-488">This example shows the effect of the default value, **Continue**.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

<span data-ttu-id="be860-489">In dit voor beeld wordt de para meter **WarningAction** gebruikt met de waarde **SilentlyContinue** om de waarschuwing te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="be860-489">This example uses the **WarningAction** parameter with the value **SilentlyContinue** to suppress the warning.</span></span> <span data-ttu-id="be860-490">Het bericht wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-490">The message isn't displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="be860-491">In dit voor beeld wordt de `$WarningPreference` variabele gewijzigd in de waarde **SilentlyContinue** .</span><span class="sxs-lookup"><span data-stu-id="be860-491">This example changes the `$WarningPreference` variable to the **SilentlyContinue** value.</span></span> <span data-ttu-id="be860-492">Het bericht wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-492">The message isn't displayed.</span></span>

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

<span data-ttu-id="be860-493">In dit voor beeld wordt de para meter **WarningAction** gebruikt om te stoppen wanneer een waarschuwing wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="be860-493">This example uses the **WarningAction** parameter to stop when a warning is generated.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

<span data-ttu-id="be860-494">In dit voor beeld wordt de `$WarningPreference` variabele gewijzigd in de **query** waarde.</span><span class="sxs-lookup"><span data-stu-id="be860-494">This example changes the `$WarningPreference` variable to the **Inquire** value.</span></span> <span data-ttu-id="be860-495">De gebruiker wordt gevraagd om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="be860-495">The user is prompted for confirmation.</span></span>

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="be860-496">In dit voor beeld wordt de para meter **WarningAction** gebruikt met de waarde **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="be860-496">This example uses the **WarningAction** parameter with the value **SilentlyContinue**.</span></span> <span data-ttu-id="be860-497">De opdracht blijft uitvoeren en er wordt geen bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-497">The command continues to execute and no message is displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="be860-498">In dit voor beeld wordt de `$WarningPreference` te **stoppen** waarde gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="be860-498">This example changes the `$WarningPreference` value to **Stop**.</span></span>

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

<span data-ttu-id="be860-499">In dit voor beeld wordt de **WarningAction** gebruikt met de **query** waarde.</span><span class="sxs-lookup"><span data-stu-id="be860-499">This example uses the **WarningAction** with the **Inquire** value.</span></span> <span data-ttu-id="be860-500">De gebruiker wordt gevraagd wanneer een waarschuwing wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-500">The user is prompted when a warning occurs.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a><span data-ttu-id="be860-501">\$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="be860-501">\$WhatIfPreference</span></span>

<span data-ttu-id="be860-502">Hiermee wordt bepaald of **WhatIf** automatisch wordt ingeschakeld voor elke opdracht die het ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="be860-502">Determines whether **WhatIf** is automatically enabled for every command that supports it.</span></span> <span data-ttu-id="be860-503">Wanneer **WhatIf** is ingeschakeld, rapporteert de cmdlet het verwachte effect van de opdracht, maar voert de-opdracht niet uit.</span><span class="sxs-lookup"><span data-stu-id="be860-503">When **WhatIf** is enabled, the cmdlet reports the expected effect of the command, but doesn't execute the command.</span></span>

<span data-ttu-id="be860-504">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="be860-504">The valid values are as follows:</span></span>

- <span data-ttu-id="be860-505">**False** ( **0** , niet ingeschakeld): (standaard) **WhatIf** is niet automatisch ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be860-505">**False** ( **0** , not enabled): (Default) **WhatIf** isn't automatically enabled.</span></span> <span data-ttu-id="be860-506">Als u deze hand matig wilt inschakelen, gebruikt u de para meter **WhatIf** van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be860-506">To enable it manually, use the cmdlet's **WhatIf** parameter.</span></span>
- <span data-ttu-id="be860-507">**True** ( **1** , ingeschakeld): **WhatIf** wordt automatisch ingeschakeld voor alle opdrachten die dit ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="be860-507">**True** ( **1** , enabled): **WhatIf** is automatically enabled on any command that supports it.</span></span> <span data-ttu-id="be860-508">Gebruikers kunnen de para meter **WhatIf** gebruiken met de waarde **False** om deze hand matig uit te scha kelen, zoals `-WhatIf:$false` .</span><span class="sxs-lookup"><span data-stu-id="be860-508">Users can use the **WhatIf** parameter with a value of **False** to disable it manually, such as `-WhatIf:$false`.</span></span>

#### <a name="examples"></a><span data-ttu-id="be860-509">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="be860-509">Examples</span></span>

<span data-ttu-id="be860-510">In deze voor beelden ziet u het effect van de verschillende waarden van `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="be860-510">These examples show the effect of the different values of `$WhatIfPreference`.</span></span>
<span data-ttu-id="be860-511">Ze laten zien hoe u de para meter **WhatIf** kunt gebruiken om de voorkeurs waarde voor een specifieke opdracht te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="be860-511">They show how to use the **WhatIf** parameter to override the preference value for a specific command.</span></span>

<span data-ttu-id="be860-512">In dit voor beeld wordt het effect van de `$WhatIfPreference` variabele ingesteld op de standaard waarde, **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="be860-512">This example shows the effect of the `$WhatIfPreference` variable set to the default value, **False**.</span></span> <span data-ttu-id="be860-513">Gebruiken `Get-ChildItem` om te controleren of het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="be860-513">Use `Get-ChildItem` to verify that the file exists.</span></span>
<span data-ttu-id="be860-514">`Remove-Item` Hiermee verwijdert u het bestand.</span><span class="sxs-lookup"><span data-stu-id="be860-514">`Remove-Item` deletes the file.</span></span> <span data-ttu-id="be860-515">Nadat het bestand is verwijderd, kunt u de verwijdering controleren met `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="be860-515">After the file is deleted, you can verify the deletion with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

<span data-ttu-id="be860-516">In dit voor beeld ziet u het effect van het gebruik van de para meter **WhatIf** wanneer de waarde van is ingesteld op `$WhatIfPreference` **False**.</span><span class="sxs-lookup"><span data-stu-id="be860-516">This example shows the effect of using the **WhatIf** parameter when the value of `$WhatIfPreference` is **False**.</span></span>

<span data-ttu-id="be860-517">Controleer of het bestand bestaat.</span><span class="sxs-lookup"><span data-stu-id="be860-517">Verify that the file exists.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="be860-518">Gebruik de para meter **WhatIf** om het resultaat van de poging om het bestand te verwijderen te bepalen.</span><span class="sxs-lookup"><span data-stu-id="be860-518">Use the **WhatIf** parameter to determine the result of attempting to delete the file.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

<span data-ttu-id="be860-519">Controleer of het bestand niet is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="be860-519">Verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="be860-520">In dit voor beeld ziet u het effect van de `$WhatIfPreference` variabele die is ingesteld op de waarde **True**.</span><span class="sxs-lookup"><span data-stu-id="be860-520">This example shows the effect of the `$WhatIfPreference` variable set to the value, **True**.</span></span> <span data-ttu-id="be860-521">Wanneer u gebruikt `Remove-Item` om een bestand te verwijderen, wordt het pad van het bestand weer gegeven, maar wordt het bestand niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="be860-521">When you use `Remove-Item` to delete a file, the file's path is displayed, but the file isn't deleted.</span></span>

<span data-ttu-id="be860-522">Poging een bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="be860-522">Attempt to delete a file.</span></span> <span data-ttu-id="be860-523">Er wordt een bericht weer gegeven over wat er zou gebeuren als `Remove-Item` het programma werd uitgevoerd, maar het bestand wordt niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="be860-523">A message is displayed about what would happen if `Remove-Item` was run, but the file isn't deleted.</span></span>

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

<span data-ttu-id="be860-524">Gebruiken `Get-ChildItem` om te controleren of het bestand niet is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="be860-524">Use `Get-ChildItem` to verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="be860-525">In dit voor beeld ziet u hoe u een bestand verwijdert wanneer de waarde van is ingesteld op `$WhatIfPreference` **True**.</span><span class="sxs-lookup"><span data-stu-id="be860-525">This example shows how to delete a file when the value of `$WhatIfPreference` is **True**.</span></span> <span data-ttu-id="be860-526">De para meter **WhatIf** wordt gebruikt met de waarde `$false` .</span><span class="sxs-lookup"><span data-stu-id="be860-526">It uses the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="be860-527">Gebruiken `Get-ChildItem` om te controleren of het bestand is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="be860-527">Use `Get-ChildItem` to verify the file was deleted.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

<span data-ttu-id="be860-528">Hier volgen enkele voor beelden van de `Get-Process` cmdlet die geen ondersteuning biedt voor **WhatIf** en `Stop-Process` die **WhatIf** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="be860-528">The following are examples of the `Get-Process` cmdlet that doesn't support **WhatIf** and `Stop-Process` that does support **WhatIf**.</span></span> <span data-ttu-id="be860-529">De `$WhatIfPreference` waarde van de variabele is **waar**.</span><span class="sxs-lookup"><span data-stu-id="be860-529">The `$WhatIfPreference` variable's value is **True**.</span></span>

<span data-ttu-id="be860-530">`Get-Process` biedt geen ondersteuning voor **WhatIf**.</span><span class="sxs-lookup"><span data-stu-id="be860-530">`Get-Process` doesn't support **WhatIf**.</span></span> <span data-ttu-id="be860-531">Wanneer de opdracht wordt uitgevoerd, wordt het **Winword** -proces weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be860-531">When the command is executed, it displays the **Winword** process.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

<span data-ttu-id="be860-532">`Stop-Process` biedt ondersteuning voor **WhatIf**.</span><span class="sxs-lookup"><span data-stu-id="be860-532">`Stop-Process` does support **WhatIf**.</span></span> <span data-ttu-id="be860-533">Het **Winword** -proces is niet gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-533">The **Winword** process isn't stopped.</span></span>

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

<span data-ttu-id="be860-534">U kunt het `Stop-Process` gedrag van de **WhatIf** negeren door de para meter **WhatIf** te gebruiken met de waarde `$false` .</span><span class="sxs-lookup"><span data-stu-id="be860-534">You can override the `Stop-Process` **WhatIf** behavior by using the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="be860-535">Het **Winword** -proces is gestopt.</span><span class="sxs-lookup"><span data-stu-id="be860-535">The **Winword** process is stopped.</span></span>

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

<span data-ttu-id="be860-536">Gebruik om te controleren of het proces **Winword** is gestopt `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="be860-536">To verify that the **Winword** process was stopped, use `Get-Process`.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a><span data-ttu-id="be860-537">Zie ook</span><span class="sxs-lookup"><span data-stu-id="be860-537">See also</span></span>

[<span data-ttu-id="be860-538">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="be860-538">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="be860-539">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be860-539">about_CommonParameters</span></span>](about_CommonParameters.md)

[<span data-ttu-id="be860-540">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="be860-540">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="be860-541">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="be860-541">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="be860-542">about_Remote</span><span class="sxs-lookup"><span data-stu-id="be860-542">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="be860-543">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="be860-543">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="be860-544">about_Variables</span><span class="sxs-lookup"><span data-stu-id="be860-544">about_Variables</span></span>](about_Variables.md)
