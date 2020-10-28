---
ms.date: 09/13/2016
ms.topic: reference
title: StopProc-zelfstudie
description: StopProc-zelfstudie
ms.openlocfilehash: 95229ee3c4905d295bd6991fe8ccf8c9840c3cdd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646443"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="e5a58-103">StopProc-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="e5a58-103">StopProc Tutorial</span></span>

<span data-ttu-id="e5a58-104">In deze sectie vindt u een zelf studie voor het maken van de Stop-Proc-cmdlet, die vergelijkbaar is met de [Stop-process-](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a58-104">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="e5a58-105">Deze zelf studie bevat fragmenten van code die illustreert hoe cmdlets worden geïmplementeerd en een uitleg van de code.</span><span class="sxs-lookup"><span data-stu-id="e5a58-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="e5a58-106">Onderwerpen in deze zelf studie</span><span class="sxs-lookup"><span data-stu-id="e5a58-106">Topics in this Tutorial</span></span>

<span data-ttu-id="e5a58-107">De onderwerpen in deze zelf studie zijn zodanig ontworpen dat ze opeenvolgend worden gelezen, met elk onderwerp dat is gebaseerd op wat in het vorige onderwerp is besproken.</span><span class="sxs-lookup"><span data-stu-id="e5a58-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="e5a58-108">[Een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md) In deze sectie wordt beschreven hoe u een cmdlet maakt die systeem wijzigingen ondersteunt, zoals het stoppen van een proces dat wordt uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="e5a58-108">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="e5a58-109">[Gebruikers berichten toevoegen aan uw cmdlet](./adding-user-messages-to-your-cmdlet.md) In deze sectie wordt beschreven hoe u de mogelijkheid om gebruikers berichten, fout berichten, waarschuwings berichten en voortgangs gegevens te schrijven naar uw cmdlet kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e5a58-109">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="e5a58-110">[Aliassen, uitbrei ding van joker tekens en Help voor cmdlet-para meters toevoegen](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) In deze sectie wordt beschreven hoe u een cmdlet maakt die parameter aliassen, Help en het uitbreiden van joker tekens ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="e5a58-110">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="e5a58-111">[Parameter sets toevoegen aan cmdlets](./adding-parameter-sets-to-a-cmdlet.md) In deze sectie wordt beschreven hoe u parameter sets toevoegt aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5a58-111">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="e5a58-112">Met parameter sets kan de cmdlet anders worden uitgevoerd op basis van de para meters die door de gebruiker zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e5a58-112">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a58-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5a58-113">See Also</span></span>

[<span data-ttu-id="e5a58-114">Een cmdlet maken waarmee het systeem wordt gewijzigd</span><span class="sxs-lookup"><span data-stu-id="e5a58-114">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="e5a58-115">Gebruikersberichten toevoegen aan uw cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5a58-115">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="e5a58-116">Aliassen, jokertekenuitbreiding en Help toevoegen aan cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="e5a58-116">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="e5a58-117">Parameter sets toevoegen aan cmdlets</span><span class="sxs-lookup"><span data-stu-id="e5a58-117">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="e5a58-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e5a58-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
