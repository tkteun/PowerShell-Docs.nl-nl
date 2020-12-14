---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 0481526aead285e3d5fb494218d1573e03216f2e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705874"
---
# <span data-ttu-id="c66a2-102">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="c66a2-102">Resolve-Path</span></span>

## <span data-ttu-id="c66a2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c66a2-103">SYNOPSIS</span></span>
<span data-ttu-id="c66a2-104">Hiermee worden de joker tekens in een pad omgezet en wordt de inhoud van het pad weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c66a2-104">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="c66a2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c66a2-105">SYNTAX</span></span>

### <span data-ttu-id="c66a2-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="c66a2-106">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="c66a2-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c66a2-107">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="c66a2-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c66a2-108">DESCRIPTION</span></span>

<span data-ttu-id="c66a2-109">Met de `Resolve-Path` cmdlet worden de items en containers weer gegeven die overeenkomen met het Joker teken patroon op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="c66a2-109">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="c66a2-110">De overeenkomst kan bestanden, mappen, register sleutels of andere objecten bevatten die toegankelijk zijn vanuit een PSDrive-provider.</span><span class="sxs-lookup"><span data-stu-id="c66a2-110">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="c66a2-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c66a2-111">EXAMPLES</span></span>

### <span data-ttu-id="c66a2-112">Voor beeld 1: het pad naar de basismap oplossen</span><span class="sxs-lookup"><span data-stu-id="c66a2-112">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="c66a2-113">De tilde (~) is een steno notatie voor de basismap van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c66a2-113">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="c66a2-114">In dit voor beeld wordt `Resolve-Path` de volledig gekwalificeerde pad waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c66a2-114">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="c66a2-115">Voor beeld 2: het pad naar de Windows-map oplossen</span><span class="sxs-lookup"><span data-stu-id="c66a2-115">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="c66a2-116">Wanneer u uitvoert vanuit de hoofdmap van station C:, retourneert deze opdracht het pad van de Windows-map in station C:.</span><span class="sxs-lookup"><span data-stu-id="c66a2-116">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="c66a2-117">Voor beeld 3: alle paden ophalen in de Windows-map</span><span class="sxs-lookup"><span data-stu-id="c66a2-117">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="c66a2-118">Met deze opdracht worden alle mappen in de map C:\Windows. geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c66a2-118">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="c66a2-119">De opdracht maakt gebruik van een pijplijn operator (|) om een pad naar een padtekenreeks te verzenden `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="c66a2-119">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="c66a2-120">Voor beeld 4: een UNC-pad omzetten</span><span class="sxs-lookup"><span data-stu-id="c66a2-120">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="c66a2-121">Met deze opdracht wordt een UNC-pad (Universal Naming Convention) omgezet en worden de shares in het pad geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c66a2-121">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="c66a2-122">Voor beeld 5: relatieve paden ophalen</span><span class="sxs-lookup"><span data-stu-id="c66a2-122">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="c66a2-123">Met deze opdracht worden relatieve paden geretourneerd voor de mappen in de hoofdmap van station C:.</span><span class="sxs-lookup"><span data-stu-id="c66a2-123">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="c66a2-124">Voor beeld 6: een pad met haakjes oplossen</span><span class="sxs-lookup"><span data-stu-id="c66a2-124">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="c66a2-125">In dit voor beeld wordt de para meter **LiteralPath** gebruikt om het pad van de \[ XML-test-submap op te lossen \] .</span><span class="sxs-lookup"><span data-stu-id="c66a2-125">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="c66a2-126">Als u **LiteralPath** gebruikt, worden de haakjes beschouwd als normale tekens in plaats van een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="c66a2-126">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="c66a2-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c66a2-127">PARAMETERS</span></span>

### <span data-ttu-id="c66a2-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="c66a2-128">-Credential</span></span>

<span data-ttu-id="c66a2-129">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c66a2-129">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c66a2-130">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c66a2-130">The default is the current user.</span></span>

