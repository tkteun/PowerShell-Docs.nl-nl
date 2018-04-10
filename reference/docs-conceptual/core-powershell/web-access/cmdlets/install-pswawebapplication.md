---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: pswawebapplication installeren
ms.technology: powershell
ms.openlocfilehash: c7f7768a41b6784d8c29afa1fccf0b855160b777
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="4dde6-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4dde6-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="4dde6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4dde6-104">SYNOPSIS</span></span>

<span data-ttu-id="4dde6-105">Hiermee configureert u de Windows PowerShell® Web Access-webtoepassing in IIS.</span><span class="sxs-lookup"><span data-stu-id="4dde6-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="4dde6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4dde6-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="4dde6-107">Standaardinstelling</span><span class="sxs-lookup"><span data-stu-id="4dde6-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4dde6-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4dde6-108">DESCRIPTION</span></span>

<span data-ttu-id="4dde6-109">De **Install-PswaWebApplication** cmdlet Windows PowerShell-webtoegang webtoepassing configureert.</span><span class="sxs-lookup"><span data-stu-id="4dde6-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="4dde6-110">Deze cmdlet installeert de webtoepassing, koppelt u deze aan een website en eventueel maakt een test SSL certificaat met de **useTestCertificate** parameter.</span><span class="sxs-lookup"><span data-stu-id="4dde6-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="4dde6-111">Voor beveiliging moeten webbeheerders redenen een testcertificaat niet gebruiken voor productieomgevingen.</span><span class="sxs-lookup"><span data-stu-id="4dde6-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="4dde6-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4dde6-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="4dde6-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="4dde6-113">-UseTestCertificate</span></span>

<span data-ttu-id="4dde6-114">Geeft aan dat een testcertificaat is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4dde6-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="4dde6-115">Als deze parameter is ingesteld op true, wordt deze cmdlet een testcertificaat maakt en configureert u de Windows PowerShell Web Access-webtoepassing met het certificaat voor HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="4dde6-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="4dde6-116">Als deze parameter is ingesteld op false, wordt er geen certificaat of een binding gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4dde6-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="4dde6-117">Deze waarde ingesteld op false als een ander certificaat wordt gebruikt voor Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="4dde6-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="4dde6-118">Aliassen</span><span class="sxs-lookup"><span data-stu-id="4dde6-118">Aliases</span></span>                              | <span data-ttu-id="4dde6-119">geen</span><span class="sxs-lookup"><span data-stu-id="4dde6-119">none</span></span>                                 |
| <span data-ttu-id="4dde6-120">Nodig?</span><span class="sxs-lookup"><span data-stu-id="4dde6-120">Required?</span></span>                            | <span data-ttu-id="4dde6-121">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-121">false</span></span>                                |
| <span data-ttu-id="4dde6-122">Positie?</span><span class="sxs-lookup"><span data-stu-id="4dde6-122">Position?</span></span>                            | <span data-ttu-id="4dde6-123">Met de naam</span><span class="sxs-lookup"><span data-stu-id="4dde6-123">named</span></span>                                |
| <span data-ttu-id="4dde6-124">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="4dde6-124">Default Value</span></span>                        | <span data-ttu-id="4dde6-125">De waarde True</span><span class="sxs-lookup"><span data-stu-id="4dde6-125">true</span></span>                                 |
| <span data-ttu-id="4dde6-126">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4dde6-127">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-127">false</span></span>                                |
| <span data-ttu-id="4dde6-128">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4dde6-129">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="4dde6-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="4dde6-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="4dde6-131">Geeft de naam voor uw webtoepassing.</span><span class="sxs-lookup"><span data-stu-id="4dde6-131">Specifies the name for your web application.</span></span> <span data-ttu-id="4dde6-132">Dit wordt weergegeven als het laatste deel van de Windows PowerShell Web Access-URL.</span><span class="sxs-lookup"><span data-stu-id="4dde6-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="4dde6-133">Aliassen</span><span class="sxs-lookup"><span data-stu-id="4dde6-133">Aliases</span></span>                              | <span data-ttu-id="4dde6-134">geen</span><span class="sxs-lookup"><span data-stu-id="4dde6-134">none</span></span>                                 |
| <span data-ttu-id="4dde6-135">Nodig?</span><span class="sxs-lookup"><span data-stu-id="4dde6-135">Required?</span></span>                            | <span data-ttu-id="4dde6-136">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-136">false</span></span>                                |
| <span data-ttu-id="4dde6-137">Positie?</span><span class="sxs-lookup"><span data-stu-id="4dde6-137">Position?</span></span>                            | <span data-ttu-id="4dde6-138">1</span><span class="sxs-lookup"><span data-stu-id="4dde6-138">1</span></span>                                    |
| <span data-ttu-id="4dde6-139">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="4dde6-139">Default Value</span></span>                        | <span data-ttu-id="4dde6-140">pswa</span><span class="sxs-lookup"><span data-stu-id="4dde6-140">pswa</span></span>                                 |
| <span data-ttu-id="4dde6-141">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4dde6-142">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-142">false</span></span>                                |
| <span data-ttu-id="4dde6-143">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4dde6-144">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="4dde6-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="4dde6-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="4dde6-146">Hiermee geeft u de naam van de webserver (IIS) website waarop u deze webtoepassing Windows PowerShell-webtoegang installeren.</span><span class="sxs-lookup"><span data-stu-id="4dde6-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="4dde6-147">Aliassen</span><span class="sxs-lookup"><span data-stu-id="4dde6-147">Aliases</span></span>                              | <span data-ttu-id="4dde6-148">geen</span><span class="sxs-lookup"><span data-stu-id="4dde6-148">none</span></span>                                 |
| <span data-ttu-id="4dde6-149">Nodig?</span><span class="sxs-lookup"><span data-stu-id="4dde6-149">Required?</span></span>                            | <span data-ttu-id="4dde6-150">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-150">false</span></span>                                |
| <span data-ttu-id="4dde6-151">Positie?</span><span class="sxs-lookup"><span data-stu-id="4dde6-151">Position?</span></span>                            | <span data-ttu-id="4dde6-152">Met de naam</span><span class="sxs-lookup"><span data-stu-id="4dde6-152">named</span></span>                                |
| <span data-ttu-id="4dde6-153">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="4dde6-153">Default Value</span></span>                        | <span data-ttu-id="4dde6-154">Standaardwebsite</span><span class="sxs-lookup"><span data-stu-id="4dde6-154">Default Web Site</span></span>                     |
| <span data-ttu-id="4dde6-155">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4dde6-156">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-156">false</span></span>                                |
| <span data-ttu-id="4dde6-157">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4dde6-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="4dde6-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4dde6-159">-Confirm</span></span>

