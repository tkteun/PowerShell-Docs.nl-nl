---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakketten uit catalogus verwijderen
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004049"
---
# <a name="unlisting-packages"></a><span data-ttu-id="04e8f-103">Unlisting pakketten</span><span class="sxs-lookup"><span data-stu-id="04e8f-103">Unlisting Packages</span></span>

<span data-ttu-id="04e8f-104">**Waarom is een pakket verwijderen vanuit PowerShell Gallery is niet beschikbaar zijn gemaakt als een optie?**</span><span class="sxs-lookup"><span data-stu-id="04e8f-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="04e8f-105">De PowerShell Gallery biedt geen ondersteuning voor gebruikers permanent verwijderen van hun pakketten.</span><span class="sxs-lookup"><span data-stu-id="04e8f-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="04e8f-106">Hierdoor kunnen anderen uw pakketten afhankelijkheden uitvoeren zonder dat u eventuele onderbrekingen in de toekomst.</span><span class="sxs-lookup"><span data-stu-id="04e8f-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="04e8f-107">Als de module Pester is afhankelijk van de Azure-module en de Azure-module wordt verwijderd uit de galerie, en vervolgens de gebruiker kan niet meer gebruikt bijvoorbeeld de Pester-module.</span><span class="sxs-lookup"><span data-stu-id="04e8f-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="04e8f-108">In plaats van een pakket is verwijderd, maar kunt u unlist deze in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="04e8f-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="04e8f-109">**Wat doet uit catalogus verwijderen een pakket op PowerShell Gallery doen?**</span><span class="sxs-lookup"><span data-stu-id="04e8f-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="04e8f-110">Een pakket, zoals de module of script op PowerShell Gallery uit catalogus verwijderen, wordt deze verwijderd uit het tabblad pakketten. Niet-vermelde pakketten wordt bovendien niet worden gedetecteerd via de zoekbalk.</span><span class="sxs-lookup"><span data-stu-id="04e8f-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="04e8f-111">De enige manier om een niet-vermelde pakket te downloaden is om op te geven van de exacte naam en versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="04e8f-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="04e8f-112">Als gevolg hiervan wordt uit catalogus verwijderen van een pakket niet verbroken andere modules of scripts die afhankelijk van deze zijn.</span><span class="sxs-lookup"><span data-stu-id="04e8f-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="04e8f-113">Als u wilt uw pakket unlist, gaat u naar de pagina met details van pakket en selecteert u 'Module verwijderen'.</span><span class="sxs-lookup"><span data-stu-id="04e8f-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="04e8f-114">Schakel het selectievakje 'Hier' uit en klik op opslaan.</span><span class="sxs-lookup"><span data-stu-id="04e8f-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="04e8f-115">**Hoe kan ik een pakket verwijderen?**</span><span class="sxs-lookup"><span data-stu-id="04e8f-115">**How can I remove an package?**</span></span>

<span data-ttu-id="04e8f-116">Als u een scenario waarbij pakket verwijderen die nodig zijn, moet u contact op met de PowerShell Gallery-beheerders.</span><span class="sxs-lookup"><span data-stu-id="04e8f-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="04e8f-117">Geldige verwijdering scenario's:</span><span class="sxs-lookup"><span data-stu-id="04e8f-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="04e8f-118">Problemen met auteursrecht.</span><span class="sxs-lookup"><span data-stu-id="04e8f-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="04e8f-119">Het pakket bevat mogelijk schadelijke inhoud.</span><span class="sxs-lookup"><span data-stu-id="04e8f-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="04e8f-120">Pakket bevat gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="04e8f-120">Package contains sensitive data.</span></span>

<span data-ttu-id="04e8f-121">Als u wilt een verwijderen pakket aanvragen naar de PowerShell Gallery-beheerders, gaat u naar de detailpagina van het pakket en selecteert u contact opnemen met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="04e8f-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
