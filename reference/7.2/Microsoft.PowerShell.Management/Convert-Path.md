---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: 3d39ea9498cec2669fa075d4630b7691671fea32
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705747"
---
# <span data-ttu-id="a0746-102">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="a0746-102">Convert-Path</span></span>

## <span data-ttu-id="a0746-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a0746-103">SYNOPSIS</span></span>
<span data-ttu-id="a0746-104">Converteert een pad van een Power shell-pad naar een Power shell-provider pad.</span><span class="sxs-lookup"><span data-stu-id="a0746-104">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="a0746-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a0746-105">SYNTAX</span></span>

### <span data-ttu-id="a0746-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="a0746-106">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="a0746-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0746-107">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="a0746-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a0746-108">DESCRIPTION</span></span>

<span data-ttu-id="a0746-109">De `Convert-Path` cmdlet converteert een pad van een Power shell-pad naar een Power shell-provider pad.</span><span class="sxs-lookup"><span data-stu-id="a0746-109">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="a0746-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a0746-110">EXAMPLES</span></span>

### <span data-ttu-id="a0746-111">Voor beeld 1: de werkmap converteren naar een standaard bestandssysteempad</span><span class="sxs-lookup"><span data-stu-id="a0746-111">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="a0746-112">In dit voor beeld wordt de huidige werkmap, die wordt vertegenwoordigd door een punt ( `.` ), geconverteerd naar een standaard bestandssysteempad.</span><span class="sxs-lookup"><span data-stu-id="a0746-112">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="a0746-113">Voor beeld 2: een pad naar een provider converteren naar een standaard registerpad</span><span class="sxs-lookup"><span data-stu-id="a0746-113">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="a0746-114">In dit voor beeld wordt het pad van de Power shell-provider geconverteerd naar een standaardpad voor het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="a0746-114">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="a0746-115">Voor beeld 3: een pad naar een teken reeks converteren</span><span class="sxs-lookup"><span data-stu-id="a0746-115">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="a0746-116">In dit voor beeld wordt het pad naar de basismap van de huidige provider, de bestandssysteem provider, geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a0746-116">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="a0746-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0746-117">PARAMETERS</span></span>

### <span data-ttu-id="a0746-118">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0746-118">-LiteralPath</span></span>

<span data-ttu-id="a0746-119">Hiermee geeft u als een teken reeks matrix het pad op dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="a0746-119">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="a0746-120">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="a0746-120">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="a0746-121">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="a0746-121">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a0746-122">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a0746-122">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a0746-123">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="a0746-123">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a0746-124">-Path</span><span class="sxs-lookup"><span data-stu-id="a0746-124">-Path</span></span>

<span data-ttu-id="a0746-125">Hiermee geeft u het Power shell-pad op dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="a0746-125">Specifies the PowerShell path to be converted.</span></span>

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

### <span data-ttu-id="a0746-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0746-126">CommonParameters</span></span>

<span data-ttu-id="a0746-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0746-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0746-128">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a0746-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0746-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="a0746-129">INPUTS</span></span>

### <span data-ttu-id="a0746-130">System. String</span><span class="sxs-lookup"><span data-stu-id="a0746-130">System.String</span></span>

<span data-ttu-id="a0746-131">U kunt een pad, maar geen letterlijk pad, naar deze cmdlet sluizen.</span><span class="sxs-lookup"><span data-stu-id="a0746-131">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="a0746-132">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a0746-132">OUTPUTS</span></span>

### <span data-ttu-id="a0746-133">System. String</span><span class="sxs-lookup"><span data-stu-id="a0746-133">System.String</span></span>

<span data-ttu-id="a0746-134">Deze cmdlet retourneert een teken reeks die het geconverteerde pad bevat.</span><span class="sxs-lookup"><span data-stu-id="a0746-134">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="a0746-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a0746-135">NOTES</span></span>

<span data-ttu-id="a0746-136">De cmdlets die het pad van de naam van het zelfstandige bestand bevatten en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="a0746-136">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="a0746-137">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="a0746-137">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="a0746-138">Gebruik deze zoals u **mapnaam**, **Normpath**, **realpath**, **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a0746-138">Use them like you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

<span data-ttu-id="a0746-139">U kunt de pad-cmdlets gebruiken met verschillende providers, waaronder het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="a0746-139">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="a0746-140">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a0746-140">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a0746-141">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a0746-141">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a0746-142">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a0746-142">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="a0746-143">`Convert-Path` alleen bestaande paden worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="a0746-143">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="a0746-144">Het kan niet worden gebruikt om een locatie te converteren die nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="a0746-144">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="a0746-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a0746-145">RELATED LINKS</span></span>

[<span data-ttu-id="a0746-146">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="a0746-146">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="a0746-147">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="a0746-147">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="a0746-148">Split-pad</span><span class="sxs-lookup"><span data-stu-id="a0746-148">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="a0746-149">Test-pad</span><span class="sxs-lookup"><span data-stu-id="a0746-149">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="a0746-150">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a0746-150">Get-PSProvider</span></span>](Get-PSProvider.md)

