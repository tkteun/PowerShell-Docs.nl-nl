---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc-zelfstudie
description: GetProc-zelfstudie
ms.openlocfilehash: 9379e791dd5361fcf5b79061bf0a601ebeb84f42
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652776"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="f97fa-103">GetProc-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="f97fa-103">GetProc Tutorial</span></span>

<span data-ttu-id="f97fa-104">Deze sectie bevat een zelf studie voor het maken van een Get-Proc-cmdlet die vergelijkbaar is met de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="f97fa-104">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="f97fa-105">Deze zelf studie bevat fragmenten van code die illustreert hoe cmdlets worden geïmplementeerd en een uitleg van de code.</span><span class="sxs-lookup"><span data-stu-id="f97fa-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="f97fa-106">Onderwerpen in deze zelf studie</span><span class="sxs-lookup"><span data-stu-id="f97fa-106">Topics in this Tutorial</span></span>

<span data-ttu-id="f97fa-107">De onderwerpen in deze zelf studie zijn zodanig ontworpen dat ze opeenvolgend worden gelezen, met elk onderwerp dat is gebaseerd op wat in het vorige onderwerp is besproken.</span><span class="sxs-lookup"><span data-stu-id="f97fa-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="f97fa-108">[Een cmdlet zonder para meters maken](./creating-a-cmdlet-without-parameters.md) In deze sectie wordt beschreven hoe u een cmdlet maakt waarmee informatie wordt opgehaald van de lokale computer zonder het gebruik van para meters, en vervolgens de informatie naar de pijp lijn schrijft.</span><span class="sxs-lookup"><span data-stu-id="f97fa-108">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f97fa-109">[Para meters toevoegen die Command-Line invoer verwerken](./adding-parameters-that-process-command-line-input.md) In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de Get-Proc cmdlet, zodat de cmdlet invoer kan verwerken op basis van expliciete objecten die worden door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f97fa-109">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="f97fa-110">De implementatie die hier wordt beschreven, haalt processen op basis van hun naam en schrijft vervolgens de informatie naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f97fa-110">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f97fa-111">[Para meters toevoegen die de invoer van de pijp lijn verwerken](./adding-parameters-that-process-pipeline-input.md) In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de Get-Proc-cmdlet, zodat de cmdlet objecten kan verwerken die worden door gegeven via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f97fa-111">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="f97fa-112">De implementatie-cmdlet die hier wordt beschreven, haalt processen op basis van objecten die zijn door gegeven aan de cmdlet en schrijft de informatie vervolgens naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f97fa-112">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="f97fa-113">[Fout rapportage voor niet-afsluiting aan uw cmdlet toevoegen](./adding-non-terminating-error-reporting-to-your-cmdlet.md) In deze sectie wordt beschreven hoe u niet-afsluit fout rapportage aan een cmdlet toevoegt.</span><span class="sxs-lookup"><span data-stu-id="f97fa-113">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="f97fa-114">De hier beschreven implementatie detecteert niet-afsluit fouten die optreden bij het verwerken van de invoer en schrijft een fout record naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="f97fa-114">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="f97fa-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f97fa-115">See Also</span></span>

[<span data-ttu-id="f97fa-116">Een cmdlet maken zonder parameters</span><span class="sxs-lookup"><span data-stu-id="f97fa-116">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="f97fa-117">Para meters toevoegen die Command-Line invoer verwerken</span><span class="sxs-lookup"><span data-stu-id="f97fa-117">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f97fa-118">Parameters toevoegen die pijplijninvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="f97fa-118">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="f97fa-119">Fout rapportage voor niet-afsluiting aan uw cmdlet toevoegen</span><span class="sxs-lookup"><span data-stu-id="f97fa-119">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="f97fa-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f97fa-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
