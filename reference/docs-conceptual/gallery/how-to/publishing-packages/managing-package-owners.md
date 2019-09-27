---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Pakket eigenaren beheren
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329020"
---
# <a name="managing-package-owners"></a><span data-ttu-id="40293-103">Pakket eigenaren beheren</span><span class="sxs-lookup"><span data-stu-id="40293-103">Managing package owners</span></span>

<span data-ttu-id="40293-104">Het eigendom van een pakket in de PowerShell Gallery wordt gedefinieerd door wie het pakket heeft gepubliceerd in de galerie.</span><span class="sxs-lookup"><span data-stu-id="40293-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="40293-105">Soms moeten deze meta gegevens worden beheerd na de initiële pakket publicatie, wat betekent dat de meta gegevens van de eigenaar onveranderbaar moeten zijn terwijl het pakket zelf niet is.</span><span class="sxs-lookup"><span data-stu-id="40293-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="40293-106">Alle pakket eigenaren zijn peers.</span><span class="sxs-lookup"><span data-stu-id="40293-106">All package owners are peers.</span></span>
<span data-ttu-id="40293-107">Dit betekent dat elke pakket eigenaar een nieuwe versie van een pakket kan publiceren.</span><span class="sxs-lookup"><span data-stu-id="40293-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="40293-108">Dit betekent ook dat elke eigenaar van het pakket alle andere pakket eigenaars kan verwijderen.</span><span class="sxs-lookup"><span data-stu-id="40293-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="40293-109">Geen enkele eigenaar heeft meer bevoegdheden dan andere eigen aren.</span><span class="sxs-lookup"><span data-stu-id="40293-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="40293-110">De eerste eigenaar van een pakket instellen</span><span class="sxs-lookup"><span data-stu-id="40293-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="40293-111">Wanneer een nieuw pakket wordt gepubliceerd naar PowerShell Gallery, wordt de eerste eigenaar gedefinieerd door de gebruiker die het pakket heeft gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="40293-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="40293-112">Dit wordt bepaald door de API-sleutel die is gebruikt in de cmdlet Publish-module.</span><span class="sxs-lookup"><span data-stu-id="40293-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="40293-113">Eigen aren toevoegen</span><span class="sxs-lookup"><span data-stu-id="40293-113">Adding Owners</span></span>

