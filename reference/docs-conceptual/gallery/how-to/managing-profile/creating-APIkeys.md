---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: API-sleutels beheren
ms.openlocfilehash: c428689d065c63716db6bc546434623e9375f8ba
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87777592"
---
# <a name="managing-api-keys"></a><span data-ttu-id="bd366-103">API-sleutels beheren</span><span class="sxs-lookup"><span data-stu-id="bd366-103">Managing API keys</span></span>

<span data-ttu-id="bd366-104">De PowerShell Gallery biedt ondersteuning voor het maken van meerdere API-sleutels ter ondersteuning van een reeks publicatie vereisten.</span><span class="sxs-lookup"><span data-stu-id="bd366-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="bd366-105">Een API-sleutel kan worden toegepast op een of meer pakketten, verleent specifieke bevoegdheden en heeft een verval datum.</span><span class="sxs-lookup"><span data-stu-id="bd366-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd366-106">Gebruikers die zijn gepubliceerd in de PowerShell Gallery voorafgaand aan de introductie van API-sleutels met een bereik, hebben een volledige Access API-sleutel.</span><span class="sxs-lookup"><span data-stu-id="bd366-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="bd366-107">De volledige toegangs sleutels hebben geen beveiligings verbeteringen die zijn ingebouwd in de API-sleutels met een bereik.</span><span class="sxs-lookup"><span data-stu-id="bd366-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="bd366-108">De volledige toegangs sleutels verlopen nooit en zijn van toepassing op alle items die eigendom zijn van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bd366-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="bd366-109">Als u deze sleutel verwijdert, kan deze niet opnieuw worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bd366-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="bd366-110">In de volgende afbeelding ziet u de beschik bare opties bij het maken van een scoped API-sleutel.</span><span class="sxs-lookup"><span data-stu-id="bd366-110">The following image shows the options available when creating a scoped API key.</span></span>

![API-sleutels maken](media/creating-APIkeys/PSGallery_KeyScoped.png)

<span data-ttu-id="bd366-112">In dit voor beeld hebben we een API-sleutel met de naam **AzureRMDataFactory**gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bd366-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="bd366-113">Deze sleutel waarde kan worden gebruikt om pakketten te pushen met namen die beginnen met ' AzureRM. DataFactory ' en die 365 dagen geldig zijn.</span><span class="sxs-lookup"><span data-stu-id="bd366-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="bd366-114">Dit is een typisch scenario wanneer verschillende teams binnen dezelfde organisatie op verschillende pakketten werken.</span><span class="sxs-lookup"><span data-stu-id="bd366-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="bd366-115">De leden van het team beschikken over een sleutel waarmee ze bevoegdheden worden verleend voor het specifieke pakket waaraan ze werken.</span><span class="sxs-lookup"><span data-stu-id="bd366-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="bd366-116">De verloop waarde voor komt het gebruik van verouderde of verg eten sleutels.</span><span class="sxs-lookup"><span data-stu-id="bd366-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="bd366-117">Globs-patronen gebruiken</span><span class="sxs-lookup"><span data-stu-id="bd366-117">Using glob patterns</span></span>

<span data-ttu-id="bd366-118">Als u op meerdere pakketten werkt, kunt u globbing-patronen gebruiken om meerdere pakketten als groep te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="bd366-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="bd366-119">API-sleutel machtigingen zijn van toepassing op alle nieuwe pakketten die overeenkomen met het Globs-patroon.</span><span class="sxs-lookup"><span data-stu-id="bd366-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="bd366-120">In het vorige voor beeld wordt bijvoorbeeld de **Globs-patroon** waarde ' AzureRM. DataFactory \* ' gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd366-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="bd366-121">U kunt een pakket met de naam ' AzureRm. DataFactoryV2. NetCore ' pushen met behulp van deze sleutel, aangezien het pakket overeenkomt met het Globs-patroon.</span><span class="sxs-lookup"><span data-stu-id="bd366-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="bd366-122">De API-sleutels veilig maken</span><span class="sxs-lookup"><span data-stu-id="bd366-122">Create API keys securely</span></span>

