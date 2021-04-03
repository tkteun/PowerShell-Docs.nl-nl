---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: e6fa1d63f2c748c590920db0cbfdf241e0646a73
ms.sourcegitcommit: c91f79576bc54e162bcc7adf78026417b2776687
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274252"
---
# <span data-ttu-id="1218e-102">Add-Type</span><span class="sxs-lookup"><span data-stu-id="1218e-102">Add-Type</span></span>

## <span data-ttu-id="1218e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1218e-103">SYNOPSIS</span></span>
<span data-ttu-id="1218e-104">Hiermee wordt een Microsoft .NET klasse toegevoegd aan een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-104">Adds a Microsoft .NET class to a PowerShell session.</span></span>

## <span data-ttu-id="1218e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1218e-105">SYNTAX</span></span>

### <span data-ttu-id="1218e-106">FromSource (standaard)</span><span class="sxs-lookup"><span data-stu-id="1218e-106">FromSource (Default)</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [<CommonParameters>]
```

### <span data-ttu-id="1218e-107">FromMember</span><span class="sxs-lookup"><span data-stu-id="1218e-107">FromMember</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>] [-UsingNamespace <String[]>]
 [-Language <Language>] [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="1218e-108">FromPath</span><span class="sxs-lookup"><span data-stu-id="1218e-108">FromPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] [-Path] <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="1218e-109">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1218e-109">FromLiteralPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] -LiteralPath <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="1218e-110">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="1218e-110">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

## <span data-ttu-id="1218e-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1218e-111">DESCRIPTION</span></span>

<span data-ttu-id="1218e-112">`Add-Type`Met de cmdlet kunt u een Microsoft .NET Framework-klasse definiëren in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-112">The `Add-Type` cmdlet lets you define a Microsoft .NET Framework class in your PowerShell session.</span></span>
<span data-ttu-id="1218e-113">U kunt vervolgens objecten instantiëren met behulp van de `New-Object` cmdlet en de objecten op dezelfde manier gebruiken als een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="1218e-113">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Framework object.</span></span> <span data-ttu-id="1218e-114">Als u een `Add-Type` opdracht aan uw Power shell-profiel toevoegt, is de klasse beschikbaar in alle Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="1218e-114">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="1218e-115">U kunt het type opgeven door een bestaande assembly-of broncode bestand op te geven, of u kunt de bron code inline opgeven of in een variabele opslaan.</span><span class="sxs-lookup"><span data-stu-id="1218e-115">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="1218e-116">U kunt zelfs een methode opgeven en `Add-Type` de klasse definiëren en genereren.</span><span class="sxs-lookup"><span data-stu-id="1218e-116">You can even specify only a method and `Add-Type` will define and generate the class.</span></span> <span data-ttu-id="1218e-117">In Windows kunt u deze functie gebruiken om aanroepen van platform Invoke (P/Invoke) aan onbeheerde functies in Power shell te maken.</span><span class="sxs-lookup"><span data-stu-id="1218e-117">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="1218e-118">Als u de bron code opgeeft, `Add-Type` compileert de opgegeven bron code en genereert een assembly in het geheugen die de nieuwe .NET Framework typen bevat.</span><span class="sxs-lookup"><span data-stu-id="1218e-118">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Framework types.</span></span>

<span data-ttu-id="1218e-119">U kunt de para meters van gebruiken `Add-Type` om een alternatieve taal en een andere compiler op te geven, C# is de standaard opties voor compiler, assembly-afhankelijkheden, de klasse-naam ruimte, de namen van het type en de resulterende assembly.</span><span class="sxs-lookup"><span data-stu-id="1218e-119">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

## <span data-ttu-id="1218e-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1218e-120">EXAMPLES</span></span>

### <span data-ttu-id="1218e-121">Voor beeld 1: een .NET-type toevoegen aan een sessie</span><span class="sxs-lookup"><span data-stu-id="1218e-121">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="1218e-122">In dit voor beeld wordt de klasse **BasicTest** toegevoegd aan de sessie door de bron code op te geven die is opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="1218e-122">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="1218e-123">De klasse **BasicTest** wordt gebruikt om gehele getallen toe te voegen, een object te maken en gehele getallen te vermenigvuldigen.</span><span class="sxs-lookup"><span data-stu-id="1218e-123">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="1218e-124">De `$Source` variabele slaat de bron code voor de klasse op.</span><span class="sxs-lookup"><span data-stu-id="1218e-124">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="1218e-125">Het type heeft een statische methode met de naam `Add` en een niet-statische methode met de naam `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="1218e-125">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="1218e-126">De- `Add-Type` cmdlet voegt de klasse toe aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-126">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="1218e-127">Omdat de inline-bron code wordt gebruikt, gebruikt de opdracht de para meter **TypeDefinition** om de code in de variabele op te geven `$Source` .</span><span class="sxs-lookup"><span data-stu-id="1218e-127">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="1218e-128">De `Add` statische methode van de klasse **BasicTest** gebruikt de tekens met dubbele punt komma's ( `::` ) om een statisch lid van de klasse op te geven.</span><span class="sxs-lookup"><span data-stu-id="1218e-128">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="1218e-129">De gehele getallen worden toegevoegd en de som wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1218e-129">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="1218e-130">`New-Object`Met de cmdlet wordt een instantie van de klasse **BasicTest** geïnstantieerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-130">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="1218e-131">Het nieuwe object wordt opgeslagen in de `$BasicTestObject` variabele.</span><span class="sxs-lookup"><span data-stu-id="1218e-131">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="1218e-132">`$BasicTestObject` maakt gebruik van de- `Multiply` methode.</span><span class="sxs-lookup"><span data-stu-id="1218e-132">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="1218e-133">De gehele getallen worden vermenigvuldigd en het product wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1218e-133">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="1218e-134">Voor beeld 2: een toegevoegd type onderzoeken</span><span class="sxs-lookup"><span data-stu-id="1218e-134">Example 2: Examine an added type</span></span>

