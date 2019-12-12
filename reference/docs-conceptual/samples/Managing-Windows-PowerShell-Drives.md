---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Windows PowerShell-stations beheren
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215506"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="4c06f-103">Windows PowerShell-stations beheren</span><span class="sxs-lookup"><span data-stu-id="4c06f-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="4c06f-104">Een *Windows Power Shell-station* is een gegevens opslag locatie die u kunt openen als een bestandssysteem station in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4c06f-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="4c06f-105">De Windows Power shell-providers maken enkele stations voor u, zoals de bestandssysteem stations (inclusief C: en D:), de register stations (HKCU: en HKLM:) en het certificaat station (CERT:), en u kunt uw eigen Windows Power Shell-stations maken.</span><span class="sxs-lookup"><span data-stu-id="4c06f-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="4c06f-106">Deze stations zijn erg nuttig, maar ze zijn alleen beschikbaar in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4c06f-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="4c06f-107">U kunt ze niet openen met andere Windows-hulpprogram ma's, zoals bestanden Verkenner of Cmd. exe.</span><span class="sxs-lookup"><span data-stu-id="4c06f-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="4c06f-108">Windows Power Shell maakt gebruik van het zelfstandige naam woord, **PSDrive**, voor opdrachten die werken met Windows Power Shell-stations.</span><span class="sxs-lookup"><span data-stu-id="4c06f-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="4c06f-109">Voor een lijst met Windows Power Shell-stations in uw Windows Power shell-sessie gebruikt u de cmdlet **Get-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="4c06f-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

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

