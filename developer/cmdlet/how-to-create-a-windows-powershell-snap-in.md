---
title: Over het maken van een PowerShell-module Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849439"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="3b1a9-102">Een Windows PowerShell-module maken</span><span class="sxs-lookup"><span data-stu-id="3b1a9-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="3b1a9-103">Een Windows PowerShell-module biedt een mechanisme voor het registreren van sets met cmdlets en een andere Windows PowerShell-provider met de shell, dus het uitbreiden van de functionaliteit van de shell.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="3b1a9-104">Een Windows PowerShell-module kan de cmdlets en providers in een enkele assembly, het kunt registreren of een specifieke lijst met cmdlets en providers.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="3b1a9-105">Module-assembly's moeten worden geïnstalleerd in een beveiligde map, net zoals met andere besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="3b1a9-106">Anders kunnen kwaadwillende gebruikers een assembly vervangen door onveilige code.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="3b1a9-107">Windows PowerShell-module klassen</span><span class="sxs-lookup"><span data-stu-id="3b1a9-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="3b1a9-108">Alle Windows PowerShell-module-klassen die zijn afgeleid van de [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) of [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klassen.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="3b1a9-109">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="3b1a9-109">Examples</span></span>

<span data-ttu-id="3b1a9-110">[Schrijven van een PowerShell-module Windows](./writing-a-windows-powershell-snap-in.md): Dit voorbeeld toont het maken van een module die wordt gebruikt voor het registreren van de cmdlets en providers in een assembly.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="3b1a9-111">[Schrijven van aangepaste Windows PowerShell module](./writing-a-custom-windows-powershell-snap-in.md): Dit voorbeeld laat zien hoe u een aangepaste module die wordt gebruikt voor het registreren van een specifieke set cmdlets en providers die kunnen of bestaat mogelijk niet in een enkele assembly maakt.</span><span class="sxs-lookup"><span data-stu-id="3b1a9-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b1a9-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3b1a9-112">See Also</span></span>

[<span data-ttu-id="3b1a9-113">System.Management.Automation.Pssnapin</span><span class="sxs-lookup"><span data-stu-id="3b1a9-113">System.Management.Automation.Pssnapin</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="3b1a9-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="3b1a9-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="3b1a9-115">Cmdlets registreren</span><span class="sxs-lookup"><span data-stu-id="3b1a9-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="3b1a9-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="3b1a9-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
