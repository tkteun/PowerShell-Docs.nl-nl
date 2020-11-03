---
description: Hierin worden de WMI Query Language (WQL) beschreven die kunnen worden gebruikt voor het ophalen van WMI-objecten in Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252726"
---
# <a name="about-wql"></a><span data-ttu-id="596a4-104">Over WQL</span><span class="sxs-lookup"><span data-stu-id="596a4-104">About WQL</span></span>

## <a name="short-description"></a><span data-ttu-id="596a4-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="596a4-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="596a4-106">Hierin worden de WMI Query Language (WQL) beschreven die kunnen worden gebruikt voor het ophalen van WMI-objecten in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="596a4-106">Describes WMI Query Language (WQL), which can be used to get WMI objects in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="596a4-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="596a4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="596a4-108">WQL is de query taal van de Windows Management Instrumentation (WMI), de taal die wordt gebruikt om informatie op te halen van WMI.</span><span class="sxs-lookup"><span data-stu-id="596a4-108">WQL is the Windows Management Instrumentation (WMI) query language, which is the language used to get information from WMI.</span></span>

<span data-ttu-id="596a4-109">U hoeft WQL niet te gebruiken om een WMI-query uit te voeren in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="596a4-109">You are not required to use WQL to perform a WMI query in Windows PowerShell.</span></span>
<span data-ttu-id="596a4-110">In plaats daarvan kunt u de para meters van de Get-WmiObject-of Get-CimInstance-cmdlets gebruiken.</span><span class="sxs-lookup"><span data-stu-id="596a4-110">Instead, you can use the parameters of the Get-WmiObject or Get-CimInstance cmdlets.</span></span> <span data-ttu-id="596a4-111">WQL-query's zijn iets sneller dan de standaard Get-WmiObject-opdrachten en de verbeterde prestaties zijn duidelijk wanneer de opdrachten op honderden systemen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="596a4-111">WQL queries are somewhat faster than standard Get-WmiObject commands and the improved performance is evident when the commands run on hundreds of systems.</span></span> <span data-ttu-id="596a4-112">U moet er echter voor zorgen dat de tijd die u besteedt aan het schrijven van een geslaagde WQL-query niet voldoet aan de verbetering van de prestaties.</span><span class="sxs-lookup"><span data-stu-id="596a4-112">However, be sure that the time you spend to write a successful WQL query doesn't outweigh the performance improvement.</span></span>

<span data-ttu-id="596a4-113">De basis WQL-instructies die u nodig hebt voor het gebruik van WQL zijn selecteren, waar en van.</span><span class="sxs-lookup"><span data-stu-id="596a4-113">The basic WQL statements you need to use WQL are Select, Where, and From.</span></span>

## <a name="when-to-use-wql"></a><span data-ttu-id="596a4-114">WANNEER WQL GEBRUIKEN?</span><span class="sxs-lookup"><span data-stu-id="596a4-114">WHEN TO USE WQL</span></span>

<span data-ttu-id="596a4-115">Wanneer u met WMI werkt en met name WQL, vergeet dan niet dat u ook Windows Power shell gebruikt.</span><span class="sxs-lookup"><span data-stu-id="596a4-115">When working with WMI, and especially with WQL, do not forget that you are also using Windows PowerShell.</span></span> <span data-ttu-id="596a4-116">Als een WQL-query niet werkt zoals verwacht, is het eenvoudiger om een standaard Windows Power shell-opdracht te gebruiken dan bij het opsporen van fouten in de WQL-query.</span><span class="sxs-lookup"><span data-stu-id="596a4-116">Often, if a WQL query does not work as expected, it's easier to use a standard Windows PowerShell command than to debug the WQL query.</span></span>

<span data-ttu-id="596a4-117">Tenzij u enorme hoeveel heden gegevens uit verschillende band breedte-gebonden externe systemen retourneert, is het nog nooit zo productief dat er uren worden besteed aan een ingewikkelde en convolutieve WQL-query wanneer er sprake is van een perfecte Windows-cmdlet die hetzelfde doet als een beetje langzamer.</span><span class="sxs-lookup"><span data-stu-id="596a4-117">Unless you are returning massive amounts of data from across bandwidth-constrained remote systems, it is rarely productive to spend hours trying to perfect a complicated and convoluted WQL query when there is a perfectly acceptable Windows cmdlet that does the same thing, if a bit more slowly.</span></span>

## <a name="using-the-select-statement"></a><span data-ttu-id="596a4-118">DE SELECT-INSTRUCTIE GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-118">USING THE SELECT STATEMENT</span></span>

<span data-ttu-id="596a4-119">Een typische WMI-query begint met een SELECT-instructie waarmee alle eigenschappen of specifieke eigenschappen van een WMI-klasse worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="596a4-119">A typical WMI query begins with a Select statement that gets all properties or particular properties of a WMI class.</span></span> <span data-ttu-id="596a4-120">Als u alle eigenschappen van een WMI-klasse wilt selecteren, gebruikt u een asterisk ( \* ).</span><span class="sxs-lookup"><span data-stu-id="596a4-120">To select all properties of a WMI class, use an asterisk (\*).</span></span> <span data-ttu-id="596a4-121">Met het sleutel woord from geeft u de WMI-klasse op.</span><span class="sxs-lookup"><span data-stu-id="596a4-121">The From keyword specifies the WMI class.</span></span>

