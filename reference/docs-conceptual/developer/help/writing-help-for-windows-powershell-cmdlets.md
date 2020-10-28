---
ms.date: 09/13/2016
ms.topic: reference
title: Help voor PowerShell-cmdlets schrijven
description: Help voor PowerShell-cmdlets schrijven
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658098"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="cc6fc-103">Help voor PowerShell-cmdlets schrijven</span><span class="sxs-lookup"><span data-stu-id="cc6fc-103">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="cc6fc-104">Power shell-cmdlets kunnen nuttig zijn, maar tenzij in uw Help-onderwerpen duidelijk wordt uitgelegd wat de cmdlet doet en hoe u deze kunt gebruiken, kan de cmdlet mogelijk niet worden gebruikt of, zelfs als dit niet mogelijk is, kan de gebruiker de gegevens weer geven.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-104">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span> <span data-ttu-id="cc6fc-105">De Help-indeling van het XML-cmdlet-bestand verbetert de consistentie, maar er is veel meer hulp nodig.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-105">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="cc6fc-106">Als u de Help-informatie over de cmdlet nooit hebt geschreven, raadpleegt u de volgende richt lijnen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-106">If you have never written cmdlet Help, review the following guidelines.</span></span> <span data-ttu-id="cc6fc-107">Het XML-schema dat is vereist voor het schrijven van het Help-onderwerp van de cmdlet wordt beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-107">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span> <span data-ttu-id="cc6fc-108">Begin met [het maken van het Help-bestand voor de cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="cc6fc-108">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span> <span data-ttu-id="cc6fc-109">Dit onderwerp bevat een beschrijving van de XML-knoop punten op het hoogste niveau.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-109">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="cc6fc-110">Richt lijnen voor het schrijven van cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-110">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="cc6fc-111">Goed schrijven</span><span class="sxs-lookup"><span data-stu-id="cc6fc-111">Write well</span></span>

<span data-ttu-id="cc6fc-112">Er wordt geen goed geschreven onderwerp vervangen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-112">Nothing replaces a well-written topic.</span></span> <span data-ttu-id="cc6fc-113">Als u geen professionele schrijver bent, kunt u een schrijver of redacteur vinden om u te helpen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-113">If you are not a professional writer, find a writer or editor to help you.</span></span> <span data-ttu-id="cc6fc-114">U kunt ook de Help-tekst kopiëren naar micro soft Word en de grammatica-en spelling controle gebruiken om uw werk te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-114">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="cc6fc-115">Schrijf eenvoudigweg</span><span class="sxs-lookup"><span data-stu-id="cc6fc-115">Write simply</span></span>

<span data-ttu-id="cc6fc-116">Gebruik eenvoudige woorden en zinsdelen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-116">Use simple words and phrases.</span></span> <span data-ttu-id="cc6fc-117">Vermijd jargon.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-117">Avoid jargon.</span></span> <span data-ttu-id="cc6fc-118">Houd er rekening mee dat veel lezers alleen zijn uitgerust met een woorden lijst in een vreemde taal en het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-118">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="cc6fc-119">Consistent schrijven</span><span class="sxs-lookup"><span data-stu-id="cc6fc-119">Write consistently</span></span>

<span data-ttu-id="cc6fc-120">Help voor gerelateerde cmdlets moet vergelijkbaar zijn (bijvoorbeeld Get-x en set-x).</span><span class="sxs-lookup"><span data-stu-id="cc6fc-120">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span> <span data-ttu-id="cc6fc-121">Gebruik de standaard beschrijvingen voor standaard parameters, zoals **Force** en **input object** .</span><span class="sxs-lookup"><span data-stu-id="cc6fc-121">Use the standard descriptions for standard parameters, like **Force** and **InputObject** .</span></span> <span data-ttu-id="cc6fc-122">(Kopieer ze in de Help voor de kern-cmdlets.) Gebruik standaard termen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-122">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span> <span data-ttu-id="cc6fc-123">Gebruik bijvoorbeeld "para meter", niet "argument" en gebruik "cmdlet" niet "opdracht" of "opdracht-Let".</span><span class="sxs-lookup"><span data-stu-id="cc6fc-123">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="cc6fc-124">De samen vatting starten met een werk woord</span><span class="sxs-lookup"><span data-stu-id="cc6fc-124">Start the synopsis with a verb</span></span>

<span data-ttu-id="cc6fc-125">In het veld samen vatting wordt de gebruiker geïnformeerd wat de cmdlet doet, niet wat het is of hoe deze werkt.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-125">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span> <span data-ttu-id="cc6fc-126">Met werk woorden maakt u een op taken gebaseerde instructie waarmee gebruikers worden geïnformeerd als deze cmdlet voldoet aan de vereisten.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-126">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span> <span data-ttu-id="cc6fc-127">Gebruik eenvoudige werk woorden zoals ' Get ', ' maken ' en ' wijzigen '.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-127">Use simple verbs like "get", "create", and "change."</span></span> <span data-ttu-id="cc6fc-128">Vermijd ' set '. Dit kan vague en decoratieve woorden als ' Modify ' zijn.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-128">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="cc6fc-129">Focus op objecten</span><span class="sxs-lookup"><span data-stu-id="cc6fc-129">Focus on objects</span></span>

