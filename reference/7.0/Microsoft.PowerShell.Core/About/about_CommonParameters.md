---
description: Hierin worden de para meters beschreven die kunnen worden gebruikt met een wille keurige cmdlet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 949fabca6052a75d2cc4f8cf71e0a88b170a3b36
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252509"
---
# <a name="about-commonparameters"></a><span data-ttu-id="8ac41-104">Over CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ac41-104">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="8ac41-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8ac41-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="8ac41-106">Hierin worden de para meters beschreven die kunnen worden gebruikt met een wille keurige cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ac41-106">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="8ac41-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8ac41-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8ac41-108">De algemene para meters zijn een set cmdlet-para meters die u met een wille keurige cmdlet kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8ac41-108">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="8ac41-109">Ze worden geïmplementeerd door Power shell, niet door de cmdlet-ontwikkelaar en ze zijn automatisch beschikbaar voor alle cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8ac41-109">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="8ac41-110">U kunt de algemene para meters voor elke cmdlet gebruiken, maar ze hebben mogelijk geen invloed op alle cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8ac41-110">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="8ac41-111">Als een cmdlet bijvoorbeeld geen uitgebreide uitvoer genereert, heeft het gebruik van de **uitgebreide** para meter algemeen geen effect.</span><span class="sxs-lookup"><span data-stu-id="8ac41-111">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="8ac41-112">De algemene para meters zijn ook beschikbaar voor geavanceerde functies die gebruikmaken van het kenmerk **CmdletBinding** of het **parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="8ac41-112">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="8ac41-113">Verschillende algemene para meters overschrijven systeem standaarden of voor keuren die u instelt met behulp van de voorkeurs variabelen van Power shell.</span><span class="sxs-lookup"><span data-stu-id="8ac41-113">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="8ac41-114">In tegens telling tot de voorkeurs variabelen zijn de algemene para meters alleen van invloed op de opdrachten waarin ze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-114">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="8ac41-115">Zie [about_Preference_Variables](./about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-115">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="8ac41-116">De volgende lijst geeft de algemene para meters weer.</span><span class="sxs-lookup"><span data-stu-id="8ac41-116">The following list displays the common parameters.</span></span> <span data-ttu-id="8ac41-117">Hun aliassen worden tussen haakjes weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8ac41-117">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="8ac41-118">**Debug** (DB)</span><span class="sxs-lookup"><span data-stu-id="8ac41-118">**Debug** (db)</span></span>
- <span data-ttu-id="8ac41-119">**Error Action** (EA)</span><span class="sxs-lookup"><span data-stu-id="8ac41-119">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="8ac41-120">**ErrorVariable** (EV)</span><span class="sxs-lookup"><span data-stu-id="8ac41-120">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="8ac41-121">**Information Action** (infa)</span><span class="sxs-lookup"><span data-stu-id="8ac41-121">**InformationAction** (infa)</span></span>
- <span data-ttu-id="8ac41-122">**InformationVariable** (IV)</span><span class="sxs-lookup"><span data-stu-id="8ac41-122">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="8ac41-123">**Outvariable** (ov)</span><span class="sxs-lookup"><span data-stu-id="8ac41-123">**OutVariable** (ov)</span></span>
- <span data-ttu-id="8ac41-124">**Outbuffer** (Ob)</span><span class="sxs-lookup"><span data-stu-id="8ac41-124">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="8ac41-125">**PipelineVariable** (PV)</span><span class="sxs-lookup"><span data-stu-id="8ac41-125">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="8ac41-126">**Uitgebreid** (VB)</span><span class="sxs-lookup"><span data-stu-id="8ac41-126">**Verbose** (vb)</span></span>
- <span data-ttu-id="8ac41-127">**WarningAction** (WA)</span><span class="sxs-lookup"><span data-stu-id="8ac41-127">**WarningAction** (wa)</span></span>
- <span data-ttu-id="8ac41-128">**WarningVariable** (WV)</span><span class="sxs-lookup"><span data-stu-id="8ac41-128">**WarningVariable** (wv)</span></span>

