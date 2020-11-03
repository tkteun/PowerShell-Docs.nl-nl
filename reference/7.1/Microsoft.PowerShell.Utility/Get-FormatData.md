---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 0024bb83b983d0b13e2fbfafb24505849acf15f6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250219"
---
# <span data-ttu-id="24015-103">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="24015-103">Get-FormatData</span></span>

## <span data-ttu-id="24015-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="24015-104">SYNOPSIS</span></span>
<span data-ttu-id="24015-105">Hiermee haalt u de opmaak gegevens op in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="24015-105">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="24015-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="24015-106">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="24015-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="24015-107">DESCRIPTION</span></span>

<span data-ttu-id="24015-108">De `Get-FormatData` cmdlet haalt de indelings gegevens in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="24015-108">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="24015-109">De indelings gegevens in de sessie bevatten opmaak gegevens uit `Format.ps1xml` opmaak bestanden, zoals die in de `$PSHOME` map, het format teren van gegevens voor modules die u in de sessie importeert, en het opmaken van gegevens voor opdrachten die u importeert in uw-sessie met behulp van de- `Import-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24015-109">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="24015-110">U kunt deze cmdlet gebruiken om de opmaak gegevens te controleren.</span><span class="sxs-lookup"><span data-stu-id="24015-110">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="24015-111">Vervolgens kunt u de- `Export-FormatData` cmdlet gebruiken om de objecten te serialiseren, converteren naar XML en deze op te slaan in `Format.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="24015-111">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="24015-112">Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het format teren van bestanden in Power shell.</span><span class="sxs-lookup"><span data-stu-id="24015-112">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="24015-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="24015-113">EXAMPLES</span></span>

### <span data-ttu-id="24015-114">Voor beeld 1: alle opmaak gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="24015-114">Example 1: Get all formatting data</span></span>

<span data-ttu-id="24015-115">In dit voor beeld worden alle opmaak gegevens in de sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="24015-115">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="24015-116">Voor beeld 2: opmaak gegevens ophalen op type naam</span><span class="sxs-lookup"><span data-stu-id="24015-116">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="24015-117">In dit voor beeld worden de opmaak gegevens items opgehaald waarvan de naam begint met `System.Management.Automation.Cmd` .</span><span class="sxs-lookup"><span data-stu-id="24015-117">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="24015-118">Voor beeld 3: een opmaak gegevens object bekijken</span><span class="sxs-lookup"><span data-stu-id="24015-118">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="24015-119">In dit voor beeld ziet u hoe u een object met een opmaak gegevens ophaalt en de eigenschappen ervan bekijkt.</span><span class="sxs-lookup"><span data-stu-id="24015-119">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### <span data-ttu-id="24015-120">Voor beeld 4: opmaak gegevens ophalen en deze exporteren</span><span class="sxs-lookup"><span data-stu-id="24015-120">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="24015-121">In dit voor beeld ziet u hoe u `Get-FormatData` `Export-FormatData` de opmaak gegevens die door een module worden toegevoegd, kunt gebruiken en exporteren.</span><span class="sxs-lookup"><span data-stu-id="24015-121">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

<span data-ttu-id="24015-122">De eerste vier opdrachten gebruiken de `Get-FormatData` -, `Import-Module` -en- `Compare-Object` cmdlets om het indelings type te identificeren dat door de **BitsTransfer** -module wordt toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="24015-122">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="24015-123">De vijfde opdracht gebruikt de `Get-FormatData` cmdlet om het indelings type op te halen dat door de **BitsTransfer** -module wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="24015-123">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="24015-124">Er wordt een pijplijn operator ( `|` ) gebruikt om het indelings type object te verzenden naar de `Export-FormatData` cmdlet, waarmee het weer wordt omgezet in XML en wordt opgeslagen in het opgegeven `format.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="24015-124">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="24015-125">Met de laatste opdracht wordt een fragment van de `format.ps1xml` Bestands inhoud weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="24015-125">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="24015-126">Voor beeld 5: opmaak gegevens ophalen op basis van de opgegeven versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="24015-126">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="24015-127">In dit voor beeld ziet u hoe u kunt gebruiken `Get-FormatData` om gegevens op te halen voor een opgegeven **TypeName** en Power shell-versie.</span><span class="sxs-lookup"><span data-stu-id="24015-127">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="24015-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24015-128">PARAMETERS</span></span>

### <span data-ttu-id="24015-129">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="24015-129">-PowerShellVersion</span></span>

<span data-ttu-id="24015-130">Geef de versie van Power shell op die met deze cmdlet wordt opgehaald voor de indelings gegevens.</span><span class="sxs-lookup"><span data-stu-id="24015-130">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="24015-131">Voer een getal in van twee cijfers, gescheiden door een punt.</span><span class="sxs-lookup"><span data-stu-id="24015-131">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="24015-132">Deze para meter is toegevoegd aan Power shell 5,1 om de compatibiliteit te verbeteren wanneer externe computers met oudere versies van Power shell worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="24015-132">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24015-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="24015-133">-TypeName</span></span>

<span data-ttu-id="24015-134">Hiermee geeft u de type namen op die met deze cmdlet worden opgehaald voor de indelings gegevens.</span><span class="sxs-lookup"><span data-stu-id="24015-134">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="24015-135">Voer de type namen in.</span><span class="sxs-lookup"><span data-stu-id="24015-135">Enter the type names.</span></span>
<span data-ttu-id="24015-136">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="24015-136">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="24015-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24015-137">CommonParameters</span></span>

<span data-ttu-id="24015-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="24015-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24015-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="24015-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24015-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="24015-140">INPUTS</span></span>

### <span data-ttu-id="24015-141">Geen</span><span class="sxs-lookup"><span data-stu-id="24015-141">None</span></span>

<span data-ttu-id="24015-142">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24015-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="24015-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="24015-143">OUTPUTS</span></span>

### <span data-ttu-id="24015-144">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="24015-144">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="24015-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="24015-145">NOTES</span></span>

## <span data-ttu-id="24015-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="24015-146">RELATED LINKS</span></span>

[<span data-ttu-id="24015-147">Exporteren-FormatData</span><span class="sxs-lookup"><span data-stu-id="24015-147">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="24015-148">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="24015-148">Update-FormatData</span></span>](Update-FormatData.md)
