---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Beheer van eigenaren
ms.openlocfilehash: fcd538148f9ff1ac96324b567d54d643f1756c93
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="managing-item-owners"></a><span data-ttu-id="bc21e-103">Beheer van eigenaren</span><span class="sxs-lookup"><span data-stu-id="bc21e-103">Managing Item Owners</span></span>

<span data-ttu-id="bc21e-104">Eigendom van een item in de PowerShell-galerie wordt gedefinieerd door die het item gepubliceerd naar de galerie.</span><span class="sxs-lookup"><span data-stu-id="bc21e-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="bc21e-105">Soms moet deze metagegevens afgezien van het eerste item publiceren, wat betekent dat de metagegevens van de eigenaar moet veranderlijke dat terwijl het item zelf kan niet worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="bc21e-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="bc21e-106">Alle item eigenaars zijn peers.</span><span class="sxs-lookup"><span data-stu-id="bc21e-106">All item owners are peers.</span></span> <span data-ttu-id="bc21e-107">Dit betekent dat de eigenaar van elk item een nieuwe versie van een item kunt publiceren.</span><span class="sxs-lookup"><span data-stu-id="bc21e-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="bc21e-108">Het betekent ook dat de eigenaar van elk item een andere eigenaar van het item kunt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bc21e-108">It also means that any item owner can remove any other item owner.</span></span> <span data-ttu-id="bc21e-109">Er is geen eigenaar heeft meer dan andere eigenaars-instantie.</span><span class="sxs-lookup"><span data-stu-id="bc21e-109">No owner has more authority than other owners.</span></span>  

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="bc21e-110">De eerste eigenaar van een Item instellen</span><span class="sxs-lookup"><span data-stu-id="bc21e-110">Setting an Item's Initial Owner</span></span> 

<span data-ttu-id="bc21e-111">Wanneer een nieuw item is gepubliceerd naar de PowerShell-galerie, is de eigenaar van de eerste gedefinieerd door de gebruiker die het item wordt gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="bc21e-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="bc21e-112">Dit wordt bepaald door waarvan API-sleutel in de cmdlet Publish-Module is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bc21e-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="bc21e-113">Eigenaars toevoegen</span><span class="sxs-lookup"><span data-stu-id="bc21e-113">Adding Owners</span></span>

