---
title: Schrijfhulp voor Windows PowerShell-Modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845456"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="49110-102">Help voor Windows PowerShell-modules schrijven</span><span class="sxs-lookup"><span data-stu-id="49110-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="49110-103">Windows PowerShell-modules kunnen Help-onderwerpen over de module en de leden van de module, zoals cmdlets, providers, functies en scripts bevatten.</span><span class="sxs-lookup"><span data-stu-id="49110-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="49110-104">De `Get-Help` cmdlet wordt de module Help-onderwerpen in dezelfde indeling als deze geeft Help weer voor andere Windows PowerShell-items en gebruikers standaard gebruiken `Get-Help` opdrachten voor het ophalen van de Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="49110-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="49110-105">Dit document wordt uitgelegd voor de indeling en de juiste plaatsing van module Help-onderwerpen en er wordt verwezen naar richtlijnen voor de module Help-inhoud.</span><span class="sxs-lookup"><span data-stu-id="49110-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="49110-106">Typen Help bij integratiemodule</span><span class="sxs-lookup"><span data-stu-id="49110-106">Types of Module Help</span></span>

<span data-ttu-id="49110-107">Een module kan de volgende typen van Help-informatie bevatten.</span><span class="sxs-lookup"><span data-stu-id="49110-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="49110-108">**Help van de cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="49110-108">**Cmdlet Help**.</span></span> <span data-ttu-id="49110-109">De Help-onderwerpen waarin wordt beschreven cmdlets in een module zijn XML-bestanden die met de opdracht help schema</span><span class="sxs-lookup"><span data-stu-id="49110-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="49110-110">**Provider Help**.</span><span class="sxs-lookup"><span data-stu-id="49110-110">**Provider Help**.</span></span> <span data-ttu-id="49110-111">De Help-onderwerpen waarin wordt beschreven providers in een module zijn XML-bestanden die gebruikmaken van de provider hulp schema.</span><span class="sxs-lookup"><span data-stu-id="49110-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="49110-112">**Functie Help**.</span><span class="sxs-lookup"><span data-stu-id="49110-112">**Function Help**.</span></span> <span data-ttu-id="49110-113">De Help-onderwerpen waarin wordt beschreven functies in een module mag XML-bestanden die met de opdracht help schema of op basis van een opmerking Help-onderwerpen in de functie of het script of scriptmodule</span><span class="sxs-lookup"><span data-stu-id="49110-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="49110-114">**Help script**.</span><span class="sxs-lookup"><span data-stu-id="49110-114">**Script Help**.</span></span> <span data-ttu-id="49110-115">De Help-onderwerpen waarin wordt beschreven scripts in een module kan het XML-bestanden die met de opdracht help schema of Help-onderwerpen op basis van een opmerking in het script of de scriptmodule zijn.</span><span class="sxs-lookup"><span data-stu-id="49110-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="49110-116">**Conceptuele ('About'), Help**.</span><span class="sxs-lookup"><span data-stu-id="49110-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="49110-117">U kunt een conceptuele ('about'), Help-onderwerp gebruiken om te beschrijven van de module en de bijbehorende leden en waarin wordt uitgelegd hoe de leden kunnen samen worden gebruikt om uit te voeren taken.</span><span class="sxs-lookup"><span data-stu-id="49110-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="49110-118">Algemene Help-onderwerpen zijn tekstbestanden met Unicode (UTF-8)-codering.</span><span class="sxs-lookup"><span data-stu-id="49110-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="49110-119">De bestandsnaam moet gebruiken de `about_<name>.help.txt` indeling, zoals about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="49110-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="49110-120">Standaard Windows PowerShell bevat meer dan 100 van deze concepten over het Help-onderwerpen en ze zijn opgemaakt als in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="49110-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="49110-121">Plaatsing van de Help bij integratiemodule</span><span class="sxs-lookup"><span data-stu-id="49110-121">Placement of Module Help</span></span>

<span data-ttu-id="49110-122">De `Get-Help` cmdlet module Help-Onderwerpbestanden in submappen van de modulemap taalspecifieke zoekt.</span><span class="sxs-lookup"><span data-stu-id="49110-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="49110-123">Bijvoorbeeld, ziet het volgende diagram voor directory-structuur u de locatie van de Help-onderwerpen voor de module SampleModule.</span><span class="sxs-lookup"><span data-stu-id="49110-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="49110-124">In het voorbeeld wordt de  *\<ModulePath >* een tijdelijke aanduiding voor een van de paden in de `PSModulePath` omgevingsvariabele, zoals $home\Documents\Modules, $pshome\Modules of een aangepast pad dat de gebruiker opgeeft.</span><span class="sxs-lookup"><span data-stu-id="49110-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="49110-125">Module Help opvragen</span><span class="sxs-lookup"><span data-stu-id="49110-125">Getting Module Help</span></span>

