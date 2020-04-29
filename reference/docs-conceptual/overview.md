---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: PowerShell-scripts
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "62058485"
---
# <a name="powershell"></a><span data-ttu-id="0209e-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0209e-103">PowerShell</span></span>

<span data-ttu-id="0209e-104">Power shell is een op taken gebaseerde opdracht regel shell en script taal die is gebaseerd op .NET.</span><span class="sxs-lookup"><span data-stu-id="0209e-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="0209e-105">Power shell helpt systeem beheerders en hoofd gebruikers om snel taken te automatiseren die besturings systemen (Linux, macOS en Windows) en processen beheren.</span><span class="sxs-lookup"><span data-stu-id="0209e-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="0209e-106">Met Power shell-opdrachten kunt u computers beheren vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="0209e-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="0209e-107">Met Power shell-providers kunt u toegang krijgen tot gegevens archieven, zoals het REGI ster en het certificaat archief, net zo eenvoudig als u toegang hebt tot het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="0209e-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="0209e-108">Power shell bevat een uitgebreide expressie-parser en een volledig ontwikkelde script taal.</span><span class="sxs-lookup"><span data-stu-id="0209e-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="0209e-109">Power shell is open source</span><span class="sxs-lookup"><span data-stu-id="0209e-109">PowerShell is open-source</span></span>

