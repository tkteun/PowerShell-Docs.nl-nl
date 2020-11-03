---
description: Hierin wordt beschreven hoe u methoden gebruikt om acties uit te voeren voor objecten in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 7160b049cffffa35263fc75fd595997c98ca2e34
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252597"
---
# <a name="about-methods"></a><span data-ttu-id="5a454-104">Over methoden</span><span class="sxs-lookup"><span data-stu-id="5a454-104">About methods</span></span>

## <a name="short-description"></a><span data-ttu-id="5a454-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a454-105">Short description</span></span>
<span data-ttu-id="5a454-106">Hierin wordt beschreven hoe u methoden gebruikt om acties uit te voeren voor objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="5a454-106">Describes how to use methods to perform actions on objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5a454-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a454-107">Long description</span></span>

<span data-ttu-id="5a454-108">Power shell gebruikt objecten om de items in de gegevens archieven of de status van de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5a454-108">PowerShell uses objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="5a454-109">File info-objecten vertegenwoordigen bijvoorbeeld de bestanden in bestandssysteem stations en ProcessInfo-objecten die de processen op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="5a454-109">For example, FileInfo objects represent the files in file system drives and ProcessInfo objects represent the processes on the computer.</span></span>

<span data-ttu-id="5a454-110">Objecten hebben eigenschappen die gegevens over het object opslaan en methoden waarmee u het object kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5a454-110">Objects have properties, which store data about the object, and methods that let you change the object.</span></span>

<span data-ttu-id="5a454-111">Een ' methode ' is een set instructies waarmee u een actie opgeeft die u op het object kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="5a454-111">A "method" is a set of instructions that specify an action you can perform on the object.</span></span> <span data-ttu-id="5a454-112">Het `FileInfo` object bevat bijvoorbeeld de `CopyTo` methode waarmee het bestand dat het object vertegenwoordigt, wordt gekopieerd `FileInfo` .</span><span class="sxs-lookup"><span data-stu-id="5a454-112">For example, the `FileInfo` object includes the `CopyTo` method that copies the file that the `FileInfo` object represents.</span></span>

