---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: 9a51c97def7cddf45c391ed91ff67ad97fbedf77
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2020
ms.locfileid: "93251909"
---
# <span data-ttu-id="1aefc-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="1aefc-103">Add-Type</span></span>

## <span data-ttu-id="1aefc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1aefc-104">SYNOPSIS</span></span>
<span data-ttu-id="1aefc-105">Hiermee voegt u een Microsoft .NET kern klasse toe aan een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-105">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="1aefc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1aefc-106">SYNTAX</span></span>

### <span data-ttu-id="1aefc-107">FromSource (standaard)</span><span class="sxs-lookup"><span data-stu-id="1aefc-107">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1aefc-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="1aefc-108">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1aefc-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="1aefc-109">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1aefc-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1aefc-110">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1aefc-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="1aefc-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="1aefc-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1aefc-112">DESCRIPTION</span></span>

<span data-ttu-id="1aefc-113">`Add-Type`Met de cmdlet kunt u een Microsoft .net kern klasse definiëren in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="1aefc-114">U kunt vervolgens objecten instantiëren met behulp van de `New-Object` -cmdlet en de objecten gebruiken op dezelfde manier als u een .net core-object zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="1aefc-115">Als u een `Add-Type` opdracht aan uw Power shell-profiel toevoegt, is de klasse beschikbaar in alle Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="1aefc-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="1aefc-116">U kunt het type opgeven door een bestaande assembly-of broncode bestand op te geven, of u kunt de bron code inline opgeven of in een variabele opslaan.</span><span class="sxs-lookup"><span data-stu-id="1aefc-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="1aefc-117">U kunt zelfs een methode opgeven en `Add-Type` de klasse definiëren en genereren.</span><span class="sxs-lookup"><span data-stu-id="1aefc-117">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="1aefc-118">In Windows kunt u deze functie gebruiken om aanroepen van platform Invoke (P/Invoke) aan onbeheerde functies in Power shell te maken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="1aefc-119">Als u de bron code opgeeft, `Add-Type` compileert de opgegeven bron code en genereert een assembly in het geheugen die de nieuwe .net-kern typen bevat.</span><span class="sxs-lookup"><span data-stu-id="1aefc-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="1aefc-120">U kunt de para meters van gebruiken `Add-Type` om een alternatieve taal en een andere compiler op te geven, C# is de standaard opties voor compiler, assembly-afhankelijkheden, de klasse-naam ruimte, de namen van het type en de resulterende assembly.</span><span class="sxs-lookup"><span data-stu-id="1aefc-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

## <span data-ttu-id="1aefc-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1aefc-121">EXAMPLES</span></span>

### <span data-ttu-id="1aefc-122">Voor beeld 1: een .NET-type toevoegen aan een sessie</span><span class="sxs-lookup"><span data-stu-id="1aefc-122">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="1aefc-123">In dit voor beeld wordt de klasse **BasicTest** toegevoegd aan de sessie door de bron code op te geven die is opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="1aefc-123">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="1aefc-124">De klasse **BasicTest** wordt gebruikt om gehele getallen toe te voegen, een object te maken en gehele getallen te vermenigvuldigen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-124">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

<span data-ttu-id="1aefc-125">De `$Source` variabele slaat de bron code voor de klasse op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-125">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="1aefc-126">Het type heeft een statische methode met de naam `Add` en een niet-statische methode met de naam `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-126">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="1aefc-127">De- `Add-Type` cmdlet voegt de klasse toe aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-127">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="1aefc-128">Omdat de inline-bron code wordt gebruikt, gebruikt de opdracht de para meter **TypeDefinition** om de code in de variabele op te geven `$Source` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-128">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="1aefc-129">De `Add` statische methode van de klasse **BasicTest** gebruikt de tekens met dubbele punt komma's ( `::` ) om een statisch lid van de klasse op te geven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-129">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="1aefc-130">De gehele getallen worden toegevoegd en de som wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-130">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="1aefc-131">`New-Object`Met de cmdlet wordt een instantie van de klasse **BasicTest** geïnstantieerd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-131">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="1aefc-132">Het nieuwe object wordt opgeslagen in de `$BasicTestObject` variabele.</span><span class="sxs-lookup"><span data-stu-id="1aefc-132">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="1aefc-133">`$BasicTestObject` maakt gebruik van de- `Multiply` methode.</span><span class="sxs-lookup"><span data-stu-id="1aefc-133">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="1aefc-134">De gehele getallen worden vermenigvuldigd en het product wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-134">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="1aefc-135">Voor beeld 2: een toegevoegd type onderzoeken</span><span class="sxs-lookup"><span data-stu-id="1aefc-135">Example 2: Examine an added type</span></span>

