---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3246d33174f39bf52dfa68b2dbe1e7b76a320b61
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251081"
---
# <span data-ttu-id="7574c-103">New-Object</span><span class="sxs-lookup"><span data-stu-id="7574c-103">New-Object</span></span>

## <span data-ttu-id="7574c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7574c-104">SYNOPSIS</span></span>
<span data-ttu-id="7574c-105">Hiermee maakt u een exemplaar van een Microsoft .NET Framework of COM-object.</span><span class="sxs-lookup"><span data-stu-id="7574c-105">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="7574c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7574c-106">SYNTAX</span></span>

### <span data-ttu-id="7574c-107">Net (standaard)</span><span class="sxs-lookup"><span data-stu-id="7574c-107">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="7574c-108">Com</span><span class="sxs-lookup"><span data-stu-id="7574c-108">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="7574c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7574c-109">DESCRIPTION</span></span>

<span data-ttu-id="7574c-110">`New-Object`Met de cmdlet maakt u een exemplaar van een .NET Framework of COM-object.</span><span class="sxs-lookup"><span data-stu-id="7574c-110">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="7574c-111">U kunt het type van een .NET Framework-klasse of een ProgID van een COM-object opgeven.</span><span class="sxs-lookup"><span data-stu-id="7574c-111">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="7574c-112">Standaard typt u de volledig gekwalificeerde naam van een .NET Framework klasse en de cmdlet retourneert een verwijzing naar een exemplaar van die klasse.</span><span class="sxs-lookup"><span data-stu-id="7574c-112">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="7574c-113">Als u een exemplaar van een COM-object wilt maken, gebruikt u de para meter **ComObject** en geeft u de ProgID van het object op als waarde.</span><span class="sxs-lookup"><span data-stu-id="7574c-113">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="7574c-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7574c-114">EXAMPLES</span></span>

### <span data-ttu-id="7574c-115">Voor beeld 1: een System. Version-object maken</span><span class="sxs-lookup"><span data-stu-id="7574c-115">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="7574c-116">In dit voor beeld wordt een **System. version** -object gemaakt met de teken reeks "1.2.3.4" als constructor.</span><span class="sxs-lookup"><span data-stu-id="7574c-116">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="7574c-117">Voor beeld 2: een Internet Explorer COM-object maken</span><span class="sxs-lookup"><span data-stu-id="7574c-117">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="7574c-118">In dit voor beeld worden twee exemplaren gemaakt van het COM-object dat de toepassing Internet Explorer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7574c-118">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="7574c-119">De eerste instantie gebruikt de hash-tabel **Property** para meter om de methode **Navigate2** aan te roepen en de eigenschap **Visible** van het object in te stellen om `$True` de toepassing zichtbaar te maken.</span><span class="sxs-lookup"><span data-stu-id="7574c-119">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="7574c-120">Het tweede exemplaar krijgt dezelfde resultaten als de afzonderlijke opdrachten.</span><span class="sxs-lookup"><span data-stu-id="7574c-120">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="7574c-121">Voor beeld 3: de strikte para meter gebruiken om een niet-afsluit fout te genereren</span><span class="sxs-lookup"><span data-stu-id="7574c-121">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="7574c-122">In dit voor beeld wordt gedemonstreerd dat het toevoegen van de **strikte** para meter zorgt ervoor dat de `New-Object` cmdlet een niet-afsluit fout genereert wanneer het COM-object gebruikmaakt van een interop-assembly.</span><span class="sxs-lookup"><span data-stu-id="7574c-122">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### <span data-ttu-id="7574c-123">Voor beeld 4: een COM-object maken voor het beheren van Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="7574c-123">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="7574c-124">In dit voor beeld ziet u hoe u een COM-object maakt en gebruikt voor het beheren van uw Windows-bureau blad.</span><span class="sxs-lookup"><span data-stu-id="7574c-124">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="7574c-125">De eerste opdracht maakt gebruik van de para meter **ComObject** van de `New-Object` cmdlet om een COM-object te maken met de **shell. Application** ProgID.</span><span class="sxs-lookup"><span data-stu-id="7574c-125">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="7574c-126">Het resulterende object wordt opgeslagen in de `$ObjShell` variabele.</span><span class="sxs-lookup"><span data-stu-id="7574c-126">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="7574c-127">Met de tweede opdracht `$ObjShell` wordt de variabele door sluizen naar de `Get-Member` cmdlet, waarin de eigenschappen en methoden van het COM-object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7574c-127">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="7574c-128">De methoden zijn onder andere de methode **ToggleDesktop** .</span><span class="sxs-lookup"><span data-stu-id="7574c-128">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="7574c-129">Met de derde opdracht wordt de methode **ToggleDesktop** van het object aangeroepen om de geopende vensters op het bureau blad te minimaliseren.</span><span class="sxs-lookup"><span data-stu-id="7574c-129">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### <span data-ttu-id="7574c-130">Voor beeld 5: meerdere argumenten door geven aan een constructor</span><span class="sxs-lookup"><span data-stu-id="7574c-130">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="7574c-131">In dit voor beeld ziet u hoe u een object maakt met een constructor waarvoor meerdere para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7574c-131">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="7574c-132">De para meters moeten in een matrix worden geplaatst wanneer de para meter **argument List** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7574c-132">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="7574c-133">Power shell verbindt elk lid van de matrix met een para meter van de constructor.</span><span class="sxs-lookup"><span data-stu-id="7574c-133">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="7574c-134">In dit voor beeld wordt de para meter splatting gebruikt voor de Lees baarheid.</span><span class="sxs-lookup"><span data-stu-id="7574c-134">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="7574c-135">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7574c-135">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="7574c-136">Voor beeld 6: een constructor aanroepen die een matrix als één para meter gebruikt</span><span class="sxs-lookup"><span data-stu-id="7574c-136">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="7574c-137">In dit voor beeld ziet u hoe u een object maakt met een constructor die een para meter gebruikt die een matrix of verzameling is.</span><span class="sxs-lookup"><span data-stu-id="7574c-137">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="7574c-138">De matrix parameter moet in een andere matrix worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="7574c-138">The array parameter must be put in wrapped inside another array.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

