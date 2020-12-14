---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 6cd7a4611f6118ed1f0846d9c11a8fe8edc69ef0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705595"
---
# <span data-ttu-id="142ce-102">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="142ce-102">Get-Variable</span></span>

## <span data-ttu-id="142ce-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="142ce-103">SYNOPSIS</span></span>
<span data-ttu-id="142ce-104">Hiermee worden de variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="142ce-104">Gets the variables in the current console.</span></span>

## <span data-ttu-id="142ce-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="142ce-105">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="142ce-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="142ce-106">DESCRIPTION</span></span>

<span data-ttu-id="142ce-107">`Get-Variable`Met de cmdlet worden de Power shell-variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="142ce-107">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="142ce-108">U kunt alleen de waarden van de variabelen ophalen door de para meter **ValueOnly** op te geven en u kunt de variabelen filteren die worden geretourneerd door de naam.</span><span class="sxs-lookup"><span data-stu-id="142ce-108">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="142ce-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="142ce-109">EXAMPLES</span></span>

### <span data-ttu-id="142ce-110">Voor beeld 1: variabelen ophalen per letter</span><span class="sxs-lookup"><span data-stu-id="142ce-110">Example 1: Get variables by letter</span></span>

<span data-ttu-id="142ce-111">Met deze opdracht worden variabelen opgehaald met namen die beginnen met de letter m.</span><span class="sxs-lookup"><span data-stu-id="142ce-111">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="142ce-112">Met deze opdracht wordt ook de waarde van de variabelen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="142ce-112">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="142ce-113">Voor beeld 2: variabele waarden ophalen per letter</span><span class="sxs-lookup"><span data-stu-id="142ce-113">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="142ce-114">Met deze opdracht worden alleen de waarden opgehaald van de variabelen met een naam die begint met m.</span><span class="sxs-lookup"><span data-stu-id="142ce-114">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="142ce-115">Voor beeld 3: variabelen ophalen met twee letters</span><span class="sxs-lookup"><span data-stu-id="142ce-115">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="142ce-116">Met deze opdracht haalt u informatie op over de variabelen die beginnen met de letter M of de letter P.</span><span class="sxs-lookup"><span data-stu-id="142ce-116">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="142ce-117">Voor beeld 4: variabelen ophalen op basis van het bereik</span><span class="sxs-lookup"><span data-stu-id="142ce-117">Example 4: Get variables by scope</span></span>

<span data-ttu-id="142ce-118">De eerste opdracht haalt alleen de variabelen op die in het lokale bereik zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="142ce-118">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="142ce-119">Het is gelijk aan `Get-Variable -Scope Local` en kan worden afgekort tot `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="142ce-119">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="142ce-120">Met de tweede opdracht wordt de `Compare-Object` cmdlet gebruikt om de variabelen te vinden die in het bovenliggende bereik zijn gedefinieerd (Scope 1), maar die alleen zichtbaar zijn in de lokale scope (scope 0).</span><span class="sxs-lookup"><span data-stu-id="142ce-120">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="142ce-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="142ce-121">PARAMETERS</span></span>

### <span data-ttu-id="142ce-122">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="142ce-122">-Exclude</span></span>

<span data-ttu-id="142ce-123">Hiermee geeft u een matrix van items op die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="142ce-123">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="142ce-124">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="142ce-124">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="142ce-125">-Include</span><span class="sxs-lookup"><span data-stu-id="142ce-125">-Include</span></span>

<span data-ttu-id="142ce-126">Hiermee wordt een matrix opgegeven met items waarop de cmdlet wordt toegepast, met uitzonde ring van alle andere.</span><span class="sxs-lookup"><span data-stu-id="142ce-126">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="142ce-127">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="142ce-127">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="142ce-128">-Name</span><span class="sxs-lookup"><span data-stu-id="142ce-128">-Name</span></span>

<span data-ttu-id="142ce-129">Hiermee geeft u de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="142ce-129">Specifies the name of the variable.</span></span>
<span data-ttu-id="142ce-130">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="142ce-130">Wildcards are permitted.</span></span>
<span data-ttu-id="142ce-131">U kunt ook de naam van een variabele naar `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="142ce-131">You can also pipe a variable name to `Get-Variable`.</span></span>

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

