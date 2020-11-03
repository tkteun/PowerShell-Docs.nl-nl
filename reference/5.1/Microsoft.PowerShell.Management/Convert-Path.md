---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: a442d8ff9f021e1ec05671d9190d35ef97ff4d72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250827"
---
# <span data-ttu-id="74887-103">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="74887-103">Convert-Path</span></span>

## <span data-ttu-id="74887-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="74887-104">SYNOPSIS</span></span>
<span data-ttu-id="74887-105">Converteert een pad van een Power shell-pad naar een Power shell-provider pad.</span><span class="sxs-lookup"><span data-stu-id="74887-105">Converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="74887-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="74887-106">SYNTAX</span></span>

### <span data-ttu-id="74887-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="74887-107">Path (Default)</span></span>

```
Convert-Path [-Path] <String[]> [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="74887-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74887-108">LiteralPath</span></span>

```
Convert-Path -LiteralPath <String[]> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="74887-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="74887-109">DESCRIPTION</span></span>

<span data-ttu-id="74887-110">De `Convert-Path` cmdlet converteert een pad van een Power shell-pad naar een Power shell-provider pad.</span><span class="sxs-lookup"><span data-stu-id="74887-110">The `Convert-Path` cmdlet converts a path from a PowerShell path to a PowerShell provider path.</span></span>

## <span data-ttu-id="74887-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="74887-111">EXAMPLES</span></span>

### <span data-ttu-id="74887-112">Voor beeld 1: de werkmap converteren naar een standaard bestandssysteempad</span><span class="sxs-lookup"><span data-stu-id="74887-112">Example 1: Convert the working directory to a standard file system path</span></span>

<span data-ttu-id="74887-113">In dit voor beeld wordt de huidige werkmap, die wordt vertegenwoordigd door een punt ( `.` ), geconverteerd naar een standaard bestandssysteempad.</span><span class="sxs-lookup"><span data-stu-id="74887-113">This example converts the current working directory, which is represented by a dot (`.`), to a standard FileSystem path.</span></span>

```
PS C:\> Convert-Path .
C:\
```

### <span data-ttu-id="74887-114">Voor beeld 2: een pad naar een provider converteren naar een standaard registerpad</span><span class="sxs-lookup"><span data-stu-id="74887-114">Example 2: Convert a provider path to a standard registry path</span></span>

<span data-ttu-id="74887-115">In dit voor beeld wordt het pad van de Power shell-provider geconverteerd naar een standaardpad voor het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="74887-115">This example converts the PowerShell provider path to a standard registry path.</span></span>

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### <span data-ttu-id="74887-116">Voor beeld 3: een pad naar een teken reeks converteren</span><span class="sxs-lookup"><span data-stu-id="74887-116">Example 3: Convert a path to a string</span></span>

<span data-ttu-id="74887-117">In dit voor beeld wordt het pad naar de basismap van de huidige provider, de bestandssysteem provider, geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="74887-117">This example converts the path to the home directory of the current provider, which is the FileSystem provider, to a string.</span></span>

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## <span data-ttu-id="74887-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="74887-118">PARAMETERS</span></span>

### <span data-ttu-id="74887-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="74887-119">-LiteralPath</span></span>

<span data-ttu-id="74887-120">Hiermee geeft u als een teken reeks matrix het pad op dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="74887-120">Specifies, as a string array, the path to be converted.</span></span> <span data-ttu-id="74887-121">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="74887-121">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="74887-122">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="74887-122">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="74887-123">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="74887-123">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="74887-124">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="74887-124">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="74887-125">-Path</span><span class="sxs-lookup"><span data-stu-id="74887-125">-Path</span></span>

<span data-ttu-id="74887-126">Hiermee geeft u het Power shell-pad op dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="74887-126">Specifies the PowerShell path to be converted.</span></span>

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

### <span data-ttu-id="74887-127">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="74887-127">-UseTransaction</span></span>
<span data-ttu-id="74887-128">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="74887-128">Includes the command in the active transaction.</span></span>
<span data-ttu-id="74887-129">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="74887-129">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="74887-130">Zie about_transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="74887-130">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="74887-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74887-131">CommonParameters</span></span>

<span data-ttu-id="74887-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74887-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74887-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="74887-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74887-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="74887-134">INPUTS</span></span>

### <span data-ttu-id="74887-135">System. String</span><span class="sxs-lookup"><span data-stu-id="74887-135">System.String</span></span>

<span data-ttu-id="74887-136">U kunt een pad, maar geen letterlijk pad, naar deze cmdlet sluizen.</span><span class="sxs-lookup"><span data-stu-id="74887-136">You can pipe a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="74887-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="74887-137">OUTPUTS</span></span>

### <span data-ttu-id="74887-138">System. String</span><span class="sxs-lookup"><span data-stu-id="74887-138">System.String</span></span>

<span data-ttu-id="74887-139">Deze cmdlet retourneert een teken reeks die het geconverteerde pad bevat.</span><span class="sxs-lookup"><span data-stu-id="74887-139">This cmdlet returns a string that contains the converted path.</span></span>

## <span data-ttu-id="74887-140">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="74887-140">NOTES</span></span>

<span data-ttu-id="74887-141">De cmdlets die het pad van de naam van het zelfstandige bestand bevatten en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.</span><span class="sxs-lookup"><span data-stu-id="74887-141">The cmdlets that contain the Path noun manipulate path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="74887-142">Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.</span><span class="sxs-lookup"><span data-stu-id="74887-142">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="74887-143">Gebruik deze zoals u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="74887-143">Use them like you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="74887-144">U kunt de pad-cmdlets gebruiken met verschillende providers, waaronder het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="74887-144">You can use the path cmdlets with several providers, including the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="74887-145">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="74887-145">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="74887-146">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="74887-146">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="74887-147">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="74887-147">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="74887-148">`Convert-Path` alleen bestaande paden worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="74887-148">`Convert-Path` only converts existing paths.</span></span> <span data-ttu-id="74887-149">Het kan niet worden gebruikt om een locatie te converteren die nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="74887-149">It cannot be used to convert a location that does not exist yet.</span></span>

## <span data-ttu-id="74887-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="74887-150">RELATED LINKS</span></span>

[<span data-ttu-id="74887-151">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="74887-151">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="74887-152">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="74887-152">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="74887-153">Split-pad</span><span class="sxs-lookup"><span data-stu-id="74887-153">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="74887-154">Test-pad</span><span class="sxs-lookup"><span data-stu-id="74887-154">Test-Path</span></span>](Test-Path.md)

[<span data-ttu-id="74887-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="74887-155">Get-PSProvider</span></span>](Get-PSProvider.md)