<span data-ttu-id="596a4-122">Een SELECT-instructie heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="596a4-122">A Select statement has the following format:</span></span>

```
Select <property> from <WMI-class>
```

<span data-ttu-id="596a4-123">De volgende SELECT-instructie selecteert bijvoorbeeld alle eigenschappen (\*) uit de exemplaren van de WMI-klasse Win32_Bios.</span><span class="sxs-lookup"><span data-stu-id="596a4-123">For example, the following Select statement selects all properties (\*) from the instances of the Win32_Bios WMI class.</span></span>

```
Select * from Win32_Bios
```

<span data-ttu-id="596a4-124">Als u een bepaalde eigenschap van een WMI-klasse wilt selecteren, plaatst u de naam van de eigenschap tussen de tref woorden Select en from.</span><span class="sxs-lookup"><span data-stu-id="596a4-124">To select a particular property of a WMI class, place the property name between the Select and From keywords.</span></span>

<span data-ttu-id="596a4-125">Met de volgende query wordt alleen de naam van het BIOS uit de WMI-klasse Win32_Bios geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="596a4-125">The following query selects only the name of the BIOS from the Win32_Bios WMI class.</span></span> <span data-ttu-id="596a4-126">Met de opdracht wordt de query opgeslagen in de variabele $queryName.</span><span class="sxs-lookup"><span data-stu-id="596a4-126">The command saves the query in the $queryName variable.</span></span>

```
Select Name from Win32_Bios
```

<span data-ttu-id="596a4-127">Als u meer dan één eigenschap wilt selecteren, gebruikt u komma's om de eigenschapnamen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="596a4-127">To select more than one property, use commas to separate the property names.</span></span>
<span data-ttu-id="596a4-128">De volgende WMI-query selecteert de naam en de versie van de WMI-klasse Win32_Bios.</span><span class="sxs-lookup"><span data-stu-id="596a4-128">The following WMI query selects the name and the version of the Win32_Bios WMI class.</span></span> <span data-ttu-id="596a4-129">Met de opdracht wordt de query opgeslagen in de variabele $queryNameVersion.</span><span class="sxs-lookup"><span data-stu-id="596a4-129">The command saves the query in the $queryNameVersion variable.</span></span>

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a><span data-ttu-id="596a4-130">DE WQL-QUERY GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-130">USING THE WQL QUERY</span></span>

<span data-ttu-id="596a4-131">Er zijn drie manieren om WQL-query's te gebruiken in Windows Power shell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="596a4-131">There are three ways to use WQL query in Windows PowerShell command.</span></span>

- <span data-ttu-id="596a4-132">De cmdlet Get-WmiObject gebruiken</span><span class="sxs-lookup"><span data-stu-id="596a4-132">Use the Get-WmiObject cmdlet</span></span>
- <span data-ttu-id="596a4-133">De cmdlet Get-CimInstance gebruiken</span><span class="sxs-lookup"><span data-stu-id="596a4-133">Use the Get-CimInstance cmdlet</span></span>
- <span data-ttu-id="596a4-134">Gebruik de [wmisearcher] type Accelerator.</span><span class="sxs-lookup"><span data-stu-id="596a4-134">Use the [wmisearcher] type accelerator.</span></span>

## <a name="using-the-get-wmiobject-cmdlet"></a><span data-ttu-id="596a4-135">DE CMDLET GET-WMIOBJECT GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-135">USING THE GET-WMIOBJECT CMDLET</span></span>

<span data-ttu-id="596a4-136">De belangrijkste manier om de WQL-query te gebruiken, is deze tussen aanhalings tekens (als een teken reeks) te plaatsen en vervolgens de query reeks als de waarde van de query parameter van de cmdlet Get-WmiObject te gebruiken, zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="596a4-136">The most basic way to use the WQL query is to enclose it in quotation marks (as a string) and then use the query string as the value of the Query parameter of the Get-WmiObject cmdlet, as shown in the following example.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="596a4-137">U kunt de WQL-instructie ook opslaan in een variabele en de variabele vervolgens gebruiken als de waarde van de query parameter, zoals wordt weer gegeven in de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="596a4-137">You can also save the WQL statement in a variable and then use the variable as the value of the Query parameter, as shown in the following command.</span></span>

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

<span data-ttu-id="596a4-138">U kunt beide indelingen gebruiken met elke WQL-instructie.</span><span class="sxs-lookup"><span data-stu-id="596a4-138">You can use either format with any WQL statement.</span></span> <span data-ttu-id="596a4-139">De volgende opdracht gebruikt de query in de variabele $queryName om alleen de naam en versie-eigenschappen van het systeem-BIOS op te halen.</span><span class="sxs-lookup"><span data-stu-id="596a4-139">The following command uses the query in the $queryName variable to get only the name and version properties of the system BIOS.</span></span>

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

