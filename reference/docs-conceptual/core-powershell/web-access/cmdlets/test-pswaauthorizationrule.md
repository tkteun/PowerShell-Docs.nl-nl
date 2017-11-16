---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="8e525-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e525-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="8e525-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8e525-104">SYNOPSIS</span></span>

<span data-ttu-id="8e525-105">Hiermee wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.</span><span class="sxs-lookup"><span data-stu-id="8e525-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e525-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8e525-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="8e525-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="8e525-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="8e525-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8e525-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="8e525-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8e525-109">DESCRIPTION</span></span>

<span data-ttu-id="8e525-110">De **Test-PswaAuthorizationRule** cmdlet wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.</span><span class="sxs-lookup"><span data-stu-id="8e525-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="8e525-111">Deze cmdlet kan ook worden gebruikt voor het testen van autorisatieregels om te valideren dat een bepaalde gebruiker, computer of eindpunt toegangsaanvraag is geautoriseerd.</span><span class="sxs-lookup"><span data-stu-id="8e525-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="8e525-112">Deze cmdlet evalueert standaard alle regels in het bestand met autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="8e525-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="8e525-113">U kunt echter een subset van regels voor het testen van opgeven.</span><span class="sxs-lookup"><span data-stu-id="8e525-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="8e525-114">U kunt deze cmdlet gebruiken om op te lossen verificatiefouten.</span><span class="sxs-lookup"><span data-stu-id="8e525-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="8e525-115">De parameters voor deze cmdlet overeen met velden op de pagina van de aanmelding Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="8e525-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="8e525-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8e525-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="8e525-117">-ComputerName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="8e525-118">Hiermee geeft u de naam van de computer om te testen.</span><span class="sxs-lookup"><span data-stu-id="8e525-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8e525-119">Aliassen</span><span class="sxs-lookup"><span data-stu-id="8e525-119">Aliases</span></span>                              | <span data-ttu-id="8e525-120">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-120">none</span></span>                                 |
| <span data-ttu-id="8e525-121">Nodig?</span><span class="sxs-lookup"><span data-stu-id="8e525-121">Required?</span></span>                            | <span data-ttu-id="8e525-122">De waarde True</span><span class="sxs-lookup"><span data-stu-id="8e525-122">true</span></span>                                 |
| <span data-ttu-id="8e525-123">Positie?</span><span class="sxs-lookup"><span data-stu-id="8e525-123">Position?</span></span>                            | <span data-ttu-id="8e525-124">2</span><span class="sxs-lookup"><span data-stu-id="8e525-124">2</span></span>                                    |
| <span data-ttu-id="8e525-125">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="8e525-125">Default Value</span></span>                        | <span data-ttu-id="8e525-126">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-126">none</span></span>                                 |
| <span data-ttu-id="8e525-127">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e525-128">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-128">false</span></span>                                |
| <span data-ttu-id="8e525-129">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e525-130">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="8e525-131">-ConfigurationName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="8e525-132">Geeft de naam van de Windows PowerShell-sessieconfiguratie, ook wel bekend als eindpunt of runspace om te testen.</span><span class="sxs-lookup"><span data-stu-id="8e525-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8e525-133">Aliassen</span><span class="sxs-lookup"><span data-stu-id="8e525-133">Aliases</span></span>                              | <span data-ttu-id="8e525-134">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-134">none</span></span>                                 |
| <span data-ttu-id="8e525-135">Nodig?</span><span class="sxs-lookup"><span data-stu-id="8e525-135">Required?</span></span>                            | <span data-ttu-id="8e525-136">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-136">false</span></span>                                |
| <span data-ttu-id="8e525-137">Positie?</span><span class="sxs-lookup"><span data-stu-id="8e525-137">Position?</span></span>                            | <span data-ttu-id="8e525-138">3</span><span class="sxs-lookup"><span data-stu-id="8e525-138">3</span></span>                                    |
| <span data-ttu-id="8e525-139">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="8e525-139">Default Value</span></span>                        | <span data-ttu-id="8e525-140">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-140">none</span></span>                                 |
| <span data-ttu-id="8e525-141">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e525-142">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-142">false</span></span>                                |
| <span data-ttu-id="8e525-143">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e525-144">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="8e525-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="8e525-146">Hiermee geeft u de URI voor het testen van verbinding.</span><span class="sxs-lookup"><span data-stu-id="8e525-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8e525-147">Aliassen</span><span class="sxs-lookup"><span data-stu-id="8e525-147">Aliases</span></span>                              | <span data-ttu-id="8e525-148">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-148">none</span></span>                                 |
| <span data-ttu-id="8e525-149">Nodig?</span><span class="sxs-lookup"><span data-stu-id="8e525-149">Required?</span></span>                            | <span data-ttu-id="8e525-150">De waarde True</span><span class="sxs-lookup"><span data-stu-id="8e525-150">true</span></span>                                 |
| <span data-ttu-id="8e525-151">Positie?</span><span class="sxs-lookup"><span data-stu-id="8e525-151">Position?</span></span>                            | <span data-ttu-id="8e525-152">2</span><span class="sxs-lookup"><span data-stu-id="8e525-152">2</span></span>                                    |
| <span data-ttu-id="8e525-153">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="8e525-153">Default Value</span></span>                        | <span data-ttu-id="8e525-154">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-154">none</span></span>                                 |
| <span data-ttu-id="8e525-155">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e525-156">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-156">false</span></span>                                |
| <span data-ttu-id="8e525-157">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e525-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="8e525-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="8e525-160">Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u gebruiken wilt voor het testen van Windows PowerShell-webtoegang autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="8e525-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="8e525-161">Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8e525-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="8e525-162">Ophalen van een **PSCredential** -object, dat vereist is voor het testen van autorisatieregels op afstand, voert u de [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e525-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="8e525-163">Aliassen</span><span class="sxs-lookup"><span data-stu-id="8e525-163">Aliases</span></span>                              | <span data-ttu-id="8e525-164">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-164">none</span></span>                                 |
| <span data-ttu-id="8e525-165">Nodig?</span><span class="sxs-lookup"><span data-stu-id="8e525-165">Required?</span></span>                            | <span data-ttu-id="8e525-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-166">false</span></span>                                |
| <span data-ttu-id="8e525-167">Positie?</span><span class="sxs-lookup"><span data-stu-id="8e525-167">Position?</span></span>                            | <span data-ttu-id="8e525-168">Met de naam</span><span class="sxs-lookup"><span data-stu-id="8e525-168">named</span></span>                                |
| <span data-ttu-id="8e525-169">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="8e525-169">Default Value</span></span>                        | <span data-ttu-id="8e525-170">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-170">none</span></span>                                 |
| <span data-ttu-id="8e525-171">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e525-172">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-172">false</span></span>                                |
| <span data-ttu-id="8e525-173">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e525-174">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="8e525-175">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="8e525-176">Hiermee geeft u een subset van regels om te testen.</span><span class="sxs-lookup"><span data-stu-id="8e525-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="8e525-177">Als deze parameter niet is opgegeven, zijn deze cmdlet van test tegen alle autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="8e525-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="8e525-178">Aliassen</span><span class="sxs-lookup"><span data-stu-id="8e525-178">Aliases</span></span>                              | <span data-ttu-id="8e525-179">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-179">none</span></span>                                 |
| <span data-ttu-id="8e525-180">Nodig?</span><span class="sxs-lookup"><span data-stu-id="8e525-180">Required?</span></span>                            | <span data-ttu-id="8e525-181">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-181">false</span></span>                                |
| <span data-ttu-id="8e525-182">Positie?</span><span class="sxs-lookup"><span data-stu-id="8e525-182">Position?</span></span>                            | <span data-ttu-id="8e525-183">Met de naam</span><span class="sxs-lookup"><span data-stu-id="8e525-183">named</span></span>                                |
| <span data-ttu-id="8e525-184">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="8e525-184">Default Value</span></span>                        | <span data-ttu-id="8e525-185">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-185">none</span></span>                                 |
| <span data-ttu-id="8e525-186">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e525-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="8e525-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="8e525-188">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e525-189">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="8e525-190">-UserName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="8e525-191">Hiermee geeft u de naam van de gebruiker om te testen.</span><span class="sxs-lookup"><span data-stu-id="8e525-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8e525-192">Aliassen</span><span class="sxs-lookup"><span data-stu-id="8e525-192">Aliases</span></span>                              | <span data-ttu-id="8e525-193">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-193">none</span></span>                                 |
| <span data-ttu-id="8e525-194">Nodig?</span><span class="sxs-lookup"><span data-stu-id="8e525-194">Required?</span></span>                            | <span data-ttu-id="8e525-195">De waarde True</span><span class="sxs-lookup"><span data-stu-id="8e525-195">true</span></span>                                 |
| <span data-ttu-id="8e525-196">Positie?</span><span class="sxs-lookup"><span data-stu-id="8e525-196">Position?</span></span>                            | <span data-ttu-id="8e525-197">1</span><span class="sxs-lookup"><span data-stu-id="8e525-197">1</span></span>                                    |
| <span data-ttu-id="8e525-198">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="8e525-198">Default Value</span></span>                        | <span data-ttu-id="8e525-199">geen</span><span class="sxs-lookup"><span data-stu-id="8e525-199">none</span></span>                                 |
| <span data-ttu-id="8e525-200">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e525-201">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-201">false</span></span>                                |
| <span data-ttu-id="8e525-202">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="8e525-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e525-203">onjuist</span><span class="sxs-lookup"><span data-stu-id="8e525-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="8e525-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="8e525-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="8e525-205">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="8e525-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="8e525-206">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8e525-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="8e525-207">INVOER</span><span class="sxs-lookup"><span data-stu-id="8e525-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8e525-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8e525-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8e525-209">Deze cmdlet accepteert een matrix met objecten PswaAuthorizationRule als invoer.</span><span class="sxs-lookup"><span data-stu-id="8e525-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="8e525-210">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8e525-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8e525-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8e525-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8e525-212">Deze cmdlet produceert een matrix met objecten PswaAuthorizationRule als uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8e525-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="8e525-213">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8e525-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="8e525-214">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="8e525-214">EXAMPLE 1</span></span>

<span data-ttu-id="8e525-215">In dit voorbeeld alle autorisatieregels gecontroleerd om de regels waarmee de gebruiker weer te geven *contoso\\mhanson* verbinding maken met de computer *srv2* en een Windows PowerShell-sessie gebruiken configuratie met de naam *testen*.</span><span class="sxs-lookup"><span data-stu-id="8e525-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="8e525-216">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="8e525-216">EXAMPLE 2</span></span>

<span data-ttu-id="8e525-217">In dit voorbeeld tests alle autorisatieregels om te controleren welke autorisatieregels gelden voor de gebruiker *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="8e525-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="8e525-218">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="8e525-218">Related topics</span></span>

- [<span data-ttu-id="8e525-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e525-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="8e525-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e525-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="8e525-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8e525-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="8e525-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e525-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
