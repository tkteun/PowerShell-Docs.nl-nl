---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 2daf4d9dacc0f15ab5347fff4bec831be25d97a6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249409"
---
# <span data-ttu-id="8fa0b-103">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8fa0b-103">Remove-ItemProperty</span></span>

## <span data-ttu-id="8fa0b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8fa0b-104">SYNOPSIS</span></span>
<span data-ttu-id="8fa0b-105">Hiermee verwijdert u de eigenschap en de waarde ervan uit een item.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-105">Deletes the property and its value from an item.</span></span>

## <span data-ttu-id="8fa0b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8fa0b-106">SYNTAX</span></span>

### <span data-ttu-id="8fa0b-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="8fa0b-107">Path (Default)</span></span>

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8fa0b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8fa0b-108">LiteralPath</span></span>

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8fa0b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8fa0b-109">DESCRIPTION</span></span>

<span data-ttu-id="8fa0b-110">`Remove-ItemProperty`Met de cmdlet wordt een eigenschap en de waarde ervan uit een item verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-110">The `Remove-ItemProperty` cmdlet deletes a property and its value from an item.</span></span>
<span data-ttu-id="8fa0b-111">U kunt deze gebruiken om register waarden en de opgeslagen gegevens te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-111">You can use it to delete registry values and the data that they store.</span></span>

## <span data-ttu-id="8fa0b-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8fa0b-112">EXAMPLES</span></span>

### <span data-ttu-id="8fa0b-113">Voor beeld 1: een register waarde verwijderen</span><span class="sxs-lookup"><span data-stu-id="8fa0b-113">Example 1: Delete a registry value</span></span>

<span data-ttu-id="8fa0b-114">Met deze opdracht worden de register waarde ' SmpProperty ' en de bijbehorende gegevens verwijderd uit de subsleutel ' SmpApplication ' van de `HKEY_LOCAL_MACHINE\Software` register sleutel.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-114">This command deletes the "SmpProperty" registry value, and its data, from the "SmpApplication" subkey of the `HKEY_LOCAL_MACHINE\Software` registry key.</span></span>

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

<span data-ttu-id="8fa0b-115">Omdat de opdracht wordt verleend vanuit een bestandssysteem station ( `PS C:\>` ), bevat deze het volledig gekwalificeerde pad van de subsleutel "SmpApplication", met inbegrip van het station, `HKLM:` en de sleutel "software".</span><span class="sxs-lookup"><span data-stu-id="8fa0b-115">Because the command is issued from a file system drive (`PS C:\>`), it includes the fully qualified path of the "SmpApplication" subkey, including the drive, `HKLM:`, and the "Software" key.</span></span>

### <span data-ttu-id="8fa0b-116">Voor beeld 2: een register waarde verwijderen van de HKCU-locatie</span><span class="sxs-lookup"><span data-stu-id="8fa0b-116">Example 2: Delete a registry value from the HKCU location</span></span>

<span data-ttu-id="8fa0b-117">Met deze opdrachten worden de register waarde ' Options ' en de bijbehorende gegevens uit de ' Mijntoep '-subsleutel van HKEY_CURRENT_USER\Software\MyCompany verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-117">These commands delete the "Options" registry value, and its data, from the "MyApp" subkey of "HKEY_CURRENT_USER\Software\MyCompany".</span></span>

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

<span data-ttu-id="8fa0b-118">Met de eerste opdracht wordt de `Set-Location` cmdlet gebruikt om de huidige locatie te wijzigen in de **HKEY_CURRENT_USER** station ( `HKCU:` ) en de `Software\MyCompany\MyApp` subsleutel.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-118">The first command uses the `Set-Location` cmdlet to change the current location to the **HKEY_CURRENT_USER** drive (`HKCU:`) and the `Software\MyCompany\MyApp` subkey.</span></span>

<span data-ttu-id="8fa0b-119">De tweede opdracht wordt gebruikt `Remove-ItemProperty` om de register waarde ' Options ' en de bijbehorende gegevens te verwijderen uit de ' Mijntoep '-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-119">The second command uses `Remove-ItemProperty` to remove the "Options" registry value, and its data, from the "MyApp" subkey.</span></span> <span data-ttu-id="8fa0b-120">Omdat **pad** vereist is, gebruikt de opdracht een punt ( `.` ) om de huidige locatie aan te geven.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-120">Because **Path** is required, the command uses a dot (`.`) to indicate the current location.</span></span> <span data-ttu-id="8fa0b-121">De **confirm** -para meter vraagt een gebruikers prompt aan voordat de waarde wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-121">The **Confirm** parameter requests a user prompt before deleting the value.</span></span>

### <span data-ttu-id="8fa0b-122">Voor beeld 3: een register waarde verwijderen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="8fa0b-122">Example 3: Remove a registry value by using the pipeline</span></span>

<span data-ttu-id="8fa0b-123">Met deze opdracht worden de register waarde ' NoOfEmployees ' en de bijbehorende gegevens uit de `HKLM\Software\MyCompany` register sleutel verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-123">This command deletes the "NoOfEmployees" registry value, and its data, from the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
```

<span data-ttu-id="8fa0b-124">De opdracht gebruikt de `Get-Item` cmdlet om een item op te halen dat de register sleutel vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-124">The command uses the `Get-Item` cmdlet to get an item that represents the registry key.</span></span>
<span data-ttu-id="8fa0b-125">Er wordt een pijplijn operator ( `|` ) gebruikt om het object naar te verzenden `Remove-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-125">It uses a pipeline operator (`|`) to send the object to `Remove-ItemProperty`.</span></span>
<span data-ttu-id="8fa0b-126">Vervolgens wordt de para meter **name** van gebruikt `Remove-ItemProperty` om de naam van de register waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-126">Then, it uses the **Name** parameter of `Remove-ItemProperty` to specify the name of the registry value.</span></span>