<span data-ttu-id="596a4-140">Houd er rekening mee dat u de para meters van de Get-WmiObject cmdlet kunt gebruiken om hetzelfde resultaat te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="596a4-140">Remember that you can use the parameters of the Get-WmiObject cmdlet to get the same result.</span></span> <span data-ttu-id="596a4-141">Met de volgende opdracht worden bijvoorbeeld ook de waarden van de eigenschappen name en version van exemplaren van de WMI-klasse Win32_Bios opgehaald.</span><span class="sxs-lookup"><span data-stu-id="596a4-141">For example, the following command also gets the values of the Name and Version properties of instances of the Win32_Bios WMI class.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a><span data-ttu-id="596a4-142">DE CMDLET GET-CIMINSTANCE GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-142">USING THE GET-CIMINSTANCE CMDLET</span></span>

<span data-ttu-id="596a4-143">Vanaf Windows Power Shell 3,0 kunt u de cmdlet Get-CimInstance gebruiken om WQL-query's uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="596a4-143">Beginning in Windows PowerShell 3.0, you can use the Get-CimInstance cmdlet to run WQL queries.</span></span>

<span data-ttu-id="596a4-144">Get-CimInstance haalt instanties van CIM-compatibele klassen op, met inbegrip van WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="596a4-144">Get-CimInstance gets instances of CIM-compliant classes, including WMI classes.</span></span> <span data-ttu-id="596a4-145">Met de CIM-cmdlets, geïntroduceerde Windows Power Shell 3,0, worden dezelfde taken uitgevoerd als voor de WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="596a4-145">The CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="596a4-146">De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de Common Information Model (CIM) standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van Windows-computers en computers waarop andere besturings systemen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="596a4-146">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage Windows computers and computers that are running other operating systems.</span></span>

<span data-ttu-id="596a4-147">De volgende opdracht maakt gebruik van de cmdlet Get-CimInstance om een WQL-query uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="596a4-147">The following command uses the Get-CimInstance cmdlet to run a WQL query.</span></span>

<span data-ttu-id="596a4-148">Elke WQL-query die met Get-WmiObject kan worden gebruikt, kan ook worden gebruikt met Get-CimInstance.</span><span class="sxs-lookup"><span data-stu-id="596a4-148">Any WQL query that can be used with Get-WmiObject can also be used with Get-CimInstance.</span></span>

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="596a4-149">Get-CimInstance retourneert een CimInstance-object in plaats van de ManagementObject die Get-WmiObject retourneert, maar de objecten zijn heel vergelijkbaar.</span><span class="sxs-lookup"><span data-stu-id="596a4-149">Get-CimInstance returns a CimInstance object, instead of the ManagementObject that Get-WmiObject returns, but the objects are quite similar.</span></span>

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a><span data-ttu-id="596a4-150">DE [wmisearcher] TYPE ACCELERATOR gebruiken</span><span class="sxs-lookup"><span data-stu-id="596a4-150">USING THE [wmisearcher] TYPE ACCELERATOR</span></span>

<span data-ttu-id="596a4-151">De [wmisearcher] type Accelerator maakt een ManagementObjectSearcher-object van een WQL-instructie teken reeks.</span><span class="sxs-lookup"><span data-stu-id="596a4-151">The [wmisearcher] type accelerator creates a ManagementObjectSearcher object from a WQL statement string.</span></span> <span data-ttu-id="596a4-152">Het ManagementObjectSearcher-object heeft veel eigenschappen en methoden, maar de meest eenvoudige methode is de Get-methode, waarmee de opgegeven WMI-query wordt aangeroepen en de resulterende objecten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="596a4-152">The ManagementObjectSearcher object has many properties and methods, but the most basic method is the Get method, which invokes the specified WMI query and returns the resulting objects.</span></span>

<span data-ttu-id="596a4-153">Met [wmisearcher] krijgt u eenvoudig toegang tot de klasse ManagementObjectSearcher .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="596a4-153">By using the [wmisearcher], you gain easy access to the ManagementObjectSearcher .NET Framework class.</span></span> <span data-ttu-id="596a4-154">Hiermee kunt u een query uitvoeren op WMI en de manier configureren waarop de query wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="596a4-154">This lets you query WMI and to configure the way the query is conducted.</span></span>

<span data-ttu-id="596a4-155">De [wmisearcher] type Accelerator gebruiken:</span><span class="sxs-lookup"><span data-stu-id="596a4-155">To use the [wmisearcher] type accelerator:</span></span>

1. <span data-ttu-id="596a4-156">De WQL-teken reeks casten naar een ManagementObjectSearcher-object.</span><span class="sxs-lookup"><span data-stu-id="596a4-156">Cast the  WQL string into a ManagementObjectSearcher object.</span></span>
2. <span data-ttu-id="596a4-157">Roep de Get-methode aan van het ManagementObjectSearcher-object.</span><span class="sxs-lookup"><span data-stu-id="596a4-157">Call the Get method of the ManagementObjectSearcher object.</span></span>

