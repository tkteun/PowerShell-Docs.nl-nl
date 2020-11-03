---
description: Hierin wordt beschreven hoe u object eigenschappen gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: c8e711086922ea6a76978085a63380156591bb1d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252585"
---
# <a name="about-properties"></a><span data-ttu-id="c0eee-104">Over eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c0eee-104">About Properties</span></span>

## <a name="short-description"></a><span data-ttu-id="c0eee-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0eee-105">Short description</span></span>
<span data-ttu-id="c0eee-106">Hierin wordt beschreven hoe u object eigenschappen gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c0eee-106">Describes how to use object properties in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c0eee-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0eee-107">Long description</span></span>

<span data-ttu-id="c0eee-108">Power shell gebruikt gestructureerde verzamelingen gegevens die objecten worden genoemd om de items in de gegevens archieven of de status van de computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-108">PowerShell uses structured collections of information called objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="c0eee-109">Normaal gesp roken werkt u met een object dat deel uitmaakt van het Microsoft .NET Framework, maar u kunt ook aangepaste objecten maken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c0eee-109">Typically, you work with object that are part of the Microsoft .NET Framework, but you can also create custom objects in PowerShell.</span></span>

<span data-ttu-id="c0eee-110">De koppeling tussen een item en het bijbehorende object is zeer dicht bij elkaar.</span><span class="sxs-lookup"><span data-stu-id="c0eee-110">The association between an item and its object is very close.</span></span> <span data-ttu-id="c0eee-111">Wanneer u een object wijzigt, wijzigt u meestal het item dat het vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c0eee-111">When you change an object, you usually change the item that it represents.</span></span> <span data-ttu-id="c0eee-112">Wanneer u bijvoorbeeld een bestand in Power shell ophaalt, krijgt u niet het daad werkelijke bestand.</span><span class="sxs-lookup"><span data-stu-id="c0eee-112">For example, when you get a file in PowerShell, you do not get the actual file.</span></span> <span data-ttu-id="c0eee-113">In plaats daarvan krijgt u een file info-object dat het bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c0eee-113">Instead, you get a FileInfo object that represents the file.</span></span> <span data-ttu-id="c0eee-114">Wanneer u het file info-object wijzigt, wordt het bestand ook gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c0eee-114">When you change the FileInfo object, the file changes too.</span></span>

<span data-ttu-id="c0eee-115">De meeste objecten hebben eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="c0eee-115">Most objects have properties.</span></span> <span data-ttu-id="c0eee-116">Eigenschappen zijn de gegevens die aan een object zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="c0eee-116">Properties are the data that is associated with an object.</span></span> <span data-ttu-id="c0eee-117">Verschillende object typen hebben andere eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="c0eee-117">Different types of object have different properties.</span></span> <span data-ttu-id="c0eee-118">Bijvoorbeeld een file info-object, dat een bestand vertegenwoordigt, een eigenschap **IsReadOnly** heeft die $True bevat als het bestand het kenmerk alleen-lezen heeft en $False als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="c0eee-118">For example, a FileInfo object, which represents a file, has an **IsReadOnly** property that contains $True if the file the read-only attribute and $False if it does not.</span></span>
<span data-ttu-id="c0eee-119">Een DirectoryInfo-object, dat een directory van het bestands systeem vertegenwoordigt, heeft een bovenliggende eigenschap die het pad naar de bovenliggende map bevat.</span><span class="sxs-lookup"><span data-stu-id="c0eee-119">A DirectoryInfo object, which represents a file system directory, has a Parent property that contains the path to the parent directory.</span></span>

### <a name="object-properties"></a><span data-ttu-id="c0eee-120">Object eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c0eee-120">Object properties</span></span>

