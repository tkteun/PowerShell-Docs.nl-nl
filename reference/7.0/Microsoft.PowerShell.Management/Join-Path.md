---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 3f9859a7d78ae9daf43b1d72df26ac30d2d551cd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249461"
---
# <span data-ttu-id="2d4de-103">Join-Path</span><span class="sxs-lookup"><span data-stu-id="2d4de-103">Join-Path</span></span>

## <span data-ttu-id="2d4de-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2d4de-104">SYNOPSIS</span></span>
<span data-ttu-id="2d4de-105">Hiermee wordt een pad en een onderliggend pad gecombineerd tot één pad.</span><span class="sxs-lookup"><span data-stu-id="2d4de-105">Combines a path and a child path into a single path.</span></span>

## <span data-ttu-id="2d4de-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2d4de-106">SYNTAX</span></span>

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="2d4de-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2d4de-107">DESCRIPTION</span></span>

<span data-ttu-id="2d4de-108">De `Join-Path` cmdlet combineert een pad en een onderliggend pad naar één pad.</span><span class="sxs-lookup"><span data-stu-id="2d4de-108">The `Join-Path` cmdlet combines a path and child-path into a single path.</span></span>
<span data-ttu-id="2d4de-109">De provider levert de pad-scheidings tekens.</span><span class="sxs-lookup"><span data-stu-id="2d4de-109">The provider supplies the path delimiters.</span></span>

## <span data-ttu-id="2d4de-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2d4de-110">EXAMPLES</span></span>

### <span data-ttu-id="2d4de-111">Voor beeld 1: een pad met een onderliggend pad combi neren</span><span class="sxs-lookup"><span data-stu-id="2d4de-111">Example 1: Combine a path with a child path</span></span>

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

<span data-ttu-id="2d4de-112">Met deze opdracht wordt gebruikt `Join-Path` om een pad te combi neren met een childpath.</span><span class="sxs-lookup"><span data-stu-id="2d4de-112">This command uses `Join-Path` to combine a path with a childpath.</span></span>