<span data-ttu-id="596a4-158">Met de volgende opdracht wordt bijvoorbeeld de query ' Alles selecteren ' gecast, wordt het resultaat opgeslagen in de variabele $bios en wordt vervolgens de Get-methode aangeroepen van het object ManagementObjectSearcher in de variabele $bios.</span><span class="sxs-lookup"><span data-stu-id="596a4-158">For example, the following command casts the "select all" query, saves the result in the $bios variable, and then calls the Get method of the ManagementObjectSearcher object in the $bios variable.</span></span>

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="596a4-159">Opmerking: alleen geselecteerde object eigenschappen worden standaard weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="596a4-159">NOTE: Only selected object properties are displayed by default.</span></span> <span data-ttu-id="596a4-160">Deze eigenschappen worden gedefinieerd in het XML-bestand van Types.ps1.</span><span class="sxs-lookup"><span data-stu-id="596a4-160">These properties are defined in the Types.ps1xml file.</span></span>

<span data-ttu-id="596a4-161">U kunt de [wmisearcher] type Accelerator gebruiken om de query of de variabele te casten.</span><span class="sxs-lookup"><span data-stu-id="596a4-161">You can use the [wmisearcher] type accelerator to cast the query or the variable.</span></span> <span data-ttu-id="596a4-162">In het volgende voor beeld wordt de type versnelling [wmisearcher] gebruikt voor het casten van de variabele.</span><span class="sxs-lookup"><span data-stu-id="596a4-162">In the following example, the [wmisearcher] type accelerator is used to cast the variable.</span></span> <span data-ttu-id="596a4-163">Het resultaat is hetzelfde.</span><span class="sxs-lookup"><span data-stu-id="596a4-163">The result is the same.</span></span>

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="596a4-164">Wanneer u de [wmisearcher] type Accelerator gebruikt, wordt de query reeks gewijzigd in een ManagementObjectSearcher-object, zoals wordt weer gegeven in de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="596a4-164">When you use the [wmisearcher] type accelerator, it changes the query string into a ManagementObjectSearcher object, as shown in the following commands.</span></span>

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

<span data-ttu-id="596a4-165">Deze opdracht indeling werkt voor elke query.</span><span class="sxs-lookup"><span data-stu-id="596a4-165">This command format works on any query.</span></span> <span data-ttu-id="596a4-166">Met de volgende opdracht wordt de waarde van de eigenschap name van de WMI-klasse Win32_Bios opgehaald.</span><span class="sxs-lookup"><span data-stu-id="596a4-166">The following command gets the value of the Name property of the Win32_Bios WMI class.</span></span>

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

<span data-ttu-id="596a4-167">U kunt deze bewerking uitvoeren in één opdracht, hoewel de opdracht iets moeilijker te interpreteren is.</span><span class="sxs-lookup"><span data-stu-id="596a4-167">You can perform this operation in a single command, although the command is a bit more difficult to interpret.</span></span>

<span data-ttu-id="596a4-168">In deze indeling gebruikt u de [wmisearcher] type Accelerator voor het casten van de WQL-query teken reeks naar een ManagementObjectSearcher en roept u vervolgens de Get-methode aan voor het object-alle in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="596a4-168">In this format, you use the [wmisearcher] type accelerator to cast the WQL query string to a ManagementObjectSearcher, and then call the Get method on the object -- all in a single command.</span></span> <span data-ttu-id="596a4-169">De haakjes () die de geconverteerde teken reeks direct Windows Power shell omsluiten om de teken reeks te casten voordat de methode wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="596a4-169">The parentheses () that enclose the casted string direct Windows PowerShell to cast the string before calling the method.</span></span>

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a><span data-ttu-id="596a4-170">DE BASIS WQL WHERE-INSTRUCTIE GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-170">USING THE BASIC WQL WHERE STATEMENT</span></span>

<span data-ttu-id="596a4-171">Een WHERE-instructie bepaalt de voor waarden voor de gegevens die een SELECT-instructie retourneert.</span><span class="sxs-lookup"><span data-stu-id="596a4-171">A Where statement establishes conditions for the data that a Select statement returns.</span></span>

<span data-ttu-id="596a4-172">De instructie WHERE heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="596a4-172">The Where statement has the following format:</span></span>

```
where <property> <operator> <value>
```

<span data-ttu-id="596a4-173">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="596a4-173">For example:</span></span>

```
where Name = 'Notepad.exe'
```

<span data-ttu-id="596a4-174">De instructie WHERE wordt gebruikt met de instructie SELECT, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="596a4-174">The Where statement is used with the Select statement, as shown in the following example.</span></span>

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

<span data-ttu-id="596a4-175">Wanneer u de WHERE-instructie gebruikt, moeten de naam en waarde van de eigenschap nauw keurig zijn.</span><span class="sxs-lookup"><span data-stu-id="596a4-175">When using the Where statement, the property name and value must be accurate.</span></span>

<span data-ttu-id="596a4-176">Met de volgende opdracht worden bijvoorbeeld de klad blok-processen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="596a4-176">For example, the following command gets the Notepad processes on the local computer.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

<span data-ttu-id="596a4-177">De volgende opdracht mislukt echter, omdat de proces naam de bestandsnaam extensie. exe bevat.</span><span class="sxs-lookup"><span data-stu-id="596a4-177">However, the following command fails, because the process name includes the ".exe" file name extension.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a><span data-ttu-id="596a4-178">WHERE-INSTRUCTIE VERGELIJKINGS OPERATORS</span><span class="sxs-lookup"><span data-stu-id="596a4-178">WHERE STATEMENT COMPARISON OPERATORS</span></span>

