---
title: Een Power shell-module installeren | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a4e9ac2884d0b300b5c1ad8b6156525438a1650
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784857"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="d0d99-102">Een PowerShell-module installeren</span><span class="sxs-lookup"><span data-stu-id="d0d99-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="d0d99-103">Nadat u de Power shell-module hebt gemaakt, wilt u waarschijnlijk de module op een systeem installeren, zodat u of anderen deze kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d0d99-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="d0d99-104">Over het algemeen is dit het kopiëren van de module bestanden (IE, de. psm1 of de binaire assembly, het module manifest en eventuele andere gekoppelde bestanden) naar een map op die computer.</span><span class="sxs-lookup"><span data-stu-id="d0d99-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="d0d99-105">Voor een zeer klein project is dit mogelijk zo eenvoudig als het kopiëren en plakken van de bestanden met Windows Verkenner op één externe computer. voor grotere oplossingen kunt u echter een geavanceerder installatie proces gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d0d99-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="d0d99-106">Ongeacht hoe u uw module op het systeem ophaalt, kan Power shell een aantal technieken gebruiken waarmee gebruikers uw modules kunnen vinden en gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d0d99-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="d0d99-107">Het belangrijkste probleem voor de installatie is daarom ervoor te zorgen dat Power shell uw module kan vinden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="d0d99-108">Zie [een Power shell-module importeren](./importing-a-powershell-module.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d0d99-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="d0d99-109">Regels voor het installeren van modules</span><span class="sxs-lookup"><span data-stu-id="d0d99-109">Rules for Installing Modules</span></span>

