---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galerie, powershell, psgallery, GDPR
title: PowerShell-galerie GDPR naleving
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189751"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="80ef2-103">PowerShell-galerie GDPR naleving</span><span class="sxs-lookup"><span data-stu-id="80ef2-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="80ef2-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="80ef2-104">Overview</span></span>

<span data-ttu-id="80ef2-105">In mei 2018 wordt Europese privacywetgeving is de algemene gegevens beveiliging regelgeving (GDPR), van kracht.</span><span class="sxs-lookup"><span data-stu-id="80ef2-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="80ef2-106">De GDPR legt nieuwe regels voor bedrijven, overheidsinstanties, non-profitorganisaties en andere organisaties aanbieding goederen en diensten naar mensen in de Europese Unie, of dat verzamelen en analyseren van gegevens die zijn gekoppeld aan de EU inwoners.</span><span class="sxs-lookup"><span data-stu-id="80ef2-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="80ef2-107">De GDPR is van toepassing ongeacht waar u zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="80ef2-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="80ef2-108">Dit artikel bevat verschillende stappen voor het verwijderen van persoonlijke gegevens van de PowerShell Gallery en kan worden gebruikt ter ondersteuning van uw verplichtingen onder de GDPR.</span><span class="sxs-lookup"><span data-stu-id="80ef2-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="80ef2-109">Als u algemene informatie over GDPR zoekt, raadpleegt u de [GDPR sectie van de portal Service vertrouwen](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="80ef2-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="80ef2-110">Persoonlijk herleidbare informatie</span><span class="sxs-lookup"><span data-stu-id="80ef2-110">Personally identifiable data</span></span>

<span data-ttu-id="80ef2-111">De PowerShell-galerie slaat de volgende informatie die kan worden geleverd door gebruikers die mogelijk persoonlijke gegevens bevatten:</span><span class="sxs-lookup"><span data-stu-id="80ef2-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="80ef2-112">Account voor PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80ef2-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="80ef2-113">Items die zijn gepubliceerd naar de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="80ef2-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="80ef2-114">E-mailcorrespondentie met het team PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80ef2-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="80ef2-115">De meeste gebruikers doen PowerShell Gallery account niet maken.</span><span class="sxs-lookup"><span data-stu-id="80ef2-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="80ef2-116">Een account is niet vereist tenzij u gaat een item publiceren of de functie 'Eigenaar Neem contact op met' in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="80ef2-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="80ef2-117">De PowerShell-galerie slaat dan e-mailcorrespondentie geïnitieerd door de gebruiker, geen persoonlijk herleidbare informatie voor gebruikers die geen account hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="80ef2-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="80ef2-118">Gebruikers die een PowerShell-galerie-account maken kunnen u items publiceren naar de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="80ef2-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="80ef2-119">Deze items moet PowerShell-code worden verwacht, maar andere informatie, inclusief persoonlijke gegevens kunnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="80ef2-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="80ef2-120">De informatie hieronder wordt beschreven hoe u alle items kan krijgen u hebt gepubliceerd naar de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="80ef2-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="80ef2-121">DSR exporteren van gegevens van de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="80ef2-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="80ef2-122">De volgende secties wordt beschreven hoe onderwerp gegevensaanvragen (DSR) in de PowerShell-galerie worden ondersteunt door uitleg over het exporteren van gegevens die zijn opgeslagen in de PowerShell-galerie en het aanvragen van deze informatie is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="80ef2-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="80ef2-123">E-mail</span><span class="sxs-lookup"><span data-stu-id="80ef2-123">Email</span></span>

<span data-ttu-id="80ef2-124">E-mailcorrespondentie kan het volgende omvatten:</span><span class="sxs-lookup"><span data-stu-id="80ef2-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="80ef2-125">E-mailbericht verzonden naar de eigenaren van PowerShell-galerie-items als de code-analyse scant gedetecteerd een probleem met een ze hebt gepubliceerd naar de PowerShell-galerie-item</span><span class="sxs-lookup"><span data-stu-id="80ef2-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="80ef2-126">E-mailbericht verzonden door iemand die naar de PowerShell Gallery team met behulp van het e-mailadres op de pagina 'Contact met ons opnemen' (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="80ef2-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="80ef2-127">Gebruikers die de functie 'Eigenaar Neem contact op met' in de galerie met PowerShell gebruiken om e-mail te verzenden naar de eigenaar van een item in de PowerShell-galerie geregistreerd</span><span class="sxs-lookup"><span data-stu-id="80ef2-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="80ef2-128">E-mailberichten verzonden naar de galerie met PowerShell of door hebben een bewaarbeleid van 90 dagen voor de ondersteuning van onderzoeken van mogelijke beveiliging moet schadelijke code worden gedetecteerd in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="80ef2-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="80ef2-129">E-mailberichten worden na 90 dagen verwijderd door het beleid.</span><span class="sxs-lookup"><span data-stu-id="80ef2-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="80ef2-130">Kopieën van alle e-mailberichten verzonden naar of van uw e-mailadres en de PowerShell-galerie in de voorbije 90 dagen mag worden aangevraagd.</span><span class="sxs-lookup"><span data-stu-id="80ef2-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="80ef2-131">Om aan te vragen deze overeenkomst, een e-mail sturen naar cgadmin@microsoft.com, met de titel: 'DSR aanvraag voor e-mailberichten met betrekking tot dit account'.</span><span class="sxs-lookup"><span data-stu-id="80ef2-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="80ef2-132">In de hoofdtekst van het bericht staat welke informatie die u aanvraagt (bijvoorbeeld: Stuur alle e-mailberichten verzonden naar of ontvangen van dit e-mailadres.) Alle e-mailberichten met betrekking tot uw e-mailadres binnen 90 dagen van de aanvraag wordt verzonden binnen 7 dagen.</span><span class="sxs-lookup"><span data-stu-id="80ef2-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="80ef2-133">Accountgegevens PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80ef2-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="80ef2-134">Als u een PowerShell-galerie-account hebt gemaakt, vindt u alle persoonlijke gegevens die zijn opgeslagen in PowerShell Gallery door de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="80ef2-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="80ef2-135">Aanmelden bij de PowerShell-galerie en klik vervolgens op uw gebruikersnaam</span><span class="sxs-lookup"><span data-stu-id="80ef2-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="80ef2-136">De volgende pagina weergegeven, is de Account-pagina, waarin het e-mailadres dat is gebruikt voor het account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80ef2-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="80ef2-137">Als u meer dan één account hebt gemaakt in de PowerShell-galerie, moet u deze stappen herhalen voor elke account.</span><span class="sxs-lookup"><span data-stu-id="80ef2-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="80ef2-138">Items in de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="80ef2-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="80ef2-139">Te vergemakkelijken uitvoerende items die zijn gepubliceerd naar de PowerShell-galerie, hebben we het script 'GetPSGalleryItemsForAuthor' gepubliceerd naar de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="80ef2-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="80ef2-140">Dit script exporteert u een kopie van elke versie van elk item in de PowerShell-galerie op basis van de auteur informatie opgeslagen in het item geplaatst.</span><span class="sxs-lookup"><span data-stu-id="80ef2-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="80ef2-141">De auteur wordt opgeslagen in het manifest item wanneer u uw item publiceren.</span><span class="sxs-lookup"><span data-stu-id="80ef2-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="80ef2-142">Er is geen garantie dat de auteur is dezelfde id als het account waarmee u in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="80ef2-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="80ef2-143">Als u een andere waarde in het veld Auteur gebruikt, moet u op te geven dat de waarde bij gebruik van dit script.</span><span class="sxs-lookup"><span data-stu-id="80ef2-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="80ef2-144">U kunt het script downloaden met behulp van de volgende PowerShell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="80ef2-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="80ef2-145">U kunt het script vervolgens rechtstreeks uitvoeren met de volgende PowerShell-opdrachten:</span><span class="sxs-lookup"><span data-stu-id="80ef2-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="80ef2-146">U wordt gevraagd de auteur en een map op uw systeem waar u de items worden opgeslagen op te geven.</span><span class="sxs-lookup"><span data-stu-id="80ef2-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="80ef2-147">Verwijderen van persoonlijke gegevens van de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80ef2-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="80ef2-148">Verwijder uw account PowerShell Gallery of een item dat u in de PowerShell-galerie bezit, e-mailbericht verzendt cgadmin@microsoft.com met de titel: 'GDPR aanvraag voor artikelen met betrekking tot dit account'.</span><span class="sxs-lookup"><span data-stu-id="80ef2-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="80ef2-149">In de hoofdtekst van het bericht staat welke gegevens u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="80ef2-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="80ef2-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="80ef2-150">For example:</span></span>

* <span data-ttu-id="80ef2-151">Verwijder versie x.y.z van mijn 'item name'-item</span><span class="sxs-lookup"><span data-stu-id="80ef2-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="80ef2-152">Verwijder alle versies van het item 'item name'</span><span class="sxs-lookup"><span data-stu-id="80ef2-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="80ef2-153">Verwijder op mijn account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80ef2-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="80ef2-154">De beheerders PowerShell Gallery moeten reageren binnen 7 dagen.</span><span class="sxs-lookup"><span data-stu-id="80ef2-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="80ef2-155">De opgegeven items worden verwijderd binnen 30 dagen nadat de aanvraag is verzonden.</span><span class="sxs-lookup"><span data-stu-id="80ef2-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