<span data-ttu-id="596a4-179">De volgende Opera tors zijn geldig in een WQL where-instructie.</span><span class="sxs-lookup"><span data-stu-id="596a4-179">The following operators are valid in a WQL Where statement.</span></span>

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

<span data-ttu-id="596a4-180">Er zijn andere opera Tors, maar deze worden gebruikt voor het maken van vergelijkingen.</span><span class="sxs-lookup"><span data-stu-id="596a4-180">There are other operators, but these are the ones used for making comparisons.</span></span>

<span data-ttu-id="596a4-181">Met de volgende query worden bijvoorbeeld de eigenschappen name en Priority van processen in de Win32_Process klasse waarvan de prioriteit van het proces groter is dan of gelijk is aan 11.</span><span class="sxs-lookup"><span data-stu-id="596a4-181">For example, the following query selects the Name and Priority properties from processes in the Win32_Process class where the process priority is greater than or equal to 11.</span></span> <span data-ttu-id="596a4-182">De Get-WmiObject-cmdlet voert de query uit.</span><span class="sxs-lookup"><span data-stu-id="596a4-182">The Get-WmiObject cmdlet runs the query.</span></span>

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a><span data-ttu-id="596a4-183">DE WQL-OPERA TORS IN DE FILTER PARAMETER GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-183">USING THE WQL OPERATORS IN THE FILTER PARAMETER</span></span>

<span data-ttu-id="596a4-184">De WQL-Opera tors kunnen ook worden gebruikt in de waarde van de filter parameter van de Get-WmiObject-of Get-CimInstance-cmdlets, en in de waarde van de query parameters van deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="596a4-184">The WQL operators can also be used in the value of the Filter parameter of the Get-WmiObject or Get-CimInstance cmdlets, as well as in the value of the Query parameters of these cmdlets.</span></span>

<span data-ttu-id="596a4-185">Met de volgende opdracht worden bijvoorbeeld de eigenschappen name en ProcessID opgehaald van de laatste vijf processen die de waarde van ProcessID hebben die groter is dan 1004.</span><span class="sxs-lookup"><span data-stu-id="596a4-185">For example, the following command gets the Name and ProcessID properties of the last five processes that have ProcessID values greater than 1004.</span></span> <span data-ttu-id="596a4-186">De opdracht maakt gebruik van de para meter filter om de voor waarde van ProcessID op te geven.</span><span class="sxs-lookup"><span data-stu-id="596a4-186">The command uses the Filter parameter to specify the ProcessID condition.</span></span>

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a><span data-ttu-id="596a4-187">DE OPERATOR LIKE GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-187">USING THE LIKE OPERATOR</span></span>

<span data-ttu-id="596a4-188">Met de operator Like kunt u Joker tekens gebruiken om de resultaten van een WQL-query te filteren.</span><span class="sxs-lookup"><span data-stu-id="596a4-188">The Like operator lets you use wildcard characters to filter the results of a WQL query.</span></span>

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

<span data-ttu-id="596a4-189">Wanneer de like-operator wordt gebruikt zonder joker tekens of bereik operators, gedraagt deze zich als de gelijkheids operator (=) en retourneert alleen objecten als ze exact overeenkomen met het patroon.</span><span class="sxs-lookup"><span data-stu-id="596a4-189">When the Like operator is used without any wildcard characters or range operators, it behaves like the equality operator (=) and returns objects only when they are an exact match for the pattern.</span></span>

<span data-ttu-id="596a4-190">U kunt de bereik bewerking combi neren met het percentage Joker teken om eenvoudige, maar krachtige filters te maken.</span><span class="sxs-lookup"><span data-stu-id="596a4-190">You can combine the range operation with the percent wildcard character to create simple, yet powerful filters.</span></span>

### <a name="like-operator-examples"></a><span data-ttu-id="596a4-191">LIKE, OPERATOR-VOOR BEELDEN</span><span class="sxs-lookup"><span data-stu-id="596a4-191">LIKE OPERATOR EXAMPLES</span></span>

#### <a name="example-1-range"></a><span data-ttu-id="596a4-192">VOOR beeld 1: [ \<range> ]</span><span class="sxs-lookup"><span data-stu-id="596a4-192">EXAMPLE 1: [\<range>]</span></span>

<span data-ttu-id="596a4-193">De volgende opdrachten starten Klad blok en zoeken naar een exemplaar van de Win32_Process klasse met een naam die begint met een letter tussen "H" en "N" (niet hoofdletter gevoelig).</span><span class="sxs-lookup"><span data-stu-id="596a4-193">The following commands start Notepad and then search for an instance of the Win32_Process class that has a name that starts with a letter between "H" and "N" (case-insensitive).</span></span>

<span data-ttu-id="596a4-194">De query moet elk proces retour neren van Hotpad.exe via Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="596a4-194">The query should return any process from Hotpad.exe through Notepad.exe.</span></span>

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a><span data-ttu-id="596a4-195">VOOR beeld 2: [ \<range> ] en%</span><span class="sxs-lookup"><span data-stu-id="596a4-195">EXAMPLE 2: [\<range>] and %</span></span>