<span data-ttu-id="1218e-135">In dit voor beeld wordt de `Get-Member` cmdlet gebruikt om de objecten te onderzoeken die de `Add-Type` `New-Object` cmdlets en zijn gemaakt in **voor beeld 1**.</span><span class="sxs-lookup"><span data-stu-id="1218e-135">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1**.</span></span>

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

<span data-ttu-id="1218e-136">Met de `Get-Member` cmdlet worden het type en de leden van de klasse **BasicTest** opgehaald die `Add-Type` aan de sessie zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1218e-136">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="1218e-137">De `Get-Member` opdracht toont aan dat het een **System. RuntimeType** -object is, dat is afgeleid van de klasse **System. object** .</span><span class="sxs-lookup"><span data-stu-id="1218e-137">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="1218e-138">Met de `Get-Member` **statische** para meter worden de statische eigenschappen en methoden van de klasse **BasicTest** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1218e-138">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="1218e-139">In de uitvoer ziet u dat de- `Add` methode is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="1218e-139">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="1218e-140">De `Get-Member` cmdlet haalt de leden van het object op dat is opgeslagen in de `$BasicTestObject` variabele.</span><span class="sxs-lookup"><span data-stu-id="1218e-140">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="1218e-141">`$BasicTestObject` is gemaakt met behulp van de `New-Object` cmdlet met de **BasicTest** -klasse.</span><span class="sxs-lookup"><span data-stu-id="1218e-141">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="1218e-142">De uitvoer laat zien dat de waarde van de `$BasicTestObject` variabele een exemplaar van de klasse **BasicTest** is en dat het een lid bevat met de naam `Multiply` .</span><span class="sxs-lookup"><span data-stu-id="1218e-142">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="1218e-143">Voor beeld 3: typen uit een assembly toevoegen</span><span class="sxs-lookup"><span data-stu-id="1218e-143">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="1218e-144">In dit voor beeld worden de klassen van de `Accessibility.dll` Assembly toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-144">This example adds the classes from the `Accessibility.dll` assembly to the current session.</span></span>

```powershell
$AccType = Add-Type -AssemblyName "accessib*" -PassThru
```

