---
title: Hiermee stelt u cmdlet-Parameter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068509"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="aec5c-102">Parametersets voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="aec5c-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="aec5c-103">Windows PowerShell maakt gebruik van parametersets zodat u één cmdlet die u verschillende acties voor verschillende scenario's uitvoeren kunt te schrijven.</span><span class="sxs-lookup"><span data-stu-id="aec5c-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="aec5c-104">Parametersets kunnen u om verschillende parameters, zodat de gebruiker zichtbaar te maken en om andere informatie op basis van de parameters die is opgegeven door de gebruiker te retourneren.</span><span class="sxs-lookup"><span data-stu-id="aec5c-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="aec5c-105">Voorbeelden van parametersets</span><span class="sxs-lookup"><span data-stu-id="aec5c-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="aec5c-106">Bijvoorbeeld, de `Get-EventLog` cmdlet (geleverd door Windows PowerShell) retourneert verschillende gegevens afhankelijk van of de gebruiker Hiermee geeft u de `List` of `LogName` parameter.</span><span class="sxs-lookup"><span data-stu-id="aec5c-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="aec5c-107">Als de `List` parameter is opgegeven, wordt de cmdlet retourneert informatie over de logboekbestanden zelf, maar niet de gebeurtenisgegevens die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="aec5c-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="aec5c-108">Als de `LogName` parameter is opgegeven, wordt de cmdlet retourneert informatie over de gebeurtenissen in een specifiek gebeurtenislogboek.</span><span class="sxs-lookup"><span data-stu-id="aec5c-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="aec5c-109">De `List` en `LogName` parameters identificeren twee afzonderlijke parametersets.</span><span class="sxs-lookup"><span data-stu-id="aec5c-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="aec5c-110">De unieke Parameter</span><span class="sxs-lookup"><span data-stu-id="aec5c-110">Unique Parameter</span></span>

<span data-ttu-id="aec5c-111">Elke parameter is ingesteld, moet een unieke parameter die de Windows PowerShell-runtime gebruiken kunt om de juiste parameterset beschikbaar te hebben.</span><span class="sxs-lookup"><span data-stu-id="aec5c-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="aec5c-112">De unieke parameter moet indien mogelijk een verplichte parameter.</span><span class="sxs-lookup"><span data-stu-id="aec5c-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="aec5c-113">Als een parameter verplicht is, wordt de gebruiker wordt gedwongen om op te geven van de parameter en de Windows PowerShell-runtime kunt deze parameter gebruiken om te identificeren van de parameter is ingesteld om te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aec5c-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="aec5c-114">De unieke parameter mag niet verplicht als u de cmdlet is ontworpen om te worden uitgevoerd zonder parameters op te geven.</span><span class="sxs-lookup"><span data-stu-id="aec5c-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="aec5c-115">Meerdere parametersets</span><span class="sxs-lookup"><span data-stu-id="aec5c-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="aec5c-116">In de volgende afbeelding ziet u in de linkerkolom drie geldig parametersets.</span><span class="sxs-lookup"><span data-stu-id="aec5c-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="aec5c-117">Parameter een uniek is voor de eerste parameter is ingesteld, parameter B uniek is voor de tweede parameter is ingesteld en parameter C uniek is voor de derde parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="aec5c-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="aec5c-118">Echter, in de rechterkolom de parametersets geen een unieke parameter.</span><span class="sxs-lookup"><span data-stu-id="aec5c-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="aec5c-120">Parameter vereisten instellen</span><span class="sxs-lookup"><span data-stu-id="aec5c-120">Parameter Set Requirements</span></span>

<span data-ttu-id="aec5c-121">De volgende vereisten zijn van toepassing op alle parametersets.</span><span class="sxs-lookup"><span data-stu-id="aec5c-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="aec5c-122">Elke parameter is ingesteld, moet ten minste één unieke parameter hebben.</span><span class="sxs-lookup"><span data-stu-id="aec5c-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="aec5c-123">Indien mogelijk, maken deze parameter een verplichte parameter.</span><span class="sxs-lookup"><span data-stu-id="aec5c-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="aec5c-124">Een parameterset waarin meerdere positionele parameters moet unieke functies voor alle parameters definiëren.</span><span class="sxs-lookup"><span data-stu-id="aec5c-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="aec5c-125">Er zijn geen twee positionele parameters kunnen dezelfde positie opgeven.</span><span class="sxs-lookup"><span data-stu-id="aec5c-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="aec5c-126">Slechts één parameter in een set kunt declareren de `ValueFromPipeline` sleutelwoord met de waarde `true`.</span><span class="sxs-lookup"><span data-stu-id="aec5c-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="aec5c-127">Meerdere parameters kunnen definiëren de `ValueFromPipelineByPropertyName` sleutelwoord met de waarde `true`.</span><span class="sxs-lookup"><span data-stu-id="aec5c-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="aec5c-128">Als er geen parameter is ingesteld voor een parameter is opgegeven, wordt de parameter hoort bij alle parametersets.</span><span class="sxs-lookup"><span data-stu-id="aec5c-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="aec5c-129">Standaard parametersets</span><span class="sxs-lookup"><span data-stu-id="aec5c-129">Default Parameter Sets</span></span>

<span data-ttu-id="aec5c-130">Wanneer er meerdere parametersets zijn gedefinieerd, kunt u de `DefaultParameterSetName` het kenmerk Cmdlet om op te geven van de standaardset van de parameter door u opgegeven trefwoord.</span><span class="sxs-lookup"><span data-stu-id="aec5c-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="aec5c-131">Windows PowerShell maakt gebruik van de standaardparameter ingesteld als deze niet kan bepalen de parameter is ingesteld om te gebruiken op basis van de informatie die door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="aec5c-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="aec5c-132">Zie voor meer informatie over de Cmdlet-kenmerk [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="aec5c-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="aec5c-133">Parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="aec5c-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="aec5c-134">Voor het maken van een parameter is ingesteld, moet u de `ParameterSetName` sleutelwoord wanneer u de Parameter-kenmerk voor elke parameter in de parameterset declareren.</span><span class="sxs-lookup"><span data-stu-id="aec5c-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="aec5c-135">Voor de parameters die deel uitmaken van meerdere parametersets, Voeg een parameterkenmerk voor elke parameter ingesteld.</span><span class="sxs-lookup"><span data-stu-id="aec5c-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="aec5c-136">Hiermee kunt u voor het definiëren van de parameter anders voor elke parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="aec5c-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="aec5c-137">U kunt bijvoorbeeld een parameter definiëren als in één set verplichte en optionele in een andere.</span><span class="sxs-lookup"><span data-stu-id="aec5c-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="aec5c-138">Elke parameter is ingesteld, moet echter een unieke parameter bevatten.</span><span class="sxs-lookup"><span data-stu-id="aec5c-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="aec5c-139">In het volgende voorbeeld wordt de `UserName` parameter is de unieke parameter van de parameterset Test01 en de `ComputerName` parameter is de unieke parameter van de parameterset Test02.</span><span class="sxs-lookup"><span data-stu-id="aec5c-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="aec5c-140">De `SharedParam` parameter behoort tot beide sets en is verplicht voor de parameter Test01 is ingesteld, maar voor de parameterset Test02 optioneel.</span><span class="sxs-lookup"><span data-stu-id="aec5c-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```