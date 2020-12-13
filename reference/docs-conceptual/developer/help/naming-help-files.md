---
ms.date: 09/12/2016
ms.topic: reference
title: Naamgeving van Help-bestanden
description: Naamgeving van Help-bestanden
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667586"
---
# <a name="naming-help-files"></a><span data-ttu-id="86ac0-103">Naamgeving van Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="86ac0-103">Naming Help Files</span></span>

<span data-ttu-id="86ac0-104">In dit onderwerp wordt uitgelegd hoe u een XML-gebaseerd Help-bestand kunt benoemen, zodat de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) het kan vinden.</span><span class="sxs-lookup"><span data-stu-id="86ac0-104">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="86ac0-105">De naam vereisten verschillen per opdracht type.</span><span class="sxs-lookup"><span data-stu-id="86ac0-105">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="86ac0-106">Help-bestanden voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="86ac0-106">Cmdlet Help Files</span></span>

<span data-ttu-id="86ac0-107">Het Help-bestand voor een C#-cmdlet moet een naam hebben voor de assembly waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-107">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="86ac0-108">Gebruik de volgende bestands indeling:</span><span class="sxs-lookup"><span data-stu-id="86ac0-108">Use the following filename format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="86ac0-109">De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="86ac0-109">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="86ac0-110">De cmdlet [Get-Wine vent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) wordt bijvoorbeeld gedefinieerd in de assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="86ac0-110">For example, the [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="86ac0-111">De `Get-Help` cmdlet zoekt alleen naar een Help-onderwerp voor de `Get-WinEvent` cmdlet in het `Microsoft.PowerShell.Diagnostics.dll-help.xml` bestand in de module directory.</span><span class="sxs-lookup"><span data-stu-id="86ac0-111">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the `Microsoft.PowerShell.Diagnostics.dll-help.xml` file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="86ac0-112">Help-bestanden voor providers</span><span class="sxs-lookup"><span data-stu-id="86ac0-112">Provider Help files</span></span>

<span data-ttu-id="86ac0-113">Het Help-bestand voor een Power shell-provider moet een naam hebben voor de assembly waarin de provider is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-113">The help file for a PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="86ac0-114">Gebruik de volgende bestands indeling:</span><span class="sxs-lookup"><span data-stu-id="86ac0-114">Use the following filename format:</span></span>

`<AssemblyName>.dll-help.xml`

<span data-ttu-id="86ac0-115">De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="86ac0-115">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="86ac0-116">Bijvoorbeeld, de certificaat provider wordt gedefinieerd in de `Microsoft.PowerShell.Security.dll` Assembly.</span><span class="sxs-lookup"><span data-stu-id="86ac0-116">For example, the Certificate provider is defined in the `Microsoft.PowerShell.Security.dll` assembly.</span></span> <span data-ttu-id="86ac0-117">De `Get-Help` cmdlet zoekt alleen naar een Help-onderwerp voor de certificaat provider in het `Microsoft.PowerShell.Security.dll-help.xml` bestand in de module directory.</span><span class="sxs-lookup"><span data-stu-id="86ac0-117">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the `Microsoft.PowerShell.Security.dll-help.xml` file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="86ac0-118">Help-bestanden voor functies</span><span class="sxs-lookup"><span data-stu-id="86ac0-118">Function Help Files</span></span>

<span data-ttu-id="86ac0-119">Functies kunnen worden gedocumenteerd met behulp van [Help op basis van opmerkingen](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of gedocumenteerd in een XML-Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="86ac0-119">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="86ac0-120">Wanneer de functie is gedocumenteerd in een XML-bestand, moet de functie een `.ExternalHelp` Opmerking bevatten die de functie koppelt aan het XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="86ac0-120">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="86ac0-121">Anders kan het `Get-Help` Help-bestand niet worden gevonden met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="86ac0-121">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="86ac0-122">Er zijn geen technische vereisten voor de naam van een functie Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="86ac0-122">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="86ac0-123">Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de functie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-123">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="86ac0-124">De volgende functie is bijvoorbeeld gedefinieerd in het `MyModule.psm1` bestand.</span><span class="sxs-lookup"><span data-stu-id="86ac0-124">For example, the following function is defined in the `MyModule.psm1` file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="86ac0-125">Help-bestanden voor de CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="86ac0-125">CIM Command Help Files</span></span>

<span data-ttu-id="86ac0-126">Het Help-bestand voor een CIM-opdracht moet een naam hebben voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-126">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="86ac0-127">Gebruik de volgende bestands indeling:</span><span class="sxs-lookup"><span data-stu-id="86ac0-127">Use the following filename format:</span></span>

`<FileName>.cdxml-help.xml`

<span data-ttu-id="86ac0-128">CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules.</span><span class="sxs-lookup"><span data-stu-id="86ac0-128">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="86ac0-129">Wanneer de CIM-opdracht in de sessie als een functie wordt geïmporteerd, voegt Power shell een `.ExternalHelp` tref woord opmerking toe aan de functie definitie die de functie koppelt aan een XML Help-bestand met de naam van het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-129">When the CIM command is imported into the session as a function, PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="86ac0-130">Help-bestanden voor de script werk stroom</span><span class="sxs-lookup"><span data-stu-id="86ac0-130">Script Workflow Help Files</span></span>

<span data-ttu-id="86ac0-131">Script werk stromen die zijn opgenomen in modules kunnen worden gedocumenteerd in Help-bestanden op basis van XML.</span><span class="sxs-lookup"><span data-stu-id="86ac0-131">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="86ac0-132">Er zijn geen technische vereisten voor de naam van het Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="86ac0-132">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="86ac0-133">Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de werk stroom van het script is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-133">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="86ac0-134">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="86ac0-134">For example:</span></span>

`<ScriptModule>.psm1-help.xml`

<span data-ttu-id="86ac0-135">In tegens telling tot andere script opdrachten, is voor de script werk stromen geen `.ExternalHelp` tref woord opmerking vereist om ze te koppelen aan een Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="86ac0-135">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="86ac0-136">In plaats daarvan doorzoekt Power shell de specifieke submappen voor de gebruikers interface van de module directory voor Help-bestanden op basis van XML en zoekt u hulp voor de script werk stroom in alle bestanden.</span><span class="sxs-lookup"><span data-stu-id="86ac0-136">Instead, PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="86ac0-137">`.ExternalHelp` tref woord opmerking wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="86ac0-137">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="86ac0-138">Omdat het `.ExternalHelp` tref woord opmerking wordt genegeerd, `Get-Help` kan de cmdlet alleen hulp voor script werk stromen vinden als deze zijn opgenomen in modules.</span><span class="sxs-lookup"><span data-stu-id="86ac0-138">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
