---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Variabelen gebruiken om objecten op te slaan
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030369"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="fff0e-103">Variabelen gebruiken om objecten op te slaan</span><span class="sxs-lookup"><span data-stu-id="fff0e-103">Using variables to store objects</span></span>

<span data-ttu-id="fff0e-104">Power shell werkt met objecten.</span><span class="sxs-lookup"><span data-stu-id="fff0e-104">PowerShell works with objects.</span></span> <span data-ttu-id="fff0e-105">Met Power shell kunt u benoemde objecten maken die variabelen worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="fff0e-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="fff0e-106">Namen van variabelen kunnen het onderstrepings teken en alfanumerieke tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="fff0e-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="fff0e-107">Bij gebruik in Power shell wordt altijd een variabele opgegeven met behulp van het \$ teken gevolgd door de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="fff0e-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="fff0e-108">Een variabele maken</span><span class="sxs-lookup"><span data-stu-id="fff0e-108">Creating a variable</span></span>

<span data-ttu-id="fff0e-109">U kunt een variabele maken door de naam van een geldige variabele te typen:</span><span class="sxs-lookup"><span data-stu-id="fff0e-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="fff0e-110">In dit voor beeld wordt geen resultaat weer gegeven omdat `$loc` geen waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="fff0e-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="fff0e-111">U kunt een variabele maken en deze in dezelfde stap aan een waarde toewijzen.</span><span class="sxs-lookup"><span data-stu-id="fff0e-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="fff0e-112">Power Shell maakt de variabele alleen als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="fff0e-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="fff0e-113">Anders wordt de opgegeven waarde toegewezen aan de bestaande variabele.</span><span class="sxs-lookup"><span data-stu-id="fff0e-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="fff0e-114">In het volgende voor beeld wordt de huidige locatie opgeslagen in de variabele `$loc`:</span><span class="sxs-lookup"><span data-stu-id="fff0e-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="fff0e-115">Power shell geeft geen uitvoer weer wanneer u deze opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="fff0e-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="fff0e-116">Power shell verzendt de uitvoer van ' Get-location ' naar `$loc`.</span><span class="sxs-lookup"><span data-stu-id="fff0e-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="fff0e-117">In Power shell worden gegevens die niet zijn toegewezen of omgeleid naar het scherm verzonden.</span><span class="sxs-lookup"><span data-stu-id="fff0e-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="fff0e-118">Wanneer u `$loc` typt, wordt uw huidige locatie weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="fff0e-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="fff0e-119">U kunt `Get-Member` gebruiken om informatie weer te geven over de inhoud van variabelen.</span><span class="sxs-lookup"><span data-stu-id="fff0e-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="fff0e-120">`Get-Member` ziet u dat `$loc` een **PathInfo** -object is, net als bij de uitvoer van `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="fff0e-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="fff0e-121">Variabelen bewerken</span><span class="sxs-lookup"><span data-stu-id="fff0e-121">Manipulating variables</span></span>

<span data-ttu-id="fff0e-122">Power shell biedt verschillende opdrachten voor het bewerken van variabelen.</span><span class="sxs-lookup"><span data-stu-id="fff0e-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="fff0e-123">U kunt een volledige lijst weer geven in een lees bare vorm door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="fff0e-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="fff0e-124">Power Shell maakt ook diverse door het systeem gedefinieerde variabelen.</span><span class="sxs-lookup"><span data-stu-id="fff0e-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="fff0e-125">U kunt de cmdlet `Remove-Variable` gebruiken om variabelen te verwijderen die niet worden beheerd door Power shell, vanuit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="fff0e-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="fff0e-126">Typ de volgende opdracht om alle variabelen te wissen:</span><span class="sxs-lookup"><span data-stu-id="fff0e-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="fff0e-127">Nadat u de vorige opdracht hebt uitgevoerd, worden in de cmdlet `Get-Variable` de systeem variabelen van Power shell weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fff0e-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="fff0e-128">Power Shell maakt ook een variabele station.</span><span class="sxs-lookup"><span data-stu-id="fff0e-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="fff0e-129">Gebruik het volgende voor beeld om alle Power shell-variabelen weer te geven met behulp van het variabele station:</span><span class="sxs-lookup"><span data-stu-id="fff0e-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="fff0e-130">Cmd. exe-variabelen gebruiken</span><span class="sxs-lookup"><span data-stu-id="fff0e-130">Using cmd.exe variables</span></span>

<span data-ttu-id="fff0e-131">Power shell kan gebruikmaken van dezelfde omgevings variabelen die beschikbaar zijn voor elk Windows-proces, inclusief **cmd. exe**.</span><span class="sxs-lookup"><span data-stu-id="fff0e-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="fff0e-132">Deze variabelen worden weer gegeven via een station met de naam `env:`.</span><span class="sxs-lookup"><span data-stu-id="fff0e-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="fff0e-133">U kunt deze variabelen weer geven door de volgende opdracht te typen:</span><span class="sxs-lookup"><span data-stu-id="fff0e-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="fff0e-134">De standaard `*-Variable`-cmdlets zijn niet ontworpen om te werken met omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="fff0e-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="fff0e-135">U krijgt toegang tot omgevings variabelen met behulp van het voor voegsel `env:` station.</span><span class="sxs-lookup"><span data-stu-id="fff0e-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="fff0e-136">De variabele **% System root%** in **cmd. exe** bevat bijvoorbeeld de naam van de hoofdmap van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="fff0e-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="fff0e-137">In Power shell gebruikt u `$env:SystemRoot` om toegang te krijgen tot dezelfde waarde.</span><span class="sxs-lookup"><span data-stu-id="fff0e-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="fff0e-138">U kunt ook omgevings variabelen maken en wijzigen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="fff0e-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="fff0e-139">Omgevings variabelen in Power shell volgen dezelfde regels voor omgevings variabelen die elders in het besturings systeem worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fff0e-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="fff0e-140">In het volgende voor beeld wordt een nieuwe omgevings variabele gemaakt:</span><span class="sxs-lookup"><span data-stu-id="fff0e-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="fff0e-141">Hoewel dit niet vereist is, is het gebruikelijk om alle hoofd letters te gebruiken voor de namen van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="fff0e-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
