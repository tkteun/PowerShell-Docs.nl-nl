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
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847276"
---
# <a name="naming-help-files"></a><span data-ttu-id="cec82-102">Naamgeving van Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="cec82-102">Naming Help Files</span></span>

<span data-ttu-id="cec82-103">In dit onderwerp wordt uitgelegd hoe u om de naam van een help op basis van een XML-bestand zodat het [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="cec82-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="cec82-104">De vereisten voor de naam verschillen voor elk opdrachttype.</span><span class="sxs-lookup"><span data-stu-id="cec82-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="cec82-105">In dit onderwerp wordt uitgelegd hoe u om de naam van een help op basis van een XML-bestand zodat het [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="cec82-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="cec82-106">De vereisten voor de naam verschillen voor elk opdrachttype.</span><span class="sxs-lookup"><span data-stu-id="cec82-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="cec82-107">Cmdlet Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="cec82-107">Cmdlet Help Files</span></span>

<span data-ttu-id="cec82-108">Het help-bestand voor een C# cmdlet moet de naam voor de assembly waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="cec82-109">Gebruik de volgende bestandsindeling: naam:</span><span class="sxs-lookup"><span data-stu-id="cec82-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="cec82-110">De indeling van de assembly-naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="cec82-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="cec82-111">Bijvoorbeeld, de [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is gedefinieerd in de assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="cec82-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="cec82-112">De `Get-Help` cmdlet zoekt een help-onderwerp voor de `Get-WinEvent` cmdlet alleen in het bestand Microsoft.PowerShell.Diagnostics.dll help.xml in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="cec82-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="cec82-113">Bijvoorbeeld, de [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is gedefinieerd in de assembly Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="cec82-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="cec82-114">De `Get-Help` cmdlet zoekt een help-onderwerp voor de `Get-WinEvent` cmdlet alleen in het bestand Microsoft.PowerShell.Diagnostics.dll help.xml in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="cec82-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="cec82-115">Provider van Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="cec82-115">Provider Help files</span></span>

<span data-ttu-id="cec82-116">Het help-bestand voor een Windows PowerShell-provider moet de naam voor de assembly waarin de provider is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="cec82-117">Gebruik de volgende bestandsindeling: naam:</span><span class="sxs-lookup"><span data-stu-id="cec82-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="cec82-118">De indeling van de assembly-naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="cec82-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="cec82-119">Bijvoorbeeld, is de certificaat-provider gedefinieerd in de assembly Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="cec82-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="cec82-120">De `Get-Help` cmdlet zoekt een help-onderwerp in voor de provider certificaat alleen in het bestand Microsoft.PowerShell.Security.dll help.xml in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="cec82-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="cec82-121">Functie Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="cec82-121">Function Help Files</span></span>

<span data-ttu-id="cec82-122">Functions kunnen worden vastgelegd met behulp van [help op basis van een opmerking](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of in een XML-help-bestand wordt vermeld.</span><span class="sxs-lookup"><span data-stu-id="cec82-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="cec82-123">Als de functie wordt gedocumenteerd in een XML-bestand, de functie moet beschikken over een `.ExternalHelp` Opmerking trefwoord dat u de functie aan het XML-bestand koppelt.</span><span class="sxs-lookup"><span data-stu-id="cec82-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="cec82-124">Anders wordt de `Get-Help` cmdlet kan het help-bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="cec82-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="cec82-125">Functions kunnen worden vastgelegd met behulp van [help op basis van een opmerking](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of in een XML-help-bestand wordt vermeld.</span><span class="sxs-lookup"><span data-stu-id="cec82-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="cec82-126">Als de functie wordt gedocumenteerd in een XML-bestand, de functie moet beschikken over een `.ExternalHelp` Opmerking trefwoord dat u de functie aan het XML-bestand koppelt.</span><span class="sxs-lookup"><span data-stu-id="cec82-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="cec82-127">Anders wordt de `Get-Help` cmdlet kan het help-bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="cec82-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="cec82-128">Er zijn geen technische vereisten voor de naam van een help-bestand.</span><span class="sxs-lookup"><span data-stu-id="cec82-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="cec82-129">Er is echter een best practice om de naam van het help-bestand voor de scriptmodule waarin de functie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="cec82-130">Bijvoorbeeld, is de volgende functie gedefinieerd in het bestand MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="cec82-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="cec82-131">CIM-opdracht Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="cec82-131">CIM Command Help Files</span></span>

<span data-ttu-id="cec82-132">Het help-bestand voor een CIM-opdracht moet de naam voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="cec82-133">Gebruik de volgende bestandsindeling: naam:</span><span class="sxs-lookup"><span data-stu-id="cec82-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="cec82-134">CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules.</span><span class="sxs-lookup"><span data-stu-id="cec82-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="cec82-135">Wanneer de CIM-opdracht wordt geïmporteerd in de sessie als een functie, Windows PowerShell wordt toegevoegd een `.ExternalHelp` Opmerking trefwoord dat u wilt de functiedefinitie van de die wordt gekoppeld aan de functie aan de hand van een XML-bestand dat de naam voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="cec82-136">Script werkstroom Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="cec82-136">Script Workflow Help Files</span></span>

<span data-ttu-id="cec82-137">Scriptwerkstromen die zijn opgenomen in modules kunnen worden beschreven in de help op basis van een XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="cec82-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="cec82-138">Er zijn geen technische vereisten voor de naam van het help-bestand.</span><span class="sxs-lookup"><span data-stu-id="cec82-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="cec82-139">Er is echter een best practice om de naam van het help-bestand voor de scriptmodule waarin de scriptwerkstroom is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="cec82-140">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cec82-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="cec82-141">In tegenstelling tot andere scripts opdrachten scriptwerkstromen hoeven niet een `.ExternalHelp` Opmerking trefwoord om deze te koppelen met een help-bestand.</span><span class="sxs-lookup"><span data-stu-id="cec82-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="cec82-142">In plaats daarvan Windows PowerShell zoekt in de UI-cultuur-specifieke submappen van de modulemap voor help op basis van een XML-bestanden en Help-informatie voor de scriptwerkstroom in alle bestanden zoekt.</span><span class="sxs-lookup"><span data-stu-id="cec82-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="cec82-143">`.ExternalHelp` Opmerking sleutelwoord worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="cec82-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="cec82-144">Omdat de `.ExternalHelp` Opmerking trefwoord wordt genegeerd, de `Get-Help` cmdlet kunt hulp zoeken over scriptwerkstromen alleen wanneer ze zijn opgenomen in modules.</span><span class="sxs-lookup"><span data-stu-id="cec82-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>