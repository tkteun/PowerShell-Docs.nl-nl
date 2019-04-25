---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakket eigenaars beheren
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084144"
---
# <a name="managing-package-owners"></a><span data-ttu-id="9933a-103">Pakket eigenaars beheren</span><span class="sxs-lookup"><span data-stu-id="9933a-103">Managing package owners</span></span>

<span data-ttu-id="9933a-104">Eigendom van een pakket in de PowerShell Gallery wordt gedefinieerd door die het pakket gepubliceerd naar de galerie.</span><span class="sxs-lookup"><span data-stu-id="9933a-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="9933a-105">Soms moet deze metagegevens na het eerste pakket publiceren, wat betekent dat de metagegevens van de eigenaar moet veranderlijke dat terwijl het pakket zelf niet worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="9933a-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="9933a-106">Alle pakket-eigenaren zijn peers.</span><span class="sxs-lookup"><span data-stu-id="9933a-106">All package owners are peers.</span></span>
<span data-ttu-id="9933a-107">Dit betekent dat de eigenaar van een pakket met een nieuwe versie van een pakket kunt publiceren.</span><span class="sxs-lookup"><span data-stu-id="9933a-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="9933a-108">Het betekent ook dat de eigenaar van een pakket met een andere eigenaar van het pakket kan verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9933a-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="9933a-109">Er is geen eigenaar heeft meer dan andere eigenaren-instantie.</span><span class="sxs-lookup"><span data-stu-id="9933a-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="9933a-110">Instellen van de oorspronkelijke eigenaar van een pakket</span><span class="sxs-lookup"><span data-stu-id="9933a-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="9933a-111">Wanneer een nieuw pakket is gepubliceerd naar de PowerShell Gallery, worden de eigenaar van de eerste wordt gedefinieerd door de gebruiker die het pakket hebt gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="9933a-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="9933a-112">Dit wordt bepaald door waarvan API-sleutel in de cmdlet Publish-Module is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9933a-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="9933a-113">Eigenaren toevoegen</span><span class="sxs-lookup"><span data-stu-id="9933a-113">Adding Owners</span></span>

