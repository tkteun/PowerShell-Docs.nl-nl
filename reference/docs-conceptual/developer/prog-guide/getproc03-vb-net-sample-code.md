---
title: Voorbeeld code voor GetProc03 (VB.NET) | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: ad8a7b13d30b77acdaa2f5365b9b2da02aaeedce
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771920"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="c90cf-102">GetProc03-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c90cf-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="c90cf-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die de invoer van een pijp lijn kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="c90cf-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="c90cf-104">Met deze implementatie wordt een `Name` para meter gedefinieerd die de invoer van de pijp lijn accepteert, worden proces gegevens van de lokale computer opgehaald op basis van de opgegeven namen. vervolgens wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c90cf-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c90cf-105">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c90cf-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
