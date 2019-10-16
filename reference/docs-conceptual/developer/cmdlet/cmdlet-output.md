---
title: Cmdlet-uitvoer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356579"
---
# <a name="cmdlet-output"></a><span data-ttu-id="76f0e-102">Cmdlet-uitvoer</span><span class="sxs-lookup"><span data-stu-id="76f0e-102">Cmdlet Output</span></span>

<span data-ttu-id="76f0e-103">In deze sectie worden de typen cmdlet-uitvoer en de methoden beschreven die cmdlets kunnen aanroepen om uitvoer te genereren, zoals fout berichten en objecten.</span><span class="sxs-lookup"><span data-stu-id="76f0e-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="76f0e-104">In deze sectie wordt ook beschreven hoe u de .NET Framework typen definieert die worden geretourneerd door uw cmdlets en hoe deze objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="76f0e-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="76f0e-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="76f0e-105">In This Section</span></span>

<span data-ttu-id="76f0e-106">[Typen cmdlet-uitvoer](./types-of-cmdlet-output.md) Beschrijft de typen en uitvoer die cmdlets kunnen genereren en de methoden die cmdlets aanroepen om de uitvoer te genereren.</span><span class="sxs-lookup"><span data-stu-id="76f0e-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="76f0e-107">[Fout rapportage voor cmdlets](./cmdlet-error-reporting.md) Beschrijft cmdlet-fout rapportage, een subset van cmdlet-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="76f0e-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="76f0e-108">[Uitvoer objecten uitbreiden](./extending-output-objects.md) In dit artikel wordt beschreven hoe u de typen bestanden (. ps1xml) gebruikt om de .NET Framework objecten uit te breiden die worden geretourneerd door cmdlets, functions en scripts.</span><span class="sxs-lookup"><span data-stu-id="76f0e-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="76f0e-109">[Power shell-indelings bestanden](../format/powershell-formatting-files.md) Hierin worden de indelings bestanden (. Format. ps1xml) beschreven waarmee de standaard weergave voor een specifieke set .NET Framework-objecten in Windows Power shell wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="76f0e-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="76f0e-110">[Aangepaste indelings bestanden](./custom-formatting-files.md) Hierin wordt beschreven hoe u uw eigen aangepaste indelings bestanden maakt om de standaard notaties te overschrijven of om de weer gave van objecten te definiëren die door uw eigen opdrachten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="76f0e-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="76f0e-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="76f0e-111">See Also</span></span>

[<span data-ttu-id="76f0e-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="76f0e-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