<span data-ttu-id="9933a-114">Nadat een pakket is gepubliceerd naar de PowerShell Gallery, is het eenvoudig extra gebruikers uitnodigen voor eigenaren van een pakket worden.</span><span class="sxs-lookup"><span data-stu-id="9933a-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="9933a-115">[Meld u bij](https://powershellgallery.com/users/account/LogOn) in PowerShell Gallery, met het account dat is de huidige eigenaar van een pakket.</span><span class="sxs-lookup"><span data-stu-id="9933a-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="9933a-116">Navigeer naar de pakketpagina van een met behulp van het tabblad 'Items', te zoeken of uw gebruikersnaam op te klikken en vervolgens [ **Mijn-pakketten beheren**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="9933a-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="9933a-117">Wanneer u bent aangemeld op als de eigenaar van een pakket, wordt er een koppeling eigenaren beheren is aan de linkerkant te klikken.</span><span class="sxs-lookup"><span data-stu-id="9933a-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="9933a-118">Geef de gebruikersnaam van de persoon die als een eigenaar wilt toevoegen en klik op 'Toevoegen'.</span><span class="sxs-lookup"><span data-stu-id="9933a-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="9933a-119">Een e-mailbericht wordt verzonden naar de nieuwe mede-eigenaar, een uitnodiging om een eigenaar van een pakket.</span><span class="sxs-lookup"><span data-stu-id="9933a-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="9933a-120">Zodra de gebruiker klikt op de koppeling, zijn ze een volledige mede-eigenaar met volledig beheer over een pakket, inclusief de mogelijkheid om andere gebruikers als eigenaren te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9933a-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="9933a-121">**HOUD ER REKENING MEE**: Totdat de nieuwe eigenaar eigenaar te zijn aangeeft, ze *niet* worden vermeld als een eigenaar van een pakket.</span><span class="sxs-lookup"><span data-stu-id="9933a-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="9933a-122">Bij het weergeven van de **eigenaren beheren** pagina, ziet u een vermelding 'in afwachting van goedkeuring' in de huidige eigenaren.</span><span class="sxs-lookup"><span data-stu-id="9933a-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="9933a-123">Deze uitnodiging kan worden verwijderd; net zoals andere eigenaren kunnen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9933a-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="9933a-124">Dit proces van de uitnodigingen wordt voorkomen dat gebruikers om andere gebruikers toevoegen als eigenaren van hun pakketten.</span><span class="sxs-lookup"><span data-stu-id="9933a-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="9933a-125">Houd er rekening mee dat de metagegevens van de "Auteurs" puur vrije tekst is. alleen 'eigenaar' worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="9933a-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="9933a-126">Eigenaars verwijderen</span><span class="sxs-lookup"><span data-stu-id="9933a-126">Removing Owners</span></span>

<span data-ttu-id="9933a-127">Wanneer een pakket meerdere eigenaren heeft en een moet worden verwijderd, is het proces is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="9933a-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="9933a-128">[Meld u bij](https://powershellgallery.com/users/account/LogOn) aan PowerShell Gallery met het account dat is de huidige eigenaar van een pakket.</span><span class="sxs-lookup"><span data-stu-id="9933a-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="9933a-129">Navigeer naar de pakketpagina van een met behulp van het tabblad pakketten, te zoeken of uw gebruikersnaam op te klikken en vervolgens [ **Mijn-pakketten beheren**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="9933a-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="9933a-130">Wanneer u bent aangemeld op als de eigenaar van een pakket, is er een koppeling eigenaren beheren aan de linkerkant te klikken;</span><span class="sxs-lookup"><span data-stu-id="9933a-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="9933a-131">Klik op de koppeling 'verwijderen' naast de eigenaar moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9933a-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="9933a-132">De overdracht van eigendom van pakket</span><span class="sxs-lookup"><span data-stu-id="9933a-132">Transferring Package Ownership</span></span>

<span data-ttu-id="9933a-133">Krijgen we soms ondersteuningsaanvragen voor het overbrengen van pakket eigendom van een gebruiker naar een andere, maar u kunt bijna altijd dit zelf doen.</span><span class="sxs-lookup"><span data-stu-id="9933a-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="9933a-134">De overdracht van eigendom van een gebruiker naar een andere is gewoon een combinatie van de bovenstaande twee functies.</span><span class="sxs-lookup"><span data-stu-id="9933a-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="9933a-135">De huidige eigenaar nodigt de nieuwe gebruiker om te worden van een mede-eigenaar en de nieuwe gebruiker accepteert de uitnodiging;</span><span class="sxs-lookup"><span data-stu-id="9933a-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="9933a-136">De nieuwe gebruiker verwijdert de oude gebruiker uit de lijst met eigenaren.</span><span class="sxs-lookup"><span data-stu-id="9933a-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="9933a-137">Deze aanvraag bij een aantal formulieren is geactiveerd, maar het proces werkt op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="9933a-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="9933a-138">Het eigendom van het pakket is gewijzigd van een ontwikkelaar naar een andere</span><span class="sxs-lookup"><span data-stu-id="9933a-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="9933a-139">Het pakket is per ongeluk gepubliceerd met behulp van het verkeerde account</span><span class="sxs-lookup"><span data-stu-id="9933a-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="9933a-140">Zwevende pakketten</span><span class="sxs-lookup"><span data-stu-id="9933a-140">Orphaned Packages</span></span>

<span data-ttu-id="9933a-141">Een laatste scenario is opgetreden, maar niet vaak.</span><span class="sxs-lookup"><span data-stu-id="9933a-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="9933a-142">Pakketten zijn wezen geworden en de enige pakket met de eigenaar van account kan niet worden gebruikt nieuwe eigenaren toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="9933a-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="9933a-143">Hier volgen enkele voorbeelden van dit scenario:</span><span class="sxs-lookup"><span data-stu-id="9933a-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="9933a-144">Account van de eigenaar is gekoppeld aan een e-mailadres dat niet meer bestaat en de gebruiker is het wachtwoord vergeten</span><span class="sxs-lookup"><span data-stu-id="9933a-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="9933a-145">De geregistreerde eigenaar heeft het bedrijf dat het pakket produceert en kan niet worden bereikt voor het bijwerken van het eigendom van het pakket verlaten</span><span class="sxs-lookup"><span data-stu-id="9933a-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="9933a-146">Vanwege een fout die slechts een handvol pakketten heeft beïnvloed, is het pakket ownerless in de galerie</span><span class="sxs-lookup"><span data-stu-id="9933a-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="9933a-147">De PowerShell Gallery-beheerders hebben toegang tot de koppeling eigenaren beheren voor een pakket.</span><span class="sxs-lookup"><span data-stu-id="9933a-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="9933a-148">Als u de rechtmatige eigenaar van een pakket en tijdelijk niet bereikbaar voor de huidige eigenaar om eigendom machtiging te krijgen, gebruikt u de koppeling 'Misbruik melden' in de galerie bereiken van de PowerShell Gallery-beheerders.</span><span class="sxs-lookup"><span data-stu-id="9933a-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="9933a-149">We volgen een proces om te controleren of uw eigendom van het pakket vervolgens.</span><span class="sxs-lookup"><span data-stu-id="9933a-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="9933a-150">Als we ontdekken dat u moet een eigenaar van het pakket, wordt er gebruikt u de koppeling eigenaren beheren voor het pakket zelf en ontvangt u de uitnodiging aan voor een eigenaar.</span><span class="sxs-lookup"><span data-stu-id="9933a-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="9933a-151">We zullen dit alleen doen nadat u hebt gecontroleerd dat u een eigenaar moet en het proces voor deze is afhankelijk van de omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="9933a-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="9933a-152">Vaak, gebruiken we de Project-URL van het pakket op een manier vinden om contact op met de projecteigenaar, maar we kunnen ook Twitter, E-mail of andere manier gebruiken voor het verbinden met de eigenaar van het project.</span><span class="sxs-lookup"><span data-stu-id="9933a-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
