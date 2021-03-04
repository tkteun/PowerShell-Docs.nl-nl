---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: cf19973acf799b25b8b598fad70f84943f958e1d
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685891"
---
# <span data-ttu-id="b17f4-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="b17f4-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="b17f4-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b17f4-104">SYNOPSIS</span></span>
<span data-ttu-id="b17f4-105">Hiermee haalt u informatie op over de Authenticode-hand tekening voor een bestand.</span><span class="sxs-lookup"><span data-stu-id="b17f4-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="b17f4-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b17f4-106">SYNTAX</span></span>

### <span data-ttu-id="b17f4-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="b17f4-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="b17f4-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b17f4-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="b17f4-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="b17f4-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="b17f4-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b17f4-110">DESCRIPTION</span></span>

<span data-ttu-id="b17f4-111">De `Get-AuthenticodeSignature` cmdlet haalt informatie op over de Authenticode-hand tekening voor een bestand of bestands inhoud als een byte matrix.</span><span class="sxs-lookup"><span data-stu-id="b17f4-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span>
<span data-ttu-id="b17f4-112">Als het bestand zowel Inge sloten ondertekende als Windows-catalogus is ondertekend, wordt de hand tekening van de Windows-catalogus gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b17f4-112">If the file is both embedded signed and Windows catalog signed, the Windows catalog signature is used.</span></span>
<span data-ttu-id="b17f4-113">Als het bestand niet is ondertekend, wordt de informatie opgehaald, maar zijn de velden leeg.</span><span class="sxs-lookup"><span data-stu-id="b17f4-113">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="b17f4-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b17f4-114">EXAMPLES</span></span>

### <span data-ttu-id="b17f4-115">Voor beeld 1: de Authenticode-hand tekening voor een bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="b17f4-115">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="b17f4-116">Met deze opdracht wordt informatie opgehaald over de Authenticode-hand tekening in het NewScript.ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="b17f4-116">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="b17f4-117">De para meter **filepath** wordt gebruikt om het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="b17f4-117">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="b17f4-118">Voor beeld 2: de Authenticode-hand tekening voor meerdere bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="b17f4-118">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="b17f4-119">Met deze opdracht wordt informatie opgehaald over de Authenticode-hand tekening voor de vier bestanden die worden vermeld op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b17f4-119">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="b17f4-120">In dit voor beeld wordt de naam van de **filepath** -para meter, die optioneel is, wegge laten.</span><span class="sxs-lookup"><span data-stu-id="b17f4-120">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="b17f4-121">Voor beeld 3: alleen geldige Authenticode-hand tekeningen ophalen voor meerdere bestanden</span><span class="sxs-lookup"><span data-stu-id="b17f4-121">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="b17f4-122">Met deze opdracht worden alle bestanden in de map weer gegeven `$PSHOME` die een geldige Authenticode-hand tekening hebben.</span><span class="sxs-lookup"><span data-stu-id="b17f4-122">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="b17f4-123">De `$PSHOME` Automatische variabele bevat het pad naar de installatie directory van Power shell.</span><span class="sxs-lookup"><span data-stu-id="b17f4-123">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="b17f4-124">De opdracht gebruikt de `Get-ChildItem` cmdlet om de bestanden in de map op te halen `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="b17f4-124">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="b17f4-125">Er wordt een patroon van gebruikt *.*</span><span class="sxs-lookup"><span data-stu-id="b17f4-125">It uses a pattern of *.*</span></span> <span data-ttu-id="b17f4-126">om directory's uit te sluiten (hoewel er ook bestanden worden uitgesloten zonder punt in de bestands naam).</span><span class="sxs-lookup"><span data-stu-id="b17f4-126">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="b17f4-127">De opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de bestanden in `$PSHOME` naar de `ForEach-Object` cmdlet, waarbij `Get-AuthenticodeSignature` wordt aangeroepen voor elk bestand.</span><span class="sxs-lookup"><span data-stu-id="b17f4-127">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="b17f4-128">De resultaten van de `Get-AuthenticodeSignature` opdracht worden verzonden naar een `Where-Object` opdracht die alleen de handtekening objecten met de status geldig selecteert.</span><span class="sxs-lookup"><span data-stu-id="b17f4-128">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="b17f4-129">Voor beeld 4: de Authenticode-hand tekening ophalen voor een bestands inhoud die is opgegeven als byte matrix</span><span class="sxs-lookup"><span data-stu-id="b17f4-129">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="b17f4-130">Met deze opdracht wordt informatie over de Authenticode-hand tekening voor de inhoud van een bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b17f4-130">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="b17f4-131">In dit voor beeld wordt de bestands extensie opgegeven samen met de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="b17f4-131">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="b17f4-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b17f4-132">PARAMETERS</span></span>