<span data-ttu-id="4c06f-110">Hoewel de stations in de weer gave afhankelijk zijn van de stations op het systeem, ziet de vermelding er ongeveer uit als de uitvoer van de opdracht **Get-PSDrive** die hierboven wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c06f-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="4c06f-111">Bestandssysteem stations zijn een subset van de Windows Power Shell-stations.</span><span class="sxs-lookup"><span data-stu-id="4c06f-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="4c06f-112">U kunt de bestandssysteem stations identificeren met de vermelding bestands systeem in de kolom provider.</span><span class="sxs-lookup"><span data-stu-id="4c06f-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="4c06f-113">(De bestandssysteem stations in Windows Power shell worden ondersteund door de Windows Power shell-systeem provider.)</span><span class="sxs-lookup"><span data-stu-id="4c06f-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="4c06f-114">Als u de syntaxis van de cmdlet **Get-PSDrive** wilt weer geven, typt u een **Get-opdracht** opdracht met de **syntaxis** parameter:</span><span class="sxs-lookup"><span data-stu-id="4c06f-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="4c06f-115">Met de para meter **PSProvider** kunt u alleen de Windows Power Shell-stations weer geven die door een bepaalde provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4c06f-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="4c06f-116">Als u bijvoorbeeld alleen de Windows Power Shell-stations wilt weer geven die worden ondersteund door de Windows Power shell-bestandssysteem provider, typt u de opdracht **Get-PSDrive** met de para meter **PSProvider** en de waarde van het **Bestands systeem** :</span><span class="sxs-lookup"><span data-stu-id="4c06f-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="4c06f-117">Als u de Windows Power Shell-stations wilt weer geven die register onderdelen vertegenwoordigen, gebruikt u de para meter **PSProvider** om alleen de Windows Power Shell-stations weer te geven die worden ondersteund door de Windows Power shell-register provider:</span><span class="sxs-lookup"><span data-stu-id="4c06f-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="4c06f-118">U kunt ook de standaard locatie-cmdlets gebruiken met de Windows Power Shell-stations:</span><span class="sxs-lookup"><span data-stu-id="4c06f-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="4c06f-119">Nieuwe Windows Power Shell-stations toevoegen (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="4c06f-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="4c06f-120">U kunt uw eigen Windows Power Shell-stations toevoegen met behulp van de opdracht **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="4c06f-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="4c06f-121">Als u de syntaxis voor de opdracht **New-PSDrive** wilt ophalen, voert u de opdracht **Get-opdracht** in met de **syntaxis** parameter:</span><span class="sxs-lookup"><span data-stu-id="4c06f-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="4c06f-122">Als u een nieuw Windows Power Shell-station wilt maken, moet u drie para meters opgeven:</span><span class="sxs-lookup"><span data-stu-id="4c06f-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="4c06f-123">Een naam voor het station (u kunt elke geldige Windows Power shell-naam gebruiken)</span><span class="sxs-lookup"><span data-stu-id="4c06f-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="4c06f-124">De PSProvider (gebruik ' File System ' voor bestandssysteem locaties en ' Registry ' voor register locaties)</span><span class="sxs-lookup"><span data-stu-id="4c06f-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="4c06f-125">De basis, dat wil zeggen, het pad naar de hoofdmap van het nieuwe station</span><span class="sxs-lookup"><span data-stu-id="4c06f-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="4c06f-126">U kunt bijvoorbeeld een station met de naam ' Office ' maken dat is toegewezen aan de map die de Microsoft Office toepassingen op uw computer bevat, zoals **C:\\programma bestanden\\Microsoft Office\\Office11**.</span><span class="sxs-lookup"><span data-stu-id="4c06f-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="4c06f-127">Typ de volgende opdracht om het station te maken:</span><span class="sxs-lookup"><span data-stu-id="4c06f-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="4c06f-128">In het algemeen zijn paden niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="4c06f-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="4c06f-129">U verwijst naar het nieuwe Windows Power Shell-station, net zoals u alle Windows Power Shell-stations gebruikt, door de naam gevolgd door een dubbele punt ( **:** ).</span><span class="sxs-lookup"><span data-stu-id="4c06f-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="4c06f-130">Een Windows Power Shell-station kan veel taken veel eenvoudiger maken.</span><span class="sxs-lookup"><span data-stu-id="4c06f-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="4c06f-131">Enkele van de belangrijkste sleutels in het Windows-REGI ster hebben bijvoorbeeld extreem lange paden, waardoor ze lastig toegankelijk zijn en moeilijk te onthouden zijn.</span><span class="sxs-lookup"><span data-stu-id="4c06f-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="4c06f-132">Essentiële configuratie-informatie bevindt zich onder **HKEY_LOCAL_MACHINE\\SOFTWARE\\micro soft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="4c06f-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="4c06f-133">Als u items in de sleutel CurrentVersion wilt bekijken en wijzigen, kunt u een Windows Power Shell-station maken dat in die sleutel is geroot door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="4c06f-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="4c06f-134">U kunt de locatie wijzigen in de **cvkey:** station, net zoals u dat zou doen met een ander station:</span><span class="sxs-lookup"><span data-stu-id="4c06f-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="4c06f-135">of:</span><span class="sxs-lookup"><span data-stu-id="4c06f-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="4c06f-136">Met de cmdlet New-PsDrive wordt het nieuwe station alleen toegevoegd aan de huidige Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="4c06f-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="4c06f-137">Als u het Windows Power shell-venster sluit, gaat het nieuwe station verloren.</span><span class="sxs-lookup"><span data-stu-id="4c06f-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="4c06f-138">Als u een Windows Power Shell-station wilt opslaan, gebruikt u de cmdlet Export-console om de huidige Windows Power shell-sessie te exporteren. vervolgens gebruikt u de para meter **PSConsoleFile** van Power shell. exe om deze te importeren.</span><span class="sxs-lookup"><span data-stu-id="4c06f-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="4c06f-139">U kunt ook het nieuwe station toevoegen aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="4c06f-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="4c06f-140">Windows Power Shell-stations verwijderen (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="4c06f-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="4c06f-141">U kunt stations verwijderen uit Windows Power shell met behulp van de cmdlet **Remove-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="4c06f-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="4c06f-142">De cmdlet **Remove-PSDrive** is eenvoudig te gebruiken. Als u een specifiek Windows Power Shell-station wilt verwijderen, geeft u gewoon de naam van het Windows Power Shell-station op.</span><span class="sxs-lookup"><span data-stu-id="4c06f-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="4c06f-143">Als u bijvoorbeeld het **Office:** Windows Power Shell-station hebt toegevoegd, zoals wordt weer gegeven in het onderwerp **New-PSDrive** , kunt u het verwijderen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="4c06f-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="4c06f-144">Als u het **cvkey:** Windows Power Shell-station, dat ook wordt weer gegeven in het onderwerp **New-PSDrive** , wilt verwijderen, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="4c06f-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="4c06f-145">Het is eenvoudig om een Windows Power Shell-station te verwijderen, maar u kunt het niet verwijderen terwijl u zich in het station bevindt.</span><span class="sxs-lookup"><span data-stu-id="4c06f-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="4c06f-146">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4c06f-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="4c06f-147">Stations toevoegen en verwijderen buiten Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="4c06f-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="4c06f-148">Windows Power shell detecteert bestandssysteem stations die worden toegevoegd of verwijderd in Windows, met inbegrip van netwerk stations die zijn toegewezen, USB-stations die zijn aangesloten en stations die worden verwijderd met behulp van de opdracht **net use** of de methoden **WScript. NetworkMapNetworkDrive** en **RemoveNetworkDrive** van een Windows Script Host (WSH)-script.</span><span class="sxs-lookup"><span data-stu-id="4c06f-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
