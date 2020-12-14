---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 4bd912db3f86ffa8b495faf3e62259f207340938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705819"
---
# <span data-ttu-id="0a8f3-102">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="0a8f3-102">Get-UICulture</span></span>

## <span data-ttu-id="0a8f3-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0a8f3-103">SYNOPSIS</span></span>
<span data-ttu-id="0a8f3-104">Hiermee worden de huidige instellingen voor de GEBRUIKERSINTERFACE cultuur in het besturings systeem opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-104">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="0a8f3-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0a8f3-105">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="0a8f3-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0a8f3-106">DESCRIPTION</span></span>

<span data-ttu-id="0a8f3-107">De `Get-UICulture` cmdlet haalt informatie op over de huidige instellingen voor de cultuur van gebruikers interface (UI) voor Windows.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-107">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="0a8f3-108">De GEBRUIKERSINTERFACE cultuur bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-108">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="0a8f3-109">U kunt ook de `Get-Culture` cmdlet gebruiken, waarmee de huidige cultuur op het systeem wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-109">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="0a8f3-110">De cultuur bepaalt de weergave opmaak van items zoals getallen, valuta en datums.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-110">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="0a8f3-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0a8f3-111">EXAMPLES</span></span>

### <span data-ttu-id="0a8f3-112">Voor beeld 1: de UI-cultuur ophalen</span><span class="sxs-lookup"><span data-stu-id="0a8f3-112">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="0a8f3-113">Met deze opdracht wordt de huidige UI-cultuur gegevens opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-113">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="0a8f3-114">Voor beeld 2: de UI-cultuur ophalen en de resultaten opmaken</span><span class="sxs-lookup"><span data-stu-id="0a8f3-114">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="0a8f3-115">Met deze opdracht worden de waarden van alle eigenschappen van de huidige GEBRUIKERSINTERFACE cultuur in een lijst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-115">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="0a8f3-116">Voor beeld 3: de waarde van de eigenschap Calendar ophalen</span><span class="sxs-lookup"><span data-stu-id="0a8f3-116">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="0a8f3-117">Met deze opdracht worden de huidige waarden weer gegeven voor de eigenschap **Calendar** van de huidige gebruikersinterface cultuur.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-117">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="0a8f3-118">Calendar is slechts één eigenschap van UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-118">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="0a8f3-119">Als u alle eigenschappen wilt weer geven, typt u `Get-UICulture | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="0a8f3-119">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="0a8f3-120">Voor beeld 4: het korte datum patroon ophalen</span><span class="sxs-lookup"><span data-stu-id="0a8f3-120">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="0a8f3-121">Met deze opdracht wordt het korte datum patroon voor de huidige GEBRUIKERSINTERFACE cultuur weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-121">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="0a8f3-122">Als u alle subeigenschappen van de eigenschap **date time format** van de UI-cultuur wilt weer geven, typt u `(Get-UICulture).DateTimeFormat | gm` .</span><span class="sxs-lookup"><span data-stu-id="0a8f3-122">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="0a8f3-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a8f3-123">PARAMETERS</span></span>

### <span data-ttu-id="0a8f3-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a8f3-124">CommonParameters</span></span>

<span data-ttu-id="0a8f3-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a8f3-126">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0a8f3-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="0a8f3-127">INPUTS</span></span>

### <span data-ttu-id="0a8f3-128">Geen</span><span class="sxs-lookup"><span data-stu-id="0a8f3-128">None</span></span>

<span data-ttu-id="0a8f3-129">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-129">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0a8f3-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0a8f3-130">OUTPUTS</span></span>

### <span data-ttu-id="0a8f3-131">System. Globalization. Culture info, micro soft. Power shell. VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="0a8f3-131">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="0a8f3-132">`Get-UICulture` retourneert een object dat de huidige GEBRUIKERSINTERFACE cultuur vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-132">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="0a8f3-133">In Windows Power Shell 3,0 wordt een **Culture info** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-133">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="0a8f3-134">In Windows Power Shell 2,0 wordt een **VistaCultureInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-134">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="0a8f3-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0a8f3-135">NOTES</span></span>

- <span data-ttu-id="0a8f3-136">U kunt ook de `$PsCulture` variabelen en gebruiken `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="0a8f3-136">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="0a8f3-137">De `$PsCulture` variabele bevat de naam van de huidige cultuur en de `$PsUICulture` variabele bevat de naam van de huidige gebruikersinterface cultuur.</span><span class="sxs-lookup"><span data-stu-id="0a8f3-137">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="0a8f3-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0a8f3-138">RELATED LINKS</span></span>

