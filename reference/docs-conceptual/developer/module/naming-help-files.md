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
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357328"
---
# <a name="naming-help-files"></a><span data-ttu-id="a7d67-102">Naamgeving van Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="a7d67-102">Naming Help Files</span></span>

<span data-ttu-id="a7d67-103">In dit onderwerp wordt uitgelegd hoe u een XML-gebaseerd Help-bestand kunt benoemen, zodat de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) het kan vinden.</span><span class="sxs-lookup"><span data-stu-id="a7d67-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="a7d67-104">De naam vereisten verschillen per opdracht type.</span><span class="sxs-lookup"><span data-stu-id="a7d67-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="a7d67-105">Help-bestanden voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="a7d67-105">Cmdlet Help Files</span></span>

<span data-ttu-id="a7d67-106">Het Help-bestand voor C# een cmdlet moet een naam hebben voor de assembly waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="a7d67-107">Gebruik de volgende indeling voor bestands namen:</span><span class="sxs-lookup"><span data-stu-id="a7d67-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="a7d67-108">De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="a7d67-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="a7d67-109">Bijvoorbeeld, de [Get-Wine vent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is gedefinieerd in de assembly micro soft. Power shell. Diagnostics. dll.</span><span class="sxs-lookup"><span data-stu-id="a7d67-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="a7d67-110">De `Get-Help`-cmdlet zoekt alleen naar een Help-onderwerp voor de cmdlet `Get-WinEvent` in het bestand micro soft. Power shell. Diagnostics. dll-Help. XML in de module directory.</span><span class="sxs-lookup"><span data-stu-id="a7d67-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="a7d67-111">Help-bestanden voor providers</span><span class="sxs-lookup"><span data-stu-id="a7d67-111">Provider Help files</span></span>

<span data-ttu-id="a7d67-112">Het Help-bestand voor een Windows Power shell-provider moet een naam hebben voor de assembly waarin de provider is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="a7d67-113">Gebruik de volgende indeling voor bestands namen:</span><span class="sxs-lookup"><span data-stu-id="a7d67-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="a7d67-114">De indeling van de assembly naam is vereist, zelfs wanneer de assembly een geneste module is.</span><span class="sxs-lookup"><span data-stu-id="a7d67-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="a7d67-115">De certificaat provider wordt bijvoorbeeld gedefinieerd in de assembly micro soft. Power shell. Security. dll.</span><span class="sxs-lookup"><span data-stu-id="a7d67-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="a7d67-116">De `Get-Help`-cmdlet zoekt alleen naar een Help-onderwerp voor de certificaat provider in het bestand micro soft. Power shell. Security. dll-Help. XML in de module directory.</span><span class="sxs-lookup"><span data-stu-id="a7d67-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="a7d67-117">Help-bestanden voor functies</span><span class="sxs-lookup"><span data-stu-id="a7d67-117">Function Help Files</span></span>

<span data-ttu-id="a7d67-118">Functies kunnen worden gedocumenteerd met behulp van [Help op basis van opmerkingen](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) of gedocumenteerd in een XML-Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="a7d67-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="a7d67-119">Wanneer de functie is gedocumenteerd in een XML-bestand, moet de functie een sleutel woord `.ExternalHelp` hebben dat de functie koppelt aan het XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="a7d67-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="a7d67-120">Anders kan de `Get-Help`-cmdlet het Help-bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="a7d67-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="a7d67-121">Er zijn geen technische vereisten voor de naam van een functie Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="a7d67-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="a7d67-122">Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de functie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="a7d67-123">De volgende functie wordt bijvoorbeeld gedefinieerd in het bestand MyModule. psm1.</span><span class="sxs-lookup"><span data-stu-id="a7d67-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="a7d67-124">Help-bestanden voor de CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="a7d67-124">CIM Command Help Files</span></span>

<span data-ttu-id="a7d67-125">Het Help-bestand voor een CIM-opdracht moet een naam hebben voor het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="a7d67-126">Gebruik de volgende indeling voor bestands namen:</span><span class="sxs-lookup"><span data-stu-id="a7d67-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="a7d67-127">CIM-opdrachten worden gedefinieerd in CDXML-bestanden die kunnen worden opgenomen in modules als geneste modules.</span><span class="sxs-lookup"><span data-stu-id="a7d67-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="a7d67-128">Wanneer de CIM-opdracht in de sessie als een functie wordt geïmporteerd, wordt in Windows Power shell een sleutel woord met de @no__t 0 toegevoegd aan de functie definitie die de functie koppelt aan een XML-Help-bestand met de naam van het CDXML-bestand waarin de CIM-opdracht is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="a7d67-129">Help-bestanden voor de script werk stroom</span><span class="sxs-lookup"><span data-stu-id="a7d67-129">Script Workflow Help Files</span></span>

<span data-ttu-id="a7d67-130">Script werk stromen die zijn opgenomen in modules kunnen worden gedocumenteerd in Help-bestanden op basis van XML.</span><span class="sxs-lookup"><span data-stu-id="a7d67-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="a7d67-131">Er zijn geen technische vereisten voor de naam van het Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="a7d67-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="a7d67-132">Een best practice heeft echter de naam van het Help-bestand voor de script module waarin de werk stroom van het script is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="a7d67-133">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a7d67-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="a7d67-134">In tegens telling tot andere script opdrachten, is voor script werk stromen geen sleutel woord `.ExternalHelp` vereist om ze te koppelen aan een Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="a7d67-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="a7d67-135">In plaats daarvan zoekt Windows Power shell de specifieke submappen voor de gebruikers interface van de module directory voor Help-bestanden op basis van XML en zoekt de hulp voor de script werk stroom in alle bestanden.</span><span class="sxs-lookup"><span data-stu-id="a7d67-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="a7d67-136">het tref woord `.ExternalHelp` opmerking wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a7d67-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="a7d67-137">Omdat het sleutel woord `.ExternalHelp` wordt genegeerd, kan de cmdlet `Get-Help` alleen hulp voor script werk stromen vinden als deze in modules zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="a7d67-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>