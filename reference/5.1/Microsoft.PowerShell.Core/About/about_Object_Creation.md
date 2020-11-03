---
description: Hierin wordt uitgelegd hoe u objecten maakt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 8903af794c83e4c84709e3eeb21489557458e988
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252786"
---
# <a name="about-object-creation"></a><span data-ttu-id="446fa-104">Over het maken van objecten</span><span class="sxs-lookup"><span data-stu-id="446fa-104">About Object Creation</span></span>

## <a name="short-description"></a><span data-ttu-id="446fa-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="446fa-105">Short description</span></span>

<span data-ttu-id="446fa-106">Hierin wordt uitgelegd hoe u objecten maakt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="446fa-106">Explains how to create objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="446fa-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="446fa-107">Long description</span></span>

<span data-ttu-id="446fa-108">U kunt objecten in Power shell maken en de objecten gebruiken die u in opdrachten en scripts hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="446fa-108">You can create objects in PowerShell and use the objects that you create in commands and scripts.</span></span>

<span data-ttu-id="446fa-109">Er zijn veel manieren om objecten te maken. deze lijst is niet definitief:</span><span class="sxs-lookup"><span data-stu-id="446fa-109">There are many ways to create objects, this list is not definitive:</span></span>

- <span data-ttu-id="446fa-110">[New-object](xref:Microsoft.PowerShell.Utility.New-Object): maakt een exemplaar van een .NET Framework-object of COM-object.</span><span class="sxs-lookup"><span data-stu-id="446fa-110">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): Creates an instance of a .NET Framework object or COM object.</span></span>
- <span data-ttu-id="446fa-111">[Import-CSV](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): maakt aangepaste objecten ( **PSCustomObject** ) van de items die zijn gedefinieerd als door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="446fa-111">[Import-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv)/
  [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): Creates custom objects ( **PSCustomObject** ) from the items defined as comma separated values.</span></span>
- <span data-ttu-id="446fa-112">[ConvertFrom-JSON](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): maakt aangepaste objecten gedefinieerd in JavaScript object NOTATION (JSON).</span><span class="sxs-lookup"><span data-stu-id="446fa-112">[ConvertFrom-Json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): Creates custom objects defined in JavaScript Object Notation (JSON).</span></span>
- <span data-ttu-id="446fa-113">[ConvertFrom-string](xref:Microsoft.PowerShell.Utility.ConvertFrom-String): gebouwd op [FlashExtract](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples), `ConvertFrom-String` maakt aangepaste objecten van gestructureerde teken reeks gegevens.</span><span class="sxs-lookup"><span data-stu-id="446fa-113">[ConvertFrom-String](xref:Microsoft.PowerShell.Utility.ConvertFrom-String): Built on top of [FlashExtract](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples), `ConvertFrom-String` creates custom objects from structured string data.</span></span>
  <span data-ttu-id="446fa-114">In dit onderwerp wordt elk van deze methoden gedemonstreerd en besproken.</span><span class="sxs-lookup"><span data-stu-id="446fa-114">This topic will demonstrate and discuss each of these methods.</span></span>
