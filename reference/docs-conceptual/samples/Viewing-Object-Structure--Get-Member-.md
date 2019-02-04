---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Structuur weergeven-Get Objectlid
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687865"
---
# <a name="viewing-object-structure-get-member"></a>Objectstructuur weergeven (Get-Member)

Omdat objecten een centrale rol in Windows PowerShell spelen, zijn er diverse systeemeigen opdrachten die zijn ontworpen voor gebruik met willekeurige objecttypen. Het belangrijkste is de **Get-Member** opdracht.

De eenvoudigste methode voor het analyseren van de objecten die een opdracht retourneert is het doorgeven van de uitvoer van deze opdracht de **Get-Member** cmdlet. De **Get-Member** cmdlet ziet u de formele naam van het objecttype en een volledige lijst met de bijbehorende leden. Het aantal elementen die worden geretourneerd kan soms overweldigend zijn. Een procesobject kan bijvoorbeeld meer dan 100 leden hebben.

Als u wilt zien alle leden van een proces-object en de pagina de uitvoer, zodat u alles kunt bekijken, typt u:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

De uitvoer van deze opdracht ziet er ongeveer als volgt:

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

We kunnen deze lange lijst met informatie beter bruikbaar maken door te filteren op elementen die we willen zien. De **Get-Member** opdracht kunt u alleen leden die eigenschappen zijn. Er zijn verschillende vormen van eigenschappen. Eigenschappen van elk type van de cmdlet worden weergegeven als we stellen de **Get-Member MemberType** parameter met de waarde **eigenschappen**. De resulterende lijst nog steeds erg lang duurt, maar iets beter beheersbare:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> De toegestane waarden van MemberType zijn AliasProperty, CodeProperty, eigenschap, NoteProperty, ScriptProperty, eigenschappen, PropertySet, methode, CodeMethod, ScriptMethod, methoden, ParameterizedProperty, ledenset en alle.

Er zijn meer dan 60 eigenschappen voor een proces. De Windows PowerShell vaak ziet u dat slechts een handvol eigenschappen voor een bekende object is dat ze allemaal met reden geeft als resultaat een onbeheersbare hoeveelheid gegevens.

> [!NOTE]
> Windows PowerShell wordt bepaald hoe een objecttype weergeven met behulp van gegevens die zijn opgeslagen in de XML-bestanden die namen hebben die eindigt op hebben. format.ps1xml. Het opmaken van gegevens voor proces-objecten die System.Diagnostics.Process .NET-objecten zijn, is opgeslagen in DotNetTypes.format.ps1xml.

Als u nodig hebt om te kijken naar eigenschappen dan die standaard door Windows PowerShell wordt weergegeven, moet u de uitvoergegevens zelf te formatteren. Dit kan worden gedaan met behulp van de indeling-cmdlets.