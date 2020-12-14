---
description: Hierin worden eenvoudiger, effectievere manieren voor het uitvoeren van script filters voor verzamelingen van objecten beschreven.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: dbd30d566414f784e7d5eca04af716c2bf1642b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706208"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="f8177-103">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="f8177-103">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="f8177-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f8177-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f8177-105">Hierin worden eenvoudiger, effectievere manieren voor het uitvoeren van script filters voor verzamelingen van objecten beschreven.</span><span class="sxs-lookup"><span data-stu-id="f8177-105">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="f8177-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f8177-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="f8177-107">Dankzij de vereenvoudigde syntaxis, geïntroduceerd in Windows Power Shell 3,0, kunt u bepaalde filter opdrachten maken zonder gebruik te maken van script blokken.</span><span class="sxs-lookup"><span data-stu-id="f8177-107">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="f8177-108">De vereenvoudigde syntaxis lijkt sterk op natuurlijke taal en is vooral nuttig voor verzamelingen van objecten die in opdrachten worden weer gegeven `Where-Object` en `ForEach-Object` de bijbehorende aliassen `where` en `foreach` .</span><span class="sxs-lookup"><span data-stu-id="f8177-108">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="f8177-109">U kunt een methode gebruiken voor de leden van een verzameling (meestal een matrix) zonder te verwijzen naar de automatische variabele `$_` in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="f8177-109">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="f8177-110">Houd rekening met de volgende twee aanroepen:</span><span class="sxs-lookup"><span data-stu-id="f8177-110">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="f8177-111">Standaard syntaxis</span><span class="sxs-lookup"><span data-stu-id="f8177-111">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="f8177-112">Vereenvoudigde syntaxis</span><span class="sxs-lookup"><span data-stu-id="f8177-112">Simplified syntax</span></span>

<span data-ttu-id="f8177-113">Onder de vereenvoudigde syntaxis worden vergelijkings operatoren die werken aan leden van objecten in een verzameling beschouwd als para meters.</span><span class="sxs-lookup"><span data-stu-id="f8177-113">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="f8177-114">U kunt een methode aanroepen voor objecten in een verzameling zonder te verwijzen naar de automatische variabele `$_` in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="f8177-114">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="f8177-115">Vergelijk de volgende twee aanroepen met die van het vorige voor beeld:</span><span class="sxs-lookup"><span data-stu-id="f8177-115">Compare the following two invocations to those of the previous example:</span></span>

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="f8177-116">Hoewel beide syntaxis werken, retourneert de vereenvoudigde syntaxis resultaten zonder te verwijzen naar de automatische variabele `$_` in een-script blok.</span><span class="sxs-lookup"><span data-stu-id="f8177-116">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="f8177-117">De naam van de methode `GetKeyAlgorithm` wordt behandeld als een para meter van `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="f8177-117">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="f8177-118">De tweede opdracht retourneert dezelfde resultaten, maar zonder fouten, omdat de vereenvoudigde syntaxis niet probeert resultaten te retour neren voor items waarvoor het opgegeven argument niet is toegepast.</span><span class="sxs-lookup"><span data-stu-id="f8177-118">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="f8177-119">In dit voor beeld `Process` wordt de eigenschap `Description` door gegeven als para meter voor de lidnaam aan de `ForEach-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f8177-119">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="f8177-120">De resultaten zijn beschrijvingen van actieve processen.</span><span class="sxs-lookup"><span data-stu-id="f8177-120">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="f8177-121">In dit voor beeld wordt de- `DirectoryInfo` methode `GetFiles` door gegeven als de para meter voor de lidnaam van de `ForEach-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f8177-121">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="f8177-122">De methode wordt aangeroepen met de zoek patroon parameter `.*` .</span><span class="sxs-lookup"><span data-stu-id="f8177-122">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="f8177-123">De resultaten zijn `FileInfo` records voor alle verborgen UNIX-bestanden in de basis mappen van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="f8177-123">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="f8177-124">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="f8177-124">SEE ALSO</span></span>

- [<span data-ttu-id="f8177-125">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="f8177-125">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="f8177-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="f8177-126">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="f8177-127">Where-object</span><span class="sxs-lookup"><span data-stu-id="f8177-127">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="f8177-128">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="f8177-128">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

