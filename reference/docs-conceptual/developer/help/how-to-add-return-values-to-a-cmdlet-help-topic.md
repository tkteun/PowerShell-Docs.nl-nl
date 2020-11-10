---
ms.date: 09/12/2016
ms.topic: reference
title: Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets
description: Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: 8c556821a257451a320916231cb20fc82e75ebb4
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389739"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="26f51-103">Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="26f51-103">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="26f51-104">In deze sectie wordt beschreven hoe u een uitvoer sectie kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26f51-104">This section describes how to add an OUTPUTS section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="26f51-105">De sectie **outputs** geeft een lijst van de .net-klassen van objecten die de cmdlet retourneert of de pijp lijn wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="26f51-105">The **OUTPUTS** section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="26f51-106">Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan de sectie **outputs** .</span><span class="sxs-lookup"><span data-stu-id="26f51-106">There is no limit to the number of classes that you can add to the **OUTPUTS** section.</span></span> <span data-ttu-id="26f51-107">De retour typen van een cmdlet bevinden zich in een `<command:returnValues>` knoop punt, waarbij elke klasse wordt Inge sloten in een- `<command:returnValue>` element.</span><span class="sxs-lookup"><span data-stu-id="26f51-107">The return types of a cmdlet are enclosed in a `<command:returnValues>` node, with each class enclosed in a `<command:returnValue>` element.</span></span>

<span data-ttu-id="26f51-108">Als een cmdlet geen uitvoer genereert, gebruikt u deze sectie om aan te geven dat er geen uitvoer is.</span><span class="sxs-lookup"><span data-stu-id="26f51-108">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="26f51-109">Schrijf bijvoorbeeld in plaats van de naam van de klasse **geen** en geef een korte uitleg.</span><span class="sxs-lookup"><span data-stu-id="26f51-109">For example, in place of the class name, write **None** and provide a brief explanation.</span></span> <span data-ttu-id="26f51-110">Als de cmdlet uitvoer voorwaarde genereert, gebruikt u dit knoop punt om de voor waarden uit te leggen en de voorwaardelijke uitvoer te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="26f51-110">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="26f51-111">Het schema bevat twee `<maml:description>` elementen in elk- `<command:returnValue>` element.</span><span class="sxs-lookup"><span data-stu-id="26f51-111">The schema includes two `<maml:description>` elements in each `<command:returnValue>` element.</span></span>
<span data-ttu-id="26f51-112">`Get-Help`Met de cmdlet wordt echter alleen de inhoud van het `<command:returnValue>/<maml:description>` element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="26f51-112">However, the `Get-Help` cmdlet displays only the content of the `<command:returnValue>/<maml:description>` element.</span></span>

<span data-ttu-id="26f51-113">Vanaf Power Shell 3,0 wordt de `Get-Help` inhoud van het element weer gegeven met de cmdlet `<maml:uri>` .</span><span class="sxs-lookup"><span data-stu-id="26f51-113">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="26f51-114">Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="26f51-114">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="26f51-115">Het knoop punt wordt weer gegeven in de volgende XML-code `<maml:returnValues>` .</span><span class="sxs-lookup"><span data-stu-id="26f51-115">The following XML shows the `<maml:returnValues>` node.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

<span data-ttu-id="26f51-116">De volgende XML-code toont een voor beeld van het gebruik van het `<maml:returnValues>` knoop punt om een uitvoer type te documenteren.</span><span class="sxs-lookup"><span data-stu-id="26f51-116">The following XML shows an example of using the `<maml:returnValues>` node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://docs.microsoft.com/dotnet/api/system.datetime </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