<span data-ttu-id="1aefc-136">In dit voor beeld wordt de `Get-Member` cmdlet gebruikt om de objecten te onderzoeken die de `Add-Type` `New-Object` cmdlets en zijn gemaakt in **voor beeld 1**.</span><span class="sxs-lookup"><span data-stu-id="1aefc-136">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

<span data-ttu-id="1aefc-137">Met de `Get-Member` cmdlet worden het type en de leden van de klasse **BasicTest** opgehaald die `Add-Type` aan de sessie zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-137">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="1aefc-138">De `Get-Member` opdracht toont aan dat het een **System. RuntimeType** -object is, dat is afgeleid van de klasse **System. object** .</span><span class="sxs-lookup"><span data-stu-id="1aefc-138">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="1aefc-139">Met de `Get-Member` **statische** para meter worden de statische eigenschappen en methoden van de klasse **BasicTest** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1aefc-139">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="1aefc-140">In de uitvoer ziet u dat de- `Add` methode is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-140">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="1aefc-141">De `Get-Member` cmdlet haalt de leden van het object op dat is opgeslagen in de `$BasicTestObject` variabele.</span><span class="sxs-lookup"><span data-stu-id="1aefc-141">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="1aefc-142">`$BasicTestObject` is gemaakt met behulp van de `New-Object` cmdlet met de **BasicTest** -klasse.</span><span class="sxs-lookup"><span data-stu-id="1aefc-142">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="1aefc-143">De uitvoer laat zien dat de waarde van de `$BasicTestObject` variabele een exemplaar van de klasse **BasicTest** is en dat het een lid bevat met de naam `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-143">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="1aefc-144">Voor beeld 3: typen uit een assembly toevoegen</span><span class="sxs-lookup"><span data-stu-id="1aefc-144">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="1aefc-145">In dit voor beeld worden de klassen van de `NJsonSchema.dll` Assembly toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-145">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="1aefc-146">`Set-Location` maakt gebruik van de para meter **Path** om de variabele op te geven `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-146">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="1aefc-147">De variabele verwijst naar de Power shell-installatie directory waar het DLL-bestand zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-147">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="1aefc-148">De `$AccType` variabele slaat een object op dat is gemaakt met de `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1aefc-148">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="1aefc-149">`Add-Type` de **assemblyname** -para meter wordt gebruikt om de naam van de assembly op te geven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-149">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="1aefc-150">`*`Met het Joker teken sterretje () kunt u de juiste assembly ophalen, zelfs wanneer u niet zeker bent van de naam of de spelling.</span><span class="sxs-lookup"><span data-stu-id="1aefc-150">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="1aefc-151">De para meter **PassThru** genereert objecten die de klassen vertegenwoordigen die aan de sessie worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-151">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="1aefc-152">Voor beeld 4: systeem eigen Windows-Api's aanroepen</span><span class="sxs-lookup"><span data-stu-id="1aefc-152">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="1aefc-153">In dit voor beeld ziet u hoe u systeem eigen Windows-Api's aanroept in Power shell.</span><span class="sxs-lookup"><span data-stu-id="1aefc-153">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="1aefc-154">`Add-Type` maakt gebruik van het mechanisme voor het aanroepen van het platform (P/Invoke) om een functie in `User32.dll` vanuit Power shell aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-154">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="1aefc-155">Dit voor beeld werkt alleen op computers met het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="1aefc-155">This example only works on computers running the Windows operating system.</span></span>

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

