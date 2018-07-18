---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: PowerShell-scripts
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094048"
---
# <a name="powershell"></a><span data-ttu-id="73e87-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="73e87-103">PowerShell</span></span>

<span data-ttu-id="73e87-104">Gebaseerd op .NET Framework en is PowerShell een taakgebaseerde opdrachtregel-shell en scripttaal; het is speciaal ontworpen voor beheerders en Hoofdgebruikers, voor het snel automatiseren van het beheer van meerdere besturingssystemen (Linux, Mac OS-, Unix- en Windows) en de processen met betrekking tot de toepassingen die op deze besturingssystemen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73e87-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="73e87-105">PowerShell is open-source</span><span class="sxs-lookup"><span data-stu-id="73e87-105">PowerShell is open source</span></span>

<span data-ttu-id="73e87-106">PowerShell-basis broncode is nu beschikbaar is in GitHub en geopend zodat u kunt bijdragen van de community.</span><span class="sxs-lookup"><span data-stu-id="73e87-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="73e87-107">Zie [PowerShell source op GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="73e87-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="73e87-108">U kunt beginnen met de bits die u nodig hebt in [ophalen PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="73e87-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="73e87-109">Of misschien met een korte Tour langs op [aan de slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="73e87-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="73e87-110">Ontwerpdoelstellingen van PowerShell</span><span class="sxs-lookup"><span data-stu-id="73e87-110">PowerShell design goals</span></span>
<span data-ttu-id="73e87-111">PowerShell is ontworpen voor het verbeteren van de opdrachtregel en scripting-omgeving door langdurige problemen en nieuwe functies toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="73e87-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="73e87-112">Zichtbaarheid</span><span class="sxs-lookup"><span data-stu-id="73e87-112">Discoverability</span></span>
<span data-ttu-id="73e87-113">PowerShell kunt gemakkelijk detecteren van de functies ervan.</span><span class="sxs-lookup"><span data-stu-id="73e87-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="73e87-114">Bijvoorbeeld, als u zoekt een lijst met cmdlets die bekijken en wijzigen van de Windows-services, typt u:</span><span class="sxs-lookup"><span data-stu-id="73e87-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="73e87-115">Nadat u ontdekte welke cmdlet voert een taak, u kunt meer informatie over de cmdlet met behulp van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73e87-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="73e87-116">Als u bijvoorbeeld op het Help-informatie weergeven over de `Get-Service` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="73e87-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="73e87-117">De meeste cmdlets introduceren objecten die kunnen worden bewerkt en vervolgens weergegeven in tekst om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="73e87-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="73e87-118">Doorsluizen voor volledig inzicht in de uitvoer van deze cmdlet, de uitvoer naar de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73e87-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="73e87-119">Bijvoorbeeld, de volgende opdracht geeft informatie weer over de leden van de uitvoer van object met de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73e87-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="73e87-120">Consistency</span><span class="sxs-lookup"><span data-stu-id="73e87-120">Consistency</span></span>
<span data-ttu-id="73e87-121">Systemen beheren kan een complexe inspanning en hulpprogramma's die u een consistente interface hebt help voor het beheren van de inherente complexiteit.</span><span class="sxs-lookup"><span data-stu-id="73e87-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="73e87-122">Helaas hebben geen opdrachtregelprogramma's of scripts COM-objecten is bekend dat voor de consistentie.</span><span class="sxs-lookup"><span data-stu-id="73e87-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="73e87-123">De consistentie van PowerShell is een van de primaire activa.</span><span class="sxs-lookup"><span data-stu-id="73e87-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="73e87-124">Als u informatie over het gebruik bijvoorbeeld de `Sort-Object` cmdlet, kunt u deze kennis gebruiken om te sorteren van de uitvoer van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73e87-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="73e87-125">U hoeft niet voor meer informatie over de verschillende sorteren routines van elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73e87-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="73e87-126">Ontwikkelaars van de cmdlet geen bovendien ontwerpen sorteren functies voor de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="73e87-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="73e87-127">PowerShell biedt hen een framework dat biedt de basisfuncties en zorgt ervoor dat ze consistent over veel aspecten van de interface.</span><span class="sxs-lookup"><span data-stu-id="73e87-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="73e87-128">Het framework wordt voorkomen dat enkele van de opties die doorgaans voor de ontwikkelaar worden geplaatst, maar hierna wordt de ontwikkeling van de cmdlets voor robuuste en eenvoudig te gebruiken veel eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="73e87-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="73e87-129">Interactieve en Scripting-omgevingen</span><span class="sxs-lookup"><span data-stu-id="73e87-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="73e87-130">PowerShell is een gecombineerde interactief en scripting-omgeving die hebt u toegang tot de opdrachtregelprogramma's en COM-objecten en ook kunt u de kracht van de .NET Framework Class Library (FCL) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="73e87-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="73e87-131">Deze omgeving worden bij de Windows-opdrachtprompt een interactieve omgeving met meerdere opdrachtregelprogramma's biedt verbeterd.</span><span class="sxs-lookup"><span data-stu-id="73e87-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="73e87-132">Het verbetert tevens bij Windows Script Host (WSH)-scripts, waarmee u kunnen meerdere opdrachtregelprogramma's en COM automation-objecten gebruiken, maar bieden een interactieve omgeving.</span><span class="sxs-lookup"><span data-stu-id="73e87-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="73e87-133">Door een combinatie van toegang tot al deze functies, PowerShell breidt de mogelijkheid van de interactieve gebruiker en schrijver van het script en systeembeheer gemakkelijker maakt.</span><span class="sxs-lookup"><span data-stu-id="73e87-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="73e87-134">Object-richting</span><span class="sxs-lookup"><span data-stu-id="73e87-134">Object Orientation</span></span>
<span data-ttu-id="73e87-135">Hoewel u met PowerShell werken door te typen van opdrachten in de tekst, moet PowerShell is gebaseerd op objecten, niet als tekst.</span><span class="sxs-lookup"><span data-stu-id="73e87-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="73e87-136">De uitvoer van een opdracht is een object.</span><span class="sxs-lookup"><span data-stu-id="73e87-136">The output of a command is an object.</span></span>
<span data-ttu-id="73e87-137">U kunt het uitvoerobject op verzenden naar een andere opdracht als invoer.</span><span class="sxs-lookup"><span data-stu-id="73e87-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="73e87-138">Als gevolg hiervan bevat PowerShell een vertrouwde-interface voor mensen met andere shells er is tijdens de introductie van een nieuwe en krachtige opdrachtregelprogramma paradigma.</span><span class="sxs-lookup"><span data-stu-id="73e87-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="73e87-139">Dit breidt het concept van het verzenden van gegevens tussen opdrachten kunt u voor het verzenden van objecten, in plaats van tekst.</span><span class="sxs-lookup"><span data-stu-id="73e87-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="73e87-140">Eenvoudig overgang naar het uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="73e87-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="73e87-141">PowerShell maakt het eenvoudig om een overgang te typen opdrachten interactief te maken en uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="73e87-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="73e87-142">U kunt de opdrachten kunt invoeren bij de PowerShell-opdrachtprompt voor het detecteren van de opdrachten die een taak uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="73e87-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="73e87-143">U kunt vervolgens deze opdrachten in een transcript of een geschiedenis opslaan voordat u ze naar een bestand voor gebruik als een script kopieert.</span><span class="sxs-lookup"><span data-stu-id="73e87-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
