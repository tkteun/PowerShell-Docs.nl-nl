---
title: Cmdlet-parameter sets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936190"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="33873-102">Cmdlet-parameter sets</span><span class="sxs-lookup"><span data-stu-id="33873-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="33873-103">Power shell gebruikt parameter sets om een enkele cmdlet te schrijven die verschillende acties voor verschillende scenario's kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="33873-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="33873-104">Met parameter sets kunt u verschillende para meters voor de gebruiker beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="33873-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="33873-105">En om andere informatie te retour neren op basis van de para meters die door de gebruiker zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="33873-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="33873-106">Voor beelden van parameter sets</span><span class="sxs-lookup"><span data-stu-id="33873-106">Examples of parameter sets</span></span>

<span data-ttu-id="33873-107">De Power shell `Get-EventLog` -cmdlet retourneert bijvoorbeeld verschillende informatie, afhankelijk van het feit of de gebruiker de para meter **List** of **LogName** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="33873-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="33873-108">Als de **List** -para meter is opgegeven, retourneert de cmdlet informatie over de logboek bestanden zelf, maar niet de gebeurtenis gegevens die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="33873-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="33873-109">Als de para meter **LogName** is opgegeven, retourneert de cmdlet informatie over de gebeurtenissen in een specifiek gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="33873-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="33873-110">De para meters **List** en **LogName** identificeren twee afzonderlijke parameter sets.</span><span class="sxs-lookup"><span data-stu-id="33873-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="33873-111">Unieke para meter</span><span class="sxs-lookup"><span data-stu-id="33873-111">Unique parameter</span></span>

<span data-ttu-id="33873-112">Elke parameterset moet een unieke para meter hebben die door de Power shell-runtime wordt gebruikt om de juiste parameterset beschikbaar te stellen.</span><span class="sxs-lookup"><span data-stu-id="33873-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="33873-113">Indien mogelijk moet de unieke para meter een verplichte para meter zijn.</span><span class="sxs-lookup"><span data-stu-id="33873-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="33873-114">Als een para meter verplicht is, moet de gebruiker de para meter opgeven en gebruikt de Power shell-runtime die para meter om de parameterset te identificeren.</span><span class="sxs-lookup"><span data-stu-id="33873-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="33873-115">De unieke para meter kan niet verplicht zijn als uw cmdlet is ontworpen om te worden uitgevoerd zonder para meters op te geven.</span><span class="sxs-lookup"><span data-stu-id="33873-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="33873-116">Meerdere parameter sets</span><span class="sxs-lookup"><span data-stu-id="33873-116">Multiple parameter sets</span></span>

<span data-ttu-id="33873-117">In de volgende afbeelding ziet u in de linkerkolom drie geldige parameter sets.</span><span class="sxs-lookup"><span data-stu-id="33873-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="33873-118">**Para meter A** is uniek voor de eerste parameterset, **para meter B** is uniek voor de tweede parameterset en **para meter C** is uniek voor de derde parameterset.</span><span class="sxs-lookup"><span data-stu-id="33873-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="33873-119">In de rechter kolom hebben de parameters sets geen unieke para meter.</span><span class="sxs-lookup"><span data-stu-id="33873-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="33873-121">Vereisten voor de parameterset</span><span class="sxs-lookup"><span data-stu-id="33873-121">Parameter set requirements</span></span>

<span data-ttu-id="33873-122">De volgende vereisten zijn van toepassing op alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="33873-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="33873-123">Elke parameterset moet ten minste één unieke para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="33873-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="33873-124">Indien mogelijk moet u voor deze para meter een verplichte para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="33873-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="33873-125">Een parameterset met meerdere positionele para meters moet unieke posities definiëren voor elke para meter.</span><span class="sxs-lookup"><span data-stu-id="33873-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="33873-126">Er kunnen niet twee positionele para meters dezelfde positie opgeven.</span><span class="sxs-lookup"><span data-stu-id="33873-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="33873-127">Slechts één para meter in een set kan het `ValueFromPipeline` tref woord declareren met `true`een waarde van.</span><span class="sxs-lookup"><span data-stu-id="33873-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="33873-128">Meerdere para meters kunnen `ValueFromPipelineByPropertyName` het sleutel woord definiëren met `true`een waarde van.</span><span class="sxs-lookup"><span data-stu-id="33873-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="33873-129">Als er geen parameterset voor een para meter is opgegeven, hoort de para meter bij alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="33873-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="33873-130">Voor een cmdlet of functie geldt een limiet van 32 parameter sets.</span><span class="sxs-lookup"><span data-stu-id="33873-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="33873-131">Standaard parameters sets</span><span class="sxs-lookup"><span data-stu-id="33873-131">Default parameter sets</span></span>

<span data-ttu-id="33873-132">Wanneer er meerdere parameter sets zijn gedefinieerd, kunt u het `DefaultParameterSetName` sleutel woord van het **cmdlet** -kenmerk gebruiken om de standaard parameterset op te geven.</span><span class="sxs-lookup"><span data-stu-id="33873-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="33873-133">Power shell gebruikt de standaard parameterset als de ingestelde para meter niet kan worden bepaald op basis van de informatie die wordt verstrekt door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="33873-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="33873-134">Zie voor meer informatie over het **cmdlet** -kenmerk de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="33873-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="33873-135">Parameter sets declareren</span><span class="sxs-lookup"><span data-stu-id="33873-135">Declaring parameter sets</span></span>

<span data-ttu-id="33873-136">Als u een parameterset wilt maken, moet u `ParameterSetName` het sleutel woord opgeven wanneer u het **parameter** kenmerk declareert voor elke para meter in de parameterset.</span><span class="sxs-lookup"><span data-stu-id="33873-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="33873-137">Voor para meters die bij meerdere parameter sets horen, voegt u een **parameter** kenmerk toe voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="33873-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="33873-138">Met dit kenmerk kunt u de para meter op verschillende manieren definiëren voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="33873-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="33873-139">U kunt bijvoorbeeld een para meter definiëren als verplicht in de ene set en optioneel in een andere.</span><span class="sxs-lookup"><span data-stu-id="33873-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="33873-140">Elke parameterset moet echter één unieke para meter bevatten.</span><span class="sxs-lookup"><span data-stu-id="33873-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="33873-141">Zie [para meter kenmerk declaratie](parameter-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="33873-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="33873-142">In het volgende voor beeld is de para meter **username** de unieke para meter `Test01` van de parameterset en de para meter **ComputerName** is de unieke para meter `Test02` van de para meter set.</span><span class="sxs-lookup"><span data-stu-id="33873-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="33873-143">De para meter **SharedParam** behoort tot beide sets en is verplicht voor `Test01` de ingestelde para meter, `Test02` maar is optioneel voor de parameterset.</span><span class="sxs-lookup"><span data-stu-id="33873-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
private string sharedParam;
```
