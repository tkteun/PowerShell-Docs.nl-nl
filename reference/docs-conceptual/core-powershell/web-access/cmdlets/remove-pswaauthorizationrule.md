---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: pswaauthorizationrule verwijderen
ms.technology: powershell
ms.openlocfilehash: a8304b68a446de0be98aa732304c71302fb8389e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="1e515-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1e515-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="1e515-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1e515-104">SYNOPSIS</span></span>

<span data-ttu-id="1e515-105">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="1e515-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e515-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1e515-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="1e515-107">Id</span><span class="sxs-lookup"><span data-stu-id="1e515-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="1e515-108">Regel</span><span class="sxs-lookup"><span data-stu-id="1e515-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1e515-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1e515-109">DESCRIPTION</span></span>

<span data-ttu-id="1e515-110">Verwijdert een opgegeven autorisatieregel uit de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="1e515-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="1e515-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1e515-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="1e515-112">-Force</span><span class="sxs-lookup"><span data-stu-id="1e515-112">-Force</span></span>

<span data-ttu-id="1e515-113">De cmdlet uitvoert zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="1e515-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="1e515-114">Standaard wordt de cmdlet gevraagd om bevestiging voordat u doorgaat.</span><span class="sxs-lookup"><span data-stu-id="1e515-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="1e515-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="1e515-115">Aliases</span></span>                              | <span data-ttu-id="1e515-116">geen</span><span class="sxs-lookup"><span data-stu-id="1e515-116">none</span></span>                                 |
| <span data-ttu-id="1e515-117">Nodig?</span><span class="sxs-lookup"><span data-stu-id="1e515-117">Required?</span></span>                            | <span data-ttu-id="1e515-118">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-118">false</span></span>                                |
| <span data-ttu-id="1e515-119">Positie?</span><span class="sxs-lookup"><span data-stu-id="1e515-119">Position?</span></span>                            | <span data-ttu-id="1e515-120">Met de naam</span><span class="sxs-lookup"><span data-stu-id="1e515-120">named</span></span>                                |
| <span data-ttu-id="1e515-121">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="1e515-121">Default Value</span></span>                        | <span data-ttu-id="1e515-122">geen</span><span class="sxs-lookup"><span data-stu-id="1e515-122">none</span></span>                                 |
| <span data-ttu-id="1e515-123">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1e515-124">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-124">false</span></span>                                |
| <span data-ttu-id="1e515-125">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1e515-126">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="1e515-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1e515-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="1e515-128">Hiermee geeft u de id's van een of meer regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1e515-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="1e515-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="1e515-129">Aliases</span></span>                              | <span data-ttu-id="1e515-130">geen</span><span class="sxs-lookup"><span data-stu-id="1e515-130">none</span></span>                                 |
| <span data-ttu-id="1e515-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="1e515-131">Required?</span></span>                            | <span data-ttu-id="1e515-132">De waarde True</span><span class="sxs-lookup"><span data-stu-id="1e515-132">true</span></span>                                 |
| <span data-ttu-id="1e515-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="1e515-133">Position?</span></span>                            | <span data-ttu-id="1e515-134">2</span><span class="sxs-lookup"><span data-stu-id="1e515-134">2</span></span>                                    |
| <span data-ttu-id="1e515-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="1e515-135">Default Value</span></span>                        | <span data-ttu-id="1e515-136">geen</span><span class="sxs-lookup"><span data-stu-id="1e515-136">none</span></span>                                 |
| <span data-ttu-id="1e515-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1e515-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1e515-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="1e515-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1e515-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="1e515-141">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1e515-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="1e515-142">Hiermee geeft u de regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1e515-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="1e515-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="1e515-143">Aliases</span></span>                              | <span data-ttu-id="1e515-144">geen</span><span class="sxs-lookup"><span data-stu-id="1e515-144">none</span></span>                                 |
| <span data-ttu-id="1e515-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="1e515-145">Required?</span></span>                            | <span data-ttu-id="1e515-146">De waarde True</span><span class="sxs-lookup"><span data-stu-id="1e515-146">true</span></span>                                 |
| <span data-ttu-id="1e515-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="1e515-147">Position?</span></span>                            | <span data-ttu-id="1e515-148">2</span><span class="sxs-lookup"><span data-stu-id="1e515-148">2</span></span>                                    |
| <span data-ttu-id="1e515-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="1e515-149">Default Value</span></span>                        | <span data-ttu-id="1e515-150">geen</span><span class="sxs-lookup"><span data-stu-id="1e515-150">none</span></span>                                 |
| <span data-ttu-id="1e515-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1e515-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="1e515-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="1e515-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1e515-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="1e515-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1e515-155">-Confirm</span></span>

