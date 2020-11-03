---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: 5d92acbe080b0d232047f1184c9a369b8837845c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250543"
---
# <span data-ttu-id="36053-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="36053-103">Split-Path</span></span>

## <span data-ttu-id="36053-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36053-104">SYNOPSIS</span></span>
<span data-ttu-id="36053-105">Retourneert het opgegeven deel van een pad.</span><span class="sxs-lookup"><span data-stu-id="36053-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="36053-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36053-106">SYNTAX</span></span>

### <span data-ttu-id="36053-107">Bovenliggendeset (standaard)</span><span class="sxs-lookup"><span data-stu-id="36053-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="36053-108">Geen Kwalificatieset</span><span class="sxs-lookup"><span data-stu-id="36053-108">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-NoQualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="36053-109">Blade</span><span class="sxs-lookup"><span data-stu-id="36053-109">LeafSet</span></span>

```
Split-Path [-Path] <String[]> [-Leaf] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="36053-110">Kwalificatieset</span><span class="sxs-lookup"><span data-stu-id="36053-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-Qualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="36053-111">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="36053-111">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] [-IsAbsolute] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="36053-112">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="36053-112">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="36053-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36053-113">DESCRIPTION</span></span>

<span data-ttu-id="36053-114">De cmdlet **Split-Path** retourneert alleen het opgegeven deel van een pad, zoals de bovenliggende map, een submap of een bestands naam.</span><span class="sxs-lookup"><span data-stu-id="36053-114">The **Split-Path** cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span>
<span data-ttu-id="36053-115">Er kunnen ook items worden opgehaald waarnaar wordt verwezen door het Splits pad en te zien of het pad relatief of absoluut is.</span><span class="sxs-lookup"><span data-stu-id="36053-115">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="36053-116">U kunt deze cmdlet gebruiken om alleen een geselecteerd deel van een pad op te halen of in te dienen.</span><span class="sxs-lookup"><span data-stu-id="36053-116">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="36053-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36053-117">EXAMPLES</span></span>

### <span data-ttu-id="36053-118">Voor beeld 1: de kwalificatie van een pad ophalen</span><span class="sxs-lookup"><span data-stu-id="36053-118">Example 1: Get the qualifier of a path</span></span>

```
PS C:\> Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
HKCU:
```

<span data-ttu-id="36053-119">Met deze opdracht wordt alleen de kwalificatie van het pad geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36053-119">This command returns only the qualifier of the path.</span></span>
<span data-ttu-id="36053-120">De kwalificatie is het station.</span><span class="sxs-lookup"><span data-stu-id="36053-120">The qualifier is the drive.</span></span>

### <span data-ttu-id="36053-121">Voor beeld 2: bestands namen weer geven</span><span class="sxs-lookup"><span data-stu-id="36053-121">Example 2: Display file names</span></span>

```
PS C:\> Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
Pass1.log
Pass2.log
...
```

<span data-ttu-id="36053-122">Met deze opdracht worden de bestanden weer gegeven waarnaar wordt verwezen door het Splits pad.</span><span class="sxs-lookup"><span data-stu-id="36053-122">This command displays the files that are referenced by the split path.</span></span>
<span data-ttu-id="36053-123">Omdat dit pad wordt gesplitst naar het laatste item, ook wel het Leaf genoemd, worden in de opdracht alleen de bestands namen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36053-123">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="36053-124">De para meter *resolver* vertelt **gesplitste paden** om de items weer te geven waarnaar de Splits pad verwijst, in plaats van het Splits pad weer te geven.</span><span class="sxs-lookup"><span data-stu-id="36053-124">The *Resolve* parameter tells **Split-Path** to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="36053-125">Net als bij alle opdracht **Split-paden** retourneert deze opdracht teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="36053-125">Like all **Split-Path** commands, this command returns strings.</span></span>
<span data-ttu-id="36053-126">Er worden geen **file info** -objecten geretourneerd die de bestanden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="36053-126">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="36053-127">Voor beeld 3: de bovenliggende container ophalen</span><span class="sxs-lookup"><span data-stu-id="36053-127">Example 3: Get the parent container</span></span>

```
PS C:\> Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="36053-128">Met deze opdracht worden alleen de bovenliggende containers van het pad geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36053-128">This command returns only the parent containers of the path.</span></span>
<span data-ttu-id="36053-129">Omdat het geen para meters bevat om de split op te geven, gebruikt **Split Path** de standaard locatie voor splitsen, de *bovenliggende* map.</span><span class="sxs-lookup"><span data-stu-id="36053-129">Because it does not include any parameters to specify the split, **Split-Path** uses the split location default, which is *Parent*.</span></span>

