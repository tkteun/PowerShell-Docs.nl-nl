---
description: Biedt essentiële informatie over objecten in Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: 678eececc2625bf02a706e8ef61c83056443a12f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252783"
---
# <a name="about-objects"></a><span data-ttu-id="53bb2-104">Over objecten</span><span class="sxs-lookup"><span data-stu-id="53bb2-104">About Objects</span></span>

## <a name="short-description"></a><span data-ttu-id="53bb2-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="53bb2-105">Short Description</span></span>

<span data-ttu-id="53bb2-106">Biedt essentiële informatie over objecten in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="53bb2-106">Provides essential information about objects in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="53bb2-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="53bb2-107">Long Description</span></span>

<span data-ttu-id="53bb2-108">Elke actie die u in Windows Power shell uitvoert, vindt plaats in de context van de objecten.</span><span class="sxs-lookup"><span data-stu-id="53bb2-108">Every action you take in Windows PowerShell occurs within the context of objects.</span></span> <span data-ttu-id="53bb2-109">Wanneer gegevens worden verplaatst van de ene opdracht naar de volgende, wordt deze verplaatst als een of meer Identificeer bare objecten.</span><span class="sxs-lookup"><span data-stu-id="53bb2-109">As data moves from one command to the next, it moves as one or more identifiable objects.</span></span> <span data-ttu-id="53bb2-110">Een object en vervolgens is een verzameling gegevens die een item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="53bb2-110">An object, then, is a collection of data that represents an item.</span></span> <span data-ttu-id="53bb2-111">Een object bestaat uit drie soorten gegevens: het object type, de bijbehorende methoden en de bijbehorende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="53bb2-111">An object is made up of three types of data: the objects type, its methods, and its properties.</span></span>

## <a name="types-methods-and-properties"></a><span data-ttu-id="53bb2-112">Typen, methoden en eigenschappen</span><span class="sxs-lookup"><span data-stu-id="53bb2-112">Types, Methods, and Properties</span></span>

<span data-ttu-id="53bb2-113">Het object type geeft aan wat voor soort object het is.</span><span class="sxs-lookup"><span data-stu-id="53bb2-113">The object type tells what kind of object it is.</span></span> <span data-ttu-id="53bb2-114">Een object dat een bestand vertegenwoordigt, is bijvoorbeeld een file info-object.</span><span class="sxs-lookup"><span data-stu-id="53bb2-114">For example, an object that represents a file is a FileInfo object.</span></span>

<span data-ttu-id="53bb2-115">De object methoden zijn acties die u op het object kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="53bb2-115">The object methods are actions that you can perform on the object.</span></span>
<span data-ttu-id="53bb2-116">Zo hebben file info-objecten een CopyTo-methode die u kunt gebruiken om het bestand te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="53bb2-116">For example, FileInfo objects have a CopyTo method that you can use to copy the file.</span></span>

<span data-ttu-id="53bb2-117">Object eigenschappen slaan informatie over het object op.</span><span class="sxs-lookup"><span data-stu-id="53bb2-117">Object properties store information about the object.</span></span> <span data-ttu-id="53bb2-118">Zo hebben file info-objecten bijvoorbeeld een eigenschap LastWriteTime die de datum en tijd opslaat waarop het bestand het laatst is geopend.</span><span class="sxs-lookup"><span data-stu-id="53bb2-118">For example, FileInfo objects have a LastWriteTime property that stores the date and time that the file was most recently accessed.</span></span>

<span data-ttu-id="53bb2-119">Wanneer u met objecten werkt, kunt u de methoden en eigenschappen van opdrachten gebruiken om actie te ondernemen en gegevens te beheren.</span><span class="sxs-lookup"><span data-stu-id="53bb2-119">When working with objects, you can use their methods and properties in commands to take action and manage data.</span></span>

## <a name="objects-in-pipelines"></a><span data-ttu-id="53bb2-120">Objecten in pijp lijnen</span><span class="sxs-lookup"><span data-stu-id="53bb2-120">Objects in Pipelines</span></span>

<span data-ttu-id="53bb2-121">Wanneer opdrachten worden gecombineerd in een pijp lijn, geven ze informatie aan elkaar door als objecten.</span><span class="sxs-lookup"><span data-stu-id="53bb2-121">When commands are combined in a pipeline, they pass information to each other as objects.</span></span> <span data-ttu-id="53bb2-122">Wanneer de eerste opdracht wordt uitgevoerd, verzendt het een of meer objecten omlaag in de pijp lijn naar de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="53bb2-122">When the first command runs, it sends one or more objects down the pipeline to the second command.</span></span> <span data-ttu-id="53bb2-123">Met de tweede opdracht worden de objecten van de eerste opdracht ontvangen, worden de objecten verwerkt en worden nieuwe of gereviseerde objecten door gegeven aan de volgende opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53bb2-123">The second command receives the objects from the first command, processes the objects, and then passes new or revised objects to the next command in the pipeline.</span></span>
<span data-ttu-id="53bb2-124">Dit wordt voortgezet totdat alle opdrachten in de pijplijn worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="53bb2-124">This continues until all commands in the pipeline run.</span></span>

<span data-ttu-id="53bb2-125">In het volgende voor beeld ziet u hoe objecten worden door gegeven van één opdracht aan de volgende:</span><span class="sxs-lookup"><span data-stu-id="53bb2-125">The following example demonstrates how objects are passed from one command to the next:</span></span>

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

<span data-ttu-id="53bb2-126">De eerste opdracht `Get-ChildItem C:` retourneert een bestands-of Directory-object voor elk item in de hoofdmap van het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="53bb2-126">The first command `Get-ChildItem C:` returns a file or directory object for each item in the root directory of the file system.</span></span> <span data-ttu-id="53bb2-127">De bestands-en Directory objecten worden naar de tweede opdracht door gegeven aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53bb2-127">The file and directory objects are passed down the pipeline to the second command.</span></span>

<span data-ttu-id="53bb2-128">De tweede opdracht `where { $_.PsIsContainer -eq $false }` maakt gebruik van de eigenschap PsIsContainer van alle bestandssysteem objecten om alleen bestanden te selecteren die de waarde False ( \$ False) hebben in de eigenschap PsIsContainer.</span><span class="sxs-lookup"><span data-stu-id="53bb2-128">The second command `where { $_.PsIsContainer -eq $false }` uses the PsIsContainer property of all file system objects to select only files, which have a value of False (\$false) in their PsIsContainer property.</span></span> <span data-ttu-id="53bb2-129">Mappen, die containers zijn en die dus de waarde True ( \$ waar) hebben in de eigenschap PsIsContainer, worden niet geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="53bb2-129">Folders, which are containers and, thus, have a value of True (\$true) in their PsIsContainer property, are not selected.</span></span>

<span data-ttu-id="53bb2-130">Met de tweede opdracht worden alleen de bestands objecten door gegeven aan de derde opdracht `Format-List` , waarin de bestands objecten in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="53bb2-130">The second command passes only the file objects to the third command `Format-List`, which displays the file objects in a list.</span></span>

## <a name="see-also"></a><span data-ttu-id="53bb2-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="53bb2-131">See Also</span></span>

[<span data-ttu-id="53bb2-132">about_Methods</span><span class="sxs-lookup"><span data-stu-id="53bb2-132">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="53bb2-133">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="53bb2-133">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="53bb2-134">about_Properties</span><span class="sxs-lookup"><span data-stu-id="53bb2-134">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="53bb2-135">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="53bb2-135">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="53bb2-136">Get-member</span><span class="sxs-lookup"><span data-stu-id="53bb2-136">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
