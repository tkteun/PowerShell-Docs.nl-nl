---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 50bc53d284fada31cf01b0504d89128eeb1710e2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250195"
---
# <span data-ttu-id="cebdf-103">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="cebdf-103">Import-Alias</span></span>

## <span data-ttu-id="cebdf-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cebdf-104">SYNOPSIS</span></span>
<span data-ttu-id="cebdf-105">Hiermee wordt een alias lijst uit een bestand geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="cebdf-105">Imports an alias list from a file.</span></span>

## <span data-ttu-id="cebdf-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cebdf-106">SYNTAX</span></span>

### <span data-ttu-id="cebdf-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="cebdf-107">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cebdf-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="cebdf-108">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="cebdf-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cebdf-109">DESCRIPTION</span></span>

<span data-ttu-id="cebdf-110">Met de `Import-Alias` cmdlet wordt een alias lijst uit een bestand geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="cebdf-110">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="cebdf-111">Als er in Windows Power Shell 3,0 een beveiligings functie wordt gebruikt, `Import-Alias` worden bestaande aliassen standaard niet overschreven.</span><span class="sxs-lookup"><span data-stu-id="cebdf-111">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="cebdf-112">Als u een bestaande alias wilt overschrijven, gebruikt u de para meter Force om te **zorgen** dat de inhoud van het alias bestand veilig is.</span><span class="sxs-lookup"><span data-stu-id="cebdf-112">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="cebdf-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cebdf-113">EXAMPLES</span></span>

### <span data-ttu-id="cebdf-114">Voor beeld 1: aliassen importeren uit een bestand</span><span class="sxs-lookup"><span data-stu-id="cebdf-114">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="cebdf-115">Met deze opdracht worden alias gegevens uit een bestand met de naam test.txt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="cebdf-115">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="cebdf-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cebdf-116">PARAMETERS</span></span>

### <span data-ttu-id="cebdf-117">-Force</span><span class="sxs-lookup"><span data-stu-id="cebdf-117">-Force</span></span>

<span data-ttu-id="cebdf-118">Hiermee kan de cmdlet een alias importeren die al is gedefinieerd of alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="cebdf-118">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="cebdf-119">U kunt de volgende opdracht gebruiken om informatie weer te geven over de momenteel gedefinieerde aliassen:</span><span class="sxs-lookup"><span data-stu-id="cebdf-119">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="cebdf-120">Als de bijbehorende alias alleen-lezen is, wordt deze weer gegeven in de waarde van de eigenschap **Options** .</span><span class="sxs-lookup"><span data-stu-id="cebdf-120">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="cebdf-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cebdf-121">-LiteralPath</span></span>

<span data-ttu-id="cebdf-122">Hiermee geeft u het pad naar een bestand met geëxporteerde alias gegevens.</span><span class="sxs-lookup"><span data-stu-id="cebdf-122">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="cebdf-123">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="cebdf-123">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="cebdf-124">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="cebdf-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="cebdf-125">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="cebdf-125">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="cebdf-126">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="cebdf-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cebdf-127">-PassThru</span><span class="sxs-lookup"><span data-stu-id="cebdf-127">-PassThru</span></span>

<span data-ttu-id="cebdf-128">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="cebdf-128">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="cebdf-129">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="cebdf-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="cebdf-130">-Path</span><span class="sxs-lookup"><span data-stu-id="cebdf-130">-Path</span></span>

<span data-ttu-id="cebdf-131">Hiermee geeft u het pad naar een bestand met geëxporteerde alias gegevens.</span><span class="sxs-lookup"><span data-stu-id="cebdf-131">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="cebdf-132">Joker tekens zijn toegestaan, maar moeten worden omgezet in één naam.</span><span class="sxs-lookup"><span data-stu-id="cebdf-132">Wildcards are allowed but they must resolve to a single name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="cebdf-133">-Bereik</span><span class="sxs-lookup"><span data-stu-id="cebdf-133">-Scope</span></span>

<span data-ttu-id="cebdf-134">Hiermee geeft u het bereik op waarin de aliassen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="cebdf-134">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="cebdf-135">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="cebdf-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cebdf-136">Globaal</span><span class="sxs-lookup"><span data-stu-id="cebdf-136">Global</span></span>
- <span data-ttu-id="cebdf-137">Lokaal</span><span class="sxs-lookup"><span data-stu-id="cebdf-137">Local</span></span>
- <span data-ttu-id="cebdf-138">Script</span><span class="sxs-lookup"><span data-stu-id="cebdf-138">Script</span></span>
- <span data-ttu-id="cebdf-139">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="cebdf-139">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="cebdf-140">De standaard waarde is lokaal.</span><span class="sxs-lookup"><span data-stu-id="cebdf-140">The default is Local.</span></span>
<span data-ttu-id="cebdf-141">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cebdf-141">For more information, see about_Scopes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cebdf-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cebdf-142">-Confirm</span></span>

<span data-ttu-id="cebdf-143">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cebdf-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cebdf-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cebdf-144">-WhatIf</span></span>

<span data-ttu-id="cebdf-145">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cebdf-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cebdf-146">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cebdf-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cebdf-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cebdf-147">CommonParameters</span></span>

<span data-ttu-id="cebdf-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cebdf-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cebdf-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cebdf-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cebdf-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="cebdf-150">INPUTS</span></span>

### <span data-ttu-id="cebdf-151">System. String</span><span class="sxs-lookup"><span data-stu-id="cebdf-151">System.String</span></span>

<span data-ttu-id="cebdf-152">U kunt een teken reeks met een pad naar door sluizen `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="cebdf-152">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="cebdf-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cebdf-153">OUTPUTS</span></span>

### <span data-ttu-id="cebdf-154">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="cebdf-154">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="cebdf-155">Wanneer u de para meter **PassThru** gebruikt, `Import-Alias` retourneert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="cebdf-155">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="cebdf-156">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="cebdf-156">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cebdf-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cebdf-157">NOTES</span></span>

## <span data-ttu-id="cebdf-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cebdf-158">RELATED LINKS</span></span>

[<span data-ttu-id="cebdf-159">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="cebdf-159">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="cebdf-160">Get-alias</span><span class="sxs-lookup"><span data-stu-id="cebdf-160">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="cebdf-161">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="cebdf-161">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="cebdf-162">Set-alias</span><span class="sxs-lookup"><span data-stu-id="cebdf-162">Set-Alias</span></span>](Set-Alias.md)

