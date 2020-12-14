---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706026"
---
# <span data-ttu-id="f597f-102">Split-Path</span><span class="sxs-lookup"><span data-stu-id="f597f-102">Split-Path</span></span>

## <span data-ttu-id="f597f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f597f-103">SYNOPSIS</span></span>
<span data-ttu-id="f597f-104">Retourneert het opgegeven deel van een pad.</span><span class="sxs-lookup"><span data-stu-id="f597f-104">Returns the specified part of a path.</span></span>

## <span data-ttu-id="f597f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f597f-105">SYNTAX</span></span>

### <span data-ttu-id="f597f-106">Bovenliggendeset (standaard)</span><span class="sxs-lookup"><span data-stu-id="f597f-106">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f597f-107">Blade</span><span class="sxs-lookup"><span data-stu-id="f597f-107">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="f597f-108">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="f597f-108">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f597f-109">Uitbreidingsset</span><span class="sxs-lookup"><span data-stu-id="f597f-109">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f597f-110">Kwalificatieset</span><span class="sxs-lookup"><span data-stu-id="f597f-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f597f-111">Geen Kwalificatieset</span><span class="sxs-lookup"><span data-stu-id="f597f-111">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f597f-112">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="f597f-112">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f597f-113">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="f597f-113">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="f597f-114">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f597f-114">DESCRIPTION</span></span>

<span data-ttu-id="f597f-115">De `Split-Path` cmdlet retourneert alleen het opgegeven deel van een pad, zoals de bovenliggende map, een submap of een bestands naam.</span><span class="sxs-lookup"><span data-stu-id="f597f-115">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="f597f-116">Er kunnen ook items worden opgehaald waarnaar wordt verwezen door het Splits pad en te zien of het pad relatief of absoluut is.</span><span class="sxs-lookup"><span data-stu-id="f597f-116">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="f597f-117">U kunt deze cmdlet gebruiken om alleen een geselecteerd deel van een pad op te halen of in te dienen.</span><span class="sxs-lookup"><span data-stu-id="f597f-117">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="f597f-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f597f-118">EXAMPLES</span></span>

### <span data-ttu-id="f597f-119">Voor beeld 1: de kwalificatie van een pad ophalen</span><span class="sxs-lookup"><span data-stu-id="f597f-119">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="f597f-120">Met deze opdracht wordt alleen de kwalificatie van het pad geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f597f-120">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="f597f-121">De kwalificatie is het station.</span><span class="sxs-lookup"><span data-stu-id="f597f-121">The qualifier is the drive.</span></span>

### <span data-ttu-id="f597f-122">Voor beeld 2: bestands namen weer geven</span><span class="sxs-lookup"><span data-stu-id="f597f-122">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="f597f-123">Met deze opdracht worden de bestanden weer gegeven waarnaar wordt verwezen door het Splits pad.</span><span class="sxs-lookup"><span data-stu-id="f597f-123">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="f597f-124">Omdat dit pad wordt gesplitst naar het laatste item, ook wel het Leaf genoemd, worden in de opdracht alleen de bestands namen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f597f-124">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="f597f-125">De para meter **resolver** geeft `Split-Path` aan dat de items waarnaar het Splits pad verwijst, worden weer gegeven in plaats van het Splits pad weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f597f-125">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="f597f-126">Net als alle `Split-Path` opdrachten retourneert deze opdracht teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f597f-126">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="f597f-127">Er worden geen **file info** -objecten geretourneerd die de bestanden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="f597f-127">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="f597f-128">Voor beeld 3: de bovenliggende container ophalen</span><span class="sxs-lookup"><span data-stu-id="f597f-128">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="f597f-129">Met deze opdracht worden alleen de bovenliggende containers van het pad geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f597f-129">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="f597f-130">Omdat het geen para meters bevat om de splitsing op te geven, `Split-Path` gebruikt de standaard locatie van de Splits site, die **ouder** is.</span><span class="sxs-lookup"><span data-stu-id="f597f-130">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent**.</span></span>