<span data-ttu-id="8ac41-129">De **actie** parameters zijn waarden van het type **ActionPreference** .</span><span class="sxs-lookup"><span data-stu-id="8ac41-129">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="8ac41-130">**ActionPreference** is een opsomming met de volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="8ac41-130">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="8ac41-131">Naam</span><span class="sxs-lookup"><span data-stu-id="8ac41-131">Name</span></span>             | <span data-ttu-id="8ac41-132">Waarde</span><span class="sxs-lookup"><span data-stu-id="8ac41-132">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="8ac41-133">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="8ac41-133">Suspend</span></span>          | <span data-ttu-id="8ac41-134">5</span><span class="sxs-lookup"><span data-stu-id="8ac41-134">5</span></span>     |
| <span data-ttu-id="8ac41-135">Negeren</span><span class="sxs-lookup"><span data-stu-id="8ac41-135">Ignore</span></span>           | <span data-ttu-id="8ac41-136">4</span><span class="sxs-lookup"><span data-stu-id="8ac41-136">4</span></span>     |
| <span data-ttu-id="8ac41-137">Inquire</span><span class="sxs-lookup"><span data-stu-id="8ac41-137">Inquire</span></span>          | <span data-ttu-id="8ac41-138">3</span><span class="sxs-lookup"><span data-stu-id="8ac41-138">3</span></span>     |
| <span data-ttu-id="8ac41-139">Doorgaan</span><span class="sxs-lookup"><span data-stu-id="8ac41-139">Continue</span></span>         | <span data-ttu-id="8ac41-140">2</span><span class="sxs-lookup"><span data-stu-id="8ac41-140">2</span></span>     |
| <span data-ttu-id="8ac41-141">Stoppen</span><span class="sxs-lookup"><span data-stu-id="8ac41-141">Stop</span></span>             | <span data-ttu-id="8ac41-142">1</span><span class="sxs-lookup"><span data-stu-id="8ac41-142">1</span></span>     |
| <span data-ttu-id="8ac41-143">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="8ac41-143">SilentlyContinue</span></span> | <span data-ttu-id="8ac41-144">0</span><span class="sxs-lookup"><span data-stu-id="8ac41-144">0</span></span>     |

<span data-ttu-id="8ac41-145">U kunt de naam of de waarde gebruiken met de para meter.</span><span class="sxs-lookup"><span data-stu-id="8ac41-145">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="8ac41-146">Naast de algemene para meters bieden veel cmdlets para meters voor risico beperking.</span><span class="sxs-lookup"><span data-stu-id="8ac41-146">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="8ac41-147">Cmdlets die Risico's voor het systeem of gebruikers gegevens vereisen, bieden doorgaans deze para meters.</span><span class="sxs-lookup"><span data-stu-id="8ac41-147">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="8ac41-148">De para meters voor risico beperking zijn:</span><span class="sxs-lookup"><span data-stu-id="8ac41-148">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="8ac41-149">**WhatIf** (Wi)</span><span class="sxs-lookup"><span data-stu-id="8ac41-149">**WhatIf** (wi)</span></span>
- <span data-ttu-id="8ac41-150">**Bevestigen** (CF)</span><span class="sxs-lookup"><span data-stu-id="8ac41-150">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="8ac41-151">ALGEMENE PARAMETER BESCHRIJVINGEN</span><span class="sxs-lookup"><span data-stu-id="8ac41-151">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="8ac41-152">Fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="8ac41-152">Debug</span></span>

<span data-ttu-id="8ac41-153">Geeft details op programmeer niveau weer over de bewerking die door de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8ac41-153">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="8ac41-154">Deze para meter werkt alleen als de opdracht een fout opsporingsgegevens genereert.</span><span class="sxs-lookup"><span data-stu-id="8ac41-154">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="8ac41-155">Deze para meter werkt bijvoorbeeld als een opdracht de cmdlet bevat `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-155">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-156">Standaard worden fout opsporings berichten niet weer gegeven omdat de waarde van de `$DebugPreference` variabele **SilentlyContinue** is.</span><span class="sxs-lookup"><span data-stu-id="8ac41-156">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue**.</span></span>

<span data-ttu-id="8ac41-157">In de interactieve modus overschrijft de para meter **debug** de waarde van de `$DebugPreference` variabele voor de huidige opdracht, waarbij de waarde wordt ingesteld `$DebugPreference` op voor **query's**.</span><span class="sxs-lookup"><span data-stu-id="8ac41-157">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire**.</span></span>

<span data-ttu-id="8ac41-158">In de niet-interactieve modus overschrijft de para meter **debug** de waarde van de `$DebugPreference` variabele voor de huidige opdracht, waarbij u de waarde van opgeeft `$DebugPreference` om **door te gaan**.</span><span class="sxs-lookup"><span data-stu-id="8ac41-158">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue**.</span></span>

