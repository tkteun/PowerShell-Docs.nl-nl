---
title: Gebruikers die aanvragen bevestiging | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067212"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="d951e-102">Gebruikers die bevestiging vragen</span><span class="sxs-lookup"><span data-stu-id="d951e-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="d951e-103">Wanneer u een waarde opgeeft `true` voor de `SupportsShouldProcess` parameter van de Cmdlet kenmerk verklaring die gebruikers kunnen opgeven de `Confirm` parameter bij de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="d951e-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="d951e-104">In de standaardomgeving, kunnen gebruikers opgeven de `Confirm` parameter of `"-Confirm:$true` zodat bevestiging wordt gevraagd wanneer de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="d951e-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="d951e-105">Dit omzeilt [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bevestiging aanvragen, zelfs voor invloedrijke bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="d951e-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="d951e-106">Als `Confirm` niet is opgegeven, de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroep vraagt om bevestiging als de `$ConfirmPreference` voorkeursvariabele is gelijk aan of groter is dan de `ConfirmImpact` instellen van de cmdlet of -provider.</span><span class="sxs-lookup"><span data-stu-id="d951e-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="d951e-107">De standaardinstelling van `$ConfirmPreference` is hoog.</span><span class="sxs-lookup"><span data-stu-id="d951e-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="d951e-108">Daarom in de standaardomgeving aanvraag alleen-cmdlets en providers die een grote impact-actie opgeeft bevestigen.</span><span class="sxs-lookup"><span data-stu-id="d951e-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="d951e-109">Als `Confirm` false is of als `"-Confirm:$false` is opgegeven, wordt de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroep vraagt om bevestiging van de gebruiker en de `$ConfirmPreference` shell-variabele wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="d951e-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="d951e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d951e-110">Remarks</span></span>

- <span data-ttu-id="d951e-111">Voor cmdlets en providers die opgeeft `SupportsShouldProcess`, maar niet `ConfirmImpact`, deze acties worden behandeld als 'normale impact' acties en ze niet standaard wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d951e-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="d951e-112">Het niveau van de impact is kleiner dan de standaardinstelling van de `$ConfirmPreference` voorkeursvariabele.</span><span class="sxs-lookup"><span data-stu-id="d951e-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="d951e-113">Als de gebruiker Hiermee geeft u de `Verbose` parameter, krijgen ze het bericht van de bewerking, zelfs als ze niet om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d951e-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="d951e-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d951e-114">See Also</span></span>

[<span data-ttu-id="d951e-115">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d951e-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
