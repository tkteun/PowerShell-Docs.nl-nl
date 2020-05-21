---
title: Retour waarden toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: a5618b72827d8ef70201437c4a99ea8bf68cdfd3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565540"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="de3bd-102">Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="de3bd-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="de3bd-103">In deze sectie wordt beschreven hoe u een sectie OUTPUTs toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de3bd-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="de3bd-104">De sectie OUTPUTs geeft een lijst van de .NET-klassen van objecten die de cmdlet retourneert of de pijp lijn wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="de3bd-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="de3bd-105">Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan de sectie OUTPUTs.</span><span class="sxs-lookup"><span data-stu-id="de3bd-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="de3bd-106">De retour typen van een cmdlet bevinden zich in een \< opdracht: returnvalues> knoop punt, waarbij elke klasse wordt Inge sloten in een \< opdracht: returnValue> element.</span><span class="sxs-lookup"><span data-stu-id="de3bd-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="de3bd-107">Als een cmdlet geen uitvoer genereert, gebruikt u deze sectie om aan te geven dat er geen uitvoer is.</span><span class="sxs-lookup"><span data-stu-id="de3bd-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="de3bd-108">Schrijf bijvoorbeeld ' geen ' in plaats van de naam van de klasse en geef een korte uitleg.</span><span class="sxs-lookup"><span data-stu-id="de3bd-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="de3bd-109">Als de cmdlet uitvoer voorwaarde genereert, gebruikt u dit knoop punt om de voor waarden uit te leggen en de voorwaardelijke uitvoer te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="de3bd-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="de3bd-110">Het schema bevat twee \< maml: beschrijving> elementen in elke \< opdracht: returnValue> element.</span><span class="sxs-lookup"><span data-stu-id="de3bd-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="de3bd-111">`Get-Help`Met de cmdlet wordt echter alleen de inhoud van de \< opdracht weer gegeven: returnValue>/ \< maml: Description> element.</span><span class="sxs-lookup"><span data-stu-id="de3bd-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="de3bd-112">Vanaf Windows Power Shell 3,0 geeft de `Get-Help` cmdlet de inhoud van het \< element maml: URI>.</span><span class="sxs-lookup"><span data-stu-id="de3bd-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="de3bd-113">Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="de3bd-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="de3bd-114">Het volgende XML-bestand bevat de \< maml: returnvalues> knoop punt.</span><span class="sxs-lookup"><span data-stu-id="de3bd-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="de3bd-115">De volgende XML-code toont een voor beeld van het gebruik van de \< maml: returnvalues> knoop punt om een uitvoer type te documenteren.</span><span class="sxs-lookup"><span data-stu-id="de3bd-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
