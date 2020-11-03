---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250580"
---
# <span data-ttu-id="6bfec-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="6bfec-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="6bfec-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6bfec-104">SYNOPSIS</span></span>
<span data-ttu-id="6bfec-105">Hiermee verwijdert u de eigenschap en de waarde ervan uit een item.</span><span class="sxs-lookup"><span data-stu-id="6bfec-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="6bfec-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6bfec-106">SYNTAX</span></span>

### <span data-ttu-id="6bfec-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="6bfec-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="6bfec-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6bfec-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="6bfec-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6bfec-109">DESCRIPTION</span></span>

<span data-ttu-id="6bfec-110">`Remove-ItemProperty`Met de cmdlet wordt een eigenschap en de waarde ervan uit een item verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="6bfec-111">U kunt deze gebruiken om register waarden en de opgeslagen gegevens te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6bfec-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="6bfec-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6bfec-112">EXAMPLES</span></span>

### <span data-ttu-id="6bfec-113">Voor beeld 1: een register waarde verwijderen</span><span class="sxs-lookup"><span data-stu-id="6bfec-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="6bfec-114">Met deze opdracht worden de register waarde ' SmpProperty ' en de bijbehorende gegevens verwijderd uit de subsleutel ' SmpApplication ' van de register sleutel ' HKEY_LOCAL_MACHINE\Software '.</span><span class="sxs-lookup"><span data-stu-id="6bfec-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the "HKEY_LOCAL_MACHINE\Software" registry key.</span></span>

<span data-ttu-id="6bfec-115">Omdat de opdracht wordt verleend vanuit een bestandssysteem station ( `PS C:\>` ), bevat deze het volledig gekwalificeerde pad van de subsleutel "SmpApplication", met inbegrip van het station, `HKLM:` en de sleutel "software".</span><span class="sxs-lookup"><span data-stu-id="6bfec-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

<span data-ttu-id="6bfec-116">De para meter **name** wordt gebruikt om de register waarde te identificeren die wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-116">It uses the **Name** parameter to identify the registry value that is being deleted.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### <span data-ttu-id="6bfec-117">Voor beeld 2: een register waarde verwijderen van de HKCU-locatie</span><span class="sxs-lookup"><span data-stu-id="6bfec-117">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="6bfec-118">Met deze opdrachten worden de register waarde ' Options ' en de bijbehorende gegevens uit de ' Mijntoep '-subsleutel van HKEY_CURRENT_USER\Software\MyCompany verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-118">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

<span data-ttu-id="6bfec-119">De eerste opdracht gebruikt de `Set-Location` cmdlet om de huidige locatie te wijzigen naar de **HKEY_CURRENT_USER** station ( `HKCU:` ) en de subsleutel ' Software\MyCompany\MyApp '.</span><span class="sxs-lookup"><span data-stu-id="6bfec-119">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the "Software\MyCompany\MyApp" subkey.</span></span>

<span data-ttu-id="6bfec-120">De tweede opdracht wordt gebruikt `Remove-ItemProperty` om de register waarde ' Options ' en de bijbehorende gegevens te verwijderen uit de ' Mijntoep '-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="6bfec-120">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span>
<span data-ttu-id="6bfec-121">Omdat **pad** vereist is, gebruikt de opdracht een punt ('. ') om de huidige locatie aan te geven.</span><span class="sxs-lookup"><span data-stu-id="6bfec-121">Because **Path** is required, the command uses a dot ('.') to indicate the current location.</span></span>
<span data-ttu-id="6bfec-122">De **naam** wordt gebruikt om op te geven welke register waarde moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-122">It uses **Name** to specify which registry value to delete.</span></span>
<span data-ttu-id="6bfec-123">De para meter **confirm** wordt gebruikt voor het aanvragen van een gebruikers prompt voordat de waarde wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-123">It uses the **Confirm** parameter to request a user prompt before deleting the value.</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### <span data-ttu-id="6bfec-124">Voor beeld 3: een register waarde verwijderen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="6bfec-124">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="6bfec-125">Met deze opdracht worden de register waarde ' NoOfEmployees ' en de bijbehorende gegevens verwijderd uit de register sleutel ' HKLM\Software\MyCompany '.</span><span class="sxs-lookup"><span data-stu-id="6bfec-125">This command deletes the "NoOfEmployees" registry value, and its data, from the "HKLM\Software\MyCompany" registry key.</span></span>