### <span data-ttu-id="f597f-131">Voor beeld 4: Hiermee wordt bepaald of een pad absoluut is</span><span class="sxs-lookup"><span data-stu-id="f597f-131">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="f597f-132">Met deze opdracht bepaalt u of het pad relatief of absoluut is.</span><span class="sxs-lookup"><span data-stu-id="f597f-132">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="f597f-133">In dit geval, omdat het pad relatief is ten opzichte van de huidige map, die wordt vertegenwoordigd door een punt ( `.` ), wordt geretourneerd `$False` .</span><span class="sxs-lookup"><span data-stu-id="f597f-133">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="f597f-134">Voor beeld 5: locatie wijzigen naar een opgegeven pad</span><span class="sxs-lookup"><span data-stu-id="f597f-134">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="f597f-135">Met deze opdracht wordt uw locatie gewijzigd in de map met het Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="f597f-135">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="f597f-136">De opdracht tussen haakjes wordt gebruikt `Split-Path` om alleen het bovenliggende item te retour neren van het pad dat is opgeslagen in de ingebouwde `$Profile` variabele.</span><span class="sxs-lookup"><span data-stu-id="f597f-136">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="f597f-137">De **bovenliggende** para meter is de standaard waarde voor de Splits locatie.</span><span class="sxs-lookup"><span data-stu-id="f597f-137">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="f597f-138">Daarom kunt u deze uit de opdracht weglaten.</span><span class="sxs-lookup"><span data-stu-id="f597f-138">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="f597f-139">De haakjes direct Power shell om de opdracht eerst uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f597f-139">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="f597f-140">Dit is een handige manier om over te stappen op een map met een lange padnaam.</span><span class="sxs-lookup"><span data-stu-id="f597f-140">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="f597f-141">Voor beeld 6: een pad splitsen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="f597f-141">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="f597f-142">Met deze opdracht wordt een pijplijn operator ( `|` ) gebruikt om een pad naar te verzenden `Split-Path` .</span><span class="sxs-lookup"><span data-stu-id="f597f-142">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="f597f-143">Het pad wordt tussen aanhalings tekens geplaatst om aan te geven dat het een enkel token is.</span><span class="sxs-lookup"><span data-stu-id="f597f-143">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="f597f-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f597f-144">PARAMETERS</span></span>

### <span data-ttu-id="f597f-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="f597f-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f597f-146">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="f597f-146">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="f597f-147">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f597f-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-148">-Extensie</span><span class="sxs-lookup"><span data-stu-id="f597f-148">-Extension</span></span>

<span data-ttu-id="f597f-149">Geeft aan dat deze cmdlet alleen de uitbrei ding van het blad retourneert.</span><span class="sxs-lookup"><span data-stu-id="f597f-149">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="f597f-150">In het pad retourneert de waarde bijvoorbeeld `C:\Test\Logs\Pass1.log` alleen `.log` .</span><span class="sxs-lookup"><span data-stu-id="f597f-150">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="f597f-151">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f597f-151">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-152">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="f597f-152">-IsAbsolute</span></span>

<span data-ttu-id="f597f-153">Geeft aan dat deze cmdlet $True retourneert als het pad absoluut is en $False als het relatief is.</span><span class="sxs-lookup"><span data-stu-id="f597f-153">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="f597f-154">Een absoluut pad heeft een lengte die groter is dan nul en gebruikt geen punt ( `.` ) om het huidige pad aan te geven.</span><span class="sxs-lookup"><span data-stu-id="f597f-154">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-155">-Leaf</span><span class="sxs-lookup"><span data-stu-id="f597f-155">-Leaf</span></span>

<span data-ttu-id="f597f-156">Geeft aan dat deze cmdlet alleen de laatste item of container in het pad retourneert.</span><span class="sxs-lookup"><span data-stu-id="f597f-156">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="f597f-157">In het pad `C:\Test\Logs\Pass1.log` retourneert bijvoorbeeld alleen Pass1. log.</span><span class="sxs-lookup"><span data-stu-id="f597f-157">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-158">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="f597f-158">-LeafBase</span></span>

<span data-ttu-id="f597f-159">Geeft aan dat deze cmdlet alleen de basis naam van het blad retourneert.</span><span class="sxs-lookup"><span data-stu-id="f597f-159">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="f597f-160">In het pad retourneert de waarde bijvoorbeeld `C:\Test\Logs\Pass1.log` alleen `Pass1` .</span><span class="sxs-lookup"><span data-stu-id="f597f-160">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="f597f-161">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f597f-161">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f597f-162">-LiteralPath</span></span>

<span data-ttu-id="f597f-163">Hiermee geeft u de paden op die moeten worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="f597f-163">Specifies the paths to be split.</span></span> <span data-ttu-id="f597f-164">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f597f-164">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="f597f-165">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f597f-165">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="f597f-166">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f597f-166">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f597f-167">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="f597f-167">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-168">-Indicator</span><span class="sxs-lookup"><span data-stu-id="f597f-168">-NoQualifier</span></span>

