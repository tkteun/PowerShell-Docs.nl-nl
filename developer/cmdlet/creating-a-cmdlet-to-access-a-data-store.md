---
title: Het maken van een Cmdlet voor toegang tot een Store gegevens | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 555baec08539403d3c15d1eca2b23eec0a874e49
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733941"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="881cf-102">Een cmdlet maken om toegang te krijgen tot een gegevensarchief</span><span class="sxs-lookup"><span data-stu-id="881cf-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="881cf-103">In deze sectie wordt beschreven hoe u een cmdlet die toegang heeft tot opgeslagen gegevens in een Windows PowerShell-provider maken.</span><span class="sxs-lookup"><span data-stu-id="881cf-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="881cf-104">Dit type cmdlet maakt gebruik van de infrastructuur van Windows PowerShell-provider van de Windows PowerShell-runtime en daarom de cmdlet-klasse moet zijn afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basisklasse.</span><span class="sxs-lookup"><span data-stu-id="881cf-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="881cf-105">De Select-Str cmdlet die hier worden beschreven kunt vinden en tekenreeksen in een bestand of object selecteren.</span><span class="sxs-lookup"><span data-stu-id="881cf-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="881cf-106">De patronen die wordt gebruikt voor het identificeren van de tekenreeks kunnen via expliciet worden opgegeven. de `Path` parameter van de cmdlet of impliciet via de `Script` parameter.</span><span class="sxs-lookup"><span data-stu-id="881cf-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="881cf-107">De cmdlet is ontworpen voor het gebruik van een Windows PowerShell-provider die is afgeleid van [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="881cf-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="881cf-108">De cmdlet kunt bijvoorbeeld opgeven de bestandssysteem-provider of de provider van de variabele die wordt geleverd door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="881cf-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="881cf-109">Zie voor meer informatie aboutWindows PowerShell-providers, [het ontwerpen van uw Windows PowerShell-provider](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="881cf-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="881cf-110">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="881cf-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="881cf-111">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="881cf-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="881cf-112">Deze cmdlet detecteert bepaalde tekenreeksen, zodat de hier gekozen naam van de term 'Selecteren' is gedefinieerd door de [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) klasse.</span><span class="sxs-lookup"><span data-stu-id="881cf-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="881cf-113">De naam van het zelfstandig naamwoord 'Str' wordt gebruikt omdat de cmdlet van tekenreeksen fungeert.</span><span class="sxs-lookup"><span data-stu-id="881cf-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="881cf-114">Houd er rekening mee dat de naam van de cmdlet werkwoord en een zelfstandig naamwoord naam van de cmdlet-klasse worden weergegeven in de onderstaande verklaring.</span><span class="sxs-lookup"><span data-stu-id="881cf-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="881cf-115">Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="881cf-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="881cf-116">De .NET-klasse voor deze cmdlet moet zijn afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basisklasse, omdat de ondersteuning die door de Windows PowerShell-runtime nodig zijn om beschikbaar te stellen van de Windows PowerShell-provider infrastructuur.</span><span class="sxs-lookup"><span data-stu-id="881cf-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="881cf-117">Houd er rekening mee dat deze cmdlet ook maakt gebruik van de klassen van de .NET Framework-reguliere expressies, zoals [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="881cf-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="881cf-118">De volgende code wordt de klassedefinitie van deze cmdlet Selecteer Str.</span><span class="sxs-lookup"><span data-stu-id="881cf-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="881cf-119">Deze cmdlet definieert een standaardparameter ingesteld door het toevoegen van de `DefaultParameterSetName` sleutelwoord kenmerk aan de klassendeclaratie van.</span><span class="sxs-lookup"><span data-stu-id="881cf-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="881cf-120">De standaard-parameterset `PatternParameterSet` wordt gebruikt als de `Script` parameter niet wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="881cf-121">Zie voor meer informatie over deze parameter is ingesteld, de `Pattern` en `Script` bespreking van de parameter in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="881cf-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="881cf-122">Parameters voor toegang tot de gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="881cf-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="881cf-123">Deze cmdlet definieert verschillende parameters waarmee de gebruiker toegang tot en opgeslagen gegevens te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="881cf-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="881cf-124">Deze parameters bevatten een `Path` parameter die aangeeft van de locatie van het gegevensarchief een `Pattern` parameter waarmee het patroon moet worden gebruikt in het zoekvak en verschillende andere parameters die ondersteuning bieden voor hoe de zoekopdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="881cf-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="881cf-125">Zie voor meer informatie over de basisprincipes van het definiëren van parameters [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="881cf-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="881cf-126">De Parameter Path declareren</span><span class="sxs-lookup"><span data-stu-id="881cf-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="881cf-127">Als u wilt zoeken in het gegevensarchief, moet deze cmdlet een Windows PowerShell-pad gebruiken voor het identificeren van de Windows PowerShell-provider die is ontworpen voor toegang tot het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="881cf-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="881cf-128">Daarom het definieert een `Path` parameter van het type string-matrix om aan te geven van de locatie van de provider.</span><span class="sxs-lookup"><span data-stu-id="881cf-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="881cf-129">Houd er rekening mee dat deze parameter deel uitmaakt van twee verschillende parametersets en dat er een alias.</span><span class="sxs-lookup"><span data-stu-id="881cf-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="881cf-130">Twee [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerken verklaren dat de `Path` parameter behoort tot de `ScriptParameterSet` en de `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="881cf-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="881cf-131">Zie voor meer informatie over parametersets [parametersets toe te voegen aan een Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="881cf-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="881cf-132">De [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk declareert een `PSPath` alias voor de `Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="881cf-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="881cf-133">Deze alias declareren wordt aanbevolen voor consistentie met andere cmdlets die toegang hebben tot de Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="881cf-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="881cf-134">Zie voor meer informatie aboutWindows PowerShell paden, 'PowerShell pad concepten' in [hoe Windows PowerShell werkt](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="881cf-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="881cf-135">De Parameter patroon declareren</span><span class="sxs-lookup"><span data-stu-id="881cf-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="881cf-136">Als u wilt opgeven om te zoeken naar patronen, deze cmdlet declareert een `Pattern` parameter die een matrix met tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="881cf-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="881cf-137">Een positief resultaat wordt geretourneerd wanneer een van de patronen zijn gevonden in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="881cf-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="881cf-138">Houd er rekening mee dat deze patronen in een matrix van gecompileerde reguliere expressies of een matrix van jokertekenpatronen gebruikt voor het letterlijke zoekopdrachten kunnen worden gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="881cf-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="881cf-139">Als deze parameter is opgegeven, de cmdlet maakt gebruik van de standaardset van de parameter `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="881cf-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="881cf-140">In dit geval wordt de cmdlet maakt gebruik van de patronen die u hier opgeeft om te selecteren van tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="881cf-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="881cf-141">Daarentegen de `Script` parameter kan ook worden gebruikt voor een script met de patronen.</span><span class="sxs-lookup"><span data-stu-id="881cf-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="881cf-142">De `Script` en `Pattern` parameters definiëren twee afzonderlijke parametersets, dus ze sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="881cf-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="881cf-143">Ondersteuning van zoekparameters declareren</span><span class="sxs-lookup"><span data-stu-id="881cf-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="881cf-144">Deze cmdlet definieert de volgende ondersteuning voor parameters die kunnen worden gebruikt voor het wijzigen van de zoekmogelijkheden van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="881cf-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="881cf-145">De `Script` parameter geeft u een scriptblok die kan worden gebruikt om u te bieden een zoekmechanisme alternatieve voor de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="881cf-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="881cf-146">Het script moet de patronen gebruikt om de overeenkomende bevatten en retourneren een [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span><span class="sxs-lookup"><span data-stu-id="881cf-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="881cf-147">Houd er rekening mee dat deze parameter is ook de unieke parameter waarmee de `ScriptParameterSet` parameterset.</span><span class="sxs-lookup"><span data-stu-id="881cf-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="881cf-148">Wanneer de Windows PowerShell-runtime ziet deze parameter, het maakt gebruik van alleen de parameters die deel uitmaken van de `ScriptParameterSet` parameterset.</span><span class="sxs-lookup"><span data-stu-id="881cf-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="881cf-149">De `SimpleMatch` parameter is een switchparameter die aangeeft of de cmdlet expliciet overeenkomt met de patronen zoals ze worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="881cf-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="881cf-150">Wanneer de gebruiker Hiermee geeft u de parameter op de opdrachtregel (`true`), de cmdlet maakt gebruik van de patronen zoals ze worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="881cf-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="881cf-151">Als de parameter niet wordt opgegeven (`false`), de cmdlet maakt gebruik van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="881cf-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="881cf-152">De standaardwaarde voor deze parameter is `false`.</span><span class="sxs-lookup"><span data-stu-id="881cf-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="881cf-153">De `CaseSensitive` parameter is een switchparameter die aangeeft of een hoofdlettergevoelige zoekopdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="881cf-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="881cf-154">Wanneer de gebruiker Hiermee geeft u de parameter op de opdrachtregel (`true`), de cmdlet controleert de hoofdletters en kleine letters van tekens bij het vergelijken van patronen.</span><span class="sxs-lookup"><span data-stu-id="881cf-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="881cf-155">Als de parameter niet wordt opgegeven (`false`), de cmdlet maakt geen onderscheid tussen hoofdletters en kleine letters.</span><span class="sxs-lookup"><span data-stu-id="881cf-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="881cf-156">Bijvoorbeeld zou "MyFile" en "myfile" beide worden geretourneerd als positieve treffers.</span><span class="sxs-lookup"><span data-stu-id="881cf-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="881cf-157">De standaardwaarde voor deze parameter is `false`.</span><span class="sxs-lookup"><span data-stu-id="881cf-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="881cf-158">De `Exclude` en `Include` parameters bepalen welke items die expliciet zijn uitgesloten van of opgenomen in het zoekvak.</span><span class="sxs-lookup"><span data-stu-id="881cf-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="881cf-159">Standaard wordt de cmdlet alle items zoeken in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="881cf-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="881cf-160">Echter, om te beperken de zoekopdracht uitgevoerd door de cmdlet, deze parameters kunnen worden gebruikt om expliciet aangeven items moeten worden opgenomen in het zoekvak of weggelaten.</span><span class="sxs-lookup"><span data-stu-id="881cf-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="881cf-161">Parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="881cf-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="881cf-162">Deze cmdlet maakt gebruik van twee parametersets (`ScriptParameterSet` en `PatternParameterSet`, dit is de standaardinstelling) als de namen van de twee parameter die wordt gebruikt in toegang tot gegevens.</span><span class="sxs-lookup"><span data-stu-id="881cf-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="881cf-163">`PatternParameterSet` de standaardset van de parameter is en wordt gebruikt als de `Pattern` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="881cf-164">`ScriptParameterSet` wordt gebruikt wanneer de gebruiker Hiermee geeft u een zoekmechanisme voor alternatieve via de `Script` parameter.</span><span class="sxs-lookup"><span data-stu-id="881cf-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="881cf-165">Zie voor meer informatie over parametersets [parametersets toe te voegen aan een Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="881cf-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="881cf-166">Invoer verwerking van methoden overschrijven</span><span class="sxs-lookup"><span data-stu-id="881cf-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="881cf-167">Cmdlets moet een of meer van de verwerking van methoden voor invoer overschrijven de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse.</span><span class="sxs-lookup"><span data-stu-id="881cf-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="881cf-168">Zie voor meer informatie over de van invoer-verwerkingsmethoden, [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="881cf-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="881cf-169">Deze cmdlet vervangt de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) gecompileerd aan de methode voor het bouwen van een matrix van reguliere expressies bij het opstarten.</span><span class="sxs-lookup"><span data-stu-id="881cf-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="881cf-170">Dit verhoogt de prestaties tijdens de zoekopdrachten die overeenkomen met eenvoudige niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="881cf-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="881cf-171">Deze cmdlet ook overschrijft de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het verwerken van de selecties die tekenreeks waarmee de gebruiker op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="881cf-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="881cf-172">Het schrijft de resultaten van de selectie van de tekenreeks in de vorm van een aangepast object door het aanroepen van een particulier **MatchString** methode.</span><span class="sxs-lookup"><span data-stu-id="881cf-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="881cf-173">Toegang krijgen tot inhoud</span><span class="sxs-lookup"><span data-stu-id="881cf-173">Accessing Content</span></span>

<span data-ttu-id="881cf-174">De cmdlet moet de provider aangegeven door de Windows PowerShell-pad, zodat deze toegang heeft tot de gegevens openen.</span><span class="sxs-lookup"><span data-stu-id="881cf-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="881cf-175">De [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object voor de runspace wordt gebruikt voor toegang tot de provider, terwijl de [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) eigenschap van de cmdlet wordt gebruikt voor het openen van de provider.</span><span class="sxs-lookup"><span data-stu-id="881cf-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="881cf-176">Toegang tot inhoud wordt geleverd door het ophalen van de [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) -object voor de provider geopend.</span><span class="sxs-lookup"><span data-stu-id="881cf-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="881cf-177">In dit voorbeeld selecteren Str-cmdlet gebruikt de [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) eigenschap om de inhoud om te scannen zichtbaar te maken.</span><span class="sxs-lookup"><span data-stu-id="881cf-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="881cf-178">Vervolgens kan worden aangeroepen de [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) methode, waarbij de vereiste Windows PowerShell-pad wordt doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="881cf-179">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="881cf-179">Code Sample</span></span>

<span data-ttu-id="881cf-180">De volgende code toont de uitvoering van deze versie van deze cmdlet Selecteer Str.</span><span class="sxs-lookup"><span data-stu-id="881cf-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="881cf-181">Houd er rekening mee dat deze code bevat de cmdlet-klasse, persoonlijke methoden die worden gebruikt door de cmdlet en de Windows PowerShell-module code die wordt gebruikt voor het registreren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="881cf-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="881cf-182">Zie voor meer informatie over het registreren van de cmdlet [het bouwen van de Cmdlet](#Defining-the-Cmdlet-Class).</span><span class="sxs-lookup"><span data-stu-id="881cf-182">For more information about registering the cmdlet, see [Building the Cmdlet](#Defining-the-Cmdlet-Class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="881cf-183">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="881cf-183">Building the Cmdlet</span></span>

<span data-ttu-id="881cf-184">Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="881cf-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="881cf-185">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="881cf-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="881cf-186">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="881cf-186">Testing the Cmdlet</span></span>

<span data-ttu-id="881cf-187">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="881cf-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="881cf-188">De volgende procedure kan worden gebruikt voor het testen van de voorbeeld-cmdlet Selecteer Str.</span><span class="sxs-lookup"><span data-stu-id="881cf-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="881cf-189">Start Windows PowerShell en zoek in het bestand notities voor exemplaren van de regels met de expressie '.NET'.</span><span class="sxs-lookup"><span data-stu-id="881cf-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="881cf-190">Houd er rekening mee dat de aanhalingstekens rond de naam van het pad alleen vereist zijn als het pad uit meer dan één woord bestaat.</span><span class="sxs-lookup"><span data-stu-id="881cf-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="881cf-191">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="881cf-192">Zoek in het bestand notities voor exemplaren van de regels met het woord "voorbij", gevolgd door andere tekst.</span><span class="sxs-lookup"><span data-stu-id="881cf-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="881cf-193">De `SimpleMatch` parameter met behulp van de standaardwaarde van `false`.</span><span class="sxs-lookup"><span data-stu-id="881cf-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="881cf-194">De zoekopdracht is niet hoofdlettergevoelig omdat de `CaseSensitive` parameter is ingesteld op `false`.</span><span class="sxs-lookup"><span data-stu-id="881cf-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="881cf-195">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="881cf-196">Zoek in de opmerkingen bij de-bestand met een reguliere expressie als het patroon.</span><span class="sxs-lookup"><span data-stu-id="881cf-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="881cf-197">De cmdlet zoekt naar alfabetische tekens en spaties tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="881cf-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="881cf-198">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="881cf-199">Een hoofdlettergevoelige zoekactie van het bestand notities voor instanties van het woord 'Parameter' uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="881cf-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="881cf-200">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="881cf-201">Zoeken in de variabele-provider wordt geleverd met Windows PowerShell voor variabelen die numerieke waarden van 0 t/m 9 bevatten.</span><span class="sxs-lookup"><span data-stu-id="881cf-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="881cf-202">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="881cf-203">Gebruik een scriptblok om te zoeken naar het bestand SelectStrCommandSample.cs voor de tekenreeks 'Pos'.</span><span class="sxs-lookup"><span data-stu-id="881cf-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="881cf-204">De **cmatch** functie voor het script een niet-hoofdlettergevoelig patroon wordt gevonden voert.</span><span class="sxs-lookup"><span data-stu-id="881cf-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="881cf-205">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="881cf-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="881cf-206">Zie ook</span><span class="sxs-lookup"><span data-stu-id="881cf-206">See Also</span></span>

[<span data-ttu-id="881cf-207">Over het maken van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="881cf-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="881cf-208">Het maken van uw eerste Cmdlet</span><span class="sxs-lookup"><span data-stu-id="881cf-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="881cf-209">Het maken van een Cmdlet die Hiermee wijzigt u het systeem</span><span class="sxs-lookup"><span data-stu-id="881cf-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="881cf-210">Ontwerp van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="881cf-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="881cf-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="881cf-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="881cf-212">[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="881cf-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="881cf-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="881cf-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
