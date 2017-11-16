---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Gebruik van variabelen op objecten van de Store
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="aa1c6-103">Gebruik van variabelen op objecten van de Store</span><span class="sxs-lookup"><span data-stu-id="aa1c6-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="aa1c6-104">PowerShell werkt met objecten.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-104">PowerShell works with objects.</span></span> <span data-ttu-id="aa1c6-105">PowerShell kunt u variabelen in wezen benoemde objecten, behouden de uitvoer voor later gebruik te maken.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="aa1c6-106">Als u worden gebruikt voor het werken met variabelen in andere houders Vergeet niet dat PowerShell variabelen objecten, niet naar tekst.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="aa1c6-107">Variabelen altijd worden opgegeven met het eerste teken $ en alle alfanumerieke tekens of het onderstrepingsteken kunnen opnemen in hun naam.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="aa1c6-108">Maken van een variabele</span><span class="sxs-lookup"><span data-stu-id="aa1c6-108">Creating a Variable</span></span>
<span data-ttu-id="aa1c6-109">U kunt een variabele maken door een geldige variabele naam te typen:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="aa1c6-110">Dit resultaat wordt geen omdat **$loc** geen waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="aa1c6-111">U kunt maken van een variabele en wijs hieraan een waarde in één stap.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="aa1c6-112">De variabele PowerShell alleen gemaakt als deze niet bestaat nog; anders wordt de opgegeven waarde toegewezen aan de bestaande variabele.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="aa1c6-113">Voor het opslaan van uw huidige locatie in de variabele **$loc**, type:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="aa1c6-114">Er wordt geen uitvoer weergegeven wanneer u deze opdracht invoert, omdat de uitvoer wordt verzonden naar $loc.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="aa1c6-115">In PowerShell wordt weergegeven uitvoer een neveneffect van het feit dat de gegevens die niet anders omgeleid, worden altijd naar het scherm verzonden.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="aa1c6-116">Typen $loc, ziet uw huidige locatie:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="aa1c6-117">U kunt **Get-lid** om informatie over de inhoud van variabelen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="aa1c6-118">$Loc aan Get-lid sluizen ziet u dat het is een **PathInfo** object, net als de uitvoer van Get-locatie:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="aa1c6-119">Variabelen bewerken</span><span class="sxs-lookup"><span data-stu-id="aa1c6-119">Manipulating Variables</span></span>
<span data-ttu-id="aa1c6-120">PowerShell levert een aantal opdrachten voor het bewerken van variabelen.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="aa1c6-121">Een volledige lijst in een leesbare vorm kunt u zien door te typen:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="aa1c6-122">Naast de variabelen die u in uw huidige PowerShell-sessie maken, zijn er verschillende systeem gedefinieerde variabelen.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="aa1c6-123">U kunt de **Remove-Variable** cmdlet op te ruimen alle variabelen die niet worden beheerd door PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="aa1c6-124">Typ de volgende opdracht om te wissen van alle variabelen:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="aa1c6-125">Het resultaat bevestiging wordt gevraagd die u hieronder ziet.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="aa1c6-126">Als u vervolgens de **Get-Variable** cmdlet, ziet u de resterende PowerShell-variabelen.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="aa1c6-127">Omdat er ook een variabele PowerShell-station, kunt u alle PowerShell-variabelen ook weergeven door te typen:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="aa1c6-128">Gebruik van variabelen Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="aa1c6-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="aa1c6-129">Hoewel PowerShell niet Cmd.exe, wordt uitgevoerd in een opdracht shell-omgeving en kunt u de dezelfde variabelen die beschikbaar zijn in elke omgeving van Windows gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="aa1c6-130">Deze variabelen worden weergegeven via een station met de naam **env**:.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="aa1c6-131">U kunt deze variabelen weergeven door te typen:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="aa1c6-132">Hoewel de standaard variabele cmdlets niet ontworpen zijn voor gebruik met **env:** variabelen, kunt u ze door te geven de **env:** voorvoegsel.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="aa1c6-133">Bijvoorbeeld, om te zien in de hoofdmap van het besturingssysteem, kunt u de opdrachtshell **% SystemRoot %** variabele van PowerShell door te typen:</span><span class="sxs-lookup"><span data-stu-id="aa1c6-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="aa1c6-134">U kunt ook maken en wijzigen van omgevingsvariabelen van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="aa1c6-135">Omgevingsvariabelen toegankelijk vanuit Windows PowerShell voldoen aan de normale regels voor omgevingsvariabelen elders in Windows.</span><span class="sxs-lookup"><span data-stu-id="aa1c6-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

