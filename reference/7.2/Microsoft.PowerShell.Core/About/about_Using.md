---
description: Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt.
Locale: en-US
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: d08ada489ebe04ae51e3927486f354a8371de03f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892539"
---
# <a name="about-using"></a><span data-ttu-id="7d12f-103">Over het gebruik van</span><span class="sxs-lookup"><span data-stu-id="7d12f-103">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="7d12f-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7d12f-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7d12f-105">Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7d12f-105">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="7d12f-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7d12f-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="7d12f-107">Met de- `using` instructie kunt u opgeven welke naam ruimten in de sessie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7d12f-107">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="7d12f-108">Het toevoegen van naam ruimten vereenvoudigt het gebruik van .NET-klassen en-leden en biedt u de mogelijkheid om klassen uit script modules en assembly's te importeren.</span><span class="sxs-lookup"><span data-stu-id="7d12f-108">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="7d12f-109">De `using` instructies moeten vóór eventuele andere instructies in een script komen.</span><span class="sxs-lookup"><span data-stu-id="7d12f-109">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="7d12f-110">De `using` instructie mag niet worden verward met de `using:` aanpassings functie voor het bereik voor variabelen.</span><span class="sxs-lookup"><span data-stu-id="7d12f-110">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="7d12f-111">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7d12f-111">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="namespace-syntax"></a><span data-ttu-id="7d12f-112">Naam ruimte syntaxis</span><span class="sxs-lookup"><span data-stu-id="7d12f-112">Namespace syntax</span></span>

<span data-ttu-id="7d12f-113">.NET-naam ruimten opgeven waarvan u de typen wilt omzetten:</span><span class="sxs-lookup"><span data-stu-id="7d12f-113">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="7d12f-114">Het opgeven van een naam ruimte maakt het gemakkelijker om te verwijzen naar typen met hun korte namen.</span><span class="sxs-lookup"><span data-stu-id="7d12f-114">Specifying a namespace makes it easier to reference types by their short names.</span></span>

## <a name="module-syntax"></a><span data-ttu-id="7d12f-115">Module syntaxis</span><span class="sxs-lookup"><span data-stu-id="7d12f-115">Module syntax</span></span>

<span data-ttu-id="7d12f-116">Klassen laden vanuit een Power shell-module:</span><span class="sxs-lookup"><span data-stu-id="7d12f-116">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="7d12f-117">De waarde van `<module-name>` kan een module naam, een volledige module specificatie of een pad naar een module bestand zijn.</span><span class="sxs-lookup"><span data-stu-id="7d12f-117">The value of `<module-name>` can be a module name, a full module specification, or a path to a module file.</span></span>

<span data-ttu-id="7d12f-118">Wanneer `<module-name>` een pad is, kan het pad volledig gekwalificeerd of relatief zijn.</span><span class="sxs-lookup"><span data-stu-id="7d12f-118">When `<module-name>` is a path, the path can be fully qualified or relative.</span></span> <span data-ttu-id="7d12f-119">Een relatief pad wordt opgelost ten opzichte van het script dat de instructie using bevat.</span><span class="sxs-lookup"><span data-stu-id="7d12f-119">A relative path is resolved relative to the script that contains the using statement.</span></span>

<span data-ttu-id="7d12f-120">Wanneer `<module-name>` is een naam of module specificatie, zoekt Power shell de **PSModulePath** voor de opgegeven module.</span><span class="sxs-lookup"><span data-stu-id="7d12f-120">When `<module-name>` is a name or module specification, PowerShell searches the **PSModulePath** for the specified module.</span></span>

<span data-ttu-id="7d12f-121">Een module specificatie is een hash-tabel met de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="7d12f-121">A module specification is a hash table that has the following keys.</span></span>

