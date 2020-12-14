---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 8ede1375faa1287b70eeb49689ec7fe1bb800d55
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705935"
---
# <span data-ttu-id="5f79a-102">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="5f79a-102">Remove-TypeData</span></span>

## <span data-ttu-id="5f79a-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="5f79a-103">Synopsis</span></span>
<span data-ttu-id="5f79a-104">Hiermee verwijdert u uitgebreide typen van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-104">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="5f79a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f79a-105">Syntax</span></span>

### <span data-ttu-id="5f79a-106">RemoveTypeDataSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="5f79a-106">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5f79a-107">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="5f79a-107">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5f79a-108">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="5f79a-108">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5f79a-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5f79a-109">DESCRIPTION</span></span>

<span data-ttu-id="5f79a-110">`Remove-TypeData`Met de cmdlet worden uitgebreide type gegevens uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f79a-110">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="5f79a-111">Deze cmdlet is alleen van invloed op de huidige sessie en sessies die zijn gemaakt in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-111">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="5f79a-112">U kunt eigenschappen en methoden toevoegen aan objecten in Power shell door ze te definiëren in `Update-TypeData` opdrachten en `Types.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="5f79a-112">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="5f79a-113">`Remove-TypeData` Hiermee verwijdert u de uitgebreide eigenschappen en methoden van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-113">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="5f79a-114">`Remove-TypeData` verwijdert de bestanden niet `Types.ps1xml` of verwijdert uitgebreide type definities van de `Types.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="5f79a-114">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="5f79a-115">`Types.ps1xml`Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)voor meer informatie over bestanden.</span><span class="sxs-lookup"><span data-stu-id="5f79a-115">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="5f79a-116">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5f79a-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5f79a-117">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="5f79a-117">Examples</span></span>

### <span data-ttu-id="5f79a-118">Voor beeld 1: type gegevens verwijderen voor een opgegeven type</span><span class="sxs-lookup"><span data-stu-id="5f79a-118">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="5f79a-119">In dit voor beeld worden alle type gegevens voor het type **System. matrix** verwijderd uit de sessie, inclusief type gegevens die zijn toegevoegd door een `Types.ps1xml` bestand en dynamische type gegevens die zijn toegevoegd aan de-sessie met behulp van de- `Update-TypeData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f79a-119">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="5f79a-120">Voor beeld 2: een uitgebreide-gegevens type uit een sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="5f79a-120">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="5f79a-121">Dit voor beeld toont het effect van het verwijderen van uitgebreide type gegevens uit een sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-121">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="5f79a-122">Met de eerste worden `Get-TypeData` uitgebreide type gegevens voor het type **System. datetime** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5f79a-122">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="5f79a-123">In de uitvoer ziet u dat een **datum/tijd** -eigenschap is toegevoegd aan alle **System. datetime** -objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="5f79a-123">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="5f79a-124">De `Get-Date` cmdlet retourneert een **System. datetime** -object.</span><span class="sxs-lookup"><span data-stu-id="5f79a-124">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="5f79a-125">De opdracht gebruikt punt notatie om de waarde van de eigenschap **DateTime** van het object **System. datetime** op te halen dat `Get-Date` retourneert.</span><span class="sxs-lookup"><span data-stu-id="5f79a-125">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

<span data-ttu-id="5f79a-126">De volgende `Get-TypeData` cmdlet voor het ophalen van alle uitgebreide type gegevens voor het type **System. datetime** en pijpen die de cmdlet voor het `Remove-TypeData` verwijderen van de gegevens van het uitgebreide type hebben.</span><span class="sxs-lookup"><span data-stu-id="5f79a-126">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="5f79a-127">De laatste `Get-Date` cmdlet toont het effect van het verwijderen van de uitgebreide type gegevens voor het type **System. datetime** .</span><span class="sxs-lookup"><span data-stu-id="5f79a-127">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="5f79a-128">Omdat de eigenschap **System. datetime** niet meer bestaat, retourneert een opdracht om de waarde ervan op te halen niets.</span><span class="sxs-lookup"><span data-stu-id="5f79a-128">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="5f79a-129">Voor beeld 3: uitgebreide typen voor modules verwijderen</span><span class="sxs-lookup"><span data-stu-id="5f79a-129">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="5f79a-130">In dit voor beeld worden alle uitgebreide type gegevens voor module objecten verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f79a-130">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="5f79a-131">Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de naam van het object type op en verwijdert alle type gegevens voor alle objecten van dat type.</span><span class="sxs-lookup"><span data-stu-id="5f79a-131">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="5f79a-132">Voor beeld 4: uitgebreide typen verwijderen uit opgegeven modules</span><span class="sxs-lookup"><span data-stu-id="5f79a-132">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="5f79a-133">In dit voor beeld wordt de para meter **Path** van de `Remove-TypeData` cmdlet gebruikt voor het verwijderen van de uitgebreide typen die zijn gedefinieerd in de `Types.ps1xml` bestanden die worden toegevoegd door de **PSScheduledJob** -en **PSWorkflow** -modules.</span><span class="sxs-lookup"><span data-stu-id="5f79a-133">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="5f79a-134">Deze opdracht is niet van invloed op dynamische type gegevens die worden toegevoegd met behulp van de- `Update-TypeData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f79a-134">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="5f79a-135">De opdracht wordt alleen uitgevoerd als de modules zijn geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-135">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="5f79a-136">Zie [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="5f79a-136">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="5f79a-137">Voor beeld 5: uitgebreide typen verwijderen uit een externe sessie</span><span class="sxs-lookup"><span data-stu-id="5f79a-137">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="5f79a-138">In dit voor beeld worden uitgebreide typen verwijderd uit een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-138">This example removes extended types from a remote session.</span></span> <span data-ttu-id="5f79a-139">De opdracht gebruikt de `Invoke-Command` cmdlet voor het verwijderen van uitgebreide type gegevens voor alle CIM-typen in de sessies in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="5f79a-139">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="5f79a-140">Parameters</span><span class="sxs-lookup"><span data-stu-id="5f79a-140">Parameters</span></span>