<span data-ttu-id="d0d99-110">De volgende informatie is van toepassing op alle modules, waaronder modules die u voor eigen gebruik maakt, modules die u van andere partijen krijgt en modules die u naar anderen distribueert.</span><span class="sxs-lookup"><span data-stu-id="d0d99-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="d0d99-111">Modules installeren in PSModulePath</span><span class="sxs-lookup"><span data-stu-id="d0d99-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="d0d99-112">Als dat mogelijk is, installeert u alle modules in een pad dat wordt weer gegeven in de omgevings variabele **PSModulePath** of voegt u het pad van de module toe aan de waarde van de **PSModulePath** -omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="d0d99-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="d0d99-113">De omgevings variabele **PSModulePath** ($env:P smodulepath) bevat de locaties van Windows Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="d0d99-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="d0d99-114">-Cmdlets zijn afhankelijk van de waarde van deze omgevings variabele om modules te vinden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="d0d99-115">De waarde van de omgevings variabele **PSModulePath** bevat standaard de volgende systeem-en gebruikers module mappen, maar u kunt de waarde toevoegen en bewerken.</span><span class="sxs-lookup"><span data-stu-id="d0d99-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="d0d99-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="d0d99-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="d0d99-117">Deze locatie is gereserveerd voor modules die worden geleverd met Windows.</span><span class="sxs-lookup"><span data-stu-id="d0d99-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="d0d99-118">Installeer geen modules op deze locatie.</span><span class="sxs-lookup"><span data-stu-id="d0d99-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="d0d99-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="d0d99-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="d0d99-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="d0d99-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="d0d99-121">Als u de waarde van de omgevings variabele **PSModulePath** wilt ophalen, gebruikt u een van de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d0d99-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="d0d99-122">Als u een pad naar de module wilt toevoegen aan de waarde van de waarde van de omgevings variabele **PSModulePath** , gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="d0d99-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="d0d99-123">Deze indeling maakt gebruik van de methode **SetEnvironmentVariable** van de klasse **System. Environment** om een sessie-onafhankelijke wijziging aan te brengen in de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="d0d99-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="d0d99-124">Zodra u het pad naar **PSModulePath**hebt toegevoegd, moet u een omgevings bericht over de wijziging uitzenden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="d0d99-125">Door de wijziging uit te zenden, kunnen andere toepassingen, zoals de shell, de wijziging ophalen.</span><span class="sxs-lookup"><span data-stu-id="d0d99-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="d0d99-126">Als u de wijziging wilt door sturen, laat u uw product installatie code een **WM_SETTINGCHANGE** -bericht verzenden `lParam` dat is ingesteld op de teken reeks omgeving.</span><span class="sxs-lookup"><span data-stu-id="d0d99-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="d0d99-127">Zorg ervoor dat u het bericht verzendt nadat de module-installatie code het **PSModulePath**heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="d0d99-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="d0d99-128">De juiste naam voor de module directory gebruiken</span><span class="sxs-lookup"><span data-stu-id="d0d99-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="d0d99-129">Een goed opgemaakte module is een module die is opgeslagen in een map met dezelfde naam als de basis naam van ten minste één bestand in de module directory.</span><span class="sxs-lookup"><span data-stu-id="d0d99-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="d0d99-130">Als een module niet goed gevormd is, wordt deze niet door Windows Power shell herkend als een module.</span><span class="sxs-lookup"><span data-stu-id="d0d99-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="d0d99-131">De ' basis naam ' van een bestand is de naam zonder de bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="d0d99-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="d0d99-132">In een goed opgemaakte module moet de naam van de map die de module bestanden bevat, overeenkomen met de basis naam van ten minste één bestand in de module.</span><span class="sxs-lookup"><span data-stu-id="d0d99-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="d0d99-133">In de voor beeld-module Fabrikam is de map die de module bestanden bevat de naam ' fabrikam ' en ten minste één bestand de basis naam ' fabrikam ' heeft.</span><span class="sxs-lookup"><span data-stu-id="d0d99-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="d0d99-134">In dit geval hebben zowel Fabrikam.psd1 als Fabrikam.dll de basis naam ' fabrikam '.</span><span class="sxs-lookup"><span data-stu-id="d0d99-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="d0d99-135">Effect van onjuiste installatie</span><span class="sxs-lookup"><span data-stu-id="d0d99-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="d0d99-136">Als de module niet de juiste indeling heeft en de locatie ervan niet is opgenomen in de waarde van de omgevings variabele **PSModulePath** , werken de basis detectie functies van Windows Power shell, zoals de volgende, niet.</span><span class="sxs-lookup"><span data-stu-id="d0d99-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="d0d99-137">Met de functie voor het automatisch laden van de module kan de module niet automatisch worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="d0d99-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="d0d99-138">De- `ListAvailable` para meter van de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) kan de module niet vinden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="d0d99-139">De module voor [importeren-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) kan niet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="d0d99-140">Als u de module wilt importeren, moet u het volledige pad naar het hoofd module bestand of het manifest bestand van de module opgeven.</span><span class="sxs-lookup"><span data-stu-id="d0d99-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="d0d99-141">Aanvullende functies, zoals de volgende, werken alleen als de module in de sessie wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="d0d99-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="d0d99-142">In goed opgemaakte modules in de omgevings variabele **PSModulePath** werken deze functies zelfs wanneer de module niet in de sessie wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="d0d99-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="d0d99-143">De cmdlet [Get-opdracht](/powershell/module/Microsoft.PowerShell.Core/Get-Command) kan geen opdrachten vinden in de module.</span><span class="sxs-lookup"><span data-stu-id="d0d99-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="d0d99-144">U kunt de Help- [cmdlets](/powershell/module/Microsoft.PowerShell.Core/Save-Help) [Update Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en Help-informatie voor de module niet bijwerken of opslaan.</span><span class="sxs-lookup"><span data-stu-id="d0d99-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="d0d99-145">Met de cmdlet [show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) kunnen de opdrachten in de module niet worden gevonden en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d0d99-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="d0d99-146">De opdrachten in de module ontbreken `Show-Command` in het venster in Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d0d99-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="d0d99-147">Waar modules worden geïnstalleerd?</span><span class="sxs-lookup"><span data-stu-id="d0d99-147">Where to Install Modules</span></span>

<span data-ttu-id="d0d99-148">In deze sectie wordt uitgelegd waar in het bestands systeem Windows Power shell-modules moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d0d99-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="d0d99-149">De locatie is afhankelijk van de manier waarop de module wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d0d99-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="d0d99-150">Modules voor een specifieke gebruiker installeren</span><span class="sxs-lookup"><span data-stu-id="d0d99-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="d0d99-151">Als u uw eigen module maakt of een module van een andere partij krijgt, zoals een Windows Power shell-community-website, en u wilt dat de module alleen beschikbaar is voor uw gebruikers account, installeert u de module in uw map met gebruikersspecifieke modules.</span><span class="sxs-lookup"><span data-stu-id="d0d99-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="d0d99-152">De map met gebruikersspecifieke modules wordt standaard toegevoegd aan de waarde van de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="d0d99-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="d0d99-153">Modules voor alle gebruikers in programma bestanden installeren</span><span class="sxs-lookup"><span data-stu-id="d0d99-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="d0d99-154">Als u wilt dat een module beschikbaar is voor alle gebruikers accounts op de computer, installeert u de module in de locatie van de programma bestanden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="d0d99-155">De locatie van de programma bestanden wordt standaard toegevoegd aan de waarde van de omgevings variabele PSModulePath in Windows Power Shell 4,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d0d99-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="d0d99-156">Voor eerdere versies van Windows Power shell kunt u de locatie van de programma bestanden ((%ProgramFiles%\WindowsPowerShell\Modules) hand matig maken en dit pad toevoegen aan de omgevings variabele PSModulePath, zoals hierboven wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="d0d99-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="d0d99-157">Modules in een productsitemap installeren</span><span class="sxs-lookup"><span data-stu-id="d0d99-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="d0d99-158">Als u de module naar andere partijen distribueert, gebruikt u de standaard locatie voor programma bestanden die hierboven wordt beschreven, of maakt u uw eigen bedrijfsspecifieke of productspecifieke submap van de map% Program Files%.</span><span class="sxs-lookup"><span data-stu-id="d0d99-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="d0d99-159">Bijvoorbeeld: fabrikam-technologieën, een fictief bedrijf, verzendt een Windows Power shell-module voor hun fabrikam Manager-product.</span><span class="sxs-lookup"><span data-stu-id="d0d99-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="d0d99-160">Het installatie programma van de module maakt een subdirectory modules in de submap van het fabrikam Manager-product.</span><span class="sxs-lookup"><span data-stu-id="d0d99-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="d0d99-161">Voor het inschakelen van de detectie functies van de Windows Power shell-module om de module fabrikam te vinden, wordt in het installatie programma van de module voor Fabrikam de modules-locatie toegevoegd aan de waarde van de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="d0d99-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="d0d99-162">Modules worden geïnstalleerd in de map common files</span><span class="sxs-lookup"><span data-stu-id="d0d99-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="d0d99-163">Als een module door meerdere onderdelen van een product of meerdere versies van een product wordt gebruikt, installeert u de module in een module-specifieke submap van de map%ProgramFiles%\Common Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="d0d99-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="d0d99-164">In het volgende voor beeld wordt de module fabrikam geïnstalleerd in een submap van Fabrikam van de `%ProgramFiles%\Common Files\Modules` submap.</span><span class="sxs-lookup"><span data-stu-id="d0d99-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="d0d99-165">Elke module bevindt zich in een eigen submap in de submap modules.</span><span class="sxs-lookup"><span data-stu-id="d0d99-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="d0d99-166">Het installatie programma zorgt er vervolgens voor dat de waarde van de omgevings variabele **PSModulePath** het pad van de submap common files modules bevat.</span><span class="sxs-lookup"><span data-stu-id="d0d99-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="d0d99-167">Meerdere versies van een module installeren</span><span class="sxs-lookup"><span data-stu-id="d0d99-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="d0d99-168">Als u meerdere versies van dezelfde module wilt installeren, gebruikt u de volgende procedure.</span><span class="sxs-lookup"><span data-stu-id="d0d99-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="d0d99-169">Maak een map voor elke versie van de module.</span><span class="sxs-lookup"><span data-stu-id="d0d99-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="d0d99-170">Het versie nummer in de mapnaam toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d0d99-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="d0d99-171">Maak een module manifest voor elke versie van de module.</span><span class="sxs-lookup"><span data-stu-id="d0d99-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="d0d99-172">Voer in de waarde van de sleutel **ModuleVersion** in het manifest het module versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="d0d99-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="d0d99-173">Sla het manifest bestand (. psd1) op in de versie-specifieke directory voor de module.</span><span class="sxs-lookup"><span data-stu-id="d0d99-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="d0d99-174">Voeg het pad van de module-basismap toe aan de waarde van de omgevings variabele **PSModulePath** , zoals wordt weer gegeven in de volgende voor beelden.</span><span class="sxs-lookup"><span data-stu-id="d0d99-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="d0d99-175">Als u een bepaalde versie van de module wilt importeren, kan de eind gebruiker gebruikmaken `MinimumVersion` `RequiredVersion` van de para meters of van de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="d0d99-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="d0d99-176">Bijvoorbeeld, als de module fabrikam beschikbaar is in versie 8,0 en 9,0, kan de directory structuur van de module Fabrikam er als volgt uitzien.</span><span class="sxs-lookup"><span data-stu-id="d0d99-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="d0d99-177">Het installatie programma voegt beide module paden toe aan de waarde van de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="d0d99-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="d0d99-178">Wanneer deze stappen zijn voltooid, haalt de para meter **ListAvailable** van de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) beide fabrikam-modules op.</span><span class="sxs-lookup"><span data-stu-id="d0d99-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="d0d99-179">Als u een bepaalde module wilt importeren, gebruikt u de `MinimumVersion` `RequiredVersion` para meters van de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="d0d99-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="d0d99-180">Als beide modules in dezelfde sessie worden geïmporteerd en de modules cmdlets met dezelfde namen bevatten, zijn de cmdlets die het laatst zijn geïmporteerd in de sessie effectief.</span><span class="sxs-lookup"><span data-stu-id="d0d99-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="d0d99-181">Conflicten bij het afhandelen van namen van opdrachten</span><span class="sxs-lookup"><span data-stu-id="d0d99-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="d0d99-182">Conflicten met de naam van de opdracht kunnen zich voordoen wanneer de opdrachten die een module exporteert dezelfde naam hebben als opdrachten in de sessie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d0d99-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="d0d99-183">Wanneer een sessie twee opdrachten met dezelfde naam bevat, voert Windows Power shell het type opdracht uit dat voor rang heeft.</span><span class="sxs-lookup"><span data-stu-id="d0d99-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="d0d99-184">Wanneer een sessie twee opdrachten bevat die dezelfde naam en hetzelfde type hebben, voert Windows Power shell de opdracht uit die het laatst aan de sessie is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d0d99-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="d0d99-185">Als u een opdracht wilt uitvoeren die niet standaard wordt uitgevoerd, kunnen gebruikers de naam van de opdracht kwalificeren met de module naam.</span><span class="sxs-lookup"><span data-stu-id="d0d99-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="d0d99-186">Als de sessie bijvoorbeeld een `Get-Date` functie en de `Get-Date` cmdlet bevat, wordt de functie standaard uitgevoerd door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="d0d99-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="d0d99-187">Als u de cmdlet wilt uitvoeren, moet u voor de opdracht de module naam gebruiken, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d0d99-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="d0d99-188">Om conflicten met de naam te voor komen, kunnen module auteurs de sleutel **DefaultCommandPrefix** in het module manifest gebruiken om een zelfstandig naam woord voor voegsel op te geven voor alle opdrachten die vanuit de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="d0d99-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="d0d99-189">Gebruikers kunnen de para meter **prefix** van de `Import-Module` cmdlet gebruiken om een alternatief voor voegsel te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d0d99-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="d0d99-190">De waarde van de para meter **prefix krijgt voor** rang op de waarde van de sleutel **DefaultCommandPrefix** .</span><span class="sxs-lookup"><span data-stu-id="d0d99-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0d99-191">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d0d99-191">See Also</span></span>

[<span data-ttu-id="d0d99-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="d0d99-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="d0d99-193">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="d0d99-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
