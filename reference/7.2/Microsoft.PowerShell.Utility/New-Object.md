---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3b2db400c5a8a1c61ec30ecee07f91d29b5eb3c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706163"
---
# <span data-ttu-id="63034-102">New-Object</span><span class="sxs-lookup"><span data-stu-id="63034-102">New-Object</span></span>

## <span data-ttu-id="63034-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="63034-103">SYNOPSIS</span></span>
<span data-ttu-id="63034-104">Hiermee maakt u een exemplaar van een Microsoft .NET Framework of COM-object.</span><span class="sxs-lookup"><span data-stu-id="63034-104">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="63034-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="63034-105">SYNTAX</span></span>

### <span data-ttu-id="63034-106">Net (standaard)</span><span class="sxs-lookup"><span data-stu-id="63034-106">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="63034-107">Com</span><span class="sxs-lookup"><span data-stu-id="63034-107">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="63034-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="63034-108">DESCRIPTION</span></span>

<span data-ttu-id="63034-109">`New-Object`Met de cmdlet maakt u een exemplaar van een .NET Framework of COM-object.</span><span class="sxs-lookup"><span data-stu-id="63034-109">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="63034-110">U kunt het type van een .NET Framework-klasse of een ProgID van een COM-object opgeven.</span><span class="sxs-lookup"><span data-stu-id="63034-110">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="63034-111">Standaard typt u de volledig gekwalificeerde naam van een .NET Framework klasse en de cmdlet retourneert een verwijzing naar een exemplaar van die klasse.</span><span class="sxs-lookup"><span data-stu-id="63034-111">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="63034-112">Als u een exemplaar van een COM-object wilt maken, gebruikt u de para meter **ComObject** en geeft u de ProgID van het object op als waarde.</span><span class="sxs-lookup"><span data-stu-id="63034-112">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="63034-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="63034-113">EXAMPLES</span></span>

### <span data-ttu-id="63034-114">Voor beeld 1: een System. Version-object maken</span><span class="sxs-lookup"><span data-stu-id="63034-114">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="63034-115">In dit voor beeld wordt een **System. version** -object gemaakt met de teken reeks "1.2.3.4" als constructor.</span><span class="sxs-lookup"><span data-stu-id="63034-115">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="63034-116">Voor beeld 2: een Internet Explorer COM-object maken</span><span class="sxs-lookup"><span data-stu-id="63034-116">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="63034-117">In dit voor beeld worden twee exemplaren gemaakt van het COM-object dat de toepassing Internet Explorer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="63034-117">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="63034-118">De eerste instantie gebruikt de hash-tabel **Property** para meter om de methode **Navigate2** aan te roepen en de eigenschap **Visible** van het object in te stellen om `$True` de toepassing zichtbaar te maken.</span><span class="sxs-lookup"><span data-stu-id="63034-118">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="63034-119">Het tweede exemplaar krijgt dezelfde resultaten als de afzonderlijke opdrachten.</span><span class="sxs-lookup"><span data-stu-id="63034-119">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="63034-120">Voor beeld 3: de strikte para meter gebruiken om een niet-afsluit fout te genereren</span><span class="sxs-lookup"><span data-stu-id="63034-120">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="63034-121">In dit voor beeld wordt gedemonstreerd dat het toevoegen van de **strikte** para meter zorgt ervoor dat de `New-Object` cmdlet een niet-afsluit fout genereert wanneer het COM-object gebruikmaakt van een interop-assembly.</span><span class="sxs-lookup"><span data-stu-id="63034-121">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

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

### <span data-ttu-id="63034-122">Voor beeld 4: een COM-object maken voor het beheren van Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="63034-122">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="63034-123">In dit voor beeld ziet u hoe u een COM-object maakt en gebruikt voor het beheren van uw Windows-bureau blad.</span><span class="sxs-lookup"><span data-stu-id="63034-123">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="63034-124">De eerste opdracht maakt gebruik van de para meter **ComObject** van de `New-Object` cmdlet om een COM-object te maken met de **shell. Application** ProgID.</span><span class="sxs-lookup"><span data-stu-id="63034-124">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="63034-125">Het resulterende object wordt opgeslagen in de `$ObjShell` variabele.</span><span class="sxs-lookup"><span data-stu-id="63034-125">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="63034-126">Met de tweede opdracht `$ObjShell` wordt de variabele door sluizen naar de `Get-Member` cmdlet, waarin de eigenschappen en methoden van het COM-object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="63034-126">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="63034-127">De methoden zijn onder andere de methode **ToggleDesktop** .</span><span class="sxs-lookup"><span data-stu-id="63034-127">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="63034-128">Met de derde opdracht wordt de methode **ToggleDesktop** van het object aangeroepen om de geopende vensters op het bureau blad te minimaliseren.</span><span class="sxs-lookup"><span data-stu-id="63034-128">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

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

