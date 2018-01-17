---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: pswaauthorizationrule verwijderen
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="894d7-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="894d7-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="894d7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="894d7-104">SYNOPSIS</span></span>

<span data-ttu-id="894d7-105">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="894d7-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="894d7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="894d7-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="894d7-107">Id</span><span class="sxs-lookup"><span data-stu-id="894d7-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="894d7-108">Regel</span><span class="sxs-lookup"><span data-stu-id="894d7-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="894d7-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="894d7-109">DESCRIPTION</span></span>

<span data-ttu-id="894d7-110">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="894d7-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="894d7-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="894d7-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="894d7-112">-Force</span><span class="sxs-lookup"><span data-stu-id="894d7-112">-Force</span></span>

<span data-ttu-id="894d7-113">De cmdlet uitvoert zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="894d7-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="894d7-114">Standaard wordt de cmdlet gevraagd om bevestiging voordat u doorgaat.</span><span class="sxs-lookup"><span data-stu-id="894d7-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="894d7-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="894d7-115">Aliases</span></span>                              | <span data-ttu-id="894d7-116">geen</span><span class="sxs-lookup"><span data-stu-id="894d7-116">none</span></span>                                 |
| <span data-ttu-id="894d7-117">Nodig?</span><span class="sxs-lookup"><span data-stu-id="894d7-117">Required?</span></span>                            | <span data-ttu-id="894d7-118">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-118">false</span></span>                                |
| <span data-ttu-id="894d7-119">Positie?</span><span class="sxs-lookup"><span data-stu-id="894d7-119">Position?</span></span>                            | <span data-ttu-id="894d7-120">Met de naam</span><span class="sxs-lookup"><span data-stu-id="894d7-120">named</span></span>                                |
| <span data-ttu-id="894d7-121">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="894d7-121">Default Value</span></span>                        | <span data-ttu-id="894d7-122">geen</span><span class="sxs-lookup"><span data-stu-id="894d7-122">none</span></span>                                 |
| <span data-ttu-id="894d7-123">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="894d7-124">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-124">false</span></span>                                |
| <span data-ttu-id="894d7-125">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="894d7-126">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="894d7-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="894d7-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="894d7-128">Hiermee geeft u de id's van een of meer regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="894d7-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="894d7-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="894d7-129">Aliases</span></span>                              | <span data-ttu-id="894d7-130">geen</span><span class="sxs-lookup"><span data-stu-id="894d7-130">none</span></span>                                 |
| <span data-ttu-id="894d7-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="894d7-131">Required?</span></span>                            | <span data-ttu-id="894d7-132">De waarde True</span><span class="sxs-lookup"><span data-stu-id="894d7-132">true</span></span>                                 |
| <span data-ttu-id="894d7-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="894d7-133">Position?</span></span>                            | <span data-ttu-id="894d7-134">2</span><span class="sxs-lookup"><span data-stu-id="894d7-134">2</span></span>                                    |
| <span data-ttu-id="894d7-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="894d7-135">Default Value</span></span>                        | <span data-ttu-id="894d7-136">geen</span><span class="sxs-lookup"><span data-stu-id="894d7-136">none</span></span>                                 |
| <span data-ttu-id="894d7-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="894d7-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="894d7-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="894d7-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="894d7-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="894d7-141">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="894d7-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="894d7-142">Hiermee geeft u de regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="894d7-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="894d7-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="894d7-143">Aliases</span></span>                              | <span data-ttu-id="894d7-144">geen</span><span class="sxs-lookup"><span data-stu-id="894d7-144">none</span></span>                                 |
| <span data-ttu-id="894d7-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="894d7-145">Required?</span></span>                            | <span data-ttu-id="894d7-146">De waarde True</span><span class="sxs-lookup"><span data-stu-id="894d7-146">true</span></span>                                 |
| <span data-ttu-id="894d7-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="894d7-147">Position?</span></span>                            | <span data-ttu-id="894d7-148">2</span><span class="sxs-lookup"><span data-stu-id="894d7-148">2</span></span>                                    |
| <span data-ttu-id="894d7-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="894d7-149">Default Value</span></span>                        | <span data-ttu-id="894d7-150">geen</span><span class="sxs-lookup"><span data-stu-id="894d7-150">none</span></span>                                 |
| <span data-ttu-id="894d7-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="894d7-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="894d7-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="894d7-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="894d7-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="894d7-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="894d7-155">-Confirm</span></span>

<span data-ttu-id="894d7-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="894d7-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="894d7-157">Nodig?</span><span class="sxs-lookup"><span data-stu-id="894d7-157">Required?</span></span>                            | <span data-ttu-id="894d7-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-158">false</span></span>                                |
| <span data-ttu-id="894d7-159">Positie?</span><span class="sxs-lookup"><span data-stu-id="894d7-159">Position?</span></span>                            | <span data-ttu-id="894d7-160">Met de naam</span><span class="sxs-lookup"><span data-stu-id="894d7-160">named</span></span>                                |
| <span data-ttu-id="894d7-161">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="894d7-161">Default Value</span></span>                        | <span data-ttu-id="894d7-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-162">false</span></span>                                |
| <span data-ttu-id="894d7-163">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="894d7-164">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-164">false</span></span>                                |
| <span data-ttu-id="894d7-165">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="894d7-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="894d7-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="894d7-167">-WhatIf</span></span>

<span data-ttu-id="894d7-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="894d7-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="894d7-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="894d7-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="894d7-170">Nodig?</span><span class="sxs-lookup"><span data-stu-id="894d7-170">Required?</span></span>                            | <span data-ttu-id="894d7-171">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-171">false</span></span>                                |
| <span data-ttu-id="894d7-172">Positie?</span><span class="sxs-lookup"><span data-stu-id="894d7-172">Position?</span></span>                            | <span data-ttu-id="894d7-173">Met de naam</span><span class="sxs-lookup"><span data-stu-id="894d7-173">named</span></span>                                |
| <span data-ttu-id="894d7-174">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="894d7-174">Default Value</span></span>                        | <span data-ttu-id="894d7-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-175">false</span></span>                                |
| <span data-ttu-id="894d7-176">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="894d7-177">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-177">false</span></span>                                |
| <span data-ttu-id="894d7-178">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="894d7-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="894d7-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="894d7-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="894d7-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="894d7-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="894d7-181">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="894d7-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="894d7-182">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="894d7-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="894d7-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="894d7-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="894d7-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="894d7-184">int\[\]</span></span>

<span data-ttu-id="894d7-185">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="894d7-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="894d7-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="894d7-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="894d7-187">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="894d7-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="894d7-188">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="894d7-188">OUTPUTS</span></span>

<span data-ttu-id="894d7-189">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="894d7-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="894d7-190">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="894d7-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="894d7-191">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="894d7-191">EXAMPLE 1</span></span>

<span data-ttu-id="894d7-192">In dit voorbeeld verwijdert u de autorisatieregel met een ID van *2*.</span><span class="sxs-lookup"><span data-stu-id="894d7-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="894d7-193">Voorbeeld 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="894d7-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="894d7-194">In dit voorbeeld verwijdert alle autorisatieregels en bevestiging van de gebruiker is ook vereist.</span><span class="sxs-lookup"><span data-stu-id="894d7-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="894d7-195">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="894d7-195">Related topics</span></span>

- [<span data-ttu-id="894d7-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="894d7-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="894d7-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="894d7-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="894d7-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="894d7-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="894d7-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="894d7-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