<span data-ttu-id="596a4-196">De volgende opdrachten selecteren alle processen met een naam die begint met een letter tussen A en P (niet hoofdletter gevoelig), gevolgd door nul of meer letters in een combi natie hiervan.</span><span class="sxs-lookup"><span data-stu-id="596a4-196">The following commands select all process that have a name that begins with a letter between A and P (case-insensitive) followed by zero or more letters in any combination.</span></span>

<span data-ttu-id="596a4-197">De Get-WmiObject-cmdlet voert de query uit, de cmdlet Select-Object haalt de eigenschappen name en ProcessID op en de Sort-Object-cmdlet sorteert de resultaten in alfabetische volg orde op naam.</span><span class="sxs-lookup"><span data-stu-id="596a4-197">The Get-WmiObject cmdlet runs the query, the Select-Object cmdlet gets the Name and ProcessID properties, and the Sort-Object cmdlet sorts the results in alphabetical order by name.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a><span data-ttu-id="596a4-198">VOOR beeld 3: niet in bereik (^)</span><span class="sxs-lookup"><span data-stu-id="596a4-198">EXAMPLE 3: Not in Range (^)</span></span>

<span data-ttu-id="596a4-199">Met de volgende opdracht worden processen opgehaald waarvan de namen niet beginnen met een van de volgende letters: A, S, W, P, R, C, U, N</span><span class="sxs-lookup"><span data-stu-id="596a4-199">The following command gets processes whose names do not begin with any of the following letters: A, S, W, P, R, C, U, N</span></span>

<span data-ttu-id="596a4-200">en er zijn nul of meer letters gevolgd.</span><span class="sxs-lookup"><span data-stu-id="596a4-200">and followed zero or more letters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a><span data-ttu-id="596a4-201">VOOR beeld 4: wille keurige tekens--of geen (%)</span><span class="sxs-lookup"><span data-stu-id="596a4-201">EXAMPLE 4: Any characters -- or none (%)</span></span>

<span data-ttu-id="596a4-202">Met de volgende opdrachten worden processen opgehaald die namen hebben die beginnen met ' calc '.</span><span class="sxs-lookup"><span data-stu-id="596a4-202">The following commands get processes that have names that begin with "calc".</span></span>
<span data-ttu-id="596a4-203">Het symbool% in WQL is gelijk aan het sterretje ( \* )-symbool in reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="596a4-203">The % symbol in WQL is equivalent to the asterisk (\*) symbol in regular expressions.</span></span>

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a><span data-ttu-id="596a4-204">VOOR beeld 5: één teken (_)</span><span class="sxs-lookup"><span data-stu-id="596a4-204">EXAMPLE 5: One character (_)</span></span>

<span data-ttu-id="596a4-205">Met de volgende opdrachten worden processen opgehaald die een naam hebben met het volgende patroon, ' c_lc.exe ' waarbij het onderstrepings teken een wille keurig teken vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="596a4-205">The following commands get processes that have names that have the following pattern, "c_lc.exe" where the underscore character represents any one character.</span></span> <span data-ttu-id="596a4-206">Dit patroon komt overeen met een wille keurige naam van calc.exe via czlc.exe of c9lc.exe, maar komt niet overeen met namen waarin de ' c ' en ' l ' door meer dan één teken worden gescheiden.</span><span class="sxs-lookup"><span data-stu-id="596a4-206">This pattern matches any name from calc.exe through czlc.exe, or c9lc.exe, but does not match names in which the "c" and "l" are separated by more than one character.</span></span>

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a><span data-ttu-id="596a4-207">VOOR beeld 6: exacte overeenkomst</span><span class="sxs-lookup"><span data-stu-id="596a4-207">EXAMPLE 6: Exact match</span></span>

<span data-ttu-id="596a4-208">Met de volgende opdrachten worden processen met de naam WLIDSVC.exe opgehaald.</span><span class="sxs-lookup"><span data-stu-id="596a4-208">The following commands get processes named WLIDSVC.exe.</span></span> <span data-ttu-id="596a4-209">Hoewel de query het like-tref woord gebruikt, is er een exacte overeenkomst nodig, omdat de waarde geen joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="596a4-209">Even though the query uses the Like keyword, it requires an exact match, because the value does not include any wildcard characters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a><span data-ttu-id="596a4-210">DE OPERATOR OR GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-210">USING THE OR OPERATOR</span></span>

<span data-ttu-id="596a4-211">Als u meerdere onafhankelijke voor waarden wilt opgeven, gebruikt u het sleutel woord of.</span><span class="sxs-lookup"><span data-stu-id="596a4-211">To specify multiple independent conditions, use the Or keyword.</span></span> <span data-ttu-id="596a4-212">Het sleutel woord of wordt weer gegeven in de component WHERE.</span><span class="sxs-lookup"><span data-stu-id="596a4-212">The Or keyword appears in the Where clause.</span></span> <span data-ttu-id="596a4-213">Het voert een inclusieve of-bewerking uit op twee (of meer) voor waarden en retourneert items die voldoen aan de voor waarden.</span><span class="sxs-lookup"><span data-stu-id="596a4-213">It performs an inclusive OR operation on two (or more) conditions and returns items that meet any of the conditions.</span></span>

