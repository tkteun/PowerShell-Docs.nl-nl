---
description: Introduceert geavanceerde functies waarmee u cmdlets kunt maken met behulp van scripts.
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: a0b8b027c91f2adedfcecd07bfc80392c1b1e071
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705524"
---
# <a name="about-functions-advanced"></a><span data-ttu-id="fe1a1-103">Over functies Geavanceerd</span><span class="sxs-lookup"><span data-stu-id="fe1a1-103">About Functions Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="fe1a1-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fe1a1-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="fe1a1-105">Introduceert geavanceerde functies waarmee u cmdlets kunt maken met behulp van scripts.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-105">Introduces advanced functions that are a way to create cmdlets using scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="fe1a1-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fe1a1-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="fe1a1-107">Een cmdlet is één opdracht die deel uitmaakt van de pijplijn semantiek van Power shell.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-107">A cmdlet is a single command that participates in the pipeline semantics of PowerShell.</span></span> <span data-ttu-id="fe1a1-108">Dit omvat binaire cmdlets, geavanceerde script functies, CDXML en werk stromen.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-108">This includes binary cmdlets, advanced script functions, CDXML, and Workflows.</span></span>

<span data-ttu-id="fe1a1-109">Met geavanceerde functies kunt u cmdlets maken die zijn geschreven als een Power shell-functie.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-109">Advanced functions allow you create cmdlets that are written as a PowerShell function.</span></span> <span data-ttu-id="fe1a1-110">Geavanceerde functies maken het gemakkelijker om cmdlets te maken zonder dat ze een binaire cmdlet hoeven te schrijven en te compileren.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-110">Advanced functions make it easier to create cmdlets without having to write and compile a binary cmdlet.</span></span> <span data-ttu-id="fe1a1-111">Binaire cmdlets zijn .NET-klassen die zijn geschreven in een .NET-taal, zoals C#.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-111">Binary cmdlets are .NET classes that are written in a .NET language such as C#.</span></span>

<span data-ttu-id="fe1a1-112">Geavanceerde functies gebruiken het `CmdletBinding` kenmerk om ze te identificeren als functies die fungeren als-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-112">Advanced functions use the `CmdletBinding` attribute to identify them as functions that act like cmdlets.</span></span> <span data-ttu-id="fe1a1-113">Het `CmdletBinding` kenmerk is vergelijkbaar met het cmdlet-kenmerk dat wordt gebruikt in gecompileerde cmdlet-klassen om de klasse als een cmdlet te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-113">The `CmdletBinding` attribute is similar to the Cmdlet attribute that is used in compiled cmdlet classes to identify the class as a cmdlet.</span></span> <span data-ttu-id="fe1a1-114">Zie [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)voor meer informatie over dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-114">For more information about this attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="fe1a1-115">In het volgende voor beeld ziet u een functie die een naam accepteert en vervolgens een begroeting afdrukt met de opgegeven naam.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-115">The following example shows a function that accepts a name and then prints a greeting using the supplied name.</span></span> <span data-ttu-id="fe1a1-116">U ziet ook dat deze functie een naam definieert die een paar woorden (verzenden) en een zelfstandig naam woord (Greeting) bevat, zoals het combi neren van woorden en zelfstandigen van een gecompileerde cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-116">Also notice that this function defines a name that includes a verb (Send) and noun (Greeting) pair like the verb-noun pair of a compiled cmdlet.</span></span> <span data-ttu-id="fe1a1-117">Functies zijn echter niet vereist voor het maken van een naam van een woorden groep.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-117">However, functions are not required to have a verb-noun name.</span></span>

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

<span data-ttu-id="fe1a1-118">De para meters van de functie worden gedeclareerd met behulp van het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-118">The parameters of the function are declared by using the Parameter attribute.</span></span>
<span data-ttu-id="fe1a1-119">Dit kenmerk kan alleen worden gebruikt, of het kan worden gecombineerd met het alias kenmerk of met verschillende kenmerken voor de validatie van de para meters.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-119">This attribute can be used alone, or it can be combined with the Alias attribute or with several other parameter validation attributes.</span></span> <span data-ttu-id="fe1a1-120">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over het declareren van para meters (inclusief dynamische para meters die tijdens runtime worden toegevoegd).</span><span class="sxs-lookup"><span data-stu-id="fe1a1-120">For more information about how to declare parameters (including dynamic parameters that are added at runtime), see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

<span data-ttu-id="fe1a1-121">Het werkelijke werk van de functie Previous wordt uitgevoerd in het proces blok, wat gelijk is aan de methode ProcessingRecord die wordt gebruikt door gecompileerde cmdlets voor het verwerken van de gegevens die worden door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-121">The actual work of the previous function is performed in the Process block, which is equivalent to the ProcessingRecord method that is used by compiled cmdlets to process the data that is passed to the cmdlet.</span></span> <span data-ttu-id="fe1a1-122">Dit blok, samen met de begin-en eind blokken, wordt beschreven in het onderwerp [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) .</span><span class="sxs-lookup"><span data-stu-id="fe1a1-122">This block, along with the Begin and End blocks, is described in the [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) topic.</span></span>

<span data-ttu-id="fe1a1-123">Geavanceerde functies verschillen op de volgende manieren van gecompileerde cmdlets:</span><span class="sxs-lookup"><span data-stu-id="fe1a1-123">Advanced functions differ from compiled cmdlets in the following ways:</span></span>

- <span data-ttu-id="fe1a1-124">Met een geavanceerde functie parameter binding wordt geen uitzonde ring gegenereerd wanneer een matrix met teken reeksen is gebonden aan een Boole-para meter.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-124">Advanced function parameter binding does not throw an exception when an array of strings is bound to a Boolean parameter.</span></span>
- <span data-ttu-id="fe1a1-125">Het kenmerk validate en het kenmerk ValidatePattern kunnen geen benoemde para meters door geven.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-125">The ValidateSet attribute and the ValidatePattern attribute cannot pass named parameters.</span></span>
- <span data-ttu-id="fe1a1-126">Geavanceerde functies kunnen niet worden gebruikt in trans acties.</span><span class="sxs-lookup"><span data-stu-id="fe1a1-126">Advanced functions cannot be used in transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe1a1-127">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="fe1a1-127">SEE ALSO</span></span>

[<span data-ttu-id="fe1a1-128">about_Functions</span><span class="sxs-lookup"><span data-stu-id="fe1a1-128">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="fe1a1-129">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="fe1a1-129">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="fe1a1-130">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="fe1a1-130">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="fe1a1-131">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="fe1a1-131">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="fe1a1-132">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="fe1a1-132">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
