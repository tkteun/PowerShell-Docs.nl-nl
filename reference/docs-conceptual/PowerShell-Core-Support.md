# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="271c0-101">Levenscyclus voor ondersteuning van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="271c0-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="271c0-102">PowerShell Core is een unieke set van hulpprogramma's en onderdelen die is verzonden, geïnstalleerd en geconfigureerd afzonderlijk vanuit Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="271c0-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="271c0-103">PowerShell Core is daarom niet opgenomen in de licentieovereenkomsten voor Windows 7/8.1/10 of Windows Server.</span><span class="sxs-lookup"><span data-stu-id="271c0-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="271c0-104">PowerShell Core wordt echter ondersteund onder traditionele Microsoft support-overeenkomsten, met inbegrip van [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], en [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="271c0-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="271c0-105">U kunt ook betalen voor [ondersteuning][] voor PowerShell Core door het indienen van een aanvraag voor de ondersteuning voor uw probleem.</span><span class="sxs-lookup"><span data-stu-id="271c0-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="271c0-106">We bieden ook [communityondersteuning][] op GitHub waarin u een probleem, een fout of een aanvraag van de functie kan opslaan.</span><span class="sxs-lookup"><span data-stu-id="271c0-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="271c0-107">U kunt ook u Help-informatie van andere leden van de community mogelijk vinden op de algemene [Microsoft-Community][] of Microsoft [PowerShell technische Community][].</span><span class="sxs-lookup"><span data-stu-id="271c0-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="271c0-108">We bieden geen garantie er dat het probleem worden aangepakt of tijdig opgelost.</span><span class="sxs-lookup"><span data-stu-id="271c0-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="271c0-109">Als er een probleem dat onmiddellijke aandacht vereist, moet u de traditionele betaald ondersteuningsopties.</span><span class="sxs-lookup"><span data-stu-id="271c0-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="271c0-110">Levenscyclus van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="271c0-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="271c0-111">Het gebruik nemen van PowerShell Core de [moderne Lifecycle-beleid van Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="271c0-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="271c0-112">Deze ondersteuningslevenscyclus is bedoeld om klanten up-to-date houden met de meest recente versies.</span><span class="sxs-lookup"><span data-stu-id="271c0-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="271c0-113">De versie 6.x-vertakking van PowerShell Core ongeveer om de zes maanden worden bijgewerkt (zoals 6.0, 6.1, 6.2, enz.)</span><span class="sxs-lookup"><span data-stu-id="271c0-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="271c0-114">U moet bijwerken in zes maanden na de release van elke nieuwe secundaire versie om te blijven ontvangen van ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="271c0-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="271c0-115">Bijvoorbeeld, als PowerShell Core 6.1 is uitgebracht op 1e juli 2018, zou worden uitgegaan dat u voor het bijwerken naar PowerShell Core 6.1 door 1e januari 2019 voor verdere ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="271c0-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Levenscyclus van de vertakking PowerShell Core][lifecycle-chart]

<span data-ttu-id="271c0-117">Het moderne Lifecycle-beleid vereist ook dat Microsoft geeft klanten 12 maanden kennisgeving voordat beëindigde ondersteuning voor een product (dat wil zeggen PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="271c0-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="271c0-118">Uiteindelijk we verwachten PowerShell Core invoert 'op lange termijn onderhoud' benadering waar we alleen onderhoud en beveiliging vereist updates moeten worden ondersteund op een specifieke vertakking of de versie van 6.x blijven.</span><span class="sxs-lookup"><span data-stu-id="271c0-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="271c0-119">Ondersteunde platformen</span><span class="sxs-lookup"><span data-stu-id="271c0-119">Supported platforms</span></span>

<span data-ttu-id="271c0-120">PowerShell Core wordt officieel ondersteund op de volgende platforms:</span><span class="sxs-lookup"><span data-stu-id="271c0-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="271c0-121">Windows 7, 8.1 en 10</span><span class="sxs-lookup"><span data-stu-id="271c0-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="271c0-122">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="271c0-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="271c0-123">[Windows-serverkanaal puntkomma per jaar][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="271c0-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="271c0-124">Ubuntu 14.04 16.04 en 17.04</span><span class="sxs-lookup"><span data-stu-id="271c0-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="271c0-125">Debian 8,7 + en 9</span><span class="sxs-lookup"><span data-stu-id="271c0-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="271c0-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="271c0-126">CentOS 7</span></span>
* <span data-ttu-id="271c0-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="271c0-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="271c0-128">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="271c0-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="271c0-129">Fedora 25, 26</span><span class="sxs-lookup"><span data-stu-id="271c0-129">Fedora 25, 26</span></span>
* <span data-ttu-id="271c0-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="271c0-130">macOS 10.12+</span></span>

<span data-ttu-id="271c0-131">Onze community heeft ook bijgedragen pakketten voor de volgende platforms, maar ze zijn niet officieel suppported:</span><span class="sxs-lookup"><span data-stu-id="271c0-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="271c0-132">Boog Linux</span><span class="sxs-lookup"><span data-stu-id="271c0-132">Arch Linux</span></span>
* <span data-ttu-id="271c0-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="271c0-133">Kali Linux</span></span>
* <span data-ttu-id="271c0-134">AppImage (werkt op meerdere platforms voor Linux)</span><span class="sxs-lookup"><span data-stu-id="271c0-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="271c0-135">Opmerkingen over licentieverlening</span><span class="sxs-lookup"><span data-stu-id="271c0-135">Notes on licensing</span></span>

<span data-ttu-id="271c0-136">PowerShell Core wordt uitgebracht onder de [MIT-licentie][].</span><span class="sxs-lookup"><span data-stu-id="271c0-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="271c0-137">Onder deze licentie, en in het ontbreken van een ondersteuningsovereenkomst betaalde, gebruikers zijn beperkt tot [communityondersteuning][].</span><span class="sxs-lookup"><span data-stu-id="271c0-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="271c0-138">Microsoft kan niet garanderen van reactiesnelheid of oplossingen met communityondersteuning.</span><span class="sxs-lookup"><span data-stu-id="271c0-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="271c0-139">Windows PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="271c0-139">Windows PowerShell Module</span></span>

<span data-ttu-id="271c0-140">Ondersteuning voor PowerShell Core niet van toepassing op andere modules product tenzij expliciet ondersteuning voor die modules PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="271c0-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="271c0-141">Bijvoorbeeld, met behulp van de `ActiveDirectory` module die wordt geleverd als onderdeel van Windows Server een niet-ondersteund scenario is.</span><span class="sxs-lookup"><span data-stu-id="271c0-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="271c0-142">Modules die niet expliciet PowerShell Core ondersteunen mogelijk echter compatibel in sommige gevallen.</span><span class="sxs-lookup"><span data-stu-id="271c0-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="271c0-143">Door het installeren van de [`WindowsPSModulePath`][] -module, kunt u de Windows PowerShell toevoegen `PSModulePath` naar uw PowerShell-kern `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="271c0-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="271c0-144">Installeer eerst de `WindowsPSModulePath` module op basis van de PowerShell-galerie:</span><span class="sxs-lookup"><span data-stu-id="271c0-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="271c0-145">Voer na het installeren van deze module de `Add-WindowsPSModulePath` cmdlet om toe te voegen van de Windows PowerShell `PSModulePath` naar PowerShell-kern:</span><span class="sxs-lookup"><span data-stu-id="271c0-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[communityondersteuning]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft-Community]: https://answers.microsoft.com/
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell technische Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/