---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: f2b3e20685ee52a7f9ca1bfd23af5fc5bca24001
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705924"
---
# <span data-ttu-id="f51aa-102">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="f51aa-102">Out-Printer</span></span>

## <span data-ttu-id="f51aa-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f51aa-103">SYNOPSIS</span></span>
<span data-ttu-id="f51aa-104">Hiermee wordt uitvoer naar een printer verzonden.</span><span class="sxs-lookup"><span data-stu-id="f51aa-104">Sends output to a printer.</span></span>

## <span data-ttu-id="f51aa-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f51aa-105">SYNTAX</span></span>

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="f51aa-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f51aa-106">DESCRIPTION</span></span>

<span data-ttu-id="f51aa-107">De `Out-Printer` cmdlet verzendt uitvoer naar de standaard printer of naar een andere printer, als deze is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f51aa-107">The `Out-Printer` cmdlet sends output to the default printer or to an alternate printer, if one is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="f51aa-108">Deze cmdlet is opnieuw geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="f51aa-108">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="f51aa-109">Deze cmdlet is alleen beschikbaar op Windows-systemen die ondersteuning bieden voor het Windows-bureau blad.</span><span class="sxs-lookup"><span data-stu-id="f51aa-109">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="f51aa-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f51aa-110">EXAMPLES</span></span>

### <span data-ttu-id="f51aa-111">Voor beeld 1: een bestand verzenden dat moet worden afgedrukt op de standaard printer</span><span class="sxs-lookup"><span data-stu-id="f51aa-111">Example 1 - Send a file to be printed on the default printer</span></span>

<span data-ttu-id="f51aa-112">In dit voor beeld ziet u hoe u een bestand afdrukt, zelfs als dit `Out-Printer` geen **pad** -para meter heeft.</span><span class="sxs-lookup"><span data-stu-id="f51aa-112">This example shows how to print a file, even though `Out-Printer` does not have a **Path** parameter.</span></span>

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

<span data-ttu-id="f51aa-113">`Get-Content`Hiermee wordt de inhoud van het `readme.txt` bestand in de huidige map opgehaald en `Out-Printer` verzonden naar de standaard printer.</span><span class="sxs-lookup"><span data-stu-id="f51aa-113">`Get-Content`gets the contents of the `readme.txt` file in the current directory and pipes it to `Out-Printer`, which sends it to the default printer.</span></span>

### <span data-ttu-id="f51aa-114">Voor beeld 2: een teken reeks naar een externe printer afdrukken</span><span class="sxs-lookup"><span data-stu-id="f51aa-114">Example 2: Print a string to a remote printer</span></span>

<span data-ttu-id="f51aa-115">In dit voor beeld wordt `Hello, World` de **PRT-6b Color-** printer op Server01 afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="f51aa-115">This example prints `Hello, World` to the **Prt-6B Color** printer on Server01.</span></span>

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

<span data-ttu-id="f51aa-116">De para meter **name** selecteert een specifieke printer in plaats van de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="f51aa-116">The **Name** parameter selects a specific printer, rather than the default.</span></span>

### <span data-ttu-id="f51aa-117">Voor beeld 3: een Help-onderwerp naar de standaard printer afdrukken</span><span class="sxs-lookup"><span data-stu-id="f51aa-117">Example 3 - Print a help topic to the default printer</span></span>

<span data-ttu-id="f51aa-118">In dit voor beeld wordt de volledige versie van het Help-onderwerp voor beschreven `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="f51aa-118">This example prints the full version of the Help topic for `Get-CimInstance`.</span></span>

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

<span data-ttu-id="f51aa-119">`Get-Help` Hiermee haalt u de volledige versie van het Help-onderwerp op `Get-CimInstance` en slaat u deze op in de `$H` variabele.</span><span class="sxs-lookup"><span data-stu-id="f51aa-119">`Get-Help` gets the full version of the Help topic for `Get-CimInstance` and stores it in the `$H` variable.</span></span> <span data-ttu-id="f51aa-120">De para meter **input object** geeft de waarde `$H` aan van to `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="f51aa-120">The **InputObject** parameter passes the value of `$H` to `Out-Printer`.</span></span>

## <span data-ttu-id="f51aa-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f51aa-121">PARAMETERS</span></span>

### <span data-ttu-id="f51aa-122">-Input object</span><span class="sxs-lookup"><span data-stu-id="f51aa-122">-InputObject</span></span>

<span data-ttu-id="f51aa-123">Hiermee geeft u de objecten die naar de printer moeten worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="f51aa-123">Specifies the objects to be sent to the printer.</span></span> <span data-ttu-id="f51aa-124">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f51aa-124">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f51aa-125">-Name</span><span class="sxs-lookup"><span data-stu-id="f51aa-125">-Name</span></span>

<span data-ttu-id="f51aa-126">Hiermee wordt de uitvoer naar de opgegeven printer verzonden.</span><span class="sxs-lookup"><span data-stu-id="f51aa-126">Sends the output to the specified printer.</span></span> <span data-ttu-id="f51aa-127">De parameter naam **naam** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="f51aa-127">The parameter name **Name** is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f51aa-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f51aa-128">CommonParameters</span></span>

<span data-ttu-id="f51aa-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f51aa-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f51aa-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f51aa-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f51aa-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="f51aa-131">INPUTS</span></span>

### <span data-ttu-id="f51aa-132">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f51aa-132">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f51aa-133">U kunt elk object door sluizen naar `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="f51aa-133">You can pipe any object to `Out-Printer`.</span></span>

## <span data-ttu-id="f51aa-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f51aa-134">OUTPUTS</span></span>

### <span data-ttu-id="f51aa-135">Geen</span><span class="sxs-lookup"><span data-stu-id="f51aa-135">None</span></span>

<span data-ttu-id="f51aa-136">`Out-Printer` retourneert geen objecten.</span><span class="sxs-lookup"><span data-stu-id="f51aa-136">`Out-Printer` does not return any objects.</span></span>

## <span data-ttu-id="f51aa-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f51aa-137">NOTES</span></span>

<span data-ttu-id="f51aa-138">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="f51aa-138">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="f51aa-139">De cmdlets die de term bevatten, `Out` hebben geen-objecten.</span><span class="sxs-lookup"><span data-stu-id="f51aa-139">The cmdlets that contain the `Out` verb do not format objects.</span></span> <span data-ttu-id="f51aa-140">Ze worden alleen weer gegeven en verzonden naar de opgegeven weergave bestemming.</span><span class="sxs-lookup"><span data-stu-id="f51aa-140">They just render them and send them to the specified display destination.</span></span> <span data-ttu-id="f51aa-141">Als u een niet-opgemaakt object naar een `Out` cmdlet verzendt, verzendt de cmdlet het naar een format-cmdlet voordat deze wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f51aa-141">If you send an unformatted object to an `Out` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="f51aa-142">`Out-Printer` Hiermee verzendt u gegevens naar de printer, maar worden er geen uitvoer objecten naar de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="f51aa-142">`Out-Printer` sends data to the printer, but does not emit any output objects to the pipeline.</span></span> <span data-ttu-id="f51aa-143">Als u de uitvoer van naar toesluist `Out-Printer` `Get-Member` , `Get-Member` rapporten dat er geen objecten zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f51aa-143">If you pipe the output of `Out-Printer` to `Get-Member`, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="f51aa-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f51aa-144">RELATED LINKS</span></span>

[<span data-ttu-id="f51aa-145">Out-file</span><span class="sxs-lookup"><span data-stu-id="f51aa-145">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="f51aa-146">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="f51aa-146">Out-String</span></span>](Out-String.md)
