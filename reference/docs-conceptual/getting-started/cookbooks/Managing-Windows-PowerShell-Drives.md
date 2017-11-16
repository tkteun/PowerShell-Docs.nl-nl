---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het beheren van Windows PowerShell-stations
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: e2908246bb584291f04b67dc8635caec93d3b72e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="256dd-103">Het beheren van Windows PowerShell-stations</span><span class="sxs-lookup"><span data-stu-id="256dd-103">Managing Windows PowerShell Drives</span></span>
<span data-ttu-id="256dd-104">Een *Windows PowerShell-station* is een locatie voor het opslaan van gegevens waartoe u toegang hebt, zoals een station file system in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="256dd-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="256dd-105">De Windows PowerShell-providers stations voor u te maken, zoals het bestandssysteem stations (inclusief C: en D:), het register stations (HKCU: en HKLM:), en het station van het certificaat (Cert:), en u uw eigen Windows PowerShell-schijven kunt maken.</span><span class="sxs-lookup"><span data-stu-id="256dd-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="256dd-106">Deze stations zeer nuttig zijn, maar ze zijn alleen beschikbaar in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="256dd-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="256dd-107">U kunt ze niet openen met behulp van andere Windows-hulpprogramma's, zoals Windows Verkenner of Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="256dd-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="256dd-108">Windows PowerShell maakt gebruik van het zelfstandig naamwoord, **PSDrive**, voor opdrachten die met Windows PowerShell werken-stations.</span><span class="sxs-lookup"><span data-stu-id="256dd-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="256dd-109">Voor een lijst van de Windows PowerShell-stations in uw Windows PowerShell-sessie, kunt u via de **Get-PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="256dd-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="256dd-110">Hoewel de stations in de weergave naargelang de schijven op uw systeem verschillen, de vermelding ziet er ongeveer als de uitvoer van de **Get-PSDrive** opdracht hierboven weergegeven.</span><span class="sxs-lookup"><span data-stu-id="256dd-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="256dd-111">Bestand systeemstations zijn een subset van de Windows PowerShell-stations.</span><span class="sxs-lookup"><span data-stu-id="256dd-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="256dd-112">U kunt het bestand systeemstations door het bestandssysteem item in de kolom Provider identificeren.</span><span class="sxs-lookup"><span data-stu-id="256dd-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="256dd-113">(De stations file system in Windows PowerShell worden ondersteund door het bestandssysteem van Windows PowerShell-provider.)</span><span class="sxs-lookup"><span data-stu-id="256dd-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="256dd-114">Om te zien van de syntaxis van de **Get-PSDrive** cmdlet, typ een **Get-Command** opdracht met de **syntaxis** parameter:</span><span class="sxs-lookup"><span data-stu-id="256dd-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="256dd-115">De **PSProvider** parameter kunt u alleen de Windows PowerShell-stations die worden weergegeven door een bepaalde provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="256dd-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="256dd-116">Bijvoorbeeld, als u wilt weergeven in de Windows PowerShell-stations die worden ondersteund door het bestandssysteem van Windows PowerShell-provider, typ een **Get-PSDrive** opdracht met de **PSProvider** parameter en de  **Bestandssysteem** waarde:</span><span class="sxs-lookup"><span data-stu-id="256dd-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="256dd-117">Als u wilt weergeven in de Windows PowerShell-stations die registeronderdelen vertegenwoordigen, gebruiken de **PSProvider** parameter zodat alleen de Windows PowerShell-stations die worden weergegeven door het register van Windows PowerShell-provider worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="256dd-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

<pre>PS> Get-PSDrive -PSProvider Registry
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

<span data-ttu-id="256dd-118">U kunt ook de standaard locatie cmdlets met de Windows PowerShell-stations gebruiken:</span><span class="sxs-lookup"><span data-stu-id="256dd-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