<span data-ttu-id="2d4de-113">Omdat de opdracht wordt uitgevoerd vanuit de `FileSystem` provider, wordt het `\` scheidings teken geleverd om lid te worden van de paden.</span><span class="sxs-lookup"><span data-stu-id="2d4de-113">Since the command is executed from the `FileSystem` provider, it provides the `\` delimiter to join the paths.</span></span>

### <span data-ttu-id="2d4de-114">Voor beeld 2: paden combi neren die al Directory scheidings tekens bevatten</span><span class="sxs-lookup"><span data-stu-id="2d4de-114">Example 2: Combine paths that already contain directory separators</span></span>

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

<span data-ttu-id="2d4de-115">Bestaande mappen gescheiden `\` en afgehandeld, zodat er slechts één schei ding is tussen `Path` en `ChildPath`</span><span class="sxs-lookup"><span data-stu-id="2d4de-115">Existing directory separators `\` and handled so there is only one separator between `Path` and `ChildPath`</span></span>

### <span data-ttu-id="2d4de-116">Voor beeld 3: bestanden en mappen weer geven door een pad met een onderliggend pad samen te voegen</span><span class="sxs-lookup"><span data-stu-id="2d4de-116">Example 3: Display files and folders by joining a path with a child path</span></span>

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

<span data-ttu-id="2d4de-117">Met deze opdracht worden de bestanden en mappen waarnaar wordt verwezen, weer gegeven door de C:\Win- \* pad en het onderliggende pad van het systeem samen te voegen \* .</span><span class="sxs-lookup"><span data-stu-id="2d4de-117">This command displays the files and folders that are referenced by joining the C:\Win\* path and the System\* child path.</span></span>
<span data-ttu-id="2d4de-118">De bestanden en mappen worden weer gegeven als `Get-ChildItem` , maar het volledig gekwalificeerde pad naar elk item wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2d4de-118">It displays the same files and folders as `Get-ChildItem`, but it displays the fully qualified path to each item.</span></span>
<span data-ttu-id="2d4de-119">In deze opdracht worden de `Path` namen van de en `ChildPath` optionele para meters wegge laten.</span><span class="sxs-lookup"><span data-stu-id="2d4de-119">In this command, the `Path` and `ChildPath` optional parameter names are omitted.</span></span>

### <span data-ttu-id="2d4de-120">Voor beeld 4: Join-Path gebruiken met de register provider van Power shell</span><span class="sxs-lookup"><span data-stu-id="2d4de-120">Example 4: Use Join-Path with the PowerShell registry provider</span></span>

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

<span data-ttu-id="2d4de-121">Met deze opdracht worden de register sleutels in de `HKLM\System` register sleutel met de volgende inhoud weer gegeven `ControlSet` .</span><span class="sxs-lookup"><span data-stu-id="2d4de-121">This command displays the registry keys in the `HKLM\System` registry subkey that include `ControlSet`.</span></span>

<span data-ttu-id="2d4de-122">De `Resolve` para meter, probeert het gekoppelde pad op te lossen, inclusief joker tekens van het huidige pad naar de provider `HKLM:\`</span><span class="sxs-lookup"><span data-stu-id="2d4de-122">The `Resolve` parameter, attempts to resolve the joined path, including wildcards from the current provider path `HKLM:\`</span></span>

### <span data-ttu-id="2d4de-123">Voor beeld 5: meerdere paden met een onderliggend pad combi neren</span><span class="sxs-lookup"><span data-stu-id="2d4de-123">Example 5: Combine multiple path roots with a child path</span></span>

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

<span data-ttu-id="2d4de-124">Met deze opdracht wordt gebruikt `Join-Path` om meerdere paden te combi neren met een onderliggend pad.</span><span class="sxs-lookup"><span data-stu-id="2d4de-124">This command uses `Join-Path` to combine multiple path roots with a child path.</span></span>

> [!NOTE]
> <span data-ttu-id="2d4de-125">De stations die door `Path` moeten worden opgegeven, bestaan of de samen voeging van dat item mislukt.</span><span class="sxs-lookup"><span data-stu-id="2d4de-125">The Drives specified by `Path` must exist or the join of that entry will fail.</span></span>

### <span data-ttu-id="2d4de-126">Voor beeld 6: de hoofd mappen van een bestandssysteem station met een onderliggend pad combi neren</span><span class="sxs-lookup"><span data-stu-id="2d4de-126">Example 6: Combine the roots of a file system drive with a child path</span></span>

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

<span data-ttu-id="2d4de-127">Met deze opdracht worden de hoofd mappen van elk systeem station van het Power shell-bestand in de-console gecombineerd met het onderliggende subdir-pad.</span><span class="sxs-lookup"><span data-stu-id="2d4de-127">This command combines the roots of each PowerShell file system drive in the console with the Subdir child path.</span></span>

<span data-ttu-id="2d4de-128">De opdracht gebruikt de `Get-PSDrive` cmdlet om de Power Shell-stations op te halen die worden ondersteund door de File System-Provider.</span><span class="sxs-lookup"><span data-stu-id="2d4de-128">The command uses the `Get-PSDrive` cmdlet to get the PowerShell drives supported by the FileSystem provider.</span></span>
<span data-ttu-id="2d4de-129">De `ForEach-Object` instructie selecteert alleen de hoofd eigenschap van de `PSDriveInfo` objecten en combineert deze met het opgegeven onderliggende pad.</span><span class="sxs-lookup"><span data-stu-id="2d4de-129">The `ForEach-Object` statement selects only the Root property of the `PSDriveInfo` objects and combines it with the specified child path.</span></span>

<span data-ttu-id="2d4de-130">In de uitvoer ziet u dat de Power Shell-stations op de computer een station bevatten dat is toegewezen aan de map C:\Program Files.</span><span class="sxs-lookup"><span data-stu-id="2d4de-130">The output shows that the PowerShell drives on the computer included a drive mapped to the C:\Program Files directory.</span></span>

### <span data-ttu-id="2d4de-131">Voor beeld 7: een onbeperkt aantal paden combi neren</span><span class="sxs-lookup"><span data-stu-id="2d4de-131">Example 7: Combine an indefinite number of paths</span></span>

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

<span data-ttu-id="2d4de-132">`AdditionalChildPath`Met de para meter kan een onbeperkt aantal paden worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="2d4de-132">The `AdditionalChildPath` parameter allows the joining of an unlimited number of paths.</span></span>

<span data-ttu-id="2d4de-133">In dit voor beeld worden geen parameter namen gebruikt, waardoor "a" bindt naar `Path` , "b" naar `ChildPath` en "c-g" om `AdditionalChildPath`</span><span class="sxs-lookup"><span data-stu-id="2d4de-133">In this example, no parameter names are used, thus "a" binds to `Path`, "b" to `ChildPath` and "c-g" to `AdditionalChildPath`</span></span>

## <span data-ttu-id="2d4de-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d4de-134">PARAMETERS</span></span>

### <span data-ttu-id="2d4de-135">-AdditionalChildPath</span><span class="sxs-lookup"><span data-stu-id="2d4de-135">-AdditionalChildPath</span></span>

<span data-ttu-id="2d4de-136">Hiermee geeft u extra elementen op die moeten worden toegevoegd aan de waarde van de para meter *Path* .</span><span class="sxs-lookup"><span data-stu-id="2d4de-136">Specifies additional elements to append to the value of the *Path* parameter.</span></span> <span data-ttu-id="2d4de-137">De `ChildPath` para meter is nog steeds verplicht en moet ook worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2d4de-137">The `ChildPath` parameter is still mandatory and must be specified as well.</span></span>

<span data-ttu-id="2d4de-138">Deze para meter wordt opgegeven met de `ValueFromRemainingArguments` eigenschap waarmee een onbeperkt aantal paden kan worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2d4de-138">This parameter is specified with the `ValueFromRemainingArguments` property which enables joining an indefinite number of paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2d4de-139">-ChildPath</span><span class="sxs-lookup"><span data-stu-id="2d4de-139">-ChildPath</span></span>

<span data-ttu-id="2d4de-140">Hiermee geeft u de elementen die moeten worden toegevoegd aan de waarde van de `Path` para meter.</span><span class="sxs-lookup"><span data-stu-id="2d4de-140">Specifies the elements to append to the value of the `Path` parameter.</span></span>
<span data-ttu-id="2d4de-141">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2d4de-141">Wildcards are permitted.</span></span>
<span data-ttu-id="2d4de-142">De `ChildPath` para meter is vereist, hoewel de parameter naam ("ChildPath") optioneel is.</span><span class="sxs-lookup"><span data-stu-id="2d4de-142">The `ChildPath` parameter is required, although the parameter name ("ChildPath") is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2d4de-143">-Credential</span><span class="sxs-lookup"><span data-stu-id="2d4de-143">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2d4de-144">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="2d4de-144">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2d4de-145">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2d4de-145">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2d4de-146">-Path</span><span class="sxs-lookup"><span data-stu-id="2d4de-146">-Path</span></span>

<span data-ttu-id="2d4de-147">Hiermee geeft u de hoofd paden (of paden) waaraan het onderliggende pad wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2d4de-147">Specifies the main path (or paths) to which the child-path is appended.</span></span>
<span data-ttu-id="2d4de-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2d4de-148">Wildcards are permitted.</span></span>

<span data-ttu-id="2d4de-149">De waarde van `Path` bepaalt welke provider wordt gekoppeld aan de paden en voegt de scheidings tekens voor het pad toe.</span><span class="sxs-lookup"><span data-stu-id="2d4de-149">The value of `Path` determines which provider joins the paths and adds the path delimiters.</span></span>
<span data-ttu-id="2d4de-150">De `Path` para meter is vereist, hoewel de parameter naam ("pad") optioneel is.</span><span class="sxs-lookup"><span data-stu-id="2d4de-150">The `Path` parameter is required, although the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2d4de-151">-Oplossen</span><span class="sxs-lookup"><span data-stu-id="2d4de-151">-Resolve</span></span>

<span data-ttu-id="2d4de-152">Geeft aan dat deze cmdlet het gekoppelde pad van de huidige provider moet proberen op te lossen.</span><span class="sxs-lookup"><span data-stu-id="2d4de-152">Indicates that this cmdlet should attempt to resolve the joined path from the current provider.</span></span>

- <span data-ttu-id="2d4de-153">Als joker tekens worden gebruikt, retourneert de cmdlet alle paden die overeenkomen met het gekoppelde pad.</span><span class="sxs-lookup"><span data-stu-id="2d4de-153">If wildcards are used, the cmdlet returns all paths that match the joined path.</span></span>
- <span data-ttu-id="2d4de-154">Als **er geen** joker tekens worden gebruikt, treedt er een fout op in de cmdlet als het pad niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="2d4de-154">If **no** wildcards are used, the cmdlet will error if the path does not exist.</span></span>

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

### <span data-ttu-id="2d4de-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d4de-155">CommonParameters</span></span>

<span data-ttu-id="2d4de-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2d4de-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d4de-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2d4de-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d4de-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="2d4de-158">INPUTS</span></span>

### <span data-ttu-id="2d4de-159">System. String</span><span class="sxs-lookup"><span data-stu-id="2d4de-159">System.String</span></span>

<span data-ttu-id="2d4de-160">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="2d4de-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="2d4de-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2d4de-161">OUTPUTS</span></span>

### <span data-ttu-id="2d4de-162">System. String</span><span class="sxs-lookup"><span data-stu-id="2d4de-162">System.String</span></span>

<span data-ttu-id="2d4de-163">Deze cmdlet retourneert een teken reeks die het resulterende pad bevat.</span><span class="sxs-lookup"><span data-stu-id="2d4de-163">This cmdlet returns a string that contains the resulting path.</span></span>

## <span data-ttu-id="2d4de-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2d4de-164">NOTES</span></span>

<span data-ttu-id="2d4de-165">De-cmdlets die het pad zelfstandig naam woord (de pad-cmdlets) bevatten, kunnen namen van paden wijzigen en de namen retour neren in een beknopte notatie die alle Power shell-providers kan interpreteren.</span><span class="sxs-lookup"><span data-stu-id="2d4de-165">The cmdlets that contain the Path noun (the Path cmdlets) manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="2d4de-166">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="2d4de-166">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="2d4de-167">Gebruik deze zoals u mapnaam, Normpath, realpath, Join's of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d4de-167">Use them like you would use Dirname, Normpath, Realpath, Join, or other path manipulators.</span></span>

<span data-ttu-id="2d4de-168">U kunt de pad-cmdlets gebruiken met verschillende providers, waaronder de `FileSystem` -, `Registry` -en- `Certificate` providers.</span><span class="sxs-lookup"><span data-stu-id="2d4de-168">You can use the path cmdlets with several providers, including the `FileSystem`, `Registry`, and `Certificate` providers.</span></span>

<span data-ttu-id="2d4de-169">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2d4de-169">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="2d4de-170">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="2d4de-170">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="2d4de-171">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2d4de-171">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2d4de-172">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2d4de-172">RELATED LINKS</span></span>

[<span data-ttu-id="2d4de-173">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="2d4de-173">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="2d4de-174">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="2d4de-174">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="2d4de-175">Split-pad</span><span class="sxs-lookup"><span data-stu-id="2d4de-175">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="2d4de-176">Test-pad</span><span class="sxs-lookup"><span data-stu-id="2d4de-176">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="2d4de-177">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2d4de-177">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="2d4de-178">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="2d4de-178">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="2d4de-179">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2d4de-179">Get-PSDrive</span></span>](Get-PSDrive.md)