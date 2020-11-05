---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 723b374d8623ff8437a27a48933057e457108eb1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249821"
---
# <span data-ttu-id="28ebe-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="28ebe-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="28ebe-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="28ebe-104">SYNOPSIS</span></span>
<span data-ttu-id="28ebe-105">Hiermee haalt u informatie op over de Authenticode-hand tekening voor een bestand.</span><span class="sxs-lookup"><span data-stu-id="28ebe-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="28ebe-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="28ebe-106">SYNTAX</span></span>

### <span data-ttu-id="28ebe-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="28ebe-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="28ebe-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="28ebe-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="28ebe-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="28ebe-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="28ebe-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="28ebe-110">DESCRIPTION</span></span>

<span data-ttu-id="28ebe-111">De `Get-AuthenticodeSignature` cmdlet haalt informatie op over de Authenticode-hand tekening voor een bestand of bestands inhoud als een byte matrix.</span><span class="sxs-lookup"><span data-stu-id="28ebe-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span> <span data-ttu-id="28ebe-112">Als het bestand niet is ondertekend, wordt de informatie opgehaald, maar zijn de velden leeg.</span><span class="sxs-lookup"><span data-stu-id="28ebe-112">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="28ebe-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="28ebe-113">EXAMPLES</span></span>

### <span data-ttu-id="28ebe-114">Voor beeld 1: de Authenticode-hand tekening voor een bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="28ebe-114">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="28ebe-115">Met deze opdracht wordt informatie opgehaald over de Authenticode-hand tekening in het NewScript.ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="28ebe-115">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="28ebe-116">De para meter **filepath** wordt gebruikt om het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="28ebe-116">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="28ebe-117">Voor beeld 2: de Authenticode-hand tekening voor meerdere bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="28ebe-117">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="28ebe-118">Met deze opdracht wordt informatie opgehaald over de Authenticode-hand tekening voor de vier bestanden die worden vermeld op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="28ebe-118">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="28ebe-119">In dit voor beeld wordt de naam van de **filepath** -para meter, die optioneel is, wegge laten.</span><span class="sxs-lookup"><span data-stu-id="28ebe-119">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="28ebe-120">Voor beeld 3: alleen geldige Authenticode-hand tekeningen ophalen voor meerdere bestanden</span><span class="sxs-lookup"><span data-stu-id="28ebe-120">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="28ebe-121">Met deze opdracht worden alle bestanden in de map weer gegeven `$PSHOME` die een geldige Authenticode-hand tekening hebben.</span><span class="sxs-lookup"><span data-stu-id="28ebe-121">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="28ebe-122">De `$PSHOME` Automatische variabele bevat het pad naar de installatie directory van Power shell.</span><span class="sxs-lookup"><span data-stu-id="28ebe-122">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="28ebe-123">De opdracht gebruikt de `Get-ChildItem` cmdlet om de bestanden in de map op te halen `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="28ebe-123">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="28ebe-124">Er wordt een patroon van gebruikt *.*</span><span class="sxs-lookup"><span data-stu-id="28ebe-124">It uses a pattern of *.*</span></span> <span data-ttu-id="28ebe-125">om directory's uit te sluiten (hoewel er ook bestanden worden uitgesloten zonder punt in de bestands naam).</span><span class="sxs-lookup"><span data-stu-id="28ebe-125">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="28ebe-126">De opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de bestanden in `$PSHOME` naar de `ForEach-Object` cmdlet, waarbij `Get-AuthenticodeSignature` wordt aangeroepen voor elk bestand.</span><span class="sxs-lookup"><span data-stu-id="28ebe-126">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="28ebe-127">De resultaten van de `Get-AuthenticodeSignature` opdracht worden verzonden naar een `Where-Object` opdracht die alleen de handtekening objecten met de status geldig selecteert.</span><span class="sxs-lookup"><span data-stu-id="28ebe-127">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="28ebe-128">Voor beeld 4: de Authenticode-hand tekening ophalen voor een bestands inhoud die is opgegeven als byte matrix</span><span class="sxs-lookup"><span data-stu-id="28ebe-128">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="28ebe-129">Met deze opdracht wordt informatie over de Authenticode-hand tekening voor de inhoud van een bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="28ebe-129">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="28ebe-130">In dit voor beeld wordt de bestands extensie opgegeven samen met de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="28ebe-130">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="28ebe-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="28ebe-131">PARAMETERS</span></span>

