---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Huidige locatie beheren
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086252"
---
# <a name="managing-current-location"></a><span data-ttu-id="8252d-103">Huidige locatie beheren</span><span class="sxs-lookup"><span data-stu-id="8252d-103">Managing Current Location</span></span>

<span data-ttu-id="8252d-104">Bij het navigeren door systemen van de map in Verkenner, hebt u meestal een specifieke locatie in de werkmap - dat wil zeggen de huidige map openen.</span><span class="sxs-lookup"><span data-stu-id="8252d-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="8252d-105">Items in de huidige map kunnen eenvoudig worden bewerkt door erop te klikken.</span><span class="sxs-lookup"><span data-stu-id="8252d-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="8252d-106">Opdrachtregelinterfaces zoals Cmd.exe, wanneer u zich in dezelfde map als een bepaald bestand, u kunt toegang tot deze door een relatief korte naam op te geven in plaats van telkens opgeven van het volledige pad naar het bestand.</span><span class="sxs-lookup"><span data-stu-id="8252d-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="8252d-107">De huidige map heet de werkmap.</span><span class="sxs-lookup"><span data-stu-id="8252d-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="8252d-108">Windows PowerShell maakt gebruik van het zelfstandig naamwoord **locatie** om te verwijzen naar de werkmap en een reeks cmdlets kunt bekijken en bewerken van uw locatie implementeert.</span><span class="sxs-lookup"><span data-stu-id="8252d-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="8252d-109">Ophalen van uw huidige locatie (Get-locatie)</span><span class="sxs-lookup"><span data-stu-id="8252d-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="8252d-110">Om te bepalen het pad van uw huidige locatie van de directory, voer de **Get-locatie** opdracht:</span><span class="sxs-lookup"><span data-stu-id="8252d-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="8252d-111">De cmdlet Get-locatie is vergelijkbaar met de **pwd** opdracht in de BASH-shell.</span><span class="sxs-lookup"><span data-stu-id="8252d-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="8252d-112">De cmdlet Set-locatie is vergelijkbaar met de **cd** opdracht in Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="8252d-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="8252d-113">Instellen van uw huidige locatie (locatie instellen)</span><span class="sxs-lookup"><span data-stu-id="8252d-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="8252d-114">De **Get-locatie** opdracht wordt gebruikt met de **locatie instellen** opdracht.</span><span class="sxs-lookup"><span data-stu-id="8252d-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="8252d-115">De **locatie instellen** opdracht kunt u uw huidige maplocatie opgeven.</span><span class="sxs-lookup"><span data-stu-id="8252d-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="8252d-116">Nadat u de opdracht hebt ingevoerd, zult u merken dat u direct feedback over het effect van de opdracht geen ontvangt.</span><span class="sxs-lookup"><span data-stu-id="8252d-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="8252d-117">De meeste Windows PowerShell-opdrachten die een actie uitvoert er weinig of geen uitvoer geproduceerd, omdat de uitvoer niet altijd handig is.</span><span class="sxs-lookup"><span data-stu-id="8252d-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="8252d-118">Om te controleren dat de wijziging van een geslaagde directory is opgetreden bij het invoeren van de **locatie instellen** opdracht, bevatten de **- PassThru gebruikt** parameter bij het invoeren van de **locatie instellen**opdracht:</span><span class="sxs-lookup"><span data-stu-id="8252d-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="8252d-119">De **- PassThru gebruikt** parameter kan worden gebruikt met veel Set-opdrachten in Windows PowerShell om te retourneren informatie over het resultaat in gevallen waarin er geen standaarduitvoer wordt.</span><span class="sxs-lookup"><span data-stu-id="8252d-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="8252d-120">U kunt paden ten opzichte van uw huidige locatie opgeven op dezelfde manier zoals u in de meeste UNIX- en Windows shells opdracht zou.</span><span class="sxs-lookup"><span data-stu-id="8252d-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="8252d-121">In de standard-notatie voor relatieve paden, een periode (**.**) Hiermee geeft u de huidige map en een dubbele punt (**...** ) staat voor de bovenliggende map van uw huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="8252d-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="8252d-122">Bijvoorbeeld, als u zich in de **C:\\Windows** map, een punt (**.**) Hiermee geeft u **C:\\Windows** en dubbele punten (**...** ) vertegenwoordigen **C:**.</span><span class="sxs-lookup"><span data-stu-id="8252d-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="8252d-123">U kunt van uw huidige locatie naar de hoofdmap van station wijzigen door te typen:</span><span class="sxs-lookup"><span data-stu-id="8252d-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="8252d-124">Dezelfde techniek werkt op Windows PowerShell-stations die niet bestand systeemstations, zoals zijn **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="8252d-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="8252d-125">U kunt uw locatie instellen op de HKLM\\softwaresleutel in het register door te typen:</span><span class="sxs-lookup"><span data-stu-id="8252d-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="8252d-126">Vervolgens kunt u de locatie van de map wijzigen naar de bovenliggende map, dit de hoofdmap van de Windows PowerShell-HKLM is: station, met behulp van een relatief pad:</span><span class="sxs-lookup"><span data-stu-id="8252d-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="8252d-127">U kunt Set-locatie typen of gebruik een van de ingebouwde Windows PowerShell-aliassen voor Set-locatie (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="8252d-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="8252d-128">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="8252d-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="8252d-129">Opslaan en terughalen van recente locaties (Push-locatie en Pop-locatie)</span><span class="sxs-lookup"><span data-stu-id="8252d-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="8252d-130">Wanneer u locaties wijzigt, is het handig bijhouden waar u zijn en kunnen worden gebruikt om terug te keren naar de vorige locatie.</span><span class="sxs-lookup"><span data-stu-id="8252d-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="8252d-131">De **Push-locatie** cmdlet in Windows PowerShell maakt u een geordende geschiedenis (een ' stack') van mappaden waar u zijn, en u kunt stap voor stap terug via de geschiedenis van directory-paden met behulp van de aanvullende  **Pop-locatie** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8252d-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="8252d-132">Bijvoorbeeld, Windows PowerShell wordt doorgaans begint in de basismap van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8252d-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="8252d-133">Het woord *stack* heeft een speciale betekenis in veel programmeertalen instellingen, met inbegrip van .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8252d-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="8252d-134">Als een fysieke stack van items is het laatste item dat u in de stack het eerste item dat u uit de stack ophalen kunt.</span><span class="sxs-lookup"><span data-stu-id="8252d-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="8252d-135">Een item toe te voegen aan een stapel wordt term aangeduid als 'pushen' van het item in de stack.</span><span class="sxs-lookup"><span data-stu-id="8252d-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="8252d-136">Binnenhalen van een item uit de stack wordt term aangeduid als 'Apparaatpagina' van het item uit de stack.</span><span class="sxs-lookup"><span data-stu-id="8252d-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="8252d-137">Als u de huidige locatie in de stack pushen en vervolgens verplaatsen naar de map lokale instellingen, typt u:</span><span class="sxs-lookup"><span data-stu-id="8252d-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="8252d-138">U kunt vervolgens de locatie van de lokale instellingen in de stack pushen en verplaatsen naar de map Temp door te typen:</span><span class="sxs-lookup"><span data-stu-id="8252d-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="8252d-139">U kunt controleren of u mappen gewijzigd door in te voeren de **Get-locatie** opdracht:</span><span class="sxs-lookup"><span data-stu-id="8252d-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="8252d-140">U kunt vervolgens terug naar de meest recent bezochte map pop door in te voeren de **Pop-locatie** opdracht in en controleer of de wijziging door te voeren de **Get-locatie** opdracht:</span><span class="sxs-lookup"><span data-stu-id="8252d-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="8252d-141">Net als met de **locatie instellen** cmdlet, u kunt opnemen de **- PassThru gebruikt** parameter bij het invoeren van de **Pop-locatie** cmdlet om weer te geven van de map die u hebt ingevoerd:</span><span class="sxs-lookup"><span data-stu-id="8252d-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="8252d-142">U kunt ook de locatie-cmdlets gebruiken met netwerkpaden.</span><span class="sxs-lookup"><span data-stu-id="8252d-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="8252d-143">Als u een server met de naam FS01 met een bestandsshare met de openbare naam hebt, kunt u uw locatie wijzigen door te typen</span><span class="sxs-lookup"><span data-stu-id="8252d-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="8252d-144">of</span><span class="sxs-lookup"><span data-stu-id="8252d-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="8252d-145">U kunt de **Push-locatie** en **locatie instellen** opdrachten om te wijzigen van de locatie op elk beschikbaar station.</span><span class="sxs-lookup"><span data-stu-id="8252d-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="8252d-146">Bijvoorbeeld, als u een lokale cd-rom-station met de stationsletter D met een gegevens-CD hebt, kunt u de locatie naar het cd-rom-station door in te voeren de **locatie instellen D:** opdracht.</span><span class="sxs-lookup"><span data-stu-id="8252d-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="8252d-147">Als de schijf leeg is, krijgt u de volgende strekking weergegeven:</span><span class="sxs-lookup"><span data-stu-id="8252d-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="8252d-148">Wanneer u een opdrachtregelinterface gebruikt, is het niet handig is dat de Bestandenverkenner gebruikt om de beschikbare fysieke stations te controleren.</span><span class="sxs-lookup"><span data-stu-id="8252d-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="8252d-149">Ook toont Verkenner niet u de alle van de Windows PowerShell-stations.</span><span class="sxs-lookup"><span data-stu-id="8252d-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="8252d-150">Windows PowerShell biedt een reeks opdrachten voor het manipuleren van Windows PowerShell-stations en we zullen praten over deze volgende.</span><span class="sxs-lookup"><span data-stu-id="8252d-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