<span data-ttu-id="bd366-123">Ter beveiliging wordt een nieuwe sleutel waarde nooit op het scherm weer gegeven en is deze alleen beschikbaar met de Kopieer knop, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bd366-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Nieuwe API-sleutel waarde verkrijgen](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="bd366-125">U kunt de waarde van de API-sleutel alleen direct na het maken of vernieuwen kopiëren.</span><span class="sxs-lookup"><span data-stu-id="bd366-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="bd366-126">Deze wordt niet weer gegeven en is niet meer toegankelijk nadat de pagina is vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="bd366-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="bd366-127">Als u de sleutel waarde kwijtraakt, moet u Regenerate gebruiken en de sleutel kopiëren nadat deze opnieuw is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bd366-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="bd366-128">Sleutel machtigingen en verloop tijd</span><span class="sxs-lookup"><span data-stu-id="bd366-128">Key permissions and expiration</span></span>

<span data-ttu-id="bd366-129">Scoped API-sleutels kunnen een van de volgende machtigingen toewijzen:</span><span class="sxs-lookup"><span data-stu-id="bd366-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="bd366-130">Nieuwe pakketten pushen</span><span class="sxs-lookup"><span data-stu-id="bd366-130">Push new packages</span></span>
- <span data-ttu-id="bd366-131">Nieuwe of bijgewerkte pakketten pushen</span><span class="sxs-lookup"><span data-stu-id="bd366-131">Push new or update packages</span></span>
- <span data-ttu-id="bd366-132">Pakketten in lijst opnemen</span><span class="sxs-lookup"><span data-stu-id="bd366-132">Unlist packages</span></span>

<span data-ttu-id="bd366-133">Elke nieuwe sleutel heeft een verval datum.</span><span class="sxs-lookup"><span data-stu-id="bd366-133">Every new key has an expiration.</span></span> <span data-ttu-id="bd366-134">De verloop waarde wordt gemeten in dagen.</span><span class="sxs-lookup"><span data-stu-id="bd366-134">The expiration value is measured in days.</span></span> <span data-ttu-id="bd366-135">De mogelijke verval waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="bd366-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="bd366-136">1 dag</span><span class="sxs-lookup"><span data-stu-id="bd366-136">1 day</span></span>
- <span data-ttu-id="bd366-137">90 dagen</span><span class="sxs-lookup"><span data-stu-id="bd366-137">90 days</span></span>
- <span data-ttu-id="bd366-138">180 dagen</span><span class="sxs-lookup"><span data-stu-id="bd366-138">180 days</span></span>
- <span data-ttu-id="bd366-139">270 dagen</span><span class="sxs-lookup"><span data-stu-id="bd366-139">270 days</span></span>
- <span data-ttu-id="bd366-140">365 dagen (standaard)</span><span class="sxs-lookup"><span data-stu-id="bd366-140">365 days (default)</span></span>

<span data-ttu-id="bd366-141">Deze instellingen kunnen niet worden gewijzigd nadat de sleutel is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bd366-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="bd366-142">U kunt geen nieuwe sleutel maken die nooit verloopt.</span><span class="sxs-lookup"><span data-stu-id="bd366-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="bd366-143">Bestaande API-sleutels bewerken en verwijderen</span><span class="sxs-lookup"><span data-stu-id="bd366-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="bd366-144">U kunt sommige instellingen van een bestaande sleutel wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bd366-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="bd366-145">Zoals eerder is vermeld, kunt u het beveiligings bereik voor een bestaande API-sleutel niet wijzigen of de verval datum wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bd366-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="bd366-146">De opties die u kunt wijzigen, worden weer gegeven in de volgende scherm afbeelding:</span><span class="sxs-lookup"><span data-stu-id="bd366-146">The changeable options are shown in the following screenshot:</span></span>

![Uw API-sleutel waarde bewerken](media/creating-APIkeys/PSGallery_EditAPIKey.png)

<span data-ttu-id="bd366-148">Als u de pakketten wilt wijzigen die worden beheerd door een sleutel, kunt u afzonderlijke pakketten kiezen in de lijst of het Globs-patroon wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bd366-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="bd366-149">Als u op **opnieuw genereren** klikt, wordt een nieuwe sleutel waarde gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bd366-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="bd366-150">Net als bij de eerste keer dat u de sleutel hebt gemaakt, moet u de sleutel waarde direct na het bijwerken **kopiëren** .</span><span class="sxs-lookup"><span data-stu-id="bd366-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="bd366-151">De **Kopieer** optie is niet beschikbaar wanneer u deze pagina verlaat.</span><span class="sxs-lookup"><span data-stu-id="bd366-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="bd366-152">Als u op **verwijderen** klikt, wordt een bevestigings bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bd366-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="bd366-153">Wanneer een sleutel eenmaal is verwijderd, kan deze niet meer worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd366-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="bd366-154">Verval datum van de sleutel</span><span class="sxs-lookup"><span data-stu-id="bd366-154">Key expiration</span></span>

<span data-ttu-id="bd366-155">Tien dagen voor het verlopen van de PowerShell Gallery wordt een waarschuwing verzonden met de account houder van de API-sleutel.</span><span class="sxs-lookup"><span data-stu-id="bd366-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="bd366-156">Na verloop van tijd is de sleutel onbruikbaar.</span><span class="sxs-lookup"><span data-stu-id="bd366-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="bd366-157">Boven aan de pagina API-sleutel beheer wordt een waarschuwings bericht weer gegeven met de sleutels die niet meer geldig zijn.</span><span class="sxs-lookup"><span data-stu-id="bd366-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="bd366-158">U kunt een nieuwe sleutel waarde genereren.</span><span class="sxs-lookup"><span data-stu-id="bd366-158">You can generate a new key value.</span></span>