<pre>PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location
Path
----
HKLM:\SOFTWARE\Microsoft</pre>

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="256dd-119">Toevoegen van nieuwe Windows PowerShell-schijven (nieuwe PSDrive)</span><span class="sxs-lookup"><span data-stu-id="256dd-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>
<span data-ttu-id="256dd-120">U kunt uw eigen Windows PowerShell-stations toevoegen met behulp van de **nieuw PSDrive** opdracht.</span><span class="sxs-lookup"><span data-stu-id="256dd-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="256dd-121">Ophalen van de syntaxis voor de **nieuw PSDrive** opdracht, voert u de **Get-Command** opdracht met de **syntaxis** parameter:</span><span class="sxs-lookup"><span data-stu-id="256dd-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="256dd-122">Een nieuwe Windows PowerShell-station wilt maken, moet u drie parameters opgeven:</span><span class="sxs-lookup"><span data-stu-id="256dd-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="256dd-123">Een naam voor station (u kunt geldige naam voor de Windows PowerShell gebruiken)</span><span class="sxs-lookup"><span data-stu-id="256dd-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="256dd-124">De PSProvider (gebruik 'Bestandssysteem' voor de locaties van systeem en 'Register' voor registerlocaties)</span><span class="sxs-lookup"><span data-stu-id="256dd-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="256dd-125">De hoofdmap, dat wil zeggen, het pad naar de hoofdmap van het nieuwe station</span><span class="sxs-lookup"><span data-stu-id="256dd-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="256dd-126">Bijvoorbeeld, kunt u een station met de naam 'Office' die is toegewezen aan de map met de Microsoft Office-toepassingen op uw computer, zoals **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="256dd-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="256dd-127">Het station wilt maken, typ de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="256dd-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="256dd-128">In het algemeen zijn paden niet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="256dd-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="256dd-129">U verwijzen naar de nieuwe Windows PowerShell-station als u alle stations van Windows PowerShell: door de naam gevolgd door een dubbele punt (**:**).</span><span class="sxs-lookup"><span data-stu-id="256dd-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="256dd-130">Een Windows PowerShell-station kunt vele taken die veel eenvoudiger maken.</span><span class="sxs-lookup"><span data-stu-id="256dd-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="256dd-131">Sommige van de belangrijkste sleutels in het Windows-register hebben bijvoorbeeld extreem lange paden, waardoor ze omslachtige voor toegang en moeilijk te onthouden.</span><span class="sxs-lookup"><span data-stu-id="256dd-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="256dd-132">Essentiële configuratie-informatie zich bevindt onder **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="256dd-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="256dd-133">Als u wilt weergeven en wijzigen van items in de registersleutel CurrentVersion, kunt u een Windows PowerShell-station dat is geroot in deze sleutel door te typen:</span><span class="sxs-lookup"><span data-stu-id="256dd-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

<span data-ttu-id="256dd-134">U kunt vervolgens de locatie waar u wilt wijzigen de **cvkey:** station net als elk ander station:''</span><span class="sxs-lookup"><span data-stu-id="256dd-134">You can then change location to the **cvkey:** drive as you would any other drive:``</span></span>

`PS> cd cvkey:`

<span data-ttu-id="256dd-135">of:</span><span class="sxs-lookup"><span data-stu-id="256dd-135">or:</span></span>

<pre>PS> Set-Location cvkey: -PassThru
Path
----
cvkey:\</pre>

<span data-ttu-id="256dd-136">De cmdlet New-PsDrive voegt het nieuwe station alleen aan de huidige Windows PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="256dd-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="256dd-137">Als u de Windows PowerShell-venster sluit, wordt het nieuwe station verloren.</span><span class="sxs-lookup"><span data-stu-id="256dd-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="256dd-138">Als u wilt opslaan op een Windows PowerShell-station, gebruikt u de cmdlet Export-Console voor het exporteren van de huidige Windows PowerShell-sessie en gebruik vervolgens de PowerShell.exe **PSConsoleFile** parameter te importeren.</span><span class="sxs-lookup"><span data-stu-id="256dd-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="256dd-139">Of het nieuwe station toevoegen aan uw Windows PowerShell-profiel.</span><span class="sxs-lookup"><span data-stu-id="256dd-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="256dd-140">Verwijderen van Windows PowerShell-schijven (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="256dd-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>
<span data-ttu-id="256dd-141">U kunt schijven uit de Windows PowerShell verwijderen met behulp van de **verwijderen PSDrive** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="256dd-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="256dd-142">De **verwijderen PSDrive** cmdlet is eenvoudig te gebruiken; voor het verwijderen van een specifieke Windows PowerShell-station u gewoon de naam van de Windows PowerShell-station.</span><span class="sxs-lookup"><span data-stu-id="256dd-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="256dd-143">Bijvoorbeeld, als u hebt toegevoegd de **Office:** Windows PowerShell-station, zoals wordt weergegeven in de **nieuw PSDrive** onderwerp, kunt u deze verwijderen door te typen:</span><span class="sxs-lookup"><span data-stu-id="256dd-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```
PS> Remove-PSDrive -Name Office
```

<span data-ttu-id="256dd-144">Verwijderen van de **cvkey:** Windows PowerShell-station, ook weergegeven in de **nieuw PSDrive** onderwerp, gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="256dd-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```
PS> Remove-PSDrive -Name cvkey
```

<span data-ttu-id="256dd-145">Het is gemakkelijk om te verwijderen van een Windows PowerShell-station, maar u kunt deze niet verwijderen terwijl u in het station bent.</span><span class="sxs-lookup"><span data-stu-id="256dd-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="256dd-146">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="256dd-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="256dd-147">Toevoegen en verwijderen van schijven buiten Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="256dd-147">Adding and Removing Drives Outside Windows PowerShell</span></span>
<span data-ttu-id="256dd-148">Windows PowerShell detecteert bestand systeemstations die worden toegevoegd of verwijderd in Windows, inclusief stations die zijn toegewezen, USB-stations die zijn gekoppeld en stations die zijn verwijderd met behulp van de **gebruik net** opdracht of het  **WScript.NetworkMapNetworkDrive** en **RemoveNetworkDrive** methoden van een script dat Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="256dd-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>

