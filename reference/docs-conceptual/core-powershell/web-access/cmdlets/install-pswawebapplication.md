---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: pswawebapplication installeren
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="bb8c0-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="bb8c0-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="bb8c0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bb8c0-104">SYNOPSIS</span></span>

<span data-ttu-id="bb8c0-105">Hiermee configureert u de Windows PowerShell® Web Access-webtoepassing in IIS.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb8c0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bb8c0-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="bb8c0-107">Standaardinstelling</span><span class="sxs-lookup"><span data-stu-id="bb8c0-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="bb8c0-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bb8c0-108">DESCRIPTION</span></span>

<span data-ttu-id="bb8c0-109">De **Install-PswaWebApplication** cmdlet Windows PowerShell-webtoegang webtoepassing configureert.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="bb8c0-110">Deze cmdlet installeert de webtoepassing, koppelt u deze aan een website en eventueel maakt een test SSL certificaat met de **useTestCertificate** parameter.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="bb8c0-111">Voor beveiliging moeten webbeheerders redenen een testcertificaat niet gebruiken voor productieomgevingen.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="bb8c0-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb8c0-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="bb8c0-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="bb8c0-113">-UseTestCertificate</span></span>

<span data-ttu-id="bb8c0-114">Geeft aan dat een testcertificaat is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="bb8c0-115">Als deze parameter is ingesteld op true, wordt deze cmdlet een testcertificaat maakt en configureert u de Windows PowerShell Web Access-webtoepassing met het certificaat voor HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="bb8c0-116">Als deze parameter is ingesteld op false, wordt er geen certificaat of een binding gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="bb8c0-117">Deze waarde ingesteld op false als een ander certificaat wordt gebruikt voor Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="bb8c0-118">Aliassen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-118">Aliases</span></span>                              | <span data-ttu-id="bb8c0-119">geen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-119">none</span></span>                                 |
| <span data-ttu-id="bb8c0-120">Nodig?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-120">Required?</span></span>                            | <span data-ttu-id="bb8c0-121">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-121">false</span></span>                                |
| <span data-ttu-id="bb8c0-122">Positie?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-122">Position?</span></span>                            | <span data-ttu-id="bb8c0-123">Met de naam</span><span class="sxs-lookup"><span data-stu-id="bb8c0-123">named</span></span>                                |
| <span data-ttu-id="bb8c0-124">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="bb8c0-124">Default Value</span></span>                        | <span data-ttu-id="bb8c0-125">De waarde True</span><span class="sxs-lookup"><span data-stu-id="bb8c0-125">true</span></span>                                 |
| <span data-ttu-id="bb8c0-126">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bb8c0-127">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-127">false</span></span>                                |
| <span data-ttu-id="bb8c0-128">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bb8c0-129">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="bb8c0-130">-WebApplicationName&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="bb8c0-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="bb8c0-131">Geeft de naam voor uw webtoepassing.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-131">Specifies the name for your web application.</span></span> <span data-ttu-id="bb8c0-132">Dit wordt weergegeven als het laatste deel van de Windows PowerShell Web Access-URL.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="bb8c0-133">Aliassen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-133">Aliases</span></span>                              | <span data-ttu-id="bb8c0-134">geen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-134">none</span></span>                                 |
| <span data-ttu-id="bb8c0-135">Nodig?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-135">Required?</span></span>                            | <span data-ttu-id="bb8c0-136">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-136">false</span></span>                                |
| <span data-ttu-id="bb8c0-137">Positie?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-137">Position?</span></span>                            | <span data-ttu-id="bb8c0-138">1</span><span class="sxs-lookup"><span data-stu-id="bb8c0-138">1</span></span>                                    |
| <span data-ttu-id="bb8c0-139">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="bb8c0-139">Default Value</span></span>                        | <span data-ttu-id="bb8c0-140">pswa</span><span class="sxs-lookup"><span data-stu-id="bb8c0-140">pswa</span></span>                                 |
| <span data-ttu-id="bb8c0-141">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bb8c0-142">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-142">false</span></span>                                |
| <span data-ttu-id="bb8c0-143">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bb8c0-144">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="bb8c0-145">-Websitenaam&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="bb8c0-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="bb8c0-146">Hiermee geeft u de naam van de webserver (IIS) website waarop u deze webtoepassing Windows PowerShell-webtoegang installeren.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="bb8c0-147">Aliassen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-147">Aliases</span></span>                              | <span data-ttu-id="bb8c0-148">geen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-148">none</span></span>                                 |
| <span data-ttu-id="bb8c0-149">Nodig?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-149">Required?</span></span>                            | <span data-ttu-id="bb8c0-150">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-150">false</span></span>                                |
| <span data-ttu-id="bb8c0-151">Positie?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-151">Position?</span></span>                            | <span data-ttu-id="bb8c0-152">Met de naam</span><span class="sxs-lookup"><span data-stu-id="bb8c0-152">named</span></span>                                |
| <span data-ttu-id="bb8c0-153">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="bb8c0-153">Default Value</span></span>                        | <span data-ttu-id="bb8c0-154">Standaardwebsite</span><span class="sxs-lookup"><span data-stu-id="bb8c0-154">Default Web Site</span></span>                     |
| <span data-ttu-id="bb8c0-155">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bb8c0-156">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-156">false</span></span>                                |
| <span data-ttu-id="bb8c0-157">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bb8c0-158">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="bb8c0-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb8c0-159">-Confirm</span></span>