### <span data-ttu-id="36053-130">Voor beeld 4: Hiermee wordt bepaald of een pad absoluut is</span><span class="sxs-lookup"><span data-stu-id="36053-130">Example 4: Determines whether a path is absolute</span></span>

```
PS C:\> Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
False
```

<span data-ttu-id="36053-131">Met deze opdracht bepaalt u of het pad relatief of absoluut is.</span><span class="sxs-lookup"><span data-stu-id="36053-131">This command determines whether the path is relative or absolute.</span></span>
<span data-ttu-id="36053-132">In dit geval, omdat het pad relatief is ten opzichte van de huidige map, die wordt vertegenwoordigd door een punt (.), wordt $False geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36053-132">In this case, because the path is relative to the current folder, which is represented by a dot (.), it returns $False.</span></span>

### <span data-ttu-id="36053-133">Voor beeld 5: locatie wijzigen naar een opgegeven pad</span><span class="sxs-lookup"><span data-stu-id="36053-133">Example 5: Change location to a specified path</span></span>

```
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="36053-134">Met deze opdracht wordt uw locatie gewijzigd in de map met het Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="36053-134">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="36053-135">De opdracht tussen haakjes gebruikt een **Split-pad** om alleen het bovenliggende item te retour neren van het pad dat is opgeslagen in de ingebouwde $profile variabele.</span><span class="sxs-lookup"><span data-stu-id="36053-135">The command in parentheses uses **Split-Path** to return only the parent of the path stored in the built-in $Profile variable.</span></span>
<span data-ttu-id="36053-136">De *bovenliggende* para meter is de standaard waarde voor de Splits locatie.</span><span class="sxs-lookup"><span data-stu-id="36053-136">The *Parent* parameter is the default split location parameter.</span></span>
<span data-ttu-id="36053-137">Daarom kunt u deze uit de opdracht weglaten.</span><span class="sxs-lookup"><span data-stu-id="36053-137">Therefore, you can omit it from the command.</span></span>
<span data-ttu-id="36053-138">De haakjes direct Power shell om de opdracht eerst uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36053-138">The parentheses direct PowerShell to run the command first.</span></span>
<span data-ttu-id="36053-139">Dit is een handige manier om over te stappen op een map met een lange padnaam.</span><span class="sxs-lookup"><span data-stu-id="36053-139">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="36053-140">Voor beeld 6: een pad splitsen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="36053-140">Example 6: Split a path by using the pipeline</span></span>

```
PS C:\> 'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="36053-141">Met deze opdracht wordt een pijplijn operator (|) gebruikt voor het verzenden van een pad naar een **Split-pad**.</span><span class="sxs-lookup"><span data-stu-id="36053-141">This command uses a pipeline operator (|) to send a path to **Split-Path**.</span></span>
<span data-ttu-id="36053-142">Het pad wordt tussen aanhalings tekens geplaatst om aan te geven dat het een enkel token is.</span><span class="sxs-lookup"><span data-stu-id="36053-142">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="36053-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36053-143">PARAMETERS</span></span>

### <span data-ttu-id="36053-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="36053-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="36053-145">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="36053-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="36053-146">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="36053-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="36053-147">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="36053-147">-IsAbsolute</span></span>