<span data-ttu-id="4dde6-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4dde6-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="4dde6-161">Nodig?</span><span class="sxs-lookup"><span data-stu-id="4dde6-161">Required?</span></span>                            | <span data-ttu-id="4dde6-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-162">false</span></span>                                |
| <span data-ttu-id="4dde6-163">Positie?</span><span class="sxs-lookup"><span data-stu-id="4dde6-163">Position?</span></span>                            | <span data-ttu-id="4dde6-164">Met de naam</span><span class="sxs-lookup"><span data-stu-id="4dde6-164">named</span></span>                                |
| <span data-ttu-id="4dde6-165">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="4dde6-165">Default Value</span></span>                        | <span data-ttu-id="4dde6-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-166">false</span></span>                                |
| <span data-ttu-id="4dde6-167">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4dde6-168">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-168">false</span></span>                                |
| <span data-ttu-id="4dde6-169">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4dde6-170">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="4dde6-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4dde6-171">-WhatIf</span></span>

<span data-ttu-id="4dde6-172">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4dde6-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4dde6-173">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4dde6-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="4dde6-174">Nodig?</span><span class="sxs-lookup"><span data-stu-id="4dde6-174">Required?</span></span>                            | <span data-ttu-id="4dde6-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-175">false</span></span>                                |
| <span data-ttu-id="4dde6-176">Positie?</span><span class="sxs-lookup"><span data-stu-id="4dde6-176">Position?</span></span>                            | <span data-ttu-id="4dde6-177">Met de naam</span><span class="sxs-lookup"><span data-stu-id="4dde6-177">named</span></span>                                |
| <span data-ttu-id="4dde6-178">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="4dde6-178">Default Value</span></span>                        | <span data-ttu-id="4dde6-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-179">false</span></span>                                |
| <span data-ttu-id="4dde6-180">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4dde6-181">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-181">false</span></span>                                |
| <span data-ttu-id="4dde6-182">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="4dde6-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4dde6-183">onjuist</span><span class="sxs-lookup"><span data-stu-id="4dde6-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4dde6-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="4dde6-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4dde6-185">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4dde6-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4dde6-186">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4dde6-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4dde6-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="4dde6-187">INPUTS</span></span>

<span data-ttu-id="4dde6-188">Deze cmdlet heeft geen invoer.</span><span class="sxs-lookup"><span data-stu-id="4dde6-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4dde6-189">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="4dde6-189">OUTPUTS</span></span>

<span data-ttu-id="4dde6-190">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="4dde6-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="4dde6-191">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4dde6-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4dde6-192">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="4dde6-192">EXAMPLE 1</span></span>

<span data-ttu-id="4dde6-193">In dit voorbeeld installeert de PSWA-webtoepassing met de standaardwaarden voor de **WebApplicationName** (*pswa*) en **Websitenaam** (*standaardwebsite* ) parameters.</span><span class="sxs-lookup"><span data-stu-id="4dde6-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="4dde6-194">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="4dde6-194">EXAMPLE 2</span></span>

<span data-ttu-id="4dde6-195">In dit voorbeeld installeert de webtoepassing PSWA met een testcertificaat en het gebruik van de standaardwaarden voor de **WebApplicationName** en **Websitenaam** parameters.</span><span class="sxs-lookup"><span data-stu-id="4dde6-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="4dde6-196">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="4dde6-196">Related topics</span></span>

- [<span data-ttu-id="4dde6-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4dde6-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4dde6-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4dde6-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="4dde6-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4dde6-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="4dde6-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4dde6-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)