<span data-ttu-id="5a454-113">Als u de methoden van een object wilt ophalen, gebruikt u de- `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a454-113">To get the methods of any object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="5a454-114">Gebruik de eigenschap **member type** met de waarde ' method '.</span><span class="sxs-lookup"><span data-stu-id="5a454-114">Use its **MemberType** property with a value of "Method".</span></span> <span data-ttu-id="5a454-115">Met de volgende opdracht worden de methoden van proces objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5a454-115">The following command gets the methods of process objects.</span></span>

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

<span data-ttu-id="5a454-116">Als u een methode van een object wilt uitvoeren of ' invoke ', typt u een punt (.), de naam van de methode en een verzameling van haakjes "()".</span><span class="sxs-lookup"><span data-stu-id="5a454-116">To perform or "invoke" a method of an object, type a dot (.), the method name, and a set of parentheses "()".</span></span> <span data-ttu-id="5a454-117">Als de methode argumenten heeft, plaatst u de argument waarden tussen de haakjes.</span><span class="sxs-lookup"><span data-stu-id="5a454-117">If the method has arguments, place the argument values inside the parentheses.</span></span> <span data-ttu-id="5a454-118">De haakjes zijn vereist voor elke methode aanroep, zelfs wanneer er geen argumenten zijn.</span><span class="sxs-lookup"><span data-stu-id="5a454-118">The parentheses are required for every method call, even when there are no arguments.</span></span> <span data-ttu-id="5a454-119">Als de methode meerdere argumenten heeft, moeten ze worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="5a454-119">If the method takes multiple arguments, they should be separated by commas.</span></span>

<span data-ttu-id="5a454-120">Met de volgende opdracht wordt bijvoorbeeld de methode Kill van processen aangeroepen om het klad blok-proces op de computer te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="5a454-120">For example, the following command invokes the Kill method of processes to end the Notepad process on the computer.</span></span>

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

<span data-ttu-id="5a454-121">Dit voor beeld kan worden inge kort door de bovenstaande instructies te combi neren.</span><span class="sxs-lookup"><span data-stu-id="5a454-121">This example can be shortened by combining the above statements.</span></span>

```powershell
(Get-Process Notepad).Kill()
```

<span data-ttu-id="5a454-122">De `Get-Process` opdracht bevindt zich tussen haakjes om ervoor te zorgen dat deze wordt uitgevoerd voordat de Kill-methode wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="5a454-122">The `Get-Process` command is enclosed in parentheses to ensure that it runs before the Kill method is invoked.</span></span> <span data-ttu-id="5a454-123">De `Kill` methode wordt vervolgens aangeroepen voor het geretourneerde `Process` object.</span><span class="sxs-lookup"><span data-stu-id="5a454-123">The `Kill` method is then invoked on the returned `Process` object.</span></span>

<span data-ttu-id="5a454-124">Een andere zeer nuttige methode is de `Replace` methode van teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="5a454-124">Another very useful method is the `Replace` method of strings.</span></span> <span data-ttu-id="5a454-125">De `Replace` -methode vervangt tekst in een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="5a454-125">The `Replace` method, replaces text within a string.</span></span> <span data-ttu-id="5a454-126">In het onderstaande voor beeld kan de punt (.) direct na het einde van de teken reeks worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5a454-126">In the example below, the dot (.) can be placed immediately after the end quote of the string.</span></span>

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

<span data-ttu-id="5a454-127">Zoals in de vorige voor beelden wordt weer gegeven, kunt u een methode aanroepen voor een object dat u krijgt met behulp van een opdracht, een object in een variabele of alles wat resulteert in een object (bijvoorbeeld een teken reeks tussen aanhalings tekens).</span><span class="sxs-lookup"><span data-stu-id="5a454-127">As shown in the previous examples, you can invoke a method on an object that you get by using a command, an object in a variable, or anything that results in an object (like a string in quotes).</span></span>

<span data-ttu-id="5a454-128">Vanaf Power Shell 4,0 wordt de methode aanroep met behulp van dynamische methode namen ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5a454-128">Starting in PowerShell 4.0, method invocation by using dynamic method names is supported.</span></span>

### <a name="learning-about-methods"></a><span data-ttu-id="5a454-129">Leren over methoden</span><span class="sxs-lookup"><span data-stu-id="5a454-129">Learning about methods</span></span>

<span data-ttu-id="5a454-130">Als u definities van de methoden van een object wilt vinden, gaat u naar Help-onderwerp voor het object type in MSDN en zoekt u naar de pagina methoden.</span><span class="sxs-lookup"><span data-stu-id="5a454-130">To find definitions of the methods of an object, go to help topic for the object type in MSDN and look for its methods page.</span></span> <span data-ttu-id="5a454-131">De volgende pagina beschrijft bijvoorbeeld de methoden van proces objecten [System. Diagnostics. process](/dotnet/api/system.diagnostics.process#methods).</span><span class="sxs-lookup"><span data-stu-id="5a454-131">For example, the following page describes the methods of process objects [System.Diagnostics.Process](/dotnet/api/system.diagnostics.process#methods).</span></span>

<span data-ttu-id="5a454-132">U kunt de argumenten van een methode bepalen door de methode definitie te bekijken, zoals het syntaxis diagram van een Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a454-132">To determine the arguments of a method, review the method definition, which is like the syntax diagram of a PowerShell cmdlet.</span></span>

<span data-ttu-id="5a454-133">Een methode definitie kan een of meer methode-hand tekeningen hebben, zoals de parameter sets van Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5a454-133">A method definition might have one or more method signatures, which are like the parameter sets of PowerShell cmdlets.</span></span> <span data-ttu-id="5a454-134">De hand tekeningen bevatten alle geldige indelingen van opdrachten om de methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="5a454-134">The signatures show all of the valid formats of commands to invoke the method.</span></span>

<span data-ttu-id="5a454-135">De `CopyTo` methode van de `FileInfo` klasse bevat bijvoorbeeld de volgende twee hand tekeningen voor de methode:</span><span class="sxs-lookup"><span data-stu-id="5a454-135">For example, the `CopyTo` method of the `FileInfo` class contains the following two method signatures:</span></span>

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

<span data-ttu-id="5a454-136">Bij de eerste hand tekening van de methode wordt de naam van het doel bestand (en een pad) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a454-136">The first method signature takes the destination file name (and a path).</span></span> <span data-ttu-id="5a454-137">In het volgende voor beeld wordt de eerste `CopyTo` methode gebruikt om het `Final.txt` bestand naar de map te kopiëren `C:\Bin` .</span><span class="sxs-lookup"><span data-stu-id="5a454-137">The following example uses the first `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> <span data-ttu-id="5a454-138">In tegens telling tot de _argument_ modus van Power shell, worden object methoden uitgevoerd in de _expressie_ modus, een Pass-Through-bewerking naar het .NET Framework waarin Power shell is gebouwd.</span><span class="sxs-lookup"><span data-stu-id="5a454-138">Unlike PowerShell's _argument_ mode, object methods execute in _expression_ mode, which is a pass-through to the .NET framework that PowerShell is built on.</span></span> <span data-ttu-id="5a454-139">In _expressie_ modus **bareword** argumenten (teken reeksen zonder aanhalings tekens) zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="5a454-139">In _expression_ mode **bareword** arguments (unquoted strings) are not allowed.</span></span> <span data-ttu-id="5a454-140">U kunt dit verschil zien wanneer u een pad gebruikt als een para meter, vergeleken met het pad als een argument.</span><span class="sxs-lookup"><span data-stu-id="5a454-140">You can see this difference when using a the path as a parameter, versus the path as an argument.</span></span> <span data-ttu-id="5a454-141">Meer informatie over het parseren van modi vindt u in [about_Parsing](about_Parsing.md)</span><span class="sxs-lookup"><span data-stu-id="5a454-141">You can read more about parsing modes in [about_Parsing](about_Parsing.md)</span></span>