## <span data-ttu-id="8fa0b-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8fa0b-127">PARAMETERS</span></span>

### <span data-ttu-id="8fa0b-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="8fa0b-128">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8fa0b-129">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-129">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="8fa0b-130">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-130">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="8fa0b-131">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="8fa0b-131">-Exclude</span></span>

<span data-ttu-id="8fa0b-132">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-132">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="8fa0b-133">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-133">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8fa0b-134">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-134">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="8fa0b-135">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="8fa0b-136">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-136">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="8fa0b-137">-Filter</span><span class="sxs-lookup"><span data-stu-id="8fa0b-137">-Filter</span></span>

<span data-ttu-id="8fa0b-138">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-138">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="8fa0b-139">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-139">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="8fa0b-140">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-140">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="8fa0b-141">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-141">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="8fa0b-142">-Force</span><span class="sxs-lookup"><span data-stu-id="8fa0b-142">-Force</span></span>

<span data-ttu-id="8fa0b-143">Hiermee wordt de cmdlet gedwongen een eigenschap van een object te verwijderen dat niet kan worden gebruikt door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-143">Forces the cmdlet to remove a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="8fa0b-144">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-144">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="8fa0b-145">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-145">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="8fa0b-146">-Include</span><span class="sxs-lookup"><span data-stu-id="8fa0b-146">-Include</span></span>

<span data-ttu-id="8fa0b-147">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="8fa0b-148">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8fa0b-149">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="8fa0b-150">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="8fa0b-151">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="8fa0b-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8fa0b-152">-LiteralPath</span></span>

<span data-ttu-id="8fa0b-153">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="8fa0b-154">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="8fa0b-155">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8fa0b-156">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8fa0b-157">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="8fa0b-158">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="8fa0b-159">-Name</span><span class="sxs-lookup"><span data-stu-id="8fa0b-159">-Name</span></span>

<span data-ttu-id="8fa0b-160">Hiermee geeft u de namen van de eigenschappen die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-160">Specifies the names of the properties to remove.</span></span>
<span data-ttu-id="8fa0b-161">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-161">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8fa0b-162">-Path</span><span class="sxs-lookup"><span data-stu-id="8fa0b-162">-Path</span></span>

<span data-ttu-id="8fa0b-163">Hiermee geeft u het pad op van het item waarvan de eigenschappen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-163">Specifies the path of the item whose properties are being removed.</span></span>
<span data-ttu-id="8fa0b-164">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8fa0b-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8fa0b-165">-Confirm</span></span>

<span data-ttu-id="8fa0b-166">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8fa0b-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8fa0b-167">-WhatIf</span></span>

<span data-ttu-id="8fa0b-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8fa0b-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8fa0b-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8fa0b-170">CommonParameters</span></span>

<span data-ttu-id="8fa0b-171">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-171">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8fa0b-172">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-172">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8fa0b-173">INVOER</span><span class="sxs-lookup"><span data-stu-id="8fa0b-173">INPUTS</span></span>

### <span data-ttu-id="8fa0b-174">System. String</span><span class="sxs-lookup"><span data-stu-id="8fa0b-174">System.String</span></span>

<span data-ttu-id="8fa0b-175">U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-175">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="8fa0b-176">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8fa0b-176">OUTPUTS</span></span>

### <span data-ttu-id="8fa0b-177">Geen</span><span class="sxs-lookup"><span data-stu-id="8fa0b-177">None</span></span>

<span data-ttu-id="8fa0b-178">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-178">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="8fa0b-179">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8fa0b-179">NOTES</span></span>

- <span data-ttu-id="8fa0b-180">In de register provider van Power shell worden register waarden beschouwd als eigenschappen van een register sleutel of-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-180">In the PowerShell Registry provider, registry values are considered to be properties of a registry key or subkey.</span></span> <span data-ttu-id="8fa0b-181">U kunt de **item Property** -cmdlets gebruiken om deze waarden te beheren.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-181">You can use the **ItemProperty** cmdlets to manage these values.</span></span>
- <span data-ttu-id="8fa0b-182">`Remove-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-182">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8fa0b-183">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="8fa0b-183">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="8fa0b-184">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fa0b-184">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8fa0b-185">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8fa0b-185">RELATED LINKS</span></span>

[<span data-ttu-id="8fa0b-186">Get-item</span><span class="sxs-lookup"><span data-stu-id="8fa0b-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="8fa0b-187">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-187">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="8fa0b-188">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-188">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="8fa0b-189">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-189">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="8fa0b-190">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-190">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="8fa0b-191">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-191">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="8fa0b-192">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="8fa0b-192">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="8fa0b-193">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-193">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="8fa0b-194">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="8fa0b-194">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="8fa0b-195">Set-Location</span><span class="sxs-lookup"><span data-stu-id="8fa0b-195">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="8fa0b-196">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8fa0b-196">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
