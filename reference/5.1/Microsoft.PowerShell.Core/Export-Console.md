---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249966"
---
# <span data-ttu-id="72a8f-103">Export-Console</span><span class="sxs-lookup"><span data-stu-id="72a8f-103">Export-Console</span></span>

## <span data-ttu-id="72a8f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="72a8f-104">SYNOPSIS</span></span>
<span data-ttu-id="72a8f-105">Exporteert de namen van modules in de huidige sessie naar een console bestand.</span><span class="sxs-lookup"><span data-stu-id="72a8f-105">Exports the names of snap-ins in the current session to a console file.</span></span>

## <span data-ttu-id="72a8f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="72a8f-106">SYNTAX</span></span>

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="72a8f-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="72a8f-107">DESCRIPTION</span></span>
<span data-ttu-id="72a8f-108">Met de cmdlet **export-console** exporteert u de namen van de Windows Power shell-modules in de huidige sessie naar een Windows Power shell-console bestand (. psc1).</span><span class="sxs-lookup"><span data-stu-id="72a8f-108">The **Export-Console** cmdlet exports the names of the Windows PowerShell snap-ins in the current session to a Windows PowerShell console file (.psc1).</span></span>
<span data-ttu-id="72a8f-109">U kunt deze cmdlet gebruiken om de modules op te slaan voor gebruik in toekomstige sessies.</span><span class="sxs-lookup"><span data-stu-id="72a8f-109">You can use this cmdlet to save the snap-ins for use in future sessions.</span></span>

<span data-ttu-id="72a8f-110">Als u de modules in het. psc1-console bestand wilt toevoegen aan een sessie, start u Windows Power shell (Powershell.exe) op de opdracht regel met behulp van Cmd.exe of een andere Windows Power shell-sessie en gebruikt u vervolgens de para meter *PSConsoleFile* van Powershell.exe om het console bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="72a8f-110">To add the snap-ins in the .psc1 console file to a session, start Windows PowerShell (Powershell.exe) at the command line by using Cmd.exe or another Windows PowerShell session, and then use the *PSConsoleFile* parameter of Powershell.exe to specify the console file.</span></span>

<span data-ttu-id="72a8f-111">Zie about_PSSnapins voor meer informatie over Windows Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="72a8f-111">For more information about Windows PowerShell snap-ins, see about_PSSnapins.</span></span>

## <span data-ttu-id="72a8f-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="72a8f-112">EXAMPLES</span></span>

### <span data-ttu-id="72a8f-113">Voor beeld 1: de namen van modules in de huidige sessie exporteren</span><span class="sxs-lookup"><span data-stu-id="72a8f-113">Example 1: Export the names of snap-ins in the current session</span></span>

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

<span data-ttu-id="72a8f-114">Met deze opdracht worden de namen van de Windows Power shell-modules in de huidige sessie geëxporteerd naar het bestand ConsoleS1. psc1 in de map consoles van de installatiemap van Windows Power shell, $pshome.</span><span class="sxs-lookup"><span data-stu-id="72a8f-114">This command exports the names of Windows PowerShell snap-ins in the current session to the ConsoleS1.psc1 file in the Consoles folder of the Windows PowerShell installation folder, $pshome.</span></span>

### <span data-ttu-id="72a8f-115">Voor beeld 2: de namen van modules exporteren naar het meest recente console bestand</span><span class="sxs-lookup"><span data-stu-id="72a8f-115">Example 2: Export the names of snap-ins to the most recent console file</span></span>

```
PS C:\> Export-Console
```

<span data-ttu-id="72a8f-116">Met deze opdracht exporteert u de namen van Windows Power shell-modules vanuit de huidige sessie naar het Windows Power shell-console bestand dat het meest recent is gebruikt in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-116">This command exports the names of Windows PowerShell snap-ins from current session to the Windows PowerShell console file that was most recently used in the current session.</span></span>
<span data-ttu-id="72a8f-117">De vorige bestands inhoud wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="72a8f-117">It overwrites the previous file contents.</span></span>

<span data-ttu-id="72a8f-118">Als u tijdens de huidige sessie geen console bestand hebt geëxporteerd, wordt u gevraagd om toestemming te krijgen om door te gaan en vervolgens om een bestands naam te worden gevraagd.</span><span class="sxs-lookup"><span data-stu-id="72a8f-118">If you have not exported a console file during the current session, you are prompted for permission to continue and then prompted for a file name.</span></span>

### <span data-ttu-id="72a8f-119">Voor beeld 3: een module toevoegen en de namen van modules exporteren</span><span class="sxs-lookup"><span data-stu-id="72a8f-119">Example 3: Add a snap-in and export the names of snap-ins</span></span>

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

