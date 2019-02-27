---
title: Modules en -modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849957"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="208b0-102">Modules en snap-ins</span><span class="sxs-lookup"><span data-stu-id="208b0-102">Modules and Snap-ins</span></span>

<span data-ttu-id="208b0-103">Cmdlets kunnen worden toegevoegd aan een sessie met modules (die door Windows PowerShell 2.0) of modules. Wanneer de cmdlet is toegevoegd aan de sessie die via een programma kan worden uitgevoerd op het door de hosttoepassing van een of interactief op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="208b0-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="208b0-104">U wordt aangeraden dat u modules als de leveringsmethode gebruiken voor cmdlets toe te voegen aan een sessie voor de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="208b0-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="208b0-105">Modules kunnen u cmdlets toevoegen door het laden van de assembly waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="208b0-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="208b0-106">Er is niet nodig voor het implementeren van een klasse-module.</span><span class="sxs-lookup"><span data-stu-id="208b0-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="208b0-107">Modules kunnen u andere resources, zoals variabelen, functies, scripts, typen en opmaak bestanden en meer toevoegen.</span><span class="sxs-lookup"><span data-stu-id="208b0-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="208b0-108">-Modules kunnen alleen worden gebruikt voor de cmdlets en providers toevoegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="208b0-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="208b0-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="208b0-109">See Also</span></span>

[<span data-ttu-id="208b0-110">Een Windows PowerShell-Module schrijven</span><span class="sxs-lookup"><span data-stu-id="208b0-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="208b0-111">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="208b0-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
