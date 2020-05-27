---
title: Een Windows Power shell-module maken | Microsoft Docs
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
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809957"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="d53ab-102">Een Windows PowerShell-module maken</span><span class="sxs-lookup"><span data-stu-id="d53ab-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="d53ab-103">Een Windows Power shell-module biedt een mechanisme voor het registreren van sets cmdlets en een andere Windows Power shell-provider met de shell, waardoor de functionaliteit van de shell wordt uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="d53ab-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="d53ab-104">Een Windows Power shell-module kan alle cmdlets en providers in één assembly registreren, of kan een specifieke lijst met cmdlets en providers registreren.</span><span class="sxs-lookup"><span data-stu-id="d53ab-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="d53ab-105">Module-assembly's moeten worden geïnstalleerd in een beveiligde map, net als bij andere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="d53ab-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="d53ab-106">Als dat niet het geval is, kunnen kwaadwillende gebruikers een assembly vervangen door onveilige code.</span><span class="sxs-lookup"><span data-stu-id="d53ab-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="d53ab-107">Windows Power shell-module klassen</span><span class="sxs-lookup"><span data-stu-id="d53ab-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="d53ab-108">Alle Windows Power shell-module klassen worden afgeleid van de klassen [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) of [System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="d53ab-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="d53ab-109">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d53ab-109">Examples</span></span>

<span data-ttu-id="d53ab-110">[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-snap-in.md): in dit voor beeld ziet u hoe u een module maakt die wordt gebruikt voor het registreren van alle cmdlets en providers in een assembly.</span><span class="sxs-lookup"><span data-stu-id="d53ab-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="d53ab-111">[Een aangepaste Windows Power shell-module schrijven](./writing-a-custom-windows-powershell-snap-in.md): in dit voor beeld ziet u hoe u een aangepaste module maakt die wordt gebruikt voor het registreren van een specifieke set cmdlets en providers die mogelijk niet in één assembly bestaan of aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="d53ab-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d53ab-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d53ab-112">See Also</span></span>

[<span data-ttu-id="d53ab-113">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="d53ab-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="d53ab-114">System. Management. Automation. Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="d53ab-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="d53ab-115">Cmdlets registreren</span><span class="sxs-lookup"><span data-stu-id="d53ab-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="d53ab-116">Windows Power shell shell SDK</span><span class="sxs-lookup"><span data-stu-id="d53ab-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)