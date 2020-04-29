---
title: Hulp voor het schrijven van Power shell-modules
ms.date: 04/10/2020
ms.openlocfilehash: 496b7e6cadff4d2db15b6452e9d38efcdf1739ec
ms.sourcegitcommit: 8f55c0157280afa4598fe385a706faf330e723a9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219656"
---
# <a name="writing-help-for-powershell-modules"></a><span data-ttu-id="6344d-102">Hulp voor het schrijven van Power shell-modules</span><span class="sxs-lookup"><span data-stu-id="6344d-102">Writing Help for PowerShell Modules</span></span>

<span data-ttu-id="6344d-103">Power shell-modules kunnen Help-onderwerpen bevatten over de module en over de module leden, zoals cmdlets, providers, functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="6344d-103">PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="6344d-104">De `Get-Help` cmdlet geeft de Help-onderwerpen van de module weer in dezelfde indeling als de Help-informatie voor andere Power shell- `Get-Help` items en gebruikers gebruiken standaard opdrachten om de Help-onderwerpen te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="6344d-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="6344d-105">In dit document vindt u informatie over de indeling en de juiste plaatsing van de Help-onderwerpen over modules en suggesties voor richt lijnen voor de Help-inhoud van de module.</span><span class="sxs-lookup"><span data-stu-id="6344d-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="6344d-106">Typen module Help</span><span class="sxs-lookup"><span data-stu-id="6344d-106">Types of Module Help</span></span>