<span data-ttu-id="1218e-145">De `$AccType` variabele slaat een object op dat is gemaakt met de `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1218e-145">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="1218e-146">`Add-Type` de **assemblyname** -para meter wordt gebruikt om de naam van de assembly op te geven.</span><span class="sxs-lookup"><span data-stu-id="1218e-146">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="1218e-147">`*`Met het Joker teken sterretje () kunt u de juiste assembly ophalen, zelfs wanneer u niet zeker bent van de naam of de spelling.</span><span class="sxs-lookup"><span data-stu-id="1218e-147">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="1218e-148">De para meter **PassThru** genereert objecten die de klassen vertegenwoordigen die aan de sessie worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1218e-148">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="1218e-149">Voor beeld 4: systeem eigen Windows-Api's aanroepen</span><span class="sxs-lookup"><span data-stu-id="1218e-149">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="1218e-150">In dit voor beeld ziet u hoe u systeem eigen Windows-Api's aanroept in Power shell.</span><span class="sxs-lookup"><span data-stu-id="1218e-150">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="1218e-151">`Add-Type` maakt gebruik van het mechanisme voor het aanroepen van het platform (P/Invoke) om een functie in `User32.dll` vanuit Power shell aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="1218e-151">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="1218e-152">Dit voor beeld werkt alleen op computers met het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="1218e-152">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="1218e-153">De `$Signature` variabele slaat de C#-hand tekening van de `ShowWindowAsync` functie op.</span><span class="sxs-lookup"><span data-stu-id="1218e-153">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="1218e-154">Om ervoor te zorgen dat de resulterende methode wordt weer gegeven in een Power shell-sessie, `public` is het sleutel woord toegevoegd aan de standaard handtekening.</span><span class="sxs-lookup"><span data-stu-id="1218e-154">To ensure that the resulting method will be visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="1218e-155">Zie de [functie ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1218e-155">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="1218e-156">De `$ShowWindowAsync` variabele slaat het object op dat door de `Add-Type` para meter **PassThru** is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1218e-156">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="1218e-157">De `Add-Type` cmdlet voegt de `ShowWindowAsync` functie als een statische methode toe aan de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-157">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="1218e-158">De opdracht gebruikt de para meter **MemberDefinition** om de definitie van de methode op te geven die is opgeslagen in de `$Signature` variabele.</span><span class="sxs-lookup"><span data-stu-id="1218e-158">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="1218e-159">De opdracht maakt gebruik van de para meters **naam** en naam **ruimte** om een naam en naam ruimte voor de klasse op te geven.</span><span class="sxs-lookup"><span data-stu-id="1218e-159">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="1218e-160">De para meter **PassThru** genereert een object dat de typen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1218e-160">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="1218e-161">De nieuwe `ShowWindowAsync` statische methode wordt gebruikt in de opdrachten om de Power shell-console te minimaliseren en te herstellen.</span><span class="sxs-lookup"><span data-stu-id="1218e-161">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="1218e-162">De methode heeft twee para meters: de venster ingang en een geheel getal dat aangeeft hoe het venster wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1218e-162">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="1218e-163">Om de Power shell-console te minimaliseren, `ShowWindowAsync` gebruikt de `Get-Process` cmdlet met de `$PID` Automatische variabele om het proces op te halen dat als host fungeert voor de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-163">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="1218e-164">Vervolgens wordt de eigenschap **MainWindowHandle** van het huidige proces en een waarde van gebruikt `2` die de waarde vertegenwoordigt `SW_MINIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="1218e-164">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="1218e-165">Als u het venster wilt herstellen, `ShowWindowAsync` gebruikt u een waarde van `4` voor de venster positie, waarmee de waarde wordt aangeduid `SW_RESTORE` .</span><span class="sxs-lookup"><span data-stu-id="1218e-165">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="1218e-166">Gebruik de waarde van dat vertegenwoordigt om het venster te maximaliseren `3` `SW_MAXIMIZE` .</span><span class="sxs-lookup"><span data-stu-id="1218e-166">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

### <span data-ttu-id="1218e-167">Voor beeld 5: een type toevoegen vanuit een Visual Basic-bestand</span><span class="sxs-lookup"><span data-stu-id="1218e-167">Example 5: Add a type from a Visual Basic file</span></span>

<span data-ttu-id="1218e-168">In dit voor beeld wordt de `Add-Type` cmdlet gebruikt om de **VBFromFile** -klasse die in het bestand is gedefinieerd, toe te voegen `Hello.vb` aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-168">This example uses the `Add-Type` cmdlet to add the **VBFromFile** class that's defined in the `Hello.vb` file to the current session.</span></span> <span data-ttu-id="1218e-169">De tekst van het `Hello.vb` bestand wordt weer gegeven in de uitvoer van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1218e-169">The text of the `Hello.vb` file is shown in the command output.</span></span>

```powershell
Add-Type -Path "C:\PS-Test\Hello.vb"
[VBFromFile]::SayHello(", World")

# From Hello.vb

Public Class VBFromFile
  Public Shared Function SayHello(sourceName As String) As String
    Dim myValue As String = "Hello"
    return myValue + sourceName
  End Function
End Class
```

```Output
Hello, World
```

<span data-ttu-id="1218e-170">`Add-Type` gebruikt de para meter **Path** om het bron bestand op te geven, `Hello.vb` en voegt het type toe dat in het bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-170">`Add-Type` uses the **Path** parameter to specify the source file, `Hello.vb`, and adds the type defined in the file.</span></span> <span data-ttu-id="1218e-171">De `SayHello` functie wordt aangeroepen als een statische methode van de **VBFromFile** -klasse.</span><span class="sxs-lookup"><span data-stu-id="1218e-171">The `SayHello` function is called as a static method of the **VBFromFile** class.</span></span>

### <span data-ttu-id="1218e-172">Voor beeld 6: een klasse met JScript.NET toevoegen</span><span class="sxs-lookup"><span data-stu-id="1218e-172">Example 6: Add a class with JScript.NET</span></span>

<span data-ttu-id="1218e-173">In dit voor beeld wordt JScript.NET gebruikt om een nieuwe klasse **FRectangle** in uw Power shell-sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="1218e-173">This example uses JScript.NET to create a new class, **FRectangle**, in your PowerShell session.</span></span>

