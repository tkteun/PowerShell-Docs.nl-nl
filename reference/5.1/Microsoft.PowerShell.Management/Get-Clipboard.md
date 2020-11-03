---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "93251941"
---
# <span data-ttu-id="3fac1-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="3fac1-103">Get-Clipboard</span></span>

## <span data-ttu-id="3fac1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3fac1-104">SYNOPSIS</span></span>
<span data-ttu-id="3fac1-105">Hiermee wordt de huidige Windows klem bord-vermelding opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3fac1-105">Gets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="3fac1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3fac1-106">SYNTAX</span></span>

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="3fac1-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3fac1-107">DESCRIPTION</span></span>

<span data-ttu-id="3fac1-108">De `Get-Clipboard` cmdlet haalt het huidige Windows klem bord-item op.</span><span class="sxs-lookup"><span data-stu-id="3fac1-108">The `Get-Clipboard` cmdlet gets the current Windows clipboard entry.</span></span> <span data-ttu-id="3fac1-109">Meerdere tekst regels worden geretourneerd als een matrix met teken reeksen die vergelijkbaar zijn met `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="3fac1-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

## <span data-ttu-id="3fac1-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3fac1-110">EXAMPLES</span></span>

### <span data-ttu-id="3fac1-111">Voor beeld 1: de inhoud van het klem bord ophalen en weer geven op de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="3fac1-111">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="3fac1-112">In dit voor beeld hebben we met de rechter muisknop op een afbeelding in een browser geklikt en de **Kopieer** actie gekozen.</span><span class="sxs-lookup"><span data-stu-id="3fac1-112">In this example we have right-clicked on an image in a browser and chose the **Copy** action.</span></span> <span data-ttu-id="3fac1-113">De volgende opdracht wordt de koppeling als een URL van de afbeelding die op het klem bord is opgeslagen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3fac1-113">The following command displays the link, as a URL, of the image that is stored in the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### <span data-ttu-id="3fac1-114">Voor beeld 2: de inhoud van het klem bord in een specifieke indeling ophalen</span><span class="sxs-lookup"><span data-stu-id="3fac1-114">Example 2: Get the content of the clipboard in a specific format</span></span>

<span data-ttu-id="3fac1-115">In dit voor beeld hebben we bestanden gekopieerd naar het klem bord in Windows Explorerby ze te selecteren en op <kbd>CTRL + C</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="3fac1-115">In this example we copied files to the clipboard in Windows Explorerby selecting them and pressing <kbd>Ctrl-C</kbd>.</span></span> <span data-ttu-id="3fac1-116">Met de volgende opdracht kunt u de inhoud van het klem bord openen als een lijst met bestanden:</span><span class="sxs-lookup"><span data-stu-id="3fac1-116">Using the following command, you can access the contents of the clipboard as a list of files:</span></span>

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## <span data-ttu-id="3fac1-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3fac1-117">PARAMETERS</span></span>

### <span data-ttu-id="3fac1-118">-Indeling</span><span class="sxs-lookup"><span data-stu-id="3fac1-118">-Format</span></span>

<span data-ttu-id="3fac1-119">Hiermee wordt het type of de indeling van het klem bord opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3fac1-119">Specifies the type, or format, of the clipboard.</span></span> <span data-ttu-id="3fac1-120">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3fac1-120">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3fac1-121">Tekst</span><span class="sxs-lookup"><span data-stu-id="3fac1-121">Text</span></span>
- <span data-ttu-id="3fac1-122">FileDropList</span><span class="sxs-lookup"><span data-stu-id="3fac1-122">FileDropList</span></span>
- <span data-ttu-id="3fac1-123">Installatiekopie</span><span class="sxs-lookup"><span data-stu-id="3fac1-123">Image</span></span>
- <span data-ttu-id="3fac1-124">Audio</span><span class="sxs-lookup"><span data-stu-id="3fac1-124">Audio</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3fac1-125">-RAW</span><span class="sxs-lookup"><span data-stu-id="3fac1-125">-Raw</span></span>

<span data-ttu-id="3fac1-126">Hiermee haalt u de volledige inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="3fac1-126">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="3fac1-127">Tekst met meerdere regels wordt geretourneerd als één teken reeks in plaats van een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="3fac1-127">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="3fac1-128">-TextFormatType</span><span class="sxs-lookup"><span data-stu-id="3fac1-128">-TextFormatType</span></span>

<span data-ttu-id="3fac1-129">Geeft het type tekst gegevens indeling van het klem bord aan.</span><span class="sxs-lookup"><span data-stu-id="3fac1-129">Specifies the text data format type of the clipboard.</span></span> <span data-ttu-id="3fac1-130">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3fac1-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3fac1-131">Tekst</span><span class="sxs-lookup"><span data-stu-id="3fac1-131">Text</span></span>
- <span data-ttu-id="3fac1-132">UnicodeText</span><span class="sxs-lookup"><span data-stu-id="3fac1-132">UnicodeText</span></span>
- <span data-ttu-id="3fac1-133">Formatting</span><span class="sxs-lookup"><span data-stu-id="3fac1-133">Rtf</span></span>
- <span data-ttu-id="3fac1-134">HTML</span><span class="sxs-lookup"><span data-stu-id="3fac1-134">Html</span></span>
- <span data-ttu-id="3fac1-135">CommaSeparatedValue</span><span class="sxs-lookup"><span data-stu-id="3fac1-135">CommaSeparatedValue</span></span>

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3fac1-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3fac1-136">CommonParameters</span></span>

<span data-ttu-id="3fac1-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3fac1-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3fac1-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3fac1-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3fac1-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="3fac1-139">INPUTS</span></span>

## <span data-ttu-id="3fac1-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3fac1-140">OUTPUTS</span></span>

### <span data-ttu-id="3fac1-141">System. String, System. IO. file info, System. IO. Stream, System. Drawing. image</span><span class="sxs-lookup"><span data-stu-id="3fac1-141">System.String, System.IO.FileInfo, System.IO.Stream, System.Drawing.Image</span></span>

## <span data-ttu-id="3fac1-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3fac1-142">NOTES</span></span>

## <span data-ttu-id="3fac1-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3fac1-143">RELATED LINKS</span></span>

[<span data-ttu-id="3fac1-144">Set-klem bord</span><span class="sxs-lookup"><span data-stu-id="3fac1-144">Set-Clipboard</span></span>](Set-Clipboard.md)
