---
ms.date: 06/12/2017
title: Lijst met pakketten opzeggen
description: De PowerShell Gallery biedt geen ondersteuning voor gebruikers die hun pakketten permanent verwijderen. Op deze manier kunnen anderen afhankelijkheden maken op uw pakketten zonder dat u in de toekomst over mogelijke onderbrekingen hoeft te zorgen.
ms.openlocfilehash: 738167011f64b5174df3504c8e1d06146f4c7db5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662421"
---
# <a name="unlisting-packages"></a><span data-ttu-id="7867d-104">Pakketten uit de catalogus verwijderen</span><span class="sxs-lookup"><span data-stu-id="7867d-104">Unlisting Packages</span></span>

<span data-ttu-id="7867d-105">**Waarom wordt het verwijderen van een pakket uit PowerShell Gallery niet weer gegeven als een optie?**</span><span class="sxs-lookup"><span data-stu-id="7867d-105">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="7867d-106">De PowerShell Gallery biedt geen ondersteuning voor gebruikers die hun pakketten permanent verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7867d-106">The PowerShell Gallery does not support users permanently deleting their packages.</span></span> <span data-ttu-id="7867d-107">Op deze manier kunnen anderen afhankelijkheden maken op uw pakketten zonder dat u in de toekomst over mogelijke onderbrekingen hoeft te zorgen.</span><span class="sxs-lookup"><span data-stu-id="7867d-107">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="7867d-108">Als de insluitings module bijvoorbeeld afhankelijk is van de Azure-module en de Azure-module uit de galerie wordt verwijderd, kunnen gebruikers de module pest niet meer gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7867d-108">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="7867d-109">In plaats van een pakket te verwijderen, kunt u de weer gave ervan opheffen.</span><span class="sxs-lookup"><span data-stu-id="7867d-109">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="7867d-110">**Wat houdt het weer geven van een pakket op PowerShell Gallery?**</span><span class="sxs-lookup"><span data-stu-id="7867d-110">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="7867d-111">Als u de weer geven van een pakket, zoals een module of script in de PowerShell Gallery, verwijdert u dit op het tabblad pakketten. Daarnaast kunnen niet-vermelde pakketten niet worden gedetecteerd met behulp van de zoek balk.</span><span class="sxs-lookup"><span data-stu-id="7867d-111">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span> <span data-ttu-id="7867d-112">De enige manier om een niet-vermeld pakket te downloaden, is door de exacte naam en versie van het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="7867d-112">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span> <span data-ttu-id="7867d-113">Als gevolg hiervan worden de onweer gave van een pakket geen andere modules of scripts die hiervan afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="7867d-113">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="7867d-114">Ga naar de pagina pakket Details en selecteer module verwijderen om het pakket weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7867d-114">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="7867d-115">Schakel het selectie vakje ' weer gegeven ' uit en selecteer Opslaan.</span><span class="sxs-lookup"><span data-stu-id="7867d-115">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="7867d-116">**Hoe kan ik een pakket verwijderen?**</span><span class="sxs-lookup"><span data-stu-id="7867d-116">**How can I remove a package?**</span></span>

<span data-ttu-id="7867d-117">Als u een scenario ondervindt waarbij het verwijderen van pakketten nood zakelijk is, neemt u contact op met de PowerShell Gallery-beheerders.</span><span class="sxs-lookup"><span data-stu-id="7867d-117">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span> <span data-ttu-id="7867d-118">Geldige verwijderings scenario's zijn:</span><span class="sxs-lookup"><span data-stu-id="7867d-118">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="7867d-119">Problemen met inbreuk op het auteurs recht.</span><span class="sxs-lookup"><span data-stu-id="7867d-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="7867d-120">Het pakket bevat mogelijk schadelijke inhoud.</span><span class="sxs-lookup"><span data-stu-id="7867d-120">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="7867d-121">Het pakket bevat gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="7867d-121">Package contains sensitive data.</span></span>

<span data-ttu-id="7867d-122">Als u een aanvraag voor het verwijderen van een pakket wilt indienen bij de PowerShell Gallery beheerders, gaat u naar de detail pagina van uw pakket en selecteert u contact opnemen met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="7867d-122">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