### <span data-ttu-id="63034-129">Voor beeld 5: meerdere argumenten door geven aan een constructor</span><span class="sxs-lookup"><span data-stu-id="63034-129">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="63034-130">In dit voor beeld ziet u hoe u een object maakt met een constructor waarvoor meerdere para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="63034-130">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="63034-131">De para meters moeten in een matrix worden geplaatst wanneer de para meter **argument List** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="63034-131">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="63034-132">Power shell verbindt elk lid van de matrix met een para meter van de constructor.</span><span class="sxs-lookup"><span data-stu-id="63034-132">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="63034-133">In dit voor beeld wordt de para meter splatting gebruikt voor de Lees baarheid.</span><span class="sxs-lookup"><span data-stu-id="63034-133">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="63034-134">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="63034-134">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="63034-135">Voor beeld 6: een constructor aanroepen die een matrix als één para meter gebruikt</span><span class="sxs-lookup"><span data-stu-id="63034-135">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="63034-136">In dit voor beeld ziet u hoe u een object maakt met een constructor die een para meter gebruikt die een matrix of verzameling is.</span><span class="sxs-lookup"><span data-stu-id="63034-136">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="63034-137">De matrix parameter moet in een andere matrix worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="63034-137">The array parameter must be put in wrapped inside another array.</span></span>

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

<span data-ttu-id="63034-138">De eerste poging om het object in dit voor beeld te maken, mislukt.</span><span class="sxs-lookup"><span data-stu-id="63034-138">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="63034-139">Power Shell heeft geprobeerd de drie leden van `$array` te binden aan de para meters van de constructor, maar de constructor heeft geen drie para meter.</span><span class="sxs-lookup"><span data-stu-id="63034-139">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="63034-140">`$array`Door in een andere matrix in te pakken, wordt voor komen dat Power shell de drie leden van `$array` de para meters van de constructor bindt.</span><span class="sxs-lookup"><span data-stu-id="63034-140">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="63034-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63034-141">PARAMETERS</span></span>

### <span data-ttu-id="63034-142">-Argument List</span><span class="sxs-lookup"><span data-stu-id="63034-142">-ArgumentList</span></span>

<span data-ttu-id="63034-143">Hiermee geeft u een matrix op met argumenten die moeten worden door gegeven aan de constructor van de .NET Framework klasse.</span><span class="sxs-lookup"><span data-stu-id="63034-143">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="63034-144">Als de constructor één para meter gebruikt die een matrix is, moet u die para meter in een andere matrix afronden.</span><span class="sxs-lookup"><span data-stu-id="63034-144">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="63034-145">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="63034-145">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="63034-146">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="63034-146">For more information about the behavior of **ArgumentList**, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="63034-147">De alias voor **argument List** is **args**.</span><span class="sxs-lookup"><span data-stu-id="63034-147">The alias for **ArgumentList** is **Args**.</span></span>

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

### <span data-ttu-id="63034-148">-ComObject</span><span class="sxs-lookup"><span data-stu-id="63034-148">-ComObject</span></span>

<span data-ttu-id="63034-149">Hiermee geeft u de programmatische id (ProgID) van het COM-object op.</span><span class="sxs-lookup"><span data-stu-id="63034-149">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

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

### <span data-ttu-id="63034-150">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="63034-150">-Property</span></span>

