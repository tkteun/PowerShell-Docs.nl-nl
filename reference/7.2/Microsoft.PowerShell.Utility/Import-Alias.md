---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 20bc5d141b68cab19374afbe44b3472c72bf69bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705435"
---
# <span data-ttu-id="9c41d-102">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="9c41d-102">Import-Alias</span></span>

## <span data-ttu-id="9c41d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9c41d-103">SYNOPSIS</span></span>
<span data-ttu-id="9c41d-104">Hiermee wordt een alias lijst uit een bestand geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9c41d-104">Imports an alias list from a file.</span></span>

## <span data-ttu-id="9c41d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9c41d-105">SYNTAX</span></span>

### <span data-ttu-id="9c41d-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="9c41d-106">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c41d-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c41d-107">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9c41d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9c41d-108">DESCRIPTION</span></span>

<span data-ttu-id="9c41d-109">Met de `Import-Alias` cmdlet wordt een alias lijst uit een bestand geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9c41d-109">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="9c41d-110">Als er in Windows Power Shell 3,0 een beveiligings functie wordt gebruikt, `Import-Alias` worden bestaande aliassen standaard niet overschreven.</span><span class="sxs-lookup"><span data-stu-id="9c41d-110">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="9c41d-111">Als u een bestaande alias wilt overschrijven, gebruikt u de para meter Force om te **zorgen** dat de inhoud van het alias bestand veilig is.</span><span class="sxs-lookup"><span data-stu-id="9c41d-111">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="9c41d-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9c41d-112">EXAMPLES</span></span>

### <span data-ttu-id="9c41d-113">Voor beeld 1: aliassen importeren uit een bestand</span><span class="sxs-lookup"><span data-stu-id="9c41d-113">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="9c41d-114">Met deze opdracht worden alias gegevens uit een bestand met de naam test.txt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9c41d-114">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="9c41d-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c41d-115">PARAMETERS</span></span>

### <span data-ttu-id="9c41d-116">-Force</span><span class="sxs-lookup"><span data-stu-id="9c41d-116">-Force</span></span>

<span data-ttu-id="9c41d-117">Hiermee kan de cmdlet een alias importeren die al is gedefinieerd of alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="9c41d-117">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="9c41d-118">U kunt de volgende opdracht gebruiken om informatie weer te geven over de momenteel gedefinieerde aliassen:</span><span class="sxs-lookup"><span data-stu-id="9c41d-118">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="9c41d-119">Als de bijbehorende alias alleen-lezen is, wordt deze weer gegeven in de waarde van de eigenschap **Options** .</span><span class="sxs-lookup"><span data-stu-id="9c41d-119">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="9c41d-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c41d-120">-LiteralPath</span></span>

<span data-ttu-id="9c41d-121">Hiermee geeft u het pad naar een bestand met geëxporteerde alias gegevens.</span><span class="sxs-lookup"><span data-stu-id="9c41d-121">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="9c41d-122">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="9c41d-122">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="9c41d-123">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="9c41d-123">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="9c41d-124">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="9c41d-124">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="9c41d-125">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="9c41d-125">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="9c41d-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9c41d-126">-PassThru</span></span>

<span data-ttu-id="9c41d-127">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="9c41d-127">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="9c41d-128">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9c41d-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9c41d-129">-Path</span><span class="sxs-lookup"><span data-stu-id="9c41d-129">-Path</span></span>

<span data-ttu-id="9c41d-130">Hiermee geeft u het pad naar een bestand met geëxporteerde alias gegevens.</span><span class="sxs-lookup"><span data-stu-id="9c41d-130">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="9c41d-131">Joker tekens zijn toegestaan, maar moeten worden omgezet in één naam.</span><span class="sxs-lookup"><span data-stu-id="9c41d-131">Wildcards are allowed but they must resolve to a single name.</span></span>

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

### <span data-ttu-id="9c41d-132">-Bereik</span><span class="sxs-lookup"><span data-stu-id="9c41d-132">-Scope</span></span>

<span data-ttu-id="9c41d-133">Hiermee geeft u het bereik op waarin de aliassen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9c41d-133">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="9c41d-134">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9c41d-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9c41d-135">Globaal</span><span class="sxs-lookup"><span data-stu-id="9c41d-135">Global</span></span>
- <span data-ttu-id="9c41d-136">Lokaal</span><span class="sxs-lookup"><span data-stu-id="9c41d-136">Local</span></span>
- <span data-ttu-id="9c41d-137">Script</span><span class="sxs-lookup"><span data-stu-id="9c41d-137">Script</span></span>
- <span data-ttu-id="9c41d-138">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="9c41d-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="9c41d-139">De standaard waarde is lokaal.</span><span class="sxs-lookup"><span data-stu-id="9c41d-139">The default is Local.</span></span>
<span data-ttu-id="9c41d-140">Zie about_Scopes voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c41d-140">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="9c41d-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c41d-141">-Confirm</span></span>

<span data-ttu-id="9c41d-142">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c41d-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c41d-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c41d-143">-WhatIf</span></span>

<span data-ttu-id="9c41d-144">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c41d-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9c41d-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c41d-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c41d-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c41d-146">CommonParameters</span></span>

<span data-ttu-id="9c41d-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c41d-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c41d-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c41d-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c41d-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="9c41d-149">INPUTS</span></span>

### <span data-ttu-id="9c41d-150">System. String</span><span class="sxs-lookup"><span data-stu-id="9c41d-150">System.String</span></span>

<span data-ttu-id="9c41d-151">U kunt een teken reeks met een pad naar door sluizen `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="9c41d-151">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="9c41d-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9c41d-152">OUTPUTS</span></span>

### <span data-ttu-id="9c41d-153">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="9c41d-153">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="9c41d-154">Wanneer u de para meter **PassThru** gebruikt, `Import-Alias` retourneert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9c41d-154">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="9c41d-155">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9c41d-155">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9c41d-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9c41d-156">NOTES</span></span>

## <span data-ttu-id="9c41d-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9c41d-157">RELATED LINKS</span></span>

[<span data-ttu-id="9c41d-158">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="9c41d-158">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="9c41d-159">Get-alias</span><span class="sxs-lookup"><span data-stu-id="9c41d-159">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="9c41d-160">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="9c41d-160">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="9c41d-161">Set-alias</span><span class="sxs-lookup"><span data-stu-id="9c41d-161">Set-Alias</span></span>](Set-Alias.md)

