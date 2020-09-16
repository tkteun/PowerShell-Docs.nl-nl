---
title: Parametersets voor cmdlets
ms.date: 09/13/2016
ms.openlocfilehash: 202cdd354693b9b7edaca5c127ae1f7d88ff4a28
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784415"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="fbcf3-102">Cmdlet-parameter sets</span><span class="sxs-lookup"><span data-stu-id="fbcf3-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="fbcf3-103">Power shell gebruikt parameter sets om een enkele cmdlet te schrijven die verschillende acties voor verschillende scenario's kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="fbcf3-104">Met parameter sets kunt u verschillende para meters voor de gebruiker beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="fbcf3-105">En om andere informatie te retour neren op basis van de para meters die door de gebruiker zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="fbcf3-106">Voor beelden van parameter sets</span><span class="sxs-lookup"><span data-stu-id="fbcf3-106">Examples of parameter sets</span></span>

<span data-ttu-id="fbcf3-107">De Power shell- `Get-EventLog` cmdlet retourneert bijvoorbeeld verschillende informatie, afhankelijk van het feit of de gebruiker de para meter **List** of **LogName** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="fbcf3-108">Als de **List** -para meter is opgegeven, retourneert de cmdlet informatie over de logboek bestanden zelf, maar niet de gebeurtenis gegevens die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="fbcf3-109">Als de para meter **LogName** is opgegeven, retourneert de cmdlet informatie over de gebeurtenissen in een specifiek gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="fbcf3-110">De para meters **List** en **LogName** identificeren twee afzonderlijke parameter sets.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="fbcf3-111">Unieke para meter</span><span class="sxs-lookup"><span data-stu-id="fbcf3-111">Unique parameter</span></span>

<span data-ttu-id="fbcf3-112">Elke parameterset moet een unieke para meter hebben die door de Power shell-runtime wordt gebruikt om de juiste parameterset beschikbaar te stellen.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="fbcf3-113">Indien mogelijk moet de unieke para meter een verplichte para meter zijn.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="fbcf3-114">Als een para meter verplicht is, moet de gebruiker de para meter opgeven en gebruikt de Power shell-runtime die para meter om de parameterset te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="fbcf3-115">De unieke para meter kan niet verplicht zijn als uw cmdlet is ontworpen om te worden uitgevoerd zonder para meters op te geven.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="fbcf3-116">Meerdere parameter sets</span><span class="sxs-lookup"><span data-stu-id="fbcf3-116">Multiple parameter sets</span></span>

<span data-ttu-id="fbcf3-117">In de volgende afbeelding ziet u in de linkerkolom drie geldige parameter sets.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="fbcf3-118">**Para meter A** is uniek voor de eerste parameterset, **para meter B** is uniek voor de tweede parameterset en **para meter C** is uniek voor de derde parameterset.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="fbcf3-119">In de rechter kolom hebben de parameters sets geen unieke para meter.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![Afbeelding van parameter sets](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="fbcf3-121">Vereisten voor de parameterset</span><span class="sxs-lookup"><span data-stu-id="fbcf3-121">Parameter set requirements</span></span>

<span data-ttu-id="fbcf3-122">De volgende vereisten zijn van toepassing op alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="fbcf3-123">Elke parameterset moet ten minste één unieke para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="fbcf3-124">Indien mogelijk moet u voor deze para meter een verplichte para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="fbcf3-125">Een parameterset met meerdere positionele para meters moet unieke posities definiëren voor elke para meter.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="fbcf3-126">Er kunnen niet twee positionele para meters dezelfde positie opgeven.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="fbcf3-127">Slechts één para meter in een set kan het `ValueFromPipeline` tref woord declareren met een waarde van `true` .</span><span class="sxs-lookup"><span data-stu-id="fbcf3-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="fbcf3-128">Meerdere para meters kunnen het `ValueFromPipelineByPropertyName` sleutel woord definiëren met een waarde van `true` .</span><span class="sxs-lookup"><span data-stu-id="fbcf3-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="fbcf3-129">Als er geen parameterset voor een para meter is opgegeven, hoort de para meter bij alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="fbcf3-130">Voor een cmdlet of functie geldt een limiet van 32 parameter sets.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="fbcf3-131">Standaard parameters sets</span><span class="sxs-lookup"><span data-stu-id="fbcf3-131">Default parameter sets</span></span>

<span data-ttu-id="fbcf3-132">Wanneer er meerdere parameter sets zijn gedefinieerd, kunt u het `DefaultParameterSetName` sleutel woord van het **cmdlet** -kenmerk gebruiken om de standaard parameterset op te geven.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="fbcf3-133">Power shell gebruikt de standaard parameterset als de ingestelde para meter niet kan worden bepaald op basis van de informatie die wordt verstrekt door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="fbcf3-134">Zie voor meer informatie over het **cmdlet** -kenmerk de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="fbcf3-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="fbcf3-135">Parameter sets declareren</span><span class="sxs-lookup"><span data-stu-id="fbcf3-135">Declaring parameter sets</span></span>

<span data-ttu-id="fbcf3-136">Als u een parameterset wilt maken, moet u het `ParameterSetName` sleutel woord opgeven wanneer u het **parameter** kenmerk declareert voor elke para meter in de parameterset.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="fbcf3-137">Voor para meters die bij meerdere parameter sets horen, voegt u een **parameter** kenmerk toe voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="fbcf3-138">Met dit kenmerk kunt u de para meter op verschillende manieren definiëren voor elke parameterset.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="fbcf3-139">U kunt bijvoorbeeld een para meter definiëren als verplicht in de ene set en optioneel in een andere.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="fbcf3-140">Elke parameterset moet echter één unieke para meter bevatten.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="fbcf3-141">Zie [para meter kenmerk declaratie](parameter-attribute-declaration.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="fbcf3-142">In het volgende voor beeld is de para meter **username** de unieke para meter van de `Test01` parameterset en de para meter **ComputerName** is de unieke para meter van de `Test02` para meter set.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="fbcf3-143">De para meter **SharedParam** behoort tot beide sets en is verplicht voor de `Test01` ingestelde para meter, maar is optioneel voor de `Test02` parameterset.</span><span class="sxs-lookup"><span data-stu-id="fbcf3-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