```powershell
Add-Type @'
 class FRectangle {
   var Length : double;
   var Height : double;
   function Perimeter() : double {
       return (Length + Height) * 2; }
   function Area() : double {
       return Length * Height;  } }
'@ -Language JScript

$rect = [FRectangle]::new()
$rect
```

```Output
Length Height
------ ------
     0      0
```

### <span data-ttu-id="1218e-174">Voor beeld 7: een F #-compiler toevoegen</span><span class="sxs-lookup"><span data-stu-id="1218e-174">Example 7: Add an F# compiler</span></span>

<span data-ttu-id="1218e-175">In dit voor beeld ziet u hoe u de cmdlet kunt gebruiken `Add-Type` om een F # code-compiler toe te voegen aan uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-175">This example shows how to use the `Add-Type` cmdlet to add an F# code compiler to your PowerShell session.</span></span> <span data-ttu-id="1218e-176">Als u dit voor beeld in Power shell wilt uitvoeren, moet het zijn `FSharp.Compiler.CodeDom.dll` geïnstalleerd met de taal F #.</span><span class="sxs-lookup"><span data-stu-id="1218e-176">To run this example in PowerShell, you must have the `FSharp.Compiler.CodeDom.dll` that is installed with the F# language.</span></span>

```powershell
Add-Type -Path "FSharp.Compiler.CodeDom.dll"
$Provider = New-Object Microsoft.FSharp.Compiler.CodeDom.FSharpCodeProvider
$FSharpCode = @"
let rec loop n =if n <= 0 then () else beginprint_endline (string_of_int n);loop (n-1)end
"@
$FSharpType = Add-Type -TypeDefinition $FSharpCode -CodeDomProvider $Provider -PassThru |
   Where-Object { $_.IsPublic }
$FSharpType::loop(4)
```

```Output
4
3
2
1
```

<span data-ttu-id="1218e-177">`Add-Type` maakt gebruik van de para meter **Path** voor het opgeven van een assembly en het ophalen van de typen in de assembly.</span><span class="sxs-lookup"><span data-stu-id="1218e-177">`Add-Type` uses the **Path** parameter to specify an assembly and gets the types in the assembly.</span></span>
<span data-ttu-id="1218e-178">`New-Object` Hiermee wordt een instantie van de F #-code provider gemaakt en wordt het resultaat opgeslagen in de `$Provider` variabele.</span><span class="sxs-lookup"><span data-stu-id="1218e-178">`New-Object` creates an instance of the F# code provider and saves the result in the `$Provider` variable.</span></span> <span data-ttu-id="1218e-179">De `$FSharpCode` variabele slaat de F #-code op die de methode **loop** definieert.</span><span class="sxs-lookup"><span data-stu-id="1218e-179">The `$FSharpCode` variable saves the F# code that defines the **Loop** method.</span></span>

<span data-ttu-id="1218e-180">De `$FSharpType` variabele bevat de resultaten van de `Add-Type` cmdlet waarmee de open bare typen worden opgeslagen die zijn gedefinieerd in `$FSharpCode` .</span><span class="sxs-lookup"><span data-stu-id="1218e-180">The the `$FSharpType` variable stores the results of the `Add-Type` cmdlet that saves the public types defined in `$FSharpCode`.</span></span> <span data-ttu-id="1218e-181">De **TypeDefinition** para meter geeft u de bron code op waarmee de typen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-181">The **TypeDefinition** parameter specifies the source code that defines the types.</span></span> <span data-ttu-id="1218e-182">De **CodeDomProvider** para meter geeft u de bron code compiler op.</span><span class="sxs-lookup"><span data-stu-id="1218e-182">The **CodeDomProvider** parameter specifies the source code compiler.</span></span> <span data-ttu-id="1218e-183">De para meter **PassThru** `Add-Type` retourneert een **runtime** -object dat de typen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1218e-183">The **PassThru** parameter directs `Add-Type` to return a **Runtime** object that represents the types.</span></span>
<span data-ttu-id="1218e-184">De objecten worden via de pijp lijn naar de `Where-Object` cmdlet verzonden, waarmee alleen de open bare typen worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-184">The objects are sent down the pipeline to the `Where-Object` cmdlet, which returns only the public types.</span></span> <span data-ttu-id="1218e-185">De cmdlet **where-object** wordt gebruikt omdat de F #-provider niet-open bare typen genereert om het resulterende open bare type te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="1218e-185">The **Where-Object** cmdlet is used because the F# provider generates non-public types to support the resulting public type.</span></span>

<span data-ttu-id="1218e-186">De methode loop wordt aangeroepen als een statische methode van het type dat is opgeslagen in de `$FSharpType` variabele.</span><span class="sxs-lookup"><span data-stu-id="1218e-186">The Loop method is called as a static method of the type stored in the `$FSharpType` variable.</span></span>

