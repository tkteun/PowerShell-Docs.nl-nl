---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 23a5241aa2f4b18fc02c3ea1c1a5bb8fb467b430
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251011"
---
# <span data-ttu-id="818a8-103">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="818a8-103">Remove-TypeData</span></span>

## <span data-ttu-id="818a8-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="818a8-104">Synopsis</span></span>
<span data-ttu-id="818a8-105">Hiermee verwijdert u uitgebreide typen van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-105">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="818a8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="818a8-106">Syntax</span></span>

### <span data-ttu-id="818a8-107">RemoveTypeDataSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="818a8-107">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="818a8-108">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="818a8-108">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="818a8-109">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="818a8-109">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="818a8-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="818a8-110">DESCRIPTION</span></span>

<span data-ttu-id="818a8-111">`Remove-TypeData`Met de cmdlet worden uitgebreide type gegevens uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="818a8-111">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="818a8-112">Deze cmdlet is alleen van invloed op de huidige sessie en sessies die zijn gemaakt in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-112">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="818a8-113">U kunt eigenschappen en methoden toevoegen aan objecten in Power shell door ze te definiëren in `Update-TypeData` opdrachten en `Types.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="818a8-113">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="818a8-114">`Remove-TypeData` Hiermee verwijdert u de uitgebreide eigenschappen en methoden van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-114">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="818a8-115">`Remove-TypeData` verwijdert de bestanden niet `Types.ps1xml` of verwijdert uitgebreide type definities van de `Types.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="818a8-115">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="818a8-116">`Types.ps1xml`Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)voor meer informatie over bestanden.</span><span class="sxs-lookup"><span data-stu-id="818a8-116">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="818a8-117">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="818a8-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="818a8-118">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="818a8-118">Examples</span></span>

### <span data-ttu-id="818a8-119">Voor beeld 1: type gegevens verwijderen voor een opgegeven type</span><span class="sxs-lookup"><span data-stu-id="818a8-119">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="818a8-120">In dit voor beeld worden alle type gegevens voor het type **System. matrix** verwijderd uit de sessie, inclusief type gegevens die zijn toegevoegd door een `Types.ps1xml` bestand en dynamische type gegevens die zijn toegevoegd aan de-sessie met behulp van de- `Update-TypeData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="818a8-120">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="818a8-121">Voor beeld 2: een uitgebreide-gegevens type uit een sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="818a8-121">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="818a8-122">Dit voor beeld toont het effect van het verwijderen van uitgebreide type gegevens uit een sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-122">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="818a8-123">Met de eerste worden `Get-TypeData` uitgebreide type gegevens voor het type **System. datetime** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="818a8-123">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="818a8-124">In de uitvoer ziet u dat een **datum/tijd** -eigenschap is toegevoegd aan alle **System. datetime** -objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="818a8-124">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="818a8-125">De `Get-Date` cmdlet retourneert een **System. datetime** -object.</span><span class="sxs-lookup"><span data-stu-id="818a8-125">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="818a8-126">De opdracht gebruikt punt notatie om de waarde van de eigenschap **DateTime** van het object **System. datetime** op te halen dat `Get-Date` retourneert.</span><span class="sxs-lookup"><span data-stu-id="818a8-126">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

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