<span data-ttu-id="1aefc-156">De `$Signature` variabele slaat de C#-hand tekening van de `ShowWindowAsync` functie op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-156">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="1aefc-157">Om ervoor te zorgen dat de resulterende methode zichtbaar is in een Power shell-sessie, `public` is het sleutel woord toegevoegd aan de standaard handtekening.</span><span class="sxs-lookup"><span data-stu-id="1aefc-157">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="1aefc-158">Zie de [functie ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-158">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="1aefc-159">De `$ShowWindowAsync` variabele slaat het object op dat door de `Add-Type` para meter **PassThru** is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-159">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="1aefc-160">De `Add-Type` cmdlet voegt de `ShowWindowAsync` functie als een statische methode toe aan de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-160">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="1aefc-161">De opdracht gebruikt de para meter **MemberDefinition** om de definitie van de methode op te geven die is opgeslagen in de `$Signature` variabele.</span><span class="sxs-lookup"><span data-stu-id="1aefc-161">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="1aefc-162">De opdracht maakt gebruik van de para meters **naam** en naam **ruimte** om een naam en naam ruimte voor de klasse op te geven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-162">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="1aefc-163">De para meter **PassThru** genereert een object dat de typen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-163">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="1aefc-164">De nieuwe `ShowWindowAsync` statische methode wordt gebruikt in de opdrachten om de Power shell-console te minimaliseren en te herstellen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-164">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="1aefc-165">De methode heeft twee para meters: de venster ingang en een geheel getal dat aangeeft hoe het venster wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-165">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="1aefc-166">Om de Power shell-console te minimaliseren, `ShowWindowAsync` gebruikt de `Get-Process` cmdlet met de `$PID` Automatische variabele om het proces op te halen dat als host fungeert voor de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-166">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="1aefc-167">Vervolgens wordt de eigenschap **MainWindowHandle** van het huidige proces en een waarde van gebruikt `2` die de waarde vertegenwoordigt `SW_MINIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-167">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="1aefc-168">Als u het venster wilt herstellen, `ShowWindowAsync` gebruikt u een waarde van `4` voor de venster positie, waarmee de waarde wordt aangeduid `SW_RESTORE` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-168">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="1aefc-169">Gebruik de waarde van dat vertegenwoordigt om het venster te maximaliseren `3` `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-169">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="1aefc-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1aefc-170">PARAMETERS</span></span>

### <span data-ttu-id="1aefc-171">-Assemblyname</span><span class="sxs-lookup"><span data-stu-id="1aefc-171">-AssemblyName</span></span>

<span data-ttu-id="1aefc-172">Hiermee geeft u de naam op van een assembly die de typen bevat.</span><span class="sxs-lookup"><span data-stu-id="1aefc-172">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="1aefc-173">`Add-Type` neemt de typen van de opgegeven assembly op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-173">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="1aefc-174">Deze para meter is vereist wanneer u typen maakt op basis van de naam van een assembly.</span><span class="sxs-lookup"><span data-stu-id="1aefc-174">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="1aefc-175">Voer de volledige of eenvoudige naam in, ook wel bekend als de gedeeltelijke naam, van een assembly.</span><span class="sxs-lookup"><span data-stu-id="1aefc-175">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="1aefc-176">Joker tekens zijn toegestaan in de naam van de assembly.</span><span class="sxs-lookup"><span data-stu-id="1aefc-176">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="1aefc-177">Als u een eenvoudige of gedeeltelijke naam opgeeft, wordt `Add-Type` deze omgezet in de volledige naam, waarna de volledige naam wordt gebruikt om de assembly te laden.</span><span class="sxs-lookup"><span data-stu-id="1aefc-177">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="1aefc-178">Deze para meter accepteert geen pad of bestands naam.</span><span class="sxs-lookup"><span data-stu-id="1aefc-178">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="1aefc-179">Als u het pad naar het bestand van de assembly-Dynamic-Link Library (DLL) wilt invoeren, gebruikt u de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="1aefc-179">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1aefc-180">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="1aefc-180">-CompilerOptions</span></span>

<span data-ttu-id="1aefc-181">Hiermee geeft u de opties voor de bron code compiler op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-181">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="1aefc-182">Deze opties worden zonder revisie naar de compiler verzonden.</span><span class="sxs-lookup"><span data-stu-id="1aefc-182">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="1aefc-183">Met deze para meter kunt u de compiler omleiden om een uitvoerbaar bestand te genereren, resources in te sluiten of opdracht regel opties in te stellen, zoals de `/unsafe` optie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-183">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="1aefc-184">U kunt de para meters **CompilerOptions** en **ReferencedAssemblies** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-184">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-185">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="1aefc-185">-IgnoreWarnings</span></span>