<span data-ttu-id="596a4-214">De operator or heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="596a4-214">The Or operator has the following format:</span></span>

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

<span data-ttu-id="596a4-215">Met de volgende opdrachten worden bijvoorbeeld alle exemplaren van de WMI-klasse Win32_Process opgehaald, maar alleen geretourneerd als de proces naam winword.exe of excel.exe is.</span><span class="sxs-lookup"><span data-stu-id="596a4-215">For example, the following commands get all instances of the Win32_Process WMI class but returns them only if the process name is winword.exe or excel.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

<span data-ttu-id="596a4-216">De instructie or kan worden gebruikt met meer dan twee voor waarden.</span><span class="sxs-lookup"><span data-stu-id="596a4-216">The Or statement can be used with more than two conditions.</span></span> <span data-ttu-id="596a4-217">In de volgende query haalt de instructie or Winword.exe, Excel.exe of Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="596a4-217">In the following query, the Or statement gets Winword.exe, Excel.exe, or Powershell.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a><span data-ttu-id="596a4-218">DE OPERATOR AND GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-218">USING THE AND OPERATOR</span></span>

<span data-ttu-id="596a4-219">Gebruik het sleutel woord en om meerdere gerelateerde voor waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="596a4-219">To specify multiple related conditions, use the And keyword.</span></span> <span data-ttu-id="596a4-220">Het sleutel woord en wordt weer gegeven in de component WHERE.</span><span class="sxs-lookup"><span data-stu-id="596a4-220">The And keyword appears in the Where clause.</span></span> <span data-ttu-id="596a4-221">Hiermee worden items geretourneerd die voldoen aan alle voor waarden.</span><span class="sxs-lookup"><span data-stu-id="596a4-221">It returns items that meet all of the conditions.</span></span>

<span data-ttu-id="596a4-222">De operator and heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="596a4-222">The And operator has the following format:</span></span>

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

<span data-ttu-id="596a4-223">Met de volgende opdrachten worden bijvoorbeeld processen opgehaald met de naam ' Winword.exe ' en de proces-ID van 6512.</span><span class="sxs-lookup"><span data-stu-id="596a4-223">For example, the following commands get processes that have a name of "Winword.exe" and the process ID of 6512.</span></span>

<span data-ttu-id="596a4-224">Houd er rekening mee dat de opdrachten de cmdlet Get-CimInstance gebruiken.</span><span class="sxs-lookup"><span data-stu-id="596a4-224">Note that the commands use the Get-CimInstance cmdlet.</span></span>

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

<span data-ttu-id="596a4-225">Alle Opera Tors, met inbegrip van de like-Opera Tors, zijn geldig met de Opera tors or en en.</span><span class="sxs-lookup"><span data-stu-id="596a4-225">All operators, including the Like operators are valid with the Or and And operators.</span></span> <span data-ttu-id="596a4-226">En u kunt de Opera tors or en en en in één query combi neren met haakjes die Windows Power shell laten zien welke componenten eerst moeten worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="596a4-226">And, you can combine the Or and And operators in a single query with parentheses that tell Windows PowerShell which clauses to process first.</span></span>

