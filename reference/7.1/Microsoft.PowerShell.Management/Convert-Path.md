---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: 498620ee79285f0c0fe2a001b99fe5dc179ea0ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251332"
---
# <span data-ttu-id="98fed-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="98fed-103">Convert-Path</span></span>

## <span data-ttu-id="98fed-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="98fed-104">SYNOPSIS</span></span>
<span data-ttu-id="98fed-105">Converteert een pad van een Power shell-pad naar een Power shell-provider pad.</span><span class="sxs-lookup"><span data-stu-id="98fed-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="98fed-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="98fed-106">SYNTAX</span></span>

### <span data-ttu-id="98fed-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="98fed-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="98fed-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="98fed-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="98fed-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="98fed-109">DESCRIPTION</span></span>

<span data-ttu-id="98fed-110">De `Convert-Path` cmdlet converteert een pad van een Power shell-pad naar een Power shell-provider pad.</span><span class="sxs-lookup"><span data-stu-id="98fed-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="98fed-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="98fed-111">EXAMPLES</span></span>

### <span data-ttu-id="98fed-112">Voor beeld 1: de werkmap converteren naar een standaard bestandssysteempad</span><span class="sxs-lookup"><span data-stu-id="98fed-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="98fed-113">In dit voor beeld wordt de huidige werkmap, die wordt vertegenwoordigd door een punt ( `.` ), geconverteerd naar een standaard bestandssysteempad.</span><span class="sxs-lookup"><span data-stu-id="98fed-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="98fed-114">Voor beeld 2: een pad naar een provider converteren naar een standaard registerpad</span><span class="sxs-lookup"><span data-stu-id="98fed-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="98fed-115">In dit voor beeld wordt het pad van de Power shell-provider geconverteerd naar een standaardpad voor het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="98fed-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="98fed-116">Voor beeld 3: een pad naar een teken reeks converteren</span><span class="sxs-lookup"><span data-stu-id="98fed-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="98fed-117">In dit voor beeld wordt het pad naar de basismap van de huidige provider, de bestandssysteem provider, geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="98fed-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="98fed-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98fed-118">PARAMETERS</span></span>

### <span data-ttu-id="98fed-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="98fed-119">-LiteralPath</span></span>

<span data-ttu-id="98fed-120">Hiermee geeft u als een teken reeks matrix het pad op dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="98fed-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="98fed-121">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="98fed-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="98fed-122">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="98fed-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="98fed-123">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="98fed-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="98fed-124">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="98fed-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="98fed-125">-Path</span><span class="sxs-lookup"><span data-stu-id="98fed-125">-Path</span></span>

<span data-ttu-id="98fed-126">Hiermee geeft u het Power shell-pad op dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="98fed-126">Specifies the PowerShell path to be converted.</span></span>

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

### <span data-ttu-id="98fed-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98fed-127">CommonParameters</span></span>

<span data-ttu-id="98fed-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98fed-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98fed-129">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="98fed-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98fed-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="98fed-130">INPUTS</span></span>

### <span data-ttu-id="98fed-131">System. String</span><span class="sxs-lookup"><span data-stu-id="98fed-131">System.String</span></span>

<span data-ttu-id="98fed-132">U kunt een pad, maar geen letterlijk pad, naar deze cmdlet sluizen.</span><span class="sxs-lookup"><span data-stu-id="98fed-132">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="98fed-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="98fed-133">OUTPUTS</span></span>

### <span data-ttu-id="98fed-134">System. String</span><span class="sxs-lookup"><span data-stu-id="98fed-134">System.String</span></span>

<span data-ttu-id="98fed-135">Deze cmdlet retourneert een teken reeks die het geconverteerde pad bevat.</span><span class="sxs-lookup"><span data-stu-id="98fed-135">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="98fed-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="98fed-136">NOTES</span></span>

<span data-ttu-id="98fed-137">De cmdlets die het pad van de naam van het zelfstandige bestand bevatten en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="98fed-137">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="98fed-138">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="98fed-138">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="98fed-139">Gebruik deze zoals u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="98fed-139">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="98fed-140">U kunt de pad-cmdlets gebruiken met verschillende providers, waaronder het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="98fed-140">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="98fed-141">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="98fed-141">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="98fed-142">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="98fed-142">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="98fed-143">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="98fed-143">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="98fed-144">`Convert-Path` alleen bestaande paden worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="98fed-144">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="98fed-145">Het kan niet worden gebruikt om een locatie te converteren die nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="98fed-145">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="98fed-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="98fed-146">RELATED LINKS</span></span>

[<span data-ttu-id="98fed-147">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="98fed-147">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="98fed-148">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="98fed-148">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="98fed-149">Split-pad</span><span class="sxs-lookup"><span data-stu-id="98fed-149">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="98fed-150">Test-pad</span><span class="sxs-lookup"><span data-stu-id="98fed-150">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="98fed-151">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="98fed-151">Get-PSProvider</span></span>](Get-PSProvider.md)

