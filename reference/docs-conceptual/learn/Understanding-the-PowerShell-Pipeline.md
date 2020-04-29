---
ms.date: 08/23/2018
keywords: Power shell, cmdlet
title: Informatie over Power shell-pijp lijnen
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030391"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="504a8-103">Pijp lijnen</span><span class="sxs-lookup"><span data-stu-id="504a8-103">Understanding pipelines</span></span>

<span data-ttu-id="504a8-104">Pijp lijnen fungeren als een reeks verbonden segmenten van pipes.</span><span class="sxs-lookup"><span data-stu-id="504a8-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="504a8-105">Items die langs de pijp lijn worden verplaatst, passeren elk segment.</span><span class="sxs-lookup"><span data-stu-id="504a8-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="504a8-106">Als u een pijp lijn in Power shell wilt maken, verbindt u opdrachten samen met de pipe-operator |.</span><span class="sxs-lookup"><span data-stu-id="504a8-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="504a8-107">De uitvoer van elke opdracht wordt gebruikt als invoer voor de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="504a8-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="504a8-108">De notatie die wordt gebruikt voor pijp lijnen, is vergelijkbaar met de notatie die wordt gebruikt in andere schalen.</span><span class="sxs-lookup"><span data-stu-id="504a8-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="504a8-109">In eerste instantie is het mogelijk niet duidelijk hoe pijp lijnen anders zijn in Power shell.</span><span class="sxs-lookup"><span data-stu-id="504a8-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="504a8-110">Hoewel er tekst op het scherm wordt weer gegeven, Power shell pipes-objecten, geen tekst, tussen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="504a8-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="504a8-111">De Power shell-pijp lijn</span><span class="sxs-lookup"><span data-stu-id="504a8-111">The PowerShell pipeline</span></span>

<span data-ttu-id="504a8-112">Pijp lijnen zijn weliswaar het meest waardevolle concept dat wordt gebruikt in opdracht regel interfaces.</span><span class="sxs-lookup"><span data-stu-id="504a8-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="504a8-113">Wanneer u correct gebruikt, kunnen pijp lijnen de moeite van het gebruik van complexe opdrachten verminderen en is het eenvoudiger om de werk stroom voor de opdrachten te zien.</span><span class="sxs-lookup"><span data-stu-id="504a8-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="504a8-114">Elke opdracht in een pijp lijn (een pijplijn element genoemd) geeft de uitvoer door aan de volgende opdracht in de pijp lijn, item-per-item.</span><span class="sxs-lookup"><span data-stu-id="504a8-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="504a8-115">Opdrachten hoeven niet meer dan één item tegelijk te verwerken.</span><span class="sxs-lookup"><span data-stu-id="504a8-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="504a8-116">Het resultaat is een gereduceerd Resource verbruik en de mogelijkheid om de uitvoer onmiddellijk te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="504a8-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="504a8-117">Als u bijvoorbeeld de `Out-Host` cmdlet gebruikt om een pagina-op-pagina weer te geven van uitvoer van een andere opdracht, ziet de uitvoer er net zo uit als de normale tekst die op het scherm wordt weer gegeven, onderverdeeld in pagina's:</span><span class="sxs-lookup"><span data-stu-id="504a8-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="504a8-118">Paginering vermindert ook het `Out-Host` CPU-gebruik omdat er een volledige pagina kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="504a8-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="504a8-119">De cmdlets die voorafgaan aan de pijp lijn worden uitgevoerd, totdat de volgende pagina van uitvoer beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="504a8-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="504a8-120">U kunt zien hoe pijpleidingen het CPU-en geheugen gebruik in Windows taak beheer beïnvloedt door de volgende opdrachten te vergelijken:</span><span class="sxs-lookup"><span data-stu-id="504a8-120">You can see how piping impacts CPU and memory usage in the Windows Task Manager by comparing the following commands:</span></span>

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> <span data-ttu-id="504a8-121">De **paginerings** parameter wordt niet ondersteund door alle Power shell-hosts.</span><span class="sxs-lookup"><span data-stu-id="504a8-121">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="504a8-122">Wanneer u bijvoorbeeld probeert de para meter **paging** te gebruiken in Power shell ISE, ziet u de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="504a8-122">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="504a8-123">Objecten in de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="504a8-123">Objects in the pipeline</span></span>

<span data-ttu-id="504a8-124">Wanneer u een cmdlet in Power shell uitvoert, wordt tekst uitvoer weer gegeven, omdat het nodig is om objecten als tekst in een console venster aan te duiden.</span><span class="sxs-lookup"><span data-stu-id="504a8-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="504a8-125">In de tekst uitvoer worden mogelijk niet alle eigenschappen weer gegeven van het object dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="504a8-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="504a8-126">Denk bijvoorbeeld aan de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="504a8-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="504a8-127">Als u uitvoert `Get-Location` terwijl uw huidige locatie de hoofdmap van station C is, ziet u de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="504a8-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="504a8-128">De tekst uitvoer is een samen vatting van informatie, niet een volledige weer gave van het object `Get-Location`dat wordt geretourneerd door.</span><span class="sxs-lookup"><span data-stu-id="504a8-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="504a8-129">De kop in de uitvoer wordt toegevoegd door het proces waarmee de gegevens voor het scherm worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="504a8-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="504a8-130">Wanneer u de uitvoer naar de `Get-Member` cmdlet Pipet, krijgt u informatie over het object `Get-Location`dat wordt geretourneerd door.</span><span class="sxs-lookup"><span data-stu-id="504a8-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="504a8-131">`Get-Location`retourneert een **PathInfo** -object dat het huidige pad en andere informatie bevat.</span><span class="sxs-lookup"><span data-stu-id="504a8-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
