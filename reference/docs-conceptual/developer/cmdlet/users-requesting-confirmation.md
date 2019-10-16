---
title: Gebruikers vragen om bevestiging | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359154"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="5cb8b-102">Gebruikers die bevestiging vragen</span><span class="sxs-lookup"><span data-stu-id="5cb8b-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="5cb8b-103">Wanneer u de waarde `true` opgeeft voor de para meter `SupportsShouldProcess` van de kenmerk declaratie van de cmdlet, kunnen gebruikers de para meter `Confirm` opgeven bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="5cb8b-104">In de standaard omgeving kunnen gebruikers de para meter `Confirm` of `"-Confirm:$true` opgeven, zodat er een bevestiging wordt gevraagd wanneer de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="5cb8b-105">Dit omzeilt [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -bevestigings aanvragen, zelfs voor bewerkingen met een hoge impact.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="5cb8b-106">Als `Confirm` niet is opgegeven, wordt met de aanroep aangevraagd [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) als de `$ConfirmPreference`-voorkeurs variabele gelijk is aan of groter is dan de `ConfirmImpact`-instelling van de cmdlet of provider.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="5cb8b-107">De standaard instelling van `$ConfirmPreference` is hoog.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="5cb8b-108">In de standaard omgeving worden alleen cmdlets en providers vermeld waarmee een bevestiging van een actie aanvraag met hoge impact wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="5cb8b-109">Als `Confirm` false is of als `"-Confirm:$false` is opgegeven, wordt met de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de bevestiging van de gebruiker aangevraagd en wordt de `$ConfirmPreference`-shell variabele genegeerd.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cb8b-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5cb8b-110">Remarks</span></span>

- <span data-ttu-id="5cb8b-111">Voor cmdlets en providers die `SupportsShouldProcess` opgeven, maar niet `ConfirmImpact`, worden deze acties behandeld als ' gemiddelde impact ' acties en worden ze niet standaard gevraagd.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="5cb8b-112">Het effect niveau is lager dan de standaard instelling van de voorkeurs variabele `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="5cb8b-113">Als de gebruiker de para meter `Verbose` opgeeft, worden deze op de hoogte gesteld van de bewerking, zelfs als ze niet worden gevraagd om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="5cb8b-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cb8b-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5cb8b-114">See Also</span></span>

[<span data-ttu-id="5cb8b-115">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="5cb8b-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
