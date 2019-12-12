---
title: De naam en samen vatting van de cmdlet toevoegen aan een Help-onderwerp voor cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353254"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="6ff59-102">De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="6ff59-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6ff59-103">In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de secties naam en samen VATTING van de Help van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ff59-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="6ff59-104">In het Help-bestand wordt deze inhoud toegevoegd aan het opdracht knooppunt voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ff59-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="6ff59-105">Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden.</span><span class="sxs-lookup"><span data-stu-id="6ff59-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="6ff59-106">Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6ff59-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="6ff59-107">De naam van de cmdlet en een samen vatting toevoegen</span><span class="sxs-lookup"><span data-stu-id="6ff59-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="6ff59-108">De Help van de cmdlet kan twee beschrijvingen voor de cmdlet weer geven.</span><span class="sxs-lookup"><span data-stu-id="6ff59-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="6ff59-109">De eerste beschrijving is een korte beschrijving die de samen vatting wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="6ff59-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="6ff59-110">De tweede beschrijving is een gedetailleerde beschrijving die wordt beschreven in [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="6ff59-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="6ff59-111">Beide beschrijvingen moeten worden geschreven als één alinea.</span><span class="sxs-lookup"><span data-stu-id="6ff59-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="6ff59-112">Herhaal de naam van de cmdlet niet in de samen vatting.</span><span class="sxs-lookup"><span data-stu-id="6ff59-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="6ff59-113">Door de gebruiker te informeren dat de get-server-cmdlet een server krijgt, is kort, maar niet informatief.</span><span class="sxs-lookup"><span data-stu-id="6ff59-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="6ff59-114">Gebruik in plaats daarvan synoniemen en Voeg details toe aan de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="6ff59-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="6ff59-115">Voor beeld: "haalt een object op dat een lokale of externe computer vertegenwoordigt."</span><span class="sxs-lookup"><span data-stu-id="6ff59-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="6ff59-116">Gebruik eenvoudige werk woorden zoals ' Get ', ' maken ' en ' wijzigen ' in de samen vatting.</span><span class="sxs-lookup"><span data-stu-id="6ff59-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="6ff59-117">Vermijd het gebruik van ' set ' omdat het Vague is en decoratieve woorden zoals ' Modify '.</span><span class="sxs-lookup"><span data-stu-id="6ff59-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="6ff59-118">Voor beeld: "haalt informatie op over de Authenticode-hand tekening in een bestand."</span><span class="sxs-lookup"><span data-stu-id="6ff59-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="6ff59-119">Schrijf in actieve Voice.</span><span class="sxs-lookup"><span data-stu-id="6ff59-119">Write in active voice.</span></span> <span data-ttu-id="6ff59-120">Bijvoorbeeld ' het object time span gebruiken... ' is veel helderder dan het object time span kan worden gebruikt voor...</span><span class="sxs-lookup"><span data-stu-id="6ff59-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="6ff59-121">Vermijd het woord ' weer geven ' bij het beschrijven van cmdlets die objecten ophalen.</span><span class="sxs-lookup"><span data-stu-id="6ff59-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="6ff59-122">Hoewel er in Windows Power shell cmdlet-gegevens worden weer gegeven, is het belang rijk om gebruikers in te stellen voor het concept dat de cmdlet retourneert .NET Framework objecten waarvan de gegevens niet mogen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6ff59-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="6ff59-123">Als u de weer gave markeert, kan de gebruiker mogelijk niet realiseren dat de cmdlet veel andere nuttige eigenschappen en methoden heeft geretourneerd die niet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6ff59-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ff59-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6ff59-124">See Also</span></span>

 [<span data-ttu-id="6ff59-125">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="6ff59-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)