<span data-ttu-id="36053-148">Geeft aan dat deze cmdlet $True retourneert als het pad absoluut is en $False als het relatief is.</span><span class="sxs-lookup"><span data-stu-id="36053-148">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span>
<span data-ttu-id="36053-149">Een absoluut pad heeft een lengte die groter is dan nul en gebruikt geen punt (.) om het huidige pad aan te geven.</span><span class="sxs-lookup"><span data-stu-id="36053-149">An absolute path has a length greater than zero and does not use a dot (.) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36053-150">-Leaf</span><span class="sxs-lookup"><span data-stu-id="36053-150">-Leaf</span></span>

<span data-ttu-id="36053-151">Geeft aan dat deze cmdlet alleen de laatste item of container in het pad retourneert.</span><span class="sxs-lookup"><span data-stu-id="36053-151">Indicates that this cmdlet returns only the last item or container in the path.</span></span>
<span data-ttu-id="36053-152">In het pad `C:\Test\Logs\Pass1.log` retourneert bijvoorbeeld alleen Pass1. log.</span><span class="sxs-lookup"><span data-stu-id="36053-152">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36053-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="36053-153">-LiteralPath</span></span>

<span data-ttu-id="36053-154">Hiermee geeft u de paden op die moeten worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="36053-154">Specifies the paths to be split.</span></span>
<span data-ttu-id="36053-155">In tegens telling tot *Path* wordt de waarde van *LiteralPath* precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="36053-155">Unlike *Path* , the value of *LiteralPath* is used exactly as it is typed.</span></span>
<span data-ttu-id="36053-156">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="36053-156">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="36053-157">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="36053-157">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="36053-158">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="36053-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36053-159">-Indicator</span><span class="sxs-lookup"><span data-stu-id="36053-159">-NoQualifier</span></span>

<span data-ttu-id="36053-160">Geeft aan dat deze cmdlet het pad retourneert zonder de kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="36053-160">Indicates that this cmdlet returns the path without the qualifier.</span></span>
<span data-ttu-id="36053-161">Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals C: of HKCU:.</span><span class="sxs-lookup"><span data-stu-id="36053-161">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>
<span data-ttu-id="36053-162">In het pad `C:\Test\Logs\Pass1.log` retourneert het bijvoorbeeld alleen \Test\Logs\Pass1.log.</span><span class="sxs-lookup"><span data-stu-id="36053-162">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only \Test\Logs\Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36053-163">-Bovenliggend item</span><span class="sxs-lookup"><span data-stu-id="36053-163">-Parent</span></span>

<span data-ttu-id="36053-164">Geeft aan dat deze cmdlet alleen de bovenliggende containers van het item of de container retourneert die door het pad worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="36053-164">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span>
<span data-ttu-id="36053-165">In het pad `C:\Test\Logs\Pass1.log` retourneert het bijvoorbeeld C:\Test\Logs.</span><span class="sxs-lookup"><span data-stu-id="36053-165">For example, in the path `C:\Test\Logs\Pass1.log`, it returns C:\Test\Logs.</span></span>
<span data-ttu-id="36053-166">De *bovenliggende* para meter is de standaard waarde voor de Splits locatie.</span><span class="sxs-lookup"><span data-stu-id="36053-166">The *Parent* parameter is the default split location parameter.</span></span>

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

### <span data-ttu-id="36053-167">-Path</span><span class="sxs-lookup"><span data-stu-id="36053-167">-Path</span></span>

<span data-ttu-id="36053-168">Hiermee geeft u de paden op die moeten worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="36053-168">Specifies the paths to be split.</span></span>
<span data-ttu-id="36053-169">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="36053-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="36053-170">Als het pad spaties bevat, plaatst u het tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="36053-170">If the path includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="36053-171">U kunt ook een pad naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="36053-171">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, NoQualifierSet, LeafSet, QualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="36053-172">-Kwalificatie</span><span class="sxs-lookup"><span data-stu-id="36053-172">-Qualifier</span></span>

