---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a>Status van de PowerShell-galerie
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10-10-2017 - PowerShell Gallery niet beschikbaar voor 2 uur 10/10/17

__Samenvatting van de Impact__: de PowerShell Gallery ervaren een periode van zeer hoge latentie, wat resulteert in onregelmatige verbindingsproblemen vanaf ongeveer 17: 00 uur (PDT) 10/10/17. Tijdens het omzetten van het probleem, is de site offline gehaald gedurende 2 uur ongeveer 10 uur (PDT) wordt gestart. De site is hersteld binnen enkele ogenblikken vóór middernacht 10/10/2017. 
 
__Root Cause__: de hoofdoorzaak van hoge latentie nog steeds wordt onderzocht.

__Resolutie__: de webservices moest offline worden gehaald en hersteld om de primaire probleem op te lossen. 

__Volgende stappen__: de hoofdoorzaak van het oorspronkelijke probleem wordt onderzocht.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>01-06/2017 - implementeren in Azure Automation momenteel niet beschikbaar

__Samenvatting van de Impact__: items met afhankelijkheden implementeren op Azure Automation van de PowerShell Gallery is momenteel niet beschikbaar.  Importeren van items van de PowerShell Gallery uit in Azure Automation is nog steeds beschikbaar.  
 
__Hoofdoorzaak__: Items die zijn afhankelijk van andere en eerder zijn geïmplementeerd op Azure Automation wordt niet geïmplementeerd voor een Azure Automation. Engineers hebt vastgesteld dat een probleem met hoe ARM-sjablonen worden gegenereerd voor items met afhankelijkheden voor het implementeren in Azure Automation-functionaliteit.

__Resolutie__: Engineers werkt als probleem wilt oplossen.  De huidige oplossing voor gebruikers is het item van de PowerShell Gallery van importeren in Azure Automation. 

__Volgende stappen__: Engineers kort de oplossing worden vrijgegeven.  In de tussentijd gebruik de aanbevolen oplossing. 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11-04-2017 - gebruikers kan niet aanmelden met Azure Active Directory (AAD) accounts

__Samenvatting van de Impact__: sommige gebruikers kunnen zich aanmelden bij de PowerShell-galerie met behulp van Azure AD-Accounts. 
 
__Hoofdoorzaak__: tijdens een update veiliger communiceren met AAD een wijziging in de instelling is overgeslagen. De tests uitgevoerd voor het valideren van de wijziging bevat geen bepaalde soorten AAD-accounts, zodat de implementatie plaatsvindt.

__Resolutie__: Engineers de ontbrekende instelling vastgesteld en gecorrigeerd van het probleem. 

__Volgende stappen__: We zullen worden wijzigen onze tests zodanig dat die een uitgebreidere set van AAD-accounttypen.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27-03/2017 - opgelost: kan geen afzonderlijke module en het script pagina's te zien

__Samenvatting van de Impact__: directe koppelingen naar de afzonderlijke pagina's de module en het script op https://www.powershellgallery.com verloren gegaan. Dit is in alle regio's worden gerapporteerd. Dit heeft geen invloed op een van de cmdlets PowerShellGet ie., installatie-Module installatiescript, Update-Module-updatescript Publish-Module Publish-Scirpt nog steeds werken.

__Root Cause__: Engineers de oorzaak geïdentificeerd als een probleem waardoor sociale media knoppen zoals Facebook naar de pagina.  

__Resolutie__: Engineers het probleem is opgelost door de Facebook count-informatie uit te schakelen.

__Volgende stappen__: We een interne bijhouden probleem om op te lossen ons gebruik van Facebook-API hebt geopend.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15-12-2016 - kan geen e-mailberichten via de website van de PowerShellGallery verzenden

__Samenvatting van de Impact__: tussen 13-12-2016 en 15-12-2016 geen berichten verzonden via de Contact-eigenaars, eigenaren beheren, contact opnemen met ondersteuning of misbruik van rapport niet zijn ontvangen door de beheerders van PowerShell-galerie.  
__Root Cause__: Engineers de oorzaak geïdentificeerd als een verificatieprobleem met de SMTP-server.  
__Resolutie__: Engineers konden los het verificatieprobleem en herstel verbinding met de SMTP-server.  
__Volgende stappen__: als u de contactpersoon eigenaars, eigenaren beheren, contact opnemen met ondersteuning of misbruik melden koppelingen gebruikt voor het verzenden van e-mail naar cgadmin@microsoft.com gedurende deze tijd en we heeft niet gereageerd, probeer het opnieuw. Onze excuses voor het ongemak.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>8-10/2016 - opgelost: kan geen e-mailberichten verzendencgadmin@microsoft.com

__Samenvatting van de Impact__: tussen 5-8-2016 en 8/10/2016 klanten kon niet worden verzonden e-mailberichten cgadmin@microsoft.com, of gebruik de functie Contact met ons opnemen.  
__Root Cause__: Engineers de oorzaak geïdentificeerd als een wijziging in de configuratie van het e-mailaccount.  
__Resolutie__: Engineers gewerkt om de configuratieprobleem te verhelpen.  
__Volgende stappen__: als u de koppeling Contact met ons gebruikt of e-mail naar verzonden cgadmin@microsoft.com gedurende deze tijd en we heeft niet gereageerd, probeer het opnieuw. Hartelijk dank voor uw geduld.



## <a name="7132016---download-items-failed"></a>13-7/2016 - Items kan niet downloaden

__Samenvatting van de Impact__: tussen 11-7-2016 en 13-7-2016, is een subset van klanten problemen met het downloaden van items uit de PowerShell-galerie. Het probleem waarschijnlijk overgenomen zelf in het volgende foutbericht weergegeven dat is geretourneerd door de installatie-Module/Script voor installatie en opslaan-Module/Save-Script:

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

__Voorlopige hoofdoorzaak__: Engineers een probleem vastgesteld met Azure inhoud leveren Network (CDN), die is geïmplementeerd naar de galerie met PowerShell op 11-7-2016.  
__Risicobeperking__: Engineers uitgeschakeld Azure CDN in de PowerShell-galerie.  
__Volgende stappen__: de onderliggende hoofdoorzaak onderzoeken en ontwikkelen van een oplossing om te voorkomen dat toekomstige exemplaren.


## <a name="5192016---download-items-failed"></a>5/19/2016 - Items kan niet downloaden
__Samenvatting van de Impact__: tussen 17/5/2016 en 5/19/2016, is een subset van klanten problemen met het downloaden van items uit de PowerShell-galerie. Het probleem waarschijnlijk overgenomen zelf in het volgende foutbericht weergegeven dat is geretourneerd door de installatie-Module/Script voor installatie en opslaan-Module/Save-Script:

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

__Voorlopige hoofdoorzaak__: Engineers een storing in de onderliggende provider van Azure Content leveren Network (CDN), die is geïmplementeerd naar de galerie met PowerShell op 17/5/2016 geïdentificeerd.  
__Risicobeperking__: Engineers uitgeschakeld Azure CDN in de PowerShell-galerie.  
__Volgende stappen__: de onderliggende hoofdoorzaak onderzoeken en ontwikkelen van een oplossing om te voorkomen dat toekomstige exemplaren.

