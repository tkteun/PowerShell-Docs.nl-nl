---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Weergave Object structuur Get lid
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: 618f34bca7bfb76ce5d48ada642a687e279c8aad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/31/2017
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="91f30-103">Objectstructuur (Get-lid) weergeven</span><span class="sxs-lookup"><span data-stu-id="91f30-103">Viewing Object Structure (Get-Member)</span></span>
<span data-ttu-id="91f30-104">Omdat objecten wordt een centrale rol in Windows PowerShell spelen, zijn er verschillende ingebouwde opdrachten ontworpen voor gebruik met willekeurige objecttypen.</span><span class="sxs-lookup"><span data-stu-id="91f30-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="91f30-105">Het belangrijkste instrument is de **Get-lid** opdracht.</span><span class="sxs-lookup"><span data-stu-id="91f30-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="91f30-106">De eenvoudigste methode voor het analyseren van de objecten die een opdracht wordt geretourneerd naar de uitvoer van de opdracht voor pipe is de **Get-lid** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91f30-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="91f30-107">De **Get-lid** cmdlet ziet u de formele naam van het objecttype en een volledig overzicht van de bijbehorende leden.</span><span class="sxs-lookup"><span data-stu-id="91f30-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="91f30-108">Het aantal elementen die worden geretourneerd soms enigszins overweldigend kan zijn.</span><span class="sxs-lookup"><span data-stu-id="91f30-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="91f30-109">Een procesobject kan bijvoorbeeld meer dan 100 leden hebben.</span><span class="sxs-lookup"><span data-stu-id="91f30-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="91f30-110">Overzicht van alle leden van een proces-object en de uitvoer van de pagina zodat u alles kunt bekijken, typt u:</span><span class="sxs-lookup"><span data-stu-id="91f30-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="91f30-111">De uitvoer van deze opdracht wordt als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="91f30-111">The output from this command will look something like this:</span></span>

```
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

<span data-ttu-id="91f30-112">Kunnen we deze lange lijst met informatie meer kan worden gebruikt met een filter voor elementen die we willen zien.</span><span class="sxs-lookup"><span data-stu-id="91f30-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="91f30-113">De **Get-lid** opdracht kunt u alleen leden die eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="91f30-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="91f30-114">Er zijn verschillende vormen van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="91f30-114">There are several forms of properties.</span></span> <span data-ttu-id="91f30-115">Eigenschappen van elk type van de cmdlet worden weergegeven als we stellen de **Get-lid MemberType** -parameter voor de waarde **eigenschappen**.</span><span class="sxs-lookup"><span data-stu-id="91f30-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="91f30-116">De resulterende lijst nog steeds erg lang zijn, maar een beetje beter kan worden beheerd:</span><span class="sxs-lookup"><span data-stu-id="91f30-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="91f30-117">De toegestane waarden van MemberType zijn AliasProperty, CodeProperty eigenschap, NoteProperty, ScriptProperty, eigenschappen, PropertySet, methode, CodeMethod, ScriptMethod, methoden, ParameterizedProperty, ledenset en alle.</span><span class="sxs-lookup"><span data-stu-id="91f30-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="91f30-118">Er zijn meer dan 60 eigenschappen voor een proces.</span><span class="sxs-lookup"><span data-stu-id="91f30-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="91f30-119">De Windows PowerShell toont vaak dat slechts een handvol eigenschappen voor een bekend object is dat ze alle reden zou een onbeheersbare hoeveelheid informatie opleveren.</span><span class="sxs-lookup"><span data-stu-id="91f30-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="91f30-120">Windows PowerShell bepaalt hoe u een objecttype dat u met behulp van informatie opgeslagen in XML-bestanden die eindigt op namen hebben. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="91f30-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="91f30-121">De indelingsgegevens voor proces-objecten die System.Diagnostics.Process .NET-objecten, wordt opgeslagen in DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="91f30-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="91f30-122">Als u nodig hebt om te kijken naar eigenschappen dan degene die standaard door Windows PowerShell wordt weergegeven, moet u de uitvoergegevens zelf formatteren.</span><span class="sxs-lookup"><span data-stu-id="91f30-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="91f30-123">Dit kan worden gedaan met behulp van de indeling-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="91f30-123">This can be done by using the format cmdlets.</span></span>

