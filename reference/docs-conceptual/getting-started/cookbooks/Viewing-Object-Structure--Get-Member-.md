---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Weergave Object structuur Get lid
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950740"
---
# <a name="viewing-object-structure-get-member"></a>Objectstructuur (Get-lid) weergeven

Omdat objecten wordt een centrale rol in Windows PowerShell spelen, zijn er verschillende ingebouwde opdrachten ontworpen voor gebruik met willekeurige objecttypen. Het belangrijkste instrument is de **Get-lid** opdracht.

De eenvoudigste methode voor het analyseren van de objecten die een opdracht wordt geretourneerd naar de uitvoer van de opdracht voor pipe is de **Get-lid** cmdlet. De **Get-lid** cmdlet ziet u de formele naam van het objecttype en een volledig overzicht van de bijbehorende leden. Het aantal elementen die worden geretourneerd soms enigszins overweldigend kan zijn. Een procesobject kan bijvoorbeeld meer dan 100 leden hebben.

Overzicht van alle leden van een proces-object en de uitvoer van de pagina zodat u alles kunt bekijken, typt u:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

De uitvoer van deze opdracht wordt als volgt uitzien:

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

Kunnen we deze lange lijst met informatie meer kan worden gebruikt met een filter voor elementen die we willen zien. De **Get-lid** opdracht kunt u alleen leden die eigenschappen zijn. Er zijn verschillende vormen van eigenschappen. Eigenschappen van elk type van de cmdlet worden weergegeven als we stellen de **Get-lid MemberType** -parameter voor de waarde **eigenschappen**. De resulterende lijst nog steeds erg lang zijn, maar een beetje beter kan worden beheerd:

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
> De toegestane waarden van MemberType zijn AliasProperty, CodeProperty eigenschap, NoteProperty, ScriptProperty, eigenschappen, PropertySet, methode, CodeMethod, ScriptMethod, methoden, ParameterizedProperty, ledenset en alle.

Er zijn meer dan 60 eigenschappen voor een proces. De Windows PowerShell toont vaak dat slechts een handvol eigenschappen voor een bekend object is dat ze alle reden zou een onbeheersbare hoeveelheid informatie opleveren.

> [!NOTE]
> Windows PowerShell bepaalt hoe u een objecttype dat u met behulp van informatie opgeslagen in XML-bestanden die eindigt op namen hebben. format.ps1xml. De indelingsgegevens voor proces-objecten die System.Diagnostics.Process .NET-objecten, wordt opgeslagen in DotNetTypes.format.ps1xml.

Als u nodig hebt om te kijken naar eigenschappen dan degene die standaard door Windows PowerShell wordt weergegeven, moet u de uitvoergegevens zelf formatteren. Dit kan worden gedaan met behulp van de indeling-cmdlets.