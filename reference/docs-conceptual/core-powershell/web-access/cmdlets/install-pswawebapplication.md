---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268296"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="f6522-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f6522-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6522-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f6522-104">SYNOPSIS</span></span>

<span data-ttu-id="f6522-105">Hiermee configureert u de web-App voor Windows PowerShell-webtoegang in IIS.</span><span class="sxs-lookup"><span data-stu-id="f6522-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6522-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f6522-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="f6522-107">Standaardinstelling</span><span class="sxs-lookup"><span data-stu-id="f6522-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="f6522-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f6522-108">DESCRIPTION</span></span>

<span data-ttu-id="f6522-109">De **Install-PswaWebApplication** cmdlet web-App voor Windows PowerShell-internettoegang configureert.</span><span class="sxs-lookup"><span data-stu-id="f6522-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="f6522-110">Deze cmdlet installeert de webtoepassing, koppelt het aan een website en (optioneel) maakt een test SSL certificaat met de **useTestCertificate** parameter.</span><span class="sxs-lookup"><span data-stu-id="f6522-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="f6522-111">Voor beveiliging moeten redenen webbeheerders een testcertificaat niet gebruiken voor productieomgevingen.</span><span class="sxs-lookup"><span data-stu-id="f6522-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="f6522-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6522-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="f6522-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="f6522-113">-UseTestCertificate</span></span>

<span data-ttu-id="f6522-114">Hiermee geeft u op dat een testcertificaat is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f6522-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="f6522-115">Als deze parameter is ingesteld op true, en vervolgens deze cmdlet een testcertificaat maakt en configureert u de web-App voor Windows PowerShell-webtoegang, met het certificaat voor HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="f6522-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="f6522-116">Als deze parameter is ingesteld op false, wordt er geen certificaat of een binding gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f6522-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="f6522-117">Deze waarde ingesteld op ONWAAR als een ander certificaat wordt gebruikt voor Windows PowerShell-webtoegang.</span><span class="sxs-lookup"><span data-stu-id="f6522-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="f6522-118">Aliassen</span><span class="sxs-lookup"><span data-stu-id="f6522-118">Aliases</span></span>                              | <span data-ttu-id="f6522-119">geen</span><span class="sxs-lookup"><span data-stu-id="f6522-119">none</span></span>                                 |
| <span data-ttu-id="f6522-120">Nodig?</span><span class="sxs-lookup"><span data-stu-id="f6522-120">Required?</span></span>                            | <span data-ttu-id="f6522-121">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-121">false</span></span>                                |
| <span data-ttu-id="f6522-122">Positie?</span><span class="sxs-lookup"><span data-stu-id="f6522-122">Position?</span></span>                            | <span data-ttu-id="f6522-123">met de naam</span><span class="sxs-lookup"><span data-stu-id="f6522-123">named</span></span>                                |
| <span data-ttu-id="f6522-124">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="f6522-124">Default Value</span></span>                        | <span data-ttu-id="f6522-125">True</span><span class="sxs-lookup"><span data-stu-id="f6522-125">true</span></span>                                 |
| <span data-ttu-id="f6522-126">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f6522-127">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-127">false</span></span>                                |
| <span data-ttu-id="f6522-128">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f6522-129">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="f6522-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="f6522-130">-WebApplicationName</span></span>

<span data-ttu-id="f6522-131">Hiermee geeft u de naam voor uw webtoepassing.</span><span class="sxs-lookup"><span data-stu-id="f6522-131">Specifies the name for your web application.</span></span> <span data-ttu-id="f6522-132">Dit wordt weergegeven als het laatste deel van de URL van de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="f6522-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="f6522-133">Aliassen</span><span class="sxs-lookup"><span data-stu-id="f6522-133">Aliases</span></span>                              | <span data-ttu-id="f6522-134">geen</span><span class="sxs-lookup"><span data-stu-id="f6522-134">none</span></span>                                 |
| <span data-ttu-id="f6522-135">Nodig?</span><span class="sxs-lookup"><span data-stu-id="f6522-135">Required?</span></span>                            | <span data-ttu-id="f6522-136">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-136">false</span></span>                                |
| <span data-ttu-id="f6522-137">Positie?</span><span class="sxs-lookup"><span data-stu-id="f6522-137">Position?</span></span>                            | <span data-ttu-id="f6522-138">1</span><span class="sxs-lookup"><span data-stu-id="f6522-138">1</span></span>                                    |
| <span data-ttu-id="f6522-139">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="f6522-139">Default Value</span></span>                        | <span data-ttu-id="f6522-140">pswa</span><span class="sxs-lookup"><span data-stu-id="f6522-140">pswa</span></span>                                 |
| <span data-ttu-id="f6522-141">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f6522-142">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-142">false</span></span>                                |
| <span data-ttu-id="f6522-143">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f6522-144">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="f6522-145">-Websitenaam</span><span class="sxs-lookup"><span data-stu-id="f6522-145">-WebSiteName</span></span>