<span data-ttu-id="8ac41-159">`-Debug:$true` heeft hetzelfde effect als `-Debug` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-159">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="8ac41-160">Gebruik `-Debug:$false` om de weer gave van fout opsporings berichten te onderdrukken wanneer `$DebugPreference` deze niet **SilentlyContinue** is. Dit is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="8ac41-160">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue** , which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="8ac41-161">Error Action</span><span class="sxs-lookup"><span data-stu-id="8ac41-161">ErrorAction</span></span>

<span data-ttu-id="8ac41-162">Hiermee wordt bepaald hoe de cmdlet reageert op een niet-afsluit fout van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-162">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="8ac41-163">Deze para meter werkt alleen als de opdracht een niet-afsluit fout genereert, zoals die van de `Write-Error` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ac41-163">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-164">De para meter **Error Action** overschrijft de waarde van de `$ErrorActionPreference` variabele voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-164">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="8ac41-165">Omdat de standaard waarde van de `$ErrorActionPreference` variabele wordt **voortgezet** , worden er fout berichten weer gegeven en wordt de uitvoering voortgezet, tenzij u de para meter **Error Action** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-165">Because the default value of the `$ErrorActionPreference` variable is **Continue** , error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="8ac41-166">De para meter **Error Action** heeft geen invloed op de afsluit fouten (zoals ontbrekende gegevens, para meters die ongeldig zijn of onvoldoende machtigingen) waarmee wordt voor komen dat een opdracht kan worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="8ac41-166">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="8ac41-167">`-ErrorAction:Continue` het fout bericht weer geven en door gaan met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-167">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="8ac41-168">`Continue` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="8ac41-168">`Continue` is the default.</span></span>

<span data-ttu-id="8ac41-169">`-ErrorAction:Ignore` onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-169">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="8ac41-170">In tegens telling tot **SilentlyContinue** **, wordt** het fout bericht niet toegevoegd aan de `$Error` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-170">Unlike **SilentlyContinue** , **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="8ac41-171">De waarde **Ignore** wordt geïntroduceerd in power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ac41-171">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="8ac41-172">`-ErrorAction:Inquire` Hiermee wordt het fout bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="8ac41-172">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="8ac41-173">Deze waarde wordt zelden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-173">This value is rarely used.</span></span>

<span data-ttu-id="8ac41-174">`-ErrorAction:SilentlyContinue` onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-174">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="8ac41-175">`-ErrorAction:Stop` geeft het fout bericht weer en stopt met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-175">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="8ac41-176">`-ErrorAction:Suspend` is alleen beschikbaar voor werk stromen die niet worden ondersteund in Power shell 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8ac41-176">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="8ac41-177">De para meter **Error Action** wordt overschreven, maar de waarde van de voorkeurs variabele wordt niet vervangen `$ErrorAction` wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-177">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="8ac41-178">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="8ac41-178">ErrorVariable</span></span>

<span data-ttu-id="8ac41-179">**ErrorVariable** slaat fout berichten over de opdracht op in de opgegeven variabele en in de `$Error` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-179">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="8ac41-180">Zie [about_Automatic_Variables](about_Automatic_Variables.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-180">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-181">Nieuwe fout berichten overschrijven standaard fout berichten die al zijn opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-181">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="8ac41-182">Als u het fout bericht wilt toevoegen aan de variabele inhoud, typt u een plus teken ( `+` ) voor de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-182">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="8ac41-183">Met de volgende opdracht wordt bijvoorbeeld de `$a` variabele gemaakt en vervolgens eventuele fouten erin opgeslagen:</span><span class="sxs-lookup"><span data-stu-id="8ac41-183">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="8ac41-184">Met de volgende opdracht worden eventuele fout berichten aan de `$a` variabele toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="8ac41-184">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="8ac41-185">Met de volgende opdracht wordt de inhoud van weer gegeven `$a` :</span><span class="sxs-lookup"><span data-stu-id="8ac41-185">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="8ac41-186">U kunt deze para meter gebruiken om een variabele te maken die alleen fout berichten uit specifieke opdrachten bevat. Dit heeft geen invloed op het gedrag van de `$Error` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-186">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="8ac41-187">De `$Error` Automatische variabele bevat fout berichten van alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-187">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="8ac41-188">U kunt matrix notatie gebruiken, zoals `$a[0]` of `$error[1,2]` om te verwijzen naar specifieke fouten die zijn opgeslagen in de variabelen.</span><span class="sxs-lookup"><span data-stu-id="8ac41-188">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="8ac41-189">De variabele met de aangepaste fout bevat alle fouten die zijn gegenereerd door de opdracht, inclusief fouten van aanroepen naar geneste functies of scripts.</span><span class="sxs-lookup"><span data-stu-id="8ac41-189">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="8ac41-190">Information Action</span><span class="sxs-lookup"><span data-stu-id="8ac41-190">InformationAction</span></span>