<span data-ttu-id="596a4-227">Met deze opdracht wordt het Windows Power shell-vervolg teken (') gebruikt om de opdracht op twee regels te verdelen.</span><span class="sxs-lookup"><span data-stu-id="596a4-227">This command uses the Windows PowerShell continuation character (\`) divide the command into two lines.</span></span>

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a><span data-ttu-id="596a4-228">ZOEKEN NAAR NULL-WAARDEN</span><span class="sxs-lookup"><span data-stu-id="596a4-228">SEARCHING FOR NULL VALUES</span></span>

<span data-ttu-id="596a4-229">Zoeken naar Null-waarden in WMI is lastig, omdat dit kan leiden tot onvoorspelbare resultaten.</span><span class="sxs-lookup"><span data-stu-id="596a4-229">Searching for null values in WMI is challenging, because it can lead to unpredictable results.</span></span> <span data-ttu-id="596a4-230">Null is niet nul en is niet gelijk aan of een lege teken reeks.</span><span class="sxs-lookup"><span data-stu-id="596a4-230">Null is not zero and it is not equivalent or to an empty string.</span></span> <span data-ttu-id="596a4-231">Sommige eigenschappen van de WMI-klasse worden geïnitialiseerd en andere niet, dus het is niet mogelijk om een zoek opdracht voor NULL te gebruiken voor alle eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="596a4-231">Some WMI class properties are initialized and others are not, so a search for null might not work for all properties.</span></span>

<span data-ttu-id="596a4-232">Als u wilt zoeken naar Null-waarden, gebruikt u de operator is met de waarde Null.</span><span class="sxs-lookup"><span data-stu-id="596a4-232">To search for null values, use the Is operator with a value of "null".</span></span>

<span data-ttu-id="596a4-233">Met de volgende opdrachten worden bijvoorbeeld processen opgehaald die een null-waarde voor de eigenschap IntallDate hebben.</span><span class="sxs-lookup"><span data-stu-id="596a4-233">For example, the following commands get processes that have a null value for the IntallDate property.</span></span> <span data-ttu-id="596a4-234">De opdrachten retour neren veel processen.</span><span class="sxs-lookup"><span data-stu-id="596a4-234">The commands return many processes.</span></span>

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="596a4-235">Met de volgende opdracht worden daarentegen gebruikers accounts opgehaald die een null-waarde voor de eigenschap Description hebben.</span><span class="sxs-lookup"><span data-stu-id="596a4-235">In contrast, the following command, gets user accounts that have a null value for the Description property.</span></span> <span data-ttu-id="596a4-236">Met deze opdracht worden geen gebruikers accounts geretourneerd, hoewel de meeste gebruikers accounts geen waarde hebben voor de eigenschap Description.</span><span class="sxs-lookup"><span data-stu-id="596a4-236">This command does not return any user accounts, even though most user accounts do not have any value for the Description property.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="596a4-237">Als u wilt zoeken naar de gebruikers accounts die geen waarde hebben voor de eigenschap Description, gebruikt u de gelijkheids operator om een lege teken reeks op te halen.</span><span class="sxs-lookup"><span data-stu-id="596a4-237">To find the user accounts that have no value for the Description property, use the equality operator to get an empty string.</span></span> <span data-ttu-id="596a4-238">Gebruik twee opeenvolgende enkele aanhalings tekens om de lege teken reeks weer te geven.</span><span class="sxs-lookup"><span data-stu-id="596a4-238">To represent the empty string, use two consecutive single quotation marks.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a><span data-ttu-id="596a4-239">WAAR OF ONWAAR GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-239">USING TRUE OR FALSE</span></span>

<span data-ttu-id="596a4-240">Gebruik waar en ONWAAR om Booleaanse waarden in de eigenschappen van WMI-objecten op te halen.</span><span class="sxs-lookup"><span data-stu-id="596a4-240">To get Boolean values in the properties of WMI objects, use True and False.</span></span>
<span data-ttu-id="596a4-241">De waarden zijn niet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="596a4-241">They are not case sensitive.</span></span>

<span data-ttu-id="596a4-242">De volgende WQL-query retourneert alleen lokale gebruikers accounts van een computer die lid is van een domein.</span><span class="sxs-lookup"><span data-stu-id="596a4-242">The following WQL query returns only local user accounts from a domain joined computer.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

<span data-ttu-id="596a4-243">Als u domein accounts wilt zoeken, gebruikt u de waarde ONWAAR, zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="596a4-243">To find domain accounts, use a value of False, as shown in the following example.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a><span data-ttu-id="596a4-244">HET ESCAPE TEKEN GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="596a4-244">USING THE ESCAPE CHARACTER</span></span>

<span data-ttu-id="596a4-245">WQL maakt gebruik van de back slash ( \) als escape-teken.</span><span class="sxs-lookup"><span data-stu-id="596a4-245">WQL uses the backslash (\) as its escape character.</span></span> <span data-ttu-id="596a4-246">Dit wijkt af van Windows Power shell, dat gebruikmaakt van het apostroffen-teken (').</span><span class="sxs-lookup"><span data-stu-id="596a4-246">This is different from Windows PowerShell, which uses the backtick character (\`).</span></span>

<span data-ttu-id="596a4-247">Aanhalings tekens en de teken reeks die voor aanhalings tekens worden gebruikt, moeten vaak worden voorafgegaan zodat ze niet onjuist zijn geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="596a4-247">Quotation marks, and the characters used for quotation marks, often need to be escaped so that they are not misinterpreted.</span></span>

<span data-ttu-id="596a4-248">Als u een gebruiker wilt zoeken waarvan de naam één aanhalings teken bevat, gebruikt u een back slash om het enkele aanhalings teken te escapen, zoals wordt weer gegeven in de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="596a4-248">To find a user whose name includes a single quotation mark, use a backslash to escape the single quotation mark, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

<span data-ttu-id="596a4-249">In sommige gevallen moet de back slash ook worden ontsnapt.</span><span class="sxs-lookup"><span data-stu-id="596a4-249">In some case, the backslash also needs to be escaped.</span></span> <span data-ttu-id="596a4-250">Met de volgende opdrachten wordt bijvoorbeeld een ongeldige query fout gegenereerd vanwege de back slash in de waarde van het bijschrift.</span><span class="sxs-lookup"><span data-stu-id="596a4-250">For example, the following commands generate an Invalid Query error due to the backslash in the Caption value.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

<span data-ttu-id="596a4-251">Als u de back slash wilt escapeel, gebruikt u een tweede back slash-teken, zoals in de volgende opdracht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="596a4-251">To escape the backslash, use a second backslash character, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a><span data-ttu-id="596a4-252">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="596a4-252">SEE ALSO</span></span>

[<span data-ttu-id="596a4-253">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="596a4-253">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="596a4-254">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="596a4-254">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="596a4-255">about_WMI</span><span class="sxs-lookup"><span data-stu-id="596a4-255">about_WMI</span></span>](about_WMI.md)

[<span data-ttu-id="596a4-256">about_WMI_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="596a4-256">about_WMI_Cmdlets</span></span>](about_WMI_Cmdlets.md)
