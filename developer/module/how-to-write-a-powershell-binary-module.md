---
title: Over het schrijven van een binaire waarde PowerShell-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229331"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="77a18-102">Een binaire PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="77a18-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="77a18-103">Een binaire module kan assembly (.dll) met de cmdlet-klassen zijn.</span><span class="sxs-lookup"><span data-stu-id="77a18-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="77a18-104">Standaard worden alle cmdlets in de assembly geïmporteerd wanneer de binaire module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="77a18-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="77a18-105">U kunt echter de cmdlets die worden geïmporteerd met het maken van een module-manifest waarvan root-module de assembly is beperken.</span><span class="sxs-lookup"><span data-stu-id="77a18-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="77a18-106">(Bijvoorbeeld de CmdletsToExport-sleutel van het manifest kan worden gebruikt voor het exporteren van alleen die cmdlets die nodig zijn.) Een binaire module kan bovendien extra bestanden, een mapstructuur en andere stukjes nuttig beheergegevens dat één cmdlet niet kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="77a18-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="77a18-107">De volgende procedure wordt beschreven hoe u maken en een binaire PowerShell-module te installeren.</span><span class="sxs-lookup"><span data-stu-id="77a18-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="77a18-108">Het maken en een binaire PowerShell-module installeren</span><span class="sxs-lookup"><span data-stu-id="77a18-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="77a18-109">Maken van een binaire PowerShell-oplossing (zoals een cmdlet die zijn geschreven in C#), met alle mogelijkheden die u nodig hebt en zorg ervoor dat deze correct kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="77a18-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="77a18-110">Vanuit het oogpunt van code is de kern van een binaire module gewoon een cmdlet-assembly.</span><span class="sxs-lookup"><span data-stu-id="77a18-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="77a18-111">PowerShell wordt in feite een assembly één cmdlet behandelen als een module in termen van laden en verwijderen met geen extra moeite van de ontwikkelaar.</span><span class="sxs-lookup"><span data-stu-id="77a18-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="77a18-112">Zie voor meer informatie over het schrijven van een cmdlet [schrijven van een Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="77a18-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="77a18-113">Maak indien nodig de rest van uw oplossing: (andere cmdlets, XML-bestanden, enzovoort) en deze worden beschreven met een module-manifest.</span><span class="sxs-lookup"><span data-stu-id="77a18-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="77a18-114">Naast het met een beschrijving van de cmdlet-assembly's in uw oplossing, kan een module-manifest wordt beschreven hoe u wilt dat uw module geëxporteerd en geïmporteerd, welke cmdlets weergegeven en wat extra bestanden gaat in de module.</span><span class="sxs-lookup"><span data-stu-id="77a18-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="77a18-115">Zoals eerder gezegd echter, kan PowerShell een binaire cmdlet, zoals een module met geen extra moeite behandelen.</span><span class="sxs-lookup"><span data-stu-id="77a18-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="77a18-116">Een module-manifest is daarom handig hoofdzakelijk bestemd voor meerdere bestanden combineren in één pakket, of voor het beheren van expliciet publicatie voor een bepaalde assembly.</span><span class="sxs-lookup"><span data-stu-id="77a18-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="77a18-117">Zie voor meer informatie, [over het schrijven van een PowerShell-Module-Manifest](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="77a18-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="77a18-118">De volgende code is een zeer eenvoudige C# codeblok met drie cmdlets in hetzelfde bestand dat kan worden gebruikt als een module.</span><span class="sxs-lookup"><span data-stu-id="77a18-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="77a18-119">Verpakt uw oplossing en het pakket opslaan naar een locatie in het pad van de module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a18-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="77a18-120">De `PSModulePath` globale omgevingsvariabele beschrijft de standaardpaden dat door PowerShell wordt gebruikt om te vinden van uw module.</span><span class="sxs-lookup"><span data-stu-id="77a18-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="77a18-121">Bijvoorbeeld, een algemeen pad naar het opslaan van een module op een systeem zouden worden `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="77a18-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="77a18-122">Als u niet de standaardpaden gebruikt, moet u de locatie van uw module expliciet status tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="77a18-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="77a18-123">Zorg dat u maakt een map voor het opslaan van uw module in, zoals u de map voor het opslaan van meerdere assembly's en bestanden voor uw oplossing moet mogelijk.</span><span class="sxs-lookup"><span data-stu-id="77a18-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="77a18-124">Houd er rekening mee dat technisch u niet hoeft te installeren op uw module overal op de `PSModulePath` -dit zijn gewoon de standaardlocaties bevinden dat PowerShell wordt gezocht naar de module.</span><span class="sxs-lookup"><span data-stu-id="77a18-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="77a18-125">Maar deze wordt beschouwd als aanbevolen procedure om dit te doen, tenzij u een goede reden voor het opslaan van uw module ergens anders hebt.</span><span class="sxs-lookup"><span data-stu-id="77a18-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="77a18-126">Zie voor meer informatie, [een PowerShell-Module installeren](./installing-a-powershell-module.md) en [wijzigen van de PowerShell-Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="77a18-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="77a18-127">De module te importeren in PowerShell met een aanroep naar [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="77a18-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="77a18-128">Aanroepen naar [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) uw module in het actieve geheugen wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="77a18-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="77a18-129">Als u met behulp van PowerShell 3.0 en hoger, gewoon de naam van de module aanroepen in de code ook importeren wordt. Zie voor meer informatie, [importeren van een PowerShell-Module](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="77a18-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="77a18-130">Module-assembly's importeren als Modules</span><span class="sxs-lookup"><span data-stu-id="77a18-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="77a18-131">De cmdlets en providers die zijn opgenomen in de module-assembly's kunnen worden geladen als binaire modules.</span><span class="sxs-lookup"><span data-stu-id="77a18-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="77a18-132">Wanneer de module-assembly's geladen als binaire modules zijn, cmdlets en providers in de module zijn beschikbaar voor de gebruiker, maar de klasse-module in de assembly wordt genegeerd en de module is niet geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="77a18-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="77a18-133">De beschikbare Windows PowerShell cmdlets in het vak-module kan niet als gevolg hiervan de module detecteren zelfs als de cmdlets en providers beschikbaar voor de sessie zijn.</span><span class="sxs-lookup"><span data-stu-id="77a18-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="77a18-134">Bovendien kunnen niet alle opmaak of typen bestanden waarnaar wordt verwezen door de module worden geïmporteerd als onderdeel van een binaire module.</span><span class="sxs-lookup"><span data-stu-id="77a18-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="77a18-135">U moet een module-manifest te maken om de opmaak en typen bestanden te importeren.</span><span class="sxs-lookup"><span data-stu-id="77a18-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="77a18-136">Zie, [over het schrijven van een PowerShell-Module-Manifest](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="77a18-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77a18-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="77a18-137">See Also</span></span>

[<span data-ttu-id="77a18-138">Een Windows PowerShell-Module schrijven</span><span class="sxs-lookup"><span data-stu-id="77a18-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