<span data-ttu-id="f597f-169">Geeft aan dat deze cmdlet het pad retourneert zonder de kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="f597f-169">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="f597f-170">Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals `C:` of `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="f597f-170">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="f597f-171">In het pad retourneert de waarde bijvoorbeeld `C:\Test\Logs\Pass1.log` alleen `\Test\Logs\Pass1.log` .</span><span class="sxs-lookup"><span data-stu-id="f597f-171">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-172">-Bovenliggend item</span><span class="sxs-lookup"><span data-stu-id="f597f-172">-Parent</span></span>

<span data-ttu-id="f597f-173">Geeft aan dat deze cmdlet alleen de bovenliggende containers van het item of de container retourneert die door het pad worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f597f-173">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="f597f-174">In het pad retourneert het bijvoorbeeld `C:\Test\Logs\Pass1.log` `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="f597f-174">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="f597f-175">De **bovenliggende** para meter is de standaard waarde voor de Splits locatie.</span><span class="sxs-lookup"><span data-stu-id="f597f-175">The **Parent** parameter is the default split location parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-176">-Path</span><span class="sxs-lookup"><span data-stu-id="f597f-176">-Path</span></span>

<span data-ttu-id="f597f-177">Hiermee geeft u de paden op die moeten worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="f597f-177">Specifies the paths to be split.</span></span> <span data-ttu-id="f597f-178">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f597f-178">Wildcard characters are permitted.</span></span> <span data-ttu-id="f597f-179">Als het pad spaties bevat, plaatst u het tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f597f-179">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="f597f-180">U kunt ook een pad naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="f597f-180">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f597f-181">-Kwalificatie</span><span class="sxs-lookup"><span data-stu-id="f597f-181">-Qualifier</span></span>

<span data-ttu-id="f597f-182">Geeft aan dat met deze cmdlet alleen de kwalificatie van het opgegeven pad wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f597f-182">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="f597f-183">Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals `C:` of `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="f597f-183">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f597f-184">-Oplossen</span><span class="sxs-lookup"><span data-stu-id="f597f-184">-Resolve</span></span>

<span data-ttu-id="f597f-185">Geeft aan dat met deze cmdlet de items worden weer gegeven waarnaar wordt verwezen door het resulterende Splits pad in plaats van de elementen van het pad weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f597f-185">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="f597f-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f597f-186">CommonParameters</span></span>

<span data-ttu-id="f597f-187">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f597f-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f597f-188">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f597f-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f597f-189">INVOER</span><span class="sxs-lookup"><span data-stu-id="f597f-189">INPUTS</span></span>

### <span data-ttu-id="f597f-190">System. String</span><span class="sxs-lookup"><span data-stu-id="f597f-190">System.String</span></span>

<span data-ttu-id="f597f-191">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="f597f-191">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="f597f-192">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f597f-192">OUTPUTS</span></span>

### <span data-ttu-id="f597f-193">System. String, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="f597f-193">System.String, System.Boolean</span></span>

<span data-ttu-id="f597f-194">`Split-Path` Retourneert tekst teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f597f-194">`Split-Path` returns text strings.</span></span> <span data-ttu-id="f597f-195">Wanneer u de para meter voor het **oplossen** opgeeft, `Split-Path` retourneert een teken reeks die de locatie van de items beschrijft; deze retourneert geen objecten die de items vertegenwoordigen, zoals een **file info** -of **RegistryKey** -object.</span><span class="sxs-lookup"><span data-stu-id="f597f-195">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="f597f-196">Wanneer u de para meter **IsAbsolute** opgeeft, `Split-Path` wordt een **Booleaanse** waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f597f-196">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="f597f-197">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f597f-197">NOTES</span></span>

- <span data-ttu-id="f597f-198">De para meters voor de Splits locatie (**Kwalificatie**, **bovenliggend element**, **uitbrei ding**, **blad**, **LeafBase** en geen **Kwalificatie**) zijn exclusief.</span><span class="sxs-lookup"><span data-stu-id="f597f-198">The split location parameters (**Qualifier**, **Parent**, **Extension**, **Leaf**, **LeafBase**, and **NoQualifier**) are exclusive.</span></span> <span data-ttu-id="f597f-199">U kunt slechts één in elke opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f597f-199">You can use only one in each command.</span></span>

- <span data-ttu-id="f597f-200">De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="f597f-200">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="f597f-201">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="f597f-201">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="f597f-202">U kunt ze gebruiken op de manier waarop u **mapnaam**, **Normpath**, **realpath**, **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f597f-202">Use them in the way that you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

- <span data-ttu-id="f597f-203">U kunt de **pad** -cmdlets samen met verschillende providers gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f597f-203">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="f597f-204">Dit zijn onder andere het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="f597f-204">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="f597f-205">`Split-Path` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f597f-205">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f597f-206">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="f597f-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f597f-207">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f597f-207">For more information, see about_Providers.</span></span>

## <span data-ttu-id="f597f-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f597f-208">RELATED LINKS</span></span>

[<span data-ttu-id="f597f-209">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="f597f-209">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="f597f-210">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="f597f-210">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="f597f-211">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="f597f-211">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="f597f-212">Test-pad</span><span class="sxs-lookup"><span data-stu-id="f597f-212">Test-Path</span></span>](Test-Path.md)
