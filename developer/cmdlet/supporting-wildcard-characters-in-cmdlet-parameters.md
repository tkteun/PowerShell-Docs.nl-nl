---
title: Ondersteuning van jokertekens in de Cmdlet-Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851371"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="16602-102">Ondersteuning voor jokertekens in de cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="16602-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="16602-103">U moet vaak ontwerpen van een cmdlet uit te voeren op basis van een groep resources in plaats van op basis van één resource.</span><span class="sxs-lookup"><span data-stu-id="16602-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="16602-104">Bijvoorbeeld, moet een cmdlet mogelijk Zoek alle bestanden in een gegevensarchief met dezelfde naam of -extensie.</span><span class="sxs-lookup"><span data-stu-id="16602-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="16602-105">U moet ondersteuning bieden voor jokertekens bij het ontwerpen van een cmdlet die wordt uitgevoerd op basis van een groep resources.</span><span class="sxs-lookup"><span data-stu-id="16602-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="16602-106">Met jokertekens wordt soms aangeduid als *bij globbing*.</span><span class="sxs-lookup"><span data-stu-id="16602-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="16602-107">Windows PowerShell-Cmdlets die gebruikmaken van jokertekens</span><span class="sxs-lookup"><span data-stu-id="16602-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="16602-108">Veel Windows PowerShell-cmdlets voor ondersteuning voor jokertekens voor hun parameterwaarden.</span><span class="sxs-lookup"><span data-stu-id="16602-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="16602-109">Bijna elke cmdlet die heeft bijvoorbeeld een `Name` of `Path` parameter ondersteunt jokertekens voor deze parameters.</span><span class="sxs-lookup"><span data-stu-id="16602-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="16602-110">(Hoewel de meeste cmdlets die beschikken over een `Path` parameter hebben ook een `LiteralPath` parameter die geen ondersteuning biedt voor jokertekens bevatten.) De volgende opdracht laat zien hoe een jokerteken wordt gebruikt voor het retourneren van alle cmdlets in de huidige sessie waarvan de naam van de Get-bewerking bevat.</span><span class="sxs-lookup"><span data-stu-id="16602-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="16602-111">**PS > get-opdracht get -\***</span><span class="sxs-lookup"><span data-stu-id="16602-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="16602-112">Ondersteunde jokertekens</span><span class="sxs-lookup"><span data-stu-id="16602-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="16602-113">Windows PowerShell ondersteunt de volgende jokertekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="16602-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="16602-114">Jokerteken</span><span class="sxs-lookup"><span data-stu-id="16602-114">Wildcard character</span></span>|<span data-ttu-id="16602-115">Description</span><span class="sxs-lookup"><span data-stu-id="16602-115">Description</span></span>|<span data-ttu-id="16602-116">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="16602-116">Example</span></span>|<span data-ttu-id="16602-117">Overeenkomsten</span><span class="sxs-lookup"><span data-stu-id="16602-117">Matches</span></span>|<span data-ttu-id="16602-118">Komt niet overeen met</span><span class="sxs-lookup"><span data-stu-id="16602-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="16602-119">Komt overeen met nul of meer tekens, vanaf de opgegeven positie</span><span class="sxs-lookup"><span data-stu-id="16602-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="16602-120">a\*</span><span class="sxs-lookup"><span data-stu-id="16602-120">a\*</span></span>|<span data-ttu-id="16602-121">Een, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="16602-121">A, ag, Apple</span></span>||
|<span data-ttu-id="16602-122">?</span><span class="sxs-lookup"><span data-stu-id="16602-122">?</span></span>|<span data-ttu-id="16602-123">Komt overeen met anycharacter op de opgegeven positie</span><span class="sxs-lookup"><span data-stu-id="16602-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="16602-124">? n</span><span class="sxs-lookup"><span data-stu-id="16602-124">?n</span></span>|<span data-ttu-id="16602-125">Een in het geval is, op</span><span class="sxs-lookup"><span data-stu-id="16602-125">An, in, on</span></span>|<span data-ttu-id="16602-126">is uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="16602-126">ran</span></span>|
|<span data-ttu-id="16602-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="16602-127">[ ]</span></span>|<span data-ttu-id="16602-128">Komt overeen met een bereik met tekens</span><span class="sxs-lookup"><span data-stu-id="16602-128">Matches a range of characters</span></span>|<span data-ttu-id="16602-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="16602-129">[a-l]ook</span></span>|<span data-ttu-id="16602-130">het adresboek, Cookeilanden, zoekt u naar</span><span class="sxs-lookup"><span data-stu-id="16602-130">book, cook, look</span></span>|<span data-ttu-id="16602-131">duurde</span><span class="sxs-lookup"><span data-stu-id="16602-131">took</span></span>|
|<span data-ttu-id="16602-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="16602-132">[ ]</span></span>|<span data-ttu-id="16602-133">Komt overeen met de opgegeven tekens</span><span class="sxs-lookup"><span data-stu-id="16602-133">Matches the specified characters</span></span>|<span data-ttu-id="16602-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="16602-134">[bc]ook</span></span>|<span data-ttu-id="16602-135">boek, Cookeilanden</span><span class="sxs-lookup"><span data-stu-id="16602-135">book, cook</span></span>|<span data-ttu-id="16602-136">zoeken</span><span class="sxs-lookup"><span data-stu-id="16602-136">look</span></span>|

