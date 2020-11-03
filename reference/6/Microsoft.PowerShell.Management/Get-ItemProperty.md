---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: abf6a5ef365a606b6ca501e9cb924528763a8754
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251022"
---
# <span data-ttu-id="308d1-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="308d1-103">Get-ItemProperty</span></span>

## <span data-ttu-id="308d1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="308d1-104">SYNOPSIS</span></span>
<span data-ttu-id="308d1-105">Hiermee worden de eigenschappen van een opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="308d1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="308d1-106">SYNTAX</span></span>

### <span data-ttu-id="308d1-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="308d1-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="308d1-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="308d1-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="308d1-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="308d1-109">DESCRIPTION</span></span>

<span data-ttu-id="308d1-110">`Get-ItemProperty`Met de cmdlet worden de eigenschappen van de opgegeven items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="308d1-111">U kunt deze cmdlet bijvoorbeeld gebruiken om de waarde van de eigenschap LastAccessTime van een File-object op te halen.</span><span class="sxs-lookup"><span data-stu-id="308d1-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span> <span data-ttu-id="308d1-112">U kunt deze cmdlet ook gebruiken om Register vermeldingen en hun waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="308d1-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="308d1-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="308d1-113">EXAMPLES</span></span>

### <span data-ttu-id="308d1-114">Voor beeld 1: informatie over een specifieke directory ophalen</span><span class="sxs-lookup"><span data-stu-id="308d1-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="308d1-115">Met deze opdracht wordt informatie over de `C:\Windows` Directory opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-115">This command gets information about the `C:\Windows` directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="308d1-116">Voor beeld 2: de eigenschappen van een specifiek bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="308d1-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="308d1-117">Met deze opdracht worden de eigenschappen van het `C:\Test\Weather.xls` bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-117">This command gets the properties of the `C:\Test\Weather.xls` file.</span></span>
<span data-ttu-id="308d1-118">Het resultaat wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="308d1-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="308d1-119">Voor beeld 3: de waardenaam en gegevens van Register vermeldingen in een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="308d1-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="308d1-120">Met deze opdracht worden de naam en de gegevens van elk van de Register vermeldingen in de registersubsleutel ' CurrentVersion ' weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="308d1-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> <span data-ttu-id="308d1-121">Deze opdracht vereist dat er een Power Shell-station `HKLM:` met de naam is toegewezen aan de component HKEY_LOCAL_MACHINE van het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="308d1-121">This command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
>
> <span data-ttu-id="308d1-122">Een station met die naam en toewijzing is standaard beschikbaar in Power shell.</span><span class="sxs-lookup"><span data-stu-id="308d1-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
> <span data-ttu-id="308d1-123">U kunt ook het pad naar deze registersubsleutel opgeven met behulp van het volgende alternatieve pad dat begint met de provider naam gevolgd door twee dubbele punten:</span><span class="sxs-lookup"><span data-stu-id="308d1-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>
>
> <span data-ttu-id="308d1-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="308d1-124">`Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

### <span data-ttu-id="308d1-125">Voor beeld 4: de waardenaam en gegevens van een register vermelding in een registersubsleutel ophalen</span><span class="sxs-lookup"><span data-stu-id="308d1-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="308d1-126">Met deze opdracht worden de waardenaam en de gegevens van de register vermelding ' ProgramFilesDir ' in de registersubsleutel ' CurrentVersion ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="308d1-127">Het **pad** geeft de subsleutel en de **naam** para meter geeft de naam van de vermelding.</span><span class="sxs-lookup"><span data-stu-id="308d1-127">The **Path** specifies the subkey and the **Name** parameter specifies the value name of the entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="308d1-128">Voor beeld 5: de waardenamen en gegevens van Register vermeldingen in een register sleutel ophalen</span><span class="sxs-lookup"><span data-stu-id="308d1-128">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="308d1-129">Met deze opdracht worden de waardenamen en gegevens van de Register vermeldingen in de register sleutel ' PowerShellEngine ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-129">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span> <span data-ttu-id="308d1-130">De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="308d1-130">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

