---
description: Hierin wordt beschreven hoe u in geavanceerde functies parameter sets definieert en gebruikt.
ms.date: 02/11/2020
title: about_Parameter_Sets
ms.openlocfilehash: 405ef1c70b49f703f17a9e76f899a9643cc065bc
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917871"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="b7261-103">Over parameter sets</span><span class="sxs-lookup"><span data-stu-id="b7261-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="b7261-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b7261-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b7261-105">Hierin wordt beschreven hoe u in geavanceerde functies parameter sets definieert en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b7261-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="b7261-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b7261-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b7261-107">Power shell gebruikt parameter sets waarmee u één functie kunt schrijven die verschillende acties voor verschillende scenario's kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b7261-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="b7261-108">Met parameter sets kunt u verschillende para meters voor de gebruiker beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="b7261-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="b7261-109">En om andere informatie te retour neren op basis van de para meters die door de gebruiker zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b7261-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="b7261-110">Vereisten voor de parameterset</span><span class="sxs-lookup"><span data-stu-id="b7261-110">Parameter set requirements</span></span>

<span data-ttu-id="b7261-111">De volgende vereisten zijn van toepassing op alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="b7261-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="b7261-112">Elke parameterset moet een unieke combi natie van para meters hebben.</span><span class="sxs-lookup"><span data-stu-id="b7261-112">Each parameter set must have a unique combination of parameters.</span></span> <span data-ttu-id="b7261-113">Indien mogelijk moet ten minste één van de unieke para meters een verplichte para meter zijn.</span><span class="sxs-lookup"><span data-stu-id="b7261-113">If possible, at least one of the unique parameters should be a mandatory parameter.</span></span>

- <span data-ttu-id="b7261-114">Een parameterset met meerdere positionele para meters moet unieke posities definiëren voor elke para meter.</span><span class="sxs-lookup"><span data-stu-id="b7261-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="b7261-115">Er kunnen niet twee positionele para meters dezelfde positie opgeven.</span><span class="sxs-lookup"><span data-stu-id="b7261-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="b7261-116">Slechts één para meter in een set kan het `ValueFromPipeline` tref woord declareren met een waarde van `true` .</span><span class="sxs-lookup"><span data-stu-id="b7261-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="b7261-117">Meerdere para meters kunnen het `ValueFromPipelineByPropertyName` sleutel woord definiëren met een waarde van `true` .</span><span class="sxs-lookup"><span data-stu-id="b7261-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="b7261-118">Als er geen parameterset voor een para meter is opgegeven, hoort de para meter bij alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="b7261-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="b7261-119">Er is een limiet van 32 parameter sets.</span><span class="sxs-lookup"><span data-stu-id="b7261-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="b7261-120">Standaard parameters sets</span><span class="sxs-lookup"><span data-stu-id="b7261-120">Default parameter sets</span></span>

<span data-ttu-id="b7261-121">Als er meerdere parameter sets zijn gedefinieerd, `DefaultParameterSetName` geeft het sleutel woord van het kenmerk **CmdletBinding** de standaard parameterset.</span><span class="sxs-lookup"><span data-stu-id="b7261-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="b7261-122">Power shell gebruikt de standaard parameterset wanneer de ingestelde para meter niet kan worden bepaald op basis van de gegevens die aan de opdracht worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7261-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="b7261-123">Zie [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md)voor meer informatie over het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="b7261-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="b7261-124">Parameter sets declareren</span><span class="sxs-lookup"><span data-stu-id="b7261-124">Declaring parameter sets</span></span>

<span data-ttu-id="b7261-125">Als u een parameterset wilt maken, moet u het `ParameterSetName` tref woord van het **parameter** kenmerk voor elke para meter in de parameterset opgeven.</span><span class="sxs-lookup"><span data-stu-id="b7261-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="b7261-126">Voor para meters die bij meerdere parameter sets horen, voegt u een **parameter** kenmerk toe voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="b7261-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="b7261-127">Met het **parameter** kenmerk kunt u de para meter op verschillende manieren definiëren voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="b7261-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="b7261-128">U kunt bijvoorbeeld een para meter definiëren als verplicht in de ene set en optioneel in een andere.</span><span class="sxs-lookup"><span data-stu-id="b7261-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="b7261-129">Elke parameterset moet echter ten minste één unieke para meter bevatten.</span><span class="sxs-lookup"><span data-stu-id="b7261-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="b7261-130">Para meters die geen toegewezen parameterset naam hebben, behoren tot alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="b7261-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="b7261-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b7261-131">Example</span></span>

<span data-ttu-id="b7261-132">De volgende voorbeeld functie telt de nummer regels, tekens en woorden in een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="b7261-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="b7261-133">Met para meters kunt u opgeven welke waarden u wilt retour neren en welke bestanden u wilt meten.</span><span class="sxs-lookup"><span data-stu-id="b7261-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="b7261-134">Er zijn vier parameters sets gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="b7261-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="b7261-135">Pad</span><span class="sxs-lookup"><span data-stu-id="b7261-135">Path</span></span>
- <span data-ttu-id="b7261-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="b7261-136">PathAll</span></span>
- <span data-ttu-id="b7261-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7261-137">LiteralPath</span></span>
- <span data-ttu-id="b7261-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="b7261-138">LiteralPathAll</span></span>

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

<span data-ttu-id="b7261-139">Elke parameterset moet een unieke para meter of een unieke combi natie van para meters hebben.</span><span class="sxs-lookup"><span data-stu-id="b7261-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="b7261-140">De `Path` `PathAll` para meters en zijn vergelijkbaar, maar de para meter **all** is uniek voor de `PathAll` parameterset.</span><span class="sxs-lookup"><span data-stu-id="b7261-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="b7261-141">Hetzelfde geldt voor de `LiteralPath` `LiteralPathAll` para meters en.</span><span class="sxs-lookup"><span data-stu-id="b7261-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="b7261-142">Hoewel de para `PathAll` meter en `LiteralPathAll` beide de para meter **all** hebben, worden deze door de para meters **Path** en **LiteralPath** onderscheiden.</span><span class="sxs-lookup"><span data-stu-id="b7261-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="b7261-143">Gebruik `Get-Command -Syntax` toont de syntaxis van elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="b7261-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="b7261-144">De naam van de parameterset wordt echter niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7261-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="b7261-145">In het volgende voor beeld ziet u welke para meters in elke parameterset kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b7261-145">The following example shows which parameters can be used in each parameter set.</span></span>

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a><span data-ttu-id="b7261-146">Parameter sets in actie</span><span class="sxs-lookup"><span data-stu-id="b7261-146">Parameter sets in action</span></span>

<span data-ttu-id="b7261-147">In dit voor beeld gebruiken we de `PathAll` para meter set.</span><span class="sxs-lookup"><span data-stu-id="b7261-147">In this example, we are using the `PathAll` parameter set.</span></span>

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```

