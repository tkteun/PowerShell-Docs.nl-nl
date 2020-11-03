---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: afc68ed45313a8bcfad2e1045e5b744424126bf2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250953"
---
# <span data-ttu-id="bf993-103">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="bf993-103">Update-TypeData</span></span>

## <span data-ttu-id="bf993-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="bf993-104">Synopsis</span></span>
<span data-ttu-id="bf993-105">Hiermee werkt u de uitgebreide type gegevens in de sessie bij.</span><span class="sxs-lookup"><span data-stu-id="bf993-105">Updates the extended type data in the session.</span></span>

## <span data-ttu-id="bf993-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf993-106">Syntax</span></span>

### <span data-ttu-id="bf993-107">Bestandsset (standaard)</span><span class="sxs-lookup"><span data-stu-id="bf993-107">FileSet (Default)</span></span>

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bf993-108">DynamicTypeSet</span><span class="sxs-lookup"><span data-stu-id="bf993-108">DynamicTypeSet</span></span>

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bf993-109">TypeDataSet</span><span class="sxs-lookup"><span data-stu-id="bf993-109">TypeDataSet</span></span>

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bf993-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf993-110">Description</span></span>

<span data-ttu-id="bf993-111">`Update-TypeData`Met de cmdlet worden de uitgebreide type gegevens in de sessie bijgewerkt door de `Types.ps1xml` bestanden opnieuw in het geheugen te laden en nieuwe uitgebreide-type gegevens toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="bf993-111">The `Update-TypeData` cmdlet updates the extended type data in the session by reloading the `Types.ps1xml` files into memory and adding new extended type data.</span></span>

<span data-ttu-id="bf993-112">Power shell laadt standaard uitgebreide type gegevens als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="bf993-112">By default, PowerShell loads extended type data as it is needed.</span></span> <span data-ttu-id="bf993-113">Zonder para meters worden `Update-TypeData` alle `Types.ps1xml` bestanden die in de sessie zijn geladen, opnieuw geladen, inclusief alle typen bestanden die u hebt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bf993-113">Without parameters, `Update-TypeData` reloads all of the `Types.ps1xml` files that it has loaded in the session, including any type files that you added.</span></span> <span data-ttu-id="bf993-114">U kunt de para meters van gebruiken `Update-TypeData` om nieuwe type bestanden toe te voegen en uitgebreide type gegevens toe te voegen en te vervangen.</span><span class="sxs-lookup"><span data-stu-id="bf993-114">You can use the parameters of `Update-TypeData` to add new type files and add and replace extended type data.</span></span>

<span data-ttu-id="bf993-115">De `Update-TypeData` cmdlet kan worden gebruikt om alle type gegevens vooraf te laden.</span><span class="sxs-lookup"><span data-stu-id="bf993-115">The `Update-TypeData` cmdlet can be used to preload all type data.</span></span> <span data-ttu-id="bf993-116">Deze functie is vooral nuttig wanneer u typen ontwikkelt en deze nieuwe typen wilt laden voor test doeleinden.</span><span class="sxs-lookup"><span data-stu-id="bf993-116">This feature is particularly useful when you are developing types and want to load those new types for testing purposes.</span></span>

