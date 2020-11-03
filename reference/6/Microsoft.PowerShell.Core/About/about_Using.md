---
description: Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 6001f2f4495490c9f2b9dbfbeac2e1f4298febd8
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253173"
---
# <a name="about-using"></a><span data-ttu-id="aecab-104">Over het gebruik van</span><span class="sxs-lookup"><span data-stu-id="aecab-104">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="aecab-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aecab-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="aecab-106">Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aecab-106">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="aecab-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aecab-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="aecab-108">Met de- `using` instructie kunt u opgeven welke naam ruimten in de sessie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aecab-108">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="aecab-109">Het toevoegen van naam ruimten vereenvoudigt het gebruik van .NET-klassen en-leden en biedt u de mogelijkheid om klassen uit script modules en assembly's te importeren.</span><span class="sxs-lookup"><span data-stu-id="aecab-109">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="aecab-110">De `using` instructies moeten vóór eventuele andere instructies in een script komen.</span><span class="sxs-lookup"><span data-stu-id="aecab-110">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="aecab-111">De `using` instructie mag niet worden verward met de `using:` aanpassings functie voor het bereik voor variabelen.</span><span class="sxs-lookup"><span data-stu-id="aecab-111">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="aecab-112">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aecab-112">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="aecab-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="aecab-113">Syntax</span></span>

<span data-ttu-id="aecab-114">.NET-naam ruimten opgeven waarvan u de typen wilt omzetten:</span><span class="sxs-lookup"><span data-stu-id="aecab-114">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="aecab-115">Klassen laden vanuit een Power shell-module:</span><span class="sxs-lookup"><span data-stu-id="aecab-115">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="aecab-116">Typen vooraf laden vanuit een .NET-assembly:</span><span class="sxs-lookup"><span data-stu-id="aecab-116">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
```

<span data-ttu-id="aecab-117">Het opgeven van een naam ruimte maakt het gemakkelijker om te verwijzen naar typen met hun korte namen.</span><span class="sxs-lookup"><span data-stu-id="aecab-117">Specifying a namespace makes it easier to reference types by their short names.</span></span>

<span data-ttu-id="aecab-118">Bij het laden van een assembly worden .NET-typen van de assembly geladen in een script tijdens het parseren.</span><span class="sxs-lookup"><span data-stu-id="aecab-118">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="aecab-119">Hierdoor kunt u nieuwe Power shell-klassen maken die gebruikmaken van typen van de vooraf geladen assembly.</span><span class="sxs-lookup"><span data-stu-id="aecab-119">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="aecab-120">Als u geen nieuwe Power shell-klassen maakt, gebruikt u `Add-Type` in plaats daarvan de-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aecab-120">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="aecab-121">Zie [add-type](xref:Microsoft.PowerShell.Utility.Add-Type)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aecab-121">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="aecab-122">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="aecab-122">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="aecab-123">Voor beeld 1: naam ruimten voor de TypeName-omzetting toevoegen</span><span class="sxs-lookup"><span data-stu-id="aecab-123">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="aecab-124">Met het volgende script wordt de cryptografische hash voor de teken reeks ' Hallo wereld ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="aecab-124">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="aecab-125">U ziet hoe `using namespace System.Text` en de `using namespace System.IO` verwijzingen naar `[UnicodeEncoding]` in `System.Text` en `[Stream]` en naar in worden vereenvoudigd `[MemoryStream]` `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="aecab-125">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

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

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="aecab-126">Voor beeld 2: klassen laden vanuit een script module</span><span class="sxs-lookup"><span data-stu-id="aecab-126">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="aecab-127">In dit voor beeld hebben we een Power shell-script module met de naam **CardGames** die de volgende klassen definieert:</span><span class="sxs-lookup"><span data-stu-id="aecab-127">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="aecab-128">**CardGames. Deck**</span><span class="sxs-lookup"><span data-stu-id="aecab-128">**CardGames.Deck**</span></span>
- <span data-ttu-id="aecab-129">**CardGames.-kaart**</span><span class="sxs-lookup"><span data-stu-id="aecab-129">**CardGames.Card**</span></span>

<span data-ttu-id="aecab-130">`Import-Module` en de `#requires` instructie importeren alleen de module functies, aliassen en variabelen, zoals gedefinieerd door de module.</span><span class="sxs-lookup"><span data-stu-id="aecab-130">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="aecab-131">Klassen zijn niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="aecab-131">Classes are not imported.</span></span> <span data-ttu-id="aecab-132">`using module`Met de opdracht wordt de module geïmporteerd en worden ook de klassedefinities geladen.</span><span class="sxs-lookup"><span data-stu-id="aecab-132">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="aecab-133">Voor beeld 3: klassen laden vanuit een assembly</span><span class="sxs-lookup"><span data-stu-id="aecab-133">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="aecab-134">In dit voor beeld wordt een assembly geladen zodat de klassen kunnen worden gebruikt voor het maken van nieuwe Power shell-klassen.</span><span class="sxs-lookup"><span data-stu-id="aecab-134">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="aecab-135">Met het volgende script maakt u een nieuwe Power shell-klasse die is afgeleid van de klasse **DirectoryContext** .</span><span class="sxs-lookup"><span data-stu-id="aecab-135">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

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
