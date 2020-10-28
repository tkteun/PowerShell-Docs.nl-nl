---
ms.date: 09/13/2016
ms.topic: reference
title: Een binaire PowerShell-module schrijven
description: Een binaire PowerShell-module schrijven
ms.openlocfilehash: 1d5cea474ac418f78cc782360b7c23b7614d6669
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663064"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="173bf-103">Een binaire PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="173bf-103">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="173bf-104">Een binaire module kan een assembly (. dll) zijn die cmdlet-klassen bevat.</span><span class="sxs-lookup"><span data-stu-id="173bf-104">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="173bf-105">Standaard worden alle cmdlets in de assembly geïmporteerd wanneer de binaire module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="173bf-105">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="173bf-106">U kunt echter de cmdlets die worden geïmporteerd beperken door een module manifest te maken waarvan de basis module de assembly is.</span><span class="sxs-lookup"><span data-stu-id="173bf-106">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="173bf-107">(De sleutel CmdletsToExport van het manifest kan bijvoorbeeld worden gebruikt voor het exporteren van alleen de cmdlets die nodig zijn.) Daarnaast kan een binaire module extra bestanden, een mapstructuur en andere delen van nuttige beheer gegevens bevatten die één cmdlet niet kan.</span><span class="sxs-lookup"><span data-stu-id="173bf-107">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="173bf-108">In de volgende procedure wordt beschreven hoe u een binaire Power shell-module maakt en installeert.</span><span class="sxs-lookup"><span data-stu-id="173bf-108">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="173bf-109">Een binaire Power shell-module maken en installeren</span><span class="sxs-lookup"><span data-stu-id="173bf-109">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="173bf-110">Maak een binaire Power Shell-oplossing (zoals een cmdlet die is geschreven in C#) met de mogelijkheden die u nodig hebt, en zorg ervoor dat deze goed wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="173bf-110">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="173bf-111">Vanuit een code perspectief is de kern van een binaire module gewoon een cmdlet-assembly.</span><span class="sxs-lookup"><span data-stu-id="173bf-111">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="173bf-112">In feite behandelt Power shell een enkele cmdlet-assembly als module, in termen van laden en verwijderen, zonder extra inspanningen voor het deel van de ontwikkelaar.</span><span class="sxs-lookup"><span data-stu-id="173bf-112">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="173bf-113">Zie [een Windows Power shell-cmdlet schrijven](../cmdlet/writing-a-windows-powershell-cmdlet.md)voor meer informatie over het schrijven van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="173bf-113">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="173bf-114">Indien nodig, kunt u de rest van uw oplossing maken: (extra cmdlets, XML-bestanden enzovoort) en deze beschrijven met een module manifest.</span><span class="sxs-lookup"><span data-stu-id="173bf-114">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="173bf-115">Naast het beschrijven van de cmdlet-assembly's in uw oplossing, kan een module manifest beschrijven hoe u de module wilt exporteren en importeren, welke cmdlets worden weer gegeven en welke extra bestanden er in de module worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="173bf-115">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="173bf-116">Zoals eerder is aangegeven, kan Power shell een binaire cmdlet beschouwen als een module zonder extra inspanning.</span><span class="sxs-lookup"><span data-stu-id="173bf-116">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="173bf-117">Als zodanig is een module manifest vooral nuttig voor het combi neren van meerdere bestanden in één pakket, of voor het expliciet beheren van de publicatie voor een bepaalde assembly.</span><span class="sxs-lookup"><span data-stu-id="173bf-117">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="173bf-118">Zie [een Power shell-module manifest schrijven](how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="173bf-118">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="173bf-119">De volgende code is een uiterst eenvoudig C#-code blok dat drie cmdlets bevat in hetzelfde bestand dat kan worden gebruikt als een module.</span><span class="sxs-lookup"><span data-stu-id="173bf-119">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="173bf-120">Verpak uw oplossing en sla het pakket ergens op in het pad van de Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="173bf-120">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="173bf-121">Met de `PSModulePath` variabele globale omgeving worden de standaard paden beschreven die Power shell gebruikt om uw module te zoeken.</span><span class="sxs-lookup"><span data-stu-id="173bf-121">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="173bf-122">Bijvoorbeeld, een gemeen schappelijk pad om een module op een systeem op te slaan zou zijn `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` .</span><span class="sxs-lookup"><span data-stu-id="173bf-122">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="173bf-123">Als u de standaard paden niet gebruikt, moet u de locatie van de module tijdens de installatie expliciet aangeven.</span><span class="sxs-lookup"><span data-stu-id="173bf-123">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="173bf-124">Zorg ervoor dat u een map maakt om uw module op te slaan in, omdat u de map mogelijk nodig hebt om meerdere assembly's en bestanden voor uw oplossing op te slaan.</span><span class="sxs-lookup"><span data-stu-id="173bf-124">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="173bf-125">Houd er rekening mee dat u de module niet hoeft te installeren. dit `PSModulePath` zijn gewoon de standaard locaties die Power shell zoekt naar uw module.</span><span class="sxs-lookup"><span data-stu-id="173bf-125">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="173bf-126">Het wordt echter wel best practice om dit te doen, tenzij u een goede reden hebt om uw module ergens anders op te slaan.</span><span class="sxs-lookup"><span data-stu-id="173bf-126">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="173bf-127">Zie [een Power shell-module installeren](./installing-a-powershell-module.md) en het installatiepad van [de Power shell-module aanpassen](./modifying-the-psmodulepath-installation-path.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="173bf-127">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="173bf-128">Importeer uw module in Power shell met een aanroep van [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="173bf-128">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="173bf-129">Bij het aanroepen van [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) wordt uw module in het actieve geheugen geladen.</span><span class="sxs-lookup"><span data-stu-id="173bf-129">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="173bf-130">Als u Power Shell 3,0 en hoger gebruikt, kunt u gewoon de naam van uw module in code aanroepen. Zie [een Power shell-module importeren](./importing-a-powershell-module.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="173bf-130">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="173bf-131">Module-Assembly's importeren als modules</span><span class="sxs-lookup"><span data-stu-id="173bf-131">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="173bf-132">Cmdlets en providers die in module-assembly's voor komen, kunnen als binaire modules worden geladen.</span><span class="sxs-lookup"><span data-stu-id="173bf-132">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="173bf-133">Wanneer de module-assembly's als binaire modules worden geladen, zijn de cmdlets en providers in de module beschikbaar voor de gebruiker, maar de module klasse in de assembly wordt genegeerd en de module is niet geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="173bf-133">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="173bf-134">Als gevolg hiervan kunnen de module-cmdlets van Windows Power shell de module niet detecteren, zelfs niet als de cmdlets en providers beschikbaar zijn voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="173bf-134">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="173bf-135">Daarnaast kunnen opmaak of typen bestanden waarnaar wordt verwezen door de module, niet worden geïmporteerd als onderdeel van een binaire module.</span><span class="sxs-lookup"><span data-stu-id="173bf-135">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="173bf-136">Als u de indeling en typen bestanden wilt importeren, moet u een module manifest maken.</span><span class="sxs-lookup"><span data-stu-id="173bf-136">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="173bf-137">Zie [een Power shell-module manifest schrijven voor meer informatie](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="173bf-137">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="173bf-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="173bf-138">See Also</span></span>

[<span data-ttu-id="173bf-139">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="173bf-139">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