<span data-ttu-id="8ac41-191">Geïntroduceerd in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="8ac41-191">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="8ac41-192">In de opdracht of het script waarin het wordt gebruikt, overschrijft de algemene para meter **Information Action** de waarde van de `$InformationPreference` Voorkeurs variabele, die standaard is ingesteld op **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="8ac41-192">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue**.</span></span> <span data-ttu-id="8ac41-193">Wanneer u gebruikt `Write-Information` in een script met **Information Action** , `Write-Information` worden waarden weer gegeven, afhankelijk van de waarde van de para meter **Information Action** .</span><span class="sxs-lookup"><span data-stu-id="8ac41-193">When you use `Write-Information` in a script with **InformationAction** , `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="8ac41-194">Zie about_Preference_Variables voor meer informatie over `$InformationPreference` . [about_Preference_Variables](./about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="8ac41-194">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-195">`-InformationAction:Stop` Hiermee stopt u een opdracht of script bij een exemplaar van de `Write-Information` opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-195">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="8ac41-196">`-InformationAction:Ignore` onderdrukt het informatie bericht en gaat verder met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-196">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="8ac41-197">In tegens telling tot **SilentlyContinue** , wordt met **negeren** het informatieve bericht volledig verg eten. het informatie bericht wordt niet toegevoegd aan de informatie stroom.</span><span class="sxs-lookup"><span data-stu-id="8ac41-197">Unlike **SilentlyContinue** , **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="8ac41-198">`-InformationAction:Inquire` Hiermee wordt het informatie bericht weer gegeven dat u in een `Write-Information` opdracht opgeeft. vervolgens wordt u gevraagd of u wilt door gaan.</span><span class="sxs-lookup"><span data-stu-id="8ac41-198">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="8ac41-199">`-InformationAction:Continue` het informatieve bericht wordt weer gegeven en blijft actief.</span><span class="sxs-lookup"><span data-stu-id="8ac41-199">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="8ac41-200">`-InformationAction:Suspend` wordt niet ondersteund in Power shell core omdat deze alleen beschikbaar is voor werk stromen.</span><span class="sxs-lookup"><span data-stu-id="8ac41-200">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="8ac41-201">`-InformationAction:SilentlyContinue` geen effect omdat het informatieve bericht niet (standaard) wordt weer gegeven en het script zonder onderbreking wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="8ac41-201">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="8ac41-202">De para meter **Information Action** wordt overschreven, maar de waarde van de voorkeurs variabele wordt niet vervangen `$InformationAction` wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-202">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="8ac41-203">InformationVariable</span><span class="sxs-lookup"><span data-stu-id="8ac41-203">InformationVariable</span></span>

<span data-ttu-id="8ac41-204">Geïntroduceerd in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="8ac41-204">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="8ac41-205">Binnen de opdracht of het script waarin het wordt gebruikt, wordt in de algemene para meter **InformationVariable** in een variabele een teken reeks opgeslagen die u opgeeft door de opdracht toe te voegen `Write-Information` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-205">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="8ac41-206">`Write-Information` de waarden worden weer gegeven, afhankelijk van de waarde van de algemene para meter **Information Action** . Als u de algemene para meter **Information Action** niet toevoegt, `Write-Information` worden teken reeksen weer gegeven, afhankelijk van de waarde van de `$InformationPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-206">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="8ac41-207">Zie about_Preference_Variables voor meer informatie over `$InformationPreference` . [about_Preference_Variables](./about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="8ac41-207">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8ac41-208">De informatie variabele bevat alle informatie berichten die door de opdracht worden gegenereerd, inclusief informatie berichten van aanroepen naar geneste functies of scripts.</span><span class="sxs-lookup"><span data-stu-id="8ac41-208">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="8ac41-209">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="8ac41-209">OutBuffer</span></span>

