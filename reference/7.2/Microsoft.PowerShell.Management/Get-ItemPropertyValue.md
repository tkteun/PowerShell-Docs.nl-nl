---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: b8980febb80a4e7dfaefba46649ac49b5b41b427
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705277"
---
# <span data-ttu-id="01a9d-102">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="01a9d-102">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="01a9d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="01a9d-103">SYNOPSIS</span></span>
<span data-ttu-id="01a9d-104">Hiermee wordt de waarde voor een of meer eigenschappen van een opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-104">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="01a9d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="01a9d-105">SYNTAX</span></span>

### <span data-ttu-id="01a9d-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="01a9d-106">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="01a9d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="01a9d-107">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="01a9d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="01a9d-108">DESCRIPTION</span></span>

<span data-ttu-id="01a9d-109">De `Get-ItemPropertyValue` haalt de huidige waarde op voor een eigenschap die u opgeeft wanneer u de para meter *name* gebruikt, die zich bevindt in een pad dat u opgeeft met de *pad* -of *LiteralPath* -para meters.</span><span class="sxs-lookup"><span data-stu-id="01a9d-109">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="01a9d-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="01a9d-110">EXAMPLES</span></span>

### <span data-ttu-id="01a9d-111">Voor beeld 1: de waarde van de eigenschap ProductID ophalen</span><span class="sxs-lookup"><span data-stu-id="01a9d-111">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="01a9d-112">Met deze opdracht wordt de waarde van de eigenschap **ProductID** van het object ' \SOFTWARE\Microsoft\Windows NT\CurrentVersion ' in de Windows-register provider opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-112">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="01a9d-113">Voor beeld 2: de laatste schrijf tijd van een bestand of map ophalen</span><span class="sxs-lookup"><span data-stu-id="01a9d-113">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="01a9d-114">Met deze opdracht wordt de waarde van de eigenschap **LastWriteTime** opgehaald, of de laatste keer dat een bestand of map is gewijzigd, in de map "C:\Users\Test\Documents\ModuleToAssembly", die in de File System Provider werkt.</span><span class="sxs-lookup"><span data-stu-id="01a9d-114">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="01a9d-115">Voor beeld 3: meerdere eigenschaps waarden van een bestand of map ophalen</span><span class="sxs-lookup"><span data-stu-id="01a9d-115">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="01a9d-116">Met deze opdracht worden de waarden van de **LastWriteTime**-, **CreationTime**-en **root** -eigenschappen van een map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-116">This command gets the values of the **LastWriteTime**, **CreationTime**, and **Root** properties of a folder.</span></span> <span data-ttu-id="01a9d-117">De eigenschapwaarden worden geretourneerd in de volg orde waarin u de eigenschapnamen hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="01a9d-117">The property values are returned in the order in which you specified the property names.</span></span>

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

## <span data-ttu-id="01a9d-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01a9d-118">PARAMETERS</span></span>

### <span data-ttu-id="01a9d-119">-Credential</span><span class="sxs-lookup"><span data-stu-id="01a9d-119">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="01a9d-120">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="01a9d-120">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="01a9d-121">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="01a9d-121">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="01a9d-122">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="01a9d-122">-Exclude</span></span>

<span data-ttu-id="01a9d-123">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="01a9d-123">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="01a9d-124">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="01a9d-124">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="01a9d-125">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="01a9d-125">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="01a9d-126">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="01a9d-126">Wildcard characters are permitted.</span></span> <span data-ttu-id="01a9d-127">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="01a9d-127">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="01a9d-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="01a9d-128">-Filter</span></span>

<span data-ttu-id="01a9d-129">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="01a9d-129">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="01a9d-130">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="01a9d-130">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="01a9d-131">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="01a9d-131">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="01a9d-132">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="01a9d-133">-Include</span><span class="sxs-lookup"><span data-stu-id="01a9d-133">-Include</span></span>

<span data-ttu-id="01a9d-134">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="01a9d-134">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="01a9d-135">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="01a9d-135">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="01a9d-136">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="01a9d-136">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="01a9d-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="01a9d-137">Wildcard characters are permitted.</span></span> <span data-ttu-id="01a9d-138">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="01a9d-138">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="01a9d-139">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="01a9d-139">-LiteralPath</span></span>

<span data-ttu-id="01a9d-140">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="01a9d-140">Specifies a path to one or more locations.</span></span> <span data-ttu-id="01a9d-141">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="01a9d-141">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="01a9d-142">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="01a9d-142">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="01a9d-143">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="01a9d-143">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="01a9d-144">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="01a9d-144">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="01a9d-145">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01a9d-145">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="01a9d-146">-Name</span><span class="sxs-lookup"><span data-stu-id="01a9d-146">-Name</span></span>

<span data-ttu-id="01a9d-147">Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-147">Specifies the name of the property or properties to retrieve.</span></span>
<span data-ttu-id="01a9d-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="01a9d-148">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="01a9d-149">-Path</span><span class="sxs-lookup"><span data-stu-id="01a9d-149">-Path</span></span>

<span data-ttu-id="01a9d-150">Hiermee geeft u het pad op naar het item of de items.</span><span class="sxs-lookup"><span data-stu-id="01a9d-150">Specifies the path to the item or items.</span></span>
<span data-ttu-id="01a9d-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="01a9d-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="01a9d-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01a9d-152">CommonParameters</span></span>

<span data-ttu-id="01a9d-153">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="01a9d-153">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="01a9d-154">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01a9d-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="01a9d-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="01a9d-155">INPUTS</span></span>

### <span data-ttu-id="01a9d-156">System. String</span><span class="sxs-lookup"><span data-stu-id="01a9d-156">System.String</span></span>

<span data-ttu-id="01a9d-157">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="01a9d-157">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="01a9d-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="01a9d-158">OUTPUTS</span></span>

### <span data-ttu-id="01a9d-159">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="01a9d-159">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="01a9d-160">Met deze cmdlet wordt een object geretourneerd voor elke eigenschaps waarde van een item die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-160">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="01a9d-161">Het object type is afhankelijk van de eigenschaps waarde die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="01a9d-161">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="01a9d-162">In een bestandssysteem station kan de cmdlet bijvoorbeeld een bestand of map retour neren.</span><span class="sxs-lookup"><span data-stu-id="01a9d-162">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="01a9d-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="01a9d-163">NOTES</span></span>

<span data-ttu-id="01a9d-164">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="01a9d-164">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="01a9d-165">Voer de cmdlet uit om de providers weer te geven die beschikbaar zijn in uw sessie `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="01a9d-165">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="01a9d-166">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01a9d-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="01a9d-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="01a9d-167">RELATED LINKS</span></span>

[<span data-ttu-id="01a9d-168">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-168">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="01a9d-169">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-169">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="01a9d-170">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-170">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="01a9d-171">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="01a9d-171">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="01a9d-172">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-172">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="01a9d-173">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-173">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="01a9d-174">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-174">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="01a9d-175">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-175">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="01a9d-176">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="01a9d-176">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="01a9d-177">about_Providers</span><span class="sxs-lookup"><span data-stu-id="01a9d-177">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

