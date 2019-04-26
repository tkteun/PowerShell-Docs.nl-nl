---
title: Windows PowerShell-Cmdlet-concepten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067063"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="1c1cf-102">Concepten voor Windows PowerShell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="1c1cf-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="1c1cf-103">In deze sectie wordt beschreven hoe cmdlets werken.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1c1cf-104">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="1c1cf-104">In This Section</span></span>

<span data-ttu-id="1c1cf-105">Deze sectie bevat de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="1c1cf-105">This section includes the following topics.</span></span>

<span data-ttu-id="1c1cf-106">[Richtlijnen voor het ontwikkelen van cmdlet](./cmdlet-development-guidelines.md) dit onderwerp bevat richtlijnen voor ontwikkeling die kunnen worden gebruikt voor het produceren van opgemaakte-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="1c1cf-107">[Cmdlet klassendeclaratie](./cmdlet-class-declaration.md) in dit onderwerp wordt beschreven cmdlet klassendeclaratie.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="1c1cf-108">[Goedgekeurde werkwoorden voor Windows PowerShell-opdrachten](./approved-verbs-for-windows-powershell-commands.md) in dit onderwerp vindt u de vooraf gedefinieerde cmdlet-woorden die u gebruiken kunt wanneer u een cmdlet-klasse declareren.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="1c1cf-109">[Cmdlet verwerking invoermethoden](./cmdlet-input-processing-methods.md) in dit onderwerp beschrijft de methoden waarmee een cmdlet voorverwerking bewerkingen uitvoeren, input van bewerkingen voor de verwerking en bewerkingen voor de verwerking te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="1c1cf-110">[Cmdlet-Parameters](./cmdlet-parameters.md) in deze sectie beschrijft de verschillende typen van de parameters die u aan de cmdlets toevoegen kunt.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="1c1cf-111">[Kenmerken van de cmdlet](./cmdlet-attributes.md) in deze sectie beschrijft de kenmerken die worden gebruikt voor het .NET Framework-klassen declareren als cmdlets op te geven velden als cmdlet-parameters, en om te declareren Invoervalidatie regels voor parameters.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="1c1cf-112">[Cmdlet aliassen](./cmdlet-aliases.md) in dit onderwerp beschrijft de cmdlet-aliassen.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="1c1cf-113">[Cmdlet-uitvoer](./cmdlet-output.md) in deze sectie beschrijft het type uitvoer die cmdlets kunnen retourneren en hoe u kunt definiëren en de objecten die zijn geretourneerd door cmdlets weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="1c1cf-114">[Registreren van Cmdlets](./modules-and-snap-ins.md) in deze sectie wordt beschreven hoe u het registreren van cmdlets met behulp van modules en -modules.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="1c1cf-115">[Aanvragen van bevestiging](./requesting-confirmation-from-cmdlets.md) in deze sectie wordt beschreven hoe cmdlets aangevraagd bevestiging van een gebruiker voordat ze een wijziging in het systeem aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="1c1cf-116">[Windows PowerShell-foutrapportage](./error-reporting-concepts.md) in deze sectie wordt beschreven hoe cmdlets wordt beëindigd fouten en niet-afsluitfouten rapporteren en wordt beschreven hoe u met het interpreteren van foutrecords.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="1c1cf-117">[Achtergrondtaken](./background-jobs.md) in dit onderwerp wordt beschreven hoe cmdlets kunt uitvoeren van hun werk binnen achtergrondtaken die niet leiden tot problemen met de opdrachten die worden uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="1c1cf-118">[Aanroepen van de Cmdlets en Scripts in een Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) in dit onderwerp wordt beschreven hoe cmdlets kan aanroepen andere cmdlets en -scripts vanuit hun mening verwerkingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="1c1cf-119">[Hiermee stelt u cmdlet](./cmdlet-sets.md) in dit onderwerp wordt beschreven basisklassen gebruiken voor het maken van sets met cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="1c1cf-120">[De status van een Windows PowerShell-sessie](./windows-powershell-session-state.md) in dit onderwerp beschrijft de status van de Windows PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1c1cf-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