### <span data-ttu-id="5f79a-141">-Path</span><span class="sxs-lookup"><span data-stu-id="5f79a-141">-Path</span></span>

<span data-ttu-id="5f79a-142">Hiermee geeft u een matrix met bestanden op die met deze cmdlet worden verwijderd uit de uitgebreide type gegevens van de sessie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-142">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="5f79a-143">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="5f79a-143">This parameter is required.</span></span>

<span data-ttu-id="5f79a-144">Voer de paden en bestands namen van een of meer `Types.ps1xml` bestanden in.</span><span class="sxs-lookup"><span data-stu-id="5f79a-144">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="5f79a-145">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f79a-145">Wildcards are not supported.</span></span> <span data-ttu-id="5f79a-146">Als u het pad weglaat, is de standaard locatie de huidige map.</span><span class="sxs-lookup"><span data-stu-id="5f79a-146">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f79a-147">-TypeData</span><span class="sxs-lookup"><span data-stu-id="5f79a-147">-TypeData</span></span>

<span data-ttu-id="5f79a-148">Hiermee geeft u de type gegevens op die met deze cmdlet uit de sessie worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f79a-148">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="5f79a-149">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="5f79a-149">This parameter is required.</span></span> <span data-ttu-id="5f79a-150">Voer een variabele in die **TypeData** -objecten (**System. Management. Automation. Runspaces. TypeData**) bevat of een opdracht waarmee **TypeData** -objecten, zoals een opdracht, worden opgehaald `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5f79a-150">Enter a variable that contains **TypeData** objects (**System.Management.Automation.Runspaces.TypeData**) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="5f79a-151">U kunt ook **TypeData** -objecten pipeen naar `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5f79a-151">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5f79a-152">-TypeName</span><span class="sxs-lookup"><span data-stu-id="5f79a-152">-TypeName</span></span>

<span data-ttu-id="5f79a-153">Hiermee geeft u de typen op waarvoor met deze cmdlet alle uitgebreide type gegevens worden verwijderd voor.</span><span class="sxs-lookup"><span data-stu-id="5f79a-153">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="5f79a-154">Voor typen in de naam ruimte van het systeem voert u de korte naam in.</span><span class="sxs-lookup"><span data-stu-id="5f79a-154">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="5f79a-155">Anders is de volledige type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="5f79a-155">Otherwise, the full type name is required.</span></span> <span data-ttu-id="5f79a-156">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f79a-156">Wildcards are not supported.</span></span>

<span data-ttu-id="5f79a-157">U kunt typen van het type sluizen naar `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5f79a-157">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="5f79a-158">Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de type naam van het object op en verwijdert alle type gegevens voor het object type.</span><span class="sxs-lookup"><span data-stu-id="5f79a-158">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5f79a-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5f79a-159">-Confirm</span></span>

<span data-ttu-id="5f79a-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f79a-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5f79a-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5f79a-161">-WhatIf</span></span>

<span data-ttu-id="5f79a-162">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f79a-162">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5f79a-163">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f79a-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5f79a-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f79a-164">CommonParameters</span></span>

<span data-ttu-id="5f79a-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f79a-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f79a-166">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f79a-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f79a-167">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="5f79a-167">Inputs</span></span>

### <span data-ttu-id="5f79a-168">System. Management. Automation. Runspaces. TypeData</span><span class="sxs-lookup"><span data-stu-id="5f79a-168">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="5f79a-169">U kunt het **TypeData** -object, zoals de items die `Get-TypeData` door de cmdlet worden geretourneerd, aan `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5f79a-169">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="5f79a-170">System. String</span><span class="sxs-lookup"><span data-stu-id="5f79a-170">System.String</span></span>

<span data-ttu-id="5f79a-171">U kunt de type namen door sluizen naar `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="5f79a-171">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="5f79a-172">Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de type naam van het object op en verwijdert alle type gegevens voor het object type.</span><span class="sxs-lookup"><span data-stu-id="5f79a-172">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="5f79a-173">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="5f79a-173">Outputs</span></span>

### <span data-ttu-id="5f79a-174">Geen</span><span class="sxs-lookup"><span data-stu-id="5f79a-174">None</span></span>

<span data-ttu-id="5f79a-175">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5f79a-175">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5f79a-176">Notities</span><span class="sxs-lookup"><span data-stu-id="5f79a-176">Notes</span></span>

<span data-ttu-id="5f79a-177">`Remove-TypeData` kan alleen de uitgebreide-type gegevens in de huidige sessie verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5f79a-177">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="5f79a-178">Het is niet mogelijk om uitgebreide type gegevens op de computer te verwijderen, maar is niet toegevoegd aan de huidige sessie, zoals uitgebreide typen die zijn gedefinieerd in modules die niet in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="5f79a-178">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="5f79a-179">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="5f79a-179">Related links</span></span>

[<span data-ttu-id="5f79a-180">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="5f79a-180">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="5f79a-181">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="5f79a-181">Update-TypeData</span></span>](Update-TypeData.md)