<span data-ttu-id="bc21e-114">Nadat een item is gepubliceerd naar de PowerShell-galerie, is het eenvoudig om uit te nodigen extra gebruikers eigenaren van een item wordt omgezet.</span><span class="sxs-lookup"><span data-stu-id="bc21e-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="bc21e-115">[Meld u aan](https://powershellgallery.com/users/account/LogOn) naar de PowerShell-galerie met het account dat de huidige eigenaar van een item.</span><span class="sxs-lookup"><span data-stu-id="bc21e-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="bc21e-116">Navigeer naar de pagina van een item met behulp van het tabblad 'Items', zoeken of uw gebruikersnaam op te klikken en vervolgens [ **mijn Items beheren**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="bc21e-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="bc21e-117">Wanneer aangemeld als eigenaar van een item, wordt er een koppeling eigenaren beheren is aan de linkerkant te klikken.</span><span class="sxs-lookup"><span data-stu-id="bc21e-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="bc21e-118">Geef de gebruikersnaam van de persoon die als een eigenaar wilt toevoegen en klik op 'Add'.</span><span class="sxs-lookup"><span data-stu-id="bc21e-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="bc21e-119">Een e-mailbericht wordt vervolgens naar de nieuwe mede-eigenaar verzonden als een uitnodiging voor een eigenaar van een item.</span><span class="sxs-lookup"><span data-stu-id="bc21e-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="bc21e-120">Als die gebruiker op de koppeling klikt, zijn ze een volledige mede-eigenaar met volledige controle over een item, inclusief de mogelijkheid om andere gebruikers als eigenaars te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bc21e-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="bc21e-121">**Opmerking**: totdat de nieuwe eigenaar eigendom bevestigt, ze *niet* worden vermeld als een eigenaar van een item.</span><span class="sxs-lookup"><span data-stu-id="bc21e-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="bc21e-122">Tijdens het weergeven van de **eigenaren beheren** pagina ziet u een vermelding 'in afwachting van goedkeuring' in de huidige eigenaren.</span><span class="sxs-lookup"><span data-stu-id="bc21e-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="bc21e-123">Deze uitnodiging kan worden verwijderd; Net als andere eigenaren kunnen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="bc21e-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="bc21e-124">Dit proces van uitnodigingen wordt voorkomen dat gebruikers ten onrechte toevoegen van andere gebruikers als eigenaars van hun items.</span><span class="sxs-lookup"><span data-stu-id="bc21e-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="bc21e-125">Houd er rekening mee dat de metagegevens 'Auteurs' puur vrije tekst. alleen 'eigenaar' worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="bc21e-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="bc21e-126">Eigenaars verwijderen</span><span class="sxs-lookup"><span data-stu-id="bc21e-126">Removing Owners</span></span>
<span data-ttu-id="bc21e-127">Wanneer een item meerdere eigenaars zijn en een moet worden verwijderd, is het proces is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="bc21e-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="bc21e-128">[Meld u aan](https://powershellgallery.com/users/account/LogOn) voor PowerShell Gallery met het account dat de huidige eigenaar van een item;</span><span class="sxs-lookup"><span data-stu-id="bc21e-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="bc21e-129">Navigeer naar de pagina van een item met behulp van het tabblad Items, zoeken of uw gebruikersnaam op te klikken en vervolgens [ **mijn Items beheren**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="bc21e-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="bc21e-130">Wanneer aangemeld als eigenaar van een item, is er een koppeling eigenaren beheren aan de linkerkant te klikken;</span><span class="sxs-lookup"><span data-stu-id="bc21e-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="bc21e-131">Klik op de koppeling 'verwijderen' naast de eigenaar moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="bc21e-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="bc21e-132">Item eigendom overdragen</span><span class="sxs-lookup"><span data-stu-id="bc21e-132">Transferring Item Ownership</span></span>
<span data-ttu-id="bc21e-133">Soms krijgen we ondersteuningsaanvragen voor het item het eigendom overdraagt van een gebruiker naar een andere, maar u kunt bijna altijd dit zelf doen.</span><span class="sxs-lookup"><span data-stu-id="bc21e-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="bc21e-134">De overdracht van eigendom van de ene gebruiker naar de andere is gewoon een combinatie van de bovenstaande functies.</span><span class="sxs-lookup"><span data-stu-id="bc21e-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="bc21e-135">De huidige eigenaar nodigt de nieuwe gebruiker om te worden van een mede-eigenaar en de nieuwe gebruiker accepteert de uitnodiging;</span><span class="sxs-lookup"><span data-stu-id="bc21e-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="bc21e-136">De nieuwe gebruiker verwijdert de oude gebruiker uit de lijst met eigenaren.</span><span class="sxs-lookup"><span data-stu-id="bc21e-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="bc21e-137">Deze aanvraag heeft geleverd in onder een aantal formulieren, maar het proces werkt op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="bc21e-137">This request has come in under a couple forms but the process works the same.</span></span>

* <span data-ttu-id="bc21e-138">Het item eigendom wordt van een ontwikkelaar gewijzigd naar een andere</span><span class="sxs-lookup"><span data-stu-id="bc21e-138">The item ownership is changing from one developer to another</span></span>
* <span data-ttu-id="bc21e-139">Het item is per ongeluk gepubliceerd met de verkeerde account</span><span class="sxs-lookup"><span data-stu-id="bc21e-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="bc21e-140">Zwevende Items</span><span class="sxs-lookup"><span data-stu-id="bc21e-140">Orphaned Items</span></span>
<span data-ttu-id="bc21e-141">Een laatste scenario heeft plaatsgevonden, maar niet vaak.</span><span class="sxs-lookup"><span data-stu-id="bc21e-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="bc21e-142">Items wezen zijn geworden en de enige item eigenaarsaccount kan niet worden gebruikt voor het toevoegen van nieuwe eigenaars.</span><span class="sxs-lookup"><span data-stu-id="bc21e-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="bc21e-143">Hier volgen enkele voorbeelden van dit scenario:</span><span class="sxs-lookup"><span data-stu-id="bc21e-143">Here are some examples of this scenario:</span></span>

* <span data-ttu-id="bc21e-144">Account van de eigenaar is gekoppeld aan een e-mailadres dat niet meer bestaat en de gebruiker het wachtwoord is vergeten</span><span class="sxs-lookup"><span data-stu-id="bc21e-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
* <span data-ttu-id="bc21e-145">De geregistreerde eigenaar heeft het bedrijf dat het item levert en kan niet worden bereikt voor het bijwerken van het item eigendom verlaten</span><span class="sxs-lookup"><span data-stu-id="bc21e-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
* <span data-ttu-id="bc21e-146">Vanwege een fout die is alleen van invloed op een aantal items, het item zich enigszins ownerless op de galerie</span><span class="sxs-lookup"><span data-stu-id="bc21e-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="bc21e-147">De PowerShell-galerie-beheerders hebben toegang tot de koppeling eigenaren beheren voor een item.</span><span class="sxs-lookup"><span data-stu-id="bc21e-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="bc21e-148">Als u de rechtmatige eigenaar van een item en geen toegang tot de huidige eigenaar om eigendom machtiging te krijgen, gebruikt u de koppeling 'Misbruik melden' in de galerie bereiken van de PowerShell-galerie-beheerders.</span><span class="sxs-lookup"><span data-stu-id="bc21e-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="bc21e-149">Er wordt een proces om te controleren of uw eigendom van het item volgt.</span><span class="sxs-lookup"><span data-stu-id="bc21e-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="bc21e-150">Als we moet u een eigenaar van het item bepalen, wordt de koppeling eigenaren beheren gebruiken voor het item onszelf en verzendt u de uitnodiging om te worden van een eigenaar.</span><span class="sxs-lookup"><span data-stu-id="bc21e-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="bc21e-151">We zullen dit alleen doen nadat u hebt gecontroleerd dat u een eigenaar moet en het proces voor dit af van de omstandigheden hangt.</span><span class="sxs-lookup"><span data-stu-id="bc21e-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="bc21e-152">Vaak het item Project URL zullen worden gebruikt voor het vinden van een manier om contact op met de eigenaar van het project, maar we kunnen ook Twitter, E-mail of andere wijze gebruikmaken voor communicatie met de eigenaar van het project.</span><span class="sxs-lookup"><span data-stu-id="bc21e-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>