<span data-ttu-id="bf993-117">Vanaf Windows Power Shell 3,0 kunt u gebruiken `Update-TypeData` om uitgebreide type gegevens in de sessie toe te voegen en te vervangen zonder een bestand te gebruiken `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="bf993-117">Beginning in Windows PowerShell 3.0, you can use `Update-TypeData` to add and replace extended type data in the session without using a `Types.ps1xml` file.</span></span> <span data-ttu-id="bf993-118">Type gegevens die dynamisch worden toegevoegd, dat wil zeggen, zonder een bestand, wordt alleen toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bf993-118">Type data that is added dynamically, that is, without a file, is added only to the current session.</span></span> <span data-ttu-id="bf993-119">Als u de type gegevens wilt toevoegen aan alle sessies, voegt u een `Update-TypeData` opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="bf993-119">To add the type data to all sessions, add an `Update-TypeData` command to your PowerShell profile.</span></span> <span data-ttu-id="bf993-120">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf993-120">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="bf993-121">Met ingang van Windows Power Shell 3,0 kunt u ook de- `Get-TypeData` cmdlet gebruiken om de uitgebreide typen in de huidige sessie en de `Remove-TypeData` cmdlet te verkrijgen voor het verwijderen van uitgebreide typen uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bf993-121">Also, beginning in Windows PowerShell 3.0, you can use the `Get-TypeData` cmdlet to get the extended types in the current session and the `Remove-TypeData` cmdlet to delete extended types from the current session.</span></span>

<span data-ttu-id="bf993-122">Uitzonde ringen die optreden in eigenschappen of van het toevoegen van eigenschappen aan een `Update-TypeData` opdracht, rapporteren geen fouten.</span><span class="sxs-lookup"><span data-stu-id="bf993-122">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors.</span></span> <span data-ttu-id="bf993-123">Dit is om uitzonde ringen te onderdrukken die tijdens het format teren en uitvoeren in veel voorkomende typen zouden optreden.</span><span class="sxs-lookup"><span data-stu-id="bf993-123">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="bf993-124">Als u .NET-eigenschappen krijgt, kunt u de onderdrukking van uitzonde ringen omzeilen door in plaats daarvan de syntaxis van de methode te gebruiken, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="bf993-124">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

`"hello".get_Length()`

<span data-ttu-id="bf993-125">Houd er rekening mee dat syntaxis van een methode alleen kan worden gebruikt met .NET-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="bf993-125">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="bf993-126">Eigenschappen die worden toegevoegd door de cmdlet uit te voeren `Update-TypeData` , kunnen de syntaxis van de methode niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf993-126">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

<span data-ttu-id="bf993-127">Zieabout_Types.ps1XML voor meer informatie over de `Types.ps1xml` bestanden in [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)Power shell.</span><span class="sxs-lookup"><span data-stu-id="bf993-127">For more information about the `Types.ps1xml` files in PowerShell, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

## <span data-ttu-id="bf993-128">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="bf993-128">Examples</span></span>

### <span data-ttu-id="bf993-129">Voor beeld 1: uitgebreide typen bijwerken</span><span class="sxs-lookup"><span data-stu-id="bf993-129">Example 1: Update extended types</span></span>

```powershell
Update-TypeData
```

<span data-ttu-id="bf993-130">Met deze opdracht wordt de uitgebreide type configuratie bijgewerkt op basis van de `Types.ps1xml` bestanden die al in de sessie zijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf993-130">This command updates the extended type configuration from the `Types.ps1xml` files that have already been used in the session.</span></span>

### <span data-ttu-id="bf993-131">Voor beeld 2: typen meerdere keren bijwerken</span><span class="sxs-lookup"><span data-stu-id="bf993-131">Example 2: Update types multiple times</span></span>

<span data-ttu-id="bf993-132">In dit voor beeld ziet u hoe u de typen in een type bestand meerdere keren in dezelfde sessie bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="bf993-132">This example shows how to update the types in a type file multiple times in the same session.</span></span>

<span data-ttu-id="bf993-133">Met de eerste opdracht wordt de uitgebreide type configuratie van de bestanden bijgewerkt en `Types.ps1xml` worden de `TypesA.types.ps1xml` en `TypesB.types.ps1xml` bestanden eerst verwerkt.</span><span class="sxs-lookup"><span data-stu-id="bf993-133">The first command updates the extended type configuration from the `Types.ps1xml` files, processing the `TypesA.types.ps1xml` and `TypesB.types.ps1xml` files first.</span></span>

<span data-ttu-id="bf993-134">De tweede opdracht laat zien hoe u de update `TypesA.types.ps1xml` opnieuw uitvoert, zoals u kunt doen als u een type in het bestand hebt toegevoegd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bf993-134">The second command shows how to update the `TypesA.types.ps1xml` again, such as you might do if you added or changed a type in the file.</span></span> <span data-ttu-id="bf993-135">U kunt de vorige opdracht voor het bestand herhalen `TypesA.types.ps1xml` of een `Update-TypeData` opdracht zonder para meters uitvoeren, omdat `TypesA.types.ps1xml` deze al in de lijst met type bestanden voor de huidige sessie staat.</span><span class="sxs-lookup"><span data-stu-id="bf993-135">You can either repeat the previous command for the `TypesA.types.ps1xml` file, or run an `Update-TypeData` command without parameters, because `TypesA.types.ps1xml` is already in the type file list for the current session.</span></span>

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### <span data-ttu-id="bf993-136">Voor beeld 3: een script eigenschap toevoegen aan DateTime-objecten</span><span class="sxs-lookup"><span data-stu-id="bf993-136">Example 3: Add a script property to DateTime objects</span></span>

<span data-ttu-id="bf993-137">In dit voor beeld wordt gebruikt `Update-TypeData` om de eigenschap **kwar taal** toe te voegen aan **System. datetime** -objecten in de huidige sessie, zoals die worden geretourneerd door de `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf993-137">This example uses `Update-TypeData` to add the **Quarter** script property to **System.DateTime** objects in the current session, such as those returned by the `Get-Date` cmdlet.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

<span data-ttu-id="bf993-138">De `Update-TypeData` opdracht gebruikt de **TypeName** para meter om **het type System. datetime** op te geven, de para meter **lidnaam** om een naam op te geven voor de nieuwe eigenschap, de eigenschap **member type** om het type **ScriptProperty** op te geven, en de **waarde** para meter om het script op te geven dat het jaarlijkse kwar taal bepaalt.</span><span class="sxs-lookup"><span data-stu-id="bf993-138">The `Update-TypeData` command uses the **TypeName** parameter to specify **the System.DateTime** type, the **MemberName** parameter to specify a name for the new property, the **MemberType** property to specify the **ScriptProperty** type, and the **Value** parameter to specify the script that determines the annual quarter.</span></span>

<span data-ttu-id="bf993-139">De waarde van de eigenschap **Value** is een script waarmee het huidige jaar kwar taal wordt berekend.</span><span class="sxs-lookup"><span data-stu-id="bf993-139">The value of the **Value** property is a script that calculates the current annual quarter.</span></span> <span data-ttu-id="bf993-140">Het script blok gebruikt de `$this` Automatische variabele voor het huidige exemplaar van het object en de in-operator om te bepalen of de waarde van de maand wordt weer gegeven in elke matrix met gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="bf993-140">The script block uses the `$this` automatic variable to represent the current instance of the object and the In operator to determine whether the month value appears in each integer array.</span></span> <span data-ttu-id="bf993-141">Zie about_Comparison_Operators voor meer informatie over de `-in` - [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)operator.</span><span class="sxs-lookup"><span data-stu-id="bf993-141">For more information about the `-in` operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span></span>

