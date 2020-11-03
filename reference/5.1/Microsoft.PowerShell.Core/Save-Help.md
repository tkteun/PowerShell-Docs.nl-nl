---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: c917e9256d49e9af70f35914a27e204a4f6efd15
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250144"
---
# <span data-ttu-id="aa996-103">Save-Help</span><span class="sxs-lookup"><span data-stu-id="aa996-103">Save-Help</span></span>

## <span data-ttu-id="aa996-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aa996-104">SYNOPSIS</span></span>
<span data-ttu-id="aa996-105">Hiermee worden de nieuwste Help-bestanden gedownload en opgeslagen in een map van het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="aa996-105">Downloads and saves the newest help files to a file system directory.</span></span>

## <span data-ttu-id="aa996-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aa996-106">SYNTAX</span></span>

### <span data-ttu-id="aa996-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="aa996-107">Path (Default)</span></span>

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="aa996-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aa996-108">LiteralPath</span></span>

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force]
 [<CommonParameters>]
```

## <span data-ttu-id="aa996-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aa996-109">DESCRIPTION</span></span>

<span data-ttu-id="aa996-110">De cmdlet **Save-Help** downloadt de nieuwste Help-bestanden voor Power shell-modules en slaat deze op in een door u opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="aa996-110">The **Save-Help** cmdlet downloads the newest help files for PowerShell modules and saves them to a directory that you specify.</span></span>
<span data-ttu-id="aa996-111">Met deze functie kunt u de Help-bestanden bijwerken op computers die geen toegang hebben tot internet, en kunt u de Help-bestanden op meerdere computers eenvoudiger bijwerken.</span><span class="sxs-lookup"><span data-stu-id="aa996-111">This feature lets you update the help files on computers that do not have access to the Internet, and makes it easier to update the help files on multiple computers.</span></span>

<span data-ttu-id="aa996-112">In Windows Power Shell 3,0, **opslaan-Help** alleen voor modules die zijn geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="aa996-112">In Windows PowerShell 3.0, **Save-Help** worked only for modules that are installed on the local computer.</span></span>
<span data-ttu-id="aa996-113">Hoewel het mogelijk is om een module te importeren vanaf een externe computer, of een verwijzing naar een **PSModuleInfo** -object te verkrijgen van een externe computer met behulp van externe communicatie met Power shell, is de eigenschap **HelpInfoUri** niet behouden en is het niet mogelijk om **de Help voor** externe modules te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aa996-113">Although it was possible to import a module from a remote computer, or obtain a reference to a **PSModuleInfo** object from a remote computer by using PowerShell remoting, the **HelpInfoUri** property was not preserved, and **Save-Help** would not work for remote module Help.</span></span>

<span data-ttu-id="aa996-114">In Windows Power Shell 4,0 wordt de eigenschap **HelpInfoUri** bewaard bij externe communicatie met Power shell, waardoor **Save-Help** kan worden gebruikt voor modules die op externe computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-114">In Windows PowerShell 4.0, the **HelpInfoUri** property is preserved over PowerShell remoting, which enables **Save-Help** to work for modules that are installed on remote computers.</span></span>
<span data-ttu-id="aa996-115">Het is ook mogelijk om een **PSModuleInfo** -object op te slaan op schijf of verwissel bare media door Export-Clixml uit te voeren op een computer die geen Internet toegang heeft, het object te importeren op een computer met Internet toegang en vervolgens **opslaan-Help** uit te voeren op het **PSModuleInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="aa996-115">It is also possible to save a **PSModuleInfo** object to disk or removable media by running Export-Clixml on a computer that does not have Internet access, import the object on a computer that does have Internet access, and then run **Save-Help** on the **PSModuleInfo** object.</span></span>
<span data-ttu-id="aa996-116">De opgeslagen Help kan worden getransporteerd naar de externe computer door gebruik te maken van Verwissel bare opslag media, zoals een USB-station.</span><span class="sxs-lookup"><span data-stu-id="aa996-116">The saved help can be transported to the remote computer by using removable storage media, such as a USB drive.</span></span>
<span data-ttu-id="aa996-117">De Help kan worden geïnstalleerd op de externe computer door **Update-Help** uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-117">The help can be installed on the remote computer by running **Update-Help**.</span></span>
<span data-ttu-id="aa996-118">Dit proces kan worden gebruikt om Help te installeren op computers die geen netwerk toegang hebben.</span><span class="sxs-lookup"><span data-stu-id="aa996-118">This process can be used to install help on computers that do not have any kind of network access.</span></span>

<span data-ttu-id="aa996-119">Als u opgeslagen Help-bestanden wilt installeren, voert u de Update-Help-cmdlet uit.</span><span class="sxs-lookup"><span data-stu-id="aa996-119">To install saved help files, run the Update-Help cmdlet.</span></span>
<span data-ttu-id="aa996-120">Voeg de para meter *SourcePath* toe om de map op te geven waarin u de Help-bestanden hebt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="aa996-120">Add its *SourcePath* parameter to specify the folder in which you saved the Help files.</span></span>

<span data-ttu-id="aa996-121">Zonder para meters wordt met de opdracht **opslaan-Help** de nieuwste Help gedownload voor alle modules in de sessie en voor modules die op de computer zijn geïnstalleerd op een locatie die wordt vermeld in de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="aa996-121">Without parameters, a **Save-Help** command downloads the newest help for all modules in the session and for modules that are installed on the computer in a location listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="aa996-122">Met deze actie worden modules die niet kunnen worden bijgewerkt zonder waarschuwing, overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="aa996-122">This action skips modules that do not support Updatable Help without warning.</span></span>

<span data-ttu-id="aa996-123">De cmdlet **Save-Help** controleert de versie van alle Help-bestanden in de doelmap.</span><span class="sxs-lookup"><span data-stu-id="aa996-123">The **Save-Help** cmdlet checks the version of any help files in the destination folder.</span></span>
<span data-ttu-id="aa996-124">Als nieuwere Help-bestanden beschikbaar zijn, downloadt deze cmdlet de nieuwste Help-bestanden van Internet en slaat deze vervolgens op in de map.</span><span class="sxs-lookup"><span data-stu-id="aa996-124">If newer help files are available, this cmdlet downloads the newest help files from the Internet, and then saves them in the folder.</span></span>
<span data-ttu-id="aa996-125">De cmdlet **Save-Help** werkt op dezelfde manier als de cmdlet Update-Help, behalve dat de gedownloade cab-bestanden (. cab) worden opgeslagen in plaats van de Help-bestanden uit de cabinetbestanden te extra heren en op de computer te installeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-125">The **Save-Help** cmdlet works just like the Update-Help cmdlet, except that it saves the downloaded cabinet (.cab) files, instead of extracting the help files from the cabinet files and installing them on the computer.</span></span>

<span data-ttu-id="aa996-126">De opgeslagen Help voor elke module bestaat uit één Help-informatie bestand (HelpInfo XML) en één CAB-bestand (CAB) voor de Help-bestanden elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="aa996-126">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span>
<span data-ttu-id="aa996-127">U hoeft de Help-bestanden niet uit het CAB-bestand uit te pakken.</span><span class="sxs-lookup"><span data-stu-id="aa996-127">You do not have to extract the help files from the cabinet file.</span></span>
<span data-ttu-id="aa996-128">De cmdlet **Update-Help** haalt de Help-bestanden op, valideert de XML voor beveiliging en installeert vervolgens de Help-bestanden en het Help-informatie bestand in een taalspecifieke submap van de module map.</span><span class="sxs-lookup"><span data-stu-id="aa996-128">The **Update-Help** cmdlet extracts the help files, validates the XML for safety, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>

<span data-ttu-id="aa996-129">Als u de Help-bestanden voor modules in de Power shell-installatiemap ($pshome \Modules) wilt opslaan, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-129">To save the help files for modules in the PowerShell installation folder ($pshome\Modules), start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="aa996-130">U moet lid zijn van de groep Administrators op de computer om de Help-bestanden voor deze modules te downloaden.</span><span class="sxs-lookup"><span data-stu-id="aa996-130">You must be a member of the Administrators group on the computer to download the help files for these modules.</span></span>

<span data-ttu-id="aa996-131">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aa996-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="aa996-132">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aa996-132">EXAMPLES</span></span>

### <span data-ttu-id="aa996-133">Voor beeld 1: de Help voor de DHCP-module opslaan</span><span class="sxs-lookup"><span data-stu-id="aa996-133">Example 1: Save the help for the DhcpServer module</span></span>

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module, save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

<span data-ttu-id="aa996-134">In dit voor beeld ziet u drie verschillende manieren om de Help- **informatie** voor de **DHCP** -module op te slaan vanaf een client computer met Internet verbinding, zonder dat u **de DHCP-module of** de server functie voor de lokale computer hoeft te installeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-134">This example shows three different ways to use **Save-Help** to save the help for the **DhcpServer** module from an Internet-connected client computer, without installing the **DhcpServer** module or the DHCP Server role on the local computer.</span></span>

### <span data-ttu-id="aa996-135">Voor beeld 2: Help installeren voor de DHCP-module</span><span class="sxs-lookup"><span data-stu-id="aa996-135">Example 2: Install help for the DhcpServer module</span></span>

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

<span data-ttu-id="aa996-136">In dit voor beeld ziet u hoe u Help kunt installeren die u in voor beeld 1 hebt opgeslagen voor de **DHCP** -module op een computer die geen toegang tot internet heeft.</span><span class="sxs-lookup"><span data-stu-id="aa996-136">This example shows how to install help that you saved in Example 1 for the **DhcpServer** module on a computer that does not have Internet access.</span></span>

### <span data-ttu-id="aa996-137">Voor beeld 3: Help voor alle modules opslaan</span><span class="sxs-lookup"><span data-stu-id="aa996-137">Example 3: Save help for all modules</span></span>

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

<span data-ttu-id="aa996-138">Met deze opdracht worden de nieuwste Help-bestanden gedownload voor alle modules in de UI-cultuur die is ingesteld voor Windows op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="aa996-138">This command downloads the newest help files for all modules in the UI culture set for Windows on the local computer.</span></span>
<span data-ttu-id="aa996-139">De Help-bestanden worden opgeslagen in de \\ \\ map Server01\Fileshare01.</span><span class="sxs-lookup"><span data-stu-id="aa996-139">It saves the help files in the \\\\Server01\Fileshare01 folder.</span></span>

### <span data-ttu-id="aa996-140">Voor beeld 4: Help voor een module op de computer opslaan</span><span class="sxs-lookup"><span data-stu-id="aa996-140">Example 4: Save help for a module on the computer</span></span>

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

<span data-ttu-id="aa996-141">Met deze opdracht worden de nieuwste Help-bestanden voor de module Server **Manager** gedownload en opgeslagen in de \\ \\ map Server01\Fileshare01.</span><span class="sxs-lookup"><span data-stu-id="aa996-141">This command downloads the newest help files for the **ServerManager** module, and then saves them in the \\\\Server01\Fileshare01 folder.</span></span>

<span data-ttu-id="aa996-142">Wanneer een module op de computer is geïnstalleerd, kunt u de module naam als de waarde van de *module* parameter typen, zelfs als de module niet in de huidige sessie is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-142">When a module is installed on the computer, you can type the module name as the value of the *Module* parameter, even if the module is not imported into the current session.</span></span>

<span data-ttu-id="aa996-143">De opdracht gebruikt de para meter *Credential* voor het opgeven van de referenties van een gebruiker die gemachtigd is om naar de bestands share te schrijven.</span><span class="sxs-lookup"><span data-stu-id="aa996-143">The command uses the *Credential* parameter to supply the credentials of a user who has permission to write to the file share.</span></span>

### <span data-ttu-id="aa996-144">Voor beeld 5: Help voor een module op een andere computer opslaan</span><span class="sxs-lookup"><span data-stu-id="aa996-144">Example 5: Save help for a module on a different computer</span></span>

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

<span data-ttu-id="aa996-145">Met deze opdrachten worden de nieuwste Help-bestanden voor de **CustomSQL** -module gedownload en opgeslagen in de \\ \\ map Server01\Fileshare01.</span><span class="sxs-lookup"><span data-stu-id="aa996-145">These commands download the newest help files for the **CustomSQL** module and save them in the \\\\Server01\Fileshare01 folder.</span></span>

<span data-ttu-id="aa996-146">Omdat de **CustomSQL** -module niet is geïnstalleerd op de computer, bevat de reeks een Invoke-Command opdracht waarmee het module object voor de CustomSQL-module van de Server02-computer wordt opgehaald en vervolgens het module-object wordt door sluizen naar de cmdlet **Save-Help** .</span><span class="sxs-lookup"><span data-stu-id="aa996-146">Because the **CustomSQL** module is not installed on the computer, the sequence includes an Invoke-Command command that gets the module object for the CustomSQL module from the Server02 computer and then pipes the module object to the **Save-Help** cmdlet.</span></span>

<span data-ttu-id="aa996-147">Als een module niet is geïnstalleerd op de computer, moet u voor de **Help** het module object gebruiken, dat informatie bevat over de locatie van de nieuwste Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="aa996-147">When a module is not installed on the computer, **Save-Help** needs the module object, which includes information about the location of the newest help files.</span></span>

### <span data-ttu-id="aa996-148">Voor beeld 6: Help voor een module in meerdere talen opslaan</span><span class="sxs-lookup"><span data-stu-id="aa996-148">Example 6: Save help for a module in multiple languages</span></span>

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

<span data-ttu-id="aa996-149">Met deze opdracht wordt de Help voor de Power shell-kern modules in vier verschillende GEBRUIKERSINTERFACE culturen opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="aa996-149">This command saves help for the PowerShell Core modules in four different UI cultures.</span></span>
<span data-ttu-id="aa996-150">De taal pakketten voor deze land instellingen hoeven niet te worden geïnstalleerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="aa996-150">The language packs for these locales do not have to be installed on the computer.</span></span>

<span data-ttu-id="aa996-151">**Save-Help** kan de Help-bestanden voor modules in verschillende gebruikersinterface culturen alleen downloaden wanneer de eigenaar van de module de vertaalde bestanden beschikbaar maakt op internet.</span><span class="sxs-lookup"><span data-stu-id="aa996-151">**Save-Help** can download help files for modules in different UI cultures only when the module owner makes the translated files available on the Internet.</span></span>

### <span data-ttu-id="aa996-152">Voor beeld 7: Help meer dan één keer per dag opslaan</span><span class="sxs-lookup"><span data-stu-id="aa996-152">Example 7: Save help more than one time each day</span></span>

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

<span data-ttu-id="aa996-153">Met deze opdracht wordt de Help-informatie opgeslagen voor alle modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-153">This command saves help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="aa996-154">De opdracht geeft de para meter *Force* om de regel te onderdrukken waarmee wordt voor komen dat de cmdlet **Save-Help** meer dan één keer in elke periode van 24 uur wordt gedownload.</span><span class="sxs-lookup"><span data-stu-id="aa996-154">The command specifies the *Force* parameter to override the rule that prevents the **Save-Help** cmdlet from downloading help more than once in each 24-hour period.</span></span>

<span data-ttu-id="aa996-155">De para meter *Force* overschrijft ook de beperking van 1 GB en omzeilt de versie controle.</span><span class="sxs-lookup"><span data-stu-id="aa996-155">The *Force* parameter also overrides the 1 GB restriction and circumvents version checking.</span></span>
<span data-ttu-id="aa996-156">Daarom kunt u bestanden downloaden, zelfs als de versie niet hoger is dan de versie in de doelmap.</span><span class="sxs-lookup"><span data-stu-id="aa996-156">Therefore, you can download files even if the version is not later than the version in the destination folder.</span></span>

<span data-ttu-id="aa996-157">De opdracht maakt gebruik van de cmdlet **Save-Help** om de Help-bestanden te downloaden en op te slaan in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="aa996-157">The command uses the **Save-Help** cmdlet to download and save the help files to the specified folder.</span></span>
<span data-ttu-id="aa996-158">De para meter *Force* is vereist wanneer u een opdracht voor **opslaan-Help** meer dan één keer per dag moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-158">The *Force* parameter is required when you have to run a **Save-Help** command more than one time each day.</span></span>

## <span data-ttu-id="aa996-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa996-159">PARAMETERS</span></span>

### <span data-ttu-id="aa996-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="aa996-160">-Credential</span></span>

<span data-ttu-id="aa996-161">Hiermee geeft u een gebruikers referentie op.</span><span class="sxs-lookup"><span data-stu-id="aa996-161">Specifies a user credential.</span></span> <span data-ttu-id="aa996-162">Met deze cmdlet wordt de opdracht uitgevoerd met behulp van referenties van een gebruiker die toegang heeft tot de bestandssysteem locatie die is opgegeven door de para meter **doelpad** .</span><span class="sxs-lookup"><span data-stu-id="aa996-162">This cmdlet runs the command by using credentials of a user who has permission to access the file system location specified by the **DestinationPath** parameter.</span></span> <span data-ttu-id="aa996-163">Deze para meter is alleen geldig wanneer de para meter **doelpad** of **LiteralPath** wordt gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="aa996-163">This parameter is valid only when the **DestinationPath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="aa996-164">Met deze para meter kunt u `Save-Help` opdrachten uitvoeren die gebruikmaken van de para meter **doelpad** op externe computers.</span><span class="sxs-lookup"><span data-stu-id="aa996-164">This parameter enables you to run `Save-Help` commands that use the **DestinationPath** parameter on remote computers.</span></span> <span data-ttu-id="aa996-165">Door expliciete referenties op te geven, kunt u de opdracht uitvoeren op een externe computer en toegang krijgen tot een bestands share op een derde computer zonder dat er een fout wordt geweigerd of als CredSSP-verificatie wordt gebruikt voor het delegeren van referenties.</span><span class="sxs-lookup"><span data-stu-id="aa996-165">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="aa996-166">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="aa996-166">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="aa996-167">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-167">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="aa996-168">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="aa996-168">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="aa996-169">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="aa996-169">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-170">-Doelpad</span><span class="sxs-lookup"><span data-stu-id="aa996-170">-DestinationPath</span></span>

<span data-ttu-id="aa996-171">Hiermee geeft u het pad op van de map waarin de Help-bestanden worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="aa996-171">Specifies the path of the folder in which the help files are saved.</span></span>
<span data-ttu-id="aa996-172">Geef geen bestands naam of bestands extensie op.</span><span class="sxs-lookup"><span data-stu-id="aa996-172">Do not specify a file name or file name extension.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-173">-Force</span><span class="sxs-lookup"><span data-stu-id="aa996-173">-Force</span></span>

<span data-ttu-id="aa996-174">Geeft aan dat deze cmdlet de beperking van eenmalige per dag niet volgt, de versie controle overs laat en bestanden downloadt die de limiet van 1 GB overschrijden.</span><span class="sxs-lookup"><span data-stu-id="aa996-174">Indicates that this cmdlet does not follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="aa996-175">Zonder deze para meter wordt slechts één opdracht voor **opslaan/Help** voor elke module toegestaan in elke periode van 24 uur. down loads zijn beperkt tot 1 GB aan niet-gecomprimeerde inhoud per module en Help-bestanden voor een module worden alleen geïnstalleerd wanneer ze nieuwer zijn dan de bestanden op de computer.</span><span class="sxs-lookup"><span data-stu-id="aa996-175">Without this parameter, only one **Save-Help** command for each module is permitted in each 24-hour period, downloads are limited to 1 GB of uncompressed content per module, and help files for a module are installed only when they are newer than the files on the computer.</span></span>

<span data-ttu-id="aa996-176">De limiet van één dag beveiligt de servers die als host fungeren voor de Help-bestanden en maken het voor u praktisch om een opdracht voor **opslaan-Help** toe te voegen aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="aa996-176">The once-per-day limit protects the servers that host the help files, and makes it practical for you to add a **Save-Help** command to your PowerShell profile.</span></span>

<span data-ttu-id="aa996-177">Als u de Help wilt opslaan voor een module in meerdere GEBRUIKERSINTERFACE culturen zonder de para meter *Force* , neemt u alle gebruikersinterface culturen op in dezelfde opdracht, zoals: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span><span class="sxs-lookup"><span data-stu-id="aa996-177">To save help for a module in multiple UI cultures without the *Force* parameter, include all UI cultures in the same command, such as: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-178">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="aa996-178">-FullyQualifiedModule</span></span>

<span data-ttu-id="aa996-179">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van ModuleSpecification-objecten.</span><span class="sxs-lookup"><span data-stu-id="aa996-179">Specifies modules with names that are specified in the form of ModuleSpecification objects.</span></span>
<span data-ttu-id="aa996-180">Dit wordt beschreven in de sectie opmerkingen van [ModuleSpecification constructor (hashtabel)](https://msdn.microsoft.com/library/jj136290) in de MSDN-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="aa996-180">This is described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="aa996-181">Bijvoorbeeld, de para meter *FullyQualifiedModule* accepteert een module naam die is opgegeven in de indeling @ {naam module = "naam module"; ModuleVersion = "version_number"} of @ {module naam = "module naam"; ModuleVersion = "version_number"; GUID = "GUID"}.</span><span class="sxs-lookup"><span data-stu-id="aa996-181">For example, the *FullyQualifiedModule* parameter accepts a module name that is specified in the format @{ModuleName = "modulename"; ModuleVersion = "version_number"} or @{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.</span></span>
<span data-ttu-id="aa996-182">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="aa996-182">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="aa996-183">U kunt de para meter *FullyQualifiedModule* niet opgeven in dezelfde opdracht als een *module* parameter.</span><span class="sxs-lookup"><span data-stu-id="aa996-183">You cannot specify the *FullyQualifiedModule* parameter in the same command as a *Module* parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-184">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aa996-184">-LiteralPath</span></span>

<span data-ttu-id="aa996-185">Hiermee geeft u een pad van de doelmap op.</span><span class="sxs-lookup"><span data-stu-id="aa996-185">Specifies a path of the destination folder.</span></span>
<span data-ttu-id="aa996-186">In tegens telling tot de waarde van de para meter *doelpad* wordt de waarde van de para meter *LiteralPath* exact gebruikt terwijl deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="aa996-186">Unlike the value of the *DestinationPath* parameter, the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="aa996-187">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="aa996-187">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="aa996-188">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="aa996-188">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="aa996-189">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="aa996-189">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-190">-Module</span><span class="sxs-lookup"><span data-stu-id="aa996-190">-Module</span></span>

<span data-ttu-id="aa996-191">Hiermee worden modules opgegeven waarvoor deze cmdlet Help kan downloaden.</span><span class="sxs-lookup"><span data-stu-id="aa996-191">Specifies modules for which this cmdlet downloads help.</span></span>
<span data-ttu-id="aa996-192">Voer een of meer module namen of naam Patters in een door komma's gescheiden lijst of in een bestand met één module naam op elke regel.</span><span class="sxs-lookup"><span data-stu-id="aa996-192">Enter one or more module names or name patters in a comma-separated list or in a file that has one module name on each line.</span></span>
<span data-ttu-id="aa996-193">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="aa996-193">Wildcard characters are permitted.</span></span>
<span data-ttu-id="aa996-194">U kunt module-objecten ook pipeen vanuit de Get-Module **-** cmdlet om op te slaan.</span><span class="sxs-lookup"><span data-stu-id="aa996-194">You can also pipe module objects from the Get-Module cmdlet to **Save-Help**.</span></span>

<span data-ttu-id="aa996-195">Standaard wordt de Help bij **opslaan Help** gedownload voor alle modules die ondersteuning bieden voor Help-informatie en die op de lokale computer zijn geïnstalleerd op een locatie die wordt vermeld in de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="aa996-195">By default, **Save-Help** downloads help for all modules that support Updatable Help and are installed on the local computer in a location listed in the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="aa996-196">Als u Help wilt opslaan voor modules die niet op de computer zijn geïnstalleerd, voert u een opdracht **Get-module** uit op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="aa996-196">To save help for modules that are not installed on the computer, run a **Get-Module** command on a remote computer.</span></span>
<span data-ttu-id="aa996-197">Pipet de resulterende module objecten vervolgens naar de cmdlet **Save-Help** of dien de module-objecten in als de waarde van de *module* -of *input object* -para meters.</span><span class="sxs-lookup"><span data-stu-id="aa996-197">Then pipe the resulting module objects to the **Save-Help** cmdlet or submit the module objects as the value of the *Module* or *InputObject* parameters.</span></span>

<span data-ttu-id="aa996-198">Als de module die u opgeeft op de computer is geïnstalleerd, kunt u de module naam of een module-object invoeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-198">If the module that you specify is installed on the computer, you can enter the module name or a module object.</span></span>
<span data-ttu-id="aa996-199">Als de module niet op de computer is geïnstalleerd, moet u een module object invoeren, zoals het resultaat van de cmdlet **Get-module** .</span><span class="sxs-lookup"><span data-stu-id="aa996-199">If the module is not installed on the computer, you must enter a module object, such as one returned by the **Get-Module** cmdlet.</span></span>

<span data-ttu-id="aa996-200">De *module* para meter van de cmdlet **Save-Help** accepteert niet het volledige pad van een module bestand of module manifest bestand.</span><span class="sxs-lookup"><span data-stu-id="aa996-200">The *Module* parameter of the **Save-Help** cmdlet does not accept the full path of a module file or module manifest file.</span></span>
<span data-ttu-id="aa996-201">Als u hulp nodig hebt bij een module die zich niet in een **PSModulePath** -locatie bevindt, importeert u de module in de huidige sessie voordat u de opdracht **Save-Help** uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aa996-201">To save help for a module that is not in a **PSModulePath** location, import the module into the current session before you run the **Save-Help** command.</span></span>

<span data-ttu-id="aa996-202">De waarde ' \* ' (alle) probeert de Help bij te werken voor alle modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-202">A value of "\*" (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="aa996-203">Dit omvat modules die geen ondersteuning bieden voor bijwerk bare Help.</span><span class="sxs-lookup"><span data-stu-id="aa996-203">This includes modules that do not support Updatable Help.</span></span>
<span data-ttu-id="aa996-204">Deze waarde kan fouten genereren wanneer de opdracht modules detecteert die geen ondersteuning bieden voor bijwerk bare Help.</span><span class="sxs-lookup"><span data-stu-id="aa996-204">This value might generate errors when the command encounters modules that do not support Updatable Help.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="aa996-205">-UICulture</span><span class="sxs-lookup"><span data-stu-id="aa996-205">-UICulture</span></span>

<span data-ttu-id="aa996-206">Hiermee geeft u de UI-cultuur waarden op waarvoor met deze cmdlet bijgewerkte Help-bestanden worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="aa996-206">Specifies UI culture values for which this cmdlet gets updated help files.</span></span>
<span data-ttu-id="aa996-207">Voer een of meer taal codes in, zoals es-ES, een variabele die cultuur objecten bevat of een opdracht die cultuur objecten, zoals een Get-Culture of Get-UICulture opdracht, ophalen.</span><span class="sxs-lookup"><span data-stu-id="aa996-207">Enter one or more language codes, such as es-ES, a variable that contains culture objects, or a command that gets culture objects, such as a Get-Culture or Get-UICulture command.</span></span>

<span data-ttu-id="aa996-208">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="aa996-208">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="aa996-209">Geef geen gedeeltelijke taal code op, zoals ' de '.</span><span class="sxs-lookup"><span data-stu-id="aa996-209">Do not specify a partial language code, such as "de".</span></span>

<span data-ttu-id="aa996-210">Standaard worden met de **Help-functie** voor het opslaan Help-bestanden in de UI-cultuur ingesteld voor Windows of de terugval cultuur.</span><span class="sxs-lookup"><span data-stu-id="aa996-210">By default, **Save-Help** gets help files in the UI culture set for Windows or its fallback culture.</span></span>
<span data-ttu-id="aa996-211">Als u de para meter *uiCulture* opgeeft, zoekt de Help alleen naar Help alleen voor de opgegeven UI **-** cultuur, niet in een terugval cultuur.</span><span class="sxs-lookup"><span data-stu-id="aa996-211">If you specify the *UICulture* parameter, **Save-Help** looks for help only for the specified UI culture, not in any fallback culture.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-212">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="aa996-212">-UseDefaultCredentials</span></span>

<span data-ttu-id="aa996-213">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd, met inbegrip van het downloaden van het web, met de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="aa996-213">Indicates that this cmdlet runs the command, including the web download, with the credentials of the current user.</span></span>
<span data-ttu-id="aa996-214">Standaard wordt de opdracht uitgevoerd zonder expliciete referenties.</span><span class="sxs-lookup"><span data-stu-id="aa996-214">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="aa996-215">Deze para meter is alleen effectief als de webdownload gebruikmaakt van NTLM-, Negotiate-of Kerberos-verificatie.</span><span class="sxs-lookup"><span data-stu-id="aa996-215">This parameter is effective only when the web download uses NTLM, negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa996-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa996-216">CommonParameters</span></span>

<span data-ttu-id="aa996-217">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa996-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa996-218">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa996-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa996-219">INVOER</span><span class="sxs-lookup"><span data-stu-id="aa996-219">INPUTS</span></span>

### <span data-ttu-id="aa996-220">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="aa996-220">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="aa996-221">U kunt een module-object vanuit de cmdlet **Get-module** door sluizen naar de *module* parameter van **Save-Help**.</span><span class="sxs-lookup"><span data-stu-id="aa996-221">You can pipe a module object from the **Get-Module** cmdlet to the *Module* parameter of **Save-Help**.</span></span>

## <span data-ttu-id="aa996-222">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aa996-222">OUTPUTS</span></span>

### <span data-ttu-id="aa996-223">Geen</span><span class="sxs-lookup"><span data-stu-id="aa996-223">None</span></span>

<span data-ttu-id="aa996-224">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-224">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aa996-225">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aa996-225">NOTES</span></span>

* <span data-ttu-id="aa996-226">Als u Help voor modules wilt opslaan in de map $pshome \Modules, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="aa996-226">To save help for modules in the $pshome\Modules folder, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="aa996-227">Alleen leden van de groep Administrators op de computer kunnen Help voor modules downloaden in de map $pshome \Modules.</span><span class="sxs-lookup"><span data-stu-id="aa996-227">Only members of the Administrators group on the computer can download help for modules in the $pshome\Modules folder.</span></span>
* <span data-ttu-id="aa996-228">De opgeslagen Help voor elke module bestaat uit één Help-informatie bestand (HelpInfo XML) en één CAB-bestand (CAB) voor de Help-bestanden elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="aa996-228">The saved help for each module consists of one help information (HelpInfo XML) file and one cabinet (.cab) file for the help files each UI culture.</span></span> <span data-ttu-id="aa996-229">U hoeft de Help-bestanden niet uit het CAB-bestand uit te pakken.</span><span class="sxs-lookup"><span data-stu-id="aa996-229">You do not have to extract the help files from the cabinet file.</span></span> <span data-ttu-id="aa996-230">De cmdlet Update-Help extraheert de Help-bestanden, valideert de XML en installeert vervolgens de Help-bestanden en het Help-informatie bestand in een taalspecifieke submap van de module map.</span><span class="sxs-lookup"><span data-stu-id="aa996-230">The Update-Help cmdlet extracts the help files, validates the XML, and then installs the help files and the help information file in a language-specific subfolder of the module folder.</span></span>
* <span data-ttu-id="aa996-231">De cmdlet **Save-Help** kan Help opslaan voor modules die niet op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-231">The **Save-Help** cmdlet can save help for modules that are not installed on the computer.</span></span> <span data-ttu-id="aa996-232">Omdat Help-bestanden echter worden geïnstalleerd in de map module, kan de cmdlet **Update-Help** alleen een bijgewerkt Help-bestand installeren voor modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="aa996-232">However, because help files are installed in the module folder, the **Update-Help** cmdlet can install updated help file only for modules that are installed on the computer.</span></span>
* <span data-ttu-id="aa996-233">Als **Save-Help** geen bijgewerkte Help-bestanden voor een module kan vinden of als u geen bijgewerkte Help-bestanden kunt vinden in de opgegeven taal, wordt deze op de achtergrond voortgezet zonder dat er een fout bericht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aa996-233">If **Save-Help** cannot find updated help files for a module, or cannot find updated help files in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="aa996-234">Geef de para meter *uitgebreid* op om te zien welke bestanden zijn opgeslagen met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="aa996-234">To see which files were saved by the command, specify the *Verbose* parameter.</span></span>
* <span data-ttu-id="aa996-235">Modules zijn de kleinste eenheid van Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="aa996-235">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="aa996-236">U kunt geen Help-informatie voor een bepaalde cmdlet opslaan, alleen voor alle cmdlets in de module.</span><span class="sxs-lookup"><span data-stu-id="aa996-236">You cannot save help for a particular cmdlet, only for all cmdlets in module.</span></span> <span data-ttu-id="aa996-237">Als u de module wilt vinden die een bepaalde cmdlet bevat, gebruikt u **de eigenschap PropertyName** in combi natie met de cmdlet Get-Command, bijvoorbeeld `(Get-Command \<cmdlet-name\>).ModuleName`</span><span class="sxs-lookup"><span data-stu-id="aa996-237">To find the module that contains a particular cmdlet, use the **ModuleName** property together with the Get-Command cmdlet, for example, `(Get-Command \<cmdlet-name\>).ModuleName`</span></span>
* <span data-ttu-id="aa996-238">**Save-Help** ondersteunt alle modules en de Power shell core-modules. Andere modules worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aa996-238">**Save-Help** supports all modules and the PowerShell Core snap-ins. It does not support any other snap-ins.</span></span>
* <span data-ttu-id="aa996-239">De cmdlets **Update Help** en **Save-Help** gebruiken de volgende poorten om Help-bestanden te downloaden: poort 80 voor http en poort 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aa996-239">The **Update-Help** and **Save-Help** cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>
* <span data-ttu-id="aa996-240">De cmdlets **Update Help** en **Save-Help** worden niet ondersteund op Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="aa996-240">The **Update-Help** and **Save-Help** cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="aa996-241">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aa996-241">RELATED LINKS</span></span>

[<span data-ttu-id="aa996-242">Get-Help</span><span class="sxs-lookup"><span data-stu-id="aa996-242">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="aa996-243">Get-module</span><span class="sxs-lookup"><span data-stu-id="aa996-243">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="aa996-244">Update-Help</span><span class="sxs-lookup"><span data-stu-id="aa996-244">Update-Help</span></span>](Update-Help.md)
