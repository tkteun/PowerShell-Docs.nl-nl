---
title: De naam van Cmdlet en samenvatting toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083330"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="9665d-102">De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="9665d-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="9665d-103">Deze sectie wordt beschreven hoe u inhoud die wordt weergegeven in de secties naam en samenvatting van de help van de cmdlet toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="9665d-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="9665d-104">In het Help-bestand, wordt deze inhoud toegevoegd aan het knooppunt van de opdracht voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9665d-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="9665d-105">Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9665d-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="9665d-106">Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9665d-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="9665d-107">De Cmdlet-naam en een samenvatting toe te voegen</span><span class="sxs-lookup"><span data-stu-id="9665d-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="9665d-108">De cmdlet Help kan twee beschrijvingen voor de cmdlet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9665d-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="9665d-109">De beschrijving van de eerste is een korte beschrijving die wordt aangeduid als de samenvatting.</span><span class="sxs-lookup"><span data-stu-id="9665d-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="9665d-110">De beschrijving van de tweede is een gedetailleerde beschrijving die wordt besproken in [de gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="9665d-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="9665d-111">Beide deze beschrijvingen tekstberichten worden geschreven als een enkele alinea.</span><span class="sxs-lookup"><span data-stu-id="9665d-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="9665d-112">Herhaal de cmdlet-naam niet in de samenvatting.</span><span class="sxs-lookup"><span data-stu-id="9665d-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="9665d-113">Waarin de gebruiker die de cmdlet Get-Server krijgt u een server is korte, maar niet informatieve.</span><span class="sxs-lookup"><span data-stu-id="9665d-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="9665d-114">In plaats daarvan gebruik van synoniemen en details toevoegen aan de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="9665d-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="9665d-115">Voorbeeld: "Haalt een object dat staat voor een lokale of externe computer."</span><span class="sxs-lookup"><span data-stu-id="9665d-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="9665d-116">Gebruik eenvoudige woorden als 'ophalen', 'maken' en '' in de samenvatting wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9665d-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="9665d-117">Vermijd het gebruik van 'instellen' omdat het vaag zijn, en decoratieve woorden zoals 'wijzigen."</span><span class="sxs-lookup"><span data-stu-id="9665d-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="9665d-118">Voorbeeld: "Hiermee haalt informatie over de Authenticode-handtekening in een bestand."</span><span class="sxs-lookup"><span data-stu-id="9665d-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="9665d-119">In de actieve stem schrijven.</span><span class="sxs-lookup"><span data-stu-id="9665d-119">Write in active voice.</span></span> <span data-ttu-id="9665d-120">Bijvoorbeeld, "gebruiken het object TimeSpan..." is veel beter dan 'de TimeSpan-object kan worden gebruikt om te...'</span><span class="sxs-lookup"><span data-stu-id="9665d-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="9665d-121">Vermijd de term 'weergegeven' bij de beschrijving van cmdlets die objecten ophalen.</span><span class="sxs-lookup"><span data-stu-id="9665d-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="9665d-122">Hoewel Windows PowerShell cmdlet gegevens worden weergegeven, is het belangrijk om te introduceren van gebruikers met het concept die de cmdlet retourneert .NET Framework-objecten waarvan de gegevens kunnen niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9665d-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="9665d-123">Als u de weergave benadrukken, kan de gebruiker niet realiseren dat de cmdlet mogelijk geretourneerd veel andere nuttige eigenschappen en methoden die niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9665d-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="9665d-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9665d-124">See Also</span></span>

 [<span data-ttu-id="9665d-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9665d-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)