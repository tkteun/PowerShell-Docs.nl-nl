---
title: GetProc-zelfstudie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068093"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="70462-102">GetProc-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="70462-102">GetProc Tutorial</span></span>

<span data-ttu-id="70462-103">In deze sectie bevat een zelfstudie voor het maken van een cmdlet Get-Proc die is vergelijkbaar met de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) geleverd door Windows PowerShell cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70462-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="70462-104">Deze zelfstudie bevat codefragmenten die laten zien hoe de cmdlets worden geïmplementeerd en een uitleg van de code.</span><span class="sxs-lookup"><span data-stu-id="70462-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="70462-105">Onderwerpen in deze zelfstudie</span><span class="sxs-lookup"><span data-stu-id="70462-105">Topics in this Tutorial</span></span>

<span data-ttu-id="70462-106">De onderwerpen in deze zelfstudie zijn ontworpen om te worden opeenvolgend gelezen met elk onderwerp bouwen op wat is besproken in het vorige onderwerp.</span><span class="sxs-lookup"><span data-stu-id="70462-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="70462-107">[Het maken van een Cmdlet zonder Parameters](./creating-a-cmdlet-without-parameters.md) in deze sectie wordt beschreven hoe u een cmdlet die wordt informatie opgehaald uit de lokale computer zonder het gebruik van parameters en vervolgens schrijft de informatie in de pijplijn te maken.</span><span class="sxs-lookup"><span data-stu-id="70462-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="70462-108">[Dat proces Command-Line invoer Parameters toe te voegen](./adding-parameters-that-process-command-line-input.md) in deze sectie wordt beschreven hoe u een parameter toevoegen aan de cmdlet Get-Proc dat invoer op basis van expliciete objecten die zijn doorgegeven aan de cmdlet kan worden verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70462-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="70462-109">De implementatie dan beschreven staat hier haalt processen op basis van hun naam en vervolgens schrijft de informatie in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="70462-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="70462-110">[Parameters die invoer van de pijplijn proces toe te voegen](./adding-parameters-that-process-pipeline-input.md) in deze sectie wordt beschreven hoe u een parameter toevoegen aan de cmdlet Get-Proc zodat de cmdlet objecten die worden doorgegeven via de pijplijn kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="70462-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="70462-111">De implementatie-cmdlet beschreven hier opgehaald op basis van objecten die zijn doorgegeven aan de cmdlet processen, en vervolgens schrijft de informatie in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="70462-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="70462-112">[Nonterminating foutrapportage toevoegen aan uw Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) in deze sectie wordt beschreven hoe u om toe te voegen nonterminating die fouten rapporteren aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70462-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="70462-113">De hier beschreven implementatie detecteert afsluitfouten die optreden bij het verwerken van invoer en een foutrecord schrijft naar de foutstroom.</span><span class="sxs-lookup"><span data-stu-id="70462-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="70462-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="70462-114">See Also</span></span>

[<span data-ttu-id="70462-115">Het maken van een Cmdlet zonder Parameters</span><span class="sxs-lookup"><span data-stu-id="70462-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="70462-116">Parameters die opdrachtregel verwerken toe te voegen</span><span class="sxs-lookup"><span data-stu-id="70462-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="70462-117">Parameters die proces Pipeline ingevoerd toe te voegen</span><span class="sxs-lookup"><span data-stu-id="70462-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="70462-118">Nonterminating die fouten rapporteren aan uw Cmdlet toe te voegen</span><span class="sxs-lookup"><span data-stu-id="70462-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="70462-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="70462-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