<span data-ttu-id="bf993-142">Met de tweede opdracht wordt de nieuwe eigenschap Quarter van de huidige datum opgehaald.</span><span class="sxs-lookup"><span data-stu-id="bf993-142">The second command gets the new Quarter property of the current date.</span></span>

### <span data-ttu-id="bf993-143">Voor beeld 4: een type bijwerken dat standaard in lijsten wordt weer gegeven</span><span class="sxs-lookup"><span data-stu-id="bf993-143">Example 4: Update a type that displays in lists by default</span></span>

<span data-ttu-id="bf993-144">In dit voor beeld ziet u hoe u de eigenschappen van een type kunt instellen dat standaard wordt weer gegeven in lijsten, dat wil zeggen, wanneer er geen eigenschappen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf993-144">This example shows how to set the properties of a type that displays in lists by default, that is, when no properties are specified.</span></span> <span data-ttu-id="bf993-145">Omdat de type gegevens niet in een bestand zijn opgegeven `Types.ps1xml` , is deze alleen geldig in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bf993-145">Because the type data is not specified in a `Types.ps1xml` file, it is effective only in the current session.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

<span data-ttu-id="bf993-146">Met de eerste opdracht wordt de `Update-TypeData` cmdlet gebruikt om de standaard lijst eigenschappen voor het type **System. datetime** in te stellen.</span><span class="sxs-lookup"><span data-stu-id="bf993-146">The first command uses the `Update-TypeData` cmdlet to set the default list properties for the **System.DateTime** type.</span></span> <span data-ttu-id="bf993-147">De opdracht gebruikt de **TypeName** para meter om het type en de para meter **DefaultDisplayPropertySet** op te geven om de standaard eigenschappen voor een lijst op te geven.</span><span class="sxs-lookup"><span data-stu-id="bf993-147">The command uses the **TypeName** parameter to specify the type and the **DefaultDisplayPropertySet** parameter to specify the default properties for a list.</span></span> <span data-ttu-id="bf993-148">De geselecteerde eigenschappen zijn onder andere de nieuwe **kwartaal** eigenschap die in een vorig voor beeld is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bf993-148">The selected properties include the new **Quarter** script property that was added in a previous example.</span></span>

<span data-ttu-id="bf993-149">De tweede opdracht gebruikt de `Get-Date` cmdlet om een **System. datetime** -object op te halen dat de huidige datum voor stelt.</span><span class="sxs-lookup"><span data-stu-id="bf993-149">The second command uses the `Get-Date` cmdlet to get a **System.DateTime** object that represents the current date.</span></span> <span data-ttu-id="bf993-150">De opdracht maakt gebruik van een pijplijn operator ( `|` ) om het **DateTime** -object naar de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="bf993-150">The command uses a pipeline operator (`|`) to send the **DateTime** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="bf993-151">Omdat met de `Format-List` opdracht niet de eigenschappen worden opgegeven die in de lijst worden weer gegeven, gebruikt Power shell de standaard waarden die door de opdracht zijn ingesteld `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="bf993-151">Because the `Format-List` command does not specify the properties to display in the list, PowerShell uses the default values that were established by the `Update-TypeData` command.</span></span>

### <span data-ttu-id="bf993-152">Voor beeld 5: type gegevens bijwerken voor een object met pijp lijn</span><span class="sxs-lookup"><span data-stu-id="bf993-152">Example 5: Update type data for a piped object</span></span>

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

<span data-ttu-id="bf993-153">In dit voor beeld wordt gedemonstreerd dat wanneer u een object pipet op `Update-TypeData` , `Update-TypeData` uitgebreide type gegevens toevoegt voor het object type.</span><span class="sxs-lookup"><span data-stu-id="bf993-153">This example demonstrates that when you pipe an object to `Update-TypeData`, `Update-TypeData` adds extended type data for the object type.</span></span>

<span data-ttu-id="bf993-154">Deze techniek is sneller dan het gebruik van de `Get-Member` cmdlet of de `Get-Type` methode om het object type op te halen.</span><span class="sxs-lookup"><span data-stu-id="bf993-154">This technique is quicker than using the `Get-Member` cmdlet or the `Get-Type` method to get the object type.</span></span> <span data-ttu-id="bf993-155">Als u echter een verzameling objecten naar een pipet `Update-TypeData` stuurt, worden de type gegevens van het eerste object type bijgewerkt en wordt er een fout geretourneerd voor alle andere objecten in de verzameling, omdat het lid al is gedefinieerd voor het type.</span><span class="sxs-lookup"><span data-stu-id="bf993-155">However, if you pipe a collection of objects to `Update-TypeData`, it updates the type data of the first object type and then returns an error for all other objects in the collection because the member is already defined on the type.</span></span>

<span data-ttu-id="bf993-156">De eerste opdracht gebruikt de `Get-Module` cmdlet om de PSScheduledJob-module op te halen.</span><span class="sxs-lookup"><span data-stu-id="bf993-156">The first command uses the `Get-Module` cmdlet to get the PSScheduledJob module.</span></span> <span data-ttu-id="bf993-157">De opdracht sluizen het module object naar de `Update-TypeData` cmdlet, waarmee de type gegevens voor het type **System. Management. Automation. PSModuleInfo** en de typen die hiervan zijn afgeleid, worden bijgewerkt, zoals het ModuleInfoGrouping-type dat `Get-Module` wordt geretourneerd wanneer u de **ListAvailable** -para meter in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf993-157">The command pipes the module object to the `Update-TypeData` cmdlet, which updates the type data for the **System.Management.Automation.PSModuleInfo** type and the types derived from it, such as the ModuleInfoGrouping type that `Get-Module` returns when you use the **ListAvailable** parameter in the command.</span></span>

<span data-ttu-id="bf993-158">`Update-TypeData`Met de opdrachten wordt de script eigenschap **SupportsUpdatableHelp** toegevoegd aan alle geïmporteerde modules.</span><span class="sxs-lookup"><span data-stu-id="bf993-158">The `Update-TypeData` commands adds the **SupportsUpdatableHelp** script property to all imported modules.</span></span> <span data-ttu-id="bf993-159">De waarde van de **waarde** -para meter is een script dat retourneert `$True` als de eigenschap **HelpInfoUri** van de module is gevuld en `$False` anders.</span><span class="sxs-lookup"><span data-stu-id="bf993-159">The value of the **Value** parameter is a script that returns `$True` if the **HelpInfoUri** property of the module is populated and `$False` otherwise.</span></span>

<span data-ttu-id="bf993-160">Met de tweede opdracht worden de module objecten sluizen van `Get-Module` naar de `Format-Table` cmdlet, die de **naam** en **SupportsUpdatableHelp** -eigenschappen van alle modules in een lijst weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bf993-160">The second command pipes the module objects from `Get-Module` to the `Format-Table` cmdlet, which displays the **Name** and **SupportsUpdatableHelp** properties of all modules in a list.</span></span>

## <span data-ttu-id="bf993-161">Parameters</span><span class="sxs-lookup"><span data-stu-id="bf993-161">Parameters</span></span>

### <span data-ttu-id="bf993-162">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="bf993-162">-AppendPath</span></span>

<span data-ttu-id="bf993-163">Hiermee geeft u het pad naar optionele `.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="bf993-163">Specifies the path to optional `.ps1xml` files.</span></span> <span data-ttu-id="bf993-164">De opgegeven bestanden worden geladen in de volg orde waarin ze worden weer gegeven nadat de ingebouwde bestanden zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="bf993-164">The specified files are loaded in the order that they are listed after the built-in files are loaded.</span></span> <span data-ttu-id="bf993-165">U kunt ook een **AppendPath** -waarde naar `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="bf993-165">You can also pipe an **AppendPath** value to `Update-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-166">-DefaultDisplayProperty</span><span class="sxs-lookup"><span data-stu-id="bf993-166">-DefaultDisplayProperty</span></span>