<span data-ttu-id="1aefc-186">Waarschuwingen voor compileren worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-186">Ignores compiler warnings.</span></span> <span data-ttu-id="1aefc-187">Gebruik deze para meter om te voor komen dat `Add-Type` waarschuwingen van het Compileer programma worden verwerkt als fouten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-187">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-188">-Taal</span><span class="sxs-lookup"><span data-stu-id="1aefc-188">-Language</span></span>

<span data-ttu-id="1aefc-189">Hiermee geeft u de taal op die wordt gebruikt in de bron code.</span><span class="sxs-lookup"><span data-stu-id="1aefc-189">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="1aefc-190">De acceptabele waarde voor deze para meter is **csharp**.</span><span class="sxs-lookup"><span data-stu-id="1aefc-190">The acceptable value for this parameter is **CSharp**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-191">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1aefc-191">-LiteralPath</span></span>

<span data-ttu-id="1aefc-192">Hiermee geeft u het pad op naar broncode bestanden of assembly-DLL-bestanden die de typen bevatten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-192">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="1aefc-193">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-193">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="1aefc-194">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="1aefc-194">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1aefc-195">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="1aefc-195">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1aefc-196">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-196">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-197">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="1aefc-197">-MemberDefinition</span></span>

<span data-ttu-id="1aefc-198">Hiermee geeft u nieuwe eigenschappen of methoden voor de klasse op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-198">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="1aefc-199">`Add-Type` genereert de sjabloon code die nodig is om de eigenschappen of methoden te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-199">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="1aefc-200">In Windows kunt u deze functie gebruiken om aanroepen van platform Invoke (P/Invoke) aan onbeheerde functies in Power shell te maken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-200">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-201">-Name</span><span class="sxs-lookup"><span data-stu-id="1aefc-201">-Name</span></span>

<span data-ttu-id="1aefc-202">Hiermee geeft u de naam op van de klasse die u wilt maken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-202">Specifies the name of the class to create.</span></span> <span data-ttu-id="1aefc-203">Deze para meter is vereist voor het genereren van een type uit een definitie van een lid.</span><span class="sxs-lookup"><span data-stu-id="1aefc-203">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="1aefc-204">De type naam en naam ruimte moeten uniek zijn binnen een sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-204">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="1aefc-205">U kunt een type niet verwijderen of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-205">You can't unload a type or change it.</span></span>
<span data-ttu-id="1aefc-206">Als u de code voor een type wilt wijzigen, moet u de naam wijzigen of een nieuwe Power shell-sessie starten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-206">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="1aefc-207">Anders mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1aefc-207">Otherwise, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-208">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="1aefc-208">-Namespace</span></span>

<span data-ttu-id="1aefc-209">Hiermee geeft u een naam ruimte voor het type op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-209">Specifies a namespace for the type.</span></span>

<span data-ttu-id="1aefc-210">Als deze para meter niet is opgenomen in de opdracht, wordt het type gemaakt in de naam ruimte **micro soft. Power shell. commands. AddType. AutoGeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="1aefc-210">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="1aefc-211">Als de para meter in de opdracht wordt opgenomen met een lege teken reeks waarde of een waarde van `$Null` , wordt het type gegenereerd in de globale naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="1aefc-211">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-212">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="1aefc-212">-OutputAssembly</span></span>

<span data-ttu-id="1aefc-213">Hiermee wordt een DLL-bestand voor de assembly gegenereerd met de opgegeven naam op de locatie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-213">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="1aefc-214">Voer een optioneel pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="1aefc-214">Enter an optional path and filename.</span></span> <span data-ttu-id="1aefc-215">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1aefc-215">Wildcard characters are permitted.</span></span> <span data-ttu-id="1aefc-216">`Add-Type`De assembly wordt standaard alleen in het geheugen gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-216">By default, `Add-Type` generates the assembly only in memory.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1aefc-217">-Output type</span><span class="sxs-lookup"><span data-stu-id="1aefc-217">-OutputType</span></span>

