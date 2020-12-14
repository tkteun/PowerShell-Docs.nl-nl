---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 5fd1ff9760cbddeb0c5c29052caf0f36d6d760d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705704"
---
# <span data-ttu-id="b5bd5-102">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-102">Tee-Object</span></span>

## <span data-ttu-id="b5bd5-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b5bd5-103">SYNOPSIS</span></span>
<span data-ttu-id="b5bd5-104">Slaat de uitvoer van de opdracht op in een bestand of variabele, en verzendt deze ook naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-104">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="b5bd5-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b5bd5-105">SYNTAX</span></span>

### <span data-ttu-id="b5bd5-106">Bestand (standaard)</span><span class="sxs-lookup"><span data-stu-id="b5bd5-106">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="b5bd5-107">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="b5bd5-107">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="b5bd5-108">Variabele</span><span class="sxs-lookup"><span data-stu-id="b5bd5-108">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="b5bd5-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b5bd5-109">DESCRIPTION</span></span>

<span data-ttu-id="b5bd5-110">De `Tee-Object` cmdlet stuurt uitvoer om, dat wil zeggen, de uitvoer van een opdracht in twee richtingen (zoals de letter T).</span><span class="sxs-lookup"><span data-stu-id="b5bd5-110">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="b5bd5-111">De uitvoer wordt opgeslagen in een bestand of variabele, en wordt ook verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-111">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="b5bd5-112">Als de `Tee-Object` laatste opdracht in de pijp lijn is, wordt de opdracht uitvoer weer gegeven bij de prompt.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-112">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="b5bd5-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b5bd5-113">EXAMPLES</span></span>

### <span data-ttu-id="b5bd5-114">Voor beeld 1: uitvoer processen naar een bestand en naar de-console</span><span class="sxs-lookup"><span data-stu-id="b5bd5-114">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="b5bd5-115">In dit voor beeld wordt een lijst opgehaald met de processen die op de computer worden uitgevoerd en wordt het resultaat naar een bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-115">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="b5bd5-116">Omdat er geen tweede pad is opgegeven, worden de processen ook weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-116">Because a second path is not specified, the processes are also displayed in the console.</span></span>

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### <span data-ttu-id="b5bd5-117">Voor beeld 2: uitvoer processen naar een variabele en `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="b5bd5-117">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="b5bd5-118">In dit voor beeld wordt een lijst opgehaald met de processen die op de computer worden uitgevoerd, worden deze opgeslagen in de `$proc` variabele en worden ze door sluizen naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="b5bd5-118">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

<span data-ttu-id="b5bd5-119">`Select-Object`Met de cmdlet worden de eigenschappen **proces** -en **handle** geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-119">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="b5bd5-120">Houd er rekening mee dat de `$proc` variabele de standaard gegevens bevat die worden geretourneerd door `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="b5bd5-120">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="b5bd5-121">Voor beeld 3: systeem bestanden uitvoeren naar twee logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="b5bd5-121">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="b5bd5-122">In dit voor beeld wordt een lijst met systeem bestanden opgeslagen in twee logboek bestanden, een cumulatief bestand en een actueel bestand.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-122">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="b5bd5-123">De opdracht gebruikt de `Get-ChildItem` cmdlet voor het uitvoeren van een recursieve zoek opdracht voor systeem bestanden op station D:.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-123">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="b5bd5-124">Een pijplijn operator (|) verzendt de lijst naar `Tee-Object` , waarmee de lijst wordt toegevoegd aan het AllSystemFiles.txt-bestand en de lijst wordt door gegeven aan de `Out-File` -cmdlet, waarmee de lijst wordt opgeslagen in het NewSystemFiles.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-124">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="b5bd5-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5bd5-125">PARAMETERS</span></span>

### <span data-ttu-id="b5bd5-126">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="b5bd5-126">-Append</span></span>

<span data-ttu-id="b5bd5-127">Geeft aan dat de cmdlet de uitvoer aan het opgegeven bestand toevoegt.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-127">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="b5bd5-128">Zonder deze para meter vervangt de nieuwe inhoud alle bestaande inhoud in het bestand zonder dat er een waarschuwing wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-128">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="b5bd5-129">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-129">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5bd5-130">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b5bd5-130">-FilePath</span></span>

<span data-ttu-id="b5bd5-131">Hiermee geeft u een bestand op dat met deze cmdlet het object opslaat in joker tekens, maar moet worden omgezet in één bestand.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-131">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b5bd5-132">-Input object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-132">-InputObject</span></span>

<span data-ttu-id="b5bd5-133">Hiermee geeft u het object op dat moet worden opgeslagen en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-133">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="b5bd5-134">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-134">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="b5bd5-135">U kunt ook een object pipet naar `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="b5bd5-135">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="b5bd5-136">Wanneer u de para meter **input object** gebruikt in `Tee-Object` plaats van de resultaten van de pijpleiding opdracht, `Tee-Object` wordt de waarde van **input object** behandeld als één enkel object, zelfs als de waarde een verzameling is.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-136">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

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

### <span data-ttu-id="b5bd5-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b5bd5-137">-LiteralPath</span></span>

<span data-ttu-id="b5bd5-138">Hiermee geeft u een bestand op waarvan deze cmdlet het object opslaat.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-138">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="b5bd5-139">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-139">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b5bd5-140">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b5bd5-141">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b5bd5-142">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-142">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5bd5-143">-Variabele</span><span class="sxs-lookup"><span data-stu-id="b5bd5-143">-Variable</span></span>

<span data-ttu-id="b5bd5-144">Hiermee geeft u een variabele op waaraan de cmdlet het object opslaat.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-144">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="b5bd5-145">Geef een naam op voor de variabele zonder het voor gaande dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="b5bd5-145">Enter a variable name without the preceding dollar sign (`$`).</span></span>

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b5bd5-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5bd5-146">CommonParameters</span></span>

<span data-ttu-id="b5bd5-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5bd5-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5bd5-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="b5bd5-149">INPUTS</span></span>

### <span data-ttu-id="b5bd5-150">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b5bd5-150">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b5bd5-151">U kunt objecten door sluizen naar `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="b5bd5-151">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="b5bd5-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b5bd5-152">OUTPUTS</span></span>

### <span data-ttu-id="b5bd5-153">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b5bd5-153">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b5bd5-154">`Tee-Object` retourneert het object dat wordt omgeleid.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-154">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="b5bd5-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b5bd5-155">NOTES</span></span>

<span data-ttu-id="b5bd5-156">U kunt ook de `Out-File` cmdlet of de omleidings operator gebruiken, beide waarmee de uitvoer in een bestand wordt opgeslagen, maar deze niet wordt verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-156">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="b5bd5-157">Vanaf Power shell 6 `Tee-Object` gebruikt de stuk lijst-minder UTF-8-code ring wanneer deze naar bestanden wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="b5bd5-157">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="b5bd5-158">Als u een andere code ring nodig hebt, gebruikt u de `Out-File` cmdlet met de para meter **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="b5bd5-158">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="b5bd5-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b5bd5-159">RELATED LINKS</span></span>

[<span data-ttu-id="b5bd5-160">Compare-object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-160">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="b5bd5-161">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-161">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="b5bd5-162">Groep-object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-162">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="b5bd5-163">Meting object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-163">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="b5bd5-164">New-Object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-164">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="b5bd5-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-165">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="b5bd5-166">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-166">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="b5bd5-167">Where-object</span><span class="sxs-lookup"><span data-stu-id="b5bd5-167">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="b5bd5-168">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b5bd5-168">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

