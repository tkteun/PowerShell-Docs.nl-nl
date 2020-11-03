---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 9fd99e346d97b9a39298170371164753cf04dad8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250420"
---
# <span data-ttu-id="978ae-103">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="978ae-103">Get-Variable</span></span>

## <span data-ttu-id="978ae-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="978ae-104">SYNOPSIS</span></span>
<span data-ttu-id="978ae-105">Hiermee worden de variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="978ae-105">Gets the variables in the current console.</span></span>

## <span data-ttu-id="978ae-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="978ae-106">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="978ae-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="978ae-107">DESCRIPTION</span></span>

<span data-ttu-id="978ae-108">`Get-Variable`Met de cmdlet worden de Power shell-variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="978ae-108">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="978ae-109">U kunt alleen de waarden van de variabelen ophalen door de para meter **ValueOnly** op te geven en u kunt de variabelen filteren die worden geretourneerd door de naam.</span><span class="sxs-lookup"><span data-stu-id="978ae-109">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="978ae-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="978ae-110">EXAMPLES</span></span>

### <span data-ttu-id="978ae-111">Voor beeld 1: variabelen ophalen per letter</span><span class="sxs-lookup"><span data-stu-id="978ae-111">Example 1: Get variables by letter</span></span>

<span data-ttu-id="978ae-112">Met deze opdracht worden variabelen opgehaald met namen die beginnen met de letter m.</span><span class="sxs-lookup"><span data-stu-id="978ae-112">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="978ae-113">Met deze opdracht wordt ook de waarde van de variabelen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="978ae-113">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="978ae-114">Voor beeld 2: variabele waarden ophalen per letter</span><span class="sxs-lookup"><span data-stu-id="978ae-114">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="978ae-115">Met deze opdracht worden alleen de waarden opgehaald van de variabelen met een naam die begint met m.</span><span class="sxs-lookup"><span data-stu-id="978ae-115">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="978ae-116">Voor beeld 3: variabelen ophalen met twee letters</span><span class="sxs-lookup"><span data-stu-id="978ae-116">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="978ae-117">Met deze opdracht haalt u informatie op over de variabelen die beginnen met de letter M of de letter P.</span><span class="sxs-lookup"><span data-stu-id="978ae-117">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="978ae-118">Voor beeld 4: variabelen ophalen op basis van het bereik</span><span class="sxs-lookup"><span data-stu-id="978ae-118">Example 4: Get variables by scope</span></span>

<span data-ttu-id="978ae-119">De eerste opdracht haalt alleen de variabelen op die in het lokale bereik zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="978ae-119">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="978ae-120">Het is gelijk aan `Get-Variable -Scope Local` en kan worden afgekort tot `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="978ae-120">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="978ae-121">Met de tweede opdracht wordt de `Compare-Object` cmdlet gebruikt om de variabelen te vinden die in het bovenliggende bereik zijn gedefinieerd (Scope 1), maar die alleen zichtbaar zijn in de lokale scope (scope 0).</span><span class="sxs-lookup"><span data-stu-id="978ae-121">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="978ae-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="978ae-122">PARAMETERS</span></span>

### <span data-ttu-id="978ae-123">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="978ae-123">-Exclude</span></span>

<span data-ttu-id="978ae-124">Hiermee geeft u een matrix van items op die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="978ae-124">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="978ae-125">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="978ae-125">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="978ae-126">-Include</span><span class="sxs-lookup"><span data-stu-id="978ae-126">-Include</span></span>

<span data-ttu-id="978ae-127">Hiermee wordt een matrix opgegeven met items waarop de cmdlet wordt toegepast, met uitzonde ring van alle andere.</span><span class="sxs-lookup"><span data-stu-id="978ae-127">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="978ae-128">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="978ae-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="978ae-129">-Name</span><span class="sxs-lookup"><span data-stu-id="978ae-129">-Name</span></span>

<span data-ttu-id="978ae-130">Hiermee geeft u de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="978ae-130">Specifies the name of the variable.</span></span>
<span data-ttu-id="978ae-131">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="978ae-131">Wildcards are permitted.</span></span>
<span data-ttu-id="978ae-132">U kunt ook de naam van een variabele naar `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="978ae-132">You can also pipe a variable name to `Get-Variable`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="978ae-133">-Bereik</span><span class="sxs-lookup"><span data-stu-id="978ae-133">-Scope</span></span>

