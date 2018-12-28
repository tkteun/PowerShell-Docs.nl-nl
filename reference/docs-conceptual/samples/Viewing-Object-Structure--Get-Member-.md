---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Structuur weergeven-Get Objectlid
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404498"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="c3fc0-103">Objectstructuur weergeven (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="c3fc0-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="c3fc0-104">Omdat objecten een centrale rol in Windows PowerShell spelen, zijn er diverse systeemeigen opdrachten die zijn ontworpen voor gebruik met willekeurige objecttypen.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="c3fc0-105">Het belangrijkste is de **Get-Member** opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="c3fc0-106">De eenvoudigste methode voor het analyseren van de objecten die een opdracht retourneert is het doorgeven van de uitvoer van deze opdracht de **Get-Member** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="c3fc0-107">De **Get-Member** cmdlet ziet u de formele naam van het objecttype en een volledige lijst met de bijbehorende leden.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="c3fc0-108">Het aantal elementen die worden geretourneerd kan soms overweldigend zijn.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="c3fc0-109">Een procesobject kan bijvoorbeeld meer dan 100 leden hebben.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="c3fc0-110">Als u wilt zien alle leden van een proces-object en de pagina de uitvoer, zodat u alles kunt bekijken, typt u:</span><span class="sxs-lookup"><span data-stu-id="c3fc0-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="c3fc0-111">De uitvoer van deze opdracht ziet er ongeveer als volgt:</span><span class="sxs-lookup"><span data-stu-id="c3fc0-111">The output from this command will look something like this:</span></span>

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

<span data-ttu-id="c3fc0-112">We kunnen deze lange lijst met informatie beter bruikbaar maken door te filteren op elementen die we willen zien.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="c3fc0-113">De **Get-Member** opdracht kunt u alleen leden die eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="c3fc0-114">Er zijn verschillende vormen van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-114">There are several forms of properties.</span></span> <span data-ttu-id="c3fc0-115">Eigenschappen van elk type van de cmdlet worden weergegeven als we stellen de **Get-Member MemberType** parameter met de waarde **eigenschappen**.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="c3fc0-116">De resulterende lijst nog steeds erg lang duurt, maar iets beter beheersbare:</span><span class="sxs-lookup"><span data-stu-id="c3fc0-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="c3fc0-117">De toegestane waarden van MemberType zijn AliasProperty, CodeProperty, eigenschap, NoteProperty, ScriptProperty, eigenschappen, PropertySet, methode, CodeMethod, ScriptMethod, methoden, ParameterizedProperty, ledenset en alle.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="c3fc0-118">Er zijn meer dan 60 eigenschappen voor een proces.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="c3fc0-119">De Windows PowerShell vaak ziet u dat slechts een handvol eigenschappen voor een bekende object is dat ze allemaal met reden geeft als resultaat een onbeheersbare hoeveelheid gegevens.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="c3fc0-120">Windows PowerShell wordt bepaald hoe een objecttype weergeven met behulp van gegevens die zijn opgeslagen in de XML-bestanden die namen hebben die eindigt op hebben. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="c3fc0-121">Het opmaken van gegevens voor proces-objecten die System.Diagnostics.Process .NET-objecten zijn, is opgeslagen in DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="c3fc0-122">Als u nodig hebt om te kijken naar eigenschappen dan die standaard door Windows PowerShell wordt weergegeven, moet u de uitvoergegevens zelf te formatteren.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="c3fc0-123">Dit kan worden gedaan met behulp van de indeling-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c3fc0-123">This can be done by using the format cmdlets.</span></span>