### <span data-ttu-id="28ebe-132">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="28ebe-132">-Content</span></span>

<span data-ttu-id="28ebe-133">Inhoud van een bestand als een byte matrix waarvoor de Authenticode-hand tekening wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="28ebe-133">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="28ebe-134">Deze para meter moet worden gebruikt met de para meter **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="28ebe-134">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="28ebe-135">De inhoud van het bestand moet de Unicode-indeling (UTF-16LE) hebben.</span><span class="sxs-lookup"><span data-stu-id="28ebe-135">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="28ebe-136">-FilePath</span><span class="sxs-lookup"><span data-stu-id="28ebe-136">-FilePath</span></span>

<span data-ttu-id="28ebe-137">Hiermee geeft u het pad op naar het bestand dat u wilt onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="28ebe-137">Specifies the path to the file to examine.</span></span> <span data-ttu-id="28ebe-138">Joker tekens zijn toegestaan, maar moeten tot één bestand leiden.</span><span class="sxs-lookup"><span data-stu-id="28ebe-138">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="28ebe-139">Het is niet nodig om het **bestandspad** te typen op de opdracht regel wanneer u een waarde voor deze para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="28ebe-139">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="28ebe-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="28ebe-140">-LiteralPath</span></span>

<span data-ttu-id="28ebe-141">Hiermee geeft u het pad op naar het bestand dat wordt onderzocht.</span><span class="sxs-lookup"><span data-stu-id="28ebe-141">Specifies the path to the file being examined.</span></span> <span data-ttu-id="28ebe-142">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="28ebe-142">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="28ebe-143">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="28ebe-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="28ebe-144">Als het pad een escape-teken bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="28ebe-144">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="28ebe-145">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape-tekens.</span><span class="sxs-lookup"><span data-stu-id="28ebe-145">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="28ebe-146">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="28ebe-146">-SourcePathOrExtension</span></span>

<span data-ttu-id="28ebe-147">Het pad naar het bestand of het bestands type van de inhoud waarvoor de Authenticode-hand tekening is opgehaald.</span><span class="sxs-lookup"><span data-stu-id="28ebe-147">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="28ebe-148">Deze para meter wordt gebruikt met **inhoud** waar bestands inhoud als een byte matrix wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="28ebe-148">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="28ebe-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28ebe-149">CommonParameters</span></span>

<span data-ttu-id="28ebe-150">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="28ebe-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28ebe-151">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="28ebe-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="28ebe-152">INVOER</span><span class="sxs-lookup"><span data-stu-id="28ebe-152">INPUTS</span></span>

### <span data-ttu-id="28ebe-153">System. String</span><span class="sxs-lookup"><span data-stu-id="28ebe-153">System.String</span></span>

<span data-ttu-id="28ebe-154">U kunt een teken reeks die een bestandspad bevat, door sluizen naar `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="28ebe-154">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="28ebe-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="28ebe-155">OUTPUTS</span></span>

### <span data-ttu-id="28ebe-156">System. Management. Automation. Signature</span><span class="sxs-lookup"><span data-stu-id="28ebe-156">System.Management.Automation.Signature</span></span>

<span data-ttu-id="28ebe-157">`Get-AuthenticodeSignature` retourneert een Signature-object voor elke hand tekening die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="28ebe-157">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="28ebe-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="28ebe-158">NOTES</span></span>

<span data-ttu-id="28ebe-159">Zie [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)voor meer informatie over Authenticode-hand tekeningen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="28ebe-159">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="28ebe-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="28ebe-160">RELATED LINKS</span></span>

[<span data-ttu-id="28ebe-161">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="28ebe-161">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="28ebe-162">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="28ebe-162">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="28ebe-163">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="28ebe-163">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="28ebe-164">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="28ebe-164">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="28ebe-165">about_Signing</span><span class="sxs-lookup"><span data-stu-id="28ebe-165">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)