<span data-ttu-id="7574c-139">De eerste poging om het object in dit voor beeld te maken, mislukt.</span><span class="sxs-lookup"><span data-stu-id="7574c-139">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="7574c-140">Power Shell heeft geprobeerd de drie leden van `$array` te binden aan de para meters van de constructor, maar de constructor heeft geen drie para meter.</span><span class="sxs-lookup"><span data-stu-id="7574c-140">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="7574c-141">`$array`Door in een andere matrix in te pakken, wordt voor komen dat Power shell de drie leden van `$array` de para meters van de constructor bindt.</span><span class="sxs-lookup"><span data-stu-id="7574c-141">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="7574c-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7574c-142">PARAMETERS</span></span>

### <span data-ttu-id="7574c-143">-Argument List</span><span class="sxs-lookup"><span data-stu-id="7574c-143">-ArgumentList</span></span>

<span data-ttu-id="7574c-144">Hiermee geeft u een matrix op met argumenten die moeten worden door gegeven aan de constructor van de .NET Framework klasse.</span><span class="sxs-lookup"><span data-stu-id="7574c-144">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="7574c-145">Als de constructor één para meter gebruikt die een matrix is, moet u die para meter in een andere matrix afronden.</span><span class="sxs-lookup"><span data-stu-id="7574c-145">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="7574c-146">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7574c-146">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="7574c-147">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="7574c-147">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="7574c-148">De alias voor **argument List** is **args**.</span><span class="sxs-lookup"><span data-stu-id="7574c-148">The alias for **ArgumentList** is **Args**.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7574c-149">-ComObject</span><span class="sxs-lookup"><span data-stu-id="7574c-149">-ComObject</span></span>

<span data-ttu-id="7574c-150">Hiermee geeft u de programmatische id (ProgID) van het COM-object op.</span><span class="sxs-lookup"><span data-stu-id="7574c-150">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7574c-151">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7574c-151">-Property</span></span>

