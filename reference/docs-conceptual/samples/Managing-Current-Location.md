---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Huidige locatie beheren
description: Power shell gebruikt de locatie van het zelfstandig naam woord om te verwijzen naar de werkmap en implementeert een groep cmdlets om uw locatie te onderzoeken en te manipuleren.
ms.openlocfilehash: 0ce9ed1269921233b0d6b07da832c12e159a84dc
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500467"
---
# <a name="managing-current-location"></a><span data-ttu-id="744c2-104">Huidige locatie beheren</span><span class="sxs-lookup"><span data-stu-id="744c2-104">Managing Current Location</span></span>

<span data-ttu-id="744c2-105">Bij het navigeren door map-systemen in Verkenner, hebt u meestal een specifieke werk locatie, namelijk de huidige geopende map.</span><span class="sxs-lookup"><span data-stu-id="744c2-105">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="744c2-106">Items in de huidige map kunnen eenvoudig worden gemanipuleerd door erop te klikken.</span><span class="sxs-lookup"><span data-stu-id="744c2-106">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="744c2-107">Voor opdracht regel interfaces, zoals Cmd.exe, kunt u, wanneer u zich in dezelfde map bevindt als een bepaald bestand, toegang krijgen door een relatief korte naam op te geven in plaats van het volledige pad naar het bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="744c2-107">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="744c2-108">De huidige map wordt de werkmap genoemd.</span><span class="sxs-lookup"><span data-stu-id="744c2-108">The current directory is called the working directory.</span></span>

