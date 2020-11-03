---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: f5000ec88defda441d5f31f6ead5d8c37412857b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251020"
---
# <span data-ttu-id="1df7d-103">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1df7d-103">Get-PSDrive</span></span>

## <span data-ttu-id="1df7d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1df7d-104">SYNOPSIS</span></span>
<span data-ttu-id="1df7d-105">Hiermee worden de stations in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1df7d-105">Gets drives in the current session.</span></span>

## <span data-ttu-id="1df7d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1df7d-106">SYNTAX</span></span>

### <span data-ttu-id="1df7d-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="1df7d-107">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1df7d-108">Letterlijke waarde</span><span class="sxs-lookup"><span data-stu-id="1df7d-108">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="1df7d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1df7d-109">DESCRIPTION</span></span>

<span data-ttu-id="1df7d-110">De- `Get-PSDrive` cmdlet haalt de stations in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="1df7d-110">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="1df7d-111">U kunt een bepaald station of alle stations in de sessie ophalen.</span><span class="sxs-lookup"><span data-stu-id="1df7d-111">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="1df7d-112">Met deze cmdlet worden de volgende typen stations opgehaald:</span><span class="sxs-lookup"><span data-stu-id="1df7d-112">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="1df7d-113">Logische Windows-stations op de computer, inclusief stations die zijn toegewezen aan netwerk shares.</span><span class="sxs-lookup"><span data-stu-id="1df7d-113">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="1df7d-114">Schijven die beschikbaar worden gesteld door Power shell-providers (zoals het certificaat:, de functie: en alias: stations) en de HKLM: en HKCU: stations die worden weer gegeven door de Windows Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="1df7d-114">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="1df7d-115">Door de sessie opgegeven tijdelijke stations en permanente toegewezen netwerk stations die u maakt met behulp van de cmdlet New-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="1df7d-115">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="1df7d-116">Vanaf Windows Power Shell 3,0 kan de **persistente** para meter van de `New-PSDrive` cmdlet toegewezen netwerk stations maken die op de lokale computer zijn opgeslagen en in andere sessies beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="1df7d-116">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="1df7d-117">Zie New-PSDrive voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1df7d-117">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="1df7d-118">Vanuit Windows Power Shell 3,0, wanneer een extern station is verbonden met de computer, wordt in Windows Power shell automatisch een PSDrive toegevoegd aan het bestands systeem dat het nieuwe station vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1df7d-118">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="1df7d-119">U hoeft Windows Power shell niet opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="1df7d-119">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="1df7d-120">Op dezelfde manier verwijdert Windows Power shell automatisch de PSDrive die de verwijderde schijf vertegenwoordigt wanneer een extern station wordt losgekoppeld van de computer.</span><span class="sxs-lookup"><span data-stu-id="1df7d-120">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="1df7d-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1df7d-121">EXAMPLES</span></span>

### <span data-ttu-id="1df7d-122">Voor beeld 1: stations in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="1df7d-122">Example 1: Get drives in the current session</span></span>

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

<span data-ttu-id="1df7d-123">Met deze opdracht worden de stations in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1df7d-123">This command gets the drives in the current session.</span></span>

