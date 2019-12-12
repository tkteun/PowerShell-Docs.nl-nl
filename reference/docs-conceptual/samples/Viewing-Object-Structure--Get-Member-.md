---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Object structuur ophalen lid weer geven
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030716"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="53aaa-103">Object structuur weer geven (Get-member)</span><span class="sxs-lookup"><span data-stu-id="53aaa-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="53aaa-104">Omdat objecten een dergelijke centrale rol spelen in Windows Power shell, zijn er verschillende systeem eigen opdrachten ontworpen om te werken met wille keurige object typen.</span><span class="sxs-lookup"><span data-stu-id="53aaa-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="53aaa-105">De belangrijkste is de opdracht **Get-member** .</span><span class="sxs-lookup"><span data-stu-id="53aaa-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="53aaa-106">De eenvoudigste techniek voor het analyseren van de objecten die een opdracht retourneert, is om de uitvoer van die opdracht door te sluizen naar de cmdlet **Get-member** .</span><span class="sxs-lookup"><span data-stu-id="53aaa-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="53aaa-107">De cmdlet **Get-member** toont u de formele naam van het object type en een volledig overzicht van de bijbehorende leden.</span><span class="sxs-lookup"><span data-stu-id="53aaa-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="53aaa-108">Het aantal geretourneerde elementen kan soms overweldigend zijn.</span><span class="sxs-lookup"><span data-stu-id="53aaa-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="53aaa-109">Zo kan een proces object meer dan 100 leden hebben.</span><span class="sxs-lookup"><span data-stu-id="53aaa-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="53aaa-110">Als u alle leden van een proces object en pagina de uitvoer wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="53aaa-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="53aaa-111">De uitvoer van deze opdracht ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="53aaa-111">The output from this command will look something like this:</span></span>

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

<span data-ttu-id="53aaa-112">We kunnen deze lange lijst met informatie bruikbaarder maken door te filteren op elementen die we willen zien.</span><span class="sxs-lookup"><span data-stu-id="53aaa-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="53aaa-113">Met de opdracht **Get-member** kunt u alleen leden met eigenschappen weer geven.</span><span class="sxs-lookup"><span data-stu-id="53aaa-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="53aaa-114">Er zijn verschillende soorten eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="53aaa-114">There are several forms of properties.</span></span> <span data-ttu-id="53aaa-115">Met de cmdlet worden eigenschappen van elk type weer gegeven als we de **Get-member member type-** para meter instellen op de waarde- **Eigenschappen**.</span><span class="sxs-lookup"><span data-stu-id="53aaa-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="53aaa-116">De resulterende lijst is nog steeds erg lang, maar een beetje meer beheersbaar:</span><span class="sxs-lookup"><span data-stu-id="53aaa-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="53aaa-117">De toegestane waarden van member type zijn AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, eigenschappen, PropertySet, method, CodeMethod, ScriptMethod, methoden, ParameterizedProperty, Memberset en all.</span><span class="sxs-lookup"><span data-stu-id="53aaa-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="53aaa-118">Er zijn meer dan 60 eigenschappen voor een proces.</span><span class="sxs-lookup"><span data-stu-id="53aaa-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="53aaa-119">In Windows Power shell worden vaak slechts een aantal eigenschappen voor een bekend object weer gegeven, wat betekent dat ze een niet-beheerde hoeveelheid gegevens produceren.</span><span class="sxs-lookup"><span data-stu-id="53aaa-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="53aaa-120">Windows Power shell bepaalt hoe een object type moet worden weer gegeven met behulp van gegevens die zijn opgeslagen in XML-bestanden met namen die eindigen op. Format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="53aaa-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="53aaa-121">De opmaak gegevens voor proces objecten, die .NET System. Diagnostics. process-objecten, worden opgeslagen in DotNetTypes. Format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="53aaa-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="53aaa-122">Als u andere eigenschappen wilt bekijken dan die in Windows Power Shell standaard worden weer gegeven, moet u de uitvoer gegevens zelf opmaken.</span><span class="sxs-lookup"><span data-stu-id="53aaa-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="53aaa-123">U kunt dit doen met behulp van de Format-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="53aaa-123">This can be done by using the format cmdlets.</span></span>
