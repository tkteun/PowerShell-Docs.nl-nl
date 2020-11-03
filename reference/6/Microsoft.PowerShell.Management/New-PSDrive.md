---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 04346a3bd324b2d7033405546f131d2d56c5a2bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250235"
---
# <span data-ttu-id="2dd4b-103">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2dd4b-103">New-PSDrive</span></span>

## <span data-ttu-id="2dd4b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2dd4b-104">SYNOPSIS</span></span>
<span data-ttu-id="2dd4b-105">Hiermee worden tijdelijke en permanente toegewezen netwerk stations gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-105">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="2dd4b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2dd4b-106">SYNTAX</span></span>

### <span data-ttu-id="2dd4b-107">Alles</span><span class="sxs-lookup"><span data-stu-id="2dd4b-107">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2dd4b-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2dd4b-108">DESCRIPTION</span></span>

<span data-ttu-id="2dd4b-109">De `New-PSDrive` cmdlet maakt tijdelijke en permanente stations die zijn toegewezen aan of gekoppeld aan een locatie in een gegevens archief, zoals een netwerk station, een map op de lokale computer of een register sleutel, en permanente Windows-toegewezen netwerk stations die zijn gekoppeld aan een bestandssysteem locatie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-109">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="2dd4b-110">Tijdelijke schijven bestaan alleen in de huidige Power shell-sessie en in sessies die u in de huidige sessie maakt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-110">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="2dd4b-111">Ze kunnen een wille keurige naam hebben die geldig is in Power shell en kan worden toegewezen aan een lokale of externe bron.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-111">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="2dd4b-112">U kunt tijdelijke Power Shell-stations gebruiken om toegang te krijgen tot gegevens in het bijbehorende gegevens archief, net zoals u dat zou doen met een toegewezen netwerk station.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-112">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="2dd4b-113">U kunt locaties wijzigen in het station, met behulp `Set-Location` van en toegang tot de inhoud van het station met behulp van `Get-Item` of `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-113">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="2dd4b-114">Omdat tijdelijke stations alleen bekend zijn bij Power shell, hebt u geen toegang tot de schijven met behulp van bestanden Verkenner, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework of met hulpprogram ma's zoals **net use**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-114">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use**.</span></span>

<span data-ttu-id="2dd4b-115">De volgende functies zijn toegevoegd aan `New-PSDrive` in Power shell 3,0:</span><span class="sxs-lookup"><span data-stu-id="2dd4b-115">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="2dd4b-116">Toegewezen netwerk stations.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-116">Mapped network drives.</span></span> <span data-ttu-id="2dd4b-117">U kunt de para meter **persistent** van gebruiken `New-PSDrive` om toegewezen Windows-netwerk stations te maken.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-117">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="2dd4b-118">In tegens telling tot tijdelijke Power Shell-stations zijn Windows toegewezen netwerk stations niet specifiek voor een bepaalde sessie.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-118">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="2dd4b-119">Ze worden opgeslagen in Windows en kunnen worden beheerd met behulp van standaard Windows-hulpprogram ma's, zoals bestanden Verkenner en **net-gebruik**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-119">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use**.</span></span> <span data-ttu-id="2dd4b-120">Toegewezen netwerk stations moeten een stationsletter naam hebben en moeten zijn verbonden met een locatie op een extern bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-120">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="2dd4b-121">Als uw opdracht lokaal is, zonder punt, blijft de para meter **persistent** het maken van een **PSDrive** buiten het bereik waarin de opdracht wordt uitgevoerd, niet behouden.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-121">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="2dd4b-122">Als u `New-PSDrive` in een script werkt en u wilt dat het station voor onbepaalde tijd blijft bestaan, moet u het script naar een punt schrijven.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-122">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="2dd4b-123">Voor de beste resultaten kunt u een nieuw station geforceerd voor onbepaalde tijd blijven toevoegen door de para meter **bereik** toe te voegen aan uw opdracht en de waarde ervan in te stellen op **Global**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-123">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global**.</span></span> <span data-ttu-id="2dd4b-124">Zie [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)voor meer informatie over dot-sourcing.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-124">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="2dd4b-125">Externe stations.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-125">External drives.</span></span> <span data-ttu-id="2dd4b-126">Wanneer een extern station is verbonden met de computer, voegt Power shell automatisch een **PSDrive** toe aan het bestands systeem dat het nieuwe station vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-126">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="2dd4b-127">U hoeft Power shell niet opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-127">You don't have to restart PowerShell.</span></span> <span data-ttu-id="2dd4b-128">Op dezelfde manier verwijdert Power shell automatisch de **PSDrive** die de verwijderde schijf vertegenwoordigt wanneer een extern station wordt losgekoppeld van de computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-128">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="2dd4b-129">Referenties voor UNC-paden (Universal Naming Convention).</span><span class="sxs-lookup"><span data-stu-id="2dd4b-129">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="2dd4b-130">Wanneer de waarde van de **hoofd** parameter een UNC-pad is, zoals `\\Server\Share` , wordt de referentie die is opgegeven in de waarde van de para meter **Credential** , gebruikt om de **PSDrive** te maken.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-130">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive**.</span></span> <span data-ttu-id="2dd4b-131">Anders is de **referentie** niet effectief wanneer u nieuwe stations voor het bestands systeem maakt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-131">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="2dd4b-132">Sommige code voorbeelden gebruiken splatting om de lengte van de lijn te verkleinen en de Lees baarheid te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-132">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="2dd4b-133">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-133">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="2dd4b-134">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2dd4b-134">EXAMPLES</span></span>

### <span data-ttu-id="2dd4b-135">Voor beeld 1: een tijdelijk station maken dat is toegewezen aan een netwerk share</span><span class="sxs-lookup"><span data-stu-id="2dd4b-135">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="2dd4b-136">In dit voor beeld maakt u een tijdelijk Power Shell-station dat is toegewezen aan een netwerk share.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-136">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="2dd4b-137">`New-PSDrive` maakt gebruik van de para meter **name** om een Power Shell-station met `Public` de naam en de para meter **PSProvider** op te geven voor de Power shell- `FileSystem` provider.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-137">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="2dd4b-138">Met de para meter **root** wordt het UNC-pad van de netwerk share opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-138">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="2dd4b-139">De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="2dd4b-139">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="2dd4b-140">Voor beeld 2: een tijdelijk station maken dat is toegewezen aan een lokale map</span><span class="sxs-lookup"><span data-stu-id="2dd4b-140">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="2dd4b-141">In dit voor beeld wordt een tijdelijk Power Shell-station gemaakt dat toegang biedt tot een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-141">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

<span data-ttu-id="2dd4b-142">Splatting maakt de parameter sleutels en-waarden.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-142">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="2dd4b-143">De para meter **name** specificeert de naam van het station, **MyDocs**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-143">The **Name** parameter specifies the drive name, **MyDocs**.</span></span> <span data-ttu-id="2dd4b-144">De **PSProvider** para meter geeft u de Power shell- `FileSystem` provider op.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-144">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="2dd4b-145">**Root** Hiermee geeft u de map van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-145">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="2dd4b-146">De **beschrijvings** parameter beschrijft het doel van het station.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-146">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="2dd4b-147">`New-PSDrive` maakt gebruik van de splatted-para meters om het station te maken `MyDocs` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-147">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="2dd4b-148">De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="2dd4b-148">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="2dd4b-149">Voor beeld 3: een tijdelijke schijf maken voor een register sleutel</span><span class="sxs-lookup"><span data-stu-id="2dd4b-149">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="2dd4b-150">In dit voor beeld wordt een tijdelijk Power Shell-station gemaakt dat toegang biedt tot een register sleutel.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-150">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="2dd4b-151">Er wordt een station gemaakt met de naam mijn bedrijf die is toegewezen aan de `HKLM:\Software\MyCompany` register sleutel.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-151">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="2dd4b-152">`New-PSDrive` maakt gebruik van de para meter **name** om een Power Shell-station met `MyCompany` de naam en de para meter **PSProvider** op te geven voor de Power shell- `Registry` provider.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-152">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="2dd4b-153">Met de para meter **root** wordt de register locatie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-153">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="2dd4b-154">De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="2dd4b-154">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="2dd4b-155">Voor beeld 4: een permanent toegewezen netwerk station maken met behulp van referenties</span><span class="sxs-lookup"><span data-stu-id="2dd4b-155">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="2dd4b-156">In dit voor beeld wordt een netwerk station toegewezen dat is geverifieerd met de referenties van een domein service account.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-156">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="2dd4b-157">Zie de beschrijving van de **referentie** parameter voor meer informatie over het **PSCredential** -object waarin referenties worden opgeslagen en hoe wacht woorden worden opgeslagen als **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-157">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString** , see the **Credential** parameter's description.</span></span>

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> <span data-ttu-id="2dd4b-158">Houd er rekening mee dat als u het bovenstaande fragment in een script gebruikt, de waarde voor de **bereik** parameter instelt op ' globaal ' om ervoor te zorgen dat het station zich buiten het huidige bereik bevindt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-158">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="2dd4b-159">De `$cred` variabele bevat een **PSCredential** -object met de referenties van het service account.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-159">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="2dd4b-160">`Get-Credential` Hiermee wordt u gevraagd het wacht woord in te voeren dat is opgeslagen in een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-160">`Get-Credential` prompts you to enter the password that's stored in a **SecureString**.</span></span>

<span data-ttu-id="2dd4b-161">`New-PSDrive` Hiermee maakt u het toegewezen netwerk station met behulp van verschillende para meters.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-161">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="2dd4b-162">**Naam** Hiermee geeft u de stationsletter op `S` die door Windows wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-162">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="2dd4b-163">en **root** definieert `\\Server01\Scripts` als de locatie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-163">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="2dd4b-164">Met **persistent** maakt u een Windows-toegewezen netwerk station dat is opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-164">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="2dd4b-165">**PSProvider** Hiermee geeft u de `FileSystem` provider op.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-165">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="2dd4b-166">**Referentie** gebruikt de `$cred` variabele om de referenties van het service account voor verificatie op te halen.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-166">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="2dd4b-167">Het toegewezen station kan worden weer gegeven op de lokale computer in Power shell-sessies, bestanden Verkenner en met hulpprogram ma's zoals **net use**.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-167">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use**.</span></span> <span data-ttu-id="2dd4b-168">De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="2dd4b-168">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="2dd4b-169">Voor beeld 5: permanente en tijdelijke stations maken</span><span class="sxs-lookup"><span data-stu-id="2dd4b-169">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="2dd4b-170">In dit voor beeld ziet u het verschil tussen een permanent toegewezen netwerk station en een tijdelijk Power Shell-station dat is toegewezen aan dezelfde netwerk share.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-170">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="2dd4b-171">Als u de Power shell-sessie sluit en vervolgens een nieuwe sessie opent, is de tijdelijke `PSDrive:` schijf niet beschikbaar, maar is het permanente `X:` station beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-171">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="2dd4b-172">Wanneer u bepaalt welke methode u moet gebruiken voor het toewijzen van netwerk stations, kunt u overwegen hoe u het station gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-172">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="2dd4b-173">Bijvoorbeeld of het permanent moet blijven en of het station zichtbaar moet zijn voor andere Windows-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-173">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## <span data-ttu-id="2dd4b-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2dd4b-174">PARAMETERS</span></span>

### <span data-ttu-id="2dd4b-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2dd4b-175">-Confirm</span></span>

<span data-ttu-id="2dd4b-176">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-177">-Credential</span><span class="sxs-lookup"><span data-stu-id="2dd4b-177">-Credential</span></span>

<span data-ttu-id="2dd4b-178">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-178">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="2dd4b-179">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-179">The default is the current user.</span></span>

<span data-ttu-id="2dd4b-180">Sinds Power Shell 3,0, wanneer de waarde van de **hoofd** parameter een UNC-pad is, kunt u referenties gebruiken om bestandssysteem stations te maken.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-180">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="2dd4b-181">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-181">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2dd4b-182">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-182">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2dd4b-183">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="2dd4b-183">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2dd4b-184">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-184">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-185">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2dd4b-185">-Description</span></span>

<span data-ttu-id="2dd4b-186">Hiermee geeft u een korte beschrijving van het station.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-186">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="2dd4b-187">Typ een wille keurige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-187">Type any string.</span></span>

<span data-ttu-id="2dd4b-188">Als u de beschrijvingen van alle stations van de sessie wilt zien, gaat u naar `Get-PSDrive | Format-Table Name, Description` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-188">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="2dd4b-189">Als u de beschrijving van een bepaald station wilt weer geven, typt u `(Get-PSDrive <DriveName>).Description` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-189">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-190">-Name</span><span class="sxs-lookup"><span data-stu-id="2dd4b-190">-Name</span></span>

<span data-ttu-id="2dd4b-191">Hiermee geeft u een naam op voor het nieuwe station.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-191">Specifies a name for the new drive.</span></span> <span data-ttu-id="2dd4b-192">Voor permanente toegewezen netwerk stations gebruikt u een stationsletter.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-192">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="2dd4b-193">Voor tijdelijke Power Shell-stations bent u niet beperkt tot stationsletters. gebruik een geldige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-193">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-194">-Persistent</span><span class="sxs-lookup"><span data-stu-id="2dd4b-194">-Persist</span></span>

<span data-ttu-id="2dd4b-195">Geeft aan dat met deze cmdlet een Windows-toegewezen netwerk station wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-195">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="2dd4b-196">De para meter **persistent** is alleen beschikbaar in Windows.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-196">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="2dd4b-197">Toegewezen netwerk stations worden opgeslagen in Windows op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-197">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="2dd4b-198">Ze zijn permanent, niet voor sessie-specifiek en kunnen worden weer gegeven en beheerd in Verkenner en andere hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-198">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="2dd4b-199">Wanneer u de opdracht lokaal en zonder punt-sourcing bereikt, blijft de para meter **persistent** het maken van een **PSDrive** buiten het bereik waarin u de opdracht uitvoert niet behouden.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-199">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="2dd4b-200">Als u `New-PSDrive` in een script uitvoert en u wilt dat het nieuwe station voor onbepaalde tijd blijft bestaan, moet u het script op de gewenste punt zetten.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-200">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="2dd4b-201">Als u de beste resultaten wilt afdwingen, geeft u **globaal** op als de waarde van de **bereik** parameter en neemt u **persistent** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-201">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="2dd4b-202">De naam van het station moet een letter zijn, zoals `D` of `E` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-202">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="2dd4b-203">De waarde van de **hoofd** parameter moet een UNC-pad van een andere computer zijn.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-203">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="2dd4b-204">De waarde van de para meter **PSProvider** moet zijn `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-204">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="2dd4b-205">Gebruik de cmdlet om een Windows-toegewezen netwerk station te verbreken `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-205">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="2dd4b-206">Wanneer u een Windows-toegewezen netwerk station verbreekt, wordt de toewijzing permanent verwijderd van de computer, niet alleen verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-206">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="2dd4b-207">Toegewezen netwerk stations zijn specifiek voor een gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-207">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="2dd4b-208">Toegewezen stations die zijn gemaakt in verhoogde sessies of sessies met de referenties van een andere gebruiker zijn niet zichtbaar in sessies die zijn gestart met andere referenties.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-208">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-209">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="2dd4b-209">-PSProvider</span></span>

