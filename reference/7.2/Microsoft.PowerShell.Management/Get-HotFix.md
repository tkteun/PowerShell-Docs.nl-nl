---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 5b5b5939d4dcae8a99b1030b533fe6a85bcc601a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705284"
---
# <span data-ttu-id="3cbf0-102">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="3cbf0-102">Get-HotFix</span></span>

## <span data-ttu-id="3cbf0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3cbf0-103">SYNOPSIS</span></span>
<span data-ttu-id="3cbf0-104">Hiermee worden de hotfixes opgehaald die op lokale of externe computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-104">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="3cbf0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3cbf0-105">SYNTAX</span></span>

### <span data-ttu-id="3cbf0-106">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="3cbf0-106">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="3cbf0-107">Description</span><span class="sxs-lookup"><span data-stu-id="3cbf0-107">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="3cbf0-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3cbf0-108">DESCRIPTION</span></span>

<span data-ttu-id="3cbf0-109">De `Get-Hotfix` cmdlet ontvangt hotfixes of updates die zijn geïnstalleerd op de lokale computer of opgegeven externe computers.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-109">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="3cbf0-110">De updates kunnen worden geïnstalleerd door Windows Update, Microsoft Update, Windows Server Update Services of hand matig geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-110">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="3cbf0-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3cbf0-111">EXAMPLES</span></span>

### <span data-ttu-id="3cbf0-112">Voor beeld 1: alle hotfixes op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="3cbf0-112">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="3cbf0-113">De `Get-Hotfix` cmdlet haalt alle hotfixes op die op de lokale computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-113">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### <span data-ttu-id="3cbf0-114">Voor beeld 2: hotfixes ophalen van meerdere computers gefilterd op een teken reeks</span><span class="sxs-lookup"><span data-stu-id="3cbf0-114">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="3cbf0-115">De `Get-Hotfix` opdracht maakt gebruik van para meters voor het ophalen van hotfixes die op externe computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-115">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="3cbf0-116">De resultaten worden gefilterd op een opgegeven beschrijvings teken reeks.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-116">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="3cbf0-117">`Get-Hotfix` Hiermee wordt de uitvoer gefilterd met de para meter **Description** en de teken reeks **beveiliging** die het sterretje ( `*` )-Joker teken bevat.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-117">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="3cbf0-118">De para meter **ComputerName** bevat een door komma's gescheiden teken reeks met namen van externe computers.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-118">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="3cbf0-119">De **referentie** parameter geeft u een gebruikers account op dat is gemachtigd voor toegang tot de externe computers en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-119">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="3cbf0-120">Voor beeld 3: controleren of een update is geïnstalleerd en computer namen naar een bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3cbf0-120">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="3cbf0-121">Met de opdrachten in dit voor beeld wordt gecontroleerd of een bepaalde update is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-121">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="3cbf0-122">Als de update niet is geïnstalleerd, wordt de naam van de computer naar een tekst bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-122">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="3cbf0-123">De `$A` variabele bevat computer namen die zijn verkregen door `Get-Content` vanuit een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-123">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="3cbf0-124">De objecten in `$A` worden naar beneden verzonden in de pijp lijn `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="3cbf0-124">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="3cbf0-125">Een `if` instructie gebruikt de `Get-Hotfix` cmdlet met de **id-** para meter en een specifiek id-nummer voor elke computer naam.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-125">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="3cbf0-126">Als op een computer de opgegeven hotfix-id niet is geïnstalleerd, `Add-Content` schrijft de cmdlet de computer naam naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-126">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="3cbf0-127">Voor beeld 4: de meest recente hotfix ophalen op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="3cbf0-127">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="3cbf0-128">In dit voor beeld wordt de meest recente hotfix opgehaald die op een computer is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-128">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="3cbf0-129">`Get-Hotfix` Hiermee worden de objecten van de pijp lijn naar de `Sort-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-129">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3cbf0-130">`Sort-Object` objecten worden gesorteerd op oplopende volg orde en de para meter **Property** wordt gebruikt om elke **InstalledOn** -datum te evalueren.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-130">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="3cbf0-131">De matrix notatie `[-1]` selecteert de meest recente geïnstalleerde hotfix.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-131">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="3cbf0-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3cbf0-132">PARAMETERS</span></span>

