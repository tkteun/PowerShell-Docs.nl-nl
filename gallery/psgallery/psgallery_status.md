---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="8523b-103">Status van de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="8523b-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="8523b-104">10-10-2017 - PowerShell Gallery niet beschikbaar voor 2 uur 10/10/17</span><span class="sxs-lookup"><span data-stu-id="8523b-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="8523b-105">__Samenvatting van de Impact__: de PowerShell Gallery ervaren een periode van zeer hoge latentie, wat resulteert in onregelmatige verbindingsproblemen vanaf ongeveer 17: 00 uur (PDT) 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="8523b-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="8523b-106">Tijdens het omzetten van het probleem, is de site offline gehaald gedurende 2 uur ongeveer 10 uur (PDT) wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="8523b-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="8523b-107">De site is hersteld binnen enkele ogenblikken vóór middernacht 10/10/2017.</span><span class="sxs-lookup"><span data-stu-id="8523b-107">The site was restored shortly before midnight 10/10/2017.</span></span>

<span data-ttu-id="8523b-108">__Root Cause__: de hoofdoorzaak van hoge latentie nog steeds wordt onderzocht.</span><span class="sxs-lookup"><span data-stu-id="8523b-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="8523b-109">__Resolutie__: de webservices moest offline worden gehaald en hersteld om de primaire probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="8523b-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span>

<span data-ttu-id="8523b-110">__Volgende stappen__: de hoofdoorzaak van het oorspronkelijke probleem wordt onderzocht.</span><span class="sxs-lookup"><span data-stu-id="8523b-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="8523b-111">01-06/2017 - implementeren in Azure Automation momenteel niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="8523b-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="8523b-112">__Samenvatting van de Impact__: items met afhankelijkheden implementeren op Azure Automation van de PowerShell Gallery is momenteel niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="8523b-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="8523b-113">Importeren van items van de PowerShell Gallery uit in Azure Automation is nog steeds beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="8523b-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>

<span data-ttu-id="8523b-114">__Hoofdoorzaak__: Items die zijn afhankelijk van andere en eerder zijn geïmplementeerd op Azure Automation wordt niet geïmplementeerd voor een Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="8523b-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="8523b-115">Engineers hebt vastgesteld dat een probleem met hoe ARM-sjablonen worden gegenereerd voor items met afhankelijkheden voor het implementeren in Azure Automation-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="8523b-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="8523b-116">__Resolutie__: Engineers werkt als probleem wilt oplossen.</span><span class="sxs-lookup"><span data-stu-id="8523b-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="8523b-117">De huidige oplossing voor gebruikers is het item van de PowerShell Gallery van importeren in Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="8523b-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span>

<span data-ttu-id="8523b-118">__Volgende stappen__: Engineers kort de oplossing worden vrijgegeven.</span><span class="sxs-lookup"><span data-stu-id="8523b-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="8523b-119">In de tussentijd gebruik de aanbevolen oplossing.</span><span class="sxs-lookup"><span data-stu-id="8523b-119">In the meantime, please use the recommended workaround.</span></span>


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="8523b-120">11-04-2017 - gebruikers kan niet aanmelden met Azure Active Directory (AAD) accounts</span><span class="sxs-lookup"><span data-stu-id="8523b-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="8523b-121">__Samenvatting van de Impact__: sommige gebruikers kunnen zich aanmelden bij de PowerShell-galerie met behulp van Azure AD-Accounts.</span><span class="sxs-lookup"><span data-stu-id="8523b-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span>

<span data-ttu-id="8523b-122">__Hoofdoorzaak__: tijdens een update veiliger communiceren met AAD een wijziging in de instelling is overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8523b-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span>
<span data-ttu-id="8523b-123">De tests uitgevoerd voor het valideren van de wijziging bevat geen bepaalde soorten AAD-accounts, zodat de implementatie plaatsvindt.</span><span class="sxs-lookup"><span data-stu-id="8523b-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="8523b-124">__Resolutie__: Engineers de ontbrekende instelling vastgesteld en gecorrigeerd van het probleem.</span><span class="sxs-lookup"><span data-stu-id="8523b-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span>