<span data-ttu-id="818a8-127">De volgende `Get-TypeData` cmdlet voor het ophalen van alle uitgebreide type gegevens voor het type **System. datetime** en pijpen die de cmdlet voor het `Remove-TypeData` verwijderen van de gegevens van het uitgebreide type hebben.</span><span class="sxs-lookup"><span data-stu-id="818a8-127">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="818a8-128">De laatste `Get-Date` cmdlet toont het effect van het verwijderen van de uitgebreide type gegevens voor het type **System. datetime** .</span><span class="sxs-lookup"><span data-stu-id="818a8-128">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="818a8-129">Omdat de eigenschap **System. datetime** niet meer bestaat, retourneert een opdracht om de waarde ervan op te halen niets.</span><span class="sxs-lookup"><span data-stu-id="818a8-129">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="818a8-130">Voor beeld 3: uitgebreide typen voor modules verwijderen</span><span class="sxs-lookup"><span data-stu-id="818a8-130">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="818a8-131">In dit voor beeld worden alle uitgebreide type gegevens voor module objecten verwijderd.</span><span class="sxs-lookup"><span data-stu-id="818a8-131">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="818a8-132">Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de naam van het object type op en verwijdert alle type gegevens voor alle objecten van dat type.</span><span class="sxs-lookup"><span data-stu-id="818a8-132">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="818a8-133">Voor beeld 4: uitgebreide typen verwijderen uit opgegeven modules</span><span class="sxs-lookup"><span data-stu-id="818a8-133">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="818a8-134">In dit voor beeld wordt de para meter **Path** van de `Remove-TypeData` cmdlet gebruikt voor het verwijderen van de uitgebreide typen die zijn gedefinieerd in de `Types.ps1xml` bestanden die worden toegevoegd door de **PSScheduledJob** -en **PSWorkflow** -modules.</span><span class="sxs-lookup"><span data-stu-id="818a8-134">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="818a8-135">Deze opdracht is niet van invloed op dynamische type gegevens die worden toegevoegd met behulp van de- `Update-TypeData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="818a8-135">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="818a8-136">De opdracht wordt alleen uitgevoerd als de modules zijn geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-136">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="818a8-137">Zie [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="818a8-137">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="818a8-138">Voor beeld 5: uitgebreide typen verwijderen uit een externe sessie</span><span class="sxs-lookup"><span data-stu-id="818a8-138">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="818a8-139">In dit voor beeld worden uitgebreide typen verwijderd uit een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-139">This example removes extended types from a remote session.</span></span> <span data-ttu-id="818a8-140">De opdracht gebruikt de `Invoke-Command` cmdlet voor het verwijderen van uitgebreide type gegevens voor alle CIM-typen in de sessies in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="818a8-140">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="818a8-141">Parameters</span><span class="sxs-lookup"><span data-stu-id="818a8-141">Parameters</span></span>

### <span data-ttu-id="818a8-142">-Path</span><span class="sxs-lookup"><span data-stu-id="818a8-142">-Path</span></span>

<span data-ttu-id="818a8-143">Hiermee geeft u een matrix met bestanden op die met deze cmdlet worden verwijderd uit de uitgebreide type gegevens van de sessie.</span><span class="sxs-lookup"><span data-stu-id="818a8-143">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="818a8-144">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="818a8-144">This parameter is required.</span></span>

<span data-ttu-id="818a8-145">Voer de paden en bestands namen van een of meer `Types.ps1xml` bestanden in.</span><span class="sxs-lookup"><span data-stu-id="818a8-145">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="818a8-146">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="818a8-146">Wildcards are not supported.</span></span> <span data-ttu-id="818a8-147">Als u het pad weglaat, is de standaard locatie de huidige map.</span><span class="sxs-lookup"><span data-stu-id="818a8-147">If you omit the path, the default location is the current directory.</span></span>

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

### <span data-ttu-id="818a8-148">-TypeData</span><span class="sxs-lookup"><span data-stu-id="818a8-148">-TypeData</span></span>

<span data-ttu-id="818a8-149">Hiermee geeft u de type gegevens op die met deze cmdlet uit de sessie worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="818a8-149">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="818a8-150">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="818a8-150">This parameter is required.</span></span> <span data-ttu-id="818a8-151">Voer een variabele in die **TypeData** -objecten ( **System. Management. Automation. Runspaces. TypeData** ) bevat of een opdracht waarmee **TypeData** -objecten, zoals een opdracht, worden opgehaald `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="818a8-151">Enter a variable that contains **TypeData** objects ( **System.Management.Automation.Runspaces.TypeData** ) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="818a8-152">U kunt ook **TypeData** -objecten pipeen naar `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="818a8-152">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

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

### <span data-ttu-id="818a8-153">-TypeName</span><span class="sxs-lookup"><span data-stu-id="818a8-153">-TypeName</span></span>

<span data-ttu-id="818a8-154">Hiermee geeft u de typen op waarvoor met deze cmdlet alle uitgebreide type gegevens worden verwijderd voor.</span><span class="sxs-lookup"><span data-stu-id="818a8-154">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="818a8-155">Voor typen in de naam ruimte van het systeem voert u de korte naam in.</span><span class="sxs-lookup"><span data-stu-id="818a8-155">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="818a8-156">Anders is de volledige type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="818a8-156">Otherwise, the full type name is required.</span></span> <span data-ttu-id="818a8-157">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="818a8-157">Wildcards are not supported.</span></span>

<span data-ttu-id="818a8-158">U kunt typen van het type sluizen naar `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="818a8-158">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="818a8-159">Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de type naam van het object op en verwijdert alle type gegevens voor het object type.</span><span class="sxs-lookup"><span data-stu-id="818a8-159">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

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

### <span data-ttu-id="818a8-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="818a8-160">-Confirm</span></span>

<span data-ttu-id="818a8-161">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="818a8-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="818a8-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="818a8-162">-WhatIf</span></span>

<span data-ttu-id="818a8-163">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="818a8-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="818a8-164">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="818a8-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="818a8-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="818a8-165">CommonParameters</span></span>

<span data-ttu-id="818a8-166">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="818a8-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="818a8-167">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="818a8-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="818a8-168">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="818a8-168">Inputs</span></span>

### <span data-ttu-id="818a8-169">System. Management. Automation. Runspaces. TypeData</span><span class="sxs-lookup"><span data-stu-id="818a8-169">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="818a8-170">U kunt het **TypeData** -object, zoals de items die `Get-TypeData` door de cmdlet worden geretourneerd, aan `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="818a8-170">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="818a8-171">System. String</span><span class="sxs-lookup"><span data-stu-id="818a8-171">System.String</span></span>

<span data-ttu-id="818a8-172">U kunt de type namen door sluizen naar `Remove-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="818a8-172">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="818a8-173">Wanneer u een object pipet op `Remove-TypeData` , `Remove-TypeData` haalt de type naam van het object op en verwijdert alle type gegevens voor het object type.</span><span class="sxs-lookup"><span data-stu-id="818a8-173">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="818a8-174">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="818a8-174">Outputs</span></span>

### <span data-ttu-id="818a8-175">Geen</span><span class="sxs-lookup"><span data-stu-id="818a8-175">None</span></span>

<span data-ttu-id="818a8-176">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="818a8-176">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="818a8-177">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="818a8-177">Notes</span></span>

<span data-ttu-id="818a8-178">`Remove-TypeData` kan alleen de uitgebreide-type gegevens in de huidige sessie verwijderen.</span><span class="sxs-lookup"><span data-stu-id="818a8-178">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="818a8-179">Het is niet mogelijk om uitgebreide type gegevens op de computer te verwijderen, maar is niet toegevoegd aan de huidige sessie, zoals uitgebreide typen die zijn gedefinieerd in modules die niet in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="818a8-179">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="818a8-180">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="818a8-180">Related links</span></span>

[<span data-ttu-id="818a8-181">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="818a8-181">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="818a8-182">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="818a8-182">Update-TypeData</span></span>](Update-TypeData.md)