<span data-ttu-id="49110-126">Wanneer een gebruiker een module wordt geïmporteerd in een sessie, wordt de Help-onderwerpen voor die module worden geïmporteerd in de sessie, samen met de module.</span><span class="sxs-lookup"><span data-stu-id="49110-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="49110-127">U kunt de Help-onderwerp-bestanden in de waarde van de sleutel FileList in de module-manifest weergeven, maar het Help-onderwerpen worden niet beïnvloed door de `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49110-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="49110-128">U kunt de module Help-onderwerpen in verschillende talen opgeven.</span><span class="sxs-lookup"><span data-stu-id="49110-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="49110-129">De `Get-Help` cmdlet module Help-onderwerpen automatisch weergegeven in de taal die is opgegeven voor de huidige gebruiker van het onderdeel Landinstellingen in het Configuratiescherm.</span><span class="sxs-lookup"><span data-stu-id="49110-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="49110-130">In Windows Vista en latere versies van Windows, `Get-Help` zoekt naar de Help-onderwerpen in taalspecifieke submappen van de modulemap in overeenstemming met de taal terugval standaarden die zijn vastgelegd voor Windows.</span><span class="sxs-lookup"><span data-stu-id="49110-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="49110-131">In Windows PowerShell 3.0 wordt uitgevoerd vanaf een `Get-Help` opdracht voor een cmdlet of de functie activeert automatisch importeren van de module.</span><span class="sxs-lookup"><span data-stu-id="49110-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="49110-132">De `Get-Help` cmdlet wordt de inhoud van de help-onderwerpen onmiddellijk weergegeven in de module.</span><span class="sxs-lookup"><span data-stu-id="49110-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="49110-133">Als de module geen help-onderwerpen bevat en er geen help-onderwerpen voor de opdrachten in de module op de computer van de gebruiker zijn, `Get-Help` wordt automatisch gegenereerde help weergegeven.</span><span class="sxs-lookup"><span data-stu-id="49110-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="49110-134">De automatisch gegenereerde help bevat de syntaxis, parameters en invoer- en -typen, maar bevat geen beschrijvingen.</span><span class="sxs-lookup"><span data-stu-id="49110-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="49110-135">De help voor het automatisch gegenereerde bevat tekst waarmee de gebruiker om te proberen te gebruiken de `Update-Help` cmdlet help voor de opdracht downloaden vanaf Internet of een bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="49110-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="49110-136">Dit ook is de aanbevolen met behulp van de **Online** parameter van de `Get-Help` cmdlet om op te halen van de online versie van het help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="49110-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="49110-137">Ondersteunende help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="49110-137">Supporting Updatable Help</span></span>

<span data-ttu-id="49110-138">Gebruikers van Windows PowerShell 3.0 en latere versies van Windows PowerShell kunnen downloaden en installeren van bijgewerkte help-bestanden voor een module van het Internet of vanaf een lokaal bestand-share.</span><span class="sxs-lookup"><span data-stu-id="49110-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="49110-139">De `Update-Help` en `Save-Help` cmdlets verbergen de details van de management van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="49110-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="49110-140">Gebruikers voeren de `Update-Help` cmdlet en gebruik vervolgens de `Get-Help` cmdlet voor het lezen van de meest recente help-bestanden voor de module bij de opdrachtprompt van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49110-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="49110-141">Gebruikers hoeven niet opnieuw opstarten van Windows of Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49110-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="49110-142">Gebruikers achter firewalls en die geen toegang tot Internet kunnen gebruiken bij te werken Help, evenals.</span><span class="sxs-lookup"><span data-stu-id="49110-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="49110-143">Beheerders met Internet gebruik toegang tot de `Save-Help` cmdlet om te downloaden en installeren van de meest recente help-bestanden naar een bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="49110-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="49110-144">Vervolgens gebruikt u gebruikers de **pad** parameter van de `Update-Help` cmdlet om op te halen van de meest recente help-bestanden van de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="49110-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="49110-145">Auteurs kunnen help-bestanden opnemen in de module en gebruik bij te werken Help bijwerken van de help-bestanden of weglaten help-bestanden van de module en gebruik bij te werken Help zowel om te installeren en deze kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="49110-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="49110-146">Zie voor meer informatie over het bij te werken Help [ondersteunende bij te werken Help](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="49110-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="49110-147">Ondersteunende online help</span><span class="sxs-lookup"><span data-stu-id="49110-147">Supporting Online Help</span></span>

<span data-ttu-id="49110-148">Gebruikers die niet of Installeer geen bijgewerkte help-bestanden op hun computers is vaak afhankelijk van de online versie van de module help-onderwerpen zijn.</span><span class="sxs-lookup"><span data-stu-id="49110-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="49110-149">De **Online** parameter van de `Get-Help` cmdlet opent de online versie van een cmdlet of een geavanceerde functie help-onderwerp voor de gebruiker in de standaardbrowser van het Internet.</span><span class="sxs-lookup"><span data-stu-id="49110-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="49110-150">De `Get-Help` cmdlet wordt de waarde van de **HelpUri** eigenschap van de cmdlet of de functie voor het vinden van de online versie van het help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="49110-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="49110-151">Vanaf Windows PowerShell 3.0, kunt u gebruikers de online versie van de cmdlet en de functie help-onderwerpen vinden door te definiëren van het kenmerk HelpUri van de cmdlet-klasse of de **HelpUri** eigenschap van de **CmdletBinding** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="49110-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="49110-152">De waarde van het kenmerk is de waarde van de **HelpUri** eigenschap van de cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="49110-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="49110-153">Zie voor meer informatie, [ondersteunende Online Help](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="49110-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49110-154">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49110-154">See Also</span></span>

[<span data-ttu-id="49110-155">Een Windows PowerShell-Module schrijven</span><span class="sxs-lookup"><span data-stu-id="49110-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="49110-156">Ondersteunende Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="49110-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="49110-157">Ondersteunende Online Help</span><span class="sxs-lookup"><span data-stu-id="49110-157">Supporting Online Help</span></span>](./supporting-online-help.md)