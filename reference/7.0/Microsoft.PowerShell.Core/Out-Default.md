---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: 3d5fb12371e9ad329323b9d95d7151a43eb5924a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249623"
---
# <span data-ttu-id="919ff-103">Out-Default</span><span class="sxs-lookup"><span data-stu-id="919ff-103">Out-Default</span></span>

## <span data-ttu-id="919ff-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="919ff-104">SYNOPSIS</span></span>
<span data-ttu-id="919ff-105">Hiermee wordt de uitvoer naar de standaard Formatter en naar de standaard uitvoer-cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="919ff-105">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="919ff-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="919ff-106">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="919ff-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="919ff-107">DESCRIPTION</span></span>

<span data-ttu-id="919ff-108">Power shell voegt automatisch `Out-Default` aan het einde van elke pijp lijn toe.</span><span class="sxs-lookup"><span data-stu-id="919ff-108">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="919ff-109">`Out-Default` bepaalt hoe de object stroom moet worden ingedeeld en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="919ff-109">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="919ff-110">Als de object stroom een stroom van teken reeksen is, `Out-Default` sluizen deze direct waarmee `Out-Host` de juiste api's worden aangeroepen die door de host worden verschaft.</span><span class="sxs-lookup"><span data-stu-id="919ff-110">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="919ff-111">Als de object stroom geen teken reeksen bevat, `Out-Default` inspecteert het object om te bepalen wat er moet gebeuren.</span><span class="sxs-lookup"><span data-stu-id="919ff-111">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="919ff-112">Eerst wordt gekeken naar het object type en wordt bepaald of er een geregistreerde _weer gave_ is voor dit object type.</span><span class="sxs-lookup"><span data-stu-id="919ff-112">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="919ff-113">Power shell definieert XML-schema en een mechanisme (de `Update-FormatData` cmdlet) waar iedereen weer gaven voor een object type kan registreren.</span><span class="sxs-lookup"><span data-stu-id="919ff-113">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="919ff-114">U kunt **brede** , **lijst** -, **tabel** -of **aangepaste** weer gaven voor elk object type opgeven.</span><span class="sxs-lookup"><span data-stu-id="919ff-114">You can specify **wide** , **list** , **table** , or **custom** views for any object type.</span></span> <span data-ttu-id="919ff-115">In de weer gaven kunt u opgeven welke eigenschappen moeten worden weer gegeven en hoe deze moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="919ff-115">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="919ff-116">Als een weer gave is geregistreerd, wordt gedefinieerd welke formatter moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="919ff-116">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="919ff-117">Dus als de geregistreerde weer gave een **tabel** weergave is, worden `Out-Default` de objecten naar gestreamd `Format-Table | Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="919ff-117">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="919ff-118">`Format-Table` transformeert de objecten naar een stroom met opmaak records (aangedreven door de gegevens in de weergave definitie) en `Out-Host` transformeert de indelings records in aanroepen van de host-interface.</span><span class="sxs-lookup"><span data-stu-id="919ff-118">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="919ff-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="919ff-119">EXAMPLES</span></span>

### <span data-ttu-id="919ff-120">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="919ff-120">Example 1</span></span>

<span data-ttu-id="919ff-121">Hoewel deze cmdlet niet bedoeld is om rechtstreeks door de eind gebruiker te worden uitgevoerd, kan het zijn.</span><span class="sxs-lookup"><span data-stu-id="919ff-121">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

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

## <span data-ttu-id="919ff-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="919ff-122">PARAMETERS</span></span>

### <span data-ttu-id="919ff-123">-Input object</span><span class="sxs-lookup"><span data-stu-id="919ff-123">-InputObject</span></span>

<span data-ttu-id="919ff-124">Hiermee wordt invoer naar de cmdlet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="919ff-124">Accepts input to the cmdlet.</span></span>

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

### <span data-ttu-id="919ff-125">-Transcript</span><span class="sxs-lookup"><span data-stu-id="919ff-125">-Transcript</span></span>

<span data-ttu-id="919ff-126">Hiermee wordt bepaald of de uitvoer naar de transcriptie-services van Power shell moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="919ff-126">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

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

### <span data-ttu-id="919ff-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="919ff-127">CommonParameters</span></span>

<span data-ttu-id="919ff-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="919ff-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="919ff-129">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="919ff-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="919ff-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="919ff-130">INPUTS</span></span>

## <span data-ttu-id="919ff-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="919ff-131">OUTPUTS</span></span>

## <span data-ttu-id="919ff-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="919ff-132">NOTES</span></span>

## <span data-ttu-id="919ff-133">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="919ff-133">RELATED LINKS</span></span>

[<span data-ttu-id="919ff-134">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="919ff-134">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="919ff-135">Format-List</span><span class="sxs-lookup"><span data-stu-id="919ff-135">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="919ff-136">Format-Table</span><span class="sxs-lookup"><span data-stu-id="919ff-136">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="919ff-137">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="919ff-137">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="919ff-138">about_Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="919ff-138">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="919ff-139">Hoe Power shell-opmaak en-uitvoer echt werkt</span><span class="sxs-lookup"><span data-stu-id="919ff-139">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)