<span data-ttu-id="72a8f-120">Met deze opdrachten wordt de NewPSSnapin Windows Power shell-module aan de huidige sessie toegevoegd, worden de namen van Windows Power shell-modules in de huidige sessie naar een console bestand geëxporteerd en wordt vervolgens een Windows Power shell-sessie gestart met het console bestand.</span><span class="sxs-lookup"><span data-stu-id="72a8f-120">These commands add the NewPSSnapin Windows PowerShell snap-in to the current session, export the names of Windows PowerShell snap-ins in the current session to a console file, and then start a Windows PowerShell session with the console file.</span></span>

<span data-ttu-id="72a8f-121">De eerste opdracht maakt gebruik van de cmdlet **add-PSSnapin** om de NewPSSnapin-module toe te voegen aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-121">The first command uses the **Add-PSSnapin** cmdlet to add the NewPSSnapin snap-in to the current session.</span></span>
<span data-ttu-id="72a8f-122">U kunt alleen Windows Power shell-modules toevoegen die zijn geregistreerd op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="72a8f-122">You can only add Windows PowerShell snap-ins that are registered on your system.</span></span>

<span data-ttu-id="72a8f-123">Met de tweede opdracht worden de namen van de Windows Power shell-modules geëxporteerd naar het bestand NewPSSnapinConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="72a8f-123">The second command exports the Windows PowerShell snap-in names to the NewPSSnapinConsole.psc1 file.</span></span>

<span data-ttu-id="72a8f-124">Met de derde opdracht start u Windows Power shell met het NewPSSnapinConsole. psc1-bestand.</span><span class="sxs-lookup"><span data-stu-id="72a8f-124">The third command starts Windows PowerShell with the NewPSSnapinConsole.psc1 file.</span></span>
<span data-ttu-id="72a8f-125">Omdat het console bestand de naam van de Windows Power shell-module bevat, zijn de cmdlets en providers in de module beschikbaar in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-125">Because the console file includes the Windows PowerShell snap-in name, the cmdlets and providers in the snap-in are available in the current session.</span></span>

### <span data-ttu-id="72a8f-126">Voor beeld 4: namen van modules exporteren naar een opgegeven locatie</span><span class="sxs-lookup"><span data-stu-id="72a8f-126">Example 4: Export names of snap-ins to a specified location</span></span>

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

<span data-ttu-id="72a8f-127">Met deze opdracht worden de namen van de Windows Power shell-modules in de huidige sessie geëxporteerd naar het Console01. psc1-bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="72a8f-127">This command exports the names of the Windows PowerShell snap-ins in the current session to the Console01.psc1 file in the current directory.</span></span>

<span data-ttu-id="72a8f-128">Met de tweede opdracht wordt de inhoud van het bestand Console01. psc1 in Klad blok weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="72a8f-128">The second command displays the contents of the Console01.psc1 file in Notepad.</span></span>

### <span data-ttu-id="72a8f-129">Voor beeld 5: bepalen welk console bestand moet worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="72a8f-129">Example 5: Determine the console file to update</span></span>

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

<span data-ttu-id="72a8f-130">In dit voor beeld ziet u hoe u de $ConsoleFileName Automatic-variabele gebruikt om het console bestand te bepalen dat wordt bijgewerkt als u **exporteren-console** gebruikt zonder een para meter voor het *pad* .</span><span class="sxs-lookup"><span data-stu-id="72a8f-130">This example shows how to use the $ConsoleFileName automatic variable to determine the console file that will be updated if you use **Export-Console** without a *Path* parameter value.</span></span>

<span data-ttu-id="72a8f-131">De eerste opdracht maakt gebruik van de *PSConsoleFile* -para meter van PowerShell.exe om Windows Power shell te openen met het bestand Console01. psc1.</span><span class="sxs-lookup"><span data-stu-id="72a8f-131">The first command uses the *PSConsoleFile* parameter of PowerShell.exe to open Windows PowerShell with the Console01.psc1 file.</span></span>

<span data-ttu-id="72a8f-132">De tweede opdracht maakt gebruik van de cmdlet **add-PSSnapin** om de MySnapin Windows Power shell-module toe te voegen aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-132">The second command uses the **Add-PSSnapin** cmdlet to add the MySnapin Windows PowerShell snap-in to the current session.</span></span>

<span data-ttu-id="72a8f-133">De derde opdracht maakt gebruik van de cmdlet **export-console** om de namen van alle Windows Power shell-modules in de sessie te exporteren naar het bestand NewConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="72a8f-133">The third command uses the **Export-Console** cmdlet to export the names of all the Windows PowerShell snap-ins in the session to the NewConsole.psc1 file.</span></span>