### <span data-ttu-id="b17f4-133">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="b17f4-133">-Content</span></span>

<span data-ttu-id="b17f4-134">Inhoud van een bestand als een byte matrix waarvoor de Authenticode-hand tekening wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b17f4-134">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="b17f4-135">Deze para meter moet worden gebruikt met de para meter **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="b17f4-135">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="b17f4-136">De inhoud van het bestand moet de Unicode-indeling (UTF-16LE) hebben.</span><span class="sxs-lookup"><span data-stu-id="b17f4-136">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

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

### <span data-ttu-id="b17f4-137">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b17f4-137">-FilePath</span></span>

<span data-ttu-id="b17f4-138">Hiermee geeft u het pad op naar het bestand dat u wilt onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="b17f4-138">Specifies the path to the file to examine.</span></span> <span data-ttu-id="b17f4-139">Joker tekens zijn toegestaan, maar moeten tot één bestand leiden.</span><span class="sxs-lookup"><span data-stu-id="b17f4-139">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="b17f4-140">Het is niet nodig om het **bestandspad** te typen op de opdracht regel wanneer u een waarde voor deze para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="b17f4-140">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

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

### <span data-ttu-id="b17f4-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b17f4-141">-LiteralPath</span></span>

<span data-ttu-id="b17f4-142">Hiermee geeft u het pad op naar het bestand dat wordt onderzocht.</span><span class="sxs-lookup"><span data-stu-id="b17f4-142">Specifies the path to the file being examined.</span></span> <span data-ttu-id="b17f4-143">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b17f4-143">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b17f4-144">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b17f4-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b17f4-145">Als het pad een escape-teken bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b17f4-145">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="b17f4-146">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape-tekens.</span><span class="sxs-lookup"><span data-stu-id="b17f4-146">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

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

### <span data-ttu-id="b17f4-147">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="b17f4-147">-SourcePathOrExtension</span></span>

<span data-ttu-id="b17f4-148">Het pad naar het bestand of het bestands type van de inhoud waarvoor de Authenticode-hand tekening is opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b17f4-148">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="b17f4-149">Deze para meter wordt gebruikt met **inhoud** waar bestands inhoud als een byte matrix wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="b17f4-149">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

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

### <span data-ttu-id="b17f4-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b17f4-150">CommonParameters</span></span>

<span data-ttu-id="b17f4-151">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b17f4-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b17f4-152">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b17f4-152">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b17f4-153">INVOER</span><span class="sxs-lookup"><span data-stu-id="b17f4-153">INPUTS</span></span>

### <span data-ttu-id="b17f4-154">System. String</span><span class="sxs-lookup"><span data-stu-id="b17f4-154">System.String</span></span>

<span data-ttu-id="b17f4-155">U kunt een teken reeks die een bestandspad bevat, door sluizen naar `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="b17f4-155">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="b17f4-156">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b17f4-156">OUTPUTS</span></span>

### <span data-ttu-id="b17f4-157">System. Management. Automation. Signature</span><span class="sxs-lookup"><span data-stu-id="b17f4-157">System.Management.Automation.Signature</span></span>

<span data-ttu-id="b17f4-158">`Get-AuthenticodeSignature` retourneert een Signature-object voor elke hand tekening die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b17f4-158">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="b17f4-159">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b17f4-159">NOTES</span></span>

<span data-ttu-id="b17f4-160">Zie [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)voor meer informatie over Authenticode-hand tekeningen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b17f4-160">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="b17f4-161">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b17f4-161">RELATED LINKS</span></span>

[<span data-ttu-id="b17f4-162">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="b17f4-162">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="b17f4-163">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="b17f4-163">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="b17f4-164">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="b17f4-164">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="b17f4-165">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="b17f4-165">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="b17f4-166">about_Signing</span><span class="sxs-lookup"><span data-stu-id="b17f4-166">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