<span data-ttu-id="bf993-167">Hiermee geeft u de eigenschap op van het type dat door de cmdlet wordt weer gegeven `Format-Wide` wanneer er geen andere eigenschappen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf993-167">Specifies the property of the type that is displayed by the `Format-Wide` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="bf993-168">Typ de naam van een standaard-of uitgebreide eigenschap van het type.</span><span class="sxs-lookup"><span data-stu-id="bf993-168">Type the name of a standard or extended property of the type.</span></span> <span data-ttu-id="bf993-169">De waarde van deze para meter kan de naam van een type zijn dat in dezelfde opdracht wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bf993-169">The value of this parameter can be the name of a type that is added in the same command.</span></span>

<span data-ttu-id="bf993-170">Deze waarde is alleen effectief wanneer er geen brede weer gaven zijn gedefinieerd voor het type in een `Format.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="bf993-170">This value is effective only when there are no wide views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="bf993-171">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-171">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-172">-DefaultDisplayPropertySet</span><span class="sxs-lookup"><span data-stu-id="bf993-172">-DefaultDisplayPropertySet</span></span>

<span data-ttu-id="bf993-173">Hiermee geeft u een of meer eigenschappen van het type op.</span><span class="sxs-lookup"><span data-stu-id="bf993-173">Specifies one or more properties of the type.</span></span> <span data-ttu-id="bf993-174">Deze eigenschappen worden weer gegeven door de `Format-List` cmdlet wanneer er geen andere eigenschappen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf993-174">These properties are displayed by the `Format-List` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="bf993-175">Typ de namen van de standaard-of uitgebreide eigenschappen van het type.</span><span class="sxs-lookup"><span data-stu-id="bf993-175">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="bf993-176">De waarde van deze para meter kan de namen zijn van typen die in dezelfde opdracht worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bf993-176">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="bf993-177">Deze waarde is alleen effectief als er geen lijst Weergaven zijn gedefinieerd voor het type in een `Format.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="bf993-177">This value is effective only when there are no list views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="bf993-178">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-179">-DefaultKeyPropertySet</span><span class="sxs-lookup"><span data-stu-id="bf993-179">-DefaultKeyPropertySet</span></span>

<span data-ttu-id="bf993-180">Hiermee geeft u een of meer eigenschappen van het type op.</span><span class="sxs-lookup"><span data-stu-id="bf993-180">Specifies one or more properties of the type.</span></span> <span data-ttu-id="bf993-181">Deze eigenschappen worden gebruikt door de `Group-Object` `Sort-Object` cmdlets en wanneer er geen andere eigenschappen zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf993-181">These properties are used by the `Group-Object` and `Sort-Object` cmdlets when no other properties are specified.</span></span>