<span data-ttu-id="bb8c0-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="bb8c0-161">Nodig?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-161">Required?</span></span>                            | <span data-ttu-id="bb8c0-162">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-162">false</span></span>                                |
| <span data-ttu-id="bb8c0-163">Positie?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-163">Position?</span></span>                            | <span data-ttu-id="bb8c0-164">Met de naam</span><span class="sxs-lookup"><span data-stu-id="bb8c0-164">named</span></span>                                |
| <span data-ttu-id="bb8c0-165">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="bb8c0-165">Default Value</span></span>                        | <span data-ttu-id="bb8c0-166">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-166">false</span></span>                                |
| <span data-ttu-id="bb8c0-167">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bb8c0-168">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-168">false</span></span>                                |
| <span data-ttu-id="bb8c0-169">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bb8c0-170">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="bb8c0-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb8c0-171">-WhatIf</span></span>

<span data-ttu-id="bb8c0-172">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bb8c0-173">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="bb8c0-174">Nodig?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-174">Required?</span></span>                            | <span data-ttu-id="bb8c0-175">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-175">false</span></span>                                |
| <span data-ttu-id="bb8c0-176">Positie?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-176">Position?</span></span>                            | <span data-ttu-id="bb8c0-177">Met de naam</span><span class="sxs-lookup"><span data-stu-id="bb8c0-177">named</span></span>                                |
| <span data-ttu-id="bb8c0-178">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="bb8c0-178">Default Value</span></span>                        | <span data-ttu-id="bb8c0-179">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-179">false</span></span>                                |
| <span data-ttu-id="bb8c0-180">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bb8c0-181">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-181">false</span></span>                                |
| <span data-ttu-id="bb8c0-182">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="bb8c0-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bb8c0-183">onjuist</span><span class="sxs-lookup"><span data-stu-id="bb8c0-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="bb8c0-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="bb8c0-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="bb8c0-185">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="bb8c0-186">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bb8c0-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="bb8c0-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="bb8c0-187">INPUTS</span></span>

<span data-ttu-id="bb8c0-188">Deze cmdlet heeft geen invoer.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="bb8c0-189">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bb8c0-189">OUTPUTS</span></span>

<span data-ttu-id="bb8c0-190">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="bb8c0-191">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bb8c0-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="bb8c0-192">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="bb8c0-192">EXAMPLE 1</span></span>

<span data-ttu-id="bb8c0-193">In dit voorbeeld installeert de PSWA-webtoepassing met de standaardwaarden voor de **WebApplicationName** (*pswa*) en **Websitenaam** (*standaardwebsite* ) parameters.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="bb8c0-194">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="bb8c0-194">EXAMPLE 2</span></span>

<span data-ttu-id="bb8c0-195">In dit voorbeeld installeert de webtoepassing PSWA met een testcertificaat en het gebruik van de standaardwaarden voor de **WebApplicationName** en **Websitenaam** parameters.</span><span class="sxs-lookup"><span data-stu-id="bb8c0-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="bb8c0-196">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="bb8c0-196">Related topics</span></span>

- [<span data-ttu-id="bb8c0-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bb8c0-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="bb8c0-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bb8c0-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="bb8c0-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bb8c0-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="bb8c0-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bb8c0-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