<span data-ttu-id="2dd4b-210">Hiermee geeft u de Power shell-provider op die ondersteuning biedt voor stations van dit type.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-210">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="2dd4b-211">Als het station bijvoorbeeld is gekoppeld aan een netwerk share of een map van het bestands systeem, is de Power shell-provider `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-211">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="2dd4b-212">Als het station is gekoppeld aan een register sleutel, is de provider `Registry` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-212">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="2dd4b-213">Tijdelijke Power Shell-stations kunnen worden gekoppeld aan elke Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-213">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="2dd4b-214">Toegewezen netwerk stations kunnen alleen worden gekoppeld met de `FileSystem` provider.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-214">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="2dd4b-215">Als u een lijst met providers in uw Power shell-sessie wilt zien, gebruikt u de `Get-PSProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-215">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-216">-Root</span><span class="sxs-lookup"><span data-stu-id="2dd4b-216">-Root</span></span>

<span data-ttu-id="2dd4b-217">Hiermee geeft u de locatie van het gegevens archief waaraan een Power Shell-station is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-217">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="2dd4b-218">Geef bijvoorbeeld een netwerk share op, zoals `\\Server01\Public` een lokale map, zoals `C:\Program Files` of een register sleutel, zoals `HKLM:\Software\Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-218">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="2dd4b-219">Tijdelijke Power Shell-stations kunnen worden gekoppeld aan een lokale of externe locatie op elk ondersteund provider-station.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-219">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="2dd4b-220">Toegewezen netwerk stations kunnen alleen worden gekoppeld aan een bestandssysteem locatie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-220">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-221">-Bereik</span><span class="sxs-lookup"><span data-stu-id="2dd4b-221">-Scope</span></span>