<span data-ttu-id="cc6fc-130">Met de meeste Get-cmdlets wordt iets weer gegeven, maar de primaire functie is om een object op te halen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-130">Most "get" cmdlets display something, but their primary function is to get an object.</span></span> <span data-ttu-id="cc6fc-131">Focus op het object in uw Help, zodat gebruikers weten dat de standaard weergave een van de vele is en dat ze de methoden en eigenschappen van het object kunnen gebruiken dat u op verschillende manieren hebt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-131">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="cc6fc-132">Gedetailleerde beschrijvingen schrijven</span><span class="sxs-lookup"><span data-stu-id="cc6fc-132">Write detailed descriptions</span></span>

<span data-ttu-id="cc6fc-133">Geef een kort overzicht van alles wat met de cmdlet kan worden uitgevoerd in de gedetailleerde beschrijving.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-133">Briefly list everything that the cmdlet can do in the detailed description.</span></span> <span data-ttu-id="cc6fc-134">Als de hoofd functie één eigenschap wijzigt, maar de cmdlet alle eigenschappen kan wijzigen, vermeldt u deze in de gedetailleerde beschrijving.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-134">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="cc6fc-135">Conventionele syntaxis gebruiken</span><span class="sxs-lookup"><span data-stu-id="cc6fc-135">Use conventional syntax</span></span>

<span data-ttu-id="cc6fc-136">Gebruik de standaard Backus-Naur indeling die gebruikelijk is voor Windows-en UNIX-opdracht regel Help.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-136">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-types-for-parameter-values"></a><span data-ttu-id="cc6fc-137">Microsoft .NET typen voor parameter waarden gebruiken</span><span class="sxs-lookup"><span data-stu-id="cc6fc-137">Use Microsoft .NET types for parameter values</span></span>

<span data-ttu-id="cc6fc-138">De tijdelijke aanduidingen voor parameter waarden (in de syntaxis en parameter beschrijvingen) tonen de .NET Framework typen van de objecten die door de para meter worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-138">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span> <span data-ttu-id="cc6fc-139">Het Power shell-team heeft deze Conventie ontwikkeld om gebruikers over de .NET Framework te leren.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-139">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="cc6fc-140">Volledige beschrijvingen van de para meters schrijven</span><span class="sxs-lookup"><span data-stu-id="cc6fc-140">Write complete parameter descriptions</span></span>

<span data-ttu-id="cc6fc-141">Parameter beschrijvingen moeten gebruikers van twee dingen informeren: wat de para meter doet (het effect) en wat ze moeten typen voor de parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-141">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="cc6fc-142">Praktijk voorbeelden schrijven</span><span class="sxs-lookup"><span data-stu-id="cc6fc-142">Write practical examples</span></span>

<span data-ttu-id="cc6fc-143">In de voor beelden ziet u hoe u alle para meters kunt gebruiken, maar het belangrijkste is om te laten zien hoe u de cmdlet in Real-World-taken kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-143">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span> <span data-ttu-id="cc6fc-144">Begin met een eenvoudig voor beeld en schrijf steeds complexe voor beelden.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-144">Start with a simple example and write increasingly complex examples.</span></span> <span data-ttu-id="cc6fc-145">In het laatste voor beeld laat zien hoe u de cmdlet in een pijp lijn kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-145">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="cc6fc-146">Het notitie veld gebruiken</span><span class="sxs-lookup"><span data-stu-id="cc6fc-146">Use the Notes field</span></span>

<span data-ttu-id="cc6fc-147">Gebruik het veld opmerkingen om concepten uit te leggen die gebruikers nodig hebben om de cmdlet te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-147">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span> <span data-ttu-id="cc6fc-148">U kunt ook notities gebruiken om gebruikers te helpen veelvoorkomende fouten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-148">You can also use notes to help users avoid common errors.</span></span> <span data-ttu-id="cc6fc-149">Vermijd Url's wanneer ze worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-149">Avoid URLs as they change.</span></span> <span data-ttu-id="cc6fc-150">Geef in plaats daarvan de gebruikers voorwaarden op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-150">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="cc6fc-151">Uw Help testen</span><span class="sxs-lookup"><span data-stu-id="cc6fc-151">Test your Help</span></span>

<span data-ttu-id="cc6fc-152">Test de Help op dezelfde manier als bij het testen van uw code.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-152">Test the Help just like you test your code.</span></span> <span data-ttu-id="cc6fc-153">Laat vrienden en collega's uw Help-inhoud lezen en feedback geven.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-153">Have friends and colleagues read your Help content and provide feedback.</span></span> <span data-ttu-id="cc6fc-154">U kunt ook feedback van nieuws groepen aanvragen.</span><span class="sxs-lookup"><span data-stu-id="cc6fc-154">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc6fc-155">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cc6fc-155">See Also</span></span>

 [<span data-ttu-id="cc6fc-156">Het Help-bestand voor cmdlets maken</span><span class="sxs-lookup"><span data-stu-id="cc6fc-156">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="cc6fc-157">De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-157">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-158">De gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-158">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="cc6fc-159">Syntaxis toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-159">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-160">Para meters toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-160">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="cc6fc-161">Invoer typen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-161">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-162">Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-162">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-163">Notities toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-163">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-164">Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-164">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-165">Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc6fc-165">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="cc6fc-166">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cc6fc-166">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
