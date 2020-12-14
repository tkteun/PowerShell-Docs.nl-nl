---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: d650a9280982703e09ec22698c3848a616abb067
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705614"
---
# <span data-ttu-id="f5641-102">Out-Default</span><span class="sxs-lookup"><span data-stu-id="f5641-102">Out-Default</span></span>

## <span data-ttu-id="f5641-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f5641-103">SYNOPSIS</span></span>
<span data-ttu-id="f5641-104">Hiermee wordt de uitvoer naar de standaard Formatter en naar de standaard uitvoer-cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f5641-104">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="f5641-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f5641-105">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="f5641-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f5641-106">DESCRIPTION</span></span>

<span data-ttu-id="f5641-107">Power shell voegt automatisch `Out-Default` aan het einde van elke pijp lijn toe.</span><span class="sxs-lookup"><span data-stu-id="f5641-107">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="f5641-108">`Out-Default` bepaalt hoe de object stroom moet worden ingedeeld en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f5641-108">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="f5641-109">Als de object stroom een stroom van teken reeksen is, `Out-Default` sluizen deze direct waarmee `Out-Host` de juiste api's worden aangeroepen die door de host worden verschaft.</span><span class="sxs-lookup"><span data-stu-id="f5641-109">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="f5641-110">Als de object stroom geen teken reeksen bevat, `Out-Default` inspecteert het object om te bepalen wat er moet gebeuren.</span><span class="sxs-lookup"><span data-stu-id="f5641-110">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="f5641-111">Eerst wordt gekeken naar het object type en wordt bepaald of er een geregistreerde _weer gave_ is voor dit object type.</span><span class="sxs-lookup"><span data-stu-id="f5641-111">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="f5641-112">Power shell definieert XML-schema en een mechanisme (de `Update-FormatData` cmdlet) waar iedereen weer gaven voor een object type kan registreren.</span><span class="sxs-lookup"><span data-stu-id="f5641-112">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="f5641-113">U kunt **brede**, **lijst**-, **tabel**-of **aangepaste** weer gaven voor elk object type opgeven.</span><span class="sxs-lookup"><span data-stu-id="f5641-113">You can specify **wide**, **list**, **table**, or **custom** views for any object type.</span></span> <span data-ttu-id="f5641-114">In de weer gaven kunt u opgeven welke eigenschappen moeten worden weer gegeven en hoe deze moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f5641-114">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="f5641-115">Als een weer gave is geregistreerd, wordt gedefinieerd welke formatter moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5641-115">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="f5641-116">Dus als de geregistreerde weer gave een **tabel** weergave is, worden `Out-Default` de objecten naar gestreamd `Format-Table | Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="f5641-116">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="f5641-117">`Format-Table` transformeert de objecten naar een stroom met opmaak records (aangedreven door de gegevens in de weergave definitie) en `Out-Host` transformeert de indelings records in aanroepen van de host-interface.</span><span class="sxs-lookup"><span data-stu-id="f5641-117">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="f5641-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f5641-118">EXAMPLES</span></span>

### <span data-ttu-id="f5641-119">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="f5641-119">Example 1</span></span>

<span data-ttu-id="f5641-120">Hoewel deze cmdlet niet bedoeld is om rechtstreeks door de eind gebruiker te worden uitgevoerd, kan het zijn.</span><span class="sxs-lookup"><span data-stu-id="f5641-120">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## <span data-ttu-id="f5641-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f5641-121">PARAMETERS</span></span>

### <span data-ttu-id="f5641-122">-Input object</span><span class="sxs-lookup"><span data-stu-id="f5641-122">-InputObject</span></span>

<span data-ttu-id="f5641-123">Hiermee wordt invoer naar de cmdlet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="f5641-123">Accepts input to the cmdlet.</span></span>

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

### <span data-ttu-id="f5641-124">-Transcript</span><span class="sxs-lookup"><span data-stu-id="f5641-124">-Transcript</span></span>

<span data-ttu-id="f5641-125">Hiermee wordt bepaald of de uitvoer naar de transcriptie-services van Power shell moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="f5641-125">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f5641-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f5641-126">CommonParameters</span></span>

<span data-ttu-id="f5641-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f5641-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f5641-128">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f5641-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f5641-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="f5641-129">INPUTS</span></span>

## <span data-ttu-id="f5641-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f5641-130">OUTPUTS</span></span>

## <span data-ttu-id="f5641-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f5641-131">NOTES</span></span>

## <span data-ttu-id="f5641-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f5641-132">RELATED LINKS</span></span>

[<span data-ttu-id="f5641-133">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="f5641-133">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="f5641-134">Format-List</span><span class="sxs-lookup"><span data-stu-id="f5641-134">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="f5641-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="f5641-135">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="f5641-136">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="f5641-136">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="f5641-137">about_Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="f5641-137">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="f5641-138">Hoe Power shell-opmaak en-uitvoer echt werkt</span><span class="sxs-lookup"><span data-stu-id="f5641-138">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

