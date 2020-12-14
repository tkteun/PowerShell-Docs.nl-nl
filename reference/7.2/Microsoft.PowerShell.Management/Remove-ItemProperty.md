---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 870d8e9797ff2cfce14034706f704c0e1c954fc2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705952"
---
# <span data-ttu-id="365df-102">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="365df-102">Remove-ItemProperty</span></span>

## <span data-ttu-id="365df-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="365df-103">SYNOPSIS</span></span>
<span data-ttu-id="365df-104">Hiermee verwijdert u de eigenschap en de waarde ervan uit een item.</span><span class="sxs-lookup"><span data-stu-id="365df-104">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="365df-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="365df-105">SYNTAX</span></span>

### <span data-ttu-id="365df-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="365df-106">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="365df-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="365df-107">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="365df-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="365df-108">DESCRIPTION</span></span>

<span data-ttu-id="365df-109">`Remove-ItemProperty`Met de cmdlet wordt een eigenschap en de waarde ervan uit een item verwijderd.</span><span class="sxs-lookup"><span data-stu-id="365df-109">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="365df-110">U kunt deze gebruiken om register waarden en de opgeslagen gegevens te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="365df-110">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="365df-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="365df-111">EXAMPLES</span></span>

### <span data-ttu-id="365df-112">Voor beeld 1: een register waarde verwijderen</span><span class="sxs-lookup"><span data-stu-id="365df-112">Example 1: Delete a registry value</span></span>