<span data-ttu-id="bf993-182">Typ de namen van de standaard-of uitgebreide eigenschappen van het type.</span><span class="sxs-lookup"><span data-stu-id="bf993-182">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="bf993-183">De waarde van deze para meter kan de namen zijn van typen die in dezelfde opdracht worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bf993-183">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="bf993-184">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-184">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-185">-Force</span><span class="sxs-lookup"><span data-stu-id="bf993-185">-Force</span></span>

<span data-ttu-id="bf993-186">Geeft aan dat de cmdlet de opgegeven type gegevens gebruikt, zelfs als er al een type gegevens voor dat type zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf993-186">Indicates that the cmdlet uses the specified type data, even if type data has already been specified for that type.</span></span>

<span data-ttu-id="bf993-187">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-187">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-188">-InheritPropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="bf993-188">-InheritPropertySerializationSet</span></span>

<span data-ttu-id="bf993-189">Hiermee wordt aangegeven of de set eigenschappen die worden geserialiseerd is overgenomen.</span><span class="sxs-lookup"><span data-stu-id="bf993-189">Indicates whether the set of properties that are serialized is inherited.</span></span> <span data-ttu-id="bf993-190">De standaardwaarde is `$Null`.</span><span class="sxs-lookup"><span data-stu-id="bf993-190">The default value is `$Null`.</span></span> <span data-ttu-id="bf993-191">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="bf993-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bf993-192">`$True`.</span><span class="sxs-lookup"><span data-stu-id="bf993-192">`$True`.</span></span> <span data-ttu-id="bf993-193">De eigenschappenset is overgenomen.</span><span class="sxs-lookup"><span data-stu-id="bf993-193">The property set is inherited.</span></span>
- <span data-ttu-id="bf993-194">`$False`.</span><span class="sxs-lookup"><span data-stu-id="bf993-194">`$False`.</span></span> <span data-ttu-id="bf993-195">De eigenschappenset is niet overgenomen.</span><span class="sxs-lookup"><span data-stu-id="bf993-195">The property set is not inherited.</span></span>
- <span data-ttu-id="bf993-196">`$Null`.</span><span class="sxs-lookup"><span data-stu-id="bf993-196">`$Null`.</span></span> <span data-ttu-id="bf993-197">Overname is niet gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-197">Inheritance is not defined.</span></span>

<span data-ttu-id="bf993-198">Deze para meter is alleen geldig wanneer de waarde van de para meter **methode serializationmethod** is `SpecificProperties` .</span><span class="sxs-lookup"><span data-stu-id="bf993-198">This parameter is valid only when the value of the **SerializationMethod** parameter is `SpecificProperties`.</span></span> <span data-ttu-id="bf993-199">Wanneer de waarde van deze para meter is `$False` , is de para meter **PropertySerializationSet** vereist.</span><span class="sxs-lookup"><span data-stu-id="bf993-199">When the value of this parameter is `$False`, the **PropertySerializationSet** parameter is required.</span></span>

<span data-ttu-id="bf993-200">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-201">-Lidnaam</span><span class="sxs-lookup"><span data-stu-id="bf993-201">-MemberName</span></span>

<span data-ttu-id="bf993-202">Hiermee geeft u de naam van een eigenschap of methode op.</span><span class="sxs-lookup"><span data-stu-id="bf993-202">Specifies the name of a property or method.</span></span>

<span data-ttu-id="bf993-203">Gebruik deze para meter met de para meters **TypeName** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf993-203">Use this parameter with the **TypeName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="bf993-204">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-205">-Member type</span><span class="sxs-lookup"><span data-stu-id="bf993-205">-MemberType</span></span>

<span data-ttu-id="bf993-206">Hiermee geeft u het type lid dat moet worden toegevoegd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bf993-206">Specifies the type of the member to add or change.</span></span>

<span data-ttu-id="bf993-207">Gebruik deze para meter met de para meters **TypeName** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf993-207">Use this parameter with the **TypeName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span> <span data-ttu-id="bf993-208">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="bf993-208">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bf993-209">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="bf993-209">AliasProperty</span></span>
- <span data-ttu-id="bf993-210">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="bf993-210">CodeMethod</span></span>
- <span data-ttu-id="bf993-211">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="bf993-211">CodeProperty</span></span>
- <span data-ttu-id="bf993-212">Noteproperty</span><span class="sxs-lookup"><span data-stu-id="bf993-212">Noteproperty</span></span>
- <span data-ttu-id="bf993-213">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="bf993-213">ScriptMethod</span></span>
- <span data-ttu-id="bf993-214">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="bf993-214">ScriptProperty</span></span>

<span data-ttu-id="bf993-215">Zie [PSMemberTypes Enumeration (Engelstalig)](/dotnet/api/system.management.automation.psmembertypes)voor meer informatie over deze waarden.</span><span class="sxs-lookup"><span data-stu-id="bf993-215">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes).</span></span>

<span data-ttu-id="bf993-216">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-217">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="bf993-217">-PrependPath</span></span>

