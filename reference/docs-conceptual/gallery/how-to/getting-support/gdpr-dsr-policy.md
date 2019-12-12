---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galerie, Power shell, psgallery, AVG
title: AVG-naleving van PowerShell Gallery
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71329062"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="80bb0-103">AVG-naleving van PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80bb0-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="80bb0-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="80bb0-104">Overview</span></span>

<span data-ttu-id="80bb0-105">In mei 2018 heeft de Europese economische wetgeving de AVG (AVG) van kracht.</span><span class="sxs-lookup"><span data-stu-id="80bb0-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="80bb0-106">De AVG legt nieuwe regels aan voor bedrijven, overheids instanties, non-profit organisaties en andere bedrijven die goederen en diensten aanbieden aan personen in de Europese Unie (EU) of die gegevens verzamelen en analyseren die zijn gekoppeld aan de inwoners van de EU.</span><span class="sxs-lookup"><span data-stu-id="80bb0-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="80bb0-107">De AVG is van toepassing, ongeacht waar u zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="80bb0-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="80bb0-108">Dit artikel bevat stappen voor het verwijderen van persoonlijke gegevens uit de PowerShell Gallery en kan worden gebruikt ter ondersteuning van uw verplichtingen onder het AVG.</span><span class="sxs-lookup"><span data-stu-id="80bb0-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="80bb0-109">Zie de [AVG-sectie van Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) voor algemene informatie over de AVG.</span><span class="sxs-lookup"><span data-stu-id="80bb0-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="80bb0-110">Persoons gegevens</span><span class="sxs-lookup"><span data-stu-id="80bb0-110">Personally identifiable data</span></span>

<span data-ttu-id="80bb0-111">De PowerShell Gallery slaat de volgende informatie op die mogelijk wordt verstrekt door gebruikers, die persoonlijke gegevens kunnen bevatten:</span><span class="sxs-lookup"><span data-stu-id="80bb0-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="80bb0-112">PowerShell Gallery-account</span><span class="sxs-lookup"><span data-stu-id="80bb0-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="80bb0-113">Pakketten die zijn gepubliceerd op de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80bb0-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="80bb0-114">E-mail correspondentie met het PowerShell Gallery-team</span><span class="sxs-lookup"><span data-stu-id="80bb0-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="80bb0-115">De meeste gebruikers maken geen PowerShell Gallery-account.</span><span class="sxs-lookup"><span data-stu-id="80bb0-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="80bb0-116">U hoeft alleen een account op te geven als u een pakket wilt publiceren of de functie contact opnemen met eigenaar in de PowerShell Gallery wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="80bb0-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="80bb0-117">Met uitzonde ring van e-mail correspondentie die door de gebruiker is gestart, worden door de PowerShell Gallery geen persoonlijke gegevens opgeslagen voor gebruikers die geen account hebben gemaakt.</span><span class="sxs-lookup"><span data-stu-id="80bb0-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="80bb0-118">Gebruikers die een PowerShell Gallery account maken, kunnen pakketten publiceren naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80bb0-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="80bb0-119">Deze pakketten worden naar verwachting Power shell-code, maar kunnen ook andere informatie bevatten, waaronder persoonlijke gegevens.</span><span class="sxs-lookup"><span data-stu-id="80bb0-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="80bb0-120">In de onderstaande informatie ziet u hoe u alle pakketten kunt ophalen die u hebt gepubliceerd op de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80bb0-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="80bb0-121">DSR-export van PowerShell Gallery gegevens</span><span class="sxs-lookup"><span data-stu-id="80bb0-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="80bb0-122">In de volgende secties wordt beschreven hoe de PowerShell Gallery gegevens subject aanvragen (DSR) ondersteunt, door te uitleggen hoe u gegevens exporteert die in de PowerShell Gallery zijn opgeslagen, en hoe u het verwijderen van deze gegevens aanvraagt.</span><span class="sxs-lookup"><span data-stu-id="80bb0-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="80bb0-123">E-mail</span><span class="sxs-lookup"><span data-stu-id="80bb0-123">Email</span></span>