<span data-ttu-id="2dd4b-222">Hiermee geeft u een bereik voor het station.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-222">Specifies a scope for the drive.</span></span> <span data-ttu-id="2dd4b-223">De acceptabele waarden voor deze para meter zijn: **Global** , **Local** en **script** , of een getal dat relatief is ten opzichte van het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-223">The acceptable values for this parameter are: **Global** , **Local** , and **Script** , or a number relative to the current scope.</span></span> <span data-ttu-id="2dd4b-224">Bereiken nummer 0 tot het aantal bereiken.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-224">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="2dd4b-225">Het huidige bereik nummer is 0 en de bovenliggende waarde is 1.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-225">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="2dd4b-226">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-226">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-227">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2dd4b-227">-WhatIf</span></span>

<span data-ttu-id="2dd4b-228">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-228">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2dd4b-229">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-229">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dd4b-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2dd4b-230">CommonParameters</span></span>

<span data-ttu-id="2dd4b-231">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-231">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2dd4b-232">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-232">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2dd4b-233">INVOER</span><span class="sxs-lookup"><span data-stu-id="2dd4b-233">INPUTS</span></span>

### <span data-ttu-id="2dd4b-234">Geen</span><span class="sxs-lookup"><span data-stu-id="2dd4b-234">None</span></span>

