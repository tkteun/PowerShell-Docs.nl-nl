---
ms.date: 09/13/2016
ms.topic: reference
title: Parametersets voor cmdlets
description: Parametersets voor cmdlets
ms.openlocfilehash: e84af7faf5b7459d8dbe06847526efe804e2c5e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668283"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="4e0e3-103">Cmdlet-parameter sets</span><span class="sxs-lookup"><span data-stu-id="4e0e3-103">Cmdlet parameter sets</span></span>

<span data-ttu-id="4e0e3-104">Power shell gebruikt parameter sets om een enkele cmdlet te schrijven die verschillende acties voor verschillende scenario's kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-104">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="4e0e3-105">Met parameter sets kunt u verschillende para meters voor de gebruiker beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-105">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="4e0e3-106">En om andere informatie te retour neren op basis van de para meters die door de gebruiker zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-106">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="4e0e3-107">Voor beelden van parameter sets</span><span class="sxs-lookup"><span data-stu-id="4e0e3-107">Examples of parameter sets</span></span>

<span data-ttu-id="4e0e3-108">De Power shell- `Get-EventLog` cmdlet retourneert bijvoorbeeld verschillende informatie, afhankelijk van het feit of de gebruiker de para meter **List** of **LogName** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-108">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="4e0e3-109">Als de **List** -para meter is opgegeven, retourneert de cmdlet informatie over de logboek bestanden zelf, maar niet de gebeurtenis gegevens die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-109">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="4e0e3-110">Als de para meter **LogName** is opgegeven, retourneert de cmdlet informatie over de gebeurtenissen in een specifiek gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-110">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="4e0e3-111">De para meters **List** en **LogName** identificeren twee afzonderlijke parameter sets.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-111">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="4e0e3-112">Unieke para meter</span><span class="sxs-lookup"><span data-stu-id="4e0e3-112">Unique parameter</span></span>

<span data-ttu-id="4e0e3-113">Elke parameterset moet een unieke para meter hebben die door de Power shell-runtime wordt gebruikt om de juiste parameterset beschikbaar te stellen.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-113">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="4e0e3-114">Indien mogelijk moet de unieke para meter een verplichte para meter zijn.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-114">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="4e0e3-115">Als een para meter verplicht is, moet de gebruiker de para meter opgeven en gebruikt de Power shell-runtime die para meter om de parameterset te identificeren.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-115">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="4e0e3-116">De unieke para meter kan niet verplicht zijn als uw cmdlet is ontworpen om te worden uitgevoerd zonder para meters op te geven.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-116">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="4e0e3-117">Meerdere parameter sets</span><span class="sxs-lookup"><span data-stu-id="4e0e3-117">Multiple parameter sets</span></span>

<span data-ttu-id="4e0e3-118">In de volgende afbeelding ziet u in de linkerkolom drie geldige parameter sets.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-118">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="4e0e3-119">**Para meter A** is uniek voor de eerste parameterset, **para meter B** is uniek voor de tweede parameterset en **para meter C** is uniek voor de derde parameterset.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-119">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="4e0e3-120">In de rechter kolom hebben de parameters sets geen unieke para meter.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-120">In the right column, the parameter sets don't have a unique parameter.</span></span>

![Afbeelding van parameter sets](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="4e0e3-122">Vereisten voor de parameterset</span><span class="sxs-lookup"><span data-stu-id="4e0e3-122">Parameter set requirements</span></span>

<span data-ttu-id="4e0e3-123">De volgende vereisten zijn van toepassing op alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-123">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="4e0e3-124">Elke parameterset moet ten minste één unieke para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-124">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="4e0e3-125">Indien mogelijk moet u voor deze para meter een verplichte para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-125">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="4e0e3-126">Een parameterset met meerdere positionele para meters moet unieke posities definiëren voor elke para meter.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-126">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="4e0e3-127">Er kunnen niet twee positionele para meters dezelfde positie opgeven.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-127">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="4e0e3-128">Slechts één para meter in een set kan het `ValueFromPipeline` tref woord declareren met een waarde van `true` .</span><span class="sxs-lookup"><span data-stu-id="4e0e3-128">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="4e0e3-129">Meerdere para meters kunnen het `ValueFromPipelineByPropertyName` sleutel woord definiëren met een waarde van `true` .</span><span class="sxs-lookup"><span data-stu-id="4e0e3-129">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="4e0e3-130">Als er geen parameterset voor een para meter is opgegeven, hoort de para meter bij alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-130">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="4e0e3-131">Voor een cmdlet of functie geldt een limiet van 32 parameter sets.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-131">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="4e0e3-132">Standaard parameters sets</span><span class="sxs-lookup"><span data-stu-id="4e0e3-132">Default parameter sets</span></span>

<span data-ttu-id="4e0e3-133">Wanneer er meerdere parameter sets zijn gedefinieerd, kunt u het `DefaultParameterSetName` sleutel woord van het **cmdlet** -kenmerk gebruiken om de standaard parameterset op te geven.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-133">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="4e0e3-134">Power shell gebruikt de standaard parameterset als de ingestelde para meter niet kan worden bepaald op basis van de informatie die wordt verstrekt door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-134">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="4e0e3-135">Zie voor meer informatie over het **cmdlet** -kenmerk de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4e0e3-135">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="4e0e3-136">Parameter sets declareren</span><span class="sxs-lookup"><span data-stu-id="4e0e3-136">Declaring parameter sets</span></span>

<span data-ttu-id="4e0e3-137">Als u een parameterset wilt maken, moet u het `ParameterSetName` sleutel woord opgeven wanneer u het **parameter** kenmerk declareert voor elke para meter in de parameterset.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-137">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="4e0e3-138">Voor para meters die bij meerdere parameter sets horen, voegt u een **parameter** kenmerk toe voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-138">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="4e0e3-139">Met dit kenmerk kunt u de para meter op verschillende manieren definiëren voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-139">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="4e0e3-140">U kunt bijvoorbeeld een para meter definiëren als verplicht in de ene set en optioneel in een andere.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-140">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="4e0e3-141">Elke parameterset moet echter één unieke para meter bevatten.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-141">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="4e0e3-142">Zie [para meter kenmerk declaratie](parameter-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-142">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="4e0e3-143">In het volgende voor beeld is de para meter **username** de unieke para meter van de `Test01` parameterset en de para meter **ComputerName** is de unieke para meter van de `Test02` para meter set.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-143">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="4e0e3-144">De para meter **SharedParam** behoort tot beide sets en is verplicht voor de `Test01` ingestelde para meter, maar is optioneel voor de `Test02` parameterset.</span><span class="sxs-lookup"><span data-stu-id="4e0e3-144">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
