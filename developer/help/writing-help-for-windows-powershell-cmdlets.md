---
title: Schrijfhulp voor PowerShell-Cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083158"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="8d5f6-102">Schrijven van Help voor PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="8d5f6-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="8d5f6-103">PowerShell-cmdlets kan nuttig zijn, maar, tenzij uw Help-onderwerpen duidelijk wat de cmdlet doet en het gebruik ervan, de cmdlet niet kan ophalen gebruikt, of nog erger, het kan frustrerend kan zijn voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="8d5f6-104">De indeling op basis van een XML-cmdlet Help verbetert de consistentie, maar erg nuttig vereist veel meer.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="8d5f6-105">Als u nooit cmdlet Help hebt geschreven, raadpleegt u de volgende richtlijnen.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="8d5f6-106">Het XML-schema vereist voor het maken van de cmdlet Help-onderwerp wordt beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="8d5f6-107">Beginnen met [het maken van de Cmdlet Help-bestand](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="8d5f6-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="8d5f6-108">Dit onderwerp bevat een beschrijving van de op het hoogste niveau XML-knooppunten.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="8d5f6-109">Richtlijnen voor de Help van de Cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="8d5f6-110">Ook schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-110">Write well</span></span>
<span data-ttu-id="8d5f6-111">Niets wordt vervangen door een goed geschreven onderwerp.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="8d5f6-112">Als u niet een professionele schrijver, vindt u een schrijver of -editor om u te helpen.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="8d5f6-113">Een ander alternatief is om te kopiëren van de Help-tekst in Microsoft Word en gebruiken van de grammatica en spelling controleren ter verbetering van uw werk.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="8d5f6-114">Alleen schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-114">Write simply</span></span>
<span data-ttu-id="8d5f6-115">Gebruik eenvoudige woorden en zinnen.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-115">Use simple words and phrases.</span></span>
<span data-ttu-id="8d5f6-116">Vermijd jargon.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-116">Avoid jargon.</span></span>
<span data-ttu-id="8d5f6-117">Houd rekening met dat veel lezers zijn uitgerust met een woordenlijst vreemde taal en het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="8d5f6-118">Consistent schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-118">Write consistently</span></span>
<span data-ttu-id="8d5f6-119">Help voor verwante cmdlets (voor bijvoorbeeld get-x en set-x) vergelijkbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="8d5f6-120">Gebruik van de beschrijvingen van de standaard voor standard parameters, zoals **Force** en **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="8d5f6-121">(Kopieer deze in de Help voor de core-cmdlets.) Standard gebruiksrechtovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="8d5f6-122">Bijvoorbeeld, gebruik 'parameter', niet 'argument' en gebruik 'cmdlet"niet"opdracht' of 'command-let'.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="8d5f6-123">De samenvatting met een bewerking starten</span><span class="sxs-lookup"><span data-stu-id="8d5f6-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="8d5f6-124">Het veld Samenvatting wordt de gebruiker geïnformeerd, wat de cmdlet, niet wat dit is of hoe het werkt.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="8d5f6-125">Bewerkingen maken een taakgebaseerde instructie waarmee gebruikers worden geïnformeerd als deze cmdlet voldoet aan de vereisten.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="8d5f6-126">Gebruik eenvoudige woorden als 'ophalen', 'maken' en "wijzigen."</span><span class="sxs-lookup"><span data-stu-id="8d5f6-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="8d5f6-127">Vermijd 'instellen', wat kan vaag zijn en decoratieve woorden als 'wijzigen' zijn.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="8d5f6-128">Richt u op objecten</span><span class="sxs-lookup"><span data-stu-id="8d5f6-128">Focus on objects</span></span>
<span data-ttu-id="8d5f6-129">De meeste 'ophalen' cmdlets weergave iets, maar de primaire functie is om op te halen van een object.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="8d5f6-130">In de Help, die zich richten op het object, zodat gebruikers weten dat de standaardweergave is een van de vele en dat ze de methoden en eigenschappen van het object dat u hebt opgehaald voor ze op verschillende manieren kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="8d5f6-131">Gedetailleerde beschrijvingen schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-131">Write detailed descriptions</span></span>
<span data-ttu-id="8d5f6-132">Geef een korte lijst alles wat de cmdlet in de gedetailleerde beschrijving doen kunt.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="8d5f6-133">Als de main-functie is een eigenschap te wijzigen, maar de cmdlet alle eigenschappen kunt wijzigen, kunt u dit in de gedetailleerde beschrijving van de lijst.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="8d5f6-134">Gebruik de syntaxis van de conventionele</span><span class="sxs-lookup"><span data-stu-id="8d5f6-134">Use conventional syntax</span></span>
<span data-ttu-id="8d5f6-135">Gebruik de standaard Backus Naur-indeling die gebruikt voor het Windows- en UNIX Help voor de opdrachtregel wordt.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="8d5f6-136">Microsoft .NET Framework-typen voor parameterwaarden gebruiken</span><span class="sxs-lookup"><span data-stu-id="8d5f6-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="8d5f6-137">De tijdelijke aanduidingen voor de parameterwaarden (in de beschrijvingen van de syntaxis en parameteropties) weergeven de .NET Framework-typen van de objecten die de parameter accepteert.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="8d5f6-138">Het PowerShell-team ontwikkeld deze afspraak om te leren van gebruikers over de .NET-Framework.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="8d5f6-139">Beschrijvingen van de volledige parameters schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="8d5f6-140">Beschrijvingen van de parameters moeten in kennis stellen gebruikers van twee dingen: wat de parameter (het effect ervan) doet en wat ze voor de parameterwaarden moeten typen.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="8d5f6-141">Praktijkvoorbeelden schrijven</span><span class="sxs-lookup"><span data-stu-id="8d5f6-141">Write practical examples</span></span>
<span data-ttu-id="8d5f6-142">Het gebruik van alle parameters moeten worden weergegeven in de voorbeelden, maar het belangrijkste is om weer te geven over het gebruik van de cmdlet in de praktijk taken.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="8d5f6-143">Beginnen met een eenvoudig voorbeeld en steeds complexer voorbeelden schrijven.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="8d5f6-144">In het laatste voorbeeld te laten zien hoe de cmdlet gebruiken in een pijplijn.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="8d5f6-145">Het veld Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8d5f6-145">Use the Notes field</span></span>
<span data-ttu-id="8d5f6-146">Gebruik het veld Notities om uit te leggen van de concepten die gebruikers nodig hebben om te begrijpen van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="8d5f6-147">U kunt ook notities gebruiken om veelvoorkomende fouten te voorkomen dat gebruikers te helpen.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="8d5f6-148">Vermijd URL's als ze worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="8d5f6-149">In plaats daarvan bieden voorwaarden om te zoeken naar gebruikers.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="8d5f6-150">Test uw hulp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-150">Test your Help</span></span>
<span data-ttu-id="8d5f6-151">Test de Help net zoals u bij het testen van uw code.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="8d5f6-152">Vrienden en collega's uw Help-inhoud lezen en feedback geven.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="8d5f6-153">Ook kunt u feedback van nieuwsgroepen krijgen.</span><span class="sxs-lookup"><span data-stu-id="8d5f6-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d5f6-154">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8d5f6-154">See Also</span></span>

 [<span data-ttu-id="8d5f6-155">Over het maken van de Cmdlet Help-bestand</span><span class="sxs-lookup"><span data-stu-id="8d5f6-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="8d5f6-156">De naam van Cmdlet en samenvatting toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-157">De gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="8d5f6-158">Syntaxis toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-159">Parameters toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="8d5f6-160">Invoertypen voor een Cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="8d5f6-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-161">Geretourneerde waarden toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-162">Opmerkingen bij de toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-163">Voorbeelden van een Cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="8d5f6-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-164">Verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="8d5f6-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8d5f6-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8d5f6-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)