<span data-ttu-id="6bfec-126">De opdracht gebruikt de `Get-Item` cmdlet om een item op te halen dat de register sleutel vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="6bfec-126">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="6bfec-127">Er wordt een pijplijn operator ( `|` ) gebruikt om het object naar te verzenden `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="6bfec-127">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="6bfec-128">Vervolgens wordt de para meter **name** van gebruikt `Remove-ItemProperty` om de naam van de register waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="6bfec-128">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

## <span data-ttu-id="6bfec-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6bfec-129">PARAMETERS</span></span>

### <span data-ttu-id="6bfec-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="6bfec-130">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="6bfec-131">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="6bfec-131">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="6bfec-132">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6bfec-132">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="6bfec-133">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="6bfec-133">-Exclude</span></span>

<span data-ttu-id="6bfec-134">Hiermee geeft u de items die met deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="6bfec-134">Specifies items that this cmdlet omits.</span></span>
<span data-ttu-id="6bfec-135">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6bfec-135">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="6bfec-136">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="6bfec-136">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="6bfec-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6bfec-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6bfec-138">-Filter</span><span class="sxs-lookup"><span data-stu-id="6bfec-138">-Filter</span></span>

<span data-ttu-id="6bfec-139">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="6bfec-139">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="6bfec-140">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6bfec-140">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="6bfec-141">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="6bfec-141">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="6bfec-142">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6bfec-142">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="6bfec-143">-Force</span><span class="sxs-lookup"><span data-stu-id="6bfec-143">-Force</span></span>

<span data-ttu-id="6bfec-144">Hiermee wordt de cmdlet gedwongen een eigenschap van een object te verwijderen dat niet kan worden gebruikt door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6bfec-144">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="6bfec-145">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="6bfec-145">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="6bfec-146">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6bfec-146">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bfec-147">-Include</span><span class="sxs-lookup"><span data-stu-id="6bfec-147">-Include</span></span>

<span data-ttu-id="6bfec-148">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="6bfec-148">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="6bfec-149">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6bfec-149">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="6bfec-150">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="6bfec-150">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="6bfec-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6bfec-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6bfec-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6bfec-152">-LiteralPath</span></span>

<span data-ttu-id="6bfec-153">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6bfec-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="6bfec-154">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="6bfec-154">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="6bfec-155">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="6bfec-155">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="6bfec-156">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="6bfec-156">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="6bfec-157">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="6bfec-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="6bfec-158">-Name</span><span class="sxs-lookup"><span data-stu-id="6bfec-158">-Name</span></span>

<span data-ttu-id="6bfec-159">Hiermee geeft u de namen van de eigenschappen die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="6bfec-160">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6bfec-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6bfec-161">-Path</span><span class="sxs-lookup"><span data-stu-id="6bfec-161">-Path</span></span>

<span data-ttu-id="6bfec-162">Hiermee geeft u het pad op van het item waarvan de eigenschappen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="6bfec-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6bfec-163">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="6bfec-164">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="6bfec-164">-UseTransaction</span></span>

<span data-ttu-id="6bfec-165">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="6bfec-165">Includes the command in the active transaction.</span></span>
<span data-ttu-id="6bfec-166">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-166">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="6bfec-167">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6bfec-167">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="6bfec-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6bfec-168">-Confirm</span></span>

<span data-ttu-id="6bfec-169">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6bfec-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6bfec-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6bfec-170">-WhatIf</span></span>

<span data-ttu-id="6bfec-171">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6bfec-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6bfec-172">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6bfec-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bfec-173">CommonParameters</span></span>

<span data-ttu-id="6bfec-174">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="6bfec-174">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="6bfec-175">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6bfec-175">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6bfec-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="6bfec-176">INPUTS</span></span>

### <span data-ttu-id="6bfec-177">System. String</span><span class="sxs-lookup"><span data-stu-id="6bfec-177">System.String</span></span>

<span data-ttu-id="6bfec-178">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="6bfec-178">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="6bfec-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6bfec-179">OUTPUTS</span></span>

### <span data-ttu-id="6bfec-180">Geen</span><span class="sxs-lookup"><span data-stu-id="6bfec-180">None</span></span>

<span data-ttu-id="6bfec-181">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6bfec-181">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="6bfec-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6bfec-182">NOTES</span></span>

<span data-ttu-id="6bfec-183">In de register provider van Power shell worden register waarden beschouwd als eigenschappen van een register sleutel of-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="6bfec-183">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="6bfec-184">U kunt de **item Property** -cmdlets gebruiken om deze waarden te beheren.</span><span class="sxs-lookup"><span data-stu-id="6bfec-184">You can use the **ItemProperty** cmdlets to manage these values.</span></span>

<span data-ttu-id="6bfec-185">`Remove-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6bfec-185">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="6bfec-186">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="6bfec-186">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="6bfec-187">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6bfec-187">For more information, see about_Providers.</span></span>

## <span data-ttu-id="6bfec-188">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6bfec-188">RELATED LINKS</span></span>

[<span data-ttu-id="6bfec-189">Get-item</span><span class="sxs-lookup"><span data-stu-id="6bfec-189">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="6bfec-190">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-190">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="6bfec-191">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-191">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="6bfec-192">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-192">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="6bfec-193">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-193">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="6bfec-194">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-194">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="6bfec-195">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="6bfec-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="6bfec-196">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-196">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="6bfec-197">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="6bfec-197">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="6bfec-198">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6bfec-198">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