## <span data-ttu-id="1218e-187">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1218e-187">PARAMETERS</span></span>

### <span data-ttu-id="1218e-188">-Assemblyname</span><span class="sxs-lookup"><span data-stu-id="1218e-188">-AssemblyName</span></span>

<span data-ttu-id="1218e-189">Hiermee geeft u de naam op van een assembly die de typen bevat.</span><span class="sxs-lookup"><span data-stu-id="1218e-189">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="1218e-190">`Add-Type` neemt de typen van de opgegeven assembly op.</span><span class="sxs-lookup"><span data-stu-id="1218e-190">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="1218e-191">Deze para meter is vereist wanneer u typen maakt op basis van de naam van een assembly.</span><span class="sxs-lookup"><span data-stu-id="1218e-191">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="1218e-192">Voer de volledige of eenvoudige naam in, ook wel bekend als de gedeeltelijke naam, van een assembly.</span><span class="sxs-lookup"><span data-stu-id="1218e-192">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="1218e-193">Joker tekens zijn toegestaan in de naam van de assembly.</span><span class="sxs-lookup"><span data-stu-id="1218e-193">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="1218e-194">Als u een eenvoudige of gedeeltelijke naam opgeeft, wordt `Add-Type` deze omgezet in de volledige naam, waarna de volledige naam wordt gebruikt om de assembly te laden.</span><span class="sxs-lookup"><span data-stu-id="1218e-194">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="1218e-195">Deze para meter accepteert geen pad of bestands naam.</span><span class="sxs-lookup"><span data-stu-id="1218e-195">This parameter doesn't accept a path or a file name.</span></span> <span data-ttu-id="1218e-196">Als u het pad naar het bestand van de assembly-Dynamic-Link Library (DLL) wilt invoeren, gebruikt u de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="1218e-196">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="1218e-197">-CodeDomProvider</span><span class="sxs-lookup"><span data-stu-id="1218e-197">-CodeDomProvider</span></span>

<span data-ttu-id="1218e-198">Hiermee geeft u een code generator of compiler op.</span><span class="sxs-lookup"><span data-stu-id="1218e-198">Specifies a code generator or compiler.</span></span> <span data-ttu-id="1218e-199">`Add-Type` gebruikt de opgegeven compiler voor het compileren van de bron code.</span><span class="sxs-lookup"><span data-stu-id="1218e-199">`Add-Type` uses the specified compiler to compile the source code.</span></span> <span data-ttu-id="1218e-200">De standaard waarde is de C#-compiler.</span><span class="sxs-lookup"><span data-stu-id="1218e-200">The default is the C# compiler.</span></span> <span data-ttu-id="1218e-201">Gebruik deze para meter als u een taal gebruikt die niet kan worden opgegeven met behulp van de para meter **Language** .</span><span class="sxs-lookup"><span data-stu-id="1218e-201">Use this parameter if you're using a language that can't be specified by using the **Language** parameter.</span></span> <span data-ttu-id="1218e-202">De **CodeDomProvider** die u opgeeft, moeten assembly's kunnen genereren van de bron code.</span><span class="sxs-lookup"><span data-stu-id="1218e-202">The **CodeDomProvider** that you specify must be able to generate assemblies from source code.</span></span>

