---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a><span data-ttu-id="8844b-103">Unlisting items</span><span class="sxs-lookup"><span data-stu-id="8844b-103">Unlisting items</span></span>

<span data-ttu-id="8844b-104">**Waarom verwijdert een item van PowerShell Gallery niet wordt weergegeven als een optie?**</span><span class="sxs-lookup"><span data-stu-id="8844b-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="8844b-105">De PowerShell-galerie biedt geen ondersteuning voor gebruikers die hun items permanent te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8844b-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span> <span data-ttu-id="8844b-106">Hierdoor kunnen anderen uw items afhankelijkheden uitvoeren zonder dat u in de toekomst mogelijk einden.</span><span class="sxs-lookup"><span data-stu-id="8844b-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span> <span data-ttu-id="8844b-107">Als de module Pester is afhankelijk van de Azure-module en de Azure-module is verwijderd uit de galerie en vervolgens de gebruiker kan niet meer gebruikt bijvoorbeeld de Pester-module.</span><span class="sxs-lookup"><span data-stu-id="8844b-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="8844b-108">In plaats van het verwijderen van een item, maar kunt u unlist deze in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="8844b-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="8844b-109">**Wat wordt er een item in PowerShell Gallery doen unlisting?**</span><span class="sxs-lookup"><span data-stu-id="8844b-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="8844b-110">Een item bijvoorbeeld module of een script op basis van PowerShell Gallery unlisting wordt verwijderd uit het tabblad Items.</span><span class="sxs-lookup"><span data-stu-id="8844b-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab.</span></span>
<span data-ttu-id="8844b-111">Niet-vermelde items wordt bovendien niet worden gedetecteerd met behulp van de zoekbalk.</span><span class="sxs-lookup"><span data-stu-id="8844b-111">In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="8844b-112">De enige manier om het downloaden van een niet-vermelde item is de exacte naam en versie van het item opgeven.</span><span class="sxs-lookup"><span data-stu-id="8844b-112">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="8844b-113">Als gevolg hiervan wordt unlisting van een item niet verbroken andere modules of scripts die afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="8844b-113">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="8844b-114">Uw item unlist, gaat u naar de pagina met objecten en selecteren Item verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8844b-114">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="8844b-115">Schakel het selectievakje 'Hier' uit en klik op opslaan.</span><span class="sxs-lookup"><span data-stu-id="8844b-115">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="8844b-116">**Hoe kan ik een item verwijderen?**</span><span class="sxs-lookup"><span data-stu-id="8844b-116">**How can I remove an item?**</span></span>

<span data-ttu-id="8844b-117">Als u een scenario waarbij item verwijdering nodig ondervindt, moet u contact op met de PowerShell-galerie-beheerders.</span><span class="sxs-lookup"><span data-stu-id="8844b-117">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="8844b-118">Verwijderen van een ongeldig scenario's:</span><span class="sxs-lookup"><span data-stu-id="8844b-118">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="8844b-119">Problemen met het auteursrecht.</span><span class="sxs-lookup"><span data-stu-id="8844b-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="8844b-120">Item bevat mogelijk schadelijke inhoud.</span><span class="sxs-lookup"><span data-stu-id="8844b-120">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="8844b-121">Item bevat gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="8844b-121">Item contains sensitive data.</span></span>

<span data-ttu-id="8844b-122">Dien een verwijderd Item aanvraag naar de beheerders van PowerShell-galerie, gaat u naar de detailpagina voor het object en neem contact op met ondersteuning selecteren.</span><span class="sxs-lookup"><span data-stu-id="8844b-122">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>  


