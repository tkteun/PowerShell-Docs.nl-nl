---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Beleid met betrekking tot ondersteuning voor PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854383"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="0d382-103">Levenscyclus voor ondersteuning van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0d382-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="0d382-104">PowerShell Core is een afzonderlijke set hulpprogramma's en onderdelen die is verzonden, geïnstalleerd en geconfigureerd afzonderlijk van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d382-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="0d382-105">PowerShell Core is dus niet opgenomen in de licentieovereenkomsten voor Windows 7/8.1/10 of Windows Server.</span><span class="sxs-lookup"><span data-stu-id="0d382-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="0d382-106">PowerShell Core wordt echter ondersteund onder traditionele Microsoft support-overeenkomsten, met inbegrip van [Premier][], [Microsoft Enterprise-overeenkomsten][enterprise-agreement], en [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="0d382-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="0d382-107">U kunt ook betalen voor [ondersteuning][] voor PowerShell Core via een ondersteuningsaanvraag voor uw probleem.</span><span class="sxs-lookup"><span data-stu-id="0d382-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="0d382-108">Ondersteuning van de community</span><span class="sxs-lookup"><span data-stu-id="0d382-108">Community Support</span></span>

<span data-ttu-id="0d382-109">We bieden ook [Ondersteuning van de community][] op GitHub, waar u een probleem, een fout of een functie-aanvraag kan indienen.</span><span class="sxs-lookup"><span data-stu-id="0d382-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="0d382-110">Bovendien kan u hulp van andere leden van de community vinden op de algemene [Microsoft Community][] of de Microsoft [PowerShell Tech Community][].</span><span class="sxs-lookup"><span data-stu-id="0d382-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="0d382-111">We bieden geen garantie er dat de community wordt adres of het probleem tijdig oplossen.</span><span class="sxs-lookup"><span data-stu-id="0d382-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="0d382-112">Als er een probleem dat onmiddellijke aandacht vereist, moet u de traditionele betaalde ondersteuningsopties.</span><span class="sxs-lookup"><span data-stu-id="0d382-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="0d382-113">Levenscyclus van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0d382-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="0d382-114">PowerShell Core is vast te stellen de [moderne Lifecycle-beleid van Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="0d382-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="0d382-115">De ondersteuningslevenscyclus van deze is bedoeld om klanten up-to-date houden met de meest recente versies.</span><span class="sxs-lookup"><span data-stu-id="0d382-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="0d382-116">De versie 6.x-vertakking van PowerShell Core ongeveer om de zes maanden worden bijgewerkt (voorbeelden: 6.0, 6.1, 6.2, enz.)</span><span class="sxs-lookup"><span data-stu-id="0d382-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d382-117">U moet binnen zes maanden na elke nieuwe secundaire versie vrij om door te gaan met het ontvangen van ondersteuning voor bijwerken.</span><span class="sxs-lookup"><span data-stu-id="0d382-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="0d382-118">Bijvoorbeeld, als PowerShell Core 6.1 wordt gepubliceerd op 1 juli 2018, zou u worden verwacht om bij te werken naar PowerShell Core 6.1 1 januari 2019 voor verdere ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="0d382-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d382-119">U moet binnen 30 dagen na elke nieuwe patchversie vrij om door te gaan met het ontvangen van ondersteuning voor bijwerken.</span><span class="sxs-lookup"><span data-stu-id="0d382-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="0d382-120">Bijvoorbeeld, als u PowerShell Core 6.1 en 6.1.3 is uitgebracht op 19 februari 2019, zou u worden verwacht bij te werken naar PowerShell Core 6.1.3 door 21 maart 2019, die 30 dagen na de release is voor verdere ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="0d382-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="0d382-121">Als er problemen worden gevonden op vereist, worden de oplossingen in de volgende cumulatieve update uitgebracht.</span><span class="sxs-lookup"><span data-stu-id="0d382-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="0d382-122">De moderne Lifecycle-beleid is ook vereist dat Microsoft biedt klanten 12 maanden kennisgeving voordat beëindigde ondersteuning voor een product (dat wil zeggen, PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="0d382-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="0d382-123">We verwachten uiteindelijk PowerShell Core gaat hanteren de 'op de lange termijn onderhoud"benadering.</span><span class="sxs-lookup"><span data-stu-id="0d382-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="0d382-124">In deze benadering onderhoud, zouden we alleen onderhoud en beveiliging updates om te blijven in de ondersteuning op een specifieke vertakking/versie van 6.x vereisen.</span><span class="sxs-lookup"><span data-stu-id="0d382-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="0d382-125">Ondersteunde platformen</span><span class="sxs-lookup"><span data-stu-id="0d382-125">Supported platforms</span></span>

<span data-ttu-id="0d382-126">De volgende tabel om te zien welke platforms de versie van PowerShell Core die u gebruikt is officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0d382-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="0d382-127">Pakketten voor sommige platforms ook bijdrage aan onze community heeft geleverd, maar ze zijn niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0d382-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="0d382-128">Deze pakketten zijn gemarkeerd als `Community` in de tabel.</span><span class="sxs-lookup"><span data-stu-id="0d382-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="0d382-129">Platforms die worden weergegeven als `Experimental` zijn niet officieel ondersteund, maar zijn beschikbaar om te experimenteren en feedback.</span><span class="sxs-lookup"><span data-stu-id="0d382-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="0d382-130">6.1</span><span class="sxs-lookup"><span data-stu-id="0d382-130">6.1</span></span>         | <span data-ttu-id="0d382-131">6.2</span><span class="sxs-lookup"><span data-stu-id="0d382-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="0d382-132">Windows 7, 8.1 en 10</span><span class="sxs-lookup"><span data-stu-id="0d382-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="0d382-133">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-133">Supported</span></span>   | <span data-ttu-id="0d382-134">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-134">Supported</span></span>   |
| <span data-ttu-id="0d382-135">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="0d382-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="0d382-136">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-136">Supported</span></span>   | <span data-ttu-id="0d382-137">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-137">Supported</span></span>   |
| <span data-ttu-id="0d382-138">[Windows Server semi-Annual-kanaal][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="0d382-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="0d382-139">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-139">Supported</span></span>   | <span data-ttu-id="0d382-140">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-140">Supported</span></span>   |
| <span data-ttu-id="0d382-141">Ubuntu 16.04 en 18.04</span><span class="sxs-lookup"><span data-stu-id="0d382-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="0d382-142">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-142">Supported</span></span>   | <span data-ttu-id="0d382-143">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-143">Supported</span></span>   |
| <span data-ttu-id="0d382-144">Ubuntu 18.10 (via Snap-pakket)</span><span class="sxs-lookup"><span data-stu-id="0d382-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="0d382-145">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-145">Community</span></span>   | <span data-ttu-id="0d382-146">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-146">Community</span></span>   |
| <span data-ttu-id="0d382-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0d382-147">Debian 9</span></span>                                          | <span data-ttu-id="0d382-148">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-148">Supported</span></span>   | <span data-ttu-id="0d382-149">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-149">Supported</span></span>   |
| <span data-ttu-id="0d382-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0d382-150">CentOS 7</span></span>                                          | <span data-ttu-id="0d382-151">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-151">Supported</span></span>   | <span data-ttu-id="0d382-152">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-152">Supported</span></span>   |
| <span data-ttu-id="0d382-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="0d382-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="0d382-154">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-154">Supported</span></span>   | <span data-ttu-id="0d382-155">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-155">Supported</span></span>   |
| <span data-ttu-id="0d382-156">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="0d382-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="0d382-157">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-157">Supported</span></span>   | <span data-ttu-id="0d382-158">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-158">Supported</span></span>   |
| <span data-ttu-id="0d382-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0d382-159">Fedora 28</span></span>                                         | <span data-ttu-id="0d382-160">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-160">Supported</span></span>   | <span data-ttu-id="0d382-161">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-161">Supported</span></span>   |
| <span data-ttu-id="0d382-162">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="0d382-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="0d382-163">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-163">Supported</span></span>   | <span data-ttu-id="0d382-164">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="0d382-164">Supported</span></span>   |
| <span data-ttu-id="0d382-165">Arch</span><span class="sxs-lookup"><span data-stu-id="0d382-165">Arch</span></span>                                              | <span data-ttu-id="0d382-166">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-166">Community</span></span>   | <span data-ttu-id="0d382-167">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-167">Community</span></span>   |
| <span data-ttu-id="0d382-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="0d382-168">Raspbian</span></span>                                          | <span data-ttu-id="0d382-169">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-169">Community</span></span>   | <span data-ttu-id="0d382-170">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-170">Community</span></span>   |
| <span data-ttu-id="0d382-171">Kali</span><span class="sxs-lookup"><span data-stu-id="0d382-171">Kali</span></span>                                              | <span data-ttu-id="0d382-172">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-172">Community</span></span>   | <span data-ttu-id="0d382-173">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-173">Community</span></span>   |
| <span data-ttu-id="0d382-174">AppImage (werkt op meerdere platforms voor Linux)</span><span class="sxs-lookup"><span data-stu-id="0d382-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="0d382-175">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-175">Community</span></span>   | <span data-ttu-id="0d382-176">Community</span><span class="sxs-lookup"><span data-stu-id="0d382-176">Community</span></span>   |
| [<span data-ttu-id="0d382-177">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="0d382-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="0d382-178">Zie de opmerking</span><span class="sxs-lookup"><span data-stu-id="0d382-178">See note</span></span>    | <span data-ttu-id="0d382-179">Zie de opmerking</span><span class="sxs-lookup"><span data-stu-id="0d382-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="0d382-180">Module-pakketten ondersteund gelijk zijn aan de distributie wordt uitgevoerd het pakket op.</span><span class="sxs-lookup"><span data-stu-id="0d382-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="0d382-181">Einde van de PowerShell-versie van de levensduur</span><span class="sxs-lookup"><span data-stu-id="0d382-181">PowerShell release end of life</span></span>

<span data-ttu-id="0d382-182">Op basis van [levenscyclus van de PowerShell Core](#lifecycle-of-powershell-core), de volgende tabel bevat de datums waarop verschillende versie wordt niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0d382-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="0d382-183">Versie</span><span class="sxs-lookup"><span data-stu-id="0d382-183">Version</span></span> | <span data-ttu-id="0d382-184">Einde van hun levensduur</span><span class="sxs-lookup"><span data-stu-id="0d382-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="0d382-185">6.0</span><span class="sxs-lookup"><span data-stu-id="0d382-185">6.0</span></span>     | <span data-ttu-id="0d382-186">Op 13 februari 2019</span><span class="sxs-lookup"><span data-stu-id="0d382-186">February 13, 2019</span></span>             |
| <span data-ttu-id="0d382-187">6.1</span><span class="sxs-lookup"><span data-stu-id="0d382-187">6.1</span></span>     | <span data-ttu-id="0d382-188">28 september 2019</span><span class="sxs-lookup"><span data-stu-id="0d382-188">September 28, 2019</span></span>            |
| <span data-ttu-id="0d382-189">6.2</span><span class="sxs-lookup"><span data-stu-id="0d382-189">6.2</span></span>     | <span data-ttu-id="0d382-190">zes maanden na 7 releases</span><span class="sxs-lookup"><span data-stu-id="0d382-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="0d382-191">Platforms die niet ondersteund worden</span><span class="sxs-lookup"><span data-stu-id="0d382-191">Platforms, which are out of support</span></span>

<span data-ttu-id="0d382-192">Wanneer een versie van het platform einde van de levenscyclus bereikt zoals gedefinieerd door de eigenaar van het platform, worden ook PowerShell Core gestaakt voor de ondersteuning van deze versie van het platform.</span><span class="sxs-lookup"><span data-stu-id="0d382-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="0d382-193">Eerder uitgebrachte pakketten blijven beschikbaar voor klanten die toegang tot, maar formele ondersteuning en de updates van welke aard dan ook niet meer worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="0d382-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="0d382-194">Dus de eigenaren van de distributie van ondersteuning voor de volgende versies beëindigd en worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0d382-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="0d382-195">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="0d382-195">OS</span></span>       | <span data-ttu-id="0d382-196">Versie</span><span class="sxs-lookup"><span data-stu-id="0d382-196">Version</span></span> | <span data-ttu-id="0d382-197">Einde van hun levensduur</span><span class="sxs-lookup"><span data-stu-id="0d382-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="0d382-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="0d382-198">Fedora</span></span>   | <span data-ttu-id="0d382-199">24</span><span class="sxs-lookup"><span data-stu-id="0d382-199">24</span></span>      | [<span data-ttu-id="0d382-200">Augustus 2017</span><span class="sxs-lookup"><span data-stu-id="0d382-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="0d382-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="0d382-201">Fedora</span></span>   | <span data-ttu-id="0d382-202">25</span><span class="sxs-lookup"><span data-stu-id="0d382-202">25</span></span>      | [<span data-ttu-id="0d382-203">December 2017</span><span class="sxs-lookup"><span data-stu-id="0d382-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="0d382-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="0d382-204">Fedora</span></span>   | <span data-ttu-id="0d382-205">26</span><span class="sxs-lookup"><span data-stu-id="0d382-205">26</span></span>      | [<span data-ttu-id="0d382-206">Mei 2018</span><span class="sxs-lookup"><span data-stu-id="0d382-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="0d382-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0d382-207">openSUSE</span></span> | <span data-ttu-id="0d382-208">42.1</span><span class="sxs-lookup"><span data-stu-id="0d382-208">42.1</span></span>    | [<span data-ttu-id="0d382-209">Mei 2017</span><span class="sxs-lookup"><span data-stu-id="0d382-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="0d382-210">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0d382-210">openSUSE</span></span> | <span data-ttu-id="0d382-211">42.2</span><span class="sxs-lookup"><span data-stu-id="0d382-211">42.2</span></span>    | [<span data-ttu-id="0d382-212">Januari 2018</span><span class="sxs-lookup"><span data-stu-id="0d382-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="0d382-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0d382-213">Ubuntu</span></span>   | <span data-ttu-id="0d382-214">16.10</span><span class="sxs-lookup"><span data-stu-id="0d382-214">16.10</span></span>   | [<span data-ttu-id="0d382-215">Juli 2017</span><span class="sxs-lookup"><span data-stu-id="0d382-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="0d382-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0d382-216">Ubuntu</span></span>   | <span data-ttu-id="0d382-217">17.04</span><span class="sxs-lookup"><span data-stu-id="0d382-217">17.04</span></span>   | [<span data-ttu-id="0d382-218">Januari 2018</span><span class="sxs-lookup"><span data-stu-id="0d382-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="0d382-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0d382-219">Ubuntu</span></span>   | <span data-ttu-id="0d382-220">17.10</span><span class="sxs-lookup"><span data-stu-id="0d382-220">17.10</span></span>   | [<span data-ttu-id="0d382-221">Juli 2018</span><span class="sxs-lookup"><span data-stu-id="0d382-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="0d382-222">Debian</span><span class="sxs-lookup"><span data-stu-id="0d382-222">Debian</span></span>   | <span data-ttu-id="0d382-223">8</span><span class="sxs-lookup"><span data-stu-id="0d382-223">8</span></span>       | [<span data-ttu-id="0d382-224">Juni 2018</span><span class="sxs-lookup"><span data-stu-id="0d382-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="0d382-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="0d382-225">Fedora</span></span>   | <span data-ttu-id="0d382-226">27</span><span class="sxs-lookup"><span data-stu-id="0d382-226">27</span></span>      | [<span data-ttu-id="0d382-227">November 2018</span><span class="sxs-lookup"><span data-stu-id="0d382-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="0d382-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0d382-228">Ubuntu</span></span>   | <span data-ttu-id="0d382-229">14.04</span><span class="sxs-lookup"><span data-stu-id="0d382-229">14.04</span></span>   | [<span data-ttu-id="0d382-230">April 2019</span><span class="sxs-lookup"><span data-stu-id="0d382-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="0d382-231">Opmerkingen bij de licentieverlening</span><span class="sxs-lookup"><span data-stu-id="0d382-231">Notes on licensing</span></span>

<span data-ttu-id="0d382-232">PowerShell Core is uitgebracht onder de [MIT-licentie][].</span><span class="sxs-lookup"><span data-stu-id="0d382-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="0d382-233">Onder deze licentie, en zonder een betaalde ondersteuningsovereenkomst, gebruikers zijn beperkt tot [Ondersteuning van de community][].</span><span class="sxs-lookup"><span data-stu-id="0d382-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="0d382-234">Met de ondersteuning van de community kan Microsoft niet garanderen van de reactiesnelheid of oplossingen.</span><span class="sxs-lookup"><span data-stu-id="0d382-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="0d382-235">Windows PowerShell Module</span><span class="sxs-lookup"><span data-stu-id="0d382-235">Windows PowerShell Module</span></span>

<span data-ttu-id="0d382-236">Ondersteuning voor PowerShell Core bevat geen van product-modules, tenzij deze modules expliciet ondersteuning voor PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="0d382-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="0d382-237">Bijvoorbeeld, met behulp van de `ActiveDirectory` module die wordt geleverd als onderdeel van Windows Server een niet-ondersteund scenario is.</span><span class="sxs-lookup"><span data-stu-id="0d382-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="0d382-238">Modules die niet expliciet PowerShell Core ondersteunen kunnen zich echter compatibel zijn in sommige gevallen.</span><span class="sxs-lookup"><span data-stu-id="0d382-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="0d382-239">Door het installeren van de [ `WindowsPSModulePath` ][] -module, kunt u de Windows PowerShell toevoegen `PSModulePath` aan uw PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="0d382-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="0d382-240">Installeer eerst de `WindowsPSModulePath` module op basis van de PowerShell Gallery:</span><span class="sxs-lookup"><span data-stu-id="0d382-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="0d382-241">Na de installatie van deze module worden uitgevoerd de `Add-WindowsPSModulePath` cmdlet om toe te voegen van de Windows PowerShell `PSModulePath` PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="0d382-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="0d382-242">Experimentele functies</span><span class="sxs-lookup"><span data-stu-id="0d382-242">Experimental features</span></span>

<span data-ttu-id="0d382-243">[Experimentele functies][] zijn beperkt tot [communityondersteuning](#community-support).</span><span class="sxs-lookup"><span data-stu-id="0d382-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Ondersteuning van de community]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentele functies]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
