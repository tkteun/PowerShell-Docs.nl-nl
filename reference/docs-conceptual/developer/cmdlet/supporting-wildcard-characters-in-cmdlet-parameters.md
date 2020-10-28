---
ms.date: 08/26/2019
ms.topic: reference
title: Ondersteuning voor jokertekens in de cmdlet-parameters
description: Ondersteuning voor jokertekens in de cmdlet-parameters
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646387"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="f649e-103">Ondersteuning voor jokertekens in de cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="f649e-103">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="f649e-104">Vaak moet u een cmdlet ontwerpen om uit te voeren op basis van een groep resources en niet op basis van één resource.</span><span class="sxs-lookup"><span data-stu-id="f649e-104">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="f649e-105">Een cmdlet kan bijvoorbeeld alle bestanden in een gegevens archief met dezelfde naam of extensie moeten zoeken.</span><span class="sxs-lookup"><span data-stu-id="f649e-105">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="f649e-106">U moet ondersteuning bieden voor joker tekens wanneer u een cmdlet ontwerpt die wordt uitgevoerd voor een groep resources.</span><span class="sxs-lookup"><span data-stu-id="f649e-106">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="f649e-107">Het gebruik van joker tekens wordt soms ook wel *globbing* genoemd.</span><span class="sxs-lookup"><span data-stu-id="f649e-107">Using wildcard characters is sometimes referred to as *globbing* .</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="f649e-108">Windows Power shell-cmdlets die gebruikmaken van joker tekens</span><span class="sxs-lookup"><span data-stu-id="f649e-108">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="f649e-109">Veel Windows Power shell-cmdlets ondersteunen joker tekens voor hun parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="f649e-109">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="f649e-110">Bijna elke cmdlet met een `Name` or- `Path` para meter ondersteunt bijvoorbeeld joker tekens voor deze para meters.</span><span class="sxs-lookup"><span data-stu-id="f649e-110">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="f649e-111">(Hoewel de meeste cmdlets die een `Path` para meter hebben ook een `LiteralPath` para meter hebben die geen joker tekens ondersteunt.) De volgende opdracht laat zien hoe een Joker teken wordt gebruikt om alle cmdlets in de huidige sessie te retour neren waarvan de naam de bewerking Get bevat.</span><span class="sxs-lookup"><span data-stu-id="f649e-111">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="f649e-112">Ondersteunde joker tekens</span><span class="sxs-lookup"><span data-stu-id="f649e-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="f649e-113">Windows Power shell ondersteunt de volgende joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f649e-113">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="f649e-114">Vervanging</span><span class="sxs-lookup"><span data-stu-id="f649e-114">Wildcard</span></span> |                             <span data-ttu-id="f649e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f649e-115">Description</span></span>                             |  <span data-ttu-id="f649e-116">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f649e-116">Example</span></span>   |     <span data-ttu-id="f649e-117">Komt overeen met</span><span class="sxs-lookup"><span data-stu-id="f649e-117">Matches</span></span>      | <span data-ttu-id="f649e-118">Komt niet overeen met</span><span class="sxs-lookup"><span data-stu-id="f649e-118">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="f649e-119">Komt overeen met nul of meer tekens, beginnend bij de opgegeven positie</span><span class="sxs-lookup"><span data-stu-id="f649e-119">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="f649e-120">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="f649e-120">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="f649e-121">?</span><span class="sxs-lookup"><span data-stu-id="f649e-121">?</span></span>        | <span data-ttu-id="f649e-122">Komt overeen met een teken op de opgegeven positie</span><span class="sxs-lookup"><span data-stu-id="f649e-122">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="f649e-123">Een, in, op</span><span class="sxs-lookup"><span data-stu-id="f649e-123">An, in, on</span></span>       | <span data-ttu-id="f649e-124">uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="f649e-124">ran</span></span>            |
| <span data-ttu-id="f649e-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="f649e-125">[ ]</span></span>      | <span data-ttu-id="f649e-126">Komt overeen met een reeks tekens</span><span class="sxs-lookup"><span data-stu-id="f649e-126">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="f649e-127">Book, Cook, zoeken</span><span class="sxs-lookup"><span data-stu-id="f649e-127">book, cook, look</span></span> | <span data-ttu-id="f649e-128">Nook, geduurde</span><span class="sxs-lookup"><span data-stu-id="f649e-128">nook, took</span></span>     |
| <span data-ttu-id="f649e-129">[ ]</span><span class="sxs-lookup"><span data-stu-id="f649e-129">[ ]</span></span>      | <span data-ttu-id="f649e-130">Komt overeen met de opgegeven tekens</span><span class="sxs-lookup"><span data-stu-id="f649e-130">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="f649e-131">Book, Nook</span><span class="sxs-lookup"><span data-stu-id="f649e-131">book, nook</span></span>       | <span data-ttu-id="f649e-132">Cook, zoeken</span><span class="sxs-lookup"><span data-stu-id="f649e-132">cook, look</span></span>     |

