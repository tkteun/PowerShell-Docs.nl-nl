---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 098e98dec6733af036795e4decb633f59d40c633
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249234"
---
# <span data-ttu-id="27806-103">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="27806-103">Get-UICulture</span></span>

## <span data-ttu-id="27806-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="27806-104">SYNOPSIS</span></span>
<span data-ttu-id="27806-105">Hiermee worden de huidige instellingen voor de GEBRUIKERSINTERFACE cultuur in het besturings systeem opgehaald.</span><span class="sxs-lookup"><span data-stu-id="27806-105">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="27806-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="27806-106">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="27806-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="27806-107">DESCRIPTION</span></span>
<span data-ttu-id="27806-108">De cmdlet **Get-uiCulture** haalt informatie op over de huidige instellingen voor de cultuur van gebruikers interface (UI) voor Windows.</span><span class="sxs-lookup"><span data-stu-id="27806-108">The **Get-UICulture** cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="27806-109">De GEBRUIKERSINTERFACE cultuur bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.</span><span class="sxs-lookup"><span data-stu-id="27806-109">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="27806-110">U kunt ook de cmdlet Get-Culture gebruiken, waarmee de huidige cultuur op het systeem wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="27806-110">You can also use the Get-Culture cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="27806-111">De cultuur bepaalt de weergave opmaak van items zoals getallen, valuta en datums.</span><span class="sxs-lookup"><span data-stu-id="27806-111">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="27806-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="27806-112">EXAMPLES</span></span>

### <span data-ttu-id="27806-113">Voor beeld 1: de UI-cultuur ophalen</span><span class="sxs-lookup"><span data-stu-id="27806-113">Example 1: Get the UI culture</span></span>

```
PS C:\> Get-UICulture
```

<span data-ttu-id="27806-114">Met deze opdracht wordt de huidige UI-cultuur gegevens opgehaald.</span><span class="sxs-lookup"><span data-stu-id="27806-114">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="27806-115">Voor beeld 2: de UI-cultuur ophalen en de resultaten opmaken</span><span class="sxs-lookup"><span data-stu-id="27806-115">Example 2: Get the UI culture and format the results</span></span>

```
PS C:\> Get-UICulture | Format-List *
```

<span data-ttu-id="27806-116">Met deze opdracht worden de waarden van alle eigenschappen van de huidige GEBRUIKERSINTERFACE cultuur in een lijst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27806-116">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="27806-117">Voor beeld 3: de waarde van de eigenschap Calendar ophalen</span><span class="sxs-lookup"><span data-stu-id="27806-117">Example 3: Get the value of the Calendar property</span></span>

```
PS C:\> (Get-UICulture).Calendar
```

<span data-ttu-id="27806-118">Met deze opdracht worden de huidige waarden weer gegeven voor de eigenschap Calendar van de huidige GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="27806-118">This command displays the current values for the Calendar property of the current UI culture.</span></span>
<span data-ttu-id="27806-119">Calendar is slechts één eigenschap van UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="27806-119">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="27806-120">Als u alle eigenschappen wilt weer geven, typt u `Get-UICulture | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="27806-120">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="27806-121">Voor beeld 4: het korte datum patroon ophalen</span><span class="sxs-lookup"><span data-stu-id="27806-121">Example 4: Get the short date pattern</span></span>

```
PS C:\> (Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="27806-122">Met deze opdracht wordt het korte datum patroon voor de huidige GEBRUIKERSINTERFACE cultuur weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27806-122">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="27806-123">Als u alle subeigenschappen van de eigenschap date time format van de UI-cultuur wilt weer geven, typt u `(Get-UICulture).DateTimeFormat | gm` .</span><span class="sxs-lookup"><span data-stu-id="27806-123">To see all of the subproperties of the DateTimeFormat property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="27806-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27806-124">PARAMETERS</span></span>

### <span data-ttu-id="27806-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27806-125">CommonParameters</span></span>
<span data-ttu-id="27806-126">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27806-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27806-127">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="27806-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27806-128">INVOER</span><span class="sxs-lookup"><span data-stu-id="27806-128">INPUTS</span></span>

### <span data-ttu-id="27806-129">Geen</span><span class="sxs-lookup"><span data-stu-id="27806-129">None</span></span>
<span data-ttu-id="27806-130">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27806-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="27806-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="27806-131">OUTPUTS</span></span>

### <span data-ttu-id="27806-132">System. Globalization. Culture info, micro soft. Power shell. VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="27806-132">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>
<span data-ttu-id="27806-133">**Get-uiCulture** retourneert een object dat de huidige gebruikersinterface cultuur vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="27806-133">**Get-UICulture** returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="27806-134">In Windows Power Shell 3,0 wordt een **Culture info** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="27806-134">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="27806-135">In Windows Power Shell 2,0 wordt een **VistaCultureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="27806-135">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="27806-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="27806-136">NOTES</span></span>

* <span data-ttu-id="27806-137">U kunt ook de variabelen $PsCulture en $PsUICulture gebruiken.</span><span class="sxs-lookup"><span data-stu-id="27806-137">You can also use the $PsCulture and $PsUICulture variables.</span></span> <span data-ttu-id="27806-138">De variabele $PsCulture slaat de naam op van de huidige cultuur en de $PsUICulture variabele bevat de naam van de huidige GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="27806-138">The $PsCulture variable stores the name of the current culture, and the $PsUICulture variable stores the name of the current UI culture.</span></span>

*

## <span data-ttu-id="27806-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="27806-139">RELATED LINKS</span></span>

## <span data-ttu-id="27806-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="27806-140">RELATED LINKS</span></span>
