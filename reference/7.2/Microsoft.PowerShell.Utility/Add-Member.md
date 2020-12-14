---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 4e9e5ec6d188bec0b4032151fb92e6995d8efbb8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705472"
---
# <span data-ttu-id="fb71a-102">Add-Member</span><span class="sxs-lookup"><span data-stu-id="fb71a-102">Add-Member</span></span>

## <span data-ttu-id="fb71a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fb71a-103">SYNOPSIS</span></span>
<span data-ttu-id="fb71a-104">Hiermee voegt u aangepaste eigenschappen en methoden toe aan een exemplaar van een Power shell-object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-104">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="fb71a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fb71a-105">SYNTAX</span></span>

### <span data-ttu-id="fb71a-106">TypeNameset (standaard)</span><span class="sxs-lookup"><span data-stu-id="fb71a-106">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="fb71a-107">NotePropertyMultiMemberSet</span><span class="sxs-lookup"><span data-stu-id="fb71a-107">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="fb71a-108">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="fb71a-108">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="fb71a-109">Ledenset</span><span class="sxs-lookup"><span data-stu-id="fb71a-109">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="fb71a-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fb71a-110">DESCRIPTION</span></span>

<span data-ttu-id="fb71a-111">`Add-Member`Met de cmdlet kunt u leden (eigenschappen en methoden) toevoegen aan een exemplaar van een Power shell-object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-111">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="fb71a-112">U kunt bijvoorbeeld een NoteProperty-lid toevoegen dat een beschrijving bevat van het object of een **ScriptMethod** -lid dat een script uitvoert om het object te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-112">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="fb71a-113">Als u het object wilt gebruiken `Add-Member` , pipet `Add-Member` of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="fb71a-113">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="fb71a-114">De **member type** para meter geeft het type lid aan dat u wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-114">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="fb71a-115">De para meter **name** wijst een naam toe aan het nieuwe lid en de para meter **Value** stelt de waarde van het lid in.</span><span class="sxs-lookup"><span data-stu-id="fb71a-115">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="fb71a-116">De eigenschappen en methoden die u toevoegt, worden alleen toegevoegd aan het specifieke exemplaar van het object dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fb71a-116">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="fb71a-117">`Add-Member` wijzigt het object type niet.</span><span class="sxs-lookup"><span data-stu-id="fb71a-117">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="fb71a-118">Als u een nieuw object type wilt maken, gebruikt u de `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb71a-118">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="fb71a-119">U kunt ook de `Export-Clixml` -cmdlet gebruiken om het exemplaar van het object, met inbegrip van de extra leden, op te slaan in een bestand.</span><span class="sxs-lookup"><span data-stu-id="fb71a-119">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="fb71a-120">Vervolgens kunt u de `Import-Clixml` cmdlet gebruiken om het exemplaar van het object opnieuw te maken op basis van de informatie die is opgeslagen in het geëxporteerde bestand.</span><span class="sxs-lookup"><span data-stu-id="fb71a-120">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="fb71a-121">Vanaf Windows Power Shell 3,0 `Add-Member` heeft nieuwe functies die het eenvoudiger maken om notitie-eigenschappen toe te voegen aan objecten.</span><span class="sxs-lookup"><span data-stu-id="fb71a-121">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="fb71a-122">U kunt de para meters **NotePropertyName** en **NotePropertyValue** gebruiken om een eigenschap Note te definiëren of de **NotePropertyMembers** -para meter, die een hash-tabel met notitie-eigenschaps namen en-waarden maakt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-122">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="fb71a-123">Met ingang van Windows Power Shell 3,0, de para meter **PassThru** , waarmee een uitvoer object wordt gegenereerd, is ook minder vaak nodig.</span><span class="sxs-lookup"><span data-stu-id="fb71a-123">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="fb71a-124">`Add-Member` voegt nu de nieuwe leden rechtstreeks toe aan het invoer object van meer typen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-124">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="fb71a-125">Zie de beschrijving van de **PassThru** -para meter voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb71a-125">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="fb71a-126">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fb71a-126">EXAMPLES</span></span>

### <span data-ttu-id="fb71a-127">Voor beeld 1: een notitie-eigenschap toevoegen aan een PSObject</span><span class="sxs-lookup"><span data-stu-id="fb71a-127">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="fb71a-128">In het volgende voor beeld wordt een **status** notitie-eigenschap met de waarde ' done ' toegevoegd aan het **file info** -object dat het `Test.txt` bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-128">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="fb71a-129">Met de eerste opdracht wordt de `Get-ChildItem` cmdlet gebruikt voor het ophalen van een **file info** -object dat het `Test.txt` bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-129">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="fb71a-130">Het wordt opgeslagen in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="fb71a-130">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="fb71a-131">Met de tweede opdracht wordt de eigenschap Note aan het object toegevoegd in `$a` .</span><span class="sxs-lookup"><span data-stu-id="fb71a-131">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="fb71a-132">De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap **status** van het object in op te halen `$a` .</span><span class="sxs-lookup"><span data-stu-id="fb71a-132">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="fb71a-133">Zoals in de uitvoer wordt weer gegeven, is de waarde gereed.</span><span class="sxs-lookup"><span data-stu-id="fb71a-133">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="fb71a-134">Voor beeld 2: een alias eigenschap toevoegen aan een PSObject</span><span class="sxs-lookup"><span data-stu-id="fb71a-134">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="fb71a-135">In het volgende voor beeld wordt een eigenschap voor **grootte** alias toegevoegd aan het object dat het `Test.txt` bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-135">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="fb71a-136">De eigenschap New is een alias voor de eigenschap **Length** .</span><span class="sxs-lookup"><span data-stu-id="fb71a-136">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="fb71a-137">De eerste opdracht gebruikt de `Get-ChildItem` cmdlet om het file info-object op te halen `Test.txt`  .</span><span class="sxs-lookup"><span data-stu-id="fb71a-137">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="fb71a-138">Met de tweede opdracht wordt de eigenschap alias **grootte** toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-138">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="fb71a-139">De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap nieuwe **grootte** op te halen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-139">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="fb71a-140">Voor beeld 3: een StringUse Note-eigenschap toevoegen aan een teken reeks</span><span class="sxs-lookup"><span data-stu-id="fb71a-140">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="fb71a-141">In dit voor beeld wordt de eigenschap **StringUse** Note toegevoegd aan een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="fb71a-141">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="fb71a-142">Omdat `Add-Member` typen niet kunnen worden toegevoegd aan invoer objecten voor **teken reeksen** , kunt u de para meter **PassThru** opgeven om een uitvoer object te genereren.</span><span class="sxs-lookup"><span data-stu-id="fb71a-142">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="fb71a-143">Met de laatste opdracht in het voor beeld wordt de nieuwe eigenschap weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb71a-143">The last command in the example displays the new property.</span></span>

<span data-ttu-id="fb71a-144">In dit voor beeld wordt de para meter **NotePropertyMembers** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-144">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="fb71a-145">De waarde van de para meter **NotePropertyMembers** is een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="fb71a-145">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="fb71a-146">De sleutel is de eigenschaps naam van de notitie, **StringUse** en de waarde is de eigenschap waarde van de notitie, **weer geven**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-146">The key is the note property name, **StringUse**, and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="fb71a-147">Voor beeld 4: een script methode toevoegen aan een file info-object</span><span class="sxs-lookup"><span data-stu-id="fb71a-147">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="fb71a-148">In dit voor beeld wordt de methode **sizeinmb kleiner** toegevoegd aan een **file info** -object dat de bestands grootte in de dichtstbijzijnde Mega byte berekent.</span><span class="sxs-lookup"><span data-stu-id="fb71a-148">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="fb71a-149">Met de tweede opdracht maakt u een **script Block** die gebruikmaakt van de **ronde** statische methode van het `[math]` type om de bestands grootte af te ronden op de tweede decimaal positie.</span><span class="sxs-lookup"><span data-stu-id="fb71a-149">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="fb71a-150">De **waarde** para meter gebruikt ook de `$This` Automatische variabele, die het huidige object vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-150">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="fb71a-151">De `$This` variabele is alleen geldig in script blokken waarmee nieuwe eigenschappen en methoden worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-151">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="fb71a-152">De laatste opdracht maakt gebruik van punt notatie voor het aanroepen van de nieuwe **sizeinmb kleiner** -script methode voor het object in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="fb71a-152">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="fb71a-153">Voor beeld 5: alle eigenschappen van een object naar een ander kopiëren</span><span class="sxs-lookup"><span data-stu-id="fb71a-153">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="fb71a-154">Deze functie kopieert alle eigenschappen van een object naar een ander object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-154">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="fb71a-155">De `foreach` lus gebruikt de `Get-Member` cmdlet om alle eigenschappen van het **from** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-155">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="fb71a-156">De opdrachten binnen de `foreach` lus worden uitgevoerd in reeksen op elk van de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-156">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="fb71a-157">De `Add-Member` opdracht wordt de eigenschap van het object **from** aan het object **aan** toegevoegd als **een NoteProperty**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-157">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="fb71a-158">De waarde wordt gekopieerd met behulp van de **waarde** -para meter.</span><span class="sxs-lookup"><span data-stu-id="fb71a-158">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="fb71a-159">De para meter **Force** wordt gebruikt om leden met dezelfde lidnaam toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-159">It uses the **Force** parameter to add members with the same member name.</span></span>

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

### <span data-ttu-id="fb71a-160">Voor beeld 6: een aangepast object maken</span><span class="sxs-lookup"><span data-stu-id="fb71a-160">Example 6: Create a custom object</span></span>

<span data-ttu-id="fb71a-161">In dit voor beeld wordt een aangepast **activa** object gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-161">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="fb71a-162">Met de `New-Object` cmdlet maakt u een **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-162">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="fb71a-163">In het voor beeld wordt de **PSObject** in de `$Asset` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-163">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="fb71a-164">Met de tweede opdracht wordt de `[ordered]` type Accelerator gebruikt voor het maken van een geordende woorden lijst met namen en waarden.</span><span class="sxs-lookup"><span data-stu-id="fb71a-164">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="fb71a-165">De opdracht slaat het resultaat op in de `$D` variabele.</span><span class="sxs-lookup"><span data-stu-id="fb71a-165">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="fb71a-166">De derde opdracht maakt gebruik van de para meter **NotePropertyMembers** van de `Add-Member` cmdlet om de woorden lijst in de variabele toe te voegen `$D` aan de **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-166">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="fb71a-167">De eigenschap **TypeName** wijst een nieuwe naam, **activa**, toe aan de **PSObject**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-167">The **TypeName** property assigns a new name, **Asset**, to the **PSObject**.</span></span>

<span data-ttu-id="fb71a-168">De laatste opdracht sluizen het nieuwe **Asset** -object naar de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb71a-168">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="fb71a-169">In de uitvoer ziet u dat het object de type naam **Asset** heeft en de notitie-eigenschappen die we in de geordende woorden lijst hebben gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-169">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

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

## <span data-ttu-id="fb71a-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb71a-170">PARAMETERS</span></span>

### <span data-ttu-id="fb71a-171">-Force</span><span class="sxs-lookup"><span data-stu-id="fb71a-171">-Force</span></span>

<span data-ttu-id="fb71a-172">Geeft aan dat deze cmdlet een nieuw lid toevoegt, zelfs het object heeft een aangepast lid met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="fb71a-172">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="fb71a-173">U kunt de para meter **Force** niet gebruiken om een standaard lid van een type te vervangen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-173">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

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

### <span data-ttu-id="fb71a-174">-Input object</span><span class="sxs-lookup"><span data-stu-id="fb71a-174">-InputObject</span></span>

<span data-ttu-id="fb71a-175">Hiermee geeft u het object waaraan het nieuwe lid wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-175">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="fb71a-176">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fb71a-176">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="fb71a-177">-Member type</span><span class="sxs-lookup"><span data-stu-id="fb71a-177">-MemberType</span></span>

<span data-ttu-id="fb71a-178">Hiermee geeft u het type lid dat moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-178">Specifies the type of the member to add.</span></span>
<span data-ttu-id="fb71a-179">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="fb71a-179">This parameter is required.</span></span>
<span data-ttu-id="fb71a-180">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="fb71a-180">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fb71a-181">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="fb71a-181">NoteProperty</span></span>
- <span data-ttu-id="fb71a-182">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="fb71a-182">AliasProperty</span></span>
- <span data-ttu-id="fb71a-183">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="fb71a-183">ScriptProperty</span></span>
- <span data-ttu-id="fb71a-184">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="fb71a-184">CodeProperty</span></span>
- <span data-ttu-id="fb71a-185">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="fb71a-185">ScriptMethod</span></span>
- <span data-ttu-id="fb71a-186">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="fb71a-186">CodeMethod</span></span>

<span data-ttu-id="fb71a-187">Zie [PSMemberTypes-inventarisatie](/dotnet/api/system.management.automation.psmembertypes) in de Power shell-SDK voor meer informatie over deze waarden.</span><span class="sxs-lookup"><span data-stu-id="fb71a-187">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the PowerShell SDK.</span></span>

<span data-ttu-id="fb71a-188">Niet alle objecten hebben elk type lid.</span><span class="sxs-lookup"><span data-stu-id="fb71a-188">Not all objects have every type of member.</span></span>
<span data-ttu-id="fb71a-189">Als u een lidtype opgeeft dat het object niet heeft, retourneert Power shell een fout.</span><span class="sxs-lookup"><span data-stu-id="fb71a-189">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

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

### <span data-ttu-id="fb71a-190">-Name</span><span class="sxs-lookup"><span data-stu-id="fb71a-190">-Name</span></span>

<span data-ttu-id="fb71a-191">Hiermee geeft u de naam van het lid dat met deze cmdlet wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-191">Specifies the name of the member that this cmdlet adds.</span></span>

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

### <span data-ttu-id="fb71a-192">-NotePropertyMembers</span><span class="sxs-lookup"><span data-stu-id="fb71a-192">-NotePropertyMembers</span></span>

<span data-ttu-id="fb71a-193">Hiermee geeft u een hash-tabel of een geordende woorden lijst met namen en waarden van notitie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-193">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="fb71a-194">Typ een hash-tabel of-woorden lijst waarin de sleutels namen van notitie-eigenschappen zijn en de waarden zijn eigenschaps waarden van notities.</span><span class="sxs-lookup"><span data-stu-id="fb71a-194">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="fb71a-195">Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen en geordende woorden lijsten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="fb71a-195">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="fb71a-196">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb71a-196">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fb71a-197">-NotePropertyName</span><span class="sxs-lookup"><span data-stu-id="fb71a-197">-NotePropertyName</span></span>

<span data-ttu-id="fb71a-198">Hiermee geeft u de naam van de notitie-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="fb71a-198">Specifies the note property name.</span></span>

<span data-ttu-id="fb71a-199">Gebruik deze para meter met de para meter **NotePropertyValue** .</span><span class="sxs-lookup"><span data-stu-id="fb71a-199">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="fb71a-200">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb71a-200">This parameter is optional.</span></span>

<span data-ttu-id="fb71a-201">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb71a-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fb71a-202">-NotePropertyValue</span><span class="sxs-lookup"><span data-stu-id="fb71a-202">-NotePropertyValue</span></span>

<span data-ttu-id="fb71a-203">Geeft de waarde van de eigenschap Note aan.</span><span class="sxs-lookup"><span data-stu-id="fb71a-203">Specifies the note property value.</span></span>

<span data-ttu-id="fb71a-204">Gebruik deze para meter met de para meter **NotePropertyName** .</span><span class="sxs-lookup"><span data-stu-id="fb71a-204">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="fb71a-205">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb71a-205">This parameter is optional.</span></span>

<span data-ttu-id="fb71a-206">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb71a-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fb71a-207">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fb71a-207">-PassThru</span></span>

<span data-ttu-id="fb71a-208">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="fb71a-208">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="fb71a-209">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fb71a-209">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="fb71a-210">Voor de meeste objecten `Add-Member` voegt de nieuwe leden toe aan het invoer object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-210">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="fb71a-211">Wanneer het invoer object echter een teken reeks is, `Add-Member` kan het lid niet toevoegen aan het invoer object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-211">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="fb71a-212">Voor deze objecten gebruikt u de para meter **PassThru** om een uitvoer object te maken.</span><span class="sxs-lookup"><span data-stu-id="fb71a-212">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="fb71a-213">In Windows Power Shell 2,0 worden `Add-Member` leden alleen toegevoegd aan de **PSObject** -wrapper van objecten, niet aan het object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-213">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="fb71a-214">Gebruik de para meter **PassThru** om een uitvoer object te maken voor een object met een **PSObject** -wrapper.</span><span class="sxs-lookup"><span data-stu-id="fb71a-214">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

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

### <span data-ttu-id="fb71a-215">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="fb71a-215">-SecondValue</span></span>

<span data-ttu-id="fb71a-216">Hiermee geeft u optionele aanvullende informatie op over **AliasProperty**-, **ScriptProperty**-, **CodeProperty**-of **CodeMethod** -leden.</span><span class="sxs-lookup"><span data-stu-id="fb71a-216">Specifies optional additional information about **AliasProperty**, **ScriptProperty**, **CodeProperty**, or **CodeMethod** members.</span></span>

<span data-ttu-id="fb71a-217">Als deze para meter wordt gebruikt bij het toevoegen van een **AliasProperty**, moet deze een gegevens type zijn.</span><span class="sxs-lookup"><span data-stu-id="fb71a-217">If used when adding an **AliasProperty**, this parameter must be a data type.</span></span>
<span data-ttu-id="fb71a-218">Een conversie naar het opgegeven gegevens type wordt toegevoegd aan de waarde van de **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-218">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="fb71a-219">Als u bijvoorbeeld een **AliasProperty** toevoegt die een alternatieve naam voor een teken reeks eigenschap levert, kunt u ook een **SecondValue** -para meter van **System. Int32** opgeven om aan te geven dat de waarde van de teken reeks eigenschap moet worden geconverteerd naar een geheel getal wanneer deze wordt geopend met behulp van de bijbehorende **AliasProperty**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-219">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="fb71a-220">U kunt de para meter **SecondValue** gebruiken om een extra **script Block** op te geven bij het toevoegen van een **ScriptProperty** -lid.</span><span class="sxs-lookup"><span data-stu-id="fb71a-220">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="fb71a-221">De eerste **script Block**, die in de **waarde** para meter wordt opgegeven, wordt gebruikt om de waarde van een variabele op te halen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-221">The first **ScriptBlock**, specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="fb71a-222">De tweede **script Block**, opgegeven in de para meter **SecondValue** , wordt gebruikt om de waarde van een variabele in te stellen.</span><span class="sxs-lookup"><span data-stu-id="fb71a-222">The second **ScriptBlock**, specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

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

### <span data-ttu-id="fb71a-223">-Waarde</span><span class="sxs-lookup"><span data-stu-id="fb71a-223">-Value</span></span>

<span data-ttu-id="fb71a-224">Hiermee geeft u de begin waarde van het toegevoegde lid op.</span><span class="sxs-lookup"><span data-stu-id="fb71a-224">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="fb71a-225">Als u een **AliasProperty**-, **CodeProperty**-, **ScriptProperty** -of **CodeMethod** -lid toevoegt, kunt u optionele, aanvullende informatie opgeven met behulp van de **SecondValue** -para meter.</span><span class="sxs-lookup"><span data-stu-id="fb71a-225">If you add an **AliasProperty**, **CodeProperty**, **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

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

### <span data-ttu-id="fb71a-226">-TypeName</span><span class="sxs-lookup"><span data-stu-id="fb71a-226">-TypeName</span></span>

<span data-ttu-id="fb71a-227">Hiermee geeft u een naam op voor het type.</span><span class="sxs-lookup"><span data-stu-id="fb71a-227">Specifies a name for the type.</span></span>

<span data-ttu-id="fb71a-228">Wanneer het type een klasse in de naam ruimte van het **systeem** is of een type dat een type Accelerator heeft, kunt u de korte naam van het type opgeven.</span><span class="sxs-lookup"><span data-stu-id="fb71a-228">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="fb71a-229">Anders is de volledige type naam vereist.</span><span class="sxs-lookup"><span data-stu-id="fb71a-229">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="fb71a-230">Deze para meter is alleen effectief wanneer de **input object** een **PSObject** is.</span><span class="sxs-lookup"><span data-stu-id="fb71a-230">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="fb71a-231">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fb71a-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="fb71a-232">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb71a-232">CommonParameters</span></span>

<span data-ttu-id="fb71a-233">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb71a-233">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb71a-234">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb71a-234">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fb71a-235">INVOER</span><span class="sxs-lookup"><span data-stu-id="fb71a-235">INPUTS</span></span>

### <span data-ttu-id="fb71a-236">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="fb71a-236">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fb71a-237">U kunt elk object type door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb71a-237">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="fb71a-238">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fb71a-238">OUTPUTS</span></span>

### <span data-ttu-id="fb71a-239">Geen-of System. object</span><span class="sxs-lookup"><span data-stu-id="fb71a-239">None or System.Object</span></span>

<span data-ttu-id="fb71a-240">Wanneer u de para meter **PassThru** gebruikt, retourneert deze cmdlet het nieuwe uitgebreide object.</span><span class="sxs-lookup"><span data-stu-id="fb71a-240">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="fb71a-241">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-241">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fb71a-242">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fb71a-242">NOTES</span></span>

<span data-ttu-id="fb71a-243">U kunt leden alleen toevoegen aan **PSObject** -objecten.</span><span class="sxs-lookup"><span data-stu-id="fb71a-243">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="fb71a-244">Gebruik de operator om te bepalen of een object een **PSObject** -object is `-is` .</span><span class="sxs-lookup"><span data-stu-id="fb71a-244">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="fb71a-245">Als u bijvoorbeeld een object wilt testen dat is opgeslagen in de `$obj` variabele, typt u `$obj -is [PSObject]` .</span><span class="sxs-lookup"><span data-stu-id="fb71a-245">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="fb71a-246">De namen van de para meters **member type**, **name**, **Value** en **SecondValue** zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb71a-246">The names of the **MemberType**, **Name**, **Value**, and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="fb71a-247">Als u de parameter namen weglaat, moeten de niet-genaamde parameter waarden in deze volg orde worden weer gegeven: **member type**, **name**, **Value** en **SecondValue**.</span><span class="sxs-lookup"><span data-stu-id="fb71a-247">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType**, **Name**, **Value**, and **SecondValue**.</span></span>

<span data-ttu-id="fb71a-248">Als u de parameter namen toevoegt, kunnen de para meters in een wille keurige volg orde worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb71a-248">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="fb71a-249">U kunt de `$this` Automatische variabele gebruiken in script blokken waarmee de waarden van nieuwe eigenschappen en methoden worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-249">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="fb71a-250">De `$this` variabele verwijst naar het exemplaar van het object waarnaar de eigenschappen en methoden worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fb71a-250">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="fb71a-251">Zie about_Automatic_Variables voor meer informatie over de `$this` variabele [](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="fb71a-251">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="fb71a-252">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fb71a-252">RELATED LINKS</span></span>

[<span data-ttu-id="fb71a-253">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="fb71a-253">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="fb71a-254">Get-member</span><span class="sxs-lookup"><span data-stu-id="fb71a-254">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="fb71a-255">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="fb71a-255">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="fb71a-256">New-Object</span><span class="sxs-lookup"><span data-stu-id="fb71a-256">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="fb71a-257">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="fb71a-257">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