<span data-ttu-id="f649e-133">Wanneer u cmdlets ontwerpt die ondersteuning bieden voor joker tekens, toestaan combi Naties van joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f649e-133">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="f649e-134">De volgende opdracht gebruikt de `Get-ChildItem` cmdlet bijvoorbeeld om alle txt-bestanden op te halen die zich in de map c:\Techdocs bevinden en die beginnen met de letters ' a ' tot en met ' l '.</span><span class="sxs-lookup"><span data-stu-id="f649e-134">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="f649e-135">In de vorige opdracht wordt het bereik Joker teken gebruikt `[a-l]` om op te geven dat de bestands naam moet beginnen met de tekens ' a ' tot en met ' l ' en het `*` Joker teken als tijdelijke aanduiding gebruikt voor tekens tussen de eerste letter van de bestands naam en de extensie **. txt** .</span><span class="sxs-lookup"><span data-stu-id="f649e-135">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="f649e-136">In het volgende voor beeld wordt een Joker teken voor een bereik gebruikt dat de letter ' d ' uitsluit, maar alle andere letters van ' a ' tot en met ' f ' bevat.</span><span class="sxs-lookup"><span data-stu-id="f649e-136">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="f649e-137">Letterlijke tekens afhandelen in Joker teken patronen</span><span class="sxs-lookup"><span data-stu-id="f649e-137">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="f649e-138">Als het Joker teken dat u opgeeft letterlijke tekens bevat die niet mogen worden interpretted als joker tekens, gebruikt u het apostroffen-teken ( `` ` `` ) als escape-teken.</span><span class="sxs-lookup"><span data-stu-id="f649e-138">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="f649e-139">Wanneer u letterlijke tekens int de Power shell-API opgeeft, gebruikt u één apostroffen.</span><span class="sxs-lookup"><span data-stu-id="f649e-139">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="f649e-140">Wanneer u letterlijke tekens opgeeft bij de Power shell-opdracht prompt, gebruikt u twee accents graves.</span><span class="sxs-lookup"><span data-stu-id="f649e-140">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="f649e-141">Het volgende patroon bevat bijvoorbeeld twee haken die letterlijk moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f649e-141">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="f649e-142">Bij gebruik in de API voor Power shell:</span><span class="sxs-lookup"><span data-stu-id="f649e-142">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="f649e-143">"John Smith \` [\* ']"</span><span class="sxs-lookup"><span data-stu-id="f649e-143">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="f649e-144">Bij gebruik van de Power shell-opdracht prompt:</span><span class="sxs-lookup"><span data-stu-id="f649e-144">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="f649e-145">"John Smith \` \` [\* \` ']"</span><span class="sxs-lookup"><span data-stu-id="f649e-145">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="f649e-146">Dit patroon komt overeen met ' John Smith [marketing] ' of ' John Smith [development] '.</span><span class="sxs-lookup"><span data-stu-id="f649e-146">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="f649e-147">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f649e-147">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="f649e-148">Uitvoer van de cmdlet en Joker tekens</span><span class="sxs-lookup"><span data-stu-id="f649e-148">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="f649e-149">Wanneer cmdlet-para meters ondersteuning bieden voor joker tekens, genereert de bewerking meestal een matrix uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f649e-149">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="f649e-150">In sommige gevallen is het niet zinvol om een matrix uitvoer te ondersteunen, omdat de gebruiker slechts één item kan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f649e-150">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="f649e-151">De `Set-Location` cmdlet biedt bijvoorbeeld geen ondersteuning voor matrix uitvoer omdat de gebruiker slechts één locatie instelt.</span><span class="sxs-lookup"><span data-stu-id="f649e-151">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="f649e-152">In dit geval ondersteunt de cmdlet nog steeds joker tekens, maar worden oplossingen op één locatie afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="f649e-152">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="f649e-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f649e-153">See Also</span></span>

[<span data-ttu-id="f649e-154">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="f649e-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="f649e-155">Klasse WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="f649e-155">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
