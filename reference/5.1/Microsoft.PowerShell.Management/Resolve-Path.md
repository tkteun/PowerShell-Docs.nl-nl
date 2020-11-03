---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: a48f2c5f62990258f14195eda934bbf4bbe589a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250564"
---
# <span data-ttu-id="811e8-103">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="811e8-103">Resolve-Path</span></span>

## <span data-ttu-id="811e8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="811e8-104">SYNOPSIS</span></span>
<span data-ttu-id="811e8-105">Hiermee worden de joker tekens in een pad omgezet en wordt de inhoud van het pad weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="811e8-105">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="811e8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="811e8-106">SYNTAX</span></span>

### <span data-ttu-id="811e8-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="811e8-107">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="811e8-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="811e8-108">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="811e8-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="811e8-109">DESCRIPTION</span></span>

<span data-ttu-id="811e8-110">Met de `Resolve-Path` cmdlet worden de items en containers weer gegeven die overeenkomen met het Joker teken patroon op de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="811e8-110">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="811e8-111">De overeenkomst kan bestanden, mappen, register sleutels of andere objecten bevatten die toegankelijk zijn vanuit een PSDrive-provider.</span><span class="sxs-lookup"><span data-stu-id="811e8-111">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="811e8-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="811e8-112">EXAMPLES</span></span>

### <span data-ttu-id="811e8-113">Voor beeld 1: het pad naar de basismap oplossen</span><span class="sxs-lookup"><span data-stu-id="811e8-113">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="811e8-114">De tilde (~) is een steno notatie voor de basismap van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="811e8-114">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="811e8-115">In dit voor beeld wordt `Resolve-Path` de volledig gekwalificeerde pad waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="811e8-115">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="811e8-116">Voor beeld 2: het pad naar de Windows-map oplossen</span><span class="sxs-lookup"><span data-stu-id="811e8-116">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="811e8-117">Wanneer u uitvoert vanuit de hoofdmap van station C:, retourneert deze opdracht het pad van de Windows-map in station C:.</span><span class="sxs-lookup"><span data-stu-id="811e8-117">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="811e8-118">Voor beeld 3: alle paden ophalen in de Windows-map</span><span class="sxs-lookup"><span data-stu-id="811e8-118">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="811e8-119">Met deze opdracht worden alle mappen in de map C:\Windows. geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="811e8-119">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="811e8-120">De opdracht maakt gebruik van een pijplijn operator (|) om een pad naar een padtekenreeks te verzenden `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="811e8-120">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="811e8-121">Voor beeld 4: een UNC-pad omzetten</span><span class="sxs-lookup"><span data-stu-id="811e8-121">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="811e8-122">Met deze opdracht wordt een UNC-pad (Universal Naming Convention) omgezet en worden de shares in het pad geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="811e8-122">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="811e8-123">Voor beeld 5: relatieve paden ophalen</span><span class="sxs-lookup"><span data-stu-id="811e8-123">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="811e8-124">Met deze opdracht worden relatieve paden geretourneerd voor de mappen in de hoofdmap van station C:.</span><span class="sxs-lookup"><span data-stu-id="811e8-124">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="811e8-125">Voor beeld 6: een pad met haakjes oplossen</span><span class="sxs-lookup"><span data-stu-id="811e8-125">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="811e8-126">In dit voor beeld wordt de para meter **LiteralPath** gebruikt om het pad van de \[ XML-test-submap op te lossen \] .</span><span class="sxs-lookup"><span data-stu-id="811e8-126">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="811e8-127">Als u **LiteralPath** gebruikt, worden de haakjes beschouwd als normale tekens in plaats van een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="811e8-127">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="811e8-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="811e8-128">PARAMETERS</span></span>

### <span data-ttu-id="811e8-129">-Credential</span><span class="sxs-lookup"><span data-stu-id="811e8-129">-Credential</span></span>

<span data-ttu-id="811e8-130">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="811e8-130">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="811e8-131">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="811e8-131">The default is the current user.</span></span>

