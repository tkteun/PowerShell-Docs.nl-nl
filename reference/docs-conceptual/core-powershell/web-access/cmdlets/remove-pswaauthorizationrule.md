---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: pswaauthorizationrule verwijderen
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="67e02-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="67e02-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="67e02-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="67e02-104">SYNOPSIS</span></span>

<span data-ttu-id="67e02-105">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="67e02-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="67e02-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="67e02-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="67e02-107">Id</span><span class="sxs-lookup"><span data-stu-id="67e02-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="67e02-108">Regel</span><span class="sxs-lookup"><span data-stu-id="67e02-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="67e02-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="67e02-109">DESCRIPTION</span></span>

<span data-ttu-id="67e02-110">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="67e02-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="67e02-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="67e02-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="67e02-112">-Force</span><span class="sxs-lookup"><span data-stu-id="67e02-112">-Force</span></span>

<span data-ttu-id="67e02-113">De cmdlet uitvoert zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="67e02-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="67e02-114">Standaard wordt de cmdlet gevraagd om bevestiging voordat u doorgaat.</span><span class="sxs-lookup"><span data-stu-id="67e02-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="67e02-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="67e02-115">Aliases</span></span>                              | <span data-ttu-id="67e02-116">geen</span><span class="sxs-lookup"><span data-stu-id="67e02-116">none</span></span>                                 |
| <span data-ttu-id="67e02-117">Nodig?</span><span class="sxs-lookup"><span data-stu-id="67e02-117">Required?</span></span>                            | <span data-ttu-id="67e02-118">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-118">false</span></span>                                |
| <span data-ttu-id="67e02-119">Positie?</span><span class="sxs-lookup"><span data-stu-id="67e02-119">Position?</span></span>                            | <span data-ttu-id="67e02-120">Met de naam</span><span class="sxs-lookup"><span data-stu-id="67e02-120">named</span></span>                                |
| <span data-ttu-id="67e02-121">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="67e02-121">Default Value</span></span>                        | <span data-ttu-id="67e02-122">geen</span><span class="sxs-lookup"><span data-stu-id="67e02-122">none</span></span>                                 |
| <span data-ttu-id="67e02-123">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="67e02-124">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-124">false</span></span>                                |
| <span data-ttu-id="67e02-125">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="67e02-126">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="67e02-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="67e02-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="67e02-128">Hiermee geeft u de id's van een of meer regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="67e02-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="67e02-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="67e02-129">Aliases</span></span>                              | <span data-ttu-id="67e02-130">geen</span><span class="sxs-lookup"><span data-stu-id="67e02-130">none</span></span>                                 |
| <span data-ttu-id="67e02-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="67e02-131">Required?</span></span>                            | <span data-ttu-id="67e02-132">De waarde True</span><span class="sxs-lookup"><span data-stu-id="67e02-132">true</span></span>                                 |
| <span data-ttu-id="67e02-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="67e02-133">Position?</span></span>                            | <span data-ttu-id="67e02-134">2</span><span class="sxs-lookup"><span data-stu-id="67e02-134">2</span></span>                                    |
| <span data-ttu-id="67e02-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="67e02-135">Default Value</span></span>                        | <span data-ttu-id="67e02-136">geen</span><span class="sxs-lookup"><span data-stu-id="67e02-136">none</span></span>                                 |
| <span data-ttu-id="67e02-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="67e02-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="67e02-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="67e02-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="67e02-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="67e02-141">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="67e02-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="67e02-142">Hiermee geeft u de regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="67e02-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="67e02-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="67e02-143">Aliases</span></span>                              | <span data-ttu-id="67e02-144">geen</span><span class="sxs-lookup"><span data-stu-id="67e02-144">none</span></span>                                 |
| <span data-ttu-id="67e02-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="67e02-145">Required?</span></span>                            | <span data-ttu-id="67e02-146">De waarde True</span><span class="sxs-lookup"><span data-stu-id="67e02-146">true</span></span>                                 |
| <span data-ttu-id="67e02-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="67e02-147">Position?</span></span>                            | <span data-ttu-id="67e02-148">2</span><span class="sxs-lookup"><span data-stu-id="67e02-148">2</span></span>                                    |
| <span data-ttu-id="67e02-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="67e02-149">Default Value</span></span>                        | <span data-ttu-id="67e02-150">geen</span><span class="sxs-lookup"><span data-stu-id="67e02-150">none</span></span>                                 |
| <span data-ttu-id="67e02-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="67e02-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="67e02-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="67e02-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="67e02-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="67e02-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="67e02-155">-Confirm</span></span>

<span data-ttu-id="67e02-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="67e02-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="67e02-157">Nodig?</span><span class="sxs-lookup"><span data-stu-id="67e02-157">Required?</span></span>                            | <span data-ttu-id="67e02-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-158">false</span></span>                                |
| <span data-ttu-id="67e02-159">Positie?</span><span class="sxs-lookup"><span data-stu-id="67e02-159">Position?</span></span>                            | <span data-ttu-id="67e02-160">Met de naam</span><span class="sxs-lookup"><span data-stu-id="67e02-160">named</span></span>                                |
| <span data-ttu-id="67e02-161">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="67e02-161">Default Value</span></span>                        | <span data-ttu-id="67e02-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-162">false</span></span>                                |
| <span data-ttu-id="67e02-163">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="67e02-164">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-164">false</span></span>                                |
| <span data-ttu-id="67e02-165">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="67e02-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="67e02-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="67e02-167">-WhatIf</span></span>

<span data-ttu-id="67e02-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="67e02-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="67e02-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67e02-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="67e02-170">Nodig?</span><span class="sxs-lookup"><span data-stu-id="67e02-170">Required?</span></span>                            | <span data-ttu-id="67e02-171">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-171">false</span></span>                                |
| <span data-ttu-id="67e02-172">Positie?</span><span class="sxs-lookup"><span data-stu-id="67e02-172">Position?</span></span>                            | <span data-ttu-id="67e02-173">Met de naam</span><span class="sxs-lookup"><span data-stu-id="67e02-173">named</span></span>                                |
| <span data-ttu-id="67e02-174">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="67e02-174">Default Value</span></span>                        | <span data-ttu-id="67e02-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-175">false</span></span>                                |
| <span data-ttu-id="67e02-176">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="67e02-177">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-177">false</span></span>                                |
| <span data-ttu-id="67e02-178">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="67e02-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="67e02-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="67e02-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="67e02-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="67e02-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="67e02-181">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="67e02-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="67e02-182">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="67e02-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="67e02-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="67e02-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="67e02-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="67e02-184">int\[\]</span></span>

<span data-ttu-id="67e02-185">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="67e02-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="67e02-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="67e02-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="67e02-187">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="67e02-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="67e02-188">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="67e02-188">OUTPUTS</span></span>

<span data-ttu-id="67e02-189">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="67e02-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="67e02-190">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="67e02-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="67e02-191">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="67e02-191">EXAMPLE 1</span></span>

<span data-ttu-id="67e02-192">In dit voorbeeld verwijdert u de autorisatieregel met een ID van *2*.</span><span class="sxs-lookup"><span data-stu-id="67e02-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="67e02-193">Voorbeeld 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="67e02-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="67e02-194">In dit voorbeeld verwijdert alle autorisatieregels en bevestiging van de gebruiker is ook vereist.</span><span class="sxs-lookup"><span data-stu-id="67e02-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="67e02-195">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="67e02-195">Related topics</span></span>

- [<span data-ttu-id="67e02-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="67e02-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="67e02-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="67e02-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="67e02-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="67e02-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="67e02-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="67e02-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)