<span data-ttu-id="1df7d-124">In de uitvoer ziet u de harde schijf (C:), het CD-ROM-station (D:) en de stations die worden weer gegeven door de Windows Power shell-providers (alias:, CERT:, env:, function:, HKCU:, HKLM: en variable:).</span><span class="sxs-lookup"><span data-stu-id="1df7d-124">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="1df7d-125">Voor beeld 2: een station op de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="1df7d-125">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="1df7d-126">Met deze opdracht wordt het station D: op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1df7d-126">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="1df7d-127">Houd er rekening mee dat de stationsletter in de opdracht niet wordt gevolgd door een dubbele punt.</span><span class="sxs-lookup"><span data-stu-id="1df7d-127">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="1df7d-128">Voor beeld 3: alle stations ophalen die worden ondersteund door de Windows Power shell File System-Provider</span><span class="sxs-lookup"><span data-stu-id="1df7d-128">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="1df7d-129">Met deze opdracht worden alle stations opgehaald die worden ondersteund door de Windows Power shell-bestandssysteem provider.</span><span class="sxs-lookup"><span data-stu-id="1df7d-129">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="1df7d-130">Dit omvat vaste stations, logische partities, toegewezen netwerk stations en tijdelijke stations die u maakt met behulp van de New-PSDrive-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1df7d-130">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="1df7d-131">Voor beeld 4: controleren of een station wordt gebruikt als een Windows Power shell-stationsnaam</span><span class="sxs-lookup"><span data-stu-id="1df7d-131">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="1df7d-132">Met deze opdracht wordt gecontroleerd of het X-station al in gebruik is als de naam van een Windows Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="1df7d-132">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="1df7d-133">Als dat niet het geval is, gebruikt de opdracht de `New-PSDrive` cmdlet om een tijdelijke schijf te maken die is toegewezen aan de register sleutel HKLM: \ software.</span><span class="sxs-lookup"><span data-stu-id="1df7d-133">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="1df7d-134">Voor beeld 5: de typen bestanden vergelijken systeem stations</span><span class="sxs-lookup"><span data-stu-id="1df7d-134">Example 5: Compare the types of files system drives</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

<span data-ttu-id="1df7d-135">In dit voor beeld worden de typen bestandssysteem stations vergeleken die worden weer gegeven met `Get-PSDrive` behulp van andere methoden.</span><span class="sxs-lookup"><span data-stu-id="1df7d-135">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="1df7d-136">In dit voor beeld ziet u verschillende manieren om stations weer te geven in Windows Power shell en ziet u dat sessie-specifieke stations die zijn gemaakt met behulp van de New-PSDrive cmdlet alleen toegankelijk zijn in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="1df7d-136">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="1df7d-137">De eerste opdracht wordt gebruikt `Get-PSDrive` om alle bestandssysteem stations in de sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="1df7d-137">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="1df7d-138">Dit omvat de vaste stations (C: en D:), een toegewezen netwerk station (G:) dat is gemaakt met behulp van de **persistente** para meter van `New-PSDrive` en een Power Shell-station (T:) die is gemaakt met `New-PSDrive` zonder de para meter **persistent** .</span><span class="sxs-lookup"><span data-stu-id="1df7d-138">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="1df7d-139">Met de opdracht **net use** worden Windows toegewezen netwerk stations weer gegeven, in dit geval alleen het station G.</span><span class="sxs-lookup"><span data-stu-id="1df7d-139">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="1df7d-140">De X:-station dat is gemaakt door, wordt niet weer gegeven `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1df7d-140">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="1df7d-141">U ziet dat het station G: ook is toegewezen aan \\ \\ Muziek- \\ GratefulDead.</span><span class="sxs-lookup"><span data-stu-id="1df7d-141">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="1df7d-142">De derde opdracht maakt gebruik van de methode **GetDrives** van de klasse Microsoft .NET Framework **System. io. DriveInfo** .</span><span class="sxs-lookup"><span data-stu-id="1df7d-142">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="1df7d-143">Met deze opdracht worden de stations van het Windows-Bestands systeem met inbegrip van station G: opgehaald, maar worden de stations die worden gemaakt door niet opgehaald `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1df7d-143">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="1df7d-144">De vierde opdracht gebruikt de `Get-CimInstance` cmdlet om de exemplaren van de klasse **Win32_LogicalDisk** op te halen.</span><span class="sxs-lookup"><span data-stu-id="1df7d-144">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="1df7d-145">Het retourneert de stations A:, C:, D:, E: en G:, maar niet de stations die zijn gemaakt door `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1df7d-145">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="1df7d-146">De laatste opdracht gebruikt de `Get-CimInstance` cmdlet om de instanties van de **Win32_NetworkConnection** -klasse weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1df7d-146">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="1df7d-147">Net zoals **net use** retourneert het alleen het permanente G: station dat is gemaakt door `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="1df7d-147">Like **net use** , it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="1df7d-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1df7d-148">PARAMETERS</span></span>

### <span data-ttu-id="1df7d-149">-Literal-waarde</span><span class="sxs-lookup"><span data-stu-id="1df7d-149">-LiteralName</span></span>

<span data-ttu-id="1df7d-150">Hiermee geeft u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="1df7d-150">Specifies the name of the drive.</span></span>