<span data-ttu-id="7574c-152">Stelt eigenschaps waarden in en roept methoden van het nieuwe object aan.</span><span class="sxs-lookup"><span data-stu-id="7574c-152">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="7574c-153">Voer een hash-tabel in waarin de sleutels de namen van eigenschappen of methoden zijn en de waarden zijn eigenschaps waarden of methode argumenten.</span><span class="sxs-lookup"><span data-stu-id="7574c-153">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="7574c-154">`New-Object` maakt het object en stelt elke eigenschaps waarde in en roept elke methode aan in de volg orde waarin ze worden weer gegeven in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="7574c-154">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="7574c-155">Als het nieuwe object is afgeleid van de klasse **PSObject** en u een eigenschap opgeeft die niet voor komt in het object, `New-Object` voegt de opgegeven eigenschap toe aan het object als een NoteProperty.</span><span class="sxs-lookup"><span data-stu-id="7574c-155">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="7574c-156">Als het object geen **PSObject** is, wordt door de opdracht een niet-afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7574c-156">If the object is not a **PSObject** , the command generates a non-terminating error.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7574c-157">-Strikte</span><span class="sxs-lookup"><span data-stu-id="7574c-157">-Strict</span></span>

<span data-ttu-id="7574c-158">Geeft aan dat de cmdlet een niet-afsluit fout genereert wanneer een COM-object dat u probeert te maken, gebruikmaakt van een interop-assembly.</span><span class="sxs-lookup"><span data-stu-id="7574c-158">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="7574c-159">Deze functie onderscheidt de werkelijke COM-objecten van .NET Framework objecten met COM-aanroep bare wrappers.</span><span class="sxs-lookup"><span data-stu-id="7574c-159">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7574c-160">-TypeName</span><span class="sxs-lookup"><span data-stu-id="7574c-160">-TypeName</span></span>

<span data-ttu-id="7574c-161">Hiermee geeft u de volledig gekwalificeerde naam van de .NET Framework klasse op.</span><span class="sxs-lookup"><span data-stu-id="7574c-161">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="7574c-162">U kunt niet zowel de para meter **TypeName** als de para meter **ComObject** opgeven.</span><span class="sxs-lookup"><span data-stu-id="7574c-162">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7574c-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7574c-163">CommonParameters</span></span>

<span data-ttu-id="7574c-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7574c-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7574c-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7574c-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7574c-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="7574c-166">INPUTS</span></span>

### <span data-ttu-id="7574c-167">Geen</span><span class="sxs-lookup"><span data-stu-id="7574c-167">None</span></span>

<span data-ttu-id="7574c-168">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7574c-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7574c-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7574c-169">OUTPUTS</span></span>

### <span data-ttu-id="7574c-170">Object</span><span class="sxs-lookup"><span data-stu-id="7574c-170">Object</span></span>

<span data-ttu-id="7574c-171">`New-Object` retourneert het object dat wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7574c-171">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="7574c-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7574c-172">NOTES</span></span>

- <span data-ttu-id="7574c-173">`New-Object` biedt de meest gebruikte functionaliteit van de functie voor VBScript CreateObject.</span><span class="sxs-lookup"><span data-stu-id="7574c-173">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="7574c-174">Een instructie zoals `Set objShell = CreateObject("Shell.Application")` in VBScript kan worden vertaald `$objShell = New-Object -COMObject "Shell.Application"` in Power shell.</span><span class="sxs-lookup"><span data-stu-id="7574c-174">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="7574c-175">`New-Object` uitbrei ding van de functionaliteit die beschikbaar is in de Windows Script Host-omgeving door eenvoudig te werken met .NET Framework objecten vanaf de opdracht regel en in scripts.</span><span class="sxs-lookup"><span data-stu-id="7574c-175">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="7574c-176">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7574c-176">RELATED LINKS</span></span>

[<span data-ttu-id="7574c-177">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="7574c-177">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="7574c-178">Compare-object</span><span class="sxs-lookup"><span data-stu-id="7574c-178">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="7574c-179">Groep-object</span><span class="sxs-lookup"><span data-stu-id="7574c-179">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="7574c-180">Meting object</span><span class="sxs-lookup"><span data-stu-id="7574c-180">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="7574c-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7574c-181">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="7574c-182">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="7574c-182">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="7574c-183">T-object</span><span class="sxs-lookup"><span data-stu-id="7574c-183">Tee-Object</span></span>](Tee-Object.md)