<span data-ttu-id="978ae-134">Hiermee geeft u de variabelen in het bereik. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="978ae-134">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="978ae-135">**Globaal**</span><span class="sxs-lookup"><span data-stu-id="978ae-135">**Global**</span></span>
- <span data-ttu-id="978ae-136">**Lokaal**</span><span class="sxs-lookup"><span data-stu-id="978ae-136">**Local**</span></span>
- <span data-ttu-id="978ae-137">**Script**</span><span class="sxs-lookup"><span data-stu-id="978ae-137">**Script**</span></span>
- <span data-ttu-id="978ae-138">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="978ae-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="978ae-139">**Local** is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="978ae-139">**Local** is the default.</span></span>
<span data-ttu-id="978ae-140">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="978ae-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="978ae-141">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="978ae-141">-ValueOnly</span></span>

<span data-ttu-id="978ae-142">Geeft aan dat met deze cmdlet alleen de waarde van de variabele wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="978ae-142">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="978ae-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="978ae-143">CommonParameters</span></span>

<span data-ttu-id="978ae-144">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="978ae-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="978ae-145">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="978ae-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="978ae-146">INVOER</span><span class="sxs-lookup"><span data-stu-id="978ae-146">INPUTS</span></span>

### <span data-ttu-id="978ae-147">System. String</span><span class="sxs-lookup"><span data-stu-id="978ae-147">System.String</span></span>

<span data-ttu-id="978ae-148">U kunt een teken reeks met de naam van de variabele door sluizen naar `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="978ae-148">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="978ae-149">UITVOER</span><span class="sxs-lookup"><span data-stu-id="978ae-149">OUTPUTS</span></span>

### <span data-ttu-id="978ae-150">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="978ae-150">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="978ae-151">Met deze cmdlet wordt een **System. Management. AutomationPSVariable** -object geretourneerd voor elke variabele die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="978ae-151">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="978ae-152">Het object type is afhankelijk van de variabele.</span><span class="sxs-lookup"><span data-stu-id="978ae-152">The object type depends on the variable.</span></span>

### <span data-ttu-id="978ae-153">System. object []</span><span class="sxs-lookup"><span data-stu-id="978ae-153">System.Object[]</span></span>

<span data-ttu-id="978ae-154">Als u de para meter **ValueOnly** opgeeft en de waarde van de opgegeven variabele een verzameling is, `Get-Variable` retourneert een `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="978ae-154">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="978ae-155">Dit gedrag voor komt dat normale bewerking door de pijp lijn de waarden van de variabele een voor een kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="978ae-155">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="978ae-156">Een tijdelijke oplossing voor het afdwingen van verzamelings inventarisatie is het insluiten `Get-Variable` van de opdracht tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="978ae-156">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="978ae-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="978ae-157">NOTES</span></span>

- <span data-ttu-id="978ae-158">Met deze cmdlet worden geen omgevings variabelen beheerd.</span><span class="sxs-lookup"><span data-stu-id="978ae-158">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="978ae-159">Als u omgevings variabelen wilt beheren, kunt u de omgevings variabele provider gebruiken.</span><span class="sxs-lookup"><span data-stu-id="978ae-159">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="978ae-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="978ae-160">RELATED LINKS</span></span>

[<span data-ttu-id="978ae-161">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="978ae-161">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="978ae-162">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="978ae-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="978ae-163">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="978ae-163">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="978ae-164">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="978ae-164">Set-Variable</span></span>](Set-Variable.md)