- <span data-ttu-id="7d12f-122">`ModuleName` - **Vereist** Hiermee geeft u de module naam op.</span><span class="sxs-lookup"><span data-stu-id="7d12f-122">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="7d12f-123">`GUID` - **Optioneel** Hiermee geeft u de GUID van de module.</span><span class="sxs-lookup"><span data-stu-id="7d12f-123">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="7d12f-124">Het is ook **vereist** om een van de drie onderstaande sleutels op te geven.</span><span class="sxs-lookup"><span data-stu-id="7d12f-124">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="7d12f-125">Deze sleutels kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7d12f-125">These keys can't be used together.</span></span>
  - <span data-ttu-id="7d12f-126">`ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="7d12f-126">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="7d12f-127">`RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="7d12f-127">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="7d12f-128">`MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="7d12f-128">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

## <a name="assembly-syntax"></a><span data-ttu-id="7d12f-129">Assembly-syntaxis</span><span class="sxs-lookup"><span data-stu-id="7d12f-129">Assembly syntax</span></span>

<span data-ttu-id="7d12f-130">Typen vooraf laden vanuit een .NET-assembly:</span><span class="sxs-lookup"><span data-stu-id="7d12f-130">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="7d12f-131">Bij het laden van een assembly worden .NET-typen van de assembly geladen in een script tijdens het parseren.</span><span class="sxs-lookup"><span data-stu-id="7d12f-131">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="7d12f-132">Hierdoor kunt u nieuwe Power shell-klassen maken die gebruikmaken van typen van de vooraf geladen assembly.</span><span class="sxs-lookup"><span data-stu-id="7d12f-132">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="7d12f-133">Als u geen nieuwe Power shell-klassen maakt, gebruikt u `Add-Type` in plaats daarvan de-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d12f-133">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="7d12f-134">Zie [add-type](xref:Microsoft.PowerShell.Utility.Add-Type)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7d12f-134">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="7d12f-135">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="7d12f-135">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="7d12f-136">Voor beeld 1: naam ruimten voor de TypeName-omzetting toevoegen</span><span class="sxs-lookup"><span data-stu-id="7d12f-136">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="7d12f-137">Met het volgende script wordt de cryptografische hash voor de teken reeks ' Hallo wereld ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7d12f-137">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="7d12f-138">U ziet hoe `using namespace System.Text` en de `using namespace System.IO` verwijzingen naar `[UnicodeEncoding]` in `System.Text` en `[Stream]` en naar in worden vereenvoudigd `[MemoryStream]` `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="7d12f-138">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="7d12f-139">Voor beeld 2: klassen laden vanuit een script module</span><span class="sxs-lookup"><span data-stu-id="7d12f-139">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="7d12f-140">In dit voor beeld hebben we een Power shell-script module met de naam **CardGames** die de volgende klassen definieert:</span><span class="sxs-lookup"><span data-stu-id="7d12f-140">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="7d12f-141">**CardGames. Deck**</span><span class="sxs-lookup"><span data-stu-id="7d12f-141">**CardGames.Deck**</span></span>
- <span data-ttu-id="7d12f-142">**CardGames.-kaart**</span><span class="sxs-lookup"><span data-stu-id="7d12f-142">**CardGames.Card**</span></span>

<span data-ttu-id="7d12f-143">`Import-Module` en de `#requires` instructie importeren alleen de module functies, aliassen en variabelen, zoals gedefinieerd door de module.</span><span class="sxs-lookup"><span data-stu-id="7d12f-143">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="7d12f-144">Klassen zijn niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7d12f-144">Classes are not imported.</span></span> <span data-ttu-id="7d12f-145">`using module`Met de opdracht wordt de module geïmporteerd en worden ook de klassedefinities geladen.</span><span class="sxs-lookup"><span data-stu-id="7d12f-145">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="7d12f-146">Voor beeld 3: klassen laden vanuit een assembly</span><span class="sxs-lookup"><span data-stu-id="7d12f-146">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="7d12f-147">In dit voor beeld wordt een assembly geladen zodat de klassen kunnen worden gebruikt voor het maken van nieuwe Power shell-klassen.</span><span class="sxs-lookup"><span data-stu-id="7d12f-147">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="7d12f-148">Met het volgende script maakt u een nieuwe Power shell-klasse die is afgeleid van de klasse **DirectoryContext** .</span><span class="sxs-lookup"><span data-stu-id="7d12f-148">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```