<span data-ttu-id="5a454-142">De tweede methode handtekening neemt de naam van het doel bestand en een Booleaanse waarde die bepaalt of het doel bestand moet worden overschreven als het al bestaat.</span><span class="sxs-lookup"><span data-stu-id="5a454-142">The second method signature takes a destination file name and a Boolean value that determines whether the destination file should be overwritten, if it already exists.</span></span>

<span data-ttu-id="5a454-143">In het volgende voor beeld wordt de tweede `CopyTo` methode gebruikt om het `Final.txt` bestand naar de map te kopiëren `C:\Bin` en om bestaande bestanden te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="5a454-143">The following example uses the second `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory, and to overwrite existing files.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a><span data-ttu-id="5a454-144">Methoden van scalaire objecten en verzamelingen</span><span class="sxs-lookup"><span data-stu-id="5a454-144">Methods of Scalar objects and Collections</span></span>

<span data-ttu-id="5a454-145">De methoden van een object (' scalair ') van een bepaald type zijn vaak anders dan de methoden van een verzameling objecten van hetzelfde type.</span><span class="sxs-lookup"><span data-stu-id="5a454-145">The methods of one ("scalar") object of a particular type are often different from the methods of a collection of objects of the same type.</span></span>

<span data-ttu-id="5a454-146">Elk proces heeft bijvoorbeeld een `Kill` methode, maar een verzameling processen heeft geen Kill-methode.</span><span class="sxs-lookup"><span data-stu-id="5a454-146">For example, every process has a `Kill` method, but a collection of processes does not have a Kill method.</span></span>

<span data-ttu-id="5a454-147">Vanaf Power Shell 3,0 probeert Power shell script fouten te voor komen die het resultaat zijn van de verschillende methoden van scalaire objecten en verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="5a454-147">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing methods of scalar objects and collections.</span></span>

<span data-ttu-id="5a454-148">Als u een verzameling verzendt, maar een methode aanvraagt die alleen voor één (' scalaire ') objecten bestaat, roept Power shell de methode aan voor elk object in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="5a454-148">If you submit a collection, but request a method that exists only on single ("scalar") objects, PowerShell invokes the method on every object in the collection.</span></span>

<span data-ttu-id="5a454-149">Als de methode bestaat voor de afzonderlijke objecten en op de verzameling, wordt alleen de methode van de verzameling aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="5a454-149">If the method exists on the individual objects and on the collection, only the collection's method is invoked.</span></span>

<span data-ttu-id="5a454-150">Deze functie werkt ook voor eigenschappen van scalaire objecten en verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="5a454-150">This feature also works on properties of scalar objects and collections.</span></span> <span data-ttu-id="5a454-151">Zie [about_Properties](about_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a454-151">For more information, see [about_Properties](about_Properties.md).</span></span>

### <a name="examples"></a><span data-ttu-id="5a454-152">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="5a454-152">Examples</span></span>

<span data-ttu-id="5a454-153">In het volgende voor beeld wordt de methode **Kill** van afzonderlijke proces objecten in een verzameling objecten uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5a454-153">The following example runs the **Kill** method of individual process objects in a collection of objects.</span></span>

<span data-ttu-id="5a454-154">Met de eerste opdracht worden drie exemplaren van het klad blok-proces gestart.</span><span class="sxs-lookup"><span data-stu-id="5a454-154">The first command starts three instances of the Notepad process.</span></span> <span data-ttu-id="5a454-155">`Get-Process` Hiermee haalt u alle drie de exemplaren van het klad blok-proces en slaat u deze op in de `$p` variabele.</span><span class="sxs-lookup"><span data-stu-id="5a454-155">`Get-Process` gets all three instance of the Notepad process and saves them in the `$p` variable.</span></span>

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

<span data-ttu-id="5a454-156">Met de volgende opdracht wordt de methode **Kill** uitgevoerd voor alle drie de processen in de `$p` variabele.</span><span class="sxs-lookup"><span data-stu-id="5a454-156">The next command runs the **Kill** method on all three processes in the `$p` variable.</span></span> <span data-ttu-id="5a454-157">Deze opdracht werkt ook als een verzameling processen geen `Kill` methode heeft.</span><span class="sxs-lookup"><span data-stu-id="5a454-157">This command works even though a collection of processes does not have a `Kill` method.</span></span>

```powershell
$p.Kill()
Get-Process Notepad
```

<span data-ttu-id="5a454-158">De `Get-Process` opdracht bevestigt dat de `Kill` methode heeft gewerkt.</span><span class="sxs-lookup"><span data-stu-id="5a454-158">The `Get-Process` command confirms that the `Kill` method worked.</span></span>

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

<span data-ttu-id="5a454-159">Dit voor beeld is functioneel equivalent aan het gebruik `Foreach-Object` van de cmdlet om de methode uit te voeren voor elk object in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="5a454-159">This example is functionally equivalent to using the `Foreach-Object` cmdlet to run the method on each object in the collection.</span></span>

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a><span data-ttu-id="5a454-160">ForEach en where-methoden</span><span class="sxs-lookup"><span data-stu-id="5a454-160">ForEach and Where methods</span></span>

<span data-ttu-id="5a454-161">Vanaf Power Shell 4,0 wordt verzamelings filtering met behulp van een methode syntaxis ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5a454-161">Beginning in PowerShell 4.0, collection filtering by using a method syntax is supported.</span></span> <span data-ttu-id="5a454-162">Hierdoor kunnen twee nieuwe methoden worden gebruikt voor het verwerken van verzamelingen `ForEach` en `Where` .</span><span class="sxs-lookup"><span data-stu-id="5a454-162">This allows use of two new methods when dealing with collections `ForEach` and `Where`.</span></span>

<span data-ttu-id="5a454-163">Meer informatie over deze methoden vindt u in [about_arrays](about_arrays.md)</span><span class="sxs-lookup"><span data-stu-id="5a454-163">You can read more about these methods in [about_arrays](about_arrays.md)</span></span>

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a><span data-ttu-id="5a454-164">Aanroepen van een specifieke methode wanneer meerdere Overloads bestaan</span><span class="sxs-lookup"><span data-stu-id="5a454-164">Calling a specific method when multiple overloads exist</span></span>

<span data-ttu-id="5a454-165">Houd rekening met het volgende scenario bij het aanroepen van .NET-methoden.</span><span class="sxs-lookup"><span data-stu-id="5a454-165">Consider the following scenario when calling .NET methods.</span></span> <span data-ttu-id="5a454-166">Als een methode een object aanneemt, maar een overbelasting heeft via een interface die een meer specifiek type heeft, kiest Power shell de methode die het object accepteert, tenzij u het expliciet naar die interface hebt gecast.</span><span class="sxs-lookup"><span data-stu-id="5a454-166">If a method takes an object but has an overload via an interface taking a more specific type, PowerShell chooses the method that accepts the object unless you explicitly cast it to that interface.</span></span>

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

<span data-ttu-id="5a454-167">In dit voor beeld is de minder specifieke `object` overbelasting van de **balk** methode gekozen.</span><span class="sxs-lookup"><span data-stu-id="5a454-167">In this example the less specific `object` overload of the **Bar** method was chosen.</span></span>

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

<span data-ttu-id="5a454-168">In dit voor beeld geven we de methode voor de interface **IFoo** om de meer specifieke overbelasting van de methode **Bar** te selecteren.</span><span class="sxs-lookup"><span data-stu-id="5a454-168">In this example we cast the method to the interface **IFoo** to select the more specific overload of the **Bar** method.</span></span>

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a><span data-ttu-id="5a454-169">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5a454-169">See Also</span></span>

[<span data-ttu-id="5a454-170">about_Objects</span><span class="sxs-lookup"><span data-stu-id="5a454-170">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="5a454-171">about_Properties</span><span class="sxs-lookup"><span data-stu-id="5a454-171">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="5a454-172">Get-member</span><span class="sxs-lookup"><span data-stu-id="5a454-172">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
