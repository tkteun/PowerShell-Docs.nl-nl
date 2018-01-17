---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: fb2937397616160c70b056e412e42fb8ff4c2f27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="cceb4-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cceb4-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="cceb4-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="cceb4-104">SYNOPSIS</span></span>

<span data-ttu-id="cceb4-105">Hiermee wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.</span><span class="sxs-lookup"><span data-stu-id="cceb4-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="cceb4-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cceb4-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="cceb4-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="cceb4-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="cceb4-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="cceb4-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="cceb4-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cceb4-109">DESCRIPTION</span></span>

<span data-ttu-id="cceb4-110">De **Test-PswaAuthorizationRule** cmdlet wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.</span><span class="sxs-lookup"><span data-stu-id="cceb4-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="cceb4-111">Deze cmdlet kan ook worden gebruikt voor het testen van autorisatieregels om te valideren dat een bepaalde gebruiker, computer of eindpunt toegangsaanvraag is geautoriseerd.</span><span class="sxs-lookup"><span data-stu-id="cceb4-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="cceb4-112">Deze cmdlet evalueert standaard alle regels in het bestand met autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="cceb4-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="cceb4-113">U kunt echter een subset van regels voor het testen van opgeven.</span><span class="sxs-lookup"><span data-stu-id="cceb4-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="cceb4-114">U kunt deze cmdlet gebruiken om op te lossen verificatiefouten.</span><span class="sxs-lookup"><span data-stu-id="cceb4-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="cceb4-115">De parameters voor deze cmdlet overeen met velden op de pagina van de aanmelding Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="cceb4-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="cceb4-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cceb4-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="cceb4-117">-ComputerName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="cceb4-118">Hiermee geeft u de naam van de computer om te testen.</span><span class="sxs-lookup"><span data-stu-id="cceb4-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="cceb4-119">Aliassen</span><span class="sxs-lookup"><span data-stu-id="cceb4-119">Aliases</span></span>                              | <span data-ttu-id="cceb4-120">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-120">none</span></span>                                 |
| <span data-ttu-id="cceb4-121">Nodig?</span><span class="sxs-lookup"><span data-stu-id="cceb4-121">Required?</span></span>                            | <span data-ttu-id="cceb4-122">De waarde True</span><span class="sxs-lookup"><span data-stu-id="cceb4-122">true</span></span>                                 |
| <span data-ttu-id="cceb4-123">Positie?</span><span class="sxs-lookup"><span data-stu-id="cceb4-123">Position?</span></span>                            | <span data-ttu-id="cceb4-124">2</span><span class="sxs-lookup"><span data-stu-id="cceb4-124">2</span></span>                                    |
| <span data-ttu-id="cceb4-125">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="cceb4-125">Default Value</span></span>                        | <span data-ttu-id="cceb4-126">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-126">none</span></span>                                 |
| <span data-ttu-id="cceb4-127">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cceb4-128">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-128">false</span></span>                                |
| <span data-ttu-id="cceb4-129">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cceb4-130">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="cceb4-131">-ConfigurationName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="cceb4-132">Geeft de naam van de Windows PowerShell-sessieconfiguratie, ook wel bekend als eindpunt of runspace om te testen.</span><span class="sxs-lookup"><span data-stu-id="cceb4-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="cceb4-133">Aliassen</span><span class="sxs-lookup"><span data-stu-id="cceb4-133">Aliases</span></span>                              | <span data-ttu-id="cceb4-134">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-134">none</span></span>                                 |
| <span data-ttu-id="cceb4-135">Nodig?</span><span class="sxs-lookup"><span data-stu-id="cceb4-135">Required?</span></span>                            | <span data-ttu-id="cceb4-136">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-136">false</span></span>                                |
| <span data-ttu-id="cceb4-137">Positie?</span><span class="sxs-lookup"><span data-stu-id="cceb4-137">Position?</span></span>                            | <span data-ttu-id="cceb4-138">3</span><span class="sxs-lookup"><span data-stu-id="cceb4-138">3</span></span>                                    |
| <span data-ttu-id="cceb4-139">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="cceb4-139">Default Value</span></span>                        | <span data-ttu-id="cceb4-140">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-140">none</span></span>                                 |
| <span data-ttu-id="cceb4-141">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cceb4-142">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-142">false</span></span>                                |
| <span data-ttu-id="cceb4-143">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cceb4-144">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="cceb4-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="cceb4-146">Hiermee geeft u de URI voor het testen van verbinding.</span><span class="sxs-lookup"><span data-stu-id="cceb4-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="cceb4-147">Aliassen</span><span class="sxs-lookup"><span data-stu-id="cceb4-147">Aliases</span></span>                              | <span data-ttu-id="cceb4-148">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-148">none</span></span>                                 |
| <span data-ttu-id="cceb4-149">Nodig?</span><span class="sxs-lookup"><span data-stu-id="cceb4-149">Required?</span></span>                            | <span data-ttu-id="cceb4-150">De waarde True</span><span class="sxs-lookup"><span data-stu-id="cceb4-150">true</span></span>                                 |
| <span data-ttu-id="cceb4-151">Positie?</span><span class="sxs-lookup"><span data-stu-id="cceb4-151">Position?</span></span>                            | <span data-ttu-id="cceb4-152">2</span><span class="sxs-lookup"><span data-stu-id="cceb4-152">2</span></span>                                    |
| <span data-ttu-id="cceb4-153">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="cceb4-153">Default Value</span></span>                        | <span data-ttu-id="cceb4-154">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-154">none</span></span>                                 |
| <span data-ttu-id="cceb4-155">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cceb4-156">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-156">false</span></span>                                |
| <span data-ttu-id="cceb4-157">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cceb4-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="cceb4-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="cceb4-160">Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u gebruiken wilt voor het testen van Windows PowerShell-webtoegang autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="cceb4-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="cceb4-161">Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="cceb4-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="cceb4-162">Ophalen van een **PSCredential** -object, dat vereist is voor het testen van autorisatieregels op afstand, voert u de [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cceb4-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="cceb4-163">Aliassen</span><span class="sxs-lookup"><span data-stu-id="cceb4-163">Aliases</span></span>                              | <span data-ttu-id="cceb4-164">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-164">none</span></span>                                 |
| <span data-ttu-id="cceb4-165">Nodig?</span><span class="sxs-lookup"><span data-stu-id="cceb4-165">Required?</span></span>                            | <span data-ttu-id="cceb4-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-166">false</span></span>                                |
| <span data-ttu-id="cceb4-167">Positie?</span><span class="sxs-lookup"><span data-stu-id="cceb4-167">Position?</span></span>                            | <span data-ttu-id="cceb4-168">Met de naam</span><span class="sxs-lookup"><span data-stu-id="cceb4-168">named</span></span>                                |
| <span data-ttu-id="cceb4-169">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="cceb4-169">Default Value</span></span>                        | <span data-ttu-id="cceb4-170">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-170">none</span></span>                                 |
| <span data-ttu-id="cceb4-171">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cceb4-172">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-172">false</span></span>                                |
| <span data-ttu-id="cceb4-173">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cceb4-174">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="cceb4-175">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="cceb4-176">Hiermee geeft u een subset van regels om te testen.</span><span class="sxs-lookup"><span data-stu-id="cceb4-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="cceb4-177">Als deze parameter niet is opgegeven, zijn deze cmdlet van test tegen alle autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="cceb4-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="cceb4-178">Aliassen</span><span class="sxs-lookup"><span data-stu-id="cceb4-178">Aliases</span></span>                              | <span data-ttu-id="cceb4-179">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-179">none</span></span>                                 |
| <span data-ttu-id="cceb4-180">Nodig?</span><span class="sxs-lookup"><span data-stu-id="cceb4-180">Required?</span></span>                            | <span data-ttu-id="cceb4-181">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-181">false</span></span>                                |
| <span data-ttu-id="cceb4-182">Positie?</span><span class="sxs-lookup"><span data-stu-id="cceb4-182">Position?</span></span>                            | <span data-ttu-id="cceb4-183">Met de naam</span><span class="sxs-lookup"><span data-stu-id="cceb4-183">named</span></span>                                |
| <span data-ttu-id="cceb4-184">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="cceb4-184">Default Value</span></span>                        | <span data-ttu-id="cceb4-185">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-185">none</span></span>                                 |
| <span data-ttu-id="cceb4-186">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cceb4-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="cceb4-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="cceb4-188">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cceb4-189">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="cceb4-190">-UserName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="cceb4-191">Hiermee geeft u de naam van de gebruiker om te testen.</span><span class="sxs-lookup"><span data-stu-id="cceb4-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="cceb4-192">Aliassen</span><span class="sxs-lookup"><span data-stu-id="cceb4-192">Aliases</span></span>                              | <span data-ttu-id="cceb4-193">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-193">none</span></span>                                 |
| <span data-ttu-id="cceb4-194">Nodig?</span><span class="sxs-lookup"><span data-stu-id="cceb4-194">Required?</span></span>                            | <span data-ttu-id="cceb4-195">De waarde True</span><span class="sxs-lookup"><span data-stu-id="cceb4-195">true</span></span>                                 |
| <span data-ttu-id="cceb4-196">Positie?</span><span class="sxs-lookup"><span data-stu-id="cceb4-196">Position?</span></span>                            | <span data-ttu-id="cceb4-197">1</span><span class="sxs-lookup"><span data-stu-id="cceb4-197">1</span></span>                                    |
| <span data-ttu-id="cceb4-198">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="cceb4-198">Default Value</span></span>                        | <span data-ttu-id="cceb4-199">geen</span><span class="sxs-lookup"><span data-stu-id="cceb4-199">none</span></span>                                 |
| <span data-ttu-id="cceb4-200">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cceb4-201">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-201">false</span></span>                                |
| <span data-ttu-id="cceb4-202">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="cceb4-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cceb4-203">onjuist</span><span class="sxs-lookup"><span data-stu-id="cceb4-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="cceb4-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="cceb4-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="cceb4-205">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="cceb4-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="cceb4-206">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cceb4-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="cceb4-207">INVOER</span><span class="sxs-lookup"><span data-stu-id="cceb4-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="cceb4-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="cceb4-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="cceb4-209">Deze cmdlet accepteert een matrix met objecten PswaAuthorizationRule als invoer.</span><span class="sxs-lookup"><span data-stu-id="cceb4-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="cceb4-210">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="cceb4-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="cceb4-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="cceb4-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="cceb4-212">Deze cmdlet produceert een matrix met objecten PswaAuthorizationRule als uitvoer.</span><span class="sxs-lookup"><span data-stu-id="cceb4-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="cceb4-213">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cceb4-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="cceb4-214">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="cceb4-214">EXAMPLE 1</span></span>

<span data-ttu-id="cceb4-215">In dit voorbeeld alle autorisatieregels gecontroleerd om de regels waarmee de gebruiker weer te geven *contoso\\mhanson* verbinding maken met de computer *srv2* en een Windows PowerShell-sessie gebruiken configuratie met de naam *testen*.</span><span class="sxs-lookup"><span data-stu-id="cceb4-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="cceb4-216">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="cceb4-216">EXAMPLE 2</span></span>

<span data-ttu-id="cceb4-217">In dit voorbeeld tests alle autorisatieregels om te controleren welke autorisatieregels gelden voor de gebruiker *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="cceb4-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="cceb4-218">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="cceb4-218">Related topics</span></span>

- [<span data-ttu-id="cceb4-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cceb4-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="cceb4-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cceb4-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="cceb4-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="cceb4-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="cceb4-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cceb4-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