<span data-ttu-id="1df7d-151">De waarde van **literal** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="1df7d-151">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="1df7d-152">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="1df7d-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1df7d-153">Als de naam escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="1df7d-153">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1df7d-154">Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="1df7d-154">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1df7d-155">-Name</span><span class="sxs-lookup"><span data-stu-id="1df7d-155">-Name</span></span>

<span data-ttu-id="1df7d-156">Hiermee geeft u als een teken reeks matrix de naam of de naam van de stations die met deze cmdlet worden opgehaald in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="1df7d-156">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="1df7d-157">Typ de naam van het station of de letter zonder een dubbele punt (:).</span><span class="sxs-lookup"><span data-stu-id="1df7d-157">Type the drive name or letter without a colon (:).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1df7d-158">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="1df7d-158">-PSProvider</span></span>

<span data-ttu-id="1df7d-159">Hiermee wordt de Windows Power shell-provider opgegeven als een teken reeks matrix.</span><span class="sxs-lookup"><span data-stu-id="1df7d-159">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="1df7d-160">Met deze cmdlet worden alleen de stations opgehaald die door deze provider worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1df7d-160">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="1df7d-161">Typ de naam van een provider, zoals File System, Registry of Certificate.</span><span class="sxs-lookup"><span data-stu-id="1df7d-161">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1df7d-162">-Bereik</span><span class="sxs-lookup"><span data-stu-id="1df7d-162">-Scope</span></span>

<span data-ttu-id="1df7d-163">Hiermee geeft u het bereik op waarin met deze cmdlet de stations worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1df7d-163">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="1df7d-164">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="1df7d-164">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1df7d-165">Globaal</span><span class="sxs-lookup"><span data-stu-id="1df7d-165">Global</span></span>
- <span data-ttu-id="1df7d-166">Lokaal</span><span class="sxs-lookup"><span data-stu-id="1df7d-166">Local</span></span>
- <span data-ttu-id="1df7d-167">Script</span><span class="sxs-lookup"><span data-stu-id="1df7d-167">Script</span></span>
- <span data-ttu-id="1df7d-168">een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope).</span><span class="sxs-lookup"><span data-stu-id="1df7d-168">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="1df7d-169">' Local ' is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="1df7d-169">"Local" is the default.</span></span>

<span data-ttu-id="1df7d-170">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1df7d-170">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="1df7d-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1df7d-171">CommonParameters</span></span>

<span data-ttu-id="1df7d-172">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1df7d-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1df7d-173">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1df7d-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1df7d-174">INVOER</span><span class="sxs-lookup"><span data-stu-id="1df7d-174">INPUTS</span></span>

### <span data-ttu-id="1df7d-175">Geen</span><span class="sxs-lookup"><span data-stu-id="1df7d-175">None</span></span>

<span data-ttu-id="1df7d-176">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="1df7d-176">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="1df7d-177">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1df7d-177">OUTPUTS</span></span>

### <span data-ttu-id="1df7d-178">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="1df7d-178">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="1df7d-179">Deze cmdlet retourneert objecten die de stations in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="1df7d-179">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="1df7d-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1df7d-180">NOTES</span></span>

* <span data-ttu-id="1df7d-181">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1df7d-181">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="1df7d-182">Gebruik de cmdlet om de providers weer te geven die beschikbaar zijn in uw sessie `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="1df7d-182">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="1df7d-183">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1df7d-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="1df7d-184">Toegewezen netwerk stations die worden gemaakt met behulp van de para meter **persistent** van de cmdlet New-PSDrive, zijn specifiek voor een gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="1df7d-184">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="1df7d-185">Toegewezen netwerk stations die u maakt in sessies die worden gestart met de optie als administrator uitvoeren of met de referenties van een andere gebruiker, zijn niet zichtbaar in sessies die worden gestart zonder expliciete referenties of met de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1df7d-185">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="1df7d-186">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1df7d-186">RELATED LINKS</span></span>

[<span data-ttu-id="1df7d-187">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1df7d-187">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="1df7d-188">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="1df7d-188">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="1df7d-189">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="1df7d-189">Get-PSProvider</span></span>](Get-PSProvider.md)
