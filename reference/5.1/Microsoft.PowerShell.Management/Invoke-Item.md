---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250787"
---
# <span data-ttu-id="0d896-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="0d896-103">Invoke-Item</span></span>

## <span data-ttu-id="0d896-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0d896-104">SYNOPSIS</span></span>
<span data-ttu-id="0d896-105">Voert de standaard actie uit op het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="0d896-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="0d896-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0d896-106">SYNTAX</span></span>

### <span data-ttu-id="0d896-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="0d896-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="0d896-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0d896-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="0d896-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0d896-109">DESCRIPTION</span></span>

<span data-ttu-id="0d896-110">De `Invoke-Item` cmdlet voert de standaard actie uit op het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="0d896-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="0d896-111">Er wordt bijvoorbeeld een uitvoerbaar bestand uitgevoerd of een document bestand geopend in de toepassing die is gekoppeld aan het document bestands type.</span><span class="sxs-lookup"><span data-stu-id="0d896-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="0d896-112">De standaard actie is afhankelijk van het type item en wordt bepaald door de Power shell-provider die toegang biedt tot de gegevens.</span><span class="sxs-lookup"><span data-stu-id="0d896-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="0d896-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0d896-113">EXAMPLES</span></span>

### <span data-ttu-id="0d896-114">Voor beeld 1: een bestand openen</span><span class="sxs-lookup"><span data-stu-id="0d896-114">Example 1: Open a file</span></span>

<span data-ttu-id="0d896-115">Met deze opdracht wordt het bestand ' aliasApr04.doc ' geopend in Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="0d896-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="0d896-116">In dit geval is het openen in Word de standaard actie voor '. doc ' bestanden.</span><span class="sxs-lookup"><span data-stu-id="0d896-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="0d896-117">Voor beeld 2: alle bestanden van een specifiek type openen</span><span class="sxs-lookup"><span data-stu-id="0d896-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="0d896-118">Met deze opdracht worden alle Microsoft Office Excel-spread sheets in de map C:\Documents and Settings\Lister\My Documents geopend.</span><span class="sxs-lookup"><span data-stu-id="0d896-118">This command opens all of the Microsoft Office Excel spreadsheets in the "C:\Documents and Settings\Lister\My Documents" folder.</span></span>
<span data-ttu-id="0d896-119">Elk werk blad wordt geopend in een nieuw exemplaar van Excel.</span><span class="sxs-lookup"><span data-stu-id="0d896-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="0d896-120">In dit geval is openen in Excel de standaard actie voor '. xls '-bestanden.</span><span class="sxs-lookup"><span data-stu-id="0d896-120">In this case, opening in Excel is the default action for ".xls" files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="0d896-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0d896-121">PARAMETERS</span></span>

### <span data-ttu-id="0d896-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="0d896-122">-Credential</span></span>

<span data-ttu-id="0d896-123">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0d896-123">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="0d896-124">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0d896-124">The default is the current user.</span></span>

<span data-ttu-id="0d896-125">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d896-125">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="0d896-126">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="0d896-126">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="0d896-127">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0d896-127">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d896-128">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="0d896-128">-Exclude</span></span>

<span data-ttu-id="0d896-129">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="0d896-129">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="0d896-130">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="0d896-130">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="0d896-131">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="0d896-131">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="0d896-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0d896-132">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0d896-133">-Filter</span><span class="sxs-lookup"><span data-stu-id="0d896-133">-Filter</span></span>

<span data-ttu-id="0d896-134">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="0d896-134">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="0d896-135">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="0d896-135">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="0d896-136">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="0d896-136">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="0d896-137">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0d896-137">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0d896-138">-Include</span><span class="sxs-lookup"><span data-stu-id="0d896-138">-Include</span></span>

<span data-ttu-id="0d896-139">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="0d896-139">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="0d896-140">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="0d896-140">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="0d896-141">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="0d896-141">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="0d896-142">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0d896-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0d896-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0d896-143">-LiteralPath</span></span>

<span data-ttu-id="0d896-144">Hiermee geeft u een pad op naar het item.</span><span class="sxs-lookup"><span data-stu-id="0d896-144">Specifies a path to the item.</span></span>
<span data-ttu-id="0d896-145">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="0d896-145">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="0d896-146">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="0d896-146">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="0d896-147">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="0d896-147">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="0d896-148">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="0d896-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0d896-149">-Path</span><span class="sxs-lookup"><span data-stu-id="0d896-149">-Path</span></span>

<span data-ttu-id="0d896-150">Hiermee geeft u het pad op naar het geselecteerde item.</span><span class="sxs-lookup"><span data-stu-id="0d896-150">Specifies the path to the selected item.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0d896-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="0d896-151">-UseTransaction</span></span>

<span data-ttu-id="0d896-152">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="0d896-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="0d896-153">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d896-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="0d896-154">Zie about_transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0d896-154">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="0d896-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0d896-155">-Confirm</span></span>
<span data-ttu-id="0d896-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0d896-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0d896-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0d896-157">-WhatIf</span></span>

<span data-ttu-id="0d896-158">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0d896-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0d896-159">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d896-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0d896-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0d896-160">CommonParameters</span></span>

<span data-ttu-id="0d896-161">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="0d896-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="0d896-162">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0d896-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0d896-163">INVOER</span><span class="sxs-lookup"><span data-stu-id="0d896-163">INPUTS</span></span>

### <span data-ttu-id="0d896-164">System. String</span><span class="sxs-lookup"><span data-stu-id="0d896-164">System.String</span></span>

<span data-ttu-id="0d896-165">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="0d896-165">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="0d896-166">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0d896-166">OUTPUTS</span></span>

### <span data-ttu-id="0d896-167">Geen</span><span class="sxs-lookup"><span data-stu-id="0d896-167">None</span></span>

<span data-ttu-id="0d896-168">Met de opdracht wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0d896-168">The command does not generate any output.</span></span>
<span data-ttu-id="0d896-169">Uitvoer kan echter worden gegenereerd door het item dat wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="0d896-169">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="0d896-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0d896-170">NOTES</span></span>

<span data-ttu-id="0d896-171">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0d896-171">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0d896-172">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="0d896-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="0d896-173">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0d896-173">For more information, see about_Providers.</span></span>

## <span data-ttu-id="0d896-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0d896-174">RELATED LINKS</span></span>

[<span data-ttu-id="0d896-175">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="0d896-175">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="0d896-176">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="0d896-176">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="0d896-177">Get-item</span><span class="sxs-lookup"><span data-stu-id="0d896-177">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="0d896-178">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="0d896-178">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="0d896-179">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="0d896-179">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="0d896-180">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="0d896-180">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="0d896-181">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="0d896-181">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="0d896-182">Set-item</span><span class="sxs-lookup"><span data-stu-id="0d896-182">Set-Item</span></span>](Set-Item.md)