<span data-ttu-id="16602-137">Bij het ontwerpen van cmdlets die ondersteuning bieden voor jokertekens bevatten, kunt u voor combinaties van jokertekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="16602-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="16602-138">Bijvoorbeeld, de volgende opdracht maakt gebruik van de `Get-ChildItem` cmdlet voor het ophalen van alle txt-bestanden die zijn opgenomen in de map c:\Techdocs en die beginnen met de letter 'a"via 'l'.</span><span class="sxs-lookup"><span data-stu-id="16602-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="16602-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="16602-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="16602-140">De vorige opdracht maakt gebruik van het jokerteken bereik **[a-l]** om op te geven dat de naam moet beginnen met de tekens 'a"via 'l'.</span><span class="sxs-lookup"><span data-stu-id="16602-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="16602-141">Vervolgens gebruikt de opdracht de \* jokerteken als tijdelijke aanduiding voor alle tekens tussen de eerste letter van de bestandsnaam en de extensie .txt.</span><span class="sxs-lookup"><span data-stu-id="16602-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="16602-142">Het volgende voorbeeld wordt een bereik wildcard-patroon dat niet van toepassing op de letter "d", maar bevat alle andere letters uit 'a"via 'f'.</span><span class="sxs-lookup"><span data-stu-id="16602-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="16602-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="16602-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="16602-144">Afhandeling van letterlijke tekens in jokertekenpatronen</span><span class="sxs-lookup"><span data-stu-id="16602-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="16602-145">Als het jokerteken-patroon dat u opgeeft letterlijke tekens bevat, gebruikt u het backtick-teken (') als een escape-teken.</span><span class="sxs-lookup"><span data-stu-id="16602-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="16602-146">Wanneer u via een programma letterlijke tekens opgeeft, gebruikt u een enkele backtick.</span><span class="sxs-lookup"><span data-stu-id="16602-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="16602-147">Wanneer u letterlijke tekens bij de opdrachtprompt opgeeft, gebruikt u twee graves.</span><span class="sxs-lookup"><span data-stu-id="16602-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="16602-148">Het volgende patroon bevat bijvoorbeeld twee haakjes letterlijk moeten worden genomen.</span><span class="sxs-lookup"><span data-stu-id="16602-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="16602-149">' John Smith \`[\*'] ' (opgegeven via een programma)</span><span class="sxs-lookup"><span data-stu-id="16602-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="16602-150">' John Smith \` \`[\*\`'] ' (opgegeven bij de opdrachtprompt)</span><span class="sxs-lookup"><span data-stu-id="16602-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="16602-151">Dit patroon komt overeen met 'John Smith [Marketing]' of 'John Smith [ontwikkeling]'.</span><span class="sxs-lookup"><span data-stu-id="16602-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="16602-152">Cmdlet-uitvoer en jokertekens</span><span class="sxs-lookup"><span data-stu-id="16602-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="16602-153">Als parameters van de cmdlet jokertekens ondersteunt, genereert een cmdlet-bewerking gewoonlijk de matrixuitvoer van een.</span><span class="sxs-lookup"><span data-stu-id="16602-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="16602-154">Soms kan zinvol het geen ter ondersteuning van een matrix uitgevoerd omdat de gebruiker kan slechts één item tegelijk gebruiken.</span><span class="sxs-lookup"><span data-stu-id="16602-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="16602-155">Bijvoorbeeld, de `Set-Location` cmdlet biedt ondersteuning voor een matrix uitgevoerd omdat de gebruiker wordt ingesteld alleen één locatie.</span><span class="sxs-lookup"><span data-stu-id="16602-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="16602-156">In dit geval de cmdlet nog steeds jokertekens worden ondersteund, maar het zorgt ervoor dat het probleem zou moeten op één locatie.</span><span class="sxs-lookup"><span data-stu-id="16602-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="16602-157">Zie ook</span><span class="sxs-lookup"><span data-stu-id="16602-157">See Also</span></span>

[<span data-ttu-id="16602-158">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16602-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="16602-159">WildcardPattern klasse</span><span class="sxs-lookup"><span data-stu-id="16602-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