<span data-ttu-id="c66a2-131">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of geef een **PSCredential** -object door.</span><span class="sxs-lookup"><span data-stu-id="c66a2-131">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="c66a2-132">U kunt een **PSCredential** -object maken met behulp van de- `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c66a2-132">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c66a2-133">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="c66a2-133">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="c66a2-134">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="c66a2-134">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="c66a2-135">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c66a2-135">-LiteralPath</span></span>

<span data-ttu-id="c66a2-136">Hiermee geeft u het pad op dat moet worden omgezet.</span><span class="sxs-lookup"><span data-stu-id="c66a2-136">Specifies the path to be resolved.</span></span>
<span data-ttu-id="c66a2-137">De waarde van de para meter **LiteralPath** wordt exact als getypt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c66a2-137">The value of the **LiteralPath** parameter is used exactly as typed.</span></span>
<span data-ttu-id="c66a2-138">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="c66a2-138">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="c66a2-139">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c66a2-139">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="c66a2-140">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="c66a2-140">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="c66a2-141">-Path</span><span class="sxs-lookup"><span data-stu-id="c66a2-141">-Path</span></span>

<span data-ttu-id="c66a2-142">Hiermee geeft u het Power shell-pad op dat moet worden omgezet.</span><span class="sxs-lookup"><span data-stu-id="c66a2-142">Specifies the PowerShell path to resolve.</span></span>
<span data-ttu-id="c66a2-143">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="c66a2-143">This parameter is required.</span></span>
<span data-ttu-id="c66a2-144">U kunt ook een padtekenreeks door sluizen naar `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="c66a2-144">You can also pipe a path string to `Resolve-Path`.</span></span>
<span data-ttu-id="c66a2-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c66a2-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c66a2-146">-Relatief</span><span class="sxs-lookup"><span data-stu-id="c66a2-146">-Relative</span></span>

<span data-ttu-id="c66a2-147">Geeft aan dat deze cmdlet een relatief pad retourneert.</span><span class="sxs-lookup"><span data-stu-id="c66a2-147">Indicates that this cmdlet returns a relative path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c66a2-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c66a2-148">CommonParameters</span></span>

<span data-ttu-id="c66a2-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c66a2-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c66a2-150">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c66a2-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c66a2-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="c66a2-151">INPUTS</span></span>

### <span data-ttu-id="c66a2-152">System. String</span><span class="sxs-lookup"><span data-stu-id="c66a2-152">System.String</span></span>

<span data-ttu-id="c66a2-153">U kunt een teken reeks met een pad naar deze cmdlet door sluizen</span><span class="sxs-lookup"><span data-stu-id="c66a2-153">You can pipe a string that contains a path to this cmdlet</span></span>

## <span data-ttu-id="c66a2-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c66a2-154">OUTPUTS</span></span>

### <span data-ttu-id="c66a2-155">System. Management. Automation. PathInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="c66a2-155">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="c66a2-156">Retourneert een **PathInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="c66a2-156">Returns a **PathInfo** object.</span></span> <span data-ttu-id="c66a2-157">Retourneert een teken reeks waarde voor het omgezette pad als u de **relatieve** para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c66a2-157">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="c66a2-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c66a2-158">NOTES</span></span>

<span data-ttu-id="c66a2-159">De `*-Path` cmdlets werken met het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="c66a2-159">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="c66a2-160">`Resolve-Path` is ontworpen om te werken met elke provider.</span><span class="sxs-lookup"><span data-stu-id="c66a2-160">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="c66a2-161">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="c66a2-161">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="c66a2-162">Zie [about_providers](../microsoft.powershell.core/about/about_providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c66a2-162">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="c66a2-163">`Resolve-Path` Hiermee worden alleen bestaande paden opgelost.</span><span class="sxs-lookup"><span data-stu-id="c66a2-163">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="c66a2-164">Het kan niet worden gebruikt om een locatie op te lossen die nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="c66a2-164">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="c66a2-165">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c66a2-165">RELATED LINKS</span></span>

[<span data-ttu-id="c66a2-166">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="c66a2-166">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="c66a2-167">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="c66a2-167">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="c66a2-168">Split-pad</span><span class="sxs-lookup"><span data-stu-id="c66a2-168">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="c66a2-169">Test-pad</span><span class="sxs-lookup"><span data-stu-id="c66a2-169">Test-Path</span></span>](Test-Path.md)