<span data-ttu-id="f6522-146">Hiermee geeft u de naam van de webserver (IIS) website waarvoor u wilt deze web-App voor Windows PowerShell-webtoegang installeren.</span><span class="sxs-lookup"><span data-stu-id="f6522-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="f6522-147">Aliassen</span><span class="sxs-lookup"><span data-stu-id="f6522-147">Aliases</span></span>                              | <span data-ttu-id="f6522-148">geen</span><span class="sxs-lookup"><span data-stu-id="f6522-148">none</span></span>                                 |
| <span data-ttu-id="f6522-149">Nodig?</span><span class="sxs-lookup"><span data-stu-id="f6522-149">Required?</span></span>                            | <span data-ttu-id="f6522-150">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-150">false</span></span>                                |
| <span data-ttu-id="f6522-151">Positie?</span><span class="sxs-lookup"><span data-stu-id="f6522-151">Position?</span></span>                            | <span data-ttu-id="f6522-152">met de naam</span><span class="sxs-lookup"><span data-stu-id="f6522-152">named</span></span>                                |
| <span data-ttu-id="f6522-153">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="f6522-153">Default Value</span></span>                        | <span data-ttu-id="f6522-154">Standaardwebsite</span><span class="sxs-lookup"><span data-stu-id="f6522-154">Default Web Site</span></span>                     |
| <span data-ttu-id="f6522-155">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f6522-156">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-156">false</span></span>                                |
| <span data-ttu-id="f6522-157">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f6522-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="f6522-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f6522-159">-Confirm</span></span>

<span data-ttu-id="f6522-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f6522-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="f6522-161">Nodig?</span><span class="sxs-lookup"><span data-stu-id="f6522-161">Required?</span></span>                            | <span data-ttu-id="f6522-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-162">false</span></span>                                |
| <span data-ttu-id="f6522-163">Positie?</span><span class="sxs-lookup"><span data-stu-id="f6522-163">Position?</span></span>                            | <span data-ttu-id="f6522-164">met de naam</span><span class="sxs-lookup"><span data-stu-id="f6522-164">named</span></span>                                |
| <span data-ttu-id="f6522-165">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="f6522-165">Default Value</span></span>                        | <span data-ttu-id="f6522-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-166">false</span></span>                                |
| <span data-ttu-id="f6522-167">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f6522-168">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-168">false</span></span>                                |
| <span data-ttu-id="f6522-169">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f6522-170">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="f6522-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f6522-171">-WhatIf</span></span>

<span data-ttu-id="f6522-172">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f6522-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f6522-173">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f6522-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="f6522-174">Nodig?</span><span class="sxs-lookup"><span data-stu-id="f6522-174">Required?</span></span>                            | <span data-ttu-id="f6522-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-175">false</span></span>                                |
| <span data-ttu-id="f6522-176">Positie?</span><span class="sxs-lookup"><span data-stu-id="f6522-176">Position?</span></span>                            | <span data-ttu-id="f6522-177">met de naam</span><span class="sxs-lookup"><span data-stu-id="f6522-177">named</span></span>                                |
| <span data-ttu-id="f6522-178">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="f6522-178">Default Value</span></span>                        | <span data-ttu-id="f6522-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-179">false</span></span>                                |
| <span data-ttu-id="f6522-180">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f6522-181">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-181">false</span></span>                                |
| <span data-ttu-id="f6522-182">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="f6522-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f6522-183">onjuist</span><span class="sxs-lookup"><span data-stu-id="f6522-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="f6522-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="f6522-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="f6522-185">Deze cmdlet worden de gangbare parameters ondersteund:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="f6522-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="f6522-186">Zie voor meer informatie, [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f6522-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="f6522-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="f6522-187">INPUTS</span></span>

<span data-ttu-id="f6522-188">Deze cmdlet gebruikt geen invoer.</span><span class="sxs-lookup"><span data-stu-id="f6522-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="f6522-189">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f6522-189">OUTPUTS</span></span>

<span data-ttu-id="f6522-190">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f6522-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="f6522-191">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f6522-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="f6522-192">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="f6522-192">EXAMPLE 1</span></span>

<span data-ttu-id="f6522-193">In dit voorbeeld installeert de PSWA-webtoepassing met de standaardwaarden voor de **WebApplicationName** (*pswa*) en **Websitenaam** (*standaardwebsite* ) parameters.</span><span class="sxs-lookup"><span data-stu-id="f6522-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="f6522-194">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="f6522-194">EXAMPLE 2</span></span>

<span data-ttu-id="f6522-195">In dit voorbeeld installeert de webtoepassing PSWA met een testcertificaat en met behulp van de standaardwaarden voor de **WebApplicationName** en **Websitenaam** parameters.</span><span class="sxs-lookup"><span data-stu-id="f6522-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="f6522-196">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="f6522-196">Related topics</span></span>

- [<span data-ttu-id="f6522-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f6522-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="f6522-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f6522-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="f6522-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f6522-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="f6522-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f6522-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)