- <span data-ttu-id="446fa-115">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): maakt aangepaste objecten die als sleutel-waardeparen zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="446fa-115">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): Creates custom objects defined as key value pairs.</span></span>
- <span data-ttu-id="446fa-116">[Add-type](xref:Microsoft.PowerShell.Utility.Add-Type): Hiermee kunt u een klasse in uw Power shell-sessie definiëren waarmee u een exemplaar kunt maken `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="446fa-116">[Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type): Allows you to define a class in your PowerShell session that you can instantiate with `New-Object`.</span></span>
- <span data-ttu-id="446fa-117">[New-module](xref:Microsoft.PowerShell.Core.New-Module): met de para meter **AsCustomObject** maakt u een aangepast object dat u definieert met behulp van een script blok.</span><span class="sxs-lookup"><span data-stu-id="446fa-117">[New-Module](xref:Microsoft.PowerShell.Core.New-Module): The **AsCustomObject** parameter creates a custom object you define using script block.</span></span>
- <span data-ttu-id="446fa-118">[Add-member](xref:Microsoft.PowerShell.Utility.Add-Member): voegt eigenschappen toe aan bestaande objecten.</span><span class="sxs-lookup"><span data-stu-id="446fa-118">[Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): Adds properties to existing objects.</span></span> <span data-ttu-id="446fa-119">U kunt gebruiken `Add-Member` om een aangepast object van een eenvoudig type te maken, zoals `[System.Int32]` .</span><span class="sxs-lookup"><span data-stu-id="446fa-119">You can use `Add-Member` to create a custom object out of a simple type, like `[System.Int32]`.</span></span>
- <span data-ttu-id="446fa-120">[Select-object](xref:Microsoft.PowerShell.Utility.Select-Object): Hiermee selecteert u de eigenschappen van een object.</span><span class="sxs-lookup"><span data-stu-id="446fa-120">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): Selects properties on an object.</span></span> <span data-ttu-id="446fa-121">U kunt gebruiken `Select-Object` om aangepaste en berekende eigenschappen te maken voor een object dat al is geïnstantieerd.</span><span class="sxs-lookup"><span data-stu-id="446fa-121">You can use `Select-Object` to create custom and calculated properties on an already instantiated object.</span></span>

<span data-ttu-id="446fa-122">De volgende aanvullende methoden zijn opgenomen in dit artikel:</span><span class="sxs-lookup"><span data-stu-id="446fa-122">The following additional methods are covered in this article:</span></span>

- <span data-ttu-id="446fa-123">Door de constructor van een type aan te roepen met behulp van een statische `new()` methode</span><span class="sxs-lookup"><span data-stu-id="446fa-123">By calling a type's constructor using a static `new()` method</span></span>
- <span data-ttu-id="446fa-124">Door typecasting hash-tabellen van eigenschaps namen en eigenschaps waarden</span><span class="sxs-lookup"><span data-stu-id="446fa-124">By typecasting hash tables of property names and property values</span></span>

## <a name="static-new-method"></a><span data-ttu-id="446fa-125">Statische methode New ()</span><span class="sxs-lookup"><span data-stu-id="446fa-125">Static new() method</span></span>

<span data-ttu-id="446fa-126">Alle .NET-typen hebben een `new()` methode waarmee u gemakkelijker instanties kunt bouwen.</span><span class="sxs-lookup"><span data-stu-id="446fa-126">All .NET types have a `new()` method that allows you to construct instances more easily.</span></span> <span data-ttu-id="446fa-127">U kunt ook alle beschik bare constructors voor een bepaald type weer geven.</span><span class="sxs-lookup"><span data-stu-id="446fa-127">You can also see all the available constructors for a given type.</span></span>

<span data-ttu-id="446fa-128">Als u de Constructors voor een type wilt zien, geeft u de naam van de `new` methode op na de naam van het type en drukt u op `<ENTER>` .</span><span class="sxs-lookup"><span data-stu-id="446fa-128">To see the constructors for a type, specify the `new` method name after the type name and press `<ENTER>`.</span></span>

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

<span data-ttu-id="446fa-129">U kunt nu een **System. URI** maken door de juiste constructor op te geven.</span><span class="sxs-lookup"><span data-stu-id="446fa-129">Now, you can create a **System.Uri** by specifying the appropriate constructor.</span></span>

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

<span data-ttu-id="446fa-130">U kunt het volgende voor beeld gebruiken om te bepalen welke .NET-typen op dit moment worden geladen om te instantiëren.</span><span class="sxs-lookup"><span data-stu-id="446fa-130">You can use the following sample to determine what .NET types are currently loaded for you to instantiate.</span></span>

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

<span data-ttu-id="446fa-131">Objecten die zijn gemaakt met de `new()` methode, hebben mogelijk niet dezelfde eigenschappen als objecten van hetzelfde type die zijn gemaakt door Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="446fa-131">Objects created using the `new()` method may not have the same properties as objects of the same type that are created by PowerShell cmdlets.</span></span> <span data-ttu-id="446fa-132">Power shell-cmdlets, providers en uitgebreid type systeem kunnen extra eigenschappen toevoegen aan het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="446fa-132">PowerShell cmdlets, providers, and Extended Type System can add extra properties to the instance.</span></span>

<span data-ttu-id="446fa-133">Zo voegt de bestandssysteem provider in Power shell zes **NoteProperty** -waarden toe aan het **DirectoryInfo** -object dat wordt geretourneerd door `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="446fa-133">For example, the FileSystem provider in PowerShell adds six **NoteProperty** values to the **DirectoryInfo** object returned by `Get-Item`.</span></span>

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="446fa-134">Wanneer u een **DirectoryInfo** -object rechtstreeks maakt, heeft dit niet de zes **NoteProperty** -waarden.</span><span class="sxs-lookup"><span data-stu-id="446fa-134">When you create a **DirectoryInfo** object directly, it does not have those six **NoteProperty** values.</span></span>

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="446fa-135">Zie voor meer informatie over het uitgebreide-type systeem [about_Types.ps1XML](about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="446fa-135">For more information about the Extended Type System, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

<span data-ttu-id="446fa-136">Deze functie is toegevoegd in Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="446fa-136">This feature was added in PowerShell 5.0</span></span>

## <a name="create-objects-from-hash-tables"></a><span data-ttu-id="446fa-137">Objecten maken op basis van hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="446fa-137">Create objects from hash tables</span></span>

<span data-ttu-id="446fa-138">U kunt een object maken op basis van een hash-tabel met eigenschappen en eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="446fa-138">You can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="446fa-139">De syntaxis is als volgt:</span><span class="sxs-lookup"><span data-stu-id="446fa-139">The syntax is as follows:</span></span>

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="446fa-140">Deze methode werkt alleen voor klassen die een constructor zonder para meters hebben.</span><span class="sxs-lookup"><span data-stu-id="446fa-140">This method works only for classes that have a parameterless constructor.</span></span> <span data-ttu-id="446fa-141">De object eigenschappen moeten openbaar en instelbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="446fa-141">The object properties must be public and settable.</span></span>

<span data-ttu-id="446fa-142">Deze functie is toegevoegd aan Power shell-versie 3,0</span><span class="sxs-lookup"><span data-stu-id="446fa-142">This feature was added in PowerShell version 3.0</span></span>

## <a name="create-custom-objects-from-hash-tables"></a><span data-ttu-id="446fa-143">Aangepaste objecten maken op basis van hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="446fa-143">Create custom objects from hash tables</span></span>

<span data-ttu-id="446fa-144">Aangepaste objecten zijn erg nuttig en zijn gemakkelijk te maken met behulp van de hash-tabel methode.</span><span class="sxs-lookup"><span data-stu-id="446fa-144">Custom objects are very useful and are easy to create using the hash table method.</span></span> <span data-ttu-id="446fa-145">De **PSCustomObject** -klasse is speciaal ontworpen voor dit doel einde.</span><span class="sxs-lookup"><span data-stu-id="446fa-145">The **PSCustomObject** class is designed specifically for this purpose.</span></span>

<span data-ttu-id="446fa-146">Aangepaste objecten zijn een uitstekende manier om een aangepaste uitvoer van een functie of script te retour neren.</span><span class="sxs-lookup"><span data-stu-id="446fa-146">Custom objects are an excellent way to return customized output from a function or script.</span></span> <span data-ttu-id="446fa-147">Dit is nuttiger dan de geretourneerde uitvoer die niet opnieuw kan worden geformatteerd of naar andere opdrachten kan worden gesluisd.</span><span class="sxs-lookup"><span data-stu-id="446fa-147">This is more useful than returning formatted output that cannot be reformatted or piped to other commands.</span></span>

<span data-ttu-id="446fa-148">De opdrachten in de `Test-Object function` set variabele waarden en gebruiken deze waarden vervolgens om een aangepast object te maken.</span><span class="sxs-lookup"><span data-stu-id="446fa-148">The commands in the `Test-Object function` set some variable values and then use those values to create a custom object.</span></span> <span data-ttu-id="446fa-149">U ziet dit object in gebruik in de sectie voor beeld van het `Update-Help` Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="446fa-149">You can see this object in use in the example section of the `Update-Help` cmdlet help topic.</span></span>

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

<span data-ttu-id="446fa-150">De uitvoer van deze functie is een verzameling aangepaste objecten die standaard zijn opgemaakt als een tabel.</span><span class="sxs-lookup"><span data-stu-id="446fa-150">The output of this function is a collection of custom objects formatted as a table by default.</span></span>

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

<span data-ttu-id="446fa-151">Gebruikers kunnen de eigenschappen van de aangepaste objecten net als bij standaard objecten beheren.</span><span class="sxs-lookup"><span data-stu-id="446fa-151">Users can manage the properties of the custom objects just as they do with standard objects.</span></span>

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a><span data-ttu-id="446fa-152">Niet-aangepaste objecten maken op basis van hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="446fa-152">Create non-custom objects from hash tables</span></span>

<span data-ttu-id="446fa-153">U kunt ook hash-tabellen gebruiken om objecten voor niet-aangepaste klassen te maken.</span><span class="sxs-lookup"><span data-stu-id="446fa-153">You can also use hash tables to create objects for non-custom classes.</span></span> <span data-ttu-id="446fa-154">Wanneer u een-object voor een niet-aangepaste klasse maakt, is de naam ruimte-gekwalificeerde typenaam vereist, maar u kunt ook een eerste **systeem** naam ruimte onderdeel weglaten.</span><span class="sxs-lookup"><span data-stu-id="446fa-154">When you create an object for a non-custom class, the namespace-qualified type name is required, although you may omit any initial **System** namespace component.</span></span>

<span data-ttu-id="446fa-155">Met de volgende opdracht wordt bijvoorbeeld een sessie optie object gemaakt.</span><span class="sxs-lookup"><span data-stu-id="446fa-155">For example, the following command creates a session option object.</span></span>

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

<span data-ttu-id="446fa-156">De vereisten van de functie hash-tabel, met name de vereiste para meters voor constructors, elimineren veel bestaande klassen.</span><span class="sxs-lookup"><span data-stu-id="446fa-156">The requirements of the hash table feature, especially the parameterless constructor requirement, eliminate many existing classes.</span></span> <span data-ttu-id="446fa-157">De meeste Power shell- _optie_ klassen zijn echter ontworpen voor gebruik met deze functie en andere zeer nuttige klassen, zoals de **ProcessStartInfo** -klasse.</span><span class="sxs-lookup"><span data-stu-id="446fa-157">However, most PowerShell _option_ classes are designed to work with this feature, as well as other very useful classes, such as the **ProcessStartInfo** class.</span></span>

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

<span data-ttu-id="446fa-158">U kunt ook de functie hash table gebruiken bij het instellen van parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="446fa-158">You can also use the hash table feature when setting parameter values.</span></span> <span data-ttu-id="446fa-159">Bijvoorbeeld, de waarde van de para meter **SessionOption** van de `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="446fa-159">For example, the value of the **SessionOption** parameter of the `New-PSSession`.</span></span>
<span data-ttu-id="446fa-160">cmdlet kan een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="446fa-160">cmdlet can be a hash table.</span></span>

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a><span data-ttu-id="446fa-161">Algemene objecten</span><span class="sxs-lookup"><span data-stu-id="446fa-161">Generic objects</span></span>

<span data-ttu-id="446fa-162">U kunt ook algemene objecten maken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="446fa-162">You can also create generic objects in PowerShell.</span></span> <span data-ttu-id="446fa-163">Algemene elementen zijn klassen, structuren, interfaces en methoden die tijdelijke aanduidingen (type para meters) hebben voor een of meer van de typen die ze opslaan of gebruiken.</span><span class="sxs-lookup"><span data-stu-id="446fa-163">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span>

<span data-ttu-id="446fa-164">In het volgende voor beeld wordt een **Dictionary** -object gemaakt.</span><span class="sxs-lookup"><span data-stu-id="446fa-164">The following example creates a **Dictionary** object.</span></span>

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

<span data-ttu-id="446fa-165">Zie voor meer informatie over generieke [algemene gegevens in .net](/dotnet/standard/generics).</span><span class="sxs-lookup"><span data-stu-id="446fa-165">For more information on Generics, see [Generics in .NET](/dotnet/standard/generics).</span></span>

## <a name="see-also"></a><span data-ttu-id="446fa-166">Zie ook</span><span class="sxs-lookup"><span data-stu-id="446fa-166">See also</span></span>

[<span data-ttu-id="446fa-167">about_Objects</span><span class="sxs-lookup"><span data-stu-id="446fa-167">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="446fa-168">about_Methods</span><span class="sxs-lookup"><span data-stu-id="446fa-168">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="446fa-169">about_Properties</span><span class="sxs-lookup"><span data-stu-id="446fa-169">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="446fa-170">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="446fa-170">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="446fa-171">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="446fa-171">about_Types.ps1xml</span></span>](about_Types.ps1xml.md)