<span data-ttu-id="bf993-218">Hiermee geeft u het pad naar de optionele `.ps1xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="bf993-218">Specifies the path to the optional `.ps1xml` files.</span></span> <span data-ttu-id="bf993-219">De opgegeven bestanden worden geladen in de volg orde waarin ze worden weer gegeven voordat de ingebouwde bestanden worden geladen.</span><span class="sxs-lookup"><span data-stu-id="bf993-219">The specified files are loaded in the order that they are listed before the built-in files are loaded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-220">-PropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="bf993-220">-PropertySerializationSet</span></span>

<span data-ttu-id="bf993-221">Hiermee geeft u de namen van eigenschappen die worden geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-221">Specifies the names of properties that are serialized.</span></span> <span data-ttu-id="bf993-222">Gebruik deze para meter wanneer de waarde van de para meter **methode serializationmethod** is **SpecificProperties**.</span><span class="sxs-lookup"><span data-stu-id="bf993-222">Use this parameter when the value of the **SerializationMethod** parameter is **SpecificProperties**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-223">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="bf993-223">-SecondValue</span></span>

<span data-ttu-id="bf993-224">Hiermee geeft u aanvullende waarden op voor **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -of **CodeMethod** -leden.</span><span class="sxs-lookup"><span data-stu-id="bf993-224">Specifies additional values for **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="bf993-225">Gebruik deze para meter met de para meters **TypeName** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf993-225">Use this parameter with the **TypeName** , **MemberType** , **Value** , and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="bf993-226">Wanneer de waarde van de para meter **member type** is `AliasProperty` , moet de waarde van de para meter **SecondValue** een gegevens type zijn.</span><span class="sxs-lookup"><span data-stu-id="bf993-226">When the value of the **MemberType** parameter is `AliasProperty`, the value of the **SecondValue** parameter must be a data type.</span></span> <span data-ttu-id="bf993-227">In Power shell wordt de waarde van de alias eigenschap geconverteerd naar het opgegeven type.</span><span class="sxs-lookup"><span data-stu-id="bf993-227">PowerShell converts (that is, casts) the value of the alias property to the specified type.</span></span> <span data-ttu-id="bf993-228">Als u bijvoorbeeld een alias eigenschap toevoegt die een alternatieve naam voor een teken reeks eigenschap levert, kunt u ook een **SecondValue** van **System. Int32** opgeven om de teken reeks waarde met alias te converteren naar een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="bf993-228">For example, if you add an alias property that provides an alternate name for a string property, you can also specify a **SecondValue** of **System.Int32** to convert the aliased string value to an integer.</span></span>

<span data-ttu-id="bf993-229">Wanneer de waarde van de para meter **member type** is `ScriptProperty` , kunt u de para meter **SecondValue** gebruiken om een extra script blok op te geven.</span><span class="sxs-lookup"><span data-stu-id="bf993-229">When the value of the **MemberType** parameter is `ScriptProperty`, you can use the **SecondValue** parameter to specify an additional script block.</span></span> <span data-ttu-id="bf993-230">Het script blok in de waarde van de para meter **Value** retourneert de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="bf993-230">The script block in the value of the **Value** parameter gets the value of a variable.</span></span> <span data-ttu-id="bf993-231">Het script blok in de waarde van de para meter **SecondValue** stelt de waarde van de variabele in.</span><span class="sxs-lookup"><span data-stu-id="bf993-231">The script block in the value of the **SecondValue** parameter set the value of the variable.</span></span>

<span data-ttu-id="bf993-232">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-233">-SerializationDepth</span><span class="sxs-lookup"><span data-stu-id="bf993-233">-SerializationDepth</span></span>

<span data-ttu-id="bf993-234">Hiermee geeft u op hoeveel niveaus van het type-objecten als teken reeksen worden geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-234">Specifies how many levels of type objects are serialized as strings.</span></span> <span data-ttu-id="bf993-235">Met de standaard waarde worden `1` het object en de bijbehorende eigenschappen geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-235">The default value `1` serializes the object and its properties.</span></span> <span data-ttu-id="bf993-236">Een waarde voor `0` het serialiseren van het object, maar niet de eigenschappen ervan.</span><span class="sxs-lookup"><span data-stu-id="bf993-236">A value of `0` serializes the object, but not its properties.</span></span> <span data-ttu-id="bf993-237">Een waarde voor `2` het serialiseren van het object, de eigenschappen ervan en alle objecten in eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="bf993-237">A value of `2` serializes the object, its properties, and any objects in property values.</span></span>

<span data-ttu-id="bf993-238">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-239">-Methode serializationmethod</span><span class="sxs-lookup"><span data-stu-id="bf993-239">-SerializationMethod</span></span>

<span data-ttu-id="bf993-240">Hiermee geeft u een serialisatie methode voor het type op.</span><span class="sxs-lookup"><span data-stu-id="bf993-240">Specifies a serialization method for the type.</span></span> <span data-ttu-id="bf993-241">Een serialisatie methode bepaalt welke eigenschappen van het type zijn geserialiseerd en de techniek die wordt gebruikt om ze te serialiseren.</span><span class="sxs-lookup"><span data-stu-id="bf993-241">A serialization method determines which properties of the type are serialized and the technique that is used to serialize them.</span></span> <span data-ttu-id="bf993-242">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="bf993-242">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bf993-243">`AllPublicProperties`.</span><span class="sxs-lookup"><span data-stu-id="bf993-243">`AllPublicProperties`.</span></span> <span data-ttu-id="bf993-244">Alle open bare eigenschappen van het type serialiseren.</span><span class="sxs-lookup"><span data-stu-id="bf993-244">Serialize all public properties of the type.</span></span> <span data-ttu-id="bf993-245">U kunt de para meter **SerializationDepth** gebruiken om te bepalen of onderliggende eigenschappen geserialiseerd zijn.</span><span class="sxs-lookup"><span data-stu-id="bf993-245">You can use the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>
- <span data-ttu-id="bf993-246">`String`.</span><span class="sxs-lookup"><span data-stu-id="bf993-246">`String`.</span></span> <span data-ttu-id="bf993-247">Serialiseren van het type als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="bf993-247">Serialize the type as a string.</span></span> <span data-ttu-id="bf993-248">U kunt de **StringSerializationSource** gebruiken om een eigenschap van het type op te geven dat moet worden gebruikt als het serialisatie resultaat.</span><span class="sxs-lookup"><span data-stu-id="bf993-248">You can use the **StringSerializationSource** to specify a property of the type to use as the serialization result.</span></span> <span data-ttu-id="bf993-249">Anders wordt het type geserialiseerd met de methode **toString** van het object.</span><span class="sxs-lookup"><span data-stu-id="bf993-249">Otherwise, the type is serialized by using the **ToString** method of the object.</span></span>
- <span data-ttu-id="bf993-250">`SpecificProperties`.</span><span class="sxs-lookup"><span data-stu-id="bf993-250">`SpecificProperties`.</span></span> <span data-ttu-id="bf993-251">Alleen de opgegeven eigenschappen van dit type serialiseren.</span><span class="sxs-lookup"><span data-stu-id="bf993-251">Serialize only the specified properties of this type.</span></span> <span data-ttu-id="bf993-252">Gebruik de para meter **PropertySerializationSet** om de eigenschappen op te geven van het type dat is geserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-252">Use the **PropertySerializationSet** parameter to specify the properties of the type that are serialized.</span></span>
  <span data-ttu-id="bf993-253">U kunt ook de para meter **InheritPropertySerializationSet** gebruiken om te bepalen of de eigenschappenset is overgenomen en de para meter **SerializationDepth** om te bepalen of onderliggende eigenschappen geserialiseerd zijn.</span><span class="sxs-lookup"><span data-stu-id="bf993-253">You can also use the **InheritPropertySerializationSet** parameter to determine whether the property set is inherited and the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>

<span data-ttu-id="bf993-254">In Power shell worden serialisatie methoden opgeslagen in **PSStandardMembers** interne objecten.</span><span class="sxs-lookup"><span data-stu-id="bf993-254">In PowerShell, serialization methods are stored in **PSStandardMembers** internal objects.</span></span>

<span data-ttu-id="bf993-255">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-256">-StringSerializationSource</span><span class="sxs-lookup"><span data-stu-id="bf993-256">-StringSerializationSource</span></span>

<span data-ttu-id="bf993-257">Hiermee geeft u de naam van een eigenschap van het type op.</span><span class="sxs-lookup"><span data-stu-id="bf993-257">Specifies the name of a property of the type.</span></span> <span data-ttu-id="bf993-258">De waarde van de opgegeven eigenschap wordt gebruikt als het serialisatie resultaat.</span><span class="sxs-lookup"><span data-stu-id="bf993-258">The value of specified property is used as the serialization result.</span></span> <span data-ttu-id="bf993-259">Deze para meter is alleen geldig wanneer de waarde van de para meter **methode serializationmethod** een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="bf993-259">This parameter is valid only when the value of the **SerializationMethod** parameter is String.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-260">-TargetTypeForDeserialization</span><span class="sxs-lookup"><span data-stu-id="bf993-260">-TargetTypeForDeserialization</span></span>

<span data-ttu-id="bf993-261">Hiermee geeft u het type op van welk object van dit type wordt geconverteerd wanneer deze worden gedeserialiseerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-261">Specifies the type to which object of this type are converted when they are deserialized.</span></span>

<span data-ttu-id="bf993-262">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-263">-TypeAdapter</span><span class="sxs-lookup"><span data-stu-id="bf993-263">-TypeAdapter</span></span>

<span data-ttu-id="bf993-264">Hiermee geeft u het type van een type adapter, zoals **micro soft. Power shell. CIM. CimInstanceAdapter**.</span><span class="sxs-lookup"><span data-stu-id="bf993-264">Specifies the type of a type adapter, such as **Microsoft.PowerShell.Cim.CimInstanceAdapter**.</span></span> <span data-ttu-id="bf993-265">Met een type adapter kan Power shell de leden van een type ophalen.</span><span class="sxs-lookup"><span data-stu-id="bf993-265">A type adapter enables PowerShell to get the members of a type.</span></span>

<span data-ttu-id="bf993-266">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-267">-TypeConverter</span><span class="sxs-lookup"><span data-stu-id="bf993-267">-TypeConverter</span></span>

<span data-ttu-id="bf993-268">Hiermee geeft u een type Converter op om waarden te converteren tussen verschillende typen.</span><span class="sxs-lookup"><span data-stu-id="bf993-268">Specifies a type converter to convert values between different types.</span></span> <span data-ttu-id="bf993-269">Als er een type Converter is gedefinieerd voor een type, wordt een exemplaar van het type Converter gebruikt voor de conversie.</span><span class="sxs-lookup"><span data-stu-id="bf993-269">If a type converter is defined for a type, an instance of the type converter is used for the conversion.</span></span>

<span data-ttu-id="bf993-270">Voer een **System. type** -waarde in die is afgeleid van de klassen **System. ComponentModel. TypeConverter** of **System. Management. Automation. PSTypeConverter** .</span><span class="sxs-lookup"><span data-stu-id="bf993-270">Enter a **System.Type** value that is derived from the **System.ComponentModel.TypeConverter** or **System.Management.Automation.PSTypeConverter** classes.</span></span>

<span data-ttu-id="bf993-271">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-272">-TypeData</span><span class="sxs-lookup"><span data-stu-id="bf993-272">-TypeData</span></span>

<span data-ttu-id="bf993-273">Hiermee geeft u een matrix van het type gegevens dat met deze cmdlet wordt toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="bf993-273">Specifies an array of type data that this cmdlet adds to the session.</span></span> <span data-ttu-id="bf993-274">Voer een variabele in die een **TypeData** -object bevat of een opdracht waarmee een **TypeData** -object wordt opgehaald, zoals een `Get-TypeData` opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf993-274">Enter a variable that contains a **TypeData** object or a command that gets a **TypeData** object, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="bf993-275">U kunt ook een **TypeData** -object pipeen naar `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="bf993-275">You can also pipe a **TypeData** object to `Update-TypeData`.</span></span>