<span data-ttu-id="63034-151">Stelt eigenschaps waarden in en roept methoden van het nieuwe object aan.</span><span class="sxs-lookup"><span data-stu-id="63034-151">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="63034-152">Voer een hash-tabel in waarin de sleutels de namen van eigenschappen of methoden zijn en de waarden zijn eigenschaps waarden of methode argumenten.</span><span class="sxs-lookup"><span data-stu-id="63034-152">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="63034-153">`New-Object` maakt het object en stelt elke eigenschaps waarde in en roept elke methode aan in de volg orde waarin ze worden weer gegeven in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="63034-153">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="63034-154">Als het nieuwe object is afgeleid van de klasse **PSObject** en u een eigenschap opgeeft die niet voor komt in het object, `New-Object` voegt de opgegeven eigenschap toe aan het object als een NoteProperty.</span><span class="sxs-lookup"><span data-stu-id="63034-154">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="63034-155">Als het object geen **PSObject** is, wordt door de opdracht een niet-afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="63034-155">If the object is not a **PSObject**, the command generates a non-terminating error.</span></span>

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

### <span data-ttu-id="63034-156">-Strikte</span><span class="sxs-lookup"><span data-stu-id="63034-156">-Strict</span></span>

<span data-ttu-id="63034-157">Geeft aan dat de cmdlet een niet-afsluit fout genereert wanneer een COM-object dat u probeert te maken, gebruikmaakt van een interop-assembly.</span><span class="sxs-lookup"><span data-stu-id="63034-157">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="63034-158">Deze functie onderscheidt de werkelijke COM-objecten van .NET Framework objecten met COM-aanroep bare wrappers.</span><span class="sxs-lookup"><span data-stu-id="63034-158">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

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

### <span data-ttu-id="63034-159">-TypeName</span><span class="sxs-lookup"><span data-stu-id="63034-159">-TypeName</span></span>

<span data-ttu-id="63034-160">Hiermee geeft u de volledig gekwalificeerde naam van de .NET Framework klasse op.</span><span class="sxs-lookup"><span data-stu-id="63034-160">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="63034-161">U kunt niet zowel de para meter **TypeName** als de para meter **ComObject** opgeven.</span><span class="sxs-lookup"><span data-stu-id="63034-161">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

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

### <span data-ttu-id="63034-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63034-162">CommonParameters</span></span>

<span data-ttu-id="63034-163">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="63034-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63034-164">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="63034-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63034-165">INVOER</span><span class="sxs-lookup"><span data-stu-id="63034-165">INPUTS</span></span>

### <span data-ttu-id="63034-166">Geen</span><span class="sxs-lookup"><span data-stu-id="63034-166">None</span></span>

<span data-ttu-id="63034-167">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="63034-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="63034-168">UITVOER</span><span class="sxs-lookup"><span data-stu-id="63034-168">OUTPUTS</span></span>

### <span data-ttu-id="63034-169">Object</span><span class="sxs-lookup"><span data-stu-id="63034-169">Object</span></span>

<span data-ttu-id="63034-170">`New-Object` retourneert het object dat wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="63034-170">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="63034-171">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="63034-171">NOTES</span></span>

- <span data-ttu-id="63034-172">`New-Object` biedt de meest gebruikte functionaliteit van de functie voor VBScript CreateObject.</span><span class="sxs-lookup"><span data-stu-id="63034-172">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="63034-173">Een instructie zoals `Set objShell = CreateObject("Shell.Application")` in VBScript kan worden vertaald `$objShell = New-Object -COMObject "Shell.Application"` in Power shell.</span><span class="sxs-lookup"><span data-stu-id="63034-173">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="63034-174">`New-Object` uitbrei ding van de functionaliteit die beschikbaar is in de Windows Script Host-omgeving door eenvoudig te werken met .NET Framework objecten vanaf de opdracht regel en in scripts.</span><span class="sxs-lookup"><span data-stu-id="63034-174">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="63034-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="63034-175">RELATED LINKS</span></span>

[<span data-ttu-id="63034-176">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="63034-176">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="63034-177">Compare-object</span><span class="sxs-lookup"><span data-stu-id="63034-177">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="63034-178">Groep-object</span><span class="sxs-lookup"><span data-stu-id="63034-178">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="63034-179">Meting object</span><span class="sxs-lookup"><span data-stu-id="63034-179">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="63034-180">Select-Object</span><span class="sxs-lookup"><span data-stu-id="63034-180">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="63034-181">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="63034-181">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="63034-182">T-object</span><span class="sxs-lookup"><span data-stu-id="63034-182">Tee-Object</span></span>](Tee-Object.md)

