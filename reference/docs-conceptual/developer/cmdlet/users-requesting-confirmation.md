---
ms.date: 09/13/2016
ms.topic: reference
title: Gebruikers die bevestiging vragen
description: Gebruikers die bevestiging vragen
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646304"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="72199-103">Gebruikers die bevestiging vragen</span><span class="sxs-lookup"><span data-stu-id="72199-103">Users Requesting Confirmation</span></span>

<span data-ttu-id="72199-104">Wanneer u een waarde van opgeeft `true` voor de `SupportsShouldProcess` para meter van de cmdlet-kenmerk declaratie, kunnen gebruikers de `Confirm` para meter opgeven bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="72199-104">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="72199-105">In de standaard omgeving kunnen gebruikers de `Confirm` para meter opgeven of `"-Confirm:$true` ervoor zorgen dat er een bevestiging wordt gevraagd wanneer de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="72199-105">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="72199-106">Dit omzeilt [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -bevestigings aanvragen, zelfs voor bewerkingen met een hoge impact.</span><span class="sxs-lookup"><span data-stu-id="72199-106">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="72199-107">Als `Confirm` niet is opgegeven, wordt met de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) een bevestiging gevraagd als de `$ConfirmPreference` Voorkeurs variabele gelijk is aan of groter is dan de `ConfirmImpact` instelling van de cmdlet of provider.</span><span class="sxs-lookup"><span data-stu-id="72199-107">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="72199-108">De standaard instelling `$ConfirmPreference` is hoog.</span><span class="sxs-lookup"><span data-stu-id="72199-108">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="72199-109">In de standaard omgeving worden alleen cmdlets en providers vermeld waarmee een bevestiging van een actie aanvraag met hoge impact wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="72199-109">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="72199-110">Als `Confirm` is ingesteld op False of als `"-Confirm:$false` is opgegeven, wordt voor de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) een bevestiging van de gebruiker aangevraagd en `$ConfirmPreference` wordt de shell-variabele genegeerd.</span><span class="sxs-lookup"><span data-stu-id="72199-110">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="72199-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="72199-111">Remarks</span></span>

- <span data-ttu-id="72199-112">Voor cmdlets en providers die `SupportsShouldProcess` , maar niet worden opgegeven, `ConfirmImpact` worden deze acties verwerkt als ' gemiddelde impact ' acties en worden ze niet standaard gevraagd.</span><span class="sxs-lookup"><span data-stu-id="72199-112">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="72199-113">Het effect niveau is lager dan de standaard instelling van de `$ConfirmPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="72199-113">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="72199-114">Als de gebruiker de `Verbose` para meter opgeeft, wordt deze op de hoogte gesteld van de bewerking, zelfs als ze niet om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="72199-114">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="72199-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="72199-115">See Also</span></span>

[<span data-ttu-id="72199-116">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="72199-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
