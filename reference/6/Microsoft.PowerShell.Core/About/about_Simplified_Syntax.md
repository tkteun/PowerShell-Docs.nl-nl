---
description: Hierin worden eenvoudiger, effectievere manieren voor het uitvoeren van script filters voor verzamelingen van objecten beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: d2e603b4d2092d4ba4ed9c1d7253991cc34ddca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252217"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="99365-104">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="99365-104">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="99365-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99365-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="99365-106">Hierin worden eenvoudiger, effectievere manieren voor het uitvoeren van script filters voor verzamelingen van objecten beschreven.</span><span class="sxs-lookup"><span data-stu-id="99365-106">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="99365-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99365-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="99365-108">Dankzij de vereenvoudigde syntaxis, geïntroduceerd in Windows Power Shell 3,0, kunt u bepaalde filter opdrachten maken zonder gebruik te maken van script blokken.</span><span class="sxs-lookup"><span data-stu-id="99365-108">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="99365-109">De vereenvoudigde syntaxis lijkt sterk op natuurlijke taal en is vooral nuttig voor verzamelingen van objecten die in opdrachten worden weer gegeven `Where-Object` en `ForEach-Object` de bijbehorende aliassen `where` en `foreach` .</span><span class="sxs-lookup"><span data-stu-id="99365-109">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="99365-110">U kunt een methode gebruiken voor de leden van een verzameling (meestal een matrix) zonder te verwijzen naar de automatische variabele `$_` in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="99365-110">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="99365-111">Houd rekening met de volgende twee aanroepen:</span><span class="sxs-lookup"><span data-stu-id="99365-111">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="99365-112">Standaard syntaxis</span><span class="sxs-lookup"><span data-stu-id="99365-112">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="99365-113">Vereenvoudigde syntaxis</span><span class="sxs-lookup"><span data-stu-id="99365-113">Simplified syntax</span></span>

<span data-ttu-id="99365-114">Onder de vereenvoudigde syntaxis worden vergelijkings operatoren die werken aan leden van objecten in een verzameling beschouwd als para meters.</span><span class="sxs-lookup"><span data-stu-id="99365-114">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="99365-115">U kunt een methode aanroepen voor objecten in een verzameling zonder te verwijzen naar de automatische variabele `$_` in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="99365-115">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="99365-116">Vergelijk de volgende twee aanroepen met die van het vorige voor beeld:</span><span class="sxs-lookup"><span data-stu-id="99365-116">Compare the following two invocations to those of the previous example:</span></span>
```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="99365-117">Hoewel beide syntaxis werken, retourneert de vereenvoudigde syntaxis resultaten zonder te verwijzen naar de automatische variabele `$_` in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="99365-117">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="99365-118">De naam van de methode `GetKeyAlgorithm` wordt behandeld als een para meter van `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="99365-118">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="99365-119">De tweede opdracht retourneert dezelfde resultaten, maar zonder fouten, omdat de vereenvoudigde syntaxis niet probeert resultaten te retour neren voor items waarvoor het opgegeven argument niet is toegepast.</span><span class="sxs-lookup"><span data-stu-id="99365-119">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="99365-120">In dit voor beeld `Process` wordt de eigenschap `Description` door gegeven als para meter voor de lidnaam aan de `ForEach-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="99365-120">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="99365-121">De resultaten zijn beschrijvingen van actieve processen.</span><span class="sxs-lookup"><span data-stu-id="99365-121">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="99365-122">In dit voor beeld wordt de- `DirectoryInfo` methode `GetFiles` door gegeven als de para meter voor de lidnaam van de `ForEach-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="99365-122">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="99365-123">De methode wordt aangeroepen met de zoek patroon parameter `.*` .</span><span class="sxs-lookup"><span data-stu-id="99365-123">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="99365-124">De resultaten zijn `FileInfo` records voor alle verborgen UNIX-bestanden in de basis mappen van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="99365-124">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="99365-125">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="99365-125">SEE ALSO</span></span>

- [<span data-ttu-id="99365-126">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="99365-126">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="99365-127">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="99365-127">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="99365-128">Where-object</span><span class="sxs-lookup"><span data-stu-id="99365-128">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="99365-129">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="99365-129">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
