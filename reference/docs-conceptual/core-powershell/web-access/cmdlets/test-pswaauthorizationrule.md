---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="b10bc-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b10bc-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="b10bc-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b10bc-104">SYNOPSIS</span></span>

<span data-ttu-id="b10bc-105">Hiermee wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.</span><span class="sxs-lookup"><span data-stu-id="b10bc-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="b10bc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b10bc-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="b10bc-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="b10bc-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="b10bc-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="b10bc-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b10bc-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b10bc-109">DESCRIPTION</span></span>

<span data-ttu-id="b10bc-110">De **Test-PswaAuthorizationRule** cmdlet wordt gecontroleerd of een regel voor een opgegeven gebruiker, computer of -eindpunt bestaat.</span><span class="sxs-lookup"><span data-stu-id="b10bc-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="b10bc-111">Deze cmdlet kan ook worden gebruikt voor het testen van autorisatieregels om te valideren dat een bepaalde gebruiker, computer of eindpunt toegangsaanvraag is geautoriseerd.</span><span class="sxs-lookup"><span data-stu-id="b10bc-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="b10bc-112">Deze cmdlet evalueert standaard alle regels in het bestand met autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="b10bc-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="b10bc-113">U kunt echter een subset van regels voor het testen van opgeven.</span><span class="sxs-lookup"><span data-stu-id="b10bc-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="b10bc-114">U kunt deze cmdlet gebruiken om op te lossen verificatiefouten.</span><span class="sxs-lookup"><span data-stu-id="b10bc-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="b10bc-115">De parameters voor deze cmdlet overeen met velden op de pagina van de aanmelding Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="b10bc-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="b10bc-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b10bc-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="b10bc-117">-ComputerName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="b10bc-118">Hiermee geeft u de naam van de computer om te testen.</span><span class="sxs-lookup"><span data-stu-id="b10bc-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="b10bc-119">Aliassen</span><span class="sxs-lookup"><span data-stu-id="b10bc-119">Aliases</span></span>                              | <span data-ttu-id="b10bc-120">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-120">none</span></span>                                 |
| <span data-ttu-id="b10bc-121">Nodig?</span><span class="sxs-lookup"><span data-stu-id="b10bc-121">Required?</span></span>                            | <span data-ttu-id="b10bc-122">De waarde True</span><span class="sxs-lookup"><span data-stu-id="b10bc-122">true</span></span>                                 |
| <span data-ttu-id="b10bc-123">Positie?</span><span class="sxs-lookup"><span data-stu-id="b10bc-123">Position?</span></span>                            | <span data-ttu-id="b10bc-124">2</span><span class="sxs-lookup"><span data-stu-id="b10bc-124">2</span></span>                                    |
| <span data-ttu-id="b10bc-125">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="b10bc-125">Default Value</span></span>                        | <span data-ttu-id="b10bc-126">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-126">none</span></span>                                 |
| <span data-ttu-id="b10bc-127">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b10bc-128">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-128">false</span></span>                                |
| <span data-ttu-id="b10bc-129">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b10bc-130">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="b10bc-131">-ConfigurationName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="b10bc-132">Geeft de naam van de Windows PowerShell-sessieconfiguratie, ook wel bekend als eindpunt of runspace om te testen.</span><span class="sxs-lookup"><span data-stu-id="b10bc-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="b10bc-133">Aliassen</span><span class="sxs-lookup"><span data-stu-id="b10bc-133">Aliases</span></span>                              | <span data-ttu-id="b10bc-134">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-134">none</span></span>                                 |
| <span data-ttu-id="b10bc-135">Nodig?</span><span class="sxs-lookup"><span data-stu-id="b10bc-135">Required?</span></span>                            | <span data-ttu-id="b10bc-136">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-136">false</span></span>                                |
| <span data-ttu-id="b10bc-137">Positie?</span><span class="sxs-lookup"><span data-stu-id="b10bc-137">Position?</span></span>                            | <span data-ttu-id="b10bc-138">3</span><span class="sxs-lookup"><span data-stu-id="b10bc-138">3</span></span>                                    |
| <span data-ttu-id="b10bc-139">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="b10bc-139">Default Value</span></span>                        | <span data-ttu-id="b10bc-140">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-140">none</span></span>                                 |
| <span data-ttu-id="b10bc-141">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b10bc-142">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-142">false</span></span>                                |
| <span data-ttu-id="b10bc-143">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b10bc-144">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="b10bc-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="b10bc-146">Hiermee geeft u de URI voor het testen van verbinding.</span><span class="sxs-lookup"><span data-stu-id="b10bc-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="b10bc-147">Aliassen</span><span class="sxs-lookup"><span data-stu-id="b10bc-147">Aliases</span></span>                              | <span data-ttu-id="b10bc-148">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-148">none</span></span>                                 |
| <span data-ttu-id="b10bc-149">Nodig?</span><span class="sxs-lookup"><span data-stu-id="b10bc-149">Required?</span></span>                            | <span data-ttu-id="b10bc-150">De waarde True</span><span class="sxs-lookup"><span data-stu-id="b10bc-150">true</span></span>                                 |
| <span data-ttu-id="b10bc-151">Positie?</span><span class="sxs-lookup"><span data-stu-id="b10bc-151">Position?</span></span>                            | <span data-ttu-id="b10bc-152">2</span><span class="sxs-lookup"><span data-stu-id="b10bc-152">2</span></span>                                    |
| <span data-ttu-id="b10bc-153">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="b10bc-153">Default Value</span></span>                        | <span data-ttu-id="b10bc-154">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-154">none</span></span>                                 |
| <span data-ttu-id="b10bc-155">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b10bc-156">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-156">false</span></span>                                |
| <span data-ttu-id="b10bc-157">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b10bc-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="b10bc-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="b10bc-160">Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u gebruiken wilt voor het testen van Windows PowerShell-webtoegang autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="b10bc-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="b10bc-161">Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b10bc-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="b10bc-162">Ophalen van een **PSCredential** -object, dat vereist is voor het testen van autorisatieregels op afstand, voert u de [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b10bc-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="b10bc-163">Aliassen</span><span class="sxs-lookup"><span data-stu-id="b10bc-163">Aliases</span></span>                              | <span data-ttu-id="b10bc-164">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-164">none</span></span>                                 |
| <span data-ttu-id="b10bc-165">Nodig?</span><span class="sxs-lookup"><span data-stu-id="b10bc-165">Required?</span></span>                            | <span data-ttu-id="b10bc-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-166">false</span></span>                                |
| <span data-ttu-id="b10bc-167">Positie?</span><span class="sxs-lookup"><span data-stu-id="b10bc-167">Position?</span></span>                            | <span data-ttu-id="b10bc-168">Met de naam</span><span class="sxs-lookup"><span data-stu-id="b10bc-168">named</span></span>                                |
| <span data-ttu-id="b10bc-169">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="b10bc-169">Default Value</span></span>                        | <span data-ttu-id="b10bc-170">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-170">none</span></span>                                 |
| <span data-ttu-id="b10bc-171">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b10bc-172">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-172">false</span></span>                                |
| <span data-ttu-id="b10bc-173">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b10bc-174">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="b10bc-175">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="b10bc-176">Hiermee geeft u een subset van regels om te testen.</span><span class="sxs-lookup"><span data-stu-id="b10bc-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="b10bc-177">Als deze parameter niet is opgegeven, zijn deze cmdlet van test tegen alle autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="b10bc-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="b10bc-178">Aliassen</span><span class="sxs-lookup"><span data-stu-id="b10bc-178">Aliases</span></span>                              | <span data-ttu-id="b10bc-179">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-179">none</span></span>                                 |
| <span data-ttu-id="b10bc-180">Nodig?</span><span class="sxs-lookup"><span data-stu-id="b10bc-180">Required?</span></span>                            | <span data-ttu-id="b10bc-181">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-181">false</span></span>                                |
| <span data-ttu-id="b10bc-182">Positie?</span><span class="sxs-lookup"><span data-stu-id="b10bc-182">Position?</span></span>                            | <span data-ttu-id="b10bc-183">Met de naam</span><span class="sxs-lookup"><span data-stu-id="b10bc-183">named</span></span>                                |
| <span data-ttu-id="b10bc-184">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="b10bc-184">Default Value</span></span>                        | <span data-ttu-id="b10bc-185">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-185">none</span></span>                                 |
| <span data-ttu-id="b10bc-186">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b10bc-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="b10bc-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="b10bc-188">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b10bc-189">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="b10bc-190">-UserName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="b10bc-191">Hiermee geeft u de naam van de gebruiker om te testen.</span><span class="sxs-lookup"><span data-stu-id="b10bc-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="b10bc-192">Aliassen</span><span class="sxs-lookup"><span data-stu-id="b10bc-192">Aliases</span></span>                              | <span data-ttu-id="b10bc-193">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-193">none</span></span>                                 |
| <span data-ttu-id="b10bc-194">Nodig?</span><span class="sxs-lookup"><span data-stu-id="b10bc-194">Required?</span></span>                            | <span data-ttu-id="b10bc-195">De waarde True</span><span class="sxs-lookup"><span data-stu-id="b10bc-195">true</span></span>                                 |
| <span data-ttu-id="b10bc-196">Positie?</span><span class="sxs-lookup"><span data-stu-id="b10bc-196">Position?</span></span>                            | <span data-ttu-id="b10bc-197">1</span><span class="sxs-lookup"><span data-stu-id="b10bc-197">1</span></span>                                    |
| <span data-ttu-id="b10bc-198">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="b10bc-198">Default Value</span></span>                        | <span data-ttu-id="b10bc-199">geen</span><span class="sxs-lookup"><span data-stu-id="b10bc-199">none</span></span>                                 |
| <span data-ttu-id="b10bc-200">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b10bc-201">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-201">false</span></span>                                |
| <span data-ttu-id="b10bc-202">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="b10bc-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b10bc-203">onjuist</span><span class="sxs-lookup"><span data-stu-id="b10bc-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b10bc-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b10bc-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b10bc-205">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b10bc-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b10bc-206">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b10bc-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b10bc-207">INVOER</span><span class="sxs-lookup"><span data-stu-id="b10bc-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="b10bc-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="b10bc-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="b10bc-209">Deze cmdlet accepteert een matrix met objecten PswaAuthorizationRule als invoer.</span><span class="sxs-lookup"><span data-stu-id="b10bc-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="b10bc-210">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="b10bc-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="b10bc-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="b10bc-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="b10bc-212">Deze cmdlet produceert een matrix met objecten PswaAuthorizationRule als uitvoer.</span><span class="sxs-lookup"><span data-stu-id="b10bc-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="b10bc-213">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b10bc-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b10bc-214">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="b10bc-214">EXAMPLE 1</span></span>

<span data-ttu-id="b10bc-215">In dit voorbeeld alle autorisatieregels gecontroleerd om de regels waarmee de gebruiker weer te geven *contoso\\mhanson* verbinding maken met de computer *srv2* en een Windows PowerShell-sessie gebruiken configuratie met de naam *testen*.</span><span class="sxs-lookup"><span data-stu-id="b10bc-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="b10bc-216">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="b10bc-216">EXAMPLE 2</span></span>

<span data-ttu-id="b10bc-217">In dit voorbeeld tests alle autorisatieregels om te controleren welke autorisatieregels gelden voor de gebruiker *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="b10bc-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="b10bc-218">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="b10bc-218">Related topics</span></span>

- [<span data-ttu-id="b10bc-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b10bc-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b10bc-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b10bc-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b10bc-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b10bc-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="b10bc-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b10bc-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)