<span data-ttu-id="8ac41-210">Bepaalt het aantal objecten dat in een buffer moet worden verzameld voordat er objecten via de pijp lijn worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="8ac41-210">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="8ac41-211">Als u deze para meter weglaat, worden er objecten verzonden wanneer ze worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8ac41-211">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-212">Deze resource management-para meter is ontworpen voor ervaren gebruikers.</span><span class="sxs-lookup"><span data-stu-id="8ac41-212">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="8ac41-213">Wanneer u deze para meter gebruikt, verzendt Power shell gegevens naar de volgende cmdlet in batches van `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-213">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="8ac41-214">In het volgende voor beeld wordt een alternatief weer gegeven tussen voor het `ForEach-Object` verwerken van blokken die gebruikmaken van de- `Write-Host` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ac41-214">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="8ac41-215">De weergave alternatieven in batches van 2 of `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-215">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a><span data-ttu-id="8ac41-216">OutVariable</span><span class="sxs-lookup"><span data-stu-id="8ac41-216">OutVariable</span></span>

<span data-ttu-id="8ac41-217">Slaat uitvoer objecten op uit de opdracht in de opgegeven variabele, naast het verzenden van de uitvoer langs de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8ac41-217">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-218">Als u de uitvoer wilt toevoegen aan de variabele, typt u een plus teken ( `+` ) voor de naam van de variabele, in plaats van de uitvoer te vervangen die daar mogelijk al is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8ac41-218">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="8ac41-219">Met de volgende opdracht wordt bijvoorbeeld de `$out` variabele gemaakt en wordt het proces object opgeslagen:</span><span class="sxs-lookup"><span data-stu-id="8ac41-219">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="8ac41-220">Met de volgende opdracht wordt het proces object aan de `$out` variabele toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="8ac41-220">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="8ac41-221">Met de volgende opdracht wordt de inhoud van de variabele weer gegeven `$out` :</span><span class="sxs-lookup"><span data-stu-id="8ac41-221">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="8ac41-222">De variabele die door de para meter **outvariable** wordt gemaakt, is een `[System.Collections.ArrayList]` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-222">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="8ac41-223">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="8ac41-223">PipelineVariable</span></span>

<span data-ttu-id="8ac41-224">**PipelineVariable** slaat de waarde van het huidige pijplijn element op als een variabele voor elke benoemde opdracht terwijl het door de pijp lijn loopt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-224">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-225">Geldige waarden zijn teken reeksen, hetzelfde als voor alle namen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="8ac41-225">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="8ac41-226">Hier volgt een voor beeld van hoe **PipelineVariable** werkt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-226">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="8ac41-227">In dit voor beeld wordt de para meter **PipelineVariable** toegevoegd aan een `Foreach-Object` opdracht voor het opslaan van de resultaten van de opdracht in variabelen.</span><span class="sxs-lookup"><span data-stu-id="8ac41-227">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="8ac41-228">Een reeks cijfers, 1 tot en met 10, wordt in de eerste `Foreach-Object` opdracht geplaatst, waarbij de resultaten worden opgeslagen in een variabele met de naam **Left**.</span><span class="sxs-lookup"><span data-stu-id="8ac41-228">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left**.</span></span>

<span data-ttu-id="8ac41-229">De resultaten van de eerste `Foreach-Object` opdracht worden in een tweede opdracht gepiped `Foreach-Object` , waarmee de objecten worden gefilterd die door de eerste opdracht worden geretourneerd `Foreach-Object` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-229">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="8ac41-230">De resultaten van de tweede opdracht worden opgeslagen in een variabele met de naam **rechts**.</span><span class="sxs-lookup"><span data-stu-id="8ac41-230">The results of the second command are stored in a variable named **Right**.</span></span>

<span data-ttu-id="8ac41-231">In de derde `Foreach-Object` opdracht worden de resultaten van de eerste twee `Foreach-Object` gepipede opdrachten, vertegenwoordigd door de variabelen **links** en **rechts** , verwerkt met behulp van een vermenigvuldigings operator.</span><span class="sxs-lookup"><span data-stu-id="8ac41-231">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right** , are processed by using a multiplication operator.</span></span> <span data-ttu-id="8ac41-232">De opdracht geeft objecten die zijn opgeslagen in de **linker** -en **rechter** variabelen die moeten worden vermenigvuldigd en geeft aan dat de resultaten moeten worden weer gegeven als ' lid van ' links bereik \* rechter bereik lid = product '.</span><span class="sxs-lookup"><span data-stu-id="8ac41-232">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a><span data-ttu-id="8ac41-233">Uitgebreid</span><span class="sxs-lookup"><span data-stu-id="8ac41-233">Verbose</span></span>

