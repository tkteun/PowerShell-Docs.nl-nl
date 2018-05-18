---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="97b86-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b86-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="97b86-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="97b86-104">SYNOPSIS</span></span>

<span data-ttu-id="97b86-105">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="97b86-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="97b86-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="97b86-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="97b86-107">Id</span><span class="sxs-lookup"><span data-stu-id="97b86-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="97b86-108">Regel</span><span class="sxs-lookup"><span data-stu-id="97b86-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="97b86-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="97b86-109">DESCRIPTION</span></span>

<span data-ttu-id="97b86-110">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="97b86-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="97b86-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="97b86-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="97b86-112">-Force</span><span class="sxs-lookup"><span data-stu-id="97b86-112">-Force</span></span>

<span data-ttu-id="97b86-113">De cmdlet uitvoert zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="97b86-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="97b86-114">Standaard wordt de cmdlet gevraagd om bevestiging voordat u doorgaat.</span><span class="sxs-lookup"><span data-stu-id="97b86-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="97b86-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="97b86-115">Aliases</span></span>                              | <span data-ttu-id="97b86-116">geen</span><span class="sxs-lookup"><span data-stu-id="97b86-116">none</span></span>                                 |
| <span data-ttu-id="97b86-117">Nodig?</span><span class="sxs-lookup"><span data-stu-id="97b86-117">Required?</span></span>                            | <span data-ttu-id="97b86-118">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-118">false</span></span>                                |
| <span data-ttu-id="97b86-119">Positie?</span><span class="sxs-lookup"><span data-stu-id="97b86-119">Position?</span></span>                            | <span data-ttu-id="97b86-120">Met de naam</span><span class="sxs-lookup"><span data-stu-id="97b86-120">named</span></span>                                |
| <span data-ttu-id="97b86-121">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="97b86-121">Default Value</span></span>                        | <span data-ttu-id="97b86-122">geen</span><span class="sxs-lookup"><span data-stu-id="97b86-122">none</span></span>                                 |
| <span data-ttu-id="97b86-123">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b86-124">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-124">false</span></span>                                |
| <span data-ttu-id="97b86-125">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b86-126">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="97b86-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="97b86-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="97b86-128">Hiermee geeft u de id's van een of meer regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="97b86-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="97b86-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="97b86-129">Aliases</span></span>                              | <span data-ttu-id="97b86-130">geen</span><span class="sxs-lookup"><span data-stu-id="97b86-130">none</span></span>                                 |
| <span data-ttu-id="97b86-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="97b86-131">Required?</span></span>                            | <span data-ttu-id="97b86-132">De waarde True</span><span class="sxs-lookup"><span data-stu-id="97b86-132">true</span></span>                                 |
| <span data-ttu-id="97b86-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="97b86-133">Position?</span></span>                            | <span data-ttu-id="97b86-134">2</span><span class="sxs-lookup"><span data-stu-id="97b86-134">2</span></span>                                    |
| <span data-ttu-id="97b86-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="97b86-135">Default Value</span></span>                        | <span data-ttu-id="97b86-136">geen</span><span class="sxs-lookup"><span data-stu-id="97b86-136">none</span></span>                                 |
| <span data-ttu-id="97b86-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b86-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="97b86-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="97b86-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b86-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="97b86-141">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="97b86-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="97b86-142">Hiermee geeft u de regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="97b86-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="97b86-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="97b86-143">Aliases</span></span>                              | <span data-ttu-id="97b86-144">geen</span><span class="sxs-lookup"><span data-stu-id="97b86-144">none</span></span>                                 |
| <span data-ttu-id="97b86-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="97b86-145">Required?</span></span>                            | <span data-ttu-id="97b86-146">De waarde True</span><span class="sxs-lookup"><span data-stu-id="97b86-146">true</span></span>                                 |
| <span data-ttu-id="97b86-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="97b86-147">Position?</span></span>                            | <span data-ttu-id="97b86-148">2</span><span class="sxs-lookup"><span data-stu-id="97b86-148">2</span></span>                                    |
| <span data-ttu-id="97b86-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="97b86-149">Default Value</span></span>                        | <span data-ttu-id="97b86-150">geen</span><span class="sxs-lookup"><span data-stu-id="97b86-150">none</span></span>                                 |
| <span data-ttu-id="97b86-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b86-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="97b86-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="97b86-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b86-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="97b86-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="97b86-155">-Confirm</span></span>

<span data-ttu-id="97b86-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="97b86-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="97b86-157">Nodig?</span><span class="sxs-lookup"><span data-stu-id="97b86-157">Required?</span></span>                            | <span data-ttu-id="97b86-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-158">false</span></span>                                |
| <span data-ttu-id="97b86-159">Positie?</span><span class="sxs-lookup"><span data-stu-id="97b86-159">Position?</span></span>                            | <span data-ttu-id="97b86-160">Met de naam</span><span class="sxs-lookup"><span data-stu-id="97b86-160">named</span></span>                                |
| <span data-ttu-id="97b86-161">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="97b86-161">Default Value</span></span>                        | <span data-ttu-id="97b86-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-162">false</span></span>                                |
| <span data-ttu-id="97b86-163">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b86-164">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-164">false</span></span>                                |
| <span data-ttu-id="97b86-165">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b86-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="97b86-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="97b86-167">-WhatIf</span></span>

<span data-ttu-id="97b86-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="97b86-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="97b86-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="97b86-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="97b86-170">Nodig?</span><span class="sxs-lookup"><span data-stu-id="97b86-170">Required?</span></span>                            | <span data-ttu-id="97b86-171">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-171">false</span></span>                                |
| <span data-ttu-id="97b86-172">Positie?</span><span class="sxs-lookup"><span data-stu-id="97b86-172">Position?</span></span>                            | <span data-ttu-id="97b86-173">Met de naam</span><span class="sxs-lookup"><span data-stu-id="97b86-173">named</span></span>                                |
| <span data-ttu-id="97b86-174">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="97b86-174">Default Value</span></span>                        | <span data-ttu-id="97b86-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-175">false</span></span>                                |
| <span data-ttu-id="97b86-176">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b86-177">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-177">false</span></span>                                |
| <span data-ttu-id="97b86-178">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="97b86-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b86-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="97b86-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="97b86-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="97b86-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="97b86-181">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="97b86-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="97b86-182">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="97b86-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="97b86-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="97b86-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="97b86-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="97b86-184">int\[\]</span></span>

<span data-ttu-id="97b86-185">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="97b86-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="97b86-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="97b86-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="97b86-187">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="97b86-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="97b86-188">UITVOER</span><span class="sxs-lookup"><span data-stu-id="97b86-188">OUTPUTS</span></span>

<span data-ttu-id="97b86-189">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="97b86-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="97b86-190">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="97b86-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="97b86-191">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="97b86-191">EXAMPLE 1</span></span>

<span data-ttu-id="97b86-192">In dit voorbeeld verwijdert u de autorisatieregel met een ID van *2*.</span><span class="sxs-lookup"><span data-stu-id="97b86-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="97b86-193">Voorbeeld 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="97b86-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="97b86-194">In dit voorbeeld verwijdert alle autorisatieregels en bevestiging van de gebruiker is ook vereist.</span><span class="sxs-lookup"><span data-stu-id="97b86-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="97b86-195">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="97b86-195">Related topics</span></span>

- [<span data-ttu-id="97b86-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b86-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="97b86-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b86-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="97b86-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="97b86-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="97b86-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b86-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)