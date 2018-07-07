---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galerie, powershell, psgallery, GDPR
title: PowerShell Gallery GDPR-naleving
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893243"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="e81a7-103">PowerShell Gallery GDPR-naleving</span><span class="sxs-lookup"><span data-stu-id="e81a7-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="e81a7-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="e81a7-104">Overview</span></span>

<span data-ttu-id="e81a7-105">Een Europese wetgeving, de General Data Protection Regulation (GDPR), wordt in mei 2018 van kracht.</span><span class="sxs-lookup"><span data-stu-id="e81a7-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="e81a7-106">De AVG legt een nieuwe regels voor bedrijven, overheidsinstellingen worden gesteld, non-profitorganisaties en andere organisaties die aanbieding goederen en diensten naar mensen in de Europese Unie (EU) of die verzamelen en analyseren van gegevens van inwoners van de EU.</span><span class="sxs-lookup"><span data-stu-id="e81a7-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="e81a7-107">De AVG is van toepassing, ongeacht waar u zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="e81a7-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="e81a7-108">In dit artikel bevat stappen voor het verwijderen van persoonlijke gegevens van de PowerShell Gallery en kan worden gebruikt voor de ondersteuning van uw verplichtingen onder de AVG.</span><span class="sxs-lookup"><span data-stu-id="e81a7-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="e81a7-109">Als u algemene informatie over GDPR zoekt, raadpleegt u de [GDPR-sectie van de Service Trust-portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="e81a7-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="e81a7-110">Persoonlijke gegevens verzenden</span><span class="sxs-lookup"><span data-stu-id="e81a7-110">Personally identifiable data</span></span>

<span data-ttu-id="e81a7-111">De PowerShell Gallery slaat de volgende informatie die kan worden geleverd door gebruikers die mogelijk persoonlijke gegevens bevatten:</span><span class="sxs-lookup"><span data-stu-id="e81a7-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="e81a7-112">PowerShell Gallery-account</span><span class="sxs-lookup"><span data-stu-id="e81a7-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="e81a7-113">Items die zijn gepubliceerd naar de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-113">Items published to the PowerShell Gallery</span></span>
- <span data-ttu-id="e81a7-114">E-mailcorrespondentie met het team van PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="e81a7-115">De meeste gebruikers maken geen een PowerShell Gallery-account.</span><span class="sxs-lookup"><span data-stu-id="e81a7-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="e81a7-116">Een account is niet vereist, tenzij u gaat publiceren van een item of de functie 'Neem contact op met eigenaar' in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e81a7-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="e81a7-117">De PowerShell Gallery slaat dan e-mailcorrespondentie gestart door de gebruiker, geen persoonlijke gegevens voor gebruikers die geen een account hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e81a7-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="e81a7-118">Gebruikers die een PowerShell Gallery-account maken kunnen items publiceren naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e81a7-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="e81a7-119">Deze items moet PowerShell-code worden verwacht, maar andere gegevens, waaronder persoonlijke gegevens kunnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="e81a7-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="e81a7-120">De informatie hieronder ziet u hoe u krijgt alle items u hebt gepubliceerd naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e81a7-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="e81a7-121">DSR-exporteren van gegevens van de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="e81a7-122">De volgende secties beschrijven hoe de PowerShell Gallery onderwerp gegevensaanvragen (DSR), ondersteunt door waarin wordt uitgelegd hoe u kunt exporteren die zijn opgeslagen in de PowerShell Gallery en het verwijderen van deze informatie aanvragen.</span><span class="sxs-lookup"><span data-stu-id="e81a7-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="e81a7-123">E-mail</span><span class="sxs-lookup"><span data-stu-id="e81a7-123">Email</span></span>

<span data-ttu-id="e81a7-124">E-mailcorrespondentie, kan het volgende omvatten:</span><span class="sxs-lookup"><span data-stu-id="e81a7-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="e81a7-125">E-mailbericht verzonden naar de eigenaars van de PowerShell Gallery items als de analyse code scant is een probleem opgetreden met een willekeurig item die ze hebt gepubliceerd naar de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="e81a7-126">E-mailbericht verzonden door iemand die naar de PowerShell Gallery-team met behulp van het e-mailadres op de pagina 'Contact opnemen' [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="e81a7-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="e81a7-127">Geregistreerde gebruikers die de functie 'Neem contact op met eigenaar' in de PowerShell Gallery gebruiken om e-mail te verzenden naar de eigenaar van een item in de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="e81a7-128">E-mailberichten verzonden naar de PowerShell Gallery of door hebben een bewaarbeleid van 90 dagen voor de ondersteuning van onderzoeken van mogelijke beveiliging moet schadelijke code worden gedetecteerd in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e81a7-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="e81a7-129">E-mailberichten worden na 90 dagen verwijderd door het beleid.</span><span class="sxs-lookup"><span data-stu-id="e81a7-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="e81a7-130">U kunt kopieën van alle e-mailberichten verzonden naar of van uw e-mailadres en de PowerShell Gallery in de afgelopen 90 dagen aanvragen.</span><span class="sxs-lookup"><span data-stu-id="e81a7-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="e81a7-131">Om aan te vragen van deze overeenkomst, stuur een e-mail naar [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), met de titel: "DSR-aanvraag voor e-mailberichten met betrekking tot dit account.</span><span class="sxs-lookup"><span data-stu-id="e81a7-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="e81a7-132">In de hoofdtekst van het bericht, staat welke gegevens u aanvraagt (bijvoorbeeld: Stuur alle e-mailberichten verzonden naar of ontvangen van dit e-mailadres.) Alle e-mailberichten met betrekking tot uw e-mailadres binnen 90 dagen na de aanvraag wordt verzonden binnen 7 dagen.</span><span class="sxs-lookup"><span data-stu-id="e81a7-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="e81a7-133">PowerShell Gallery-accountgegevens</span><span class="sxs-lookup"><span data-stu-id="e81a7-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="e81a7-134">Als u een PowerShell Gallery-account hebt gemaakt, vindt u alle persoonlijke gegevens die zijn opgeslagen in de PowerShell Gallery door de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="e81a7-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="e81a7-135">Aanmelden bij de PowerShell Gallery, en klik vervolgens op uw gebruikersnaam</span><span class="sxs-lookup"><span data-stu-id="e81a7-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="e81a7-136">De volgende pagina wordt weergegeven is de Account-pagina, waarin het e-mailadres dat is gebruikt voor het account van de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="e81a7-137">Als u meer dan één account hebt gemaakt in de PowerShell Gallery, moet u deze stappen herhalen voor elk account.</span><span class="sxs-lookup"><span data-stu-id="e81a7-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="e81a7-138">Items in de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="e81a7-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="e81a7-139">Om te kunnen exporteren items die zijn gepubliceerd naar de PowerShell Gallery, hebben we het script "GetPSGalleryItemsForAuthor" gepubliceerd naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e81a7-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="e81a7-140">Met dit script wordt een kopie van elke versie van elk item in de PowerShell Gallery op basis van de van auteurgegevens die zijn opgeslagen in het artikel plaatsen geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="e81a7-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="e81a7-141">De auteur van de wordt opgeslagen in het itemmanifest van de wanneer u uw item publiceert.</span><span class="sxs-lookup"><span data-stu-id="e81a7-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="e81a7-142">Er is geen garantie dat de auteur van de dezelfde id als het account dat u in de PowerShell Gallery gebruikt is.</span><span class="sxs-lookup"><span data-stu-id="e81a7-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="e81a7-143">Als u een andere waarde in het veld ' auteur ' gebruikt, moet u die waarde leveren wanneer dit script te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e81a7-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="e81a7-144">U kunt het script downloaden met behulp van de volgende PowerShell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="e81a7-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="e81a7-145">U kunt het script vervolgens rechtstreeks door het uitvoeren van de volgende PowerShell-opdrachten uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="e81a7-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="e81a7-146">U wordt gevraagd om op te geven van de auteur en een map op uw systeem waar u de items worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e81a7-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="e81a7-147">Verwijderen van persoonlijke gegevens uit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="e81a7-148">Als u wilt verwijderen van de PowerShell Gallery-account of een item dat u in de PowerShell Gallery eigenaar bent, e-mailbericht verzendt cgadmin@microsoft.com met de titel: 'AVG-aanvraag voor artikelen met betrekking tot dit account'.</span><span class="sxs-lookup"><span data-stu-id="e81a7-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="e81a7-149">In de hoofdtekst van het bericht staat welke gegevens u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e81a7-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="e81a7-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e81a7-150">For example:</span></span>

- <span data-ttu-id="e81a7-151">Verwijder x.y.z versie van het item "itemnaam"</span><span class="sxs-lookup"><span data-stu-id="e81a7-151">Please delete version x.y.z of my item "item name"</span></span>
- <span data-ttu-id="e81a7-152">Verwijder alle versies van mijn item "itemnaam"</span><span class="sxs-lookup"><span data-stu-id="e81a7-152">Please delete all versions of my item "item name"</span></span>
- <span data-ttu-id="e81a7-153">Verwijder op mijn account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e81a7-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="e81a7-154">De PowerShell Gallery-beheerders wordt binnen 7 werkdagen beantwoorden.</span><span class="sxs-lookup"><span data-stu-id="e81a7-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="e81a7-155">De items die is opgegeven worden, verwijderd binnen 30 dagen nadat de aanvraag is verzonden.</span><span class="sxs-lookup"><span data-stu-id="e81a7-155">The items specified will be deleted within 30 days after the request is sent.</span></span>