---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 1c07d79af1516becff86a0706906fa6ddfe03ab8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251398"
---
# <span data-ttu-id="b3605-103">Add-Member</span><span class="sxs-lookup"><span data-stu-id="b3605-103">Add-Member</span></span>

## <span data-ttu-id="b3605-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b3605-104">SYNOPSIS</span></span>
<span data-ttu-id="b3605-105">Hiermee voegt u aangepaste eigenschappen en methoden toe aan een exemplaar van een Power shell-object.</span><span class="sxs-lookup"><span data-stu-id="b3605-105">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="b3605-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b3605-106">SYNTAX</span></span>

### <span data-ttu-id="b3605-107">TypeNameset (standaard)</span><span class="sxs-lookup"><span data-stu-id="b3605-107">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="b3605-108">NotePropertyMultiMemberSet</span><span class="sxs-lookup"><span data-stu-id="b3605-108">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="b3605-109">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="b3605-109">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="b3605-110">Ledenset</span><span class="sxs-lookup"><span data-stu-id="b3605-110">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="b3605-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b3605-111">DESCRIPTION</span></span>

<span data-ttu-id="b3605-112">`Add-Member`Met de cmdlet kunt u leden (eigenschappen en methoden) toevoegen aan een exemplaar van een Power shell-object.</span><span class="sxs-lookup"><span data-stu-id="b3605-112">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="b3605-113">U kunt bijvoorbeeld een NoteProperty-lid toevoegen dat een beschrijving bevat van het object of een **ScriptMethod** -lid dat een script uitvoert om het object te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b3605-113">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="b3605-114">Als u het object wilt gebruiken `Add-Member` , pipet `Add-Member` of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="b3605-114">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="b3605-115">De **member type** para meter geeft het type lid aan dat u wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b3605-115">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="b3605-116">De para meter **name** wijst een naam toe aan het nieuwe lid en de para meter **Value** stelt de waarde van het lid in.</span><span class="sxs-lookup"><span data-stu-id="b3605-116">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="b3605-117">De eigenschappen en methoden die u toevoegt, worden alleen toegevoegd aan het specifieke exemplaar van het object dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="b3605-117">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="b3605-118">`Add-Member` wijzigt het object type niet.</span><span class="sxs-lookup"><span data-stu-id="b3605-118">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="b3605-119">Als u een nieuw object type wilt maken, gebruikt u de `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3605-119">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="b3605-120">U kunt ook de `Export-Clixml` -cmdlet gebruiken om het exemplaar van het object, met inbegrip van de extra leden, op te slaan in een bestand.</span><span class="sxs-lookup"><span data-stu-id="b3605-120">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="b3605-121">Vervolgens kunt u de `Import-Clixml` cmdlet gebruiken om het exemplaar van het object opnieuw te maken op basis van de informatie die is opgeslagen in het geëxporteerde bestand.</span><span class="sxs-lookup"><span data-stu-id="b3605-121">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="b3605-122">Vanaf Windows Power Shell 3,0 `Add-Member` heeft nieuwe functies die het eenvoudiger maken om notitie-eigenschappen toe te voegen aan objecten.</span><span class="sxs-lookup"><span data-stu-id="b3605-122">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="b3605-123">U kunt de para meters **NotePropertyName** en **NotePropertyValue** gebruiken om een eigenschap Note te definiëren of de **NotePropertyMembers** -para meter, die een hash-tabel met notitie-eigenschaps namen en-waarden maakt.</span><span class="sxs-lookup"><span data-stu-id="b3605-123">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="b3605-124">Met ingang van Windows Power Shell 3,0, de para meter **PassThru** , waarmee een uitvoer object wordt gegenereerd, is ook minder vaak nodig.</span><span class="sxs-lookup"><span data-stu-id="b3605-124">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="b3605-125">`Add-Member` voegt nu de nieuwe leden rechtstreeks toe aan het invoer object van meer typen.</span><span class="sxs-lookup"><span data-stu-id="b3605-125">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="b3605-126">Zie de beschrijving van de **PassThru** -para meter voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b3605-126">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="b3605-127">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b3605-127">EXAMPLES</span></span>

### <span data-ttu-id="b3605-128">Voor beeld 1: een notitie-eigenschap toevoegen aan een PSObject</span><span class="sxs-lookup"><span data-stu-id="b3605-128">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="b3605-129">In het volgende voor beeld wordt een **status** notitie-eigenschap met de waarde ' done ' toegevoegd aan het **file info** -object dat het `Test.txt` bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b3605-129">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="b3605-130">Met de eerste opdracht wordt de `Get-ChildItem` cmdlet gebruikt voor het ophalen van een **file info** -object dat het `Test.txt` bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b3605-130">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="b3605-131">Het wordt opgeslagen in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="b3605-131">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="b3605-132">Met de tweede opdracht wordt de eigenschap Note aan het object toegevoegd in `$a` .</span><span class="sxs-lookup"><span data-stu-id="b3605-132">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="b3605-133">De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap **status** van het object in op te halen `$a` .</span><span class="sxs-lookup"><span data-stu-id="b3605-133">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="b3605-134">Zoals in de uitvoer wordt weer gegeven, is de waarde gereed.</span><span class="sxs-lookup"><span data-stu-id="b3605-134">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="b3605-135">Voor beeld 2: een alias eigenschap toevoegen aan een PSObject</span><span class="sxs-lookup"><span data-stu-id="b3605-135">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="b3605-136">In het volgende voor beeld wordt een eigenschap voor **grootte** alias toegevoegd aan het object dat het `Test.txt` bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b3605-136">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="b3605-137">De eigenschap New is een alias voor de eigenschap **Length** .</span><span class="sxs-lookup"><span data-stu-id="b3605-137">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="b3605-138">De eerste opdracht gebruikt de `Get-ChildItem` cmdlet om het file info-object op te halen `Test.txt` **FileInfo** .</span><span class="sxs-lookup"><span data-stu-id="b3605-138">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="b3605-139">Met de tweede opdracht wordt de eigenschap alias **grootte** toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b3605-139">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="b3605-140">De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap nieuwe **grootte** op te halen.</span><span class="sxs-lookup"><span data-stu-id="b3605-140">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="b3605-141">Voor beeld 3: een StringUse Note-eigenschap toevoegen aan een teken reeks</span><span class="sxs-lookup"><span data-stu-id="b3605-141">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="b3605-142">In dit voor beeld wordt de eigenschap **StringUse** Note toegevoegd aan een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="b3605-142">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="b3605-143">Omdat `Add-Member` typen niet kunnen worden toegevoegd aan invoer objecten voor **teken reeksen** , kunt u de para meter **PassThru** opgeven om een uitvoer object te genereren.</span><span class="sxs-lookup"><span data-stu-id="b3605-143">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="b3605-144">Met de laatste opdracht in het voor beeld wordt de nieuwe eigenschap weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b3605-144">The last command in the example displays the new property.</span></span>

<span data-ttu-id="b3605-145">In dit voor beeld wordt de para meter **NotePropertyMembers** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b3605-145">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="b3605-146">De waarde van de para meter **NotePropertyMembers** is een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="b3605-146">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="b3605-147">De sleutel is de eigenschaps naam van de notitie, **StringUse** en de waarde is de eigenschap waarde van de notitie, **weer geven**.</span><span class="sxs-lookup"><span data-stu-id="b3605-147">The key is the note property name, **StringUse** , and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="b3605-148">Voor beeld 4: een script methode toevoegen aan een file info-object</span><span class="sxs-lookup"><span data-stu-id="b3605-148">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="b3605-149">In dit voor beeld wordt de methode **sizeinmb kleiner** toegevoegd aan een **file info** -object dat de bestands grootte in de dichtstbijzijnde Mega byte berekent.</span><span class="sxs-lookup"><span data-stu-id="b3605-149">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="b3605-150">Met de tweede opdracht maakt u een **script Block** die gebruikmaakt van de **ronde** statische methode van het `[math]` type om de bestands grootte af te ronden op de tweede decimaal positie.</span><span class="sxs-lookup"><span data-stu-id="b3605-150">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="b3605-151">De **waarde** para meter gebruikt ook de `$This` Automatische variabele, die het huidige object vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b3605-151">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="b3605-152">De `$This` variabele is alleen geldig in script blokken waarmee nieuwe eigenschappen en methoden worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b3605-152">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="b3605-153">De laatste opdracht maakt gebruik van punt notatie voor het aanroepen van de nieuwe **sizeinmb kleiner** -script methode voor het object in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="b3605-153">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="b3605-154">Voor beeld 5: alle eigenschappen van een object naar een ander kopiëren</span><span class="sxs-lookup"><span data-stu-id="b3605-154">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="b3605-155">Deze functie kopieert alle eigenschappen van een object naar een ander object.</span><span class="sxs-lookup"><span data-stu-id="b3605-155">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="b3605-156">De `foreach` lus gebruikt de `Get-Member` cmdlet om alle eigenschappen van het **from** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="b3605-156">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="b3605-157">De opdrachten binnen de `foreach` lus worden uitgevoerd in reeksen op elk van de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b3605-157">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="b3605-158">De `Add-Member` opdracht wordt de eigenschap van het object **from** aan het object **aan** toegevoegd als **een NoteProperty**.</span><span class="sxs-lookup"><span data-stu-id="b3605-158">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="b3605-159">De waarde wordt gekopieerd met behulp van de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="b3605-159">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="b3605-160">De para meter **Force** wordt gebruikt om leden met dezelfde lidnaam toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="b3605-160">It uses the **Force** parameter to add members with the same member name.</span></span>

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### <span data-ttu-id="b3605-161">Voor beeld 6: een aangepast object maken</span><span class="sxs-lookup"><span data-stu-id="b3605-161">Example 6: Create a custom object</span></span>

<span data-ttu-id="b3605-162">In dit voor beeld wordt een aangepast **activa** object gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b3605-162">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="b3605-163">Met de `New-Object` cmdlet maakt u een **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="b3605-163">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="b3605-164">In het voor beeld wordt de **PSObject** in de `$Asset` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b3605-164">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="b3605-165">Met de tweede opdracht wordt de `[ordered]` type Accelerator gebruikt voor het maken van een geordende woorden lijst met namen en waarden.</span><span class="sxs-lookup"><span data-stu-id="b3605-165">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="b3605-166">De opdracht slaat het resultaat op in de `$D` variabele.</span><span class="sxs-lookup"><span data-stu-id="b3605-166">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="b3605-167">De derde opdracht maakt gebruik van de para meter **NotePropertyMembers** van de `Add-Member` cmdlet om de woorden lijst in de variabele toe te voegen `$D` aan de **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="b3605-167">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="b3605-168">De eigenschap **TypeName** wijst een nieuwe naam, **activa** , toe aan de **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="b3605-168">The **TypeName** property assigns a new name, **Asset** , to the **PSObject**.</span></span>

<span data-ttu-id="b3605-169">De laatste opdracht sluizen het nieuwe **Asset** -object naar de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3605-169">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="b3605-170">In de uitvoer ziet u dat het object de type naam **Asset** heeft en de notitie-eigenschappen die we in de geordende woorden lijst hebben gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b3605-170">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## <span data-ttu-id="b3605-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b3605-171">PARAMETERS</span></span>

### <span data-ttu-id="b3605-172">-Force</span><span class="sxs-lookup"><span data-stu-id="b3605-172">-Force</span></span>

<span data-ttu-id="b3605-173">Geeft aan dat deze cmdlet een nieuw lid toevoegt, zelfs het object heeft een aangepast lid met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="b3605-173">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="b3605-174">U kunt de para meter **Force** niet gebruiken om een standaard lid van een type te vervangen.</span><span class="sxs-lookup"><span data-stu-id="b3605-174">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-175">-Input object</span><span class="sxs-lookup"><span data-stu-id="b3605-175">-InputObject</span></span>

<span data-ttu-id="b3605-176">Hiermee geeft u het object waaraan het nieuwe lid wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b3605-176">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="b3605-177">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b3605-177">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-178">-Member type</span><span class="sxs-lookup"><span data-stu-id="b3605-178">-MemberType</span></span>

<span data-ttu-id="b3605-179">Hiermee geeft u het type lid dat moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b3605-179">Specifies the type of the member to add.</span></span>
<span data-ttu-id="b3605-180">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="b3605-180">This parameter is required.</span></span>
<span data-ttu-id="b3605-181">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b3605-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b3605-182">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="b3605-182">NoteProperty</span></span>
- <span data-ttu-id="b3605-183">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="b3605-183">AliasProperty</span></span>
- <span data-ttu-id="b3605-184">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="b3605-184">ScriptProperty</span></span>
- <span data-ttu-id="b3605-185">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="b3605-185">CodeProperty</span></span>
- <span data-ttu-id="b3605-186">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="b3605-186">ScriptMethod</span></span>
- <span data-ttu-id="b3605-187">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="b3605-187">CodeMethod</span></span>

<span data-ttu-id="b3605-188">Zie [PSMemberTypes Enumeration (Engelstalig)](/dotnet/api/system.management.automation.psmembertypes) in de MSDN-bibliotheek voor meer informatie over deze waarden.</span><span class="sxs-lookup"><span data-stu-id="b3605-188">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the MSDN library.</span></span>

<span data-ttu-id="b3605-189">Niet alle objecten hebben elk type lid.</span><span class="sxs-lookup"><span data-stu-id="b3605-189">Not all objects have every type of member.</span></span>
<span data-ttu-id="b3605-190">Als u een lidtype opgeeft dat het object niet heeft, retourneert Power shell een fout.</span><span class="sxs-lookup"><span data-stu-id="b3605-190">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-191">-Name</span><span class="sxs-lookup"><span data-stu-id="b3605-191">-Name</span></span>

<span data-ttu-id="b3605-192">Hiermee geeft u de naam van het lid dat met deze cmdlet wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b3605-192">Specifies the name of the member that this cmdlet adds.</span></span>

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-193">-NotePropertyMembers</span><span class="sxs-lookup"><span data-stu-id="b3605-193">-NotePropertyMembers</span></span>

<span data-ttu-id="b3605-194">Hiermee geeft u een hash-tabel of een geordende woorden lijst met namen en waarden van notitie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b3605-194">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="b3605-195">Typ een hash-tabel of-woorden lijst waarin de sleutels namen van notitie-eigenschappen zijn en de waarden zijn eigenschaps waarden van notities.</span><span class="sxs-lookup"><span data-stu-id="b3605-195">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="b3605-196">Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen en geordende woorden lijsten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b3605-196">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="b3605-197">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b3605-197">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-198">-NotePropertyName</span><span class="sxs-lookup"><span data-stu-id="b3605-198">-NotePropertyName</span></span>

<span data-ttu-id="b3605-199">Hiermee geeft u de naam van de notitie-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b3605-199">Specifies the note property name.</span></span>

<span data-ttu-id="b3605-200">Gebruik deze para meter met de para meter **NotePropertyValue** .</span><span class="sxs-lookup"><span data-stu-id="b3605-200">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="b3605-201">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="b3605-201">This parameter is optional.</span></span>

<span data-ttu-id="b3605-202">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b3605-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-203">-NotePropertyValue</span><span class="sxs-lookup"><span data-stu-id="b3605-203">-NotePropertyValue</span></span>

<span data-ttu-id="b3605-204">Geeft de waarde van de eigenschap Note aan.</span><span class="sxs-lookup"><span data-stu-id="b3605-204">Specifies the note property value.</span></span>

<span data-ttu-id="b3605-205">Gebruik deze para meter met de para meter **NotePropertyName** .</span><span class="sxs-lookup"><span data-stu-id="b3605-205">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="b3605-206">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="b3605-206">This parameter is optional.</span></span>

<span data-ttu-id="b3605-207">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b3605-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-208">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b3605-208">-PassThru</span></span>

<span data-ttu-id="b3605-209">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="b3605-209">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b3605-210">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="b3605-210">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="b3605-211">Voor de meeste objecten `Add-Member` voegt de nieuwe leden toe aan het invoer object.</span><span class="sxs-lookup"><span data-stu-id="b3605-211">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="b3605-212">Wanneer het invoer object echter een teken reeks is, `Add-Member` kan het lid niet toevoegen aan het invoer object.</span><span class="sxs-lookup"><span data-stu-id="b3605-212">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="b3605-213">Voor deze objecten gebruikt u de para meter **PassThru** om een uitvoer object te maken.</span><span class="sxs-lookup"><span data-stu-id="b3605-213">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="b3605-214">In Windows Power Shell 2,0 worden `Add-Member` leden alleen toegevoegd aan de **PSObject** -wrapper van objecten, niet aan het object.</span><span class="sxs-lookup"><span data-stu-id="b3605-214">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="b3605-215">Gebruik de para meter **PassThru** om een uitvoer object te maken voor een object met een **PSObject** -wrapper.</span><span class="sxs-lookup"><span data-stu-id="b3605-215">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

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

### <span data-ttu-id="b3605-216">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="b3605-216">-SecondValue</span></span>

<span data-ttu-id="b3605-217">Hiermee geeft u optionele aanvullende informatie op over **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -of **CodeMethod** -leden.</span><span class="sxs-lookup"><span data-stu-id="b3605-217">Specifies optional additional information about **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="b3605-218">Als deze para meter wordt gebruikt bij het toevoegen van een **AliasProperty** , moet deze een gegevens type zijn.</span><span class="sxs-lookup"><span data-stu-id="b3605-218">If used when adding an **AliasProperty** , this parameter must be a data type.</span></span>
<span data-ttu-id="b3605-219">Een conversie naar het opgegeven gegevens type wordt toegevoegd aan de waarde van de **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="b3605-219">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="b3605-220">Als u bijvoorbeeld een **AliasProperty** toevoegt die een alternatieve naam voor een teken reeks eigenschap levert, kunt u ook een **SecondValue** -para meter van **System. Int32** opgeven om aan te geven dat de waarde van de teken reeks eigenschap moet worden geconverteerd naar een geheel getal wanneer deze wordt geopend met behulp van de bijbehorende **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="b3605-220">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="b3605-221">U kunt de para meter **SecondValue** gebruiken om een extra **script Block** op te geven bij het toevoegen van een **ScriptProperty** -lid.</span><span class="sxs-lookup"><span data-stu-id="b3605-221">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="b3605-222">De eerste **script Block** , die in de **waarde** para meter wordt opgegeven, wordt gebruikt om de waarde van een variabele op te halen.</span><span class="sxs-lookup"><span data-stu-id="b3605-222">The first **ScriptBlock** , specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="b3605-223">De tweede **script Block** , opgegeven in de para meter **SecondValue** , wordt gebruikt om de waarde van een variabele in te stellen.</span><span class="sxs-lookup"><span data-stu-id="b3605-223">The second **ScriptBlock** , specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-224">-Waarde</span><span class="sxs-lookup"><span data-stu-id="b3605-224">-Value</span></span>

<span data-ttu-id="b3605-225">Hiermee geeft u de begin waarde van het toegevoegde lid op.</span><span class="sxs-lookup"><span data-stu-id="b3605-225">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="b3605-226">Als u een **AliasProperty** -, **CodeProperty** -, **ScriptProperty** -of **CodeMethod** -lid toevoegt, kunt u optionele, aanvullende informatie opgeven met behulp van de **SecondValue** -para meter.</span><span class="sxs-lookup"><span data-stu-id="b3605-226">If you add an **AliasProperty** , **CodeProperty** , **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-227">-TypeName</span><span class="sxs-lookup"><span data-stu-id="b3605-227">-TypeName</span></span>

<span data-ttu-id="b3605-228">Hiermee geeft u een naam op voor het type.</span><span class="sxs-lookup"><span data-stu-id="b3605-228">Specifies a name for the type.</span></span>

<span data-ttu-id="b3605-229">Wanneer het type een klasse in de naam ruimte van het **systeem** is of een type dat een type Accelerator heeft, kunt u de korte naam van het type opgeven.</span><span class="sxs-lookup"><span data-stu-id="b3605-229">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="b3605-230">Anders is de volledige type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="b3605-230">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="b3605-231">Deze para meter is alleen effectief wanneer de **input object** een **PSObject** is.</span><span class="sxs-lookup"><span data-stu-id="b3605-231">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="b3605-232">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b3605-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3605-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3605-233">CommonParameters</span></span>

<span data-ttu-id="b3605-234">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b3605-234">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b3605-235">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b3605-235">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b3605-236">INVOER</span><span class="sxs-lookup"><span data-stu-id="b3605-236">INPUTS</span></span>

### <span data-ttu-id="b3605-237">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b3605-237">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b3605-238">U kunt elk object type door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3605-238">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="b3605-239">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b3605-239">OUTPUTS</span></span>

### <span data-ttu-id="b3605-240">Geen-of System. object</span><span class="sxs-lookup"><span data-stu-id="b3605-240">None or System.Object</span></span>

<span data-ttu-id="b3605-241">Wanneer u de para meter **PassThru** gebruikt, retourneert deze cmdlet het nieuwe uitgebreide object.</span><span class="sxs-lookup"><span data-stu-id="b3605-241">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="b3605-242">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b3605-242">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b3605-243">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b3605-243">NOTES</span></span>

<span data-ttu-id="b3605-244">U kunt leden alleen toevoegen aan **PSObject** -objecten.</span><span class="sxs-lookup"><span data-stu-id="b3605-244">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="b3605-245">Gebruik de operator om te bepalen of een object een **PSObject** -object is `-is` .</span><span class="sxs-lookup"><span data-stu-id="b3605-245">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="b3605-246">Als u bijvoorbeeld een object wilt testen dat is opgeslagen in de `$obj` variabele, typt u `$obj -is [PSObject]` .</span><span class="sxs-lookup"><span data-stu-id="b3605-246">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="b3605-247">De namen van de para meters **member type** , **name** , **Value** en **SecondValue** zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="b3605-247">The names of the **MemberType** , **Name** , **Value** , and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="b3605-248">Als u de parameter namen weglaat, moeten de niet-genaamde parameter waarden in deze volg orde worden weer gegeven: **member type** , **name** , **Value** en **SecondValue**.</span><span class="sxs-lookup"><span data-stu-id="b3605-248">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType** , **Name** , **Value** , and **SecondValue**.</span></span>

<span data-ttu-id="b3605-249">Als u de parameter namen toevoegt, kunnen de para meters in een wille keurige volg orde worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b3605-249">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="b3605-250">U kunt de `$this` Automatische variabele gebruiken in script blokken waarmee de waarden van nieuwe eigenschappen en methoden worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b3605-250">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="b3605-251">De `$this` variabele verwijst naar het exemplaar van het object waarnaar de eigenschappen en methoden worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b3605-251">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="b3605-252">Zie about_Automatic_Variables voor meer informatie over de `$this` variabele [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b3605-252">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="b3605-253">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b3605-253">RELATED LINKS</span></span>

[<span data-ttu-id="b3605-254">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="b3605-254">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="b3605-255">Get-member</span><span class="sxs-lookup"><span data-stu-id="b3605-255">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="b3605-256">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="b3605-256">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="b3605-257">New-Object</span><span class="sxs-lookup"><span data-stu-id="b3605-257">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="b3605-258">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b3605-258">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