### <span data-ttu-id="142ce-132">-Bereik</span><span class="sxs-lookup"><span data-stu-id="142ce-132">-Scope</span></span>

<span data-ttu-id="142ce-133">Hiermee geeft u de variabelen in het bereik. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="142ce-133">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="142ce-134">**Globaal**</span><span class="sxs-lookup"><span data-stu-id="142ce-134">**Global**</span></span>
- <span data-ttu-id="142ce-135">**Lokale**</span><span class="sxs-lookup"><span data-stu-id="142ce-135">**Local**</span></span>
- <span data-ttu-id="142ce-136">**Script**</span><span class="sxs-lookup"><span data-stu-id="142ce-136">**Script**</span></span>
- <span data-ttu-id="142ce-137">Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)</span><span class="sxs-lookup"><span data-stu-id="142ce-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="142ce-138">**Local** is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="142ce-138">**Local** is the default.</span></span>
<span data-ttu-id="142ce-139">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="142ce-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="142ce-140">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="142ce-140">-ValueOnly</span></span>

<span data-ttu-id="142ce-141">Geeft aan dat met deze cmdlet alleen de waarde van de variabele wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="142ce-141">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="142ce-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="142ce-142">CommonParameters</span></span>

<span data-ttu-id="142ce-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="142ce-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="142ce-144">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="142ce-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="142ce-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="142ce-145">INPUTS</span></span>

### <span data-ttu-id="142ce-146">System. String</span><span class="sxs-lookup"><span data-stu-id="142ce-146">System.String</span></span>

<span data-ttu-id="142ce-147">U kunt een teken reeks met de naam van de variabele door sluizen naar `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="142ce-147">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="142ce-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="142ce-148">OUTPUTS</span></span>

### <span data-ttu-id="142ce-149">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="142ce-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="142ce-150">Met deze cmdlet wordt een **System. Management. AutomationPSVariable** -object geretourneerd voor elke variabele die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="142ce-150">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="142ce-151">Het object type is afhankelijk van de variabele.</span><span class="sxs-lookup"><span data-stu-id="142ce-151">The object type depends on the variable.</span></span>

### <span data-ttu-id="142ce-152">System. object []</span><span class="sxs-lookup"><span data-stu-id="142ce-152">System.Object[]</span></span>

<span data-ttu-id="142ce-153">Als u de para meter **ValueOnly** opgeeft en de waarde van de opgegeven variabele een verzameling is, `Get-Variable` retourneert een `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="142ce-153">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="142ce-154">Dit gedrag voor komt dat normale bewerking door de pijp lijn de waarden van de variabele een voor een kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="142ce-154">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="142ce-155">Een tijdelijke oplossing voor het afdwingen van verzamelings inventarisatie is het insluiten `Get-Variable` van de opdracht tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="142ce-155">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="142ce-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="142ce-156">NOTES</span></span>

- <span data-ttu-id="142ce-157">Met deze cmdlet worden geen omgevings variabelen beheerd.</span><span class="sxs-lookup"><span data-stu-id="142ce-157">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="142ce-158">Als u omgevings variabelen wilt beheren, kunt u de omgevings variabele provider gebruiken.</span><span class="sxs-lookup"><span data-stu-id="142ce-158">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="142ce-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="142ce-159">RELATED LINKS</span></span>

[<span data-ttu-id="142ce-160">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="142ce-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="142ce-161">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="142ce-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="142ce-162">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="142ce-162">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="142ce-163">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="142ce-163">Set-Variable</span></span>](Set-Variable.md)