<span data-ttu-id="36053-173">Geeft aan dat met deze cmdlet alleen de kwalificatie van het opgegeven pad wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36053-173">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span>
<span data-ttu-id="36053-174">Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals C: of HKCU:.</span><span class="sxs-lookup"><span data-stu-id="36053-174">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36053-175">-Oplossen</span><span class="sxs-lookup"><span data-stu-id="36053-175">-Resolve</span></span>

<span data-ttu-id="36053-176">Geeft aan dat met deze cmdlet de items worden weer gegeven waarnaar wordt verwezen door het resulterende Splits pad in plaats van de elementen van het pad weer te geven.</span><span class="sxs-lookup"><span data-stu-id="36053-176">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="36053-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="36053-177">-UseTransaction</span></span>

<span data-ttu-id="36053-178">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="36053-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="36053-179">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36053-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="36053-180">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36053-180">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36053-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36053-181">CommonParameters</span></span>

<span data-ttu-id="36053-182">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36053-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36053-183">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36053-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36053-184">INVOER</span><span class="sxs-lookup"><span data-stu-id="36053-184">INPUTS</span></span>

### <span data-ttu-id="36053-185">System. String</span><span class="sxs-lookup"><span data-stu-id="36053-185">System.String</span></span>

<span data-ttu-id="36053-186">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="36053-186">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="36053-187">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36053-187">OUTPUTS</span></span>

### <span data-ttu-id="36053-188">System. String, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="36053-188">System.String, System.Boolean</span></span>

<span data-ttu-id="36053-189">**Split-Path** retourneert tekst teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="36053-189">**Split-Path** returns text strings.</span></span>
<span data-ttu-id="36053-190">Wanneer u de para meter voor *omzetten* opgeeft, retourneert **Split-Path** een teken reeks die de locatie van de items beschrijft. het retourneert geen objecten die de items vertegenwoordigen, zoals een **file info** -of **RegistryKey** -object.</span><span class="sxs-lookup"><span data-stu-id="36053-190">When you specify the *Resolve* parameter, **Split-Path** returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="36053-191">Wanneer u de para meter *IsAbsolute* opgeeft, retourneert **Split-Path** een **Boole** -waarde.</span><span class="sxs-lookup"><span data-stu-id="36053-191">When you specify the *IsAbsolute* parameter, **Split-Path** returns a **Boolean** value.</span></span>

## <span data-ttu-id="36053-192">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36053-192">NOTES</span></span>

* <span data-ttu-id="36053-193">De para meters voor de Splits locatie ( *Kwalificatie* , *bovenliggend element* , *Leaf* en geen *Kwalificatie* ) zijn exclusief.</span><span class="sxs-lookup"><span data-stu-id="36053-193">The split location parameters ( *Qualifier* , *Parent* , *Leaf* , and *NoQualifier* ) are exclusive.</span></span> <span data-ttu-id="36053-194">U kunt slechts één in elke opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36053-194">You can use only one in each command.</span></span>

  <span data-ttu-id="36053-195">De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="36053-195">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span>
<span data-ttu-id="36053-196">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="36053-196">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="36053-197">U kunt ze gebruiken op de manier waarop u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36053-197">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

  <span data-ttu-id="36053-198">U kunt de **pad** -cmdlets samen met verschillende providers gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36053-198">You can use the **Path** cmdlets together with several providers.</span></span>
<span data-ttu-id="36053-199">Dit zijn onder andere het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="36053-199">These include the FileSystem, Registry, and Certificate providers.</span></span>

  <span data-ttu-id="36053-200">**Split-Path** is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36053-200">**Split-Path** is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="36053-201">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="36053-201">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="36053-202">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36053-202">For more information, see about_Providers.</span></span>

## <span data-ttu-id="36053-203">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36053-203">RELATED LINKS</span></span>

[<span data-ttu-id="36053-204">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="36053-204">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="36053-205">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="36053-205">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="36053-206">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="36053-206">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="36053-207">Test-pad</span><span class="sxs-lookup"><span data-stu-id="36053-207">Test-Path</span></span>](Test-Path.md)