<span data-ttu-id="8ac41-234">Geeft gedetailleerde informatie weer over de bewerking die door de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8ac41-234">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="8ac41-235">Deze informatie komt overeen met de informatie in een tracering of in een transactie logboek.</span><span class="sxs-lookup"><span data-stu-id="8ac41-235">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="8ac41-236">Deze para meter werkt alleen als de opdracht een uitgebreid bericht genereert.</span><span class="sxs-lookup"><span data-stu-id="8ac41-236">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="8ac41-237">Deze para meter werkt bijvoorbeeld als een opdracht de cmdlet bevat `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-237">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-238">De para meter **uitgebreid** overschrijft de waarde van de `$VerbosePreference` variabele voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-238">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="8ac41-239">Omdat de standaard waarde van de `$VerbosePreference` variabele **SilentlyContinue** is, worden uitgebreide berichten niet standaard weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8ac41-239">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue** , verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="8ac41-240">`-Verbose:$true` heeft hetzelfde effect als `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="8ac41-240">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="8ac41-241">`-Verbose:$false` onderdrukt de weer gave van uitgebreide berichten.</span><span class="sxs-lookup"><span data-stu-id="8ac41-241">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="8ac41-242">Gebruik deze para meter als de waarde van `$VerbosePreference` niet **SilentlyContinue** is (de standaard instelling).</span><span class="sxs-lookup"><span data-stu-id="8ac41-242">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="8ac41-243">WarningAction</span><span class="sxs-lookup"><span data-stu-id="8ac41-243">WarningAction</span></span>