<span data-ttu-id="8523b-125">__Volgende stappen__: We zullen worden wijzigen onze tests zodanig dat die een uitgebreidere set van AAD-accounttypen.</span><span class="sxs-lookup"><span data-stu-id="8523b-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="8523b-126">27-03/2017 - opgelost: kan geen afzonderlijke module en het script pagina's te zien</span><span class="sxs-lookup"><span data-stu-id="8523b-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="8523b-127">__Samenvatting van de Impact__: directe koppelingen naar de afzonderlijke pagina's module en het script op https://www.powershellgallery.com verloren gegaan.</span><span class="sxs-lookup"><span data-stu-id="8523b-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="8523b-128">Dit is in alle regio's worden gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="8523b-128">This was being reported across all the regions.</span></span> <span data-ttu-id="8523b-129">Dit heeft geen invloed op een van de cmdlets PowerShellGet ie., installatie-Module installatiescript, Update-Module-updatescript Publish-Module Publish-Scirpt nog steeds werken.</span><span class="sxs-lookup"><span data-stu-id="8523b-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="8523b-130">__Root Cause__: Engineers de oorzaak geïdentificeerd als een probleem waardoor sociale media knoppen zoals Facebook naar de pagina.</span><span class="sxs-lookup"><span data-stu-id="8523b-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="8523b-131">__Resolutie__: Engineers het probleem is opgelost door de Facebook count-informatie uit te schakelen.</span><span class="sxs-lookup"><span data-stu-id="8523b-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="8523b-132">__Volgende stappen__: We een interne bijhouden probleem om op te lossen ons gebruik van Facebook-API hebt geopend.</span><span class="sxs-lookup"><span data-stu-id="8523b-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="8523b-133">15-12-2016 - kan geen e-mailberichten via de website van de PowerShellGallery verzenden</span><span class="sxs-lookup"><span data-stu-id="8523b-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="8523b-134">__Samenvatting van de Impact__: tussen 13-12-2016 en 15-12-2016 geen berichten verzonden via de Contact-eigenaars, eigenaren beheren, contact opnemen met ondersteuning of misbruik van rapport niet zijn ontvangen door de beheerders van PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="8523b-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="8523b-135">__Root Cause__: Engineers de oorzaak geïdentificeerd als een verificatieprobleem met de SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="8523b-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="8523b-136">__Resolutie__: Engineers konden los het verificatieprobleem en herstel verbinding met de SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="8523b-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="8523b-137">__Volgende stappen__: als u de contactpersoon eigenaars, eigenaren beheren, contact opnemen met ondersteuning of misbruik melden koppelingen gebruikt voor het verzenden van e-mail naar cgadmin@microsoft.com gedurende deze tijd en we heeft niet gereageerd, probeer het opnieuw.</span><span class="sxs-lookup"><span data-stu-id="8523b-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="8523b-138">Onze excuses voor het ongemak.</span><span class="sxs-lookup"><span data-stu-id="8523b-138">We apologize for the inconvenience.</span></span>



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="8523b-139">8-10/2016 - opgelost: kan geen e-mailberichten verzenden cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="8523b-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="8523b-140">__Samenvatting van de Impact__: tussen 5-8-2016 en 8/10/2016 klanten kon niet worden verzonden e-mailberichten cgadmin@microsoft.com, of gebruik de functie Contact met ons opnemen.</span><span class="sxs-lookup"><span data-stu-id="8523b-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="8523b-141">__Root Cause__: Engineers de oorzaak geïdentificeerd als een wijziging in de configuratie van het e-mailaccount.</span><span class="sxs-lookup"><span data-stu-id="8523b-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="8523b-142">__Resolutie__: Engineers gewerkt om de configuratieprobleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="8523b-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="8523b-143">__Volgende stappen__: als u de koppeling Contact met ons gebruikt of e-mail naar verzonden cgadmin@microsoft.com gedurende deze tijd en we heeft niet gereageerd, probeer het opnieuw.</span><span class="sxs-lookup"><span data-stu-id="8523b-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="8523b-144">Hartelijk dank voor uw geduld.</span><span class="sxs-lookup"><span data-stu-id="8523b-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="8523b-145">13-7/2016 - Items kan niet downloaden</span><span class="sxs-lookup"><span data-stu-id="8523b-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="8523b-146">__Samenvatting van de Impact__: tussen 11-7-2016 en 13-7-2016, is een subset van klanten problemen met het downloaden van items uit de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="8523b-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="8523b-147">Het probleem waarschijnlijk overgenomen zelf in het volgende foutbericht weergegeven dat is geretourneerd door de installatie-Module/Script voor installatie en opslaan-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="8523b-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="8523b-148">__Voorlopige hoofdoorzaak__: Engineers een probleem vastgesteld met Azure inhoud leveren Network (CDN), die is geïmplementeerd naar de galerie met PowerShell op 11-7-2016.</span><span class="sxs-lookup"><span data-stu-id="8523b-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>
<span data-ttu-id="8523b-149">__Risicobeperking__: Engineers uitgeschakeld Azure CDN in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="8523b-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="8523b-150">__Volgende stappen__: de onderliggende hoofdoorzaak onderzoeken en ontwikkelen van een oplossing om te voorkomen dat toekomstige exemplaren.</span><span class="sxs-lookup"><span data-stu-id="8523b-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="8523b-151">5/19/2016 - Items kan niet downloaden</span><span class="sxs-lookup"><span data-stu-id="8523b-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="8523b-152">__Samenvatting van de Impact__: tussen 17/5/2016 en 5/19/2016, is een subset van klanten problemen met het downloaden van items uit de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="8523b-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="8523b-153">Het probleem waarschijnlijk overgenomen zelf in het volgende foutbericht weergegeven dat is geretourneerd door de installatie-Module/Script voor installatie en opslaan-Module/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="8523b-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because:
End of Central Directory record could not be found.
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install.
WARNING: Package 'AzureRM' failed to install.
VERBOSE: Module 'AzureRM.Network' was saved successfully.
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the
module 'AzureRM'.
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully.
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 +
$null = PackageManagement\Save-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ +
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage)
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage
```

<span data-ttu-id="8523b-154">__Voorlopige hoofdoorzaak__: Engineers een storing in de onderliggende provider van Azure Content leveren Network (CDN), die is geïmplementeerd naar de galerie met PowerShell op 17/5/2016 geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="8523b-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>
<span data-ttu-id="8523b-155">__Risicobeperking__: Engineers uitgeschakeld Azure CDN in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="8523b-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="8523b-156">__Volgende stappen__: de onderliggende hoofdoorzaak onderzoeken en ontwikkelen van een oplossing om te voorkomen dat toekomstige exemplaren.</span><span class="sxs-lookup"><span data-stu-id="8523b-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>