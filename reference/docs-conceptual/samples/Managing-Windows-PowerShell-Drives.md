---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell-stations beheren
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293245"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="d7b0c-103">Windows PowerShell-stations beheren</span><span class="sxs-lookup"><span data-stu-id="d7b0c-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="d7b0c-104">Een *Windows PowerShell-station* is een locatie voor het opslaan van gegevens waartoe u toegang hebt, zoals een station bestand system in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="d7b0c-105">De Windows PowerShell-providers maken bepaalde stations, zoals het bestandssysteem stations (inclusief C: en D:), het register stations (HKCU: en HKLM:), en het station van het certificaat (Cert:), en kunt u uw eigen Windows PowerShell-stations.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="d7b0c-106">Deze stations zijn zeer nuttig, maar ze zijn alleen beschikbaar in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="d7b0c-107">U geen toegang tot deze met behulp van andere Windows-hulpprogramma's, zoals Verkenner of Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="d7b0c-108">Windows PowerShell maakt gebruik van het zelfstandig naamwoord, **PSDrive**, voor de opdrachten die met Windows PowerShell werken-stations.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="d7b0c-109">Voor een lijst van de Windows PowerShell-stations in uw Windows PowerShell-sessie, gebruikt u de **Get-PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="d7b0c-110">Hoewel de stations in de weergave met de stations op uw systeem variëren, de aanbieding zal er ongeveer als volgt de uitvoer van de **Get-PSDrive** opdracht hierboven wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="d7b0c-111">Bestand systeemstations vormen een subset van de Windows PowerShell-stations.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="d7b0c-112">U kunt de systeemstations bestand door het bestandssysteem item in de kolom Provider kunt identificeren.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="d7b0c-113">(De stations bestand system in Windows PowerShell worden ondersteund door het bestandssysteem van Windows PowerShell-provider.)</span><span class="sxs-lookup"><span data-stu-id="d7b0c-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="d7b0c-114">Om te zien van de syntaxis van de **Get-PSDrive** cmdlet, typ een **Get-Command** opdracht met de **syntaxis** parameter:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="d7b0c-115">De **PSProvider** parameter kunt u alleen de Windows PowerShell-stations die worden weergegeven door een bepaalde provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="d7b0c-116">Bijvoorbeeld, als de Windows PowerShell-stations die worden ondersteund door het bestandssysteem van Windows PowerShell-provider, typt u een **Get-PSDrive** opdracht met de **PSProvider** parameter en de  **Bestandssysteem** waarde:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="d7b0c-117">Als u de Windows PowerShell-stations die registeronderdelen vertegenwoordigen, gebruikt u de **PSProvider** parameter om weer te geven alleen de Windows PowerShell-stations die worden ondersteund door het register van Windows PowerShell-provider:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="d7b0c-118">U kunt ook de standaard locatie-cmdlets gebruiken met de Windows PowerShell-stations:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="d7b0c-119">Toevoegen van nieuwe Windows PowerShell-stations (nieuwe PSDrive)</span><span class="sxs-lookup"><span data-stu-id="d7b0c-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="d7b0c-120">U kunt uw eigen Windows PowerShell-stations toevoegen met behulp van de **New-PSDrive** opdracht.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="d7b0c-121">Om op te halen van de syntaxis voor de **New-PSDrive** opdracht, voer de **Get-Command** opdracht met de **syntaxis** parameter:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="d7b0c-122">Een nieuwe Windows PowerShell-station wilt maken, moet u drie parameters opgeven:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="d7b0c-123">Een naam op voor het station (u kunt een geldige naam voor de Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d7b0c-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="d7b0c-124">De PSProvider (gebruik "Bestandssysteem" voor bestand systeemlocaties en '-register voor registerlocaties)</span><span class="sxs-lookup"><span data-stu-id="d7b0c-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="d7b0c-125">De hoofdmap, dat wil zeggen, het pad naar de hoofdmap van het nieuwe station</span><span class="sxs-lookup"><span data-stu-id="d7b0c-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="d7b0c-126">Bijvoorbeeld, kunt u een station met de naam 'Office' die is gekoppeld aan de map met de Microsoft Office-toepassingen op uw computer, zoals **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="d7b0c-127">Het station wilt maken, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="d7b0c-128">In het algemeen zijn paden niet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="d7b0c-129">U verwijst naar het nieuwe Windows PowerShell-station, zoals u dat wel alle Windows PowerShell-stations: door de naam gevolgd door een dubbele punt doet (**:**).</span><span class="sxs-lookup"><span data-stu-id="d7b0c-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="d7b0c-130">Een Windows PowerShell-station kunt vele taken die veel eenvoudiger maken.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="d7b0c-131">Sommige van de belangrijkste sleutels in het Windows-register hebben bijvoorbeeld extreem lange paden, zodat ze toegang krijgen tot omslachtig en moeilijk te onthouden.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="d7b0c-132">Essentiële configuratie-informatie zich bevindt onder **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="d7b0c-133">Als u wilt weergeven en wijzigen van items in de registersleutel CurrentVersion, kunt u een Windows PowerShell-station die verankerd ligt in deze sleutel maken door te typen:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="d7b0c-134">U kunt vervolgens Wijzig de locatie in de **cvkey:** station net als elk ander station:''</span><span class="sxs-lookup"><span data-stu-id="d7b0c-134">You can then change location to the **cvkey:** drive as you would any other drive:\`\`</span></span>