<span data-ttu-id="8ac41-244">Hiermee wordt bepaald hoe de cmdlet reageert op een waarschuwing van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-244">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="8ac41-245">**Continue** is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="8ac41-245">**Continue** is the default value.</span></span> <span data-ttu-id="8ac41-246">Deze para meter werkt alleen als er een waarschuwings bericht wordt gegenereerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-246">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="8ac41-247">Deze para meter werkt bijvoorbeeld als een opdracht de cmdlet bevat `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-247">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-248">De para meter **WarningAction** overschrijft de waarde van de `$WarningPreference` variabele voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-248">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="8ac41-249">Omdat de standaard waarde van de `$WarningPreference` variabele wordt **voortgezet** , worden er waarschuwingen weer gegeven en wordt de uitvoering voortgezet, tenzij u de para meter **WarningAction** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-249">Because the default value of the `$WarningPreference` variable is **Continue** , warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="8ac41-250">`-WarningAction:Continue` geeft de waarschuwings berichten weer en gaat verder met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-250">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="8ac41-251">`Continue` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="8ac41-251">`Continue` is the default.</span></span>

<span data-ttu-id="8ac41-252">`-WarningAction:Inquire` Hiermee wordt het waarschuwings bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="8ac41-252">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="8ac41-253">Deze waarde wordt zelden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-253">This value is rarely used.</span></span>

<span data-ttu-id="8ac41-254">`-WarningAction:SilentlyContinue` onderdrukt het waarschuwings bericht en gaat door met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-254">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="8ac41-255">`-WarningAction:Stop` geeft het waarschuwings bericht weer en stopt met het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-255">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="8ac41-256">De para meter **WarningAction** wordt overschreven, maar de waarde van de voorkeurs variabele wordt niet vervangen `$WarningAction` wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-256">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="8ac41-257">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="8ac41-257">WarningVariable</span></span>

<span data-ttu-id="8ac41-258">Slaat waarschuwingen over de opdracht op in de opgegeven variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-258">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-259">Alle gegenereerde waarschuwingen worden opgeslagen in de variabele, zelfs als de waarschuwingen niet worden weer gegeven voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8ac41-259">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="8ac41-260">Als u de waarschuwingen wilt toevoegen aan de variabele inhoud, in plaats van waarschuwingen te vervangen die daar al zijn opgeslagen, typt u een plus teken ( `+` ) voor de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-260">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="8ac41-261">Met de volgende opdracht wordt bijvoorbeeld de `$a` variabele gemaakt en vervolgens eventuele waarschuwingen opgeslagen:</span><span class="sxs-lookup"><span data-stu-id="8ac41-261">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="8ac41-262">Met de volgende opdracht worden eventuele waarschuwingen aan de `$a` variabele toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="8ac41-262">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="8ac41-263">Met de volgende opdracht wordt de inhoud van weer gegeven `$a` :</span><span class="sxs-lookup"><span data-stu-id="8ac41-263">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="8ac41-264">U kunt deze para meter gebruiken om een variabele te maken die alleen waarschuwingen van specifieke opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="8ac41-264">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="8ac41-265">U kunt matrix notatie gebruiken, zoals `$a[0]` of `$warning[1,2]` om te verwijzen naar specifieke waarschuwingen die zijn opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="8ac41-265">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="8ac41-266">De variabele Warning bevat alle waarschuwingen die zijn gegenereerd door de opdracht, inclusief waarschuwingen van aanroepen naar geneste functies of scripts.</span><span class="sxs-lookup"><span data-stu-id="8ac41-266">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>

### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="8ac41-267">Beschrijvingen van de para meters voor risico beheer</span><span class="sxs-lookup"><span data-stu-id="8ac41-267">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="8ac41-268">WhatIf</span><span class="sxs-lookup"><span data-stu-id="8ac41-268">WhatIf</span></span>

<span data-ttu-id="8ac41-269">Hier wordt een bericht weer gegeven waarin het effect van de opdracht wordt beschreven, in plaats van de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="8ac41-269">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-270">De para meter **WhatIf** overschrijft de waarde van de `$WhatIfPreference` variabele voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-270">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="8ac41-271">Omdat de standaard waarde van de `$WhatIfPreference` variabele 0 (uitgeschakeld) is, wordt het gedrag **WhatIf** niet uitgevoerd zonder de para meter **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="8ac41-271">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="8ac41-272">Zie [about_Preference_Variables](about_Preference_Variables.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-272">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="8ac41-273">`-WhatIf:$true` heeft hetzelfde effect als `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-273">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="8ac41-274">`-WhatIf:$false` onderdrukt het automatische WhatIf-gedrag dat resulteert wanneer de waarde van de `$WhatIfPreference` variabele 1 is.</span><span class="sxs-lookup"><span data-stu-id="8ac41-274">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="8ac41-275">Met de volgende opdracht wordt bijvoorbeeld de `-WhatIf` para meter gebruikt in een `Remove-Item` opdracht:</span><span class="sxs-lookup"><span data-stu-id="8ac41-275">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="8ac41-276">In plaats van het item te verwijderen, worden de bewerkingen weer gegeven die worden uitgevoerd in Power shell en de items die zouden worden beïnvloed.</span><span class="sxs-lookup"><span data-stu-id="8ac41-276">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="8ac41-277">Met deze opdracht wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="8ac41-277">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="8ac41-278">Bevestigen</span><span class="sxs-lookup"><span data-stu-id="8ac41-278">Confirm</span></span>