```yaml
Type: System.CodeDom.Compiler.CodeDomProvider
Parameter Sets: FromSource, FromMember
Aliases: Provider

Required: False
Position: Named
Default value: C# compiler
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1218e-203">-CompilerParameters</span><span class="sxs-lookup"><span data-stu-id="1218e-203">-CompilerParameters</span></span>

<span data-ttu-id="1218e-204">Hiermee geeft u de opties voor de bron code compiler op.</span><span class="sxs-lookup"><span data-stu-id="1218e-204">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="1218e-205">Deze opties worden zonder revisie naar de compiler verzonden.</span><span class="sxs-lookup"><span data-stu-id="1218e-205">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="1218e-206">Met deze para meter kunt u de compiler omleiden om een uitvoerbaar bestand te genereren, resources in te sluiten of opdracht regel opties in te stellen, zoals de `/unsafe` optie.</span><span class="sxs-lookup"><span data-stu-id="1218e-206">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span> <span data-ttu-id="1218e-207">Met deze para meter wordt de **CompilerParameters** -klasse, **System. CodeDom. compiler. CompilerParameters** geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-207">This parameter implements the **CompilerParameters** class, **System.CodeDom.Compiler.CompilerParameters**.</span></span>

<span data-ttu-id="1218e-208">U kunt de para meters **CompilerParameters** en **ReferencedAssemblies** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1218e-208">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.CodeDom.Compiler.CompilerParameters
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: CP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1218e-209">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="1218e-209">-IgnoreWarnings</span></span>

<span data-ttu-id="1218e-210">Waarschuwingen voor compileren worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-210">Ignores compiler warnings.</span></span> <span data-ttu-id="1218e-211">Gebruik deze para meter om te voor komen dat `Add-Type` waarschuwingen van het Compileer programma worden verwerkt als fouten.</span><span class="sxs-lookup"><span data-stu-id="1218e-211">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

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

### <span data-ttu-id="1218e-212">-Taal</span><span class="sxs-lookup"><span data-stu-id="1218e-212">-Language</span></span>

<span data-ttu-id="1218e-213">Hiermee geeft u de taal op die wordt gebruikt in de bron code.</span><span class="sxs-lookup"><span data-stu-id="1218e-213">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="1218e-214">De `Add-Type` cmdlet gebruikt de waarde van deze para meter om de juiste **CodeDomProvider** te selecteren.</span><span class="sxs-lookup"><span data-stu-id="1218e-214">The `Add-Type` cmdlet uses the value of this parameter to select the appropriate **CodeDomProvider**.</span></span> <span data-ttu-id="1218e-215">CSharp is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="1218e-215">CSharp is the default value.</span></span> <span data-ttu-id="1218e-216">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1218e-216">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1218e-217">CSharp</span><span class="sxs-lookup"><span data-stu-id="1218e-217">CSharp</span></span>
- <span data-ttu-id="1218e-218">CSharpVersion2</span><span class="sxs-lookup"><span data-stu-id="1218e-218">CSharpVersion2</span></span>
- <span data-ttu-id="1218e-219">CSharpVersion3</span><span class="sxs-lookup"><span data-stu-id="1218e-219">CSharpVersion3</span></span>
- <span data-ttu-id="1218e-220">JScript</span><span class="sxs-lookup"><span data-stu-id="1218e-220">JScript</span></span>
- <span data-ttu-id="1218e-221">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1218e-221">VisualBasic</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp, CSharpVersion2, CSharpVersion3, JScript, VisualBasic

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1218e-222">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1218e-222">-LiteralPath</span></span>

<span data-ttu-id="1218e-223">Hiermee geeft u het pad op naar broncode bestanden of assembly-DLL-bestanden die de typen bevatten.</span><span class="sxs-lookup"><span data-stu-id="1218e-223">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="1218e-224">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="1218e-224">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="1218e-225">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="1218e-225">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1218e-226">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="1218e-226">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1218e-227">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="1218e-227">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1218e-228">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="1218e-228">-MemberDefinition</span></span>

<span data-ttu-id="1218e-229">Hiermee geeft u nieuwe eigenschappen of methoden voor de klasse op.</span><span class="sxs-lookup"><span data-stu-id="1218e-229">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="1218e-230">`Add-Type` genereert de sjabloon code die nodig is om de eigenschappen of methoden te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="1218e-230">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="1218e-231">In Windows kunt u deze functie gebruiken om aanroepen van platform Invoke (P/Invoke) aan onbeheerde functies in Power shell te maken.</span><span class="sxs-lookup"><span data-stu-id="1218e-231">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="1218e-232">-Name</span><span class="sxs-lookup"><span data-stu-id="1218e-232">-Name</span></span>

<span data-ttu-id="1218e-233">Hiermee geeft u de naam op van de klasse die u wilt maken.</span><span class="sxs-lookup"><span data-stu-id="1218e-233">Specifies the name of the class to create.</span></span> <span data-ttu-id="1218e-234">Deze para meter is vereist voor het genereren van een type uit een definitie van een lid.</span><span class="sxs-lookup"><span data-stu-id="1218e-234">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="1218e-235">De type naam en naam ruimte moeten uniek zijn binnen een sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-235">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="1218e-236">U kunt een type niet verwijderen of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1218e-236">You can't unload a type or change it.</span></span>
<span data-ttu-id="1218e-237">Als u de code voor een type wilt wijzigen, moet u de naam wijzigen of een nieuwe Power shell-sessie starten.</span><span class="sxs-lookup"><span data-stu-id="1218e-237">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="1218e-238">Anders mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1218e-238">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="1218e-239">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="1218e-239">-Namespace</span></span>

<span data-ttu-id="1218e-240">Hiermee geeft u een naam ruimte voor het type op.</span><span class="sxs-lookup"><span data-stu-id="1218e-240">Specifies a namespace for the type.</span></span>

<span data-ttu-id="1218e-241">Als deze para meter niet is opgenomen in de opdracht, wordt het type gemaakt in de naam ruimte **micro soft. Power shell. commands. AddType. AutoGeneratedTypes** .</span><span class="sxs-lookup"><span data-stu-id="1218e-241">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="1218e-242">Als de para meter in de opdracht wordt opgenomen met een lege teken reeks waarde of een waarde van `$Null` , wordt het type gegenereerd in de globale naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="1218e-242">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="1218e-243">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="1218e-243">-OutputAssembly</span></span>

<span data-ttu-id="1218e-244">Hiermee wordt een DLL-bestand voor de assembly gegenereerd met de opgegeven naam op de locatie.</span><span class="sxs-lookup"><span data-stu-id="1218e-244">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="1218e-245">Voer een optioneel pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="1218e-245">Enter an optional path and file name.</span></span> <span data-ttu-id="1218e-246">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1218e-246">Wildcard characters are permitted.</span></span> <span data-ttu-id="1218e-247">`Add-Type`De assembly wordt standaard alleen in het geheugen gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-247">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="1218e-248">-Output type</span><span class="sxs-lookup"><span data-stu-id="1218e-248">-OutputType</span></span>

<span data-ttu-id="1218e-249">Hiermee geeft u het uitvoer type van de uitvoer-assembly op.</span><span class="sxs-lookup"><span data-stu-id="1218e-249">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="1218e-250">Standaard is geen uitvoer type opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1218e-250">By default, no output type is specified.</span></span> <span data-ttu-id="1218e-251">Deze para meter is alleen geldig wanneer een uitvoer-assembly is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1218e-251">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="1218e-252">Zie [OutputAssemblyType Enumeration (Engelstalig)](/dotnet/api/microsoft.powershell.commands.outputassemblytype)voor meer informatie over de waarden.</span><span class="sxs-lookup"><span data-stu-id="1218e-252">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="1218e-253">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1218e-253">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1218e-254">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="1218e-254">ConsoleApplication</span></span>
- <span data-ttu-id="1218e-255">Bibliotheek</span><span class="sxs-lookup"><span data-stu-id="1218e-255">Library</span></span>
- <span data-ttu-id="1218e-256">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="1218e-256">WindowsApplication</span></span>

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

### <span data-ttu-id="1218e-257">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1218e-257">-PassThru</span></span>

<span data-ttu-id="1218e-258">Retourneert een **System. runtime** -object dat de typen vertegenwoordigt die zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1218e-258">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="1218e-259">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1218e-259">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="1218e-260">-Path</span><span class="sxs-lookup"><span data-stu-id="1218e-260">-Path</span></span>

<span data-ttu-id="1218e-261">Hiermee geeft u het pad op naar broncode bestanden of assembly-DLL-bestanden die de typen bevatten.</span><span class="sxs-lookup"><span data-stu-id="1218e-261">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="1218e-262">Als u bron code bestanden verzendt, `Add-Type` compileert de code in de bestanden en maakt een assembly in het geheugen van de typen.</span><span class="sxs-lookup"><span data-stu-id="1218e-262">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="1218e-263">De bestandsnaam extensie die in de waarde van het **pad** is opgegeven, bepaalt de compiler die `Add-Type` gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1218e-263">The file name extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="1218e-264">Als u een assembly-bestand verzendt, `Add-Type` neemt de typen van de assembly toe.</span><span class="sxs-lookup"><span data-stu-id="1218e-264">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="1218e-265">Als u een assembly in het geheugen of de Global Assembly Cache wilt opgeven, gebruikt u de **assemblyname** -para meter.</span><span class="sxs-lookup"><span data-stu-id="1218e-265">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="1218e-266">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="1218e-266">-ReferencedAssemblies</span></span>

<span data-ttu-id="1218e-267">Hiermee geeft u de assembly's op waarvan het type afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="1218e-267">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="1218e-268">`Add-Type`Verwijzingen en zijn standaard `System.dll` `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="1218e-268">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="1218e-269">In de assembly's die u opgeeft met behulp van deze para meter wordt een aanvulling op de standaard-assembly's verwezen.</span><span class="sxs-lookup"><span data-stu-id="1218e-269">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="1218e-270">U kunt de para meters **CompilerParameters** en **ReferencedAssemblies** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1218e-270">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="1218e-271">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="1218e-271">-TypeDefinition</span></span>

