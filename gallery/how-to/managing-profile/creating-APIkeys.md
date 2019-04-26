---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: API-sleutels beheren
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084339"
---
# <a name="managing-api-keys"></a><span data-ttu-id="84d59-103">API-sleutels beheren</span><span class="sxs-lookup"><span data-stu-id="84d59-103">Managing API keys</span></span>

<span data-ttu-id="84d59-104">De PowerShell Gallery biedt ondersteuning voor het maken van meerdere API-sleutels ter ondersteuning van een bereik van de publicatie van vereisten.</span><span class="sxs-lookup"><span data-stu-id="84d59-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="84d59-105">Een API-sleutel kan worden toegepast op een of meer pakketten, verleent u specifieke bevoegdheden en heeft een vervaldatum.</span><span class="sxs-lookup"><span data-stu-id="84d59-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84d59-106">Gebruikers die gepubliceerd naar de PowerShell Gallery vóór de introductie van binnen het bereik API-sleutels heeft een 'volledige toegang tot de API key'.</span><span class="sxs-lookup"><span data-stu-id="84d59-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="84d59-107">De volledige toegangssleutel beschikt niet over de verbeteringen in de beveiliging die is ingebouwd in binnen het bereik API-sleutels.</span><span class="sxs-lookup"><span data-stu-id="84d59-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="84d59-108">De volledige toegang tot de sleutels nooit verloopt en toepassen op Alles eigendom zijn van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="84d59-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="84d59-109">Als u deze sleutel verwijdert, kan niet opnieuw gemaakt.</span><span class="sxs-lookup"><span data-stu-id="84d59-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="84d59-110">De volgende afbeelding toont de beschikbare opties bij het maken van een bereik API-sleutel.</span><span class="sxs-lookup"><span data-stu-id="84d59-110">The following image shows the options available when creating a scoped API key.</span></span>