<span data-ttu-id="72a8f-134">Met de vierde opdracht wordt de $ConsoleFileName variabele weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="72a8f-134">The fourth command displays the $ConsoleFileName variable.</span></span>
<span data-ttu-id="72a8f-135">Het bevat het meest recent gebruikte console bestand.</span><span class="sxs-lookup"><span data-stu-id="72a8f-135">It contains the most recently used console file.</span></span>
<span data-ttu-id="72a8f-136">In de voorbeeld uitvoer ziet u dat NewConsole.ps1 het meest recent gebruikte bestand is.</span><span class="sxs-lookup"><span data-stu-id="72a8f-136">The sample output shows that NewConsole.ps1 is the most recently used file.</span></span>

<span data-ttu-id="72a8f-137">De vijfde opdracht voegt SnapIn03 toe aan de huidige console.</span><span class="sxs-lookup"><span data-stu-id="72a8f-137">The fifth command adds SnapIn03 to the current console.</span></span>

<span data-ttu-id="72a8f-138">De zesde opdracht maakt gebruik van de cmdlet **export-console** zonder een *Path* -para meter.</span><span class="sxs-lookup"><span data-stu-id="72a8f-138">The sixth command uses the **Export-Console** cmdlet without a *Path* parameter.</span></span>
<span data-ttu-id="72a8f-139">Met deze opdracht worden de namen van alle Windows Power shell-modules in de huidige sessie geëxporteerd naar het laatst gebruikte bestand, NewConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="72a8f-139">This command exports the names of all the Windows PowerShell snap-ins in the current session to the most recently used file, NewConsole.psc1.</span></span>

## <span data-ttu-id="72a8f-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72a8f-140">PARAMETERS</span></span>

### <span data-ttu-id="72a8f-141">-Force</span><span class="sxs-lookup"><span data-stu-id="72a8f-141">-Force</span></span>
<span data-ttu-id="72a8f-142">Geeft aan dat met deze cmdlet de gegevens in een console bestand worden overschreven zonder dat er een waarschuwing wordt gegeven, zelfs als het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="72a8f-142">Indicates that this cmdlet overwrites the data in a console file without warning, even if the file has the read-only attribute.</span></span>
<span data-ttu-id="72a8f-143">Het kenmerk alleen-lezen wordt gewijzigd en wordt niet opnieuw ingesteld wanneer de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="72a8f-143">The read-only attribute is changed and is not reset when the command finishes.</span></span>

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

### <span data-ttu-id="72a8f-144">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="72a8f-144">-NoClobber</span></span>
<span data-ttu-id="72a8f-145">Geeft aan dat deze cmdlet een bestaand console bestand niet overschrijft.</span><span class="sxs-lookup"><span data-stu-id="72a8f-145">Indicates that this cmdlet does not overwrite  an existing console file.</span></span>
<span data-ttu-id="72a8f-146">Als er een bestand in het opgegeven pad voor komt, wordt het bestand standaard zonder waarschuwing overschreven door de **console exporteren** .</span><span class="sxs-lookup"><span data-stu-id="72a8f-146">By default, if a file occurs in the specified path, **Export-Console** overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72a8f-147">-Path</span><span class="sxs-lookup"><span data-stu-id="72a8f-147">-Path</span></span>
<span data-ttu-id="72a8f-148">Hiermee geeft u een pad en een bestands naam voor het console bestand (\*. psc1).</span><span class="sxs-lookup"><span data-stu-id="72a8f-148">Specifies a path and file name for the console file (\*.psc1).</span></span>
<span data-ttu-id="72a8f-149">Voer een optioneel pad en een naam in.</span><span class="sxs-lookup"><span data-stu-id="72a8f-149">Enter an optional path and name.</span></span>
<span data-ttu-id="72a8f-150">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="72a8f-150">Wildcard characters are not permitted.</span></span>

<span data-ttu-id="72a8f-151">Als u alleen een bestands naam opgeeft, maakt **exporteren-console** een bestand met die naam en de bestandsnaam extensie. psc1 in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="72a8f-151">If you specify only a file name, **Export-Console** creates a file that has that name and the .psc1 file name extension in the current directory.</span></span>

<span data-ttu-id="72a8f-152">Deze para meter is vereist tenzij u Windows Power shell hebt geopend met de para meter *PSConsoleFile* of een console bestand hebt geëxporteerd tijdens de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-152">This parameter is required unless you have opened Windows PowerShell with the *PSConsoleFile* parameter or exported a console file during the current session.</span></span>
<span data-ttu-id="72a8f-153">Het is ook vereist wanneer u de para meter *NoClobber* gebruikt om te voor komen dat het huidige console bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="72a8f-153">It is also required when you use the *NoClobber* parameter to prevent the current console file from being overwritten.</span></span>

