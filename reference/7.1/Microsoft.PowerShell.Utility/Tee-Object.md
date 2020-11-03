---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: fdfbb75bf95c8dc248441b6399312ed0592f62de
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249894"
---
# <span data-ttu-id="8b8dd-103">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-103">Tee-Object</span></span>

## <span data-ttu-id="8b8dd-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8b8dd-104">SYNOPSIS</span></span>
<span data-ttu-id="8b8dd-105">Slaat de uitvoer van de opdracht op in een bestand of variabele, en verzendt deze ook naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-105">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="8b8dd-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8b8dd-106">SYNTAX</span></span>

### <span data-ttu-id="8b8dd-107">Bestand (standaard)</span><span class="sxs-lookup"><span data-stu-id="8b8dd-107">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="8b8dd-108">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="8b8dd-108">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="8b8dd-109">Variabele</span><span class="sxs-lookup"><span data-stu-id="8b8dd-109">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="8b8dd-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8b8dd-110">DESCRIPTION</span></span>

<span data-ttu-id="8b8dd-111">De `Tee-Object` cmdlet stuurt uitvoer om, dat wil zeggen, de uitvoer van een opdracht in twee richtingen (zoals de letter T).</span><span class="sxs-lookup"><span data-stu-id="8b8dd-111">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="8b8dd-112">De uitvoer wordt opgeslagen in een bestand of variabele, en wordt ook verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-112">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="8b8dd-113">Als de `Tee-Object` laatste opdracht in de pijp lijn is, wordt de opdracht uitvoer weer gegeven bij de prompt.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-113">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="8b8dd-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8b8dd-114">EXAMPLES</span></span>

### <span data-ttu-id="8b8dd-115">Voor beeld 1: uitvoer processen naar een bestand en naar de-console</span><span class="sxs-lookup"><span data-stu-id="8b8dd-115">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="8b8dd-116">In dit voor beeld wordt een lijst opgehaald met de processen die op de computer worden uitgevoerd en wordt het resultaat naar een bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-116">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="8b8dd-117">Omdat er geen tweede pad is opgegeven, worden de processen ook weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-117">Because a second path is not specified, the processes are also displayed in the console.</span></span>

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

### <span data-ttu-id="8b8dd-118">Voor beeld 2: uitvoer processen naar een variabele en `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="8b8dd-118">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="8b8dd-119">In dit voor beeld wordt een lijst opgehaald met de processen die op de computer worden uitgevoerd, worden deze opgeslagen in de `$proc` variabele en worden ze door sluizen naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8b8dd-119">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

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

<span data-ttu-id="8b8dd-120">`Select-Object`Met de cmdlet worden de eigenschappen **proces** -en **handle** geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-120">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="8b8dd-121">Houd er rekening mee dat de `$proc` variabele de standaard gegevens bevat die worden geretourneerd door `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="8b8dd-121">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="8b8dd-122">Voor beeld 3: systeem bestanden uitvoeren naar twee logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="8b8dd-122">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="8b8dd-123">In dit voor beeld wordt een lijst met systeem bestanden opgeslagen in twee logboek bestanden, een cumulatief bestand en een actueel bestand.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-123">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="8b8dd-124">De opdracht gebruikt de `Get-ChildItem` cmdlet voor het uitvoeren van een recursieve zoek opdracht voor systeem bestanden op station D:.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-124">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="8b8dd-125">Een pijplijn operator (|) verzendt de lijst naar `Tee-Object` , waarmee de lijst wordt toegevoegd aan het AllSystemFiles.txt-bestand en de lijst wordt door gegeven aan de `Out-File` -cmdlet, waarmee de lijst wordt opgeslagen in het NewSystemFiles.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-125">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="8b8dd-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b8dd-126">PARAMETERS</span></span>

### <span data-ttu-id="8b8dd-127">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="8b8dd-127">-Append</span></span>

