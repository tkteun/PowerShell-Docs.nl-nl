---
title: StopProc-zelfstudie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067300"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="8d64a-102">StopProc-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="8d64a-102">StopProc Tutorial</span></span>

<span data-ttu-id="8d64a-103">Deze sectie bevat een zelfstudie voor het maken van de cmdlet Stop-Proc, dit vergelijkbaar met is de [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) geleverd door Windows PowerShell cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d64a-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="8d64a-104">Deze zelfstudie bevat codefragmenten die laten zien hoe de cmdlets worden geïmplementeerd en een uitleg van de code.</span><span class="sxs-lookup"><span data-stu-id="8d64a-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="8d64a-105">Onderwerpen in deze zelfstudie</span><span class="sxs-lookup"><span data-stu-id="8d64a-105">Topics in this Tutorial</span></span>

<span data-ttu-id="8d64a-106">De onderwerpen in deze zelfstudie zijn ontworpen om te worden opeenvolgend gelezen met elk onderwerp bouwen op wat is besproken in het vorige onderwerp.</span><span class="sxs-lookup"><span data-stu-id="8d64a-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="8d64a-107">[Het maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md) in deze sectie wordt beschreven hoe u een cmdlet die ondersteuning biedt voor wijziging van het systeem, zoals het stoppen van een proces wordt uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="8d64a-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="8d64a-108">[Berichten van de gebruiker toe te voegen aan uw Cmdlet](./adding-user-messages-to-your-cmdlet.md) in deze sectie wordt beschreven hoe u de mogelijkheid voor het schrijven van berichten van de gebruiker, Foutopsporingsberichten, waarschuwingsberichten en gegevens over de voortgang aan uw cmdlet toevoegen.</span><span class="sxs-lookup"><span data-stu-id="8d64a-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="8d64a-109">[Toevoegen van aliassen, jokertekens, en voor het tot Cmdlet-Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) in deze sectie wordt beschreven hoe u een cmdlet die ondersteuning biedt voor aliassen, Help en jokertekens maken.</span><span class="sxs-lookup"><span data-stu-id="8d64a-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="8d64a-110">[Parametersets toevoegen aan de Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) in deze sectie wordt beschreven hoe u om toe te voegen parameter wordt ingesteld op een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d64a-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="8d64a-111">Parametersets kunnen de cmdlet werken anders, afhankelijk van welke parameters zijn opgegeven door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8d64a-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d64a-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8d64a-112">See Also</span></span>

[<span data-ttu-id="8d64a-113">Het maken van een Cmdlet die Hiermee wijzigt u het systeem</span><span class="sxs-lookup"><span data-stu-id="8d64a-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="8d64a-114">Berichten van de gebruiker toe te voegen aan uw Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d64a-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="8d64a-115">Toevoegen van aliassen, jokertekens, en voor het tot Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="8d64a-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="8d64a-116">Parameter toe te voegen wordt ingesteld op Cmdlets</span><span class="sxs-lookup"><span data-stu-id="8d64a-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="8d64a-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8d64a-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