<span data-ttu-id="1218e-272">Hiermee geeft u de bron code die de type definities bevat.</span><span class="sxs-lookup"><span data-stu-id="1218e-272">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="1218e-273">Voer de bron code in een teken reeks of hier in, of voer een variabele in die de bron code bevat.</span><span class="sxs-lookup"><span data-stu-id="1218e-273">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="1218e-274">Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1218e-274">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="1218e-275">Neem een naam ruimte declaratie op in uw type definitie.</span><span class="sxs-lookup"><span data-stu-id="1218e-275">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="1218e-276">Als u de naam ruimte declaratie weglaat, kan uw type dezelfde naam hebben als een ander type of de snelkoppeling voor een ander type, waardoor een onbedoelde overschrijving wordt veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="1218e-276">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="1218e-277">Als u bijvoorbeeld een type met de naam **Exception** definieert, zullen scripts die **uitzonde ring** gebruiken als de snelkoppeling voor **System. Exception** , mislukken.</span><span class="sxs-lookup"><span data-stu-id="1218e-277">For example, if you define a type called **Exception**, scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="1218e-278">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="1218e-278">-UsingNamespace</span></span>

<span data-ttu-id="1218e-279">Hiermee geeft u andere naam ruimten op die voor de klasse zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="1218e-279">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="1218e-280">Dit is vergelijkbaar met het sleutel woord C# `Using` .</span><span class="sxs-lookup"><span data-stu-id="1218e-280">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="1218e-281">Maakt standaard `Add-Type` een verwijzing naar de **systeem** naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="1218e-281">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="1218e-282">Wanneer de para meter **MemberDefinition** wordt gebruikt, wordt `Add-Type` standaard ook naar de **System. runtime. InteropServices** -naam ruimte verwezen.</span><span class="sxs-lookup"><span data-stu-id="1218e-282">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="1218e-283">Er wordt verwezen naar de naam ruimten die u toevoegt met behulp van de para meter **UsingNamespace** , naast de standaard naam ruimten.</span><span class="sxs-lookup"><span data-stu-id="1218e-283">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="1218e-284">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1218e-284">CommonParameters</span></span>