## <span data-ttu-id="308d1-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="308d1-131">PARAMETERS</span></span>

### <span data-ttu-id="308d1-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="308d1-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="308d1-133">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="308d1-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="308d1-134">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="308d1-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="308d1-135">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="308d1-135">-Exclude</span></span>

<span data-ttu-id="308d1-136">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="308d1-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="308d1-137">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="308d1-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="308d1-138">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="308d1-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="308d1-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="308d1-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="308d1-140">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="308d1-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="308d1-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="308d1-141">-Filter</span></span>

<span data-ttu-id="308d1-142">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="308d1-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="308d1-143">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="308d1-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="308d1-144">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="308d1-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="308d1-145">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="308d1-146">-Include</span><span class="sxs-lookup"><span data-stu-id="308d1-146">-Include</span></span>

<span data-ttu-id="308d1-147">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="308d1-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="308d1-148">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="308d1-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="308d1-149">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="308d1-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="308d1-150">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="308d1-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="308d1-151">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="308d1-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="308d1-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="308d1-152">-LiteralPath</span></span>

<span data-ttu-id="308d1-153">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="308d1-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="308d1-154">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="308d1-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="308d1-155">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="308d1-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="308d1-156">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="308d1-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="308d1-157">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="308d1-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="308d1-158">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="308d1-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="308d1-159">-Name</span><span class="sxs-lookup"><span data-stu-id="308d1-159">-Name</span></span>

<span data-ttu-id="308d1-160">Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-160">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="308d1-161">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="308d1-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="308d1-162">-Path</span><span class="sxs-lookup"><span data-stu-id="308d1-162">-Path</span></span>

<span data-ttu-id="308d1-163">Hiermee geeft u het pad op naar het item of de items.</span><span class="sxs-lookup"><span data-stu-id="308d1-163">Specifies the path to the item or items.</span></span>
<span data-ttu-id="308d1-164">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="308d1-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="308d1-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="308d1-165">CommonParameters</span></span>

<span data-ttu-id="308d1-166">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="308d1-166">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="308d1-167">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="308d1-167">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="308d1-168">INVOER</span><span class="sxs-lookup"><span data-stu-id="308d1-168">INPUTS</span></span>

### <span data-ttu-id="308d1-169">System. String</span><span class="sxs-lookup"><span data-stu-id="308d1-169">System.String</span></span>

<span data-ttu-id="308d1-170">U kunt een teken reeks met een pad naar door sluizen `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="308d1-170">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="308d1-171">UITVOER</span><span class="sxs-lookup"><span data-stu-id="308d1-171">OUTPUTS</span></span>

### <span data-ttu-id="308d1-172">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="308d1-172">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="308d1-173">`Get-ItemProperty` retourneert een object voor elke item eigenschap die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-173">`Get-ItemProperty` returns an object for each item property that it gets.</span></span> <span data-ttu-id="308d1-174">Het object type is afhankelijk van het object dat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="308d1-174">The object type depends on the object that is retrieved.</span></span> <span data-ttu-id="308d1-175">Zo kan een bestand of map in een bestandssysteem station worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="308d1-175">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="308d1-176">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="308d1-176">NOTES</span></span>

<span data-ttu-id="308d1-177">De `Get-ItemProperty` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="308d1-177">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="308d1-178">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="308d1-178">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="308d1-179">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="308d1-179">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="308d1-180">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="308d1-180">RELATED LINKS</span></span>

[<span data-ttu-id="308d1-181">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-181">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="308d1-182">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-182">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="308d1-183">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-183">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="308d1-184">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-184">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="308d1-185">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-185">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="308d1-186">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-186">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="308d1-187">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="308d1-187">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="308d1-188">about_Providers</span><span class="sxs-lookup"><span data-stu-id="308d1-188">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