`PS> cd cvkey:`

<span data-ttu-id="d7b0c-135">of:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="d7b0c-136">De cmdlet New-PsDrive voegt het nieuwe station alleen voor de huidige Windows PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="d7b0c-137">Als u de Windows PowerShell-venster sluit, wordt het nieuwe station verloren gaan.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="d7b0c-138">Als u wilt opslaan op een Windows PowerShell-station, gebruikt u de cmdlet Export-Console voor het exporteren van de huidige Windows PowerShell-sessie en gebruik vervolgens de PowerShell.exe **PSConsoleFile** parameter om het te importeren.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="d7b0c-139">Of het nieuwe station toevoegen aan uw Windows PowerShell-profiel.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="d7b0c-140">Verwijderen van Windows PowerShell-stations (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="d7b0c-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="d7b0c-141">U kunt stations uit de Windows PowerShell verwijderen met behulp van de **Remove-PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="d7b0c-142">De **Remove-PSDrive** cmdlet is eenvoudig te gebruiken; als u wilt verwijderen van een specifieke Windows PowerShell-station, u gewoon de naam van de Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="d7b0c-143">Bijvoorbeeld, als u hebt toegevoegd de **Office:** Windows PowerShell-station, zoals wordt weergegeven in de **New-PSDrive** onderwerp, kunt u deze verwijderen door te typen:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="d7b0c-144">Verwijderen van de **cvkey:** Windows PowerShell station, ook weergegeven in de **New-PSDrive** onderwerp, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="d7b0c-145">Het is eenvoudig te verwijderen van een Windows PowerShell-station, maar u kunt deze niet verwijderen wanneer u zich in het station.</span><span class="sxs-lookup"><span data-stu-id="d7b0c-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="d7b0c-146">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d7b0c-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="d7b0c-147">Externe Windows PowerShell-stations toevoegen en verwijderen</span><span class="sxs-lookup"><span data-stu-id="d7b0c-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="d7b0c-148">Windows PowerShell detecteert bestand systeemstations die worden toegevoegd of verwijderd in Windows, inclusief stations die zijn toegewezen, USB-stations die zijn gekoppeld en stations die zijn verwijderd met behulp van de **netgebruik** opdracht of het  **WScript.NetworkMapNetworkDrive** en **RemoveNetworkDrive** methoden van een script Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="d7b0c-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>