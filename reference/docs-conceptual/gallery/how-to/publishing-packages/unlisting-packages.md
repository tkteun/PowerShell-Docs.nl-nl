---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Lijst met pakketten opzeggen
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329027"
---
# <a name="unlisting-packages"></a><span data-ttu-id="6b074-103">Pakketten uit de catalogus verwijderen</span><span class="sxs-lookup"><span data-stu-id="6b074-103">Unlisting Packages</span></span>

<span data-ttu-id="6b074-104">**Waarom wordt het verwijderen van een pakket uit PowerShell Gallery niet weer gegeven als een optie?**</span><span class="sxs-lookup"><span data-stu-id="6b074-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="6b074-105">De PowerShell Gallery biedt geen ondersteuning voor gebruikers die hun pakketten permanent verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6b074-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="6b074-106">Op deze manier kunnen anderen afhankelijkheden maken op uw pakketten zonder dat u in de toekomst over mogelijke onderbrekingen hoeft te zorgen.</span><span class="sxs-lookup"><span data-stu-id="6b074-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="6b074-107">Als de insluitings module bijvoorbeeld afhankelijk is van de Azure-module en de Azure-module uit de galerie is verwijderd, kan de gebruiker niet langer gebruikmaken van de module Pest.</span><span class="sxs-lookup"><span data-stu-id="6b074-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="6b074-108">In plaats van een pakket te verwijderen, kunt u de weer gave echter opheffen.</span><span class="sxs-lookup"><span data-stu-id="6b074-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="6b074-109">**Wat houdt het weer geven van een pakket op PowerShell Gallery?**</span><span class="sxs-lookup"><span data-stu-id="6b074-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="6b074-110">Het opheffen van de weer geven van een pakket, zoals module of script op PowerShell Gallery, wordt verwijderd uit het tabblad pakketten. Daarnaast kunnen niet-vermelde pakketten niet worden gedetecteerd met behulp van de zoek balk.</span><span class="sxs-lookup"><span data-stu-id="6b074-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="6b074-111">De enige manier om een niet-vermeld pakket te downloaden, is door de exacte naam en versie van het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="6b074-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="6b074-112">Als gevolg hiervan worden de onvermelding van een pakket geen andere modules of scripts die hiervan afhankelijk zijn, verbroken.</span><span class="sxs-lookup"><span data-stu-id="6b074-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="6b074-113">Ga naar de pagina pakket Details en selecteer module verwijderen om het pakket weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6b074-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="6b074-114">Schakel het selectie vakje ' weer gegeven ' uit en klik op opslaan.</span><span class="sxs-lookup"><span data-stu-id="6b074-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="6b074-115">**Hoe kan ik een pakket verwijderen?**</span><span class="sxs-lookup"><span data-stu-id="6b074-115">**How can I remove an package?**</span></span>

<span data-ttu-id="6b074-116">Als u een scenario ondervindt waarbij het verwijderen van pakketten nood zakelijk is, neemt u contact op met de PowerShell Gallery-beheerders.</span><span class="sxs-lookup"><span data-stu-id="6b074-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="6b074-117">Geldige verwijderings scenario's zijn:</span><span class="sxs-lookup"><span data-stu-id="6b074-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="6b074-118">Problemen met inbreuk op het auteurs recht.</span><span class="sxs-lookup"><span data-stu-id="6b074-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="6b074-119">Het pakket bevat mogelijk schadelijke inhoud.</span><span class="sxs-lookup"><span data-stu-id="6b074-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="6b074-120">Het pakket bevat gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="6b074-120">Package contains sensitive data.</span></span>

<span data-ttu-id="6b074-121">Als u een aanvraag voor het verwijderen van een pakket wilt indienen bij de PowerShell Gallery beheerders, gaat u naar de detail pagina van uw pakket en selecteert u contact opnemen met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="6b074-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
