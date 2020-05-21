---
title: Voor beelden toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 82bee7b7bb0ef49203636f2a293075f3db924ce4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557087"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="d5a14-102">Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="d5a14-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="d5a14-103">Wat u moet weten over voor beelden in cmdlet Help</span><span class="sxs-lookup"><span data-stu-id="d5a14-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="d5a14-104">Een lijst met alle parameter namen in de opdracht, zelfs wanneer de parameter namen optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="d5a14-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="d5a14-105">Op deze manier kan de gebruiker de opdracht eenvoudig interpreteren.</span><span class="sxs-lookup"><span data-stu-id="d5a14-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="d5a14-106">Vermijd aliassen en gedeeltelijke parameter namen, zelfs als ze werken in Windows Power shell®.</span><span class="sxs-lookup"><span data-stu-id="d5a14-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="d5a14-107">In het voor beeld wordt de rationele uitleg uitgelegd voor het bouwen van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d5a14-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="d5a14-108">Leg uit waarom u specifieke para meters en waarden hebt gekozen en hoe u variabelen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d5a14-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="d5a14-109">Als de opdracht expressies gebruikt, moet u deze gedetailleerd uitleggen.</span><span class="sxs-lookup"><span data-stu-id="d5a14-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="d5a14-110">Als de opdracht Eigenschappen en methoden van objecten gebruikt, met name eigenschappen die niet worden weer gegeven in de standaard weergave, kunt u het voor beeld gebruiken om de gebruiker over het object te informeren.</span><span class="sxs-lookup"><span data-stu-id="d5a14-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="d5a14-111">Help-weer gaven waarin voor beelden worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="d5a14-111">Help Views that Display Examples</span></span>

<span data-ttu-id="d5a14-112">Voor beelden worden alleen weer gegeven in de gedetailleerde en volledige weer gave van de Help van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5a14-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="d5a14-113">Een voor beeld-knoop punt toevoegen</span><span class="sxs-lookup"><span data-stu-id="d5a14-113">Adding an Examples Node</span></span>

<span data-ttu-id="d5a14-114">In het volgende XML-bestand ziet u hoe u een knoop punt voor beelden kunt toevoegen die één voorbeeld knooppunt bevat.</span><span class="sxs-lookup"><span data-stu-id="d5a14-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="d5a14-115">Voeg extra voorbeeld knooppunten toe voor elk voor beeld dat u wilt toevoegen in het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="d5a14-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="d5a14-116">Een voorbeeld titel toevoegen</span><span class="sxs-lookup"><span data-stu-id="d5a14-116">Adding an Example Title</span></span>

<span data-ttu-id="d5a14-117">In het volgende XML-bestand ziet u hoe u een titel kunt toevoegen voor het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="d5a14-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="d5a14-118">De titel wordt gebruikt om het voor beeld uit te stellen uit andere voor beelden.</span><span class="sxs-lookup"><span data-stu-id="d5a14-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="d5a14-119">Windows Power shell® gebruikt een standaard header die een opeenvolgend voorbeeld nummer bevat.</span><span class="sxs-lookup"><span data-stu-id="d5a14-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="d5a14-120">Voorafgaande tekens toevoegen</span><span class="sxs-lookup"><span data-stu-id="d5a14-120">Adding Preceding Characters</span></span>

<span data-ttu-id="d5a14-121">In het volgende XML-bestand ziet u hoe u tekens kunt toevoegen, zoals de Windows Power shell-prompt, die direct vóór de voor beeld-opdracht worden weer gegeven (zonder tussenliggende spaties).</span><span class="sxs-lookup"><span data-stu-id="d5a14-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="d5a14-122">Windows Power Shell® maakt gebruik van de Windows Power shell-prompt: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="d5a14-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="d5a14-123">De opdracht toevoegen</span><span class="sxs-lookup"><span data-stu-id="d5a14-123">Adding the Command</span></span>

<span data-ttu-id="d5a14-124">In het volgende XML-bestand ziet u hoe u de werkelijke opdracht van het voor beeld kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d5a14-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="d5a14-125">Wanneer u de opdracht toevoegt, typt u de volledige naam (geen alias gebruiken) van cmdlets en para meters.</span><span class="sxs-lookup"><span data-stu-id="d5a14-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="d5a14-126">Gebruik waar mogelijk kleine letters.</span><span class="sxs-lookup"><span data-stu-id="d5a14-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="d5a14-127">Een beschrijving toevoegen</span><span class="sxs-lookup"><span data-stu-id="d5a14-127">Adding a Description</span></span>

<span data-ttu-id="d5a14-128">In het volgende XML-bestand ziet u hoe u een beschrijving voor het voor beeld kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d5a14-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="d5a14-129">Windows Power shell® gebruikt één set \< maml: para> Tags voor de beschrijving, zelfs als er meerdere \< maml: para codes> Tags kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d5a14-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="d5a14-130">Voorbeeld uitvoer toevoegen</span><span class="sxs-lookup"><span data-stu-id="d5a14-130">Adding Example Output</span></span>

<span data-ttu-id="d5a14-131">In het volgende XML-bestand ziet u hoe de uitvoer van de opdracht kan worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d5a14-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="d5a14-132">De gegevens van de opdracht resultaten zijn optioneel, maar in sommige gevallen is het handig om te demonstreren wat het effect is van het gebruik van specifieke para meters.</span><span class="sxs-lookup"><span data-stu-id="d5a14-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="d5a14-133">Windows Power shell® gebruikt twee sets lege \< maml: para codes> om de uitvoer van de opdracht van de opdracht te scheiden.</span><span class="sxs-lookup"><span data-stu-id="d5a14-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