<span data-ttu-id="1aefc-218">Hiermee geeft u het uitvoer type van de uitvoer-assembly op.</span><span class="sxs-lookup"><span data-stu-id="1aefc-218">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="1aefc-219">Standaard is geen uitvoer type opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1aefc-219">By default, no output type is specified.</span></span> <span data-ttu-id="1aefc-220">Deze para meter is alleen geldig wanneer een uitvoer-assembly is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1aefc-220">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="1aefc-221">Zie [OutputAssemblyType Enumeration (Engelstalig)](/dotnet/api/microsoft.powershell.commands.outputassemblytype)voor meer informatie over de waarden.</span><span class="sxs-lookup"><span data-stu-id="1aefc-221">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="1aefc-222">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1aefc-222">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1aefc-223">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="1aefc-223">ConsoleApplication</span></span>
- <span data-ttu-id="1aefc-224">Bibliotheek</span><span class="sxs-lookup"><span data-stu-id="1aefc-224">Library</span></span>
- <span data-ttu-id="1aefc-225">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="1aefc-225">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1aefc-226">De `ConsoleApplication` waarden en en `WindowsApplication` mogen niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-226">The `ConsoleApplication` and `WindowsApplication` values don't produce working output and should not be used.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-227">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1aefc-227">-PassThru</span></span>

<span data-ttu-id="1aefc-228">Retourneert een **System. runtime** -object dat de typen vertegenwoordigt die zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-228">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="1aefc-229">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1aefc-229">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-230">-Path</span><span class="sxs-lookup"><span data-stu-id="1aefc-230">-Path</span></span>

<span data-ttu-id="1aefc-231">Hiermee geeft u het pad op naar broncode bestanden of assembly-DLL-bestanden die de typen bevatten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-231">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="1aefc-232">Als u bron code bestanden verzendt, `Add-Type` compileert de code in de bestanden en maakt een assembly in het geheugen van de typen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-232">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="1aefc-233">De bestands extensie die in de waarde van het **pad** is opgegeven, bepaalt de compiler die `Add-Type` gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-233">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="1aefc-234">Als u een assembly-bestand verzendt, `Add-Type` neemt de typen van de assembly toe.</span><span class="sxs-lookup"><span data-stu-id="1aefc-234">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="1aefc-235">Als u een assembly in het geheugen of de Global Assembly Cache wilt opgeven, gebruikt u de **assemblyname** -para meter.</span><span class="sxs-lookup"><span data-stu-id="1aefc-235">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-236">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="1aefc-236">-ReferencedAssemblies</span></span>

<span data-ttu-id="1aefc-237">Hiermee geeft u de assembly's op waarvan het type afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="1aefc-237">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="1aefc-238">`Add-Type`Verwijzingen en zijn standaard `System.dll` `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-238">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="1aefc-239">In de assembly's die u opgeeft met behulp van deze para meter wordt een aanvulling op de standaard-assembly's verwezen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-239">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="1aefc-240">Vanaf Power shell 6 bevat **ReferencedAssemblies** niet de standaard-.net-assembly's.</span><span class="sxs-lookup"><span data-stu-id="1aefc-240">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="1aefc-241">U moet in de waarde die wordt door gegeven aan deze para meter een specifieke verwijzing naar deze bevatten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-241">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="1aefc-242">U kunt de para meters **CompilerOptions** en **ReferencedAssemblies** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-242">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-243">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="1aefc-243">-TypeDefinition</span></span>

<span data-ttu-id="1aefc-244">Hiermee geeft u de bron code die de type definities bevat.</span><span class="sxs-lookup"><span data-stu-id="1aefc-244">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="1aefc-245">Voer de bron code in een teken reeks of hier in, of voer een variabele in die de bron code bevat.</span><span class="sxs-lookup"><span data-stu-id="1aefc-245">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="1aefc-246">Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-246">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="1aefc-247">Neem een naam ruimte declaratie op in uw type definitie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-247">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="1aefc-248">Als u de naam ruimte declaratie weglaat, kan uw type dezelfde naam hebben als een ander type of de snelkoppeling voor een ander type, waardoor een onbedoelde overschrijving wordt veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-248">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="1aefc-249">Als u bijvoorbeeld een type met de naam **Exception** definieert, zullen scripts die **uitzonde ring** gebruiken als de snelkoppeling voor **System. Exception** , mislukken.</span><span class="sxs-lookup"><span data-stu-id="1aefc-249">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-250">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="1aefc-250">-UsingNamespace</span></span>

