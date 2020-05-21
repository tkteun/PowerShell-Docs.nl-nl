---
title: Naamgeving van Help-bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: d13324871bac7ba21c0e042e8674c5996e5dba85
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560216"
---
# <a name="naming-help-files"></a><span data-ttu-id="c023a-102">Naamgeving van Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="c023a-102">Naming Help Files</span></span>

<span data-ttu-id="c023a-103">In dit onderwerp wordt uitgelegd hoe u een XML-gebaseerd Help-bestand kunt benoemen, zodat de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) het kan vinden.</span><span class="sxs-lookup"><span data-stu-id="c023a-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="c023a-104">De naam vereisten verschillen per opdracht type.</span><span class="sxs-lookup"><span data-stu-id="c023a-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="c023a-105">Help-bestanden voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="c023a-105">Cmdlet Help Files</span></span>

<span data-ttu-id="c023a-106">Het Help-bestand voor een C#-cmdlet moet een naam hebben voor de assembly waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="c023a-107">Gebruik de volgende indeling voor bestands namen:</span><span class="sxs-lookup"><span data-stu-id="c023a-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="c023a-108">De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="c023a-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="c023a-109">Bijvoorbeeld, de [Get-Wine vent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is gedefinieerd in de assembly micro soft. Power shell. Diagnostics. dll.</span><span class="sxs-lookup"><span data-stu-id="c023a-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="c023a-110">De `Get-Help` cmdlet zoekt alleen naar een Help-onderwerp voor de `Get-WinEvent` cmdlet in het bestand micro soft. Power shell. Diagnostics. dll-Help. XML in de module directory.</span><span class="sxs-lookup"><span data-stu-id="c023a-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="c023a-111">Help-bestanden voor providers</span><span class="sxs-lookup"><span data-stu-id="c023a-111">Provider Help files</span></span>

<span data-ttu-id="c023a-112">Het Help-bestand voor een Windows Power shell-provider moet een naam hebben voor de assembly waarin de provider is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="c023a-113">Gebruik de volgende indeling voor bestands namen:</span><span class="sxs-lookup"><span data-stu-id="c023a-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="c023a-114">De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="c023a-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="c023a-115">De certificaat provider wordt bijvoorbeeld gedefinieerd in de assembly micro soft. Power shell. Security. dll.</span><span class="sxs-lookup"><span data-stu-id="c023a-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="c023a-116">De `Get-Help` cmdlet zoekt alleen naar een Help-onderwerp voor de certificaat provider in het bestand micro soft. Power shell. Security. dll-Help. XML in de module directory.</span><span class="sxs-lookup"><span data-stu-id="c023a-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="c023a-117">Help-bestanden voor functies</span><span class="sxs-lookup"><span data-stu-id="c023a-117">Function Help Files</span></span>

<span data-ttu-id="c023a-118">Functies kunnen worden gedocumenteerd met behulp van [Help op basis van opmerkingen](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of gedocumenteerd in een XML-Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="c023a-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="c023a-119">Wanneer de functie is gedocumenteerd in een XML-bestand, moet de functie een `.ExternalHelp` Opmerking bevatten die de functie koppelt aan het XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="c023a-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="c023a-120">Anders kan het `Get-Help` Help-bestand niet worden gevonden met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c023a-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="c023a-121">Er zijn geen technische vereisten voor de naam van een functie Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="c023a-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="c023a-122">Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de functie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="c023a-123">De volgende functie wordt bijvoorbeeld gedefinieerd in het bestand MyModule. psm1.</span><span class="sxs-lookup"><span data-stu-id="c023a-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="c023a-124">Help-bestanden voor de CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="c023a-124">CIM Command Help Files</span></span>

<span data-ttu-id="c023a-125">Het Help-bestand voor een CIM-opdracht moet een naam hebben voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="c023a-126">Gebruik de volgende indeling voor bestands namen:</span><span class="sxs-lookup"><span data-stu-id="c023a-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="c023a-127">CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules.</span><span class="sxs-lookup"><span data-stu-id="c023a-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="c023a-128">Wanneer de CIM-opdracht in de sessie als een functie wordt geïmporteerd, wordt door Windows Power shell een `.ExternalHelp` tref woord opmerking toegevoegd aan de functie definitie die de functie koppelt aan een XML Help-bestand met de naam van het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="c023a-129">Help-bestanden voor de script werk stroom</span><span class="sxs-lookup"><span data-stu-id="c023a-129">Script Workflow Help Files</span></span>

<span data-ttu-id="c023a-130">Script werk stromen die zijn opgenomen in modules kunnen worden gedocumenteerd in Help-bestanden op basis van XML.</span><span class="sxs-lookup"><span data-stu-id="c023a-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="c023a-131">Er zijn geen technische vereisten voor de naam van het Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="c023a-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="c023a-132">Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de werk stroom van het script is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="c023a-133">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c023a-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="c023a-134">In tegens telling tot andere script opdrachten, is voor de script werk stromen geen `.ExternalHelp` tref woord opmerking vereist om ze te koppelen aan een Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="c023a-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="c023a-135">In plaats daarvan zoekt Windows Power shell de specifieke submappen voor de gebruikers interface van de module directory voor Help-bestanden op basis van XML en zoekt de hulp voor de script werk stroom in alle bestanden.</span><span class="sxs-lookup"><span data-stu-id="c023a-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="c023a-136">`.ExternalHelp`tref woord opmerking wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="c023a-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="c023a-137">Omdat het `.ExternalHelp` tref woord opmerking wordt genegeerd, `Get-Help` kan de cmdlet alleen hulp voor script werk stromen vinden als deze zijn opgenomen in modules.</span><span class="sxs-lookup"><span data-stu-id="c023a-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