<span data-ttu-id="72a8f-154">Als u deze para meter weglaat, wordt het console bestand dat het meest recent is gebruikt in deze sessie overschreven door de **console** .</span><span class="sxs-lookup"><span data-stu-id="72a8f-154">If you omit this parameter, **Export-Console** overwrites the console file that was used most recently in this session.</span></span>
<span data-ttu-id="72a8f-155">Het pad van het meest recent gebruikte console bestand wordt opgeslagen in de waarde van de $ConsoleFileName automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="72a8f-155">The path of the most recently used console file is stored in the value of the $ConsoleFileName automatic variable.</span></span>
<span data-ttu-id="72a8f-156">Zie about_Automatic_Variables voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-156">For more information, see about_Automatic_Variables.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="72a8f-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="72a8f-157">-Confirm</span></span>
<span data-ttu-id="72a8f-158">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="72a8f-158">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72a8f-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="72a8f-159">-WhatIf</span></span>
<span data-ttu-id="72a8f-160">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="72a8f-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="72a8f-161">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="72a8f-161">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="72a8f-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72a8f-162">CommonParameters</span></span>
<span data-ttu-id="72a8f-163">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72a8f-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72a8f-164">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72a8f-165">INVOER</span><span class="sxs-lookup"><span data-stu-id="72a8f-165">INPUTS</span></span>

### <span data-ttu-id="72a8f-166">System. String</span><span class="sxs-lookup"><span data-stu-id="72a8f-166">System.String</span></span>
<span data-ttu-id="72a8f-167">U kunt een padtekenreeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72a8f-167">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="72a8f-168">UITVOER</span><span class="sxs-lookup"><span data-stu-id="72a8f-168">OUTPUTS</span></span>

### <span data-ttu-id="72a8f-169">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="72a8f-169">System.IO.FileInfo</span></span>
<span data-ttu-id="72a8f-170">Met deze cmdlet wordt een bestand gemaakt dat de geëxporteerde aliassen bevat.</span><span class="sxs-lookup"><span data-stu-id="72a8f-170">This cmdlet creates a file that contains the exported aliases.</span></span>

## <span data-ttu-id="72a8f-171">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="72a8f-171">NOTES</span></span>

* <span data-ttu-id="72a8f-172">Wanneer een console bestand (. psc1) wordt gebruikt om de sessie te starten, wordt de naam van het console bestand automatisch opgeslagen in de automatische variabele $ConsoleFileName.</span><span class="sxs-lookup"><span data-stu-id="72a8f-172">When a console file (.psc1) is used to start the session, the name of the console file is automatically stored in the $ConsoleFileName automatic variable.</span></span> <span data-ttu-id="72a8f-173">De waarde van $ConsoleFileName wordt bijgewerkt wanneer u de para meter *Path* van **export-console** gebruikt om een nieuw console bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="72a8f-173">The value of $ConsoleFileName is updated when you use the *Path* parameter of **Export-Console** to specify a new console file.</span></span> <span data-ttu-id="72a8f-174">Als er geen console bestand wordt gebruikt, heeft $ConsoleFileName geen waarde ($Null).</span><span class="sxs-lookup"><span data-stu-id="72a8f-174">When no console file is used, $ConsoleFileName has no value ($Null).</span></span>

  <span data-ttu-id="72a8f-175">Als u een Windows Power shell-console bestand wilt gebruiken in een nieuwe sessie, gebruikt u de volgende syntaxis om Windows Power shell te starten:</span><span class="sxs-lookup"><span data-stu-id="72a8f-175">To use a Windows PowerShell console file in a new session, use the following syntax to start Windows PowerShell:</span></span>

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  <span data-ttu-id="72a8f-176">U kunt ook Windows Power shell-modules voor toekomstige sessies opslaan door een Add-PSSnapin-opdracht toe te voegen aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="72a8f-176">You can also save Windows PowerShell snap-ins for future sessions by adding an Add-PSSnapin command to your Windows PowerShell profile.</span></span>
<span data-ttu-id="72a8f-177">Zie about_Profiles voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72a8f-177">For more information, see about_Profiles.</span></span>


## <span data-ttu-id="72a8f-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="72a8f-178">RELATED LINKS</span></span>

[<span data-ttu-id="72a8f-179">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="72a8f-179">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="72a8f-180">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="72a8f-180">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="72a8f-181">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="72a8f-181">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
