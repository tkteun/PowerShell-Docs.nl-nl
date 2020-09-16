---
title: Modules en modules | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787305"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="18ae4-102">Modules en snap-ins</span><span class="sxs-lookup"><span data-stu-id="18ae4-102">Modules and Snap-ins</span></span>

<span data-ttu-id="18ae4-103">Cmdlets kunnen worden toegevoegd aan een sessie met behulp van modules (geïntroduceerd door Windows Power Shell 2,0) of modules. Zodra de cmdlet is toegevoegd aan de sessie, kan de toepassing programmatisch worden uitgevoerd door een hosttoepassing of interactief op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="18ae4-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="18ae4-104">U wordt aangeraden modules te gebruiken als de leverings methode voor het toevoegen van cmdlets aan een sessie om de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="18ae4-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="18ae4-105">Met modules kunt u cmdlets toevoegen door de assembly te laden waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="18ae4-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="18ae4-106">U hoeft geen module te implementeren.</span><span class="sxs-lookup"><span data-stu-id="18ae4-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="18ae4-107">Met modules kunt u andere resources toevoegen, zoals variabelen, functies, scripts, typen en indelings bestanden, en meer.</span><span class="sxs-lookup"><span data-stu-id="18ae4-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="18ae4-108">Modules kunnen alleen worden gebruikt om cmdlets en providers toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="18ae4-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="18ae4-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="18ae4-109">See Also</span></span>

[<span data-ttu-id="18ae4-110">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="18ae4-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="18ae4-111">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="18ae4-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