<span data-ttu-id="6344d-107">Een module kan de volgende soorten Help bevatten.</span><span class="sxs-lookup"><span data-stu-id="6344d-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="6344d-108">**Help voor cmdlets**.</span><span class="sxs-lookup"><span data-stu-id="6344d-108">**Cmdlet Help**.</span></span> <span data-ttu-id="6344d-109">De Help-onderwerpen waarin cmdlets in een module worden beschreven, zijn XML-bestanden die gebruikmaken van het opdracht Help-schema</span><span class="sxs-lookup"><span data-stu-id="6344d-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="6344d-110">**Help**voor de provider.</span><span class="sxs-lookup"><span data-stu-id="6344d-110">**Provider Help**.</span></span> <span data-ttu-id="6344d-111">De Help-onderwerpen waarin providers in een module worden beschreven, zijn XML-bestanden die gebruikmaken van het Help-schema van de provider.</span><span class="sxs-lookup"><span data-stu-id="6344d-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="6344d-112">**Functie Help**.</span><span class="sxs-lookup"><span data-stu-id="6344d-112">**Function Help**.</span></span> <span data-ttu-id="6344d-113">De Help-onderwerpen die functies in een module beschrijven, kunnen XML-bestanden zijn die gebruikmaken van de opdracht Help-schema of de Help-onderwerpen op basis van opmerkingen in de functie, of het script of de script module</span><span class="sxs-lookup"><span data-stu-id="6344d-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="6344d-114">**Help voor scripts**.</span><span class="sxs-lookup"><span data-stu-id="6344d-114">**Script Help**.</span></span> <span data-ttu-id="6344d-115">De Help-onderwerpen waarin scripts in een module worden beschreven, kunnen XML-bestanden zijn die gebruikmaken van de opdracht Help-schema of de Help-onderwerpen op basis van opmerkingen in de script-of script module.</span><span class="sxs-lookup"><span data-stu-id="6344d-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="6344d-116">**Conceptuele informatie ("about")**.</span><span class="sxs-lookup"><span data-stu-id="6344d-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="6344d-117">U kunt een conceptueel ("about") Help-onderwerp gebruiken om de module en de bijbehorende leden te beschrijven en te uitleggen hoe de leden kunnen worden gebruikt om taken uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6344d-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span>
  <span data-ttu-id="6344d-118">Conceptuele Help-onderwerpen zijn tekst bestanden met Unicode-code ring (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="6344d-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="6344d-119">De bestands naam moet de `about_<name>.help.txt` indeling gebruiken, zoals. `about_MyModule.help.txt`</span><span class="sxs-lookup"><span data-stu-id="6344d-119">The file name must use the `about_<name>.help.txt` format, such as `about_MyModule.help.txt`.</span></span> <span data-ttu-id="6344d-120">Power shell bevat standaard meer dan 100 van de volgende conceptuele informatie over Help-onderwerpen en ze zijn ingedeeld zoals in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="6344d-120">By default, PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

<span data-ttu-id="6344d-121">Alle schema bestanden kunnen worden gevonden in de `$PSHOME\Schemas\PSMaml` map.</span><span class="sxs-lookup"><span data-stu-id="6344d-121">All of the schema files can be found in the `$PSHOME\Schemas\PSMaml` folder.</span></span>

## <a name="placement-of-module-help"></a><span data-ttu-id="6344d-122">Plaatsing van module-Help</span><span class="sxs-lookup"><span data-stu-id="6344d-122">Placement of Module Help</span></span>

<span data-ttu-id="6344d-123">De `Get-Help` cmdlet zoekt naar de Help-onderwerpen van module bestanden in taalspecifieke submappen van de module directory.</span><span class="sxs-lookup"><span data-stu-id="6344d-123">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="6344d-124">In het volgende diagram van een mapstructuur ziet u bijvoorbeeld de locatie van de Help-onderwerpen voor de module SampleModule.</span><span class="sxs-lookup"><span data-stu-id="6344d-124">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="6344d-125">In het voor beeld vertegenwoordigt `<ModulePath>` de tijdelijke aanduiding een van de paden in `PSModulePath` de omgevings variabele, `$HOME\Documents\Modules`zoals `$PSHOME\Modules`,, of een aangepast pad dat door de gebruiker is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6344d-125">In the example, the `<ModulePath>` placeholder represents one of the paths in the `PSModulePath` environment variable, such as `$HOME\Documents\Modules`, `$PSHOME\Modules`, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="6344d-126">Help voor module ophalen</span><span class="sxs-lookup"><span data-stu-id="6344d-126">Getting Module Help</span></span>

<span data-ttu-id="6344d-127">Wanneer een gebruiker een module in een sessie importeert, worden de Help-onderwerpen voor die module in de-sessie samen met de module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6344d-127">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="6344d-128">U kunt de bestand met Help-onderwerpen weer geven in de waarde van de sleutel file list in het module manifest, maar Help-onderwerpen `Export-ModuleMember` worden niet beïnvloed door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6344d-128">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="6344d-129">U kunt Help-onderwerpen over modules in verschillende talen opgeven.</span><span class="sxs-lookup"><span data-stu-id="6344d-129">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="6344d-130">Met `Get-Help` de cmdlet worden automatisch Help-onderwerpen over modules weer gegeven in de taal die is opgegeven voor de huidige gebruiker in het onderdeel land instellingen van het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="6344d-130">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="6344d-131">In Windows Vista en latere versies van Windows zoekt `Get-Help` u naar de Help-onderwerpen in taalspecifieke submappen van de module directory in overeenstemming met de taal vereisten voor het uitvoeren van Windows.</span><span class="sxs-lookup"><span data-stu-id="6344d-131">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="6344d-132">Vanaf Power Shell 3,0 voert een `Get-Help` opdracht uit voor een cmdlet of functie activeert automatisch het importeren van de module.</span><span class="sxs-lookup"><span data-stu-id="6344d-132">Beginning in PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="6344d-133">Met `Get-Help` de cmdlet wordt direct de inhoud van de Help-onderwerpen in de module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6344d-133">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="6344d-134">Als de module geen Help-onderwerpen bevat en er geen Help-onderwerpen zijn voor de opdrachten in de module op de computer van de `Get-Help` gebruiker, wordt automatisch gegenereerde Help weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6344d-134">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="6344d-135">De automatisch gegenereerde Help omvat de opdracht syntaxis, para meters en invoer-en uitvoer typen, maar bevat geen beschrijvingen.</span><span class="sxs-lookup"><span data-stu-id="6344d-135">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="6344d-136">De automatisch gegenereerde Help bevat tekst waarmee de gebruiker wordt gevraagd om de `Update-Help` cmdlet te gebruiken voor het downloaden van de Help voor de opdracht van Internet of een bestands share.</span><span class="sxs-lookup"><span data-stu-id="6344d-136">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="6344d-137">U wordt ook aangeraden de **online** -para `Get-Help` meter van de cmdlet te gebruiken om de online versie van het Help-onderwerp op te halen.</span><span class="sxs-lookup"><span data-stu-id="6344d-137">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="6344d-138">Ondersteunende help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="6344d-138">Supporting Updatable Help</span></span>

<span data-ttu-id="6344d-139">Gebruikers van Power Shell 3,0 en latere versies van Power shell kunnen bijgewerkte Help-bestanden downloaden en installeren voor een module van Internet of van een lokale bestands share.</span><span class="sxs-lookup"><span data-stu-id="6344d-139">Users of PowerShell 3.0 and later versions of PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="6344d-140">De `Update-Help` cmdlets en `Save-Help` verbergen de beheer gegevens van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6344d-140">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="6344d-141">Gebruikers voeren de `Update-Help` cmdlet uit en gebruiken vervolgens `Get-Help` de cmdlet om de nieuwste Help-bestanden voor de module te lezen in de Power shell-opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="6344d-141">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the PowerShell command prompt.</span></span>
<span data-ttu-id="6344d-142">Gebruikers hoeven Windows of Power shell niet opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="6344d-142">Users do not need to restart Windows or PowerShell.</span></span>

<span data-ttu-id="6344d-143">Gebruikers achter firewalls en verbindingen zonder Internet toegang kunnen ook gebruikmaken van de Bewerk bare Help.</span><span class="sxs-lookup"><span data-stu-id="6344d-143">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span>
<span data-ttu-id="6344d-144">Beheerders met Internet toegang gebruiken de `Save-Help` cmdlet om de nieuwste Help-bestanden te downloaden en te installeren op een bestands share.</span><span class="sxs-lookup"><span data-stu-id="6344d-144">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="6344d-145">Vervolgens gebruiken gebruikers de para meter **Path** van de `Update-Help` cmdlet om de nieuwste Help-bestanden van de bestands share op te halen.</span><span class="sxs-lookup"><span data-stu-id="6344d-145">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="6344d-146">Module auteurs kunnen Help-bestanden in de module toevoegen en de Help-informatie gebruiken voor het bijwerken van de Help-bestanden, of de Help-bestanden van de module weglaten en de Bewerk bare Help gebruiken om ze te installeren en bij te werken.</span><span class="sxs-lookup"><span data-stu-id="6344d-146">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="6344d-147">Zie [ondersteunende Help](./supporting-updatable-help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="6344d-147">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="6344d-148">Ondersteunende online help</span><span class="sxs-lookup"><span data-stu-id="6344d-148">Supporting Online Help</span></span>

<span data-ttu-id="6344d-149">Gebruikers die geen bijgewerkte Help-bestanden op hun computers kunnen of installeren, zijn vaak afhankelijk van de online versie van de Help-onderwerpen over modules.</span><span class="sxs-lookup"><span data-stu-id="6344d-149">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="6344d-150">Met **Online** de para meter online `Get-Help` van de cmdlet opent u de online versie van een cmdlet of geavanceerde functie Help onderwerp voor de gebruiker in de standaard browser van Internet.</span><span class="sxs-lookup"><span data-stu-id="6344d-150">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="6344d-151">De `Get-Help` cmdlet gebruikt de waarde van de eigenschap **HelpUri** van de cmdlet of functie om de online versie van het Help-onderwerp te vinden.</span><span class="sxs-lookup"><span data-stu-id="6344d-151">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="6344d-152">Vanaf Power Shell 3,0 kunt u gebruikers helpen bij het vinden van de online versie van cmdlet-en Function Help-onderwerpen door het kenmerk HelpUri te definiëren voor de klasse cmdlet of de eigenschap **HelpUri** van het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="6344d-152">Beginning in PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="6344d-153">De waarde van het kenmerk is de waarde van de eigenschap **HelpUri** van de cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="6344d-153">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="6344d-154">Zie ondersteuning voor online- [Help](./supporting-online-help.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6344d-154">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6344d-155">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6344d-155">See Also</span></span>

[<span data-ttu-id="6344d-156">Een Power shell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="6344d-156">Writing a PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="6344d-157">Ondersteunende help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="6344d-157">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="6344d-158">Ondersteunende online help</span><span class="sxs-lookup"><span data-stu-id="6344d-158">Supporting Online Help</span></span>](./supporting-online-help.md)