### <span data-ttu-id="3cbf0-133">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3cbf0-133">-ComputerName</span></span>

<span data-ttu-id="3cbf0-134">Hiermee geeft u een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-134">Specifies a remote computer.</span></span> <span data-ttu-id="3cbf0-135">Typ de NetBIOS-naam, een Internet Protocol (IP-adres) of een Fully Qualified Domain Name (FQDN) van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-135">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="3cbf0-136">Wanneer de para meter **ComputerName** niet is opgegeven, `Get-Hotfix` wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-136">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="3cbf0-137">De para meter **ComputerName** is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-137">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="3cbf0-138">Als uw computer niet is geconfigureerd voor het uitvoeren van externe opdrachten, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="3cbf0-138">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3cbf0-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="3cbf0-139">-Credential</span></span>

<span data-ttu-id="3cbf0-140">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-140">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="3cbf0-141">De standaard waarde is de huidige gebruiker</span><span class="sxs-lookup"><span data-stu-id="3cbf0-141">The default is the current user</span></span>

<span data-ttu-id="3cbf0-142">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3cbf0-142">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3cbf0-143">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-143">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="3cbf0-144">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="3cbf0-144">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="3cbf0-145">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-145">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cbf0-146">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3cbf0-146">-Description</span></span>

<span data-ttu-id="3cbf0-147">`Get-HotFix` maakt gebruik van de **beschrijvings** parameter om typen hotfixes op te geven.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-147">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="3cbf0-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-148">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3cbf0-149">-Id</span><span class="sxs-lookup"><span data-stu-id="3cbf0-149">-Id</span></span>

<span data-ttu-id="3cbf0-150">Hiermee worden de `Get-HotFix` resultaten voor specifieke hotfix-id's gefilterd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-150">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="3cbf0-151">Joker tekens worden niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-151">Wildcards aren't accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cbf0-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3cbf0-152">CommonParameters</span></span>

<span data-ttu-id="3cbf0-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3cbf0-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3cbf0-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="3cbf0-155">INPUTS</span></span>

### <span data-ttu-id="3cbf0-156">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3cbf0-156">String</span></span>

<span data-ttu-id="3cbf0-157">U kunt een of meer computer namen door geven om-HotFix op te halen.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-157">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="3cbf0-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3cbf0-158">OUTPUTS</span></span>

### <span data-ttu-id="3cbf0-159">System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="3cbf0-159">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="3cbf0-160">`Get-HotFix` retourneert objecten die de hotfixes op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-160">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="3cbf0-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3cbf0-161">NOTES</span></span>

<span data-ttu-id="3cbf0-162">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-162">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="3cbf0-163">De  [WMI-klasse](/windows/desktop/WmiSdk/retrieving-a-class) Win32_QuickFixEngineering vertegenwoordigt een kleine update van het hele systeem, vaak een QFE-update (Quick-Fix Engineering) genoemd, toegepast op het huidige besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-163">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="3cbf0-164">Deze klasse retourneert alleen de updates die zijn geleverd door CBS (Component Based Servicing).</span><span class="sxs-lookup"><span data-stu-id="3cbf0-164">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="3cbf0-165">Deze updates worden niet vermeld in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-165">These updates are not listed in the registry.</span></span> <span data-ttu-id="3cbf0-166">Updates die zijn geleverd door Microsoft Windows Installer (MSI) of de [Windows Update](https://update.microsoft.com) -site, worden niet door **Win32_QuickFixEngineering** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-166">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="3cbf0-167">Zie [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-167">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="3cbf0-168">De `Get-HotFix` uitvoer kan variëren op verschillende besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="3cbf0-168">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="3cbf0-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3cbf0-169">RELATED LINKS</span></span>

[<span data-ttu-id="3cbf0-170">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="3cbf0-170">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="3cbf0-171">Add-content</span><span class="sxs-lookup"><span data-stu-id="3cbf0-171">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="3cbf0-172">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="3cbf0-172">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="3cbf0-173">Win32_QuickFixEngineering klasse</span><span class="sxs-lookup"><span data-stu-id="3cbf0-173">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