<span data-ttu-id="c0eee-121">Als u de eigenschappen van een object wilt ophalen, gebruikt u de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0eee-121">To get the properties of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="c0eee-122">Als u bijvoorbeeld de eigenschappen van een **file info** -object wilt ophalen, gebruikt u de `Get-ChildItem` cmdlet om het file info-object op te halen dat een bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c0eee-122">For example, to get the properties of a **FileInfo** object, use the `Get-ChildItem` cmdlet to get the FileInfo object that represents a file.</span></span> <span data-ttu-id="c0eee-123">Gebruik vervolgens een pijplijn operator (&#124;) om het **file info** -object naar te verzenden `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="c0eee-123">Then, use a pipeline operator (&#124;) to send the **FileInfo** object to `Get-Member`.</span></span> <span data-ttu-id="c0eee-124">Met de volgende opdracht wordt het PowerShell.exe-bestand opgehaald en verzonden naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="c0eee-124">The following command gets the PowerShell.exe file and sends it to `Get-Member`.</span></span>
<span data-ttu-id="c0eee-125">De \$ Automatische variabele Pshome bevat het pad van de installatie directory van Power shell.</span><span class="sxs-lookup"><span data-stu-id="c0eee-125">The \$Pshome automatic variable contains the path of the PowerShell installation directory.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

<span data-ttu-id="c0eee-126">De uitvoer van de opdracht geeft een lijst van de leden van het object **file info** .</span><span class="sxs-lookup"><span data-stu-id="c0eee-126">The output of the command lists the members of the **FileInfo** object.</span></span>
<span data-ttu-id="c0eee-127">Leden bevatten zowel eigenschappen als methoden.</span><span class="sxs-lookup"><span data-stu-id="c0eee-127">Members include both properties and methods.</span></span> <span data-ttu-id="c0eee-128">Wanneer u in Power shell werkt, hebt u toegang tot alle leden van de objecten.</span><span class="sxs-lookup"><span data-stu-id="c0eee-128">When you work in PowerShell, you have access to all the members of the objects.</span></span>

<span data-ttu-id="c0eee-129">Als u alleen de eigenschappen van een object en niet de methoden wilt ophalen, gebruikt u de para meter member type van de `Get-Member` cmdlet met de waarde ' Property ', zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-129">To get only the properties of an object and not the methods, use the MemberType parameter of the `Get-Member` cmdlet with a value of "property", as shown in the following example.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

<span data-ttu-id="c0eee-130">Nadat u de eigenschappen hebt gevonden, kunt u deze gebruiken in uw Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="c0eee-130">After you find the properties, you can use them in your PowerShell commands.</span></span>

## <a name="property-values"></a><span data-ttu-id="c0eee-131">Eigenschaps waarden</span><span class="sxs-lookup"><span data-stu-id="c0eee-131">Property values</span></span>

<span data-ttu-id="c0eee-132">Hoewel elk object van een specifiek type dezelfde eigenschappen heeft, beschrijven de waarden van die eigenschappen het specifieke object.</span><span class="sxs-lookup"><span data-stu-id="c0eee-132">Although every object of a specific type has the same properties, the values of those properties describe the particular object.</span></span> <span data-ttu-id="c0eee-133">Elk file info-object heeft bijvoorbeeld een eigenschap CreationTime, maar de waarde van die eigenschap verschilt voor elk bestand.</span><span class="sxs-lookup"><span data-stu-id="c0eee-133">For example, every FileInfo object has a CreationTime property, but the value of that property differs for each file.</span></span>

<span data-ttu-id="c0eee-134">De meest voorkomende manier om de waarden van de eigenschappen van een object op te halen, is door de punt methode te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c0eee-134">The most common way to get the values of the properties of an object is to use the dot method.</span></span> <span data-ttu-id="c0eee-135">Typ een verwijzing naar het object, bijvoorbeeld een variabele die het object bevat, of een opdracht die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="c0eee-135">Type a reference to the object, such as a variable that contains the object, or a command that gets the object.</span></span> <span data-ttu-id="c0eee-136">Typ vervolgens een punt (.), gevolgd door de naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="c0eee-136">Then, type a dot (.) followed by the property name.</span></span>

<span data-ttu-id="c0eee-137">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap CreationTime van het PowerShell.exe-bestand weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-137">For example, the following command displays the value of the CreationTime property of the PowerShell.exe file.</span></span> <span data-ttu-id="c0eee-138">De `Get-ChildItem` opdracht retourneert een file info-object dat het PowerShell.exe bestand vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c0eee-138">The `Get-ChildItem` command returns a FileInfo object that represents the PowerShell.exe file.</span></span> <span data-ttu-id="c0eee-139">De opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze wordt uitgevoerd voordat er eigenschappen worden geopend.</span><span class="sxs-lookup"><span data-stu-id="c0eee-139">The command is enclosed in parentheses to make sure that it is executed before any properties are accessed.</span></span> <span data-ttu-id="c0eee-140">De `Get-ChildItem` opdracht wordt als volgt gevolgd door een punt en de naam van de eigenschap CreationTime:</span><span class="sxs-lookup"><span data-stu-id="c0eee-140">The `Get-ChildItem` command is followed by a dot and the name of the CreationTime property, as follows:</span></span>

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="c0eee-141">U kunt ook een object opslaan in een variabele en vervolgens de eigenschappen ophalen met behulp van de punt methode, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="c0eee-141">You can also save an object in a variable and then get its properties by using the dot method, as shown in the following example:</span></span>

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="c0eee-142">U kunt ook de `Select-Object` `Format-List` cmdlets en gebruiken om de eigenschaps waarden van een object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-142">You can also use the `Select-Object` and `Format-List` cmdlets to display the property values of an object.</span></span> <span data-ttu-id="c0eee-143">`Select-Object` en `Format-List` elk hebben een **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="c0eee-143">`Select-Object` and `Format-List` each have a **Property** parameter.</span></span> <span data-ttu-id="c0eee-144">U kunt de para meter **Property** gebruiken om een of meer eigenschappen en hun waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-144">You can use the **Property** parameter to specify one or more properties and their values.</span></span> <span data-ttu-id="c0eee-145">U kunt ook het Joker teken () gebruiken \* om alle eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-145">Or, you can use the wildcard character (\*) to represent all the properties.</span></span>

<span data-ttu-id="c0eee-146">Met de volgende opdracht worden bijvoorbeeld de waarden van alle eigenschappen van het PowerShell.exe-bestand weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0eee-146">For example, the following command displays the values of all the properties of the PowerShell.exe file.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a><span data-ttu-id="c0eee-147">Statische eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c0eee-147">Static properties</span></span>

<span data-ttu-id="c0eee-148">U kunt de statische eigenschappen van .NET-klassen gebruiken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c0eee-148">You can use the static properties of .NET classes in PowerShell.</span></span> <span data-ttu-id="c0eee-149">Statische eigenschappen zijn eigenschappen van klasse, in tegens telling tot standaard eigenschappen, die eigenschappen van een object zijn.</span><span class="sxs-lookup"><span data-stu-id="c0eee-149">Static properties are properties of class, unlike standard properties, which are properties of an object.</span></span>

<span data-ttu-id="c0eee-150">Als u de statische eigenschappen van een klasse wilt ophalen, gebruikt u de statische para meter van de cmdlet Get-Member.</span><span class="sxs-lookup"><span data-stu-id="c0eee-150">To get the static properties of an class, use the Static parameter of the Get-Member cmdlet.</span></span>

<span data-ttu-id="c0eee-151">Met de volgende opdracht worden bijvoorbeeld de statische eigenschappen van de `System.DateTime` klasse opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c0eee-151">For example, the following command gets the static properties of the `System.DateTime` class.</span></span>

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

<span data-ttu-id="c0eee-152">Als u de waarde van een statische eigenschap wilt ophalen, gebruikt u de volgende syntaxis.</span><span class="sxs-lookup"><span data-stu-id="c0eee-152">To get the value of a static property, use the following syntax.</span></span>

```
[<ClassName>]::<Property>
```

<span data-ttu-id="c0eee-153">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap UtcNow static van de `System.DateTime` klasse opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c0eee-153">For example, the following command gets the value of the UtcNow static property of the `System.DateTime` class.</span></span>

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a><span data-ttu-id="c0eee-154">Eigenschappen van scalaire objecten en verzamelingen</span><span class="sxs-lookup"><span data-stu-id="c0eee-154">Properties of scalar objects and collections</span></span>

<span data-ttu-id="c0eee-155">De eigenschappen van een object ("scalair") van een bepaald type zijn vaak anders dan de eigenschappen van een verzameling objecten van hetzelfde type.</span><span class="sxs-lookup"><span data-stu-id="c0eee-155">The properties of one ("scalar") object of a particular type are often different from the properties of a collection of objects of the same type.</span></span>
<span data-ttu-id="c0eee-156">Elke service heeft bijvoorbeeld de eigenschap **DisplayName** , maar een verzameling services heeft geen eigenschap **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="c0eee-156">For example, every service has as **DisplayName** property, but a collection of services does not have a **DisplayName** property.</span></span>

<span data-ttu-id="c0eee-157">Met de volgende opdracht wordt de waarde van de eigenschap **DisplayName** van de service ' AudioSrv ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c0eee-157">The following command gets the value of the **DisplayName** property of the 'Audiosrv' service.</span></span>

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

<span data-ttu-id="c0eee-158">Vanaf Power Shell 3,0 probeert Power shell script fouten te voor komen die het resultaat zijn van de verschillende eigenschappen van scalaire objecten en verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="c0eee-158">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing properties of scalar objects and collections.</span></span> <span data-ttu-id="c0eee-159">Dezelfde opdracht retourneert de waarde van de eigenschap **DisplayName** van elke service die `Get-Service` retourneert.</span><span class="sxs-lookup"><span data-stu-id="c0eee-159">The same command returns the value of the **DisplayName** property of every service that `Get-Service` returns.</span></span>

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

<span data-ttu-id="c0eee-160">Wanneer u een verzameling verzendt, maar een eigenschap aanvraagt die alleen voor één (' scalaire ') objecten bestaat, retourneert Power shell de waarde van die eigenschap voor elk object in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="c0eee-160">When you submit a collection, but request a property that exists only on single ("scalar") objects, PowerShell returns the value of that property for every object in the collection.</span></span>

<span data-ttu-id="c0eee-161">Alle verzamelingen hebben een eigenschap **Count** die het aantal objecten in de verzameling retourneert.</span><span class="sxs-lookup"><span data-stu-id="c0eee-161">All collections have a **Count** property that returns how many objects are in the collection.</span></span>

```powershell
(Get-Service).Count
```

```output
176
```

<span data-ttu-id="c0eee-162">Als u vanaf Power Shell 3,0 de eigenschap Count of length van nul objecten of één object aanvraagt, retourneert Power shell de juiste waarde.</span><span class="sxs-lookup"><span data-stu-id="c0eee-162">Beginning in PowerShell 3.0, if you request the Count or Length property of zero objects or one object, PowerShell returns the correct value.</span></span>

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

<span data-ttu-id="c0eee-163">Als er een eigenschap bestaat voor de afzonderlijke objecten en de verzameling, wordt alleen de eigenschap van de verzameling geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c0eee-163">If a property exists on the individual objects and on the collection, only the collection's property is returned.</span></span>

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

<span data-ttu-id="c0eee-164">Deze functie werkt ook met methoden van scalaire objecten en verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="c0eee-164">This feature also works on methods of scalar objects and collections.</span></span> <span data-ttu-id="c0eee-165">Zie [about_Methods](about_methods.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0eee-165">For more information, see [about_Methods](about_methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0eee-166">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c0eee-166">See also</span></span>

[<span data-ttu-id="c0eee-167">about_Methods</span><span class="sxs-lookup"><span data-stu-id="c0eee-167">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="c0eee-168">about_Objects</span><span class="sxs-lookup"><span data-stu-id="c0eee-168">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="c0eee-169">Get-member</span><span class="sxs-lookup"><span data-stu-id="c0eee-169">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="c0eee-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="c0eee-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="c0eee-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="c0eee-171">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)
