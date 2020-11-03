---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: fe49b968c859060b6f1c82c27bac87b33dabe079
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251021"
---
# <span data-ttu-id="8c7c2-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="8c7c2-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="8c7c2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8c7c2-104">SYNOPSIS</span></span>
<span data-ttu-id="8c7c2-105">Hiermee wordt de waarde voor een of meer eigenschappen van een opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="8c7c2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8c7c2-106">SYNTAX</span></span>

### <span data-ttu-id="8c7c2-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="8c7c2-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="8c7c2-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c7c2-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="8c7c2-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8c7c2-109">DESCRIPTION</span></span>

<span data-ttu-id="8c7c2-110">De `Get-ItemPropertyValue` haalt de huidige waarde op voor een eigenschap die u opgeeft wanneer u de para meter *name* gebruikt, die zich bevindt in een pad dat u opgeeft met de *pad* -of *LiteralPath* -para meters.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="8c7c2-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8c7c2-111">EXAMPLES</span></span>

### <span data-ttu-id="8c7c2-112">Voor beeld 1: de waarde van de eigenschap ProductID ophalen</span><span class="sxs-lookup"><span data-stu-id="8c7c2-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="8c7c2-113">Met deze opdracht wordt de waarde van de eigenschap **ProductID** van het object ' \SOFTWARE\Microsoft\Windows NT\CurrentVersion ' in de Windows-register provider opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="8c7c2-114">Voor beeld 2: de laatste schrijf tijd van een bestand of map ophalen</span><span class="sxs-lookup"><span data-stu-id="8c7c2-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="8c7c2-115">Met deze opdracht wordt de waarde van de eigenschap **LastWriteTime** opgehaald, of de laatste keer dat een bestand of map is gewijzigd, in de map "C:\Users\Test\Documents\ModuleToAssembly", die in de File System Provider werkt.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="8c7c2-116">Voor beeld 3: meerdere eigenschaps waarden van een bestand of map ophalen</span><span class="sxs-lookup"><span data-stu-id="8c7c2-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="8c7c2-117">Met deze opdracht worden de waarden van de **LastWriteTime** -, **CreationTime** -en **root** -eigenschappen van een map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span> <span data-ttu-id="8c7c2-118">De eigenschapwaarden worden geretourneerd in de volg orde waarin u de eigenschapnamen hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-118">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="8c7c2-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c7c2-119">PARAMETERS</span></span>

### <span data-ttu-id="8c7c2-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="8c7c2-120">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="8c7c2-121">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-121">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="8c7c2-122">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-122">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="8c7c2-123">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="8c7c2-123">-Exclude</span></span>

<span data-ttu-id="8c7c2-124">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-124">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="8c7c2-125">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c7c2-125">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8c7c2-126">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="8c7c2-126">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="8c7c2-127">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-127">Wildcard characters are permitted.</span></span> <span data-ttu-id="8c7c2-128">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-128">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="8c7c2-129">-Filter</span><span class="sxs-lookup"><span data-stu-id="8c7c2-129">-Filter</span></span>

<span data-ttu-id="8c7c2-130">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-130">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="8c7c2-131">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-131">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="8c7c2-132">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-132">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="8c7c2-133">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-133">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="8c7c2-134">-Include</span><span class="sxs-lookup"><span data-stu-id="8c7c2-134">-Include</span></span>

<span data-ttu-id="8c7c2-135">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="8c7c2-136">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c7c2-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="8c7c2-137">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="8c7c2-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="8c7c2-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="8c7c2-139">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="8c7c2-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8c7c2-140">-LiteralPath</span></span>

<span data-ttu-id="8c7c2-141">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="8c7c2-142">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="8c7c2-143">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8c7c2-144">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8c7c2-145">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="8c7c2-146">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="8c7c2-147">-Name</span><span class="sxs-lookup"><span data-stu-id="8c7c2-147">-Name</span></span>

<span data-ttu-id="8c7c2-148">Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-148">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="8c7c2-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8c7c2-150">-Path</span><span class="sxs-lookup"><span data-stu-id="8c7c2-150">-Path</span></span>

<span data-ttu-id="8c7c2-151">Hiermee geeft u het pad op naar het item of de items.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-151">Specifies the path to the item or items.</span></span>
<span data-ttu-id="8c7c2-152">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-152">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8c7c2-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c7c2-153">CommonParameters</span></span>

<span data-ttu-id="8c7c2-154">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="8c7c2-154">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="8c7c2-155">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8c7c2-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="8c7c2-156">INPUTS</span></span>

### <span data-ttu-id="8c7c2-157">System. String</span><span class="sxs-lookup"><span data-stu-id="8c7c2-157">System.String</span></span>

<span data-ttu-id="8c7c2-158">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="8c7c2-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8c7c2-159">OUTPUTS</span></span>

### <span data-ttu-id="8c7c2-160">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="8c7c2-160">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="8c7c2-161">Met deze cmdlet wordt een object geretourneerd voor elke eigenschaps waarde van een item die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-161">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="8c7c2-162">Het object type is afhankelijk van de eigenschaps waarde die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-162">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="8c7c2-163">In een bestandssysteem station kan de cmdlet bijvoorbeeld een bestand of map retour neren.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-163">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="8c7c2-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8c7c2-164">NOTES</span></span>

<span data-ttu-id="8c7c2-165">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-165">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="8c7c2-166">Voer de cmdlet uit om de providers weer te geven die beschikbaar zijn in uw sessie `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="8c7c2-166">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="8c7c2-167">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c7c2-167">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="8c7c2-168">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8c7c2-168">RELATED LINKS</span></span>

[<span data-ttu-id="8c7c2-169">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-169">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="8c7c2-170">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-170">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="8c7c2-171">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-171">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="8c7c2-172">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="8c7c2-172">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="8c7c2-173">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-173">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="8c7c2-174">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-174">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="8c7c2-175">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-175">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="8c7c2-176">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-176">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="8c7c2-177">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="8c7c2-177">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="8c7c2-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8c7c2-178">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