<span data-ttu-id="1aefc-251">Hiermee geeft u andere naam ruimten op die voor de klasse zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="1aefc-251">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="1aefc-252">Dit is vergelijkbaar met het sleutel woord C# `Using` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-252">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="1aefc-253">Maakt standaard `Add-Type` een verwijzing naar de **systeem** naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="1aefc-253">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="1aefc-254">Wanneer de para meter **MemberDefinition** wordt gebruikt, wordt `Add-Type` standaard ook naar de **System. runtime. InteropServices** -naam ruimte verwezen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-254">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="1aefc-255">Er wordt verwezen naar de naam ruimten die u toevoegt met behulp van de para meter **UsingNamespace** , naast de standaard naam ruimten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-255">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1aefc-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1aefc-256">CommonParameters</span></span>

<span data-ttu-id="1aefc-257">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1aefc-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1aefc-258">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1aefc-259">INVOER</span><span class="sxs-lookup"><span data-stu-id="1aefc-259">INPUTS</span></span>

### <span data-ttu-id="1aefc-260">Geen</span><span class="sxs-lookup"><span data-stu-id="1aefc-260">None</span></span>

<span data-ttu-id="1aefc-261">U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-261">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="1aefc-262">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1aefc-262">OUTPUTS</span></span>

### <span data-ttu-id="1aefc-263">Geen of System. type</span><span class="sxs-lookup"><span data-stu-id="1aefc-263">None or System.Type</span></span>

<span data-ttu-id="1aefc-264">Wanneer u de para meter **PassThru** gebruikt, `Add-Type` retourneert een **System. type** -object dat het nieuwe type vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1aefc-264">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="1aefc-265">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1aefc-265">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="1aefc-266">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1aefc-266">NOTES</span></span>

<span data-ttu-id="1aefc-267">De typen die u toevoegt, zijn alleen aanwezig in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-267">The types that you add exist only in the current session.</span></span> <span data-ttu-id="1aefc-268">Als u de typen in alle sessies wilt gebruiken, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="1aefc-268">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="1aefc-269">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie over het profiel.</span><span class="sxs-lookup"><span data-stu-id="1aefc-269">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="1aefc-270">Type namen en naam ruimten moeten uniek zijn binnen een sessie.</span><span class="sxs-lookup"><span data-stu-id="1aefc-270">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="1aefc-271">U kunt een type niet verwijderen of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-271">You can't unload a type or change it.</span></span> <span data-ttu-id="1aefc-272">Als u de code voor een type moet wijzigen, moet u de naam wijzigen of een nieuwe Power shell-sessie starten.</span><span class="sxs-lookup"><span data-stu-id="1aefc-272">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="1aefc-273">Anders mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1aefc-273">Otherwise, the command fails.</span></span>

<span data-ttu-id="1aefc-274">In Windows Power shell (versie 5,1 en lager) moet u gebruiken `Add-Type` voor alles wat nog niet is geladen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-274">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="1aefc-275">Dit geldt meestal voor assembly's die zijn gevonden in de GAC (Global assembly cache).</span><span class="sxs-lookup"><span data-stu-id="1aefc-275">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="1aefc-276">In Power shell 6 en hoger is er geen GAC, waardoor Power shell zijn eigen assembly's installeert in `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="1aefc-276">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="1aefc-277">Deze assembly's worden automatisch op aanvraag geladen, dus u hoeft ze niet te gebruiken `Add-Type` om ze te laden.</span><span class="sxs-lookup"><span data-stu-id="1aefc-277">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="1aefc-278">Het gebruik van `Add-Type` is echter nog steeds toegestaan om scripts impliciet compatibel te maken met elke versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="1aefc-278">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="1aefc-279">Assembly's in de GAC kunnen worden geladen op type naam, in plaats van op pad.</span><span class="sxs-lookup"><span data-stu-id="1aefc-279">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="1aefc-280">Voor het laden van assembly's vanuit een wille keurig pad is vereist `Add-Type` , omdat deze assembly's niet automatisch kunnen worden geladen.</span><span class="sxs-lookup"><span data-stu-id="1aefc-280">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="1aefc-281">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1aefc-281">RELATED LINKS</span></span>

[<span data-ttu-id="1aefc-282">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1aefc-282">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="1aefc-283">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1aefc-283">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="1aefc-284">Lid toevoegen</span><span class="sxs-lookup"><span data-stu-id="1aefc-284">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="1aefc-285">New-Object</span><span class="sxs-lookup"><span data-stu-id="1aefc-285">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="1aefc-286">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="1aefc-286">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="1aefc-287">Platform aanroepen (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="1aefc-287">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="1aefc-288">Where-object</span><span class="sxs-lookup"><span data-stu-id="1aefc-288">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
