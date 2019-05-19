---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Variabelen gebruiken om objecten op te slaan
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 16e82b83df967674da11193c8ac60d637687a01b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854322"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="24487-103">Variabelen gebruiken om objecten op te slaan</span><span class="sxs-lookup"><span data-stu-id="24487-103">Using variables to store objects</span></span>

<span data-ttu-id="24487-104">PowerShell in combinatie met objecten.</span><span class="sxs-lookup"><span data-stu-id="24487-104">PowerShell works with objects.</span></span> <span data-ttu-id="24487-105">PowerShell kunt u benoemde objecten bekend als variabelen maken.</span><span class="sxs-lookup"><span data-stu-id="24487-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="24487-106">Namen van variabelen kunnen het onderstrepingsteken en een alfanumerieke tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="24487-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="24487-107">Wanneer gebruikt in PowerShell, een variabele altijd is opgegeven met behulp van de \$ gevolgd door de naam van variabele.</span><span class="sxs-lookup"><span data-stu-id="24487-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="24487-108">Het maken van een variabele</span><span class="sxs-lookup"><span data-stu-id="24487-108">Creating a variable</span></span>

<span data-ttu-id="24487-109">U kunt een variabele maken met een geldige variabele naam te typen:</span><span class="sxs-lookup"><span data-stu-id="24487-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="24487-110">In dit voorbeeld retourneert geen resultaat omdat `$loc` heeft geen waarde.</span><span class="sxs-lookup"><span data-stu-id="24487-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="24487-111">U kunt een variabele maken en hieraan een waarde in één stap.</span><span class="sxs-lookup"><span data-stu-id="24487-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="24487-112">De variabele PowerShell alleen gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="24487-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="24487-113">Anders wordt de opgegeven waarde toegewezen aan de bestaande variabele.</span><span class="sxs-lookup"><span data-stu-id="24487-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="24487-114">Het volgende voorbeeld wordt de huidige locatie opgeslagen in de variabele `$loc`:</span><span class="sxs-lookup"><span data-stu-id="24487-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="24487-115">Er is geen uitvoer wordt weergegeven wanneer u deze opdracht in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24487-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="24487-116">PowerShell stuurt de uitvoer van Get-locatie naar `$loc`.</span><span class="sxs-lookup"><span data-stu-id="24487-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="24487-117">Gegevens die niet is toegewezen of omgeleid is in PowerShell verzonden naar het scherm.</span><span class="sxs-lookup"><span data-stu-id="24487-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="24487-118">Typen `$loc` ziet u uw huidige locatie:</span><span class="sxs-lookup"><span data-stu-id="24487-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="24487-119">U kunt `Get-Member` om informatie over de inhoud van variabelen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="24487-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="24487-120">`Get-Member` ziet u dat `$loc` is een **PathInfo** object, net als de uitvoer van `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="24487-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

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

## <a name="manipulating-variables"></a><span data-ttu-id="24487-121">Variabelen bewerken</span><span class="sxs-lookup"><span data-stu-id="24487-121">Manipulating variables</span></span>

<span data-ttu-id="24487-122">PowerShell biedt diverse opdrachten voor het bewerken van variabelen.</span><span class="sxs-lookup"><span data-stu-id="24487-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="24487-123">U kunt een volledige lijst in een leesbare vorm zien door te typen:</span><span class="sxs-lookup"><span data-stu-id="24487-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="24487-124">PowerShell maakt ook verschillende systeem gedefinieerde variabelen.</span><span class="sxs-lookup"><span data-stu-id="24487-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="24487-125">U kunt de `Remove-Variable` cmdlet voor het verwijderen van variabelen, die niet worden beheerd met PowerShell, uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="24487-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="24487-126">Typ de volgende opdracht om te wissen van alle variabelen:</span><span class="sxs-lookup"><span data-stu-id="24487-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="24487-127">Na het uitvoeren van de vorige opdracht, de `Get-Variable` cmdlet ziet u de PowerShell-systeemvariabelen.</span><span class="sxs-lookup"><span data-stu-id="24487-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="24487-128">PowerShell maakt ook een variabele station.</span><span class="sxs-lookup"><span data-stu-id="24487-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="24487-129">Gebruik het volgende voorbeeld om alle PowerShell-variabelen met behulp van de variabele station weer te geven:</span><span class="sxs-lookup"><span data-stu-id="24487-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="24487-130">Cmd.exe variabelen gebruiken</span><span class="sxs-lookup"><span data-stu-id="24487-130">Using cmd.exe variables</span></span>

<span data-ttu-id="24487-131">PowerShell kunt gebruiken de dezelfde omgevingsvariabelen die beschikbaar zijn voor alle Windows-proces, inclusief **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="24487-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="24487-132">Deze variabelen worden weergegeven via een station met de naam `env:`.</span><span class="sxs-lookup"><span data-stu-id="24487-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="24487-133">U kunt deze variabelen weergeven door de volgende opdracht te typen:</span><span class="sxs-lookup"><span data-stu-id="24487-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="24487-134">De standaard `*-Variable` cmdlets zijn niet ontworpen voor gebruik met omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="24487-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="24487-135">Omgevingsvariabelen worden geopend met behulp van de `env:` stationsvoorvoegsel.</span><span class="sxs-lookup"><span data-stu-id="24487-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="24487-136">Bijvoorbeeld, de **% SystemRoot %** variabele in **cmd.exe** bevat de naam van de map hoofdmap van het besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="24487-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="24487-137">In PowerShell, gebruikt u `$env:SystemRoot` voor toegang tot dezelfde waarde.</span><span class="sxs-lookup"><span data-stu-id="24487-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="24487-138">U kunt ook maken en wijzigen van omgevingsvariabelen uit in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24487-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="24487-139">Omgevingsvariabelen in PowerShell volgt dezelfde regels gelden voor omgevingsvariabelen die elders in het besturingssysteem worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="24487-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="24487-140">Het volgende voorbeeld wordt een nieuwe omgevingsvariabele:</span><span class="sxs-lookup"><span data-stu-id="24487-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="24487-141">Hoewel dit niet vereist, is het gebruikelijk voor namen van omgevingsvariabelen gebruiken alle hoofdletters.</span><span class="sxs-lookup"><span data-stu-id="24487-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
