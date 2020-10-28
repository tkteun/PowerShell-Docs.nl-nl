---
ms.date: 09/13/2016
ms.topic: reference
title: Concepten voor Windows PowerShell-cmdlets
description: Concepten voor Windows PowerShell-cmdlets
ms.openlocfilehash: da34d3d229f6d57ee22d84fc024b31eb2ee27ba3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652523"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="37fd8-103">Concepten voor Windows PowerShell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="37fd8-103">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="37fd8-104">In deze sectie wordt beschreven hoe cmdlets werken.</span><span class="sxs-lookup"><span data-stu-id="37fd8-104">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="37fd8-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="37fd8-105">In This Section</span></span>

<span data-ttu-id="37fd8-106">Deze sectie bevat de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="37fd8-106">This section includes the following topics.</span></span>

<span data-ttu-id="37fd8-107">[Richt lijnen voor het ontwikkelen van cmdlets](./cmdlet-development-guidelines.md) Dit onderwerp bevat richt lijnen voor ontwikkel aars die kunnen worden gebruikt voor het produceren van goed opgemaakte cmdlets.</span><span class="sxs-lookup"><span data-stu-id="37fd8-107">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="37fd8-108">[Declaratie](./cmdlet-class-declaration.md) van de cmdlet-klasse In dit onderwerp wordt de klasse-declaratie van de cmdlet beschreven.</span><span class="sxs-lookup"><span data-stu-id="37fd8-108">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="37fd8-109">[Goedgekeurde werk woorden voor Windows Power shell-opdrachten](./approved-verbs-for-windows-powershell-commands.md) In dit onderwerp vindt u de vooraf gedefinieerde cmdlet-termen die u kunt gebruiken bij het declareren van een cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="37fd8-109">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="37fd8-110">[Cmdlet invoer verwerkings methoden](./cmdlet-input-processing-methods.md) In dit onderwerp worden de methoden beschreven voor het uitvoeren van voor verwerking van bewerkingen, invoer bewerkingen en het verwerken van bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="37fd8-110">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="37fd8-111">[Cmdlet-para meters](./cmdlet-parameters.md) In deze sectie worden de verschillende typen para meters beschreven die u aan cmdlets kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="37fd8-111">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="37fd8-112">[Cmdlet-kenmerken](./cmdlet-attributes.md) In deze sectie worden de kenmerken beschreven die worden gebruikt voor het declareren van .NET Framework klassen als-cmdlets, het declareren van velden als cmdlet-para meters en voor het declareren van invoer validatie regels voor para meters.</span><span class="sxs-lookup"><span data-stu-id="37fd8-112">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="37fd8-113">[Cmdlet-aliassen](./cmdlet-aliases.md) In dit onderwerp worden cmdlet-aliassen beschreven.</span><span class="sxs-lookup"><span data-stu-id="37fd8-113">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="37fd8-114">[Cmdlet-uitvoer](./cmdlet-output.md) In deze sectie wordt het type uitvoer beschreven dat door cmdlets kan worden geretourneerd en hoe u de objecten die worden geretourneerd door cmdlets kunt definiëren en weer geven.</span><span class="sxs-lookup"><span data-stu-id="37fd8-114">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="37fd8-115">[Cmdlets registreren](./modules-and-snap-ins.md) In deze sectie wordt beschreven hoe u cmdlets registreert met behulp van modules en modules.</span><span class="sxs-lookup"><span data-stu-id="37fd8-115">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="37fd8-116">[Bevestiging vragen](./requesting-confirmation-from-cmdlets.md) In deze sectie wordt beschreven hoe u met cmdlets een bevestiging van een gebruiker vraagt voordat u een wijziging in het systeem aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="37fd8-116">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="37fd8-117">[Windows Power Shell-fout rapportage](./error-reporting-concepts.md) In deze sectie wordt beschreven hoe u met cmdlets fouten en niet-afsluit fouten rapporteert, en wordt beschreven hoe u fout records kunt interpreteren.</span><span class="sxs-lookup"><span data-stu-id="37fd8-117">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="37fd8-118">[Achtergrond taken](./background-jobs.md) In dit onderwerp wordt beschreven hoe cmdlets hun werk kunnen uitvoeren binnen achtergrond taken die de opdrachten die in de huidige sessie worden uitgevoerd, niet verstoren.</span><span class="sxs-lookup"><span data-stu-id="37fd8-118">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="37fd8-119">[Cmdlets en scripts binnen een cmdlet aanroepen](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) In dit onderwerp wordt beschreven hoe cmdlets andere cmdlets en scripts kunnen aanroepen vanuit hun invoer methoden.</span><span class="sxs-lookup"><span data-stu-id="37fd8-119">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="37fd8-120">[Cmdlet-sets](./cmdlet-sets.md) In dit onderwerp wordt beschreven hoe u basis klassen gebruikt voor het maken van sets cmdlets.</span><span class="sxs-lookup"><span data-stu-id="37fd8-120">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="37fd8-121">[Windows Power shell-sessie status](./windows-powershell-session-state.md) In dit onderwerp wordt de Windows Power shell-sessie status beschreven.</span><span class="sxs-lookup"><span data-stu-id="37fd8-121">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
