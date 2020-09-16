---
title: Zelf studie voor GetProc | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cc99cb4de8e3b8fcab8eac28b21162764aecd8a1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784262"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="ff98e-102">GetProc-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="ff98e-102">GetProc Tutorial</span></span>

<span data-ttu-id="ff98e-103">Deze sectie bevat een zelf studie voor het maken van een Get-proc-cmdlet die vergelijkbaar is met de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="ff98e-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="ff98e-104">Deze zelf studie bevat fragmenten van code die illustreert hoe cmdlets worden geïmplementeerd en een uitleg van de code.</span><span class="sxs-lookup"><span data-stu-id="ff98e-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="ff98e-105">Onderwerpen in deze zelf studie</span><span class="sxs-lookup"><span data-stu-id="ff98e-105">Topics in this Tutorial</span></span>

<span data-ttu-id="ff98e-106">De onderwerpen in deze zelf studie zijn zodanig ontworpen dat ze opeenvolgend worden gelezen, met elk onderwerp dat is gebaseerd op wat in het vorige onderwerp is besproken.</span><span class="sxs-lookup"><span data-stu-id="ff98e-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="ff98e-107">[Een cmdlet zonder para meters maken](./creating-a-cmdlet-without-parameters.md) In deze sectie wordt beschreven hoe u een cmdlet maakt waarmee informatie wordt opgehaald van de lokale computer zonder het gebruik van para meters, en vervolgens de informatie naar de pijp lijn schrijft.</span><span class="sxs-lookup"><span data-stu-id="ff98e-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="ff98e-108">[Para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md) In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de cmdlet Get-proc, zodat de cmdlet invoer kan verwerken op basis van expliciete objecten die worden door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff98e-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="ff98e-109">De implementatie die hier wordt beschreven, haalt processen op basis van hun naam en schrijft vervolgens de informatie naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ff98e-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="ff98e-110">[Para meters toevoegen die de invoer van de pijp lijn verwerken](./adding-parameters-that-process-pipeline-input.md) In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de cmdlet Get-proc, zodat de cmdlet objecten kan verwerken die worden door gegeven via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ff98e-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="ff98e-111">De implementatie-cmdlet die hier wordt beschreven, haalt processen op basis van objecten die zijn door gegeven aan de cmdlet en schrijft de informatie vervolgens naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ff98e-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="ff98e-112">[Fout rapportage voor niet-afsluiting aan uw cmdlet toevoegen](./adding-non-terminating-error-reporting-to-your-cmdlet.md) In deze sectie wordt beschreven hoe u niet-afsluit fout rapportage aan een cmdlet toevoegt.</span><span class="sxs-lookup"><span data-stu-id="ff98e-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="ff98e-113">De hier beschreven implementatie detecteert niet-afsluit fouten die optreden bij het verwerken van de invoer en schrijft een fout record naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="ff98e-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff98e-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ff98e-114">See Also</span></span>

[<span data-ttu-id="ff98e-115">Een cmdlet maken zonder parameters</span><span class="sxs-lookup"><span data-stu-id="ff98e-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="ff98e-116">Para meters toevoegen die opdracht regel invoer verwerken</span><span class="sxs-lookup"><span data-stu-id="ff98e-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="ff98e-117">Parameters toevoegen die pijplijninvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="ff98e-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="ff98e-118">Fout rapportage voor niet-afsluiting aan uw cmdlet toevoegen</span><span class="sxs-lookup"><span data-stu-id="ff98e-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="ff98e-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ff98e-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