<span data-ttu-id="8b8dd-128">Geeft aan dat de cmdlet de uitvoer aan het opgegeven bestand toevoegt.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-128">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="8b8dd-129">Zonder deze para meter vervangt de nieuwe inhoud alle bestaande inhoud in het bestand zonder dat er een waarschuwing wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-129">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="8b8dd-130">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-130">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8b8dd-131">-FilePath</span><span class="sxs-lookup"><span data-stu-id="8b8dd-131">-FilePath</span></span>

<span data-ttu-id="8b8dd-132">Hiermee geeft u een bestand op dat met deze cmdlet het object opslaat in joker tekens, maar moet worden omgezet in één bestand.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-132">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

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

### <span data-ttu-id="8b8dd-133">-Input object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-133">-InputObject</span></span>

<span data-ttu-id="8b8dd-134">Hiermee geeft u het object op dat moet worden opgeslagen en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-134">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="8b8dd-135">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-135">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="8b8dd-136">U kunt ook een object pipet naar `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="8b8dd-136">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="8b8dd-137">Wanneer u de para meter **input object** gebruikt in `Tee-Object` plaats van de resultaten van de pijpleiding opdracht, `Tee-Object` wordt de waarde van **input object** behandeld als één enkel object, zelfs als de waarde een verzameling is.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-137">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

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

### <span data-ttu-id="8b8dd-138">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8b8dd-138">-LiteralPath</span></span>

<span data-ttu-id="8b8dd-139">Hiermee geeft u een bestand op waarvan deze cmdlet het object opslaat.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-139">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="8b8dd-140">In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-140">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="8b8dd-141">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-141">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8b8dd-142">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-142">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8b8dd-143">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-143">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="8b8dd-144">-Variabele</span><span class="sxs-lookup"><span data-stu-id="8b8dd-144">-Variable</span></span>

<span data-ttu-id="8b8dd-145">Hiermee geeft u een variabele op waaraan de cmdlet het object opslaat.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-145">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="8b8dd-146">Geef een naam op voor de variabele zonder het voor gaande dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="8b8dd-146">Enter a variable name without the preceding dollar sign (`$`).</span></span>

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

### <span data-ttu-id="8b8dd-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b8dd-147">CommonParameters</span></span>

<span data-ttu-id="8b8dd-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b8dd-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b8dd-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="8b8dd-150">INPUTS</span></span>

### <span data-ttu-id="8b8dd-151">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8b8dd-151">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8b8dd-152">U kunt objecten door sluizen naar `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="8b8dd-152">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="8b8dd-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8b8dd-153">OUTPUTS</span></span>

### <span data-ttu-id="8b8dd-154">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8b8dd-154">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8b8dd-155">`Tee-Object` retourneert het object dat wordt omgeleid.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-155">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="8b8dd-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8b8dd-156">NOTES</span></span>

<span data-ttu-id="8b8dd-157">U kunt ook de `Out-File` cmdlet of de omleidings operator gebruiken, beide waarmee de uitvoer in een bestand wordt opgeslagen, maar deze niet wordt verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-157">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="8b8dd-158">Vanaf Power shell 6 `Tee-Object` gebruikt de stuk lijst-minder UTF-8-code ring wanneer deze naar bestanden wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="8b8dd-158">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="8b8dd-159">Als u een andere code ring nodig hebt, gebruikt u de `Out-File` cmdlet met de para meter **Encoding** .</span><span class="sxs-lookup"><span data-stu-id="8b8dd-159">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="8b8dd-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8b8dd-160">RELATED LINKS</span></span>

[<span data-ttu-id="8b8dd-161">Compare-object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-161">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="8b8dd-162">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-162">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="8b8dd-163">Groep-object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-163">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="8b8dd-164">Meting object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-164">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="8b8dd-165">New-Object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-165">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="8b8dd-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-166">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="8b8dd-167">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-167">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="8b8dd-168">Where-object</span><span class="sxs-lookup"><span data-stu-id="8b8dd-168">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="8b8dd-169">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="8b8dd-169">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