<span data-ttu-id="0209e-110">Power shell-basis bron code is nu beschikbaar in GitHub en open voor bijdragen van de community.</span><span class="sxs-lookup"><span data-stu-id="0209e-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="0209e-111">Zie [Power shell-bron op github](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="0209e-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="0209e-112">U kunt beginnen met de bits die u nodig hebt om [Power shell](https://github.com/PowerShell/PowerShell#get-powershell)op te halen.</span><span class="sxs-lookup"><span data-stu-id="0209e-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="0209e-113">Of, misschien, met een korte rond leiding om aan de [slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)te gaan.</span><span class="sxs-lookup"><span data-stu-id="0209e-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="0209e-114">Power shell-ontwerp doelen</span><span class="sxs-lookup"><span data-stu-id="0209e-114">PowerShell design goals</span></span>

<span data-ttu-id="0209e-115">Power shell is ontworpen voor het verbeteren van de opdracht regel-en script omgeving door langdurige problemen te elimineren en nieuwe functies toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="0209e-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="0209e-116">Detectie</span><span class="sxs-lookup"><span data-stu-id="0209e-116">Discoverability</span></span>

<span data-ttu-id="0209e-117">Power Shell maakt het eenvoudig om de functies te ontdekken.</span><span class="sxs-lookup"><span data-stu-id="0209e-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="0209e-118">Als u bijvoorbeeld een lijst met cmdlets wilt vinden waarmee Windows-Services worden weer gegeven en gewijzigd, typt u:</span><span class="sxs-lookup"><span data-stu-id="0209e-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="0209e-119">Nadat u hebt gedetecteerd welke cmdlet een taak uitvoert, kunt u meer informatie over de cmdlet vinden met behulp `Get-Help` van de-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0209e-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="0209e-120">Als u bijvoorbeeld Help over de `Get-Service` cmdlet wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="0209e-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="0209e-121">De meeste cmdlets retour neren objecten die kunnen worden gemanipuleerd en vervolgens weer gegeven als tekst voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="0209e-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="0209e-122">Als u de uitvoer van een cmdlet volledig wilt begrijpen, pipet u `Get-Member` de uitvoer naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0209e-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="0209e-123">Met de volgende opdracht wordt bijvoorbeeld informatie weer gegeven over de leden van het object dat door `Get-Service` de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0209e-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="0209e-124">Consistentie</span><span class="sxs-lookup"><span data-stu-id="0209e-124">Consistency</span></span>

<span data-ttu-id="0209e-125">Het beheren van systemen kan een complexe taak zijn.</span><span class="sxs-lookup"><span data-stu-id="0209e-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="0209e-126">Hulpprogram ma's die een consistente interface hebben, helpen de inherente complexiteit te beheren.</span><span class="sxs-lookup"><span data-stu-id="0209e-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="0209e-127">Helaas zijn opdracht regel Programma's en COM-objecten (scriptable Component Object Model) niet bekend voor hun consistentie.</span><span class="sxs-lookup"><span data-stu-id="0209e-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="0209e-128">De consistentie van Power shell is een van de primaire activa.</span><span class="sxs-lookup"><span data-stu-id="0209e-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="0209e-129">Als u bijvoorbeeld leert hoe u de `Sort-Object` cmdlet gebruikt, kunt u die kennis gebruiken om de uitvoer van een cmdlet te sorteren.</span><span class="sxs-lookup"><span data-stu-id="0209e-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="0209e-130">U hoeft niet meer te weten te komen over de verschillende sorteer routines van elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0209e-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="0209e-131">Daarnaast hoeven cmdlet-ontwikkel aars geen sorteer functies te ontwerpen voor hun cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0209e-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="0209e-132">Power shell biedt een Framework met de basis functies die consistentie afdwingt.</span><span class="sxs-lookup"><span data-stu-id="0209e-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="0209e-133">Het Framework elimineert enkele keuzes die resteren voor de ontwikkelaar.</span><span class="sxs-lookup"><span data-stu-id="0209e-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="0209e-134">Maar als resultaat wordt de ontwikkeling van cmdlets veel eenvoudiger.</span><span class="sxs-lookup"><span data-stu-id="0209e-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="0209e-135">Interactieve en script omgevingen</span><span class="sxs-lookup"><span data-stu-id="0209e-135">Interactive and scripting environments</span></span>

<span data-ttu-id="0209e-136">De opdracht prompt van Windows biedt een interactieve shell met toegang tot opdracht regel Programma's en basis scripts.</span><span class="sxs-lookup"><span data-stu-id="0209e-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="0209e-137">Windows Script Host (WSH) heeft script bare opdracht regel Programma's en COM Automation-objecten, maar biedt geen interactieve shell.</span><span class="sxs-lookup"><span data-stu-id="0209e-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="0209e-138">Power shell combineert een interactieve shell en een script omgeving.</span><span class="sxs-lookup"><span data-stu-id="0209e-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="0209e-139">Power shell kan toegang krijgen tot opdracht regel Programma's, COM-objecten en .NET-klassen bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="0209e-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="0209e-140">Deze combi natie van functies breidt de mogelijkheden van de interactieve gebruiker, de script schrijver en de systeem beheerder uit.</span><span class="sxs-lookup"><span data-stu-id="0209e-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="0209e-141">Object stand</span><span class="sxs-lookup"><span data-stu-id="0209e-141">Object orientation</span></span>

<span data-ttu-id="0209e-142">Power shell is gebaseerd op object niet tekst.</span><span class="sxs-lookup"><span data-stu-id="0209e-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="0209e-143">De uitvoer van een opdracht is een object.</span><span class="sxs-lookup"><span data-stu-id="0209e-143">The output of a command is an object.</span></span> <span data-ttu-id="0209e-144">U kunt het uitvoer object, via de pijp lijn, naar een andere opdracht verzenden als invoer.</span><span class="sxs-lookup"><span data-stu-id="0209e-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="0209e-145">Deze pijp lijn biedt een bekende interface voor personen die ervaring hebben met andere shells.</span><span class="sxs-lookup"><span data-stu-id="0209e-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="0209e-146">Power shell breidt dit concept uit door objecten te verzenden in plaats van tekst.</span><span class="sxs-lookup"><span data-stu-id="0209e-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="0209e-147">Eenvoudige overgang naar scripts</span><span class="sxs-lookup"><span data-stu-id="0209e-147">Easy transition to scripting</span></span>

<span data-ttu-id="0209e-148">Met de opdracht detectie van Power shell kunt u eenvoudig een migratie uitvoeren van opdrachten die interactief worden getypt om scripts te maken en uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0209e-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="0209e-149">Met Power shell-transcripten en-geschiedenis kunt u eenvoudig opdrachten kopiëren naar een bestand voor gebruik als een script.</span><span class="sxs-lookup"><span data-stu-id="0209e-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