<span data-ttu-id="811e8-132">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of geef een **PSCredential** -object door.</span><span class="sxs-lookup"><span data-stu-id="811e8-132">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="811e8-133">U kunt een **PSCredential** -object maken met behulp van de- `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="811e8-133">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="811e8-134">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="811e8-134">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="811e8-135">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="811e8-135">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="811e8-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="811e8-136">-LiteralPath</span></span>

<span data-ttu-id="811e8-137">Hiermee geeft u het pad op dat moet worden omgezet.</span><span class="sxs-lookup"><span data-stu-id="811e8-137">Specifies the path to be resolved.</span></span> <span data-ttu-id="811e8-138">De waarde van de para meter **LiteralPath** wordt exact als getypt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="811e8-138">The value of the **LiteralPath** parameter is used exactly as typed.</span></span> <span data-ttu-id="811e8-139">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="811e8-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="811e8-140">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="811e8-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="811e8-141">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="811e8-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="811e8-142">-Path</span><span class="sxs-lookup"><span data-stu-id="811e8-142">-Path</span></span>

<span data-ttu-id="811e8-143">Hiermee geeft u het Power shell-pad op dat moet worden omgezet.</span><span class="sxs-lookup"><span data-stu-id="811e8-143">Specifies the PowerShell path to resolve.</span></span> <span data-ttu-id="811e8-144">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="811e8-144">This parameter is required.</span></span> <span data-ttu-id="811e8-145">U kunt ook een padtekenreeks door sluizen naar `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="811e8-145">You can also pipe a path string to `Resolve-Path`.</span></span> <span data-ttu-id="811e8-146">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="811e8-146">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="811e8-147">-Relatief</span><span class="sxs-lookup"><span data-stu-id="811e8-147">-Relative</span></span>

<span data-ttu-id="811e8-148">Geeft aan dat deze cmdlet een relatief pad retourneert.</span><span class="sxs-lookup"><span data-stu-id="811e8-148">Indicates that this cmdlet returns a relative path.</span></span>

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

### <span data-ttu-id="811e8-149">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="811e8-149">-UseTransaction</span></span>
<span data-ttu-id="811e8-150">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="811e8-150">Includes the command in the active transaction.</span></span>
<span data-ttu-id="811e8-151">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="811e8-151">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="811e8-152">Zie about_transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="811e8-152">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="811e8-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="811e8-153">CommonParameters</span></span>

<span data-ttu-id="811e8-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="811e8-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="811e8-155">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="811e8-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="811e8-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="811e8-156">INPUTS</span></span>

### <span data-ttu-id="811e8-157">System. String</span><span class="sxs-lookup"><span data-stu-id="811e8-157">System.String</span></span>

<span data-ttu-id="811e8-158">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="811e8-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="811e8-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="811e8-159">OUTPUTS</span></span>

### <span data-ttu-id="811e8-160">System. Management. Automation. PathInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="811e8-160">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="811e8-161">Retourneert een **PathInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="811e8-161">Returns a **PathInfo** object.</span></span> <span data-ttu-id="811e8-162">Retourneert een teken reeks waarde voor het omgezette pad als u de **relatieve** para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="811e8-162">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="811e8-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="811e8-163">NOTES</span></span>

<span data-ttu-id="811e8-164">De `*-Path` cmdlets werken met het bestands systeem, het REGI ster en de certificaat providers.</span><span class="sxs-lookup"><span data-stu-id="811e8-164">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="811e8-165">`Resolve-Path` is ontworpen om te werken met elke provider.</span><span class="sxs-lookup"><span data-stu-id="811e8-165">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="811e8-166">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="811e8-166">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="811e8-167">Zie [about_providers](../microsoft.powershell.core/about/about_providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="811e8-167">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="811e8-168">`Resolve-Path` Hiermee worden alleen bestaande paden opgelost.</span><span class="sxs-lookup"><span data-stu-id="811e8-168">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="811e8-169">Het kan niet worden gebruikt om een locatie op te lossen die nog niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="811e8-169">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="811e8-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="811e8-170">RELATED LINKS</span></span>

[<span data-ttu-id="811e8-171">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="811e8-171">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="811e8-172">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="811e8-172">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="811e8-173">Split-pad</span><span class="sxs-lookup"><span data-stu-id="811e8-173">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="811e8-174">Test-pad</span><span class="sxs-lookup"><span data-stu-id="811e8-174">Test-Path</span></span>](Test-Path.md)