<span data-ttu-id="1e515-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1e515-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="1e515-157">Nodig?</span><span class="sxs-lookup"><span data-stu-id="1e515-157">Required?</span></span>                            | <span data-ttu-id="1e515-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-158">false</span></span>                                |
| <span data-ttu-id="1e515-159">Positie?</span><span class="sxs-lookup"><span data-stu-id="1e515-159">Position?</span></span>                            | <span data-ttu-id="1e515-160">Met de naam</span><span class="sxs-lookup"><span data-stu-id="1e515-160">named</span></span>                                |
| <span data-ttu-id="1e515-161">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="1e515-161">Default Value</span></span>                        | <span data-ttu-id="1e515-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-162">false</span></span>                                |
| <span data-ttu-id="1e515-163">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1e515-164">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-164">false</span></span>                                |
| <span data-ttu-id="1e515-165">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1e515-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="1e515-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1e515-167">-WhatIf</span></span>

<span data-ttu-id="1e515-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1e515-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1e515-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1e515-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="1e515-170">Nodig?</span><span class="sxs-lookup"><span data-stu-id="1e515-170">Required?</span></span>                            | <span data-ttu-id="1e515-171">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-171">false</span></span>                                |
| <span data-ttu-id="1e515-172">Positie?</span><span class="sxs-lookup"><span data-stu-id="1e515-172">Position?</span></span>                            | <span data-ttu-id="1e515-173">Met de naam</span><span class="sxs-lookup"><span data-stu-id="1e515-173">named</span></span>                                |
| <span data-ttu-id="1e515-174">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="1e515-174">Default Value</span></span>                        | <span data-ttu-id="1e515-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-175">false</span></span>                                |
| <span data-ttu-id="1e515-176">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1e515-177">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-177">false</span></span>                                |
| <span data-ttu-id="1e515-178">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="1e515-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1e515-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="1e515-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1e515-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1e515-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1e515-181">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="1e515-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1e515-182">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1e515-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="1e515-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="1e515-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="1e515-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="1e515-184">int\[\]</span></span>

<span data-ttu-id="1e515-185">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="1e515-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="1e515-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="1e515-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="1e515-187">Deze cmdlet accepteert een matrix van gehele getallen of een matrix met objecten PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="1e515-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="1e515-188">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1e515-188">OUTPUTS</span></span>

<span data-ttu-id="1e515-189">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1e515-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="1e515-190">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1e515-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1e515-191">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="1e515-191">EXAMPLE 1</span></span>

<span data-ttu-id="1e515-192">In dit voorbeeld verwijdert u de autorisatieregel met een ID van *2*.</span><span class="sxs-lookup"><span data-stu-id="1e515-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="1e515-193">Voorbeeld 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="1e515-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="1e515-194">In dit voorbeeld verwijdert alle autorisatieregels en bevestiging van de gebruiker is ook vereist.</span><span class="sxs-lookup"><span data-stu-id="1e515-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="1e515-195">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="1e515-195">Related topics</span></span>

- [<span data-ttu-id="1e515-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1e515-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="1e515-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1e515-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="1e515-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="1e515-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="1e515-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1e515-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
