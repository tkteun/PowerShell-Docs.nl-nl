---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: af48f2ca889dcc101d466e40f2ecbe0cdf62c066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="11970-103">Items uit catalogus verwijderen</span><span class="sxs-lookup"><span data-stu-id="11970-103">Unlisting items</span></span>

<span data-ttu-id="11970-104">**Waarom verwijdert een item van PowerShell Gallery niet wordt weergegeven als een optie?**</span><span class="sxs-lookup"><span data-stu-id="11970-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="11970-105">De PowerShell-galerie biedt geen ondersteuning voor gebruikers die hun items permanent te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="11970-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="11970-106">Hierdoor kunnen anderen uw items afhankelijkheden uitvoeren zonder dat u in de toekomst mogelijk einden.</span><span class="sxs-lookup"><span data-stu-id="11970-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="11970-107">Als de module Pester is afhankelijk van de Azure-module en de Azure-module is verwijderd uit de galerie en vervolgens de gebruiker kan niet meer gebruikt bijvoorbeeld de Pester-module.</span><span class="sxs-lookup"><span data-stu-id="11970-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="11970-108">In plaats van het verwijderen van een item, maar kunt u unlist deze in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="11970-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="11970-109">**Wat wordt er een item in PowerShell Gallery doen unlisting?**</span><span class="sxs-lookup"><span data-stu-id="11970-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="11970-110">Een item bijvoorbeeld module of een script op basis van PowerShell Gallery unlisting wordt verwijderd uit het tabblad Items. Niet-vermelde items wordt bovendien niet worden gedetecteerd met behulp van de zoekbalk.</span><span class="sxs-lookup"><span data-stu-id="11970-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="11970-111">De enige manier om het downloaden van een niet-vermelde item is de exacte naam en versie van het item opgeven.</span><span class="sxs-lookup"><span data-stu-id="11970-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="11970-112">Als gevolg hiervan wordt unlisting van een item niet verbroken andere modules of scripts die afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="11970-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="11970-113">Uw item unlist, gaat u naar de pagina met objecten en selecteren Item verwijderen.</span><span class="sxs-lookup"><span data-stu-id="11970-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="11970-114">Schakel het selectievakje 'Hier' uit en klik op opslaan.</span><span class="sxs-lookup"><span data-stu-id="11970-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="11970-115">**Hoe kan ik een item verwijderen?**</span><span class="sxs-lookup"><span data-stu-id="11970-115">**How can I remove an item?**</span></span>

<span data-ttu-id="11970-116">Als u een scenario waarbij item verwijdering nodig ondervindt, moet u contact op met de PowerShell-galerie-beheerders.</span><span class="sxs-lookup"><span data-stu-id="11970-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="11970-117">Verwijderen van een ongeldig scenario's:</span><span class="sxs-lookup"><span data-stu-id="11970-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="11970-118">Problemen met het auteursrecht.</span><span class="sxs-lookup"><span data-stu-id="11970-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="11970-119">Item bevat mogelijk schadelijke inhoud.</span><span class="sxs-lookup"><span data-stu-id="11970-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="11970-120">Item bevat gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="11970-120">Item contains sensitive data.</span></span>

<span data-ttu-id="11970-121">Dien een verwijderd Item aanvraag naar de beheerders van PowerShell-galerie, gaat u naar de detailpagina voor het object en neem contact op met ondersteuning selecteren.</span><span class="sxs-lookup"><span data-stu-id="11970-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>