<span data-ttu-id="744c2-109">Windows Power shell gebruikt de **locatie** van het zelfstandig naam woord om te verwijzen naar de werkmap en implementeert een groep cmdlets om uw locatie te onderzoeken en te manipuleren.</span><span class="sxs-lookup"><span data-stu-id="744c2-109">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="744c2-110">Uw huidige locatie ophalen (Get-locatie)</span><span class="sxs-lookup"><span data-stu-id="744c2-110">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="744c2-111">Als u het pad van de huidige maplocatie wilt bepalen, voert u de opdracht **Get-location** in:</span><span class="sxs-lookup"><span data-stu-id="744c2-111">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="744c2-112">De cmdlet Get-Location is vergelijkbaar met de opdracht **pwd** in de bash-shell.</span><span class="sxs-lookup"><span data-stu-id="744c2-112">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="744c2-113">De cmdlet Set-Location is vergelijkbaar met de **cd** -opdracht in Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="744c2-113">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="744c2-114">Uw huidige locatie instellen (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="744c2-114">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="744c2-115">De opdracht **Get-locatie** wordt gebruikt met de opdracht **Set-Location** .</span><span class="sxs-lookup"><span data-stu-id="744c2-115">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="744c2-116">Met de opdracht **Set-Location** kunt u de huidige maplocatie opgeven.</span><span class="sxs-lookup"><span data-stu-id="744c2-116">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="744c2-117">Nadat u de opdracht hebt ingevoerd, zult u merken dat u geen directe feedback krijgt over het effect van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="744c2-117">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="744c2-118">De meeste Windows Power shell-opdrachten die een actie uitvoeren, produceren weinig of geen uitvoer omdat de uitvoer niet altijd nuttig is.</span><span class="sxs-lookup"><span data-stu-id="744c2-118">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="744c2-119">Als u wilt controleren of er een gewijzigde Directory is gewijzigd wanneer u de opdracht **Set-Location** opgeeft, neemt u de para meter **-PassThru** op wanneer u de opdracht **Set-Location** opgeeft:</span><span class="sxs-lookup"><span data-stu-id="744c2-119">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="744c2-120">De para meter **-PassThru** kan worden gebruikt met veel set-opdrachten in Windows Power shell om informatie over het resultaat te retour neren in gevallen waarin er geen standaard uitvoer is.</span><span class="sxs-lookup"><span data-stu-id="744c2-120">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="744c2-121">U kunt paden ten opzichte van uw huidige locatie opgeven op dezelfde manier als in de meeste UNIX-en Windows-opdracht shells.</span><span class="sxs-lookup"><span data-stu-id="744c2-121">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="744c2-122">In de standaard notatie voor relatieve paden, een punt (**.**) vertegenwoordigt de huidige map en een dubbele punt (**..**) vertegenwoordigt de bovenliggende map van uw huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="744c2-122">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="744c2-123">Bijvoorbeeld, als u zich in de map **C: \\ Windows** bevindt, een punt (**.**) vertegenwoordigt **c: \\ Windows** en dubbele punten (**..**) vertegenwoordigen **c:**.</span><span class="sxs-lookup"><span data-stu-id="744c2-123">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="744c2-124">U kunt van uw huidige locatie naar de hoofdmap van station C: overschakelen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="744c2-124">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="744c2-125">Dezelfde techniek werkt op Windows Power Shell-stations die geen bestandssysteem stations zijn, zoals **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="744c2-125">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="744c2-126">U kunt uw locatie in het REGI ster instellen op de HKLM- \\ software sleutel door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="744c2-126">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="744c2-127">U kunt de maplocatie vervolgens wijzigen in de bovenliggende map. Dit is de hoofdmap van het station Windows Power shell HKLM:, met behulp van een relatief pad:</span><span class="sxs-lookup"><span data-stu-id="744c2-127">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="744c2-128">U kunt Set-Location typen of een van de ingebouwde Windows Power shell-aliassen voor Set-Location (cd, chdir, SL) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="744c2-128">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="744c2-129">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="744c2-129">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="744c2-130">Recente locaties opslaan en intrekken (push-locatie en pop-locatie)</span><span class="sxs-lookup"><span data-stu-id="744c2-130">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="744c2-131">Wanneer u locaties wijzigt, is het handig om bij te houden waar u bent geweest en te kunnen terugkeren naar uw vorige locatie.</span><span class="sxs-lookup"><span data-stu-id="744c2-131">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="744c2-132">Met de cmdlet **Push-location** in Windows Power Shell maakt u een geordende geschiedenis (een ' stack ') van directory paden waar u zich bevindt, en kunt u de geschiedenis van mappaden door lopen met behulp van de complementaire cmdlet van de **pop-locatie** .</span><span class="sxs-lookup"><span data-stu-id="744c2-132">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="744c2-133">Windows Power shell wordt bijvoorbeeld doorgaans gestart in de basismap van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="744c2-133">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="744c2-134">De woord *stack* heeft een speciale betekenis in veel programma-instellingen, waaronder .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="744c2-134">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="744c2-135">Net als bij een fysieke stack met items is het laatste item dat u op de stack plaatst het eerste item dat u de stack kunt afhalen.</span><span class="sxs-lookup"><span data-stu-id="744c2-135">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="744c2-136">Het toevoegen van een item aan een stack is colloquially ' het item ' pushen ' naar de stack.</span><span class="sxs-lookup"><span data-stu-id="744c2-136">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="744c2-137">Het ophalen van een item uit de stack is colloquially bekend als ' het opzeggen ' van het item van de stack.</span><span class="sxs-lookup"><span data-stu-id="744c2-137">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="744c2-138">Als u de huidige locatie naar de stack wilt pushen en vervolgens naar de map Local Settings wilt gaan, typt u:</span><span class="sxs-lookup"><span data-stu-id="744c2-138">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="744c2-139">U kunt vervolgens de locatie van de lokale instellingen naar de stack pushen en naar de map Temp gaan door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="744c2-139">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="744c2-140">U kunt controleren of u de mappen hebt gewijzigd door de opdracht **Get-locatie** in te voeren:</span><span class="sxs-lookup"><span data-stu-id="744c2-140">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="744c2-141">U kunt vervolgens weer terug naar de meest recent bezochte map door de opdracht **pop-locatie** in te voeren en de wijziging te controleren door de opdracht **Get-locatie** in te voeren:</span><span class="sxs-lookup"><span data-stu-id="744c2-141">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="744c2-142">Net als bij de cmdlet **Set-Location** kunt u de para meter **-PassThru** toevoegen wanneer u de **pop-locatie** -cmdlet invoert om de door u ingevoerde map weer te geven:</span><span class="sxs-lookup"><span data-stu-id="744c2-142">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="744c2-143">U kunt ook de locatie-cmdlets met netwerk paden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="744c2-143">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="744c2-144">Als u een server met de naam FS01 hebt met een share met de naam Public, kunt u uw locatie wijzigen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="744c2-144">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="744c2-145">of</span><span class="sxs-lookup"><span data-stu-id="744c2-145">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="744c2-146">U kunt de opdrachten **Push-locatie** en **Stel locatie** gebruiken om de locatie te wijzigen in alle beschik bare stations.</span><span class="sxs-lookup"><span data-stu-id="744c2-146">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="744c2-147">Als u bijvoorbeeld een lokaal CD-ROM-station hebt met stationsletter D dat een gegevens-CD bevat, kunt u de locatie wijzigen in het CD-station door de opdracht **Set-Location D:** in te voeren.</span><span class="sxs-lookup"><span data-stu-id="744c2-147">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="744c2-148">Als het station leeg is, wordt het volgende fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="744c2-148">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="744c2-149">Wanneer u een opdracht regel interface gebruikt, is het niet handig om bestanden Verkenner te gebruiken om de beschik bare fysieke stations te controleren.</span><span class="sxs-lookup"><span data-stu-id="744c2-149">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="744c2-150">Daarnaast worden de alle Windows Power Shell-stations niet weer gegeven in de Verkenner.</span><span class="sxs-lookup"><span data-stu-id="744c2-150">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="744c2-151">Windows Power shell biedt een reeks opdrachten voor het bewerken van Windows Power Shell-stations, en we zullen hierover over de volgende stappen gaan.</span><span class="sxs-lookup"><span data-stu-id="744c2-151">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
