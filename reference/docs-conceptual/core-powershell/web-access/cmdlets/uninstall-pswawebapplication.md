---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: Uninstall-pswawebapplication
ms.technology: powershell
ms.openlocfilehash: cc54c94426d754ff2d3bf658e3e92083f02cd6c7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="d2a48-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="d2a48-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2a48-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d2a48-104">SYNOPSIS</span></span>

<span data-ttu-id="d2a48-105">Hiermee verwijdert u de webtoepassing Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="d2a48-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2a48-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d2a48-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="d2a48-107">Standaardinstelling</span><span class="sxs-lookup"><span data-stu-id="d2a48-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="d2a48-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d2a48-108">DESCRIPTION</span></span>

<span data-ttu-id="d2a48-109">De **Uninstall-PswaWebApplication** cmdlet verwijdert u de Windows PowerShell-webtoepassing en verwijdert u de website in IIS.</span><span class="sxs-lookup"><span data-stu-id="d2a48-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="d2a48-110">De cmdlet worden niet verwijderd IIS of andere onderdelen geïnstalleerd, omdat ze zijn vereist voor Windows PowerShell om uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d2a48-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="d2a48-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2a48-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="d2a48-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="d2a48-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="d2a48-113">Geeft aan dat de testcertificaten gemaakt door de **installeren\_PswaWebApplication** cmdlet (met de **UseTestCertificate** parameter) is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d2a48-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="d2a48-114">Het testcertificaat met dezelfde naam als het account dat is gemaakt door de **Install-PswaWebApplication** cmdlet wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d2a48-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="d2a48-115">Aliassen</span><span class="sxs-lookup"><span data-stu-id="d2a48-115">Aliases</span></span>                              | <span data-ttu-id="d2a48-116">geen</span><span class="sxs-lookup"><span data-stu-id="d2a48-116">none</span></span>                                 |
| <span data-ttu-id="d2a48-117">Nodig?</span><span class="sxs-lookup"><span data-stu-id="d2a48-117">Required?</span></span>                            | <span data-ttu-id="d2a48-118">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-118">false</span></span>                                |
| <span data-ttu-id="d2a48-119">Positie?</span><span class="sxs-lookup"><span data-stu-id="d2a48-119">Position?</span></span>                            | <span data-ttu-id="d2a48-120">Met de naam</span><span class="sxs-lookup"><span data-stu-id="d2a48-120">named</span></span>                                |
| <span data-ttu-id="d2a48-121">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="d2a48-121">Default Value</span></span>                        | <span data-ttu-id="d2a48-122">De waarde True</span><span class="sxs-lookup"><span data-stu-id="d2a48-122">true</span></span>                                 |
| <span data-ttu-id="d2a48-123">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d2a48-124">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-124">false</span></span>                                |
| <span data-ttu-id="d2a48-125">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d2a48-126">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="d2a48-127">-WebApplicationName &lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="d2a48-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="d2a48-128">Hiermee geeft u de naam van de webtoepassing te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d2a48-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="d2a48-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="d2a48-129">Aliases</span></span>                              | <span data-ttu-id="d2a48-130">geen</span><span class="sxs-lookup"><span data-stu-id="d2a48-130">none</span></span>                                 |
| <span data-ttu-id="d2a48-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="d2a48-131">Required?</span></span>                            | <span data-ttu-id="d2a48-132">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-132">false</span></span>                                |
| <span data-ttu-id="d2a48-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="d2a48-133">Position?</span></span>                            | <span data-ttu-id="d2a48-134">1</span><span class="sxs-lookup"><span data-stu-id="d2a48-134">1</span></span>                                    |
| <span data-ttu-id="d2a48-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="d2a48-135">Default Value</span></span>                        | <span data-ttu-id="d2a48-136">pswa</span><span class="sxs-lookup"><span data-stu-id="d2a48-136">pswa</span></span>                                 |
| <span data-ttu-id="d2a48-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d2a48-138">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-138">false</span></span>                                |
| <span data-ttu-id="d2a48-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d2a48-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="d2a48-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="d2a48-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="d2a48-142">Geeft de naam van de website waarop de webtoepassing is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d2a48-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="d2a48-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="d2a48-143">Aliases</span></span>                              | <span data-ttu-id="d2a48-144">geen</span><span class="sxs-lookup"><span data-stu-id="d2a48-144">none</span></span>                                 |
| <span data-ttu-id="d2a48-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="d2a48-145">Required?</span></span>                            | <span data-ttu-id="d2a48-146">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-146">false</span></span>                                |
| <span data-ttu-id="d2a48-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="d2a48-147">Position?</span></span>                            | <span data-ttu-id="d2a48-148">Met de naam</span><span class="sxs-lookup"><span data-stu-id="d2a48-148">named</span></span>                                |
| <span data-ttu-id="d2a48-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="d2a48-149">Default Value</span></span>                        | <span data-ttu-id="d2a48-150">Standaardwebsite</span><span class="sxs-lookup"><span data-stu-id="d2a48-150">Default Web Site</span></span>                     |
| <span data-ttu-id="d2a48-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d2a48-152">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-152">false</span></span>                                |
| <span data-ttu-id="d2a48-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d2a48-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="d2a48-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d2a48-155">-Confirm</span></span>

