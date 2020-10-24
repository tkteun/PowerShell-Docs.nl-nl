---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Object structuur ophalen lid weer geven
description: Get-Member is een krachtig hulp programma waarmee het type en de structuur van objecten in Power shell kunnen worden weer geven.
ms.openlocfilehash: 3c294fe47294e2cf8daf125aac55661dd38cf9bb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501215"
---
# <a name="viewing-object-structure-get-member"></a>Objectstructuur weergeven (Get-Member)

Omdat objecten een dergelijke centrale rol spelen in Windows Power shell, zijn er verschillende systeem eigen opdrachten ontworpen om te werken met wille keurige object typen. De belangrijkste is de opdracht **Get-member** .

De eenvoudigste techniek voor het analyseren van de objecten die een opdracht retourneert, is om de uitvoer van die opdracht door te sluizen naar de cmdlet **Get-member** . De cmdlet **Get-member** toont u de formele naam van het object type en een volledig overzicht van de bijbehorende leden. Het aantal geretourneerde elementen kan soms overweldigend zijn. Zo kan een proces object meer dan 100 leden hebben.

Als u alle leden van een proces object en pagina de uitvoer wilt weer geven, typt u:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

De uitvoer van deze opdracht ziet er ongeveer als volgt uit:

```Output
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

We kunnen deze lange lijst met informatie bruikbaarder maken door te filteren op elementen die we willen zien. Met de opdracht **Get-member** kunt u alleen leden met eigenschappen weer geven. Er zijn verschillende soorten eigenschappen. Met de cmdlet worden eigenschappen van elk type weer gegeven als we de **Get-member member type-** para meter instellen op de waarde- **Eigenschappen**. De resulterende lijst is nog steeds erg lang, maar een beetje meer beheersbaar:

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
> De toegestane waarden van member type zijn AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, eigenschappen, PropertySet, method, CodeMethod, ScriptMethod, methoden, ParameterizedProperty, Memberset en all.

Er zijn meer dan 60 eigenschappen voor een proces. In Windows Power shell worden vaak slechts een aantal eigenschappen voor een bekend object weer gegeven, wat betekent dat ze een niet-beheerde hoeveelheid gegevens produceren.

> [!NOTE]
> Windows Power shell bepaalt hoe een object type moet worden weer gegeven met behulp van gegevens die zijn opgeslagen in XML-bestanden met namen die eindigen op .format.ps1XML. De opmaak gegevens voor proces objecten, die .NET System. Diagnostics. process-objecten, worden opgeslagen in DotNetTypes.format.ps1XML.

Als u andere eigenschappen wilt bekijken dan die in Windows Power Shell standaard worden weer gegeven, moet u de uitvoer gegevens zelf opmaken. U kunt dit doen met behulp van de Format-cmdlets.