<span data-ttu-id="365df-113">Met deze opdracht worden de register waarde ' SmpProperty ' en de bijbehorende gegevens verwijderd uit de subsleutel ' SmpApplication ' van de `HKEY_LOCAL_MACHINE\Software` register sleutel.</span><span class="sxs-lookup"><span data-stu-id="365df-113">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="365df-114">Omdat de opdracht wordt verleend vanuit een bestandssysteem station ( `PS C:\>` ), bevat deze het volledig gekwalificeerde pad van de subsleutel "SmpApplication", met inbegrip van het station, `HKLM:` en de sleutel "software".</span><span class="sxs-lookup"><span data-stu-id="365df-114">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="365df-115">Voor beeld 2: een register waarde verwijderen van de HKCU-locatie</span><span class="sxs-lookup"><span data-stu-id="365df-115">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="365df-116">Met deze opdrachten worden de register waarde ' Options ' en de bijbehorende gegevens uit de ' Mijntoep '-subsleutel van HKEY_CURRENT_USER\Software\MyCompany verwijderd.</span><span class="sxs-lookup"><span data-stu-id="365df-116">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="365df-117">Met de eerste opdracht wordt de `Set-Location` cmdlet gebruikt om de huidige locatie te wijzigen in de **HKEY_CURRENT_USER** station ( `HKCU:` ) en de `Software\MyCompany\MyApp` subsleutel.</span><span class="sxs-lookup"><span data-stu-id="365df-117">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="365df-118">De tweede opdracht wordt gebruikt `Remove-ItemProperty` om de register waarde ' Options ' en de bijbehorende gegevens te verwijderen uit de ' Mijntoep '-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="365df-118">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="365df-119">Omdat **pad** vereist is, gebruikt de opdracht een punt ( `.` ) om de huidige locatie aan te geven.</span><span class="sxs-lookup"><span data-stu-id="365df-119">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="365df-120">De **confirm** -para meter vraagt een gebruikers prompt aan voordat de waarde wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="365df-120">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="365df-121">Voor beeld 3: een register waarde verwijderen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="365df-121">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="365df-122">Met deze opdracht worden de register waarde ' NoOfEmployees ' en de bijbehorende gegevens uit de `HKLM\Software\MyCompany` register sleutel verwijderd.</span><span class="sxs-lookup"><span data-stu-id="365df-122">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="365df-123">De opdracht gebruikt de `Get-Item` cmdlet om een item op te halen dat de register sleutel vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="365df-123">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="365df-124">Er wordt een pijplijn operator ( `|` ) gebruikt om het object naar te verzenden `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="365df-124">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="365df-125">Vervolgens wordt de para meter **name** van gebruikt `Remove-ItemProperty` om de naam van de register waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="365df-125">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="365df-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="365df-126">PARAMETERS</span></span>

### <span data-ttu-id="365df-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="365df-127">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="365df-128">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="365df-128">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="365df-129">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="365df-129">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="365df-130">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="365df-130">-Exclude</span></span>

<span data-ttu-id="365df-131">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="365df-131">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="365df-132">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="365df-132">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="365df-133">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="365df-133">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="365df-134">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="365df-134">Wildcard characters are permitted.</span></span> <span data-ttu-id="365df-135">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="365df-135">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="365df-136">-Filter</span><span class="sxs-lookup"><span data-stu-id="365df-136">-Filter</span></span>

<span data-ttu-id="365df-137">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="365df-137">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="365df-138">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="365df-138">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="365df-139">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="365df-139">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="365df-140">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="365df-140">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="365df-141">-Force</span><span class="sxs-lookup"><span data-stu-id="365df-141">-Force</span></span>

<span data-ttu-id="365df-142">Hiermee wordt de cmdlet gedwongen een eigenschap van een object te verwijderen dat niet kan worden gebruikt door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="365df-142">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="365df-143">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="365df-143">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="365df-144">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="365df-144">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="365df-145">-Include</span><span class="sxs-lookup"><span data-stu-id="365df-145">-Include</span></span>

<span data-ttu-id="365df-146">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="365df-146">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="365df-147">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="365df-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="365df-148">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="365df-148">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="365df-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="365df-149">Wildcard characters are permitted.</span></span> <span data-ttu-id="365df-150">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="365df-150">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="365df-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="365df-151">-LiteralPath</span></span>

<span data-ttu-id="365df-152">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="365df-152">Specifies a path to one or more locations.</span></span> <span data-ttu-id="365df-153">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="365df-153">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="365df-154">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="365df-154">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="365df-155">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="365df-155">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="365df-156">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="365df-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="365df-157">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="365df-157">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="365df-158">-Name</span><span class="sxs-lookup"><span data-stu-id="365df-158">-Name</span></span>

<span data-ttu-id="365df-159">Hiermee geeft u de namen van de eigenschappen die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="365df-159">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="365df-160">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="365df-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="365df-161">-Path</span><span class="sxs-lookup"><span data-stu-id="365df-161">-Path</span></span>

<span data-ttu-id="365df-162">Hiermee geeft u het pad op van het item waarvan de eigenschappen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="365df-162">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="365df-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="365df-163">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="365df-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="365df-164">-Confirm</span></span>

<span data-ttu-id="365df-165">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="365df-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="365df-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="365df-166">-WhatIf</span></span>

<span data-ttu-id="365df-167">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="365df-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="365df-168">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="365df-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="365df-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="365df-169">CommonParameters</span></span>

<span data-ttu-id="365df-170">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="365df-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="365df-171">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="365df-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="365df-172">INVOER</span><span class="sxs-lookup"><span data-stu-id="365df-172">INPUTS</span></span>

### <span data-ttu-id="365df-173">System. String</span><span class="sxs-lookup"><span data-stu-id="365df-173">System.String</span></span>

<span data-ttu-id="365df-174">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="365df-174">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="365df-175">UITVOER</span><span class="sxs-lookup"><span data-stu-id="365df-175">OUTPUTS</span></span>

### <span data-ttu-id="365df-176">Geen</span><span class="sxs-lookup"><span data-stu-id="365df-176">None</span></span>

<span data-ttu-id="365df-177">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="365df-177">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="365df-178">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="365df-178">NOTES</span></span>

- <span data-ttu-id="365df-179">In de register provider van Power shell worden register waarden beschouwd als eigenschappen van een register sleutel of-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="365df-179">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="365df-180">U kunt de **item Property** -cmdlets gebruiken om deze waarden te beheren.</span><span class="sxs-lookup"><span data-stu-id="365df-180">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="365df-181">`Remove-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="365df-181">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="365df-182">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="365df-182">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="365df-183">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="365df-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="365df-184">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="365df-184">RELATED LINKS</span></span>

[<span data-ttu-id="365df-185">Get-item</span><span class="sxs-lookup"><span data-stu-id="365df-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="365df-186">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-186">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="365df-187">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-187">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="365df-188">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-188">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="365df-189">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-189">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="365df-190">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-190">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="365df-191">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="365df-191">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="365df-192">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-192">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="365df-193">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="365df-193">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="365df-194">Set-Location</span><span class="sxs-lookup"><span data-stu-id="365df-194">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="365df-195">about_Providers</span><span class="sxs-lookup"><span data-stu-id="365df-195">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