<span data-ttu-id="d2a48-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d2a48-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="d2a48-157">Nodig?</span><span class="sxs-lookup"><span data-stu-id="d2a48-157">Required?</span></span>                            | <span data-ttu-id="d2a48-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-158">false</span></span>                                |
| <span data-ttu-id="d2a48-159">Positie?</span><span class="sxs-lookup"><span data-stu-id="d2a48-159">Position?</span></span>                            | <span data-ttu-id="d2a48-160">Met de naam</span><span class="sxs-lookup"><span data-stu-id="d2a48-160">named</span></span>                                |
| <span data-ttu-id="d2a48-161">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="d2a48-161">Default Value</span></span>                        | <span data-ttu-id="d2a48-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-162">false</span></span>                                |
| <span data-ttu-id="d2a48-163">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d2a48-164">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-164">false</span></span>                                |
| <span data-ttu-id="d2a48-165">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d2a48-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="d2a48-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d2a48-167">-WhatIf</span></span>

<span data-ttu-id="d2a48-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d2a48-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d2a48-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2a48-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="d2a48-170">Nodig?</span><span class="sxs-lookup"><span data-stu-id="d2a48-170">Required?</span></span>                            | <span data-ttu-id="d2a48-171">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-171">false</span></span>                                |
| <span data-ttu-id="d2a48-172">Positie?</span><span class="sxs-lookup"><span data-stu-id="d2a48-172">Position?</span></span>                            | <span data-ttu-id="d2a48-173">Met de naam</span><span class="sxs-lookup"><span data-stu-id="d2a48-173">named</span></span>                                |
| <span data-ttu-id="d2a48-174">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="d2a48-174">Default Value</span></span>                        | <span data-ttu-id="d2a48-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-175">false</span></span>                                |
| <span data-ttu-id="d2a48-176">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d2a48-177">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-177">false</span></span>                                |
| <span data-ttu-id="d2a48-178">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="d2a48-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d2a48-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="d2a48-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="d2a48-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="d2a48-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="d2a48-181">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="d2a48-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="d2a48-182">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d2a48-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="d2a48-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="d2a48-183">INPUTS</span></span>

<span data-ttu-id="d2a48-184">Deze cmdlet heeft geen invoer.</span><span class="sxs-lookup"><span data-stu-id="d2a48-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="d2a48-185">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="d2a48-185">OUTPUTS</span></span>

<span data-ttu-id="d2a48-186">Deze cmdlet retourneert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d2a48-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="d2a48-187">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d2a48-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="d2a48-188">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="d2a48-188">EXAMPLE 1</span></span>

<span data-ttu-id="d2a48-189">Deze opdracht verwijdert u de Windows PowerShell-webtoepassing.</span><span class="sxs-lookup"><span data-stu-id="d2a48-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="d2a48-190">Deze cmdlet kunt u de Windows PowerShell-webtoepassing verwijderen als u met behulp van de standaardwaarden hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d2a48-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="d2a48-191">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="d2a48-191">EXAMPLE 2</span></span>

<span data-ttu-id="d2a48-192">Deze opdracht verwijdert de Windows PowerShell-webtoepassing en Hiermee verwijdert u de testcertificaat dat is gekoppeld aan de toepassing.</span><span class="sxs-lookup"><span data-stu-id="d2a48-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="d2a48-193">Deze cmdlet kunt u de Windows PowerShell-webtoepassing verwijderen als u met behulp van de standaardwaarden zijn geïnstalleerd en een testcertificaat gemaakt.</span><span class="sxs-lookup"><span data-stu-id="d2a48-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="d2a48-194">Voorbeeld 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="d2a48-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="d2a48-195">Deze opdracht verwijdert u de Windows PowerShell-webtoepassing wanneer een aangepaste website en de toepassing tijdens de installatie zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2a48-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="d2a48-196">De opdracht verwijdert u de website met de naam *persoonlijke site* en de toepassing met de naam *testtoepassing* en specificeert de testcertificaten die zijn gekoppeld aan de toepassing worden ook verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d2a48-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="d2a48-197">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="d2a48-197">Related topics</span></span>

- [<span data-ttu-id="d2a48-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d2a48-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="d2a48-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d2a48-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="d2a48-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="d2a48-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="d2a48-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d2a48-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="d2a48-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d2a48-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