<span data-ttu-id="1218e-285">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1218e-285">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1218e-286">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1218e-286">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1218e-287">INVOER</span><span class="sxs-lookup"><span data-stu-id="1218e-287">INPUTS</span></span>

### <span data-ttu-id="1218e-288">Geen</span><span class="sxs-lookup"><span data-stu-id="1218e-288">None</span></span>

<span data-ttu-id="1218e-289">U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="1218e-289">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="1218e-290">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1218e-290">OUTPUTS</span></span>

### <span data-ttu-id="1218e-291">Geen of System. type</span><span class="sxs-lookup"><span data-stu-id="1218e-291">None or System.Type</span></span>

<span data-ttu-id="1218e-292">Wanneer u de para meter **PassThru** gebruikt, `Add-Type` retourneert een **System. type** -object dat het nieuwe type vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1218e-292">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="1218e-293">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1218e-293">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="1218e-294">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1218e-294">NOTES</span></span>

<span data-ttu-id="1218e-295">De typen die u toevoegt, zijn alleen aanwezig in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-295">The types that you add exist only in the current session.</span></span> <span data-ttu-id="1218e-296">Als u de typen in alle sessies wilt gebruiken, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="1218e-296">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="1218e-297">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie over het profiel.</span><span class="sxs-lookup"><span data-stu-id="1218e-297">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="1218e-298">Type namen en naam ruimten moeten uniek zijn binnen een sessie.</span><span class="sxs-lookup"><span data-stu-id="1218e-298">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="1218e-299">U kunt een type niet verwijderen of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1218e-299">You can't unload a type or change it.</span></span> <span data-ttu-id="1218e-300">Als u de code voor een type moet wijzigen, moet u de naam wijzigen of een nieuwe Power shell-sessie starten.</span><span class="sxs-lookup"><span data-stu-id="1218e-300">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="1218e-301">Anders mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1218e-301">Otherwise, the command fails.</span></span>

<span data-ttu-id="1218e-302">De **CodeDomProvider** -klasse voor sommige talen, zoals ironpython en J#, genereert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1218e-302">The **CodeDomProvider** class for some languages, such as IronPython and J#, doesn't generate output.</span></span> <span data-ttu-id="1218e-303">Als gevolg hiervan kunnen de typen die in deze talen zijn geschreven, niet worden gebruikt met `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="1218e-303">As a result, types written in these languages can't be used with `Add-Type`.</span></span>

<span data-ttu-id="1218e-304">Deze cmdlet is gebaseerd op de CodeDomProvider- [klasse](/dotnet/api/system.codedom.compiler.codedomprovider)van het Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1218e-304">This cmdlet is based on the Microsoft .NET Framework [CodeDomProvider Class](/dotnet/api/system.codedom.compiler.codedomprovider).</span></span>

## <span data-ttu-id="1218e-305">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1218e-305">RELATED LINKS</span></span>

[<span data-ttu-id="1218e-306">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1218e-306">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="1218e-307">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1218e-307">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="1218e-308">Lid toevoegen</span><span class="sxs-lookup"><span data-stu-id="1218e-308">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="1218e-309">New-Object</span><span class="sxs-lookup"><span data-stu-id="1218e-309">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="1218e-310">OutputAssemblyType</span><span class="sxs-lookup"><span data-stu-id="1218e-310">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="1218e-311">Platform aanroepen (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="1218e-311">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="1218e-312">Where-object</span><span class="sxs-lookup"><span data-stu-id="1218e-312">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
