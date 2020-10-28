---
ms.date: 09/13/2016
ms.topic: reference
title: De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets
description: De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: aeeb0cdd1d6d17b88067928ff952dc57a9441917
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659054"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="8458d-103">De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="8458d-103">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="8458d-104">In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de secties **naam** en samen **vatting** van de Help van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8458d-104">This section describes how to add content that is displayed in the **NAME** and **SYNOPSIS** sections of the cmdlet help.</span></span> <span data-ttu-id="8458d-105">In het Help-bestand wordt deze inhoud toegevoegd aan het opdracht knooppunt voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8458d-105">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8458d-106">Als u een volledig overzicht van een Help-bestand wilt weer geven, opent u een van de `dll-Help.xml` bestanden die zich in de installatie directory van Power shell bevinden.</span><span class="sxs-lookup"><span data-stu-id="8458d-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="8458d-107">Het `Microsoft.PowerShell.Commands.Management.dll-Help.xml` bestand bevat bijvoorbeeld inhoud voor verschillende Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8458d-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="8458d-108">De naam van de cmdlet en een samen vatting toevoegen</span><span class="sxs-lookup"><span data-stu-id="8458d-108">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="8458d-109">De Help van de cmdlet kan twee beschrijvingen voor de cmdlet weer geven.</span><span class="sxs-lookup"><span data-stu-id="8458d-109">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="8458d-110">De eerste beschrijving is een korte beschrijving die de samen vatting wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="8458d-110">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="8458d-111">De tweede beschrijving is een gedetailleerde beschrijving die wordt beschreven in [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="8458d-111">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>
  <span data-ttu-id="8458d-112">Beide beschrijvingen moeten worden geschreven als één alinea.</span><span class="sxs-lookup"><span data-stu-id="8458d-112">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="8458d-113">Herhaal de naam van de cmdlet niet in de samen vatting.</span><span class="sxs-lookup"><span data-stu-id="8458d-113">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="8458d-114">De gebruiker te informeren dat de `Get-Server` cmdlet een server krijgt, is kort, maar niet informatie.</span><span class="sxs-lookup"><span data-stu-id="8458d-114">Informing the user that the `Get-Server` cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="8458d-115">Gebruik in plaats daarvan synoniemen en Voeg details toe aan de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="8458d-115">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="8458d-116">Voor beeld: "haalt een object op dat een lokale of externe computer vertegenwoordigt."</span><span class="sxs-lookup"><span data-stu-id="8458d-116">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="8458d-117">Gebruik eenvoudige werk woorden zoals ' Get ', ' maken ' en ' wijzigen ' in de samen vatting.</span><span class="sxs-lookup"><span data-stu-id="8458d-117">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="8458d-118">Vermijd het gebruik van ' set ' omdat het Vague is en decoratieve woorden zoals ' Modify '.</span><span class="sxs-lookup"><span data-stu-id="8458d-118">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="8458d-119">Voor beeld: "haalt informatie op over de Authenticode-hand tekening in een bestand."</span><span class="sxs-lookup"><span data-stu-id="8458d-119">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="8458d-120">Schrijf in actieve Voice.</span><span class="sxs-lookup"><span data-stu-id="8458d-120">Write in active voice.</span></span> <span data-ttu-id="8458d-121">Bijvoorbeeld ' het object time span gebruiken... ' is veel helderder dan het object time span kan worden gebruikt voor...</span><span class="sxs-lookup"><span data-stu-id="8458d-121">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="8458d-122">Vermijd het woord ' weer geven ' bij het beschrijven van cmdlets die objecten ophalen.</span><span class="sxs-lookup"><span data-stu-id="8458d-122">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="8458d-123">Hoewel er in Windows Power shell cmdlet-gegevens worden weer gegeven, is het belang rijk om gebruikers in te stellen voor het concept dat de cmdlet retourneert .NET Framework objecten waarvan de gegevens niet mogen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8458d-123">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="8458d-124">Als u de weer gave markeert, kan de gebruiker mogelijk niet realiseren dat de cmdlet veel andere nuttige eigenschappen en methoden heeft geretourneerd die niet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8458d-124">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8458d-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8458d-125">See Also</span></span>

[<span data-ttu-id="8458d-126">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8458d-126">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
