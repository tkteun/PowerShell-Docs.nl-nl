---
title: Zelf studie voor StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359229"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="968af-102">StopProc-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="968af-102">StopProc Tutorial</span></span>

<span data-ttu-id="968af-103">Deze sectie bevat een zelf studie voor het maken van de cmdlet stop-proc, die vergelijkbaar is met de [Stop-process-](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="968af-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="968af-104">Deze zelf studie bevat fragmenten van code die illustreert hoe cmdlets worden geïmplementeerd en een uitleg van de code.</span><span class="sxs-lookup"><span data-stu-id="968af-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="968af-105">Onderwerpen in deze zelf studie</span><span class="sxs-lookup"><span data-stu-id="968af-105">Topics in this Tutorial</span></span>

<span data-ttu-id="968af-106">De onderwerpen in deze zelf studie zijn zodanig ontworpen dat ze opeenvolgend worden gelezen, met elk onderwerp dat is gebaseerd op wat in het vorige onderwerp is besproken.</span><span class="sxs-lookup"><span data-stu-id="968af-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="968af-107">[Een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md) In deze sectie wordt beschreven hoe u een cmdlet maakt die systeem wijzigingen ondersteunt, zoals het stoppen van een proces dat wordt uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="968af-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="968af-108">[Gebruikers berichten toevoegen aan uw cmdlet](./adding-user-messages-to-your-cmdlet.md) In deze sectie wordt beschreven hoe u de mogelijkheid om gebruikers berichten, fout berichten, waarschuwings berichten en voortgangs gegevens te schrijven naar uw cmdlet kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="968af-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="968af-109">[Aliassen, uitbrei ding van joker tekens en Help voor cmdlet-para meters toevoegen](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) In deze sectie wordt beschreven hoe u een cmdlet maakt die parameter aliassen, Help en het uitbreiden van joker tekens ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="968af-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="968af-110">[Parameter sets toevoegen aan cmdlets](./adding-parameter-sets-to-a-cmdlet.md) In deze sectie wordt beschreven hoe u parameter sets toevoegt aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="968af-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="968af-111">Met parameter sets kan de cmdlet anders worden uitgevoerd op basis van de para meters die door de gebruiker zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="968af-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="968af-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="968af-112">See Also</span></span>

[<span data-ttu-id="968af-113">Een cmdlet maken die het systeem wijzigt</span><span class="sxs-lookup"><span data-stu-id="968af-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="968af-114">Gebruikers berichten toevoegen aan uw cmdlet</span><span class="sxs-lookup"><span data-stu-id="968af-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="968af-115">Aliassen, uitbrei ding van joker tekens en Help voor cmdlet-para meters toevoegen</span><span class="sxs-lookup"><span data-stu-id="968af-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="968af-116">Parameter sets toevoegen aan cmdlets</span><span class="sxs-lookup"><span data-stu-id="968af-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="968af-117">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="968af-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
