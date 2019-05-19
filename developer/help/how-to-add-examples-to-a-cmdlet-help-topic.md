---
title: Voorbeelden van een Cmdlet Help-onderwerp toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855114"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="57080-102">Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="57080-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="57080-103">Om te weten over de voorbeelden in de Help van Cmdlet</span><span class="sxs-lookup"><span data-stu-id="57080-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="57080-104">De lijst alle van de namen van parameters in de opdracht, zelfs wanneer de namen van parameters optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="57080-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="57080-105">Hiermee wordt de gebruiker de opdracht eenvoudig interpreteren.</span><span class="sxs-lookup"><span data-stu-id="57080-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="57080-106">Vermijd aliassen en gedeeltelijke parameternamen, zelfs als ze in Windows PowerShell® werken.</span><span class="sxs-lookup"><span data-stu-id="57080-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="57080-107">Leg uit de rationele voor het samenstellen van de opdracht in de beschrijving van het voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="57080-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="57080-108">Wordt uitgelegd waarom u bepaalde parameters en waarden, en hoe u variabelen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57080-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="57080-109">Als de opdracht gebruikmaakt van expressies, kunt u ze in detail uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="57080-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="57080-110">Als de opdracht gebruikt eigenschappen en methoden van objecten, met name de eigenschappen die niet in de standaard weer te geven verschijnen, gebruikt u het voorbeeld als een verkoopkans vertelt de gebruiker over het object.</span><span class="sxs-lookup"><span data-stu-id="57080-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="57080-111">Help-weergaven die voorbeelden weergeven</span><span class="sxs-lookup"><span data-stu-id="57080-111">Help Views that Display Examples</span></span>

<span data-ttu-id="57080-112">Voorbeelden weergegeven alleen in de gedetailleerde en volledige weergaven van de cmdlet Help.</span><span class="sxs-lookup"><span data-stu-id="57080-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="57080-113">Toevoegen van een knooppunt voorbeelden</span><span class="sxs-lookup"><span data-stu-id="57080-113">Adding an Examples Node</span></span>

<span data-ttu-id="57080-114">De volgende XML-code laat zien hoe een voorbeelden-knooppunt dat één voorbeeldknooppunt bevat toevoegen.</span><span class="sxs-lookup"><span data-stu-id="57080-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="57080-115">Voorbeeld van de aanvullende knooppunten toevoegen voor elke voorbeelden die u wilt opnemen in het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="57080-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="57080-116">De titel van een voorbeeld toevoegen</span><span class="sxs-lookup"><span data-stu-id="57080-116">Adding an Example Title</span></span>

<span data-ttu-id="57080-117">De volgende XML-code laat zien hoe een titel voor het voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="57080-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="57080-118">De titel wordt gebruikt om in te stellen in het voorbeeld naast andere voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="57080-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="57080-119">Windows PowerShell® maakt gebruik van een standard-header die een aantal opeenvolgende voorbeeld bevatten.</span><span class="sxs-lookup"><span data-stu-id="57080-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="57080-120">Toe te voegen vóór tekens</span><span class="sxs-lookup"><span data-stu-id="57080-120">Adding Preceding Characters</span></span>

<span data-ttu-id="57080-121">De volgende XML-code laat zien hoe om toe te voegen tekens, zoals de Windows PowerShell-prompt die direct vóór de opdracht (zonder spaties) worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="57080-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="57080-122">Windows PowerShell® maakt gebruik van de Windows PowerShell-prompt: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="57080-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="57080-123">De opdracht toe te voegen</span><span class="sxs-lookup"><span data-stu-id="57080-123">Adding the Command</span></span>

<span data-ttu-id="57080-124">De volgende XML-code laat zien hoe de werkelijke opdracht van het voorbeeld toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="57080-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="57080-125">Bij het toevoegen van de opdracht, typt u de volledige naam (gebruik geen alias) van de cmdlets en -parameters.</span><span class="sxs-lookup"><span data-stu-id="57080-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="57080-126">Kleine letters indien mogelijk ook gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57080-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="57080-127">Een beschrijving toevoegen</span><span class="sxs-lookup"><span data-stu-id="57080-127">Adding a Description</span></span>

<span data-ttu-id="57080-128">Het volgende XML-bestand ziet hoe u een beschrijving op voor het voorbeeld toevoegen.</span><span class="sxs-lookup"><span data-stu-id="57080-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="57080-129">Windows PowerShell® maakt gebruik van een enkele set \<maml:para > tags voor de beschrijving, zelfs als meerdere \<maml:para > tags kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="57080-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="57080-130">Voorbeeld van uitvoer toevoegen</span><span class="sxs-lookup"><span data-stu-id="57080-130">Adding Example Output</span></span>

<span data-ttu-id="57080-131">De volgende XML-code laat zien hoe de uitvoer van de opdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="57080-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="57080-132">Informatie over de opdracht is optioneel, maar in sommige gevallen is het handig om te demonstreren het effect van het gebruik van bepaalde parameters.</span><span class="sxs-lookup"><span data-stu-id="57080-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="57080-133">Windows PowerShell® maakt gebruik van twee sets met lege \<maml:para > tags voor het scheiden van de opdrachtuitvoer vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="57080-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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