<span data-ttu-id="2dd4b-235">U kunt geen pijplijn invoer voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-235">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="2dd4b-236">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2dd4b-236">OUTPUTS</span></span>

### <span data-ttu-id="2dd4b-237">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="2dd4b-237">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="2dd4b-238">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2dd4b-238">NOTES</span></span>

<span data-ttu-id="2dd4b-239">`New-PSDrive` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-239">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2dd4b-240">Gebruik om een lijst weer te geven van de providers die beschikbaar zijn in uw sessie `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="2dd4b-240">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="2dd4b-241">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie over providers.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-241">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="2dd4b-242">Toegewezen netwerk stations zijn specifiek voor een gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-242">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="2dd4b-243">Toegewezen stations die zijn gemaakt in verhoogde sessies of sessies met de referenties van een andere gebruiker zijn niet zichtbaar in sessies die zijn gestart met andere referenties.</span><span class="sxs-lookup"><span data-stu-id="2dd4b-243">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="2dd4b-244">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2dd4b-244">RELATED LINKS</span></span>

[<span data-ttu-id="2dd4b-245">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2dd4b-245">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="2dd4b-246">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="2dd4b-246">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="2dd4b-247">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2dd4b-247">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="2dd4b-248">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="2dd4b-248">Remove-PSDrive</span></span>](Remove-PSDrive.md)