<span data-ttu-id="80bb0-124">E-mail correspondentie kan bestaan uit een van de volgende:</span><span class="sxs-lookup"><span data-stu-id="80bb0-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="80bb0-125">E-mail bericht verzonden naar de eigen aren van PowerShell Gallery-pakketten als tijdens het scannen van de code analyse is vastgesteld dat er een probleem is met een pakket dat ze naar de PowerShell Gallery hebben gepubliceerd</span><span class="sxs-lookup"><span data-stu-id="80bb0-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="80bb0-126">E-mail berichten die door iedereen naar het PowerShell Gallery-team worden verzonden met behulp van het e-mail adres op de pagina contact opnemen [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="80bb0-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="80bb0-127">Geregistreerde gebruikers die gebruikmaken van de functie contact opnemen met de eigenaar van de PowerShell Gallery om e-mail te verzenden naar de eigenaar van een pakket in de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80bb0-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="80bb0-128">E-mail berichten die worden verzonden door of naar het PowerShell Gallery een Bewaar beleid van 90 dagen hebben om mogelijke beveiligings onderzoeken te ondersteunen, moeten schadelijke code worden gedetecteerd op de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80bb0-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="80bb0-129">E-mail berichten worden na 90 dagen verwijderd door beleid.</span><span class="sxs-lookup"><span data-stu-id="80bb0-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="80bb0-130">U kunt een kopie aanvragen van alle e-mails die zijn verzonden naar of van uw e-mail adres en de PowerShell Gallery in de afgelopen 90 dagen.</span><span class="sxs-lookup"><span data-stu-id="80bb0-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="80bb0-131">Als u deze correspondentie wilt aanvragen, stuurt u een e-mail bericht naar [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)met de titel: ' DSR-aanvraag voor e-mail berichten met betrekking tot dit account '.</span><span class="sxs-lookup"><span data-stu-id="80bb0-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="80bb0-132">Geef in de hoofd tekst van het bericht aan welke gegevens u aanvraagt (bijvoorbeeld: verzend alle e-mails die zijn verzonden naar of ontvangen van dit e-mail adres.) Alle e-mail berichten met uw e-mail adres binnen 90 dagen na de aanvraag worden binnen 7 werk dagen verzonden.</span><span class="sxs-lookup"><span data-stu-id="80bb0-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="80bb0-133">PowerShell Gallery-account gegevens</span><span class="sxs-lookup"><span data-stu-id="80bb0-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="80bb0-134">Als u een PowerShell Gallery-account hebt gemaakt, kunt u alle persoonlijke gegevens die zijn opgeslagen in PowerShell Gallery vinden door de volgende stappen uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="80bb0-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="80bb0-135">Meld u aan bij de PowerShell Gallery en klik op uw gebruikers naam</span><span class="sxs-lookup"><span data-stu-id="80bb0-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="80bb0-136">De volgende pagina die wordt weer gegeven, is de account pagina, waarin het e-mail adres wordt weer gegeven dat voor het PowerShell Gallery account wordt gebruikt</span><span class="sxs-lookup"><span data-stu-id="80bb0-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="80bb0-137">Als u meer dan één account hebt gemaakt in de PowerShell Gallery, moet u deze stappen voor elk account herhalen.</span><span class="sxs-lookup"><span data-stu-id="80bb0-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="80bb0-138">Pakketten in de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80bb0-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="80bb0-139">Om het exporteren van pakketten die naar het PowerShell Gallery zijn gepubliceerd te vergemakkelijken, hebben we het script ' GetPSGalleryItemsForAuthor ' gepubliceerd op de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80bb0-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="80bb0-140">Met dit script wordt een kopie van elke versie van elk pakket dat wordt geplaatst in de PowerShell Gallery geëxporteerd op basis van de informatie in de auteur die in het pakket is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="80bb0-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="80bb0-141">De auteur wordt opgeslagen in het pakket manifest wanneer u het pakket publiceert.</span><span class="sxs-lookup"><span data-stu-id="80bb0-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="80bb0-142">Er is geen garantie dat de auteur dezelfde identiteit heeft als het account dat u gebruikt in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="80bb0-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="80bb0-143">Als u een andere waarde in het veld Auteur gebruikt, moet u die waarde opgeven wanneer u dit script gebruikt.</span><span class="sxs-lookup"><span data-stu-id="80bb0-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="80bb0-144">U kunt het script downloaden met behulp van de volgende Power shell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="80bb0-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="80bb0-145">U kunt het script vervolgens rechtstreeks uitvoeren door de volgende Power shell-opdrachten uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="80bb0-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="80bb0-146">U wordt gevraagd om de auteur en een map op het systeem op te geven waar u de pakketten wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="80bb0-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="80bb0-147">Persoonlijke gegevens verwijderen uit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="80bb0-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="80bb0-148">Als u uw PowerShell Gallery account of een pakket dat u in de PowerShell Gallery bezit wilt verwijderen, stuurt u een e-mail bericht naar cgadmin@microsoft.com met de titel: ' AVG-aanvraag voor items met betrekking tot dit account '.</span><span class="sxs-lookup"><span data-stu-id="80bb0-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="80bb0-149">In de hoofd tekst van de bericht status welke informatie u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="80bb0-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="80bb0-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="80bb0-150">For example:</span></span>

- <span data-ttu-id="80bb0-151">Verwijder versie x. y. z van mijn pakket "pakket naam"</span><span class="sxs-lookup"><span data-stu-id="80bb0-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="80bb0-152">Verwijder alle versies van mijn pakket "pakket naam"</span><span class="sxs-lookup"><span data-stu-id="80bb0-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="80bb0-153">Verwijder mijn PowerShell Gallery-account</span><span class="sxs-lookup"><span data-stu-id="80bb0-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="80bb0-154">De PowerShell Gallery-beheerders reageren binnen 7 werk dagen.</span><span class="sxs-lookup"><span data-stu-id="80bb0-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="80bb0-155">De opgegeven pakketten worden binnen 30 dagen nadat de aanvraag is verzonden, verwijderd.</span><span class="sxs-lookup"><span data-stu-id="80bb0-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