<span data-ttu-id="40293-114">Wanneer een pakket is gepubliceerd naar de PowerShell Gallery, is het eenvoudig om extra gebruikers uit te nodigen om eigenaar te worden van een pakket.</span><span class="sxs-lookup"><span data-stu-id="40293-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="40293-115">[Meld](https://powershellgallery.com/users/account/LogOn) u aan bij de PowerShell Gallery met het account dat de huidige eigenaar is van een pakket.</span><span class="sxs-lookup"><span data-stu-id="40293-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="40293-116">Navigeer naar een pakket pagina met behulp van het tabblad ' items ', zoek of klik op uw gebruikers naam en vervolgens op [**mijn pakketten beheren**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="40293-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="40293-117">Wanneer u bent aangemeld als eigenaar van een pakket, kunt u aan de linkerkant op de link eigen aren beheren klikken.</span><span class="sxs-lookup"><span data-stu-id="40293-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="40293-118">Voer de gebruikers naam in van de persoon die u wilt toevoegen als eigenaar en klik op toevoegen.</span><span class="sxs-lookup"><span data-stu-id="40293-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="40293-119">Er wordt een e-mail bericht verzonden naar de nieuwe mede-eigenaar, als een uitnodiging om eigenaar te worden van een pakket.</span><span class="sxs-lookup"><span data-stu-id="40293-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="40293-120">Zodra de gebruiker op de koppeling klikt, is deze een volledige mede-eigenaar met volledige controle over een pakket, inclusief de mogelijkheid om andere gebruikers als eigen aren te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="40293-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="40293-121">**OPMERKING**: Totdat de nieuwe eigenaar het eigendom bevestigt, *wordt deze niet* vermeld als een eigenaar van een pakket.</span><span class="sxs-lookup"><span data-stu-id="40293-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="40293-122">Wanneer u de pagina **eigen aars beheren** bekijkt, ziet u de vermelding ' goed keuring in behandeling ' in de huidige eigen aars.</span><span class="sxs-lookup"><span data-stu-id="40293-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="40293-123">Deze uitnodiging kan worden verwijderd. net zoals andere eigen aren kunnen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40293-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="40293-124">Dit proces van uitnodigingen voor komt dat gebruikers onterecht andere gebruikers toevoegen als eigen aren van hun pakketten.</span><span class="sxs-lookup"><span data-stu-id="40293-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="40293-125">Houd er rekening mee dat de meta gegevens van ' auteurs ' niet-vrije tekst zijn. alleen "eigen aren" worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="40293-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="40293-126">Eigen aren verwijderen</span><span class="sxs-lookup"><span data-stu-id="40293-126">Removing Owners</span></span>

<span data-ttu-id="40293-127">Wanneer een pakket meerdere eigen aren heeft en één moet worden verwijderd, is het proces eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="40293-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="40293-128">[Meld](https://powershellgallery.com/users/account/LogOn) u aan bij PowerShell Gallery met het account dat de huidige eigenaar is van een pakket.</span><span class="sxs-lookup"><span data-stu-id="40293-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="40293-129">Ga naar een pakket pagina met het tabblad pakketten, zoek of klik op uw gebruikers naam en vervolgens op [**mijn pakketten beheren**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="40293-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="40293-130">Wanneer u bent aangemeld als eigenaar van een pakket, kunt u aan de linkerkant op de link eigen aren beheren klikken;</span><span class="sxs-lookup"><span data-stu-id="40293-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="40293-131">Klik op de koppeling verwijderen naast de eigenaar die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40293-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="40293-132">Eigendom van het pakket overdragen</span><span class="sxs-lookup"><span data-stu-id="40293-132">Transferring Package Ownership</span></span>

<span data-ttu-id="40293-133">Soms krijgen we ondersteunings aanvragen voor het overdragen van pakket eigendom van een gebruiker naar een andere, maar u kunt dit bijna altijd zelf doen.</span><span class="sxs-lookup"><span data-stu-id="40293-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="40293-134">Het overdragen van het eigendom van de ene gebruiker naar een andere is slechts een combi natie van de bovenstaande functies.</span><span class="sxs-lookup"><span data-stu-id="40293-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="40293-135">De huidige eigenaar verzoekt de nieuwe gebruiker een mede-eigenaar te worden en de nieuwe gebruiker accepteert de uitnodiging.</span><span class="sxs-lookup"><span data-stu-id="40293-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="40293-136">De nieuwe gebruiker verwijdert de oude gebruiker uit de lijst met eigen aren.</span><span class="sxs-lookup"><span data-stu-id="40293-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="40293-137">Deze aanvraag is beschikbaar in een paar formulieren, maar het proces werkt op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="40293-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="40293-138">Het eigendom van het pakket verandert van de ene ontwikkelaar naar een andere</span><span class="sxs-lookup"><span data-stu-id="40293-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="40293-139">Het pakket is per ongeluk gepubliceerd met het verkeerde account</span><span class="sxs-lookup"><span data-stu-id="40293-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="40293-140">Zwevende pakketten</span><span class="sxs-lookup"><span data-stu-id="40293-140">Orphaned Packages</span></span>

<span data-ttu-id="40293-141">Er is een laatste scenario opgetreden, maar dit is niet vaak.</span><span class="sxs-lookup"><span data-stu-id="40293-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="40293-142">Pakketten zijn zwevend geworden en het enige pakket eigenaars account kan niet worden gebruikt om nieuwe eigen aren toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="40293-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="40293-143">Hier volgen enkele voor beelden van dit scenario:</span><span class="sxs-lookup"><span data-stu-id="40293-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="40293-144">Het account van de eigenaar is gekoppeld aan een e-mail adres dat niet meer bestaat en de gebruiker is het wacht woord verg eten</span><span class="sxs-lookup"><span data-stu-id="40293-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="40293-145">De geregistreerde eigenaar heeft het bedrijf verlaten dat het pakket produceert en kan niet worden bereikt om het eigendom van het pakket bij te werken</span><span class="sxs-lookup"><span data-stu-id="40293-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="40293-146">Als gevolg van een bug die alleen een aantal pakketten heeft beïnvloed, is het pakket eigenaar van de galerie.</span><span class="sxs-lookup"><span data-stu-id="40293-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="40293-147">De PowerShell Gallery-beheerders hebben toegang tot de koppeling eigen aren beheren voor elk pakket.</span><span class="sxs-lookup"><span data-stu-id="40293-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="40293-148">Als u de eigenaar van een pakket bent van de Rightful en de huidige eigenaar niet kan bereiken om eigendoms machtigingen te krijgen, gebruikt u de koppeling ' misbruik melden ' in de galerie om de PowerShell Gallery beheerders te bereiken.</span><span class="sxs-lookup"><span data-stu-id="40293-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="40293-149">We gaan vervolgens een proces volgen om uw eigendom van het pakket te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="40293-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="40293-150">Als we bepalen dat u een eigenaar van het pakket moet zijn, gebruiken we de koppeling eigen aren beheren voor het pakket zelf en sturen we u de uitnodiging om eigenaar te worden.</span><span class="sxs-lookup"><span data-stu-id="40293-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="40293-151">We zullen dit alleen doen nadat u hebt gecontroleerd of u een eigenaar moet zijn en het proces hiervoor afhankelijk is van omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="40293-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="40293-152">Vaak gebruiken we de project-URL van het pakket om een manier te vinden om contact op te nemen met de project eigenaar, maar we kunnen ook gebruikmaken van Twitter, E-mail of een andere manier om contact op te nemen met de project eigenaar.</span><span class="sxs-lookup"><span data-stu-id="40293-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