<span data-ttu-id="bf993-276">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-276">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-277">-TypeName</span><span class="sxs-lookup"><span data-stu-id="bf993-277">-TypeName</span></span>

<span data-ttu-id="bf993-278">Hiermee geeft u de naam van het type dat moet worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="bf993-278">Specifies the name of the type to extend.</span></span>

<span data-ttu-id="bf993-279">Voor typen in de naam ruimte van het **systeem** voert u de korte naam in.</span><span class="sxs-lookup"><span data-stu-id="bf993-279">For types in the **System** namespace, enter the short name.</span></span> <span data-ttu-id="bf993-280">Anders is de volledige type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="bf993-280">Otherwise, the full type name is required.</span></span> <span data-ttu-id="bf993-281">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf993-281">Wildcards are not supported.</span></span>

<span data-ttu-id="bf993-282">U kunt typen van het type sluizen naar `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="bf993-282">You can pipe type names to `Update-TypeData`.</span></span> <span data-ttu-id="bf993-283">Wanneer u een object pipet op `Update-TypeData` , `Update-TypeData` wordt hiermee de type naam van het object opgehaald en worden gegevens naar het object type getypt.</span><span class="sxs-lookup"><span data-stu-id="bf993-283">When you pipe an object to `Update-TypeData`, `Update-TypeData` gets the type name of the object and type data to the object type.</span></span>

<span data-ttu-id="bf993-284">Gebruik deze para meter met de para meters **lidnaam** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf993-284">Use this parameter with the **MemberName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="bf993-285">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-286">-Waarde</span><span class="sxs-lookup"><span data-stu-id="bf993-286">-Value</span></span>

<span data-ttu-id="bf993-287">Hiermee geeft u de waarde van de eigenschap of methode op.</span><span class="sxs-lookup"><span data-stu-id="bf993-287">Specifies the value of the property or method.</span></span>

<span data-ttu-id="bf993-288">Als u een `AliasProperty` ,, `CodeProperty` `ScriptProperty` of lid toevoegt `CodeMethod` , kunt u de para meter **SecondValue** gebruiken om aanvullende informatie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="bf993-288">If you add an `AliasProperty`, `CodeProperty`, `ScriptProperty`, or `CodeMethod` member, you can use the **SecondValue** parameter to add additional information.</span></span>

<span data-ttu-id="bf993-289">Gebruik deze para meter met de para meters **lidnaam** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf993-289">Use this parameter with the **MemberName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="bf993-290">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf993-290">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf993-291">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bf993-291">-Confirm</span></span>

<span data-ttu-id="bf993-292">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bf993-292">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bf993-293">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bf993-293">-WhatIf</span></span>

<span data-ttu-id="bf993-294">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bf993-294">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bf993-295">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-295">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bf993-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf993-296">CommonParameters</span></span>

<span data-ttu-id="bf993-297">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bf993-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf993-298">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bf993-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf993-299">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="bf993-299">Inputs</span></span>

### <span data-ttu-id="bf993-300">System. String</span><span class="sxs-lookup"><span data-stu-id="bf993-300">System.String</span></span>

<span data-ttu-id="bf993-301">U kunt een teken reeks die de waarden van de para meters **AppendPath** , **TypeName** of **TypeData** bevat, door sluizen naar `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="bf993-301">You can pipe a string that contains the values of the **AppendPath** , **TypeName** , or **TypeData** parameters to `Update-TypeData`.</span></span>

## <span data-ttu-id="bf993-302">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="bf993-302">Outputs</span></span>

### <span data-ttu-id="bf993-303">Geen</span><span class="sxs-lookup"><span data-stu-id="bf993-303">None</span></span>

<span data-ttu-id="bf993-304">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bf993-304">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="bf993-305">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bf993-305">Notes</span></span>

## <span data-ttu-id="bf993-306">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="bf993-306">Related links</span></span>

[<span data-ttu-id="bf993-307">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="bf993-307">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="bf993-308">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="bf993-308">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="bf993-309">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="bf993-309">Remove-TypeData</span></span>](Remove-TypeData.md)
