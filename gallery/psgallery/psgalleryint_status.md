---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="b77f3-103">Status van de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="b77f3-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="b77f3-104">27-03/2017 - opgelost: kan geen afzonderlijke module en het script pagina's te zien</span><span class="sxs-lookup"><span data-stu-id="b77f3-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="b77f3-105">__Samenvatting van de Impact__: directe koppelingen naar de afzonderlijke pagina's de module en het script op https://www.powershellgallery.com verloren gegaan.</span><span class="sxs-lookup"><span data-stu-id="b77f3-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="b77f3-106">Dit is in alle regio's worden gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="b77f3-106">This was being reported across all the regions.</span></span> <span data-ttu-id="b77f3-107">Dit heeft geen invloed op een van de cmdlets PowerShellGet ie., installatie-Module installatiescript, Update-Module-updatescript Publish-Module Publish-Script nog steeds werken.</span><span class="sxs-lookup"><span data-stu-id="b77f3-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="b77f3-108">__Root Cause__: Engineers de oorzaak geïdentificeerd als een probleem waardoor sociale media knoppen zoals Facebook naar de pagina.</span><span class="sxs-lookup"><span data-stu-id="b77f3-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="b77f3-109">__Resolutie__: Engineers het probleem is opgelost door de Facebook count-informatie uit te schakelen.</span><span class="sxs-lookup"><span data-stu-id="b77f3-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="b77f3-110">__Volgende stappen__: We een interne bijhouden probleem om op te lossen ons gebruik van Facebook-API hebt geopend.</span><span class="sxs-lookup"><span data-stu-id="b77f3-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="b77f3-111">15-12-2016 - kan geen e-mailberichten via de website van de PowerShellGallery verzenden</span><span class="sxs-lookup"><span data-stu-id="b77f3-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="b77f3-112">__Samenvatting van de Impact__: tussen 13-12-2016 en 15-12-2016 geen berichten verzonden via de Contact-eigenaars, eigenaren beheren, contact opnemen met ondersteuning of misbruik van rapport niet zijn ontvangen door de beheerders van PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="b77f3-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="b77f3-113">__Root Cause__: Engineers de oorzaak geïdentificeerd als een verificatieprobleem met de SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="b77f3-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="b77f3-114">__Resolutie__: Engineers konden los het verificatieprobleem en herstel verbinding met de SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="b77f3-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="b77f3-115">__Volgende stappen__: als u de contactpersoon eigenaars, eigenaren beheren, contact opnemen met ondersteuning of misbruik melden koppelingen gebruikt voor het verzenden van e-mail naar cgadmin@microsoft.com gedurende deze tijd en we heeft niet gereageerd, probeer het opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b77f3-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="b77f3-116">Onze excuses voor het ongemak.</span><span class="sxs-lookup"><span data-stu-id="b77f3-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="b77f3-117">8-10/2016 - opgelost: kan geen e-mailberichten verzendencgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="b77f3-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="b77f3-118">__Samenvatting van de Impact__: tussen 5-8-2016 en 8/10/2016 klanten kon niet worden verzonden e-mailberichten cgadmin@microsoft.com, of gebruik de functie Contact met ons opnemen.</span><span class="sxs-lookup"><span data-stu-id="b77f3-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="b77f3-119">__Root Cause__: Engineers de oorzaak geïdentificeerd als een wijziging in de configuratie van het e-mailaccount.</span><span class="sxs-lookup"><span data-stu-id="b77f3-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="b77f3-120">__Resolutie__: Engineers gewerkt om de configuratieprobleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="b77f3-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="b77f3-121">__Volgende stappen__: als u de koppeling Contact met ons gebruikt of e-mail naar verzonden cgadmin@microsoft.com gedurende deze tijd en we heeft niet gereageerd, probeer het opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b77f3-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="b77f3-122">Hartelijk dank voor uw geduld.</span><span class="sxs-lookup"><span data-stu-id="b77f3-122">Thank you for your patience.</span></span>