![Het maken van API-sleutels](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="84d59-112">In dit voorbeeld hebben we een API-sleutel met de naam gemaakt **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="84d59-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="84d59-113">De waarde van deze sleutel kan worden gebruikt om pakketten met namen die beginnen met 'AzureRM.DataFactory' en is geldig tot 365 dagen.</span><span class="sxs-lookup"><span data-stu-id="84d59-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="84d59-114">Dit is een typisch scenario bij verschillende teams binnen dezelfde organisatie aan verschillende pakketten werken.</span><span class="sxs-lookup"><span data-stu-id="84d59-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="84d59-115">De leden van het team hebben een sleutel die deze machtigingen voor het specifieke pakket dat ze werken verleent op.</span><span class="sxs-lookup"><span data-stu-id="84d59-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="84d59-116">De vervaltijd wordt voorkomen dat het gebruik van verouderde of vergeten sleutels.</span><span class="sxs-lookup"><span data-stu-id="84d59-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="84d59-117">Met behulp van glob patronen</span><span class="sxs-lookup"><span data-stu-id="84d59-117">Using glob patterns</span></span>

<span data-ttu-id="84d59-118">Als u op meerdere pakketten werkt, kunt u bij globbing patronen zodat deze overeenkomen met meerdere pakketten als een groep.</span><span class="sxs-lookup"><span data-stu-id="84d59-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="84d59-119">API-sleutel machtigingen toepassen op alle nieuwe pakketten die overeenkomt met het patroon glob.</span><span class="sxs-lookup"><span data-stu-id="84d59-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="84d59-120">Het vorige voorbeeld gebruikt bijvoorbeeld een **Glob patroon** waarde van 'AzureRM.DataFactory\*'.</span><span class="sxs-lookup"><span data-stu-id="84d59-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="84d59-121">U kunt een pakket met de naam met behulp van deze sleutel omdat het pakket overeenkomt met het patroon glob AzureRm.DataFactoryV2.Netcore pushen.</span><span class="sxs-lookup"><span data-stu-id="84d59-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="84d59-122">API-sleutels veilig maken</span><span class="sxs-lookup"><span data-stu-id="84d59-122">Create API keys securely</span></span>

<span data-ttu-id="84d59-123">Voor beveiliging, de waarde van een nieuwe sleutel nooit op het scherm wordt weergegeven en is alleen beschikbaar met de knop kopiëren, zoals hieronder wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="84d59-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Het ophalen van de nieuwe API-sleutelwaarde](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="84d59-125">U kunt alleen de waarde van de API-sleutel kopiëren onmiddellijk na het maken of vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="84d59-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="84d59-126">Deze worden niet weergegeven en wordt niet meer toegankelijk opnieuw nadat de pagina wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="84d59-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="84d59-127">Als u de waarde van de sleutel verliest, moet u gebruik van de sleutel opnieuw genereren en kopieer de sleutel nadat deze is opnieuw gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="84d59-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="84d59-128">Machtigingen en de vervaldatum</span><span class="sxs-lookup"><span data-stu-id="84d59-128">Key permissions and expiration</span></span>

<span data-ttu-id="84d59-129">Scoped API-sleutels kunnen een van de volgende machtigingen toewijzen:</span><span class="sxs-lookup"><span data-stu-id="84d59-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="84d59-130">Nieuwe push-pakketten</span><span class="sxs-lookup"><span data-stu-id="84d59-130">Push new packages</span></span>
- <span data-ttu-id="84d59-131">Nieuwe push of pakketten bijwerken</span><span class="sxs-lookup"><span data-stu-id="84d59-131">Push new or update packages</span></span>
- <span data-ttu-id="84d59-132">Unlist pakketten</span><span class="sxs-lookup"><span data-stu-id="84d59-132">Unlist packages</span></span>

<span data-ttu-id="84d59-133">Elke nieuwe sleutel heeft een vervaldatum.</span><span class="sxs-lookup"><span data-stu-id="84d59-133">Every new key has an expiration.</span></span> <span data-ttu-id="84d59-134">De vervaltijd wordt gemeten in dagen.</span><span class="sxs-lookup"><span data-stu-id="84d59-134">The expiration value is measured in days.</span></span> <span data-ttu-id="84d59-135">De vervaldatum voor de mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="84d59-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="84d59-136">1 dag</span><span class="sxs-lookup"><span data-stu-id="84d59-136">1 day</span></span>
- <span data-ttu-id="84d59-137">90 dagen</span><span class="sxs-lookup"><span data-stu-id="84d59-137">90 days</span></span>
- <span data-ttu-id="84d59-138">180 dagen</span><span class="sxs-lookup"><span data-stu-id="84d59-138">180 days</span></span>
- <span data-ttu-id="84d59-139">270 dagen</span><span class="sxs-lookup"><span data-stu-id="84d59-139">270 days</span></span>
- <span data-ttu-id="84d59-140">365 dagen (standaard)</span><span class="sxs-lookup"><span data-stu-id="84d59-140">365 days (default)</span></span>

<span data-ttu-id="84d59-141">Deze instellingen kunnen niet worden gewijzigd nadat de sleutel is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="84d59-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="84d59-142">U kunt een nieuwe sleutel nooit verloopt kan niet maken.</span><span class="sxs-lookup"><span data-stu-id="84d59-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="84d59-143">Bewerken en verwijderen van bestaande API-sleutels</span><span class="sxs-lookup"><span data-stu-id="84d59-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="84d59-144">U kunt bepaalde instellingen van een bestaande sleutel wijzigen.</span><span class="sxs-lookup"><span data-stu-id="84d59-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="84d59-145">Zoals eerder vermeld, kan u wijzigen van het beveiligingsbereik voor een bestaande API-sleutel of wijzigen van de vervaldatum.</span><span class="sxs-lookup"><span data-stu-id="84d59-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="84d59-146">De instelbare opties worden weergegeven in de volgende schermafbeelding:</span><span class="sxs-lookup"><span data-stu-id="84d59-146">The changeable options are shown in the following screenshot:</span></span>

![Het ophalen van de nieuwe API-sleutelwaarde](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="84d59-148">Als u wilt wijzigen van de pakketten die wordt beheerd door een sleutel, kunt u afzonderlijke pakketten in de lijst kiezen of het patroon glob wijzigen.</span><span class="sxs-lookup"><span data-stu-id="84d59-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="84d59-149">Te klikken op **opnieuw genereren** wordt de waarde van een nieuwe sleutel gemaakt.</span><span class="sxs-lookup"><span data-stu-id="84d59-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="84d59-150">Net zoals wanneer u de sleutel in eerste instantie hebt gemaakt, u moet **kopie** de waarde van de sleutel onmiddellijk na het bijwerken van het.</span><span class="sxs-lookup"><span data-stu-id="84d59-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="84d59-151">De **kopie** optie is niet beschikbaar wanneer u deze pagina verlaat.</span><span class="sxs-lookup"><span data-stu-id="84d59-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="84d59-152">Te klikken op **verwijderen** verschijnt een bevestigingsbericht.</span><span class="sxs-lookup"><span data-stu-id="84d59-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="84d59-153">Zodra een sleutel is verwijderd, wordt het onbruikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="84d59-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="84d59-154">Vervaldatum van de sleutel</span><span class="sxs-lookup"><span data-stu-id="84d59-154">Key expiration</span></span>

<span data-ttu-id="84d59-155">Tien dagen vóór de vervaldatum, verzendt de PowerShell Gallery een waarschuwing e-mailbericht de accounteigenaar van de API-sleutel.</span><span class="sxs-lookup"><span data-stu-id="84d59-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="84d59-156">De sleutel is na de verloopdatum onbruikbaar.</span><span class="sxs-lookup"><span data-stu-id="84d59-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="84d59-157">Een waarschuwingsbericht wordt weergegeven aan de bovenkant van de API-Sleutelbeheer-pagina met welke sleutels zijn niet langer geldig.</span><span class="sxs-lookup"><span data-stu-id="84d59-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="84d59-158">U kunt de waarde van een nieuwe sleutel genereren.</span><span class="sxs-lookup"><span data-stu-id="84d59-158">You can generate a new key value.</span></span>