<span data-ttu-id="8ac41-279">Vraagt u om bevestiging voordat de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8ac41-279">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="8ac41-280">De para meter **confirm** onderdrukt de waarde van de `$ConfirmPreference` variabele voor de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-280">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="8ac41-281">De standaardwaarde is waar.</span><span class="sxs-lookup"><span data-stu-id="8ac41-281">The default value is true.</span></span> <span data-ttu-id="8ac41-282">Zie [about_Preference_Variables](about_Preference_Variables.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-282">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="8ac41-283">`-Confirm:$true` heeft hetzelfde effect als `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="8ac41-283">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="8ac41-284">`-Confirm:$false` onderdrukt automatische bevestiging. dit gebeurt wanneer de waarde van `$ConfirmPreference` kleiner is dan of gelijk is aan het geschatte risico van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ac41-284">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="8ac41-285">Met de volgende opdracht wordt bijvoorbeeld de **confirm** -para meter met een `Remove-Item` opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8ac41-285">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="8ac41-286">Voordat u het item verwijdert, worden de bewerkingen weer gegeven die worden uitgevoerd en de items die zouden worden beïnvloed, en wordt u gevraagd om goed te keuren.</span><span class="sxs-lookup"><span data-stu-id="8ac41-286">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="8ac41-287">De opties voor het bevestigen van antwoorden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="8ac41-287">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="8ac41-288">Antwoord</span><span class="sxs-lookup"><span data-stu-id="8ac41-288">Response</span></span>       |<span data-ttu-id="8ac41-289">Resultaat</span><span class="sxs-lookup"><span data-stu-id="8ac41-289">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="8ac41-290">Ja (Y)</span><span class="sxs-lookup"><span data-stu-id="8ac41-290">Yes (Y)</span></span>        |<span data-ttu-id="8ac41-291">Voer de actie uit.</span><span class="sxs-lookup"><span data-stu-id="8ac41-291">Perform the action.</span></span>                                        |
|<span data-ttu-id="8ac41-292">Ja op alles (A)</span><span class="sxs-lookup"><span data-stu-id="8ac41-292">Yes to All (A)</span></span> |<span data-ttu-id="8ac41-293">Alle acties uitvoeren en volgende bevestigde query's onderdrukken</span><span class="sxs-lookup"><span data-stu-id="8ac41-293">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="8ac41-294">voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-294">for this command.</span></span>                                          |
|<span data-ttu-id="8ac41-295">Nee (N):</span><span class="sxs-lookup"><span data-stu-id="8ac41-295">No (N):</span></span>        |<span data-ttu-id="8ac41-296">Voer de actie niet uit.</span><span class="sxs-lookup"><span data-stu-id="8ac41-296">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="8ac41-297">Nee naar alle (L):</span><span class="sxs-lookup"><span data-stu-id="8ac41-297">No to All (L):</span></span> |<span data-ttu-id="8ac41-298">Geen acties uitvoeren en volgende bevestiging onderdrukken</span><span class="sxs-lookup"><span data-stu-id="8ac41-298">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="8ac41-299">query's voor deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-299">queries for this command.</span></span>                                  |
|<span data-ttu-id="8ac41-300">Suspend (S):</span><span class="sxs-lookup"><span data-stu-id="8ac41-300">Suspend (S):</span></span>   |<span data-ttu-id="8ac41-301">De opdracht onderbreken en een tijdelijke sessie maken.</span><span class="sxs-lookup"><span data-stu-id="8ac41-301">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="8ac41-302">Help (?)</span><span class="sxs-lookup"><span data-stu-id="8ac41-302">Help (?)</span></span>       |<span data-ttu-id="8ac41-303">Help weer geven voor deze opties.</span><span class="sxs-lookup"><span data-stu-id="8ac41-303">Display help for these options.</span></span>                            |

<span data-ttu-id="8ac41-304">Met de optie **suspend** wordt de opdracht in de wacht stand geplaatst en wordt er een tijdelijke geneste sessie gemaakt waarin u kunt werken totdat u een optie voor **bevestigen** kiest.</span><span class="sxs-lookup"><span data-stu-id="8ac41-304">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="8ac41-305">De opdracht prompt voor de geneste sessie heeft twee extra caret (>>) om aan te geven dat het een onderliggende bewerking is van de oorspronkelijke bovenliggende opdracht.</span><span class="sxs-lookup"><span data-stu-id="8ac41-305">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="8ac41-306">U kunt opdrachten en scripts uitvoeren in de geneste sessie.</span><span class="sxs-lookup"><span data-stu-id="8ac41-306">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="8ac41-307">Als u de geneste sessie wilt beëindigen en wilt terugkeren naar de bevestigings opties voor de oorspronkelijke opdracht, typt u ' afsluiten '.</span><span class="sxs-lookup"><span data-stu-id="8ac41-307">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="8ac41-308">In het volgende voor beeld wordt **de optie voor** uitstel (en) gebruikt om een opdracht tijdelijk te onderbreken terwijl de gebruiker de Help voor een opdracht parameter controleert.</span><span class="sxs-lookup"><span data-stu-id="8ac41-308">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="8ac41-309">Nadat de benodigde gegevens zijn verkregen, typt u ' exit ' om de geneste prompt te beëindigen en selecteert u vervolgens het Ja (y)-antwoord op de query bevestigen.</span><span class="sxs-lookup"><span data-stu-id="8ac41-309">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a><span data-ttu-id="8ac41-310">WOORD</span><span class="sxs-lookup"><span data-stu-id="8ac41-310">KEYWORDS</span></span>

<span data-ttu-id="8ac41-311">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="8ac41-311">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="8ac41-312">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="8ac41-312">SEE ALSO</span></span>

[<span data-ttu-id="8ac41-313">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="8ac41-313">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="8ac41-314">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="8ac41-314">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="8ac41-315">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="8ac41-315">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="8ac41-316">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="8ac41-316">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="8ac41-317">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="8ac41-317">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)