---
description: Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: ff6b43c3af1deddb5cb1b4c2e2c86a2cc2cac5d4
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253165"
---
# <a name="about-using"></a>Over het gebruik van

## <a name="short-description"></a>KORTE BESCHRIJVING
Hiermee kunt u aangeven welke naam ruimten in de sessie worden gebruikt.

## <a name="long-description"></a>LANGE BESCHRIJVING

Met de- `using` instructie kunt u opgeven welke naam ruimten in de sessie worden gebruikt. Het toevoegen van naam ruimten vereenvoudigt het gebruik van .NET-klassen en-leden en biedt u de mogelijkheid om klassen uit script modules en assembly's te importeren.

De `using` instructies moeten vóór eventuele andere instructies in een script komen.

De `using` instructie mag niet worden verward met de `using:` aanpassings functie voor het bereik voor variabelen. Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.

## <a name="syntax"></a>Syntax

.NET-naam ruimten opgeven waarvan u de typen wilt omzetten:

```
using namespace <.NET-namespace>
```

Klassen laden vanuit een Power shell-module:

```
using module <module-name>
```

Typen vooraf laden vanuit een .NET-assembly:

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

Het opgeven van een naam ruimte maakt het gemakkelijker om te verwijzen naar typen met hun korte namen.

Bij het laden van een assembly worden .NET-typen van de assembly geladen in een script tijdens het parseren. Hierdoor kunt u nieuwe Power shell-klassen maken die gebruikmaken van typen van de vooraf geladen assembly.

In Windows Power shell 5,1 kunt u de assembly laden door de naam van het pad of de naam. Wanneer u de naam gebruikt, zoekt Power shell in de globale assembly-cache van .NET (GAC) voor de bijbehorende assembly.

Als u geen nieuwe Power shell-klassen maakt, gebruikt u `Add-Type` in plaats daarvan de-cmdlet. Zie [add-type](xref:Microsoft.PowerShell.Utility.Add-Type)voor meer informatie.

## <a name="examples"></a>Voorbeelden

### <a name="example-1---add-namespaces-for-typename-resolution"></a>Voor beeld 1: naam ruimten voor de TypeName-omzetting toevoegen

Met het volgende script wordt de cryptografische hash voor de teken reeks ' Hallo wereld ' opgehaald.

U ziet hoe `using namespace System.Text` en de `using namespace System.IO` verwijzingen naar `[UnicodeEncoding]` in `System.Text` en `[Stream]` en naar in worden vereenvoudigd `[MemoryStream]` `System.IO` .

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

### <a name="example-2---load-classes-from-a-script-module"></a>Voor beeld 2: klassen laden vanuit een script module

In dit voor beeld hebben we een Power shell-script module met de naam **CardGames** die de volgende klassen definieert:

- **CardGames. Deck**
- **CardGames.-kaart**

`Import-Module` en de `#requires` instructie importeren alleen de module functies, aliassen en variabelen, zoals gedefinieerd door de module. Klassen zijn niet geïmporteerd. `using module`Met de opdracht wordt de module geïmporteerd en worden ook de klassedefinities geladen.

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a>Voor beeld 3: klassen laden vanuit een assembly

In dit voor beeld wordt een assembly geladen zodat de klassen kunnen worden gebruikt voor het maken van nieuwe Power shell-klassen. Met het volgende script maakt u een nieuwe Power shell-klasse die is afgeleid van de klasse **DirectoryContext** .

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
