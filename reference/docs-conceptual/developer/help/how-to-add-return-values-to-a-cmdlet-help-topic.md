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
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995936"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="14002-102">Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="14002-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="14002-103">In deze sectie wordt beschreven hoe u een sectie OUTPUTs toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="14002-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="14002-104">De sectie OUTPUTs geeft een lijst van de .NET-klassen van objecten die de cmdlet retourneert of de pijp lijn wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="14002-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="14002-105">Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan de sectie OUTPUTs.</span><span class="sxs-lookup"><span data-stu-id="14002-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="14002-106">De retour typen van een cmdlet bevinden zich in een \<opdracht: returnValues > knoop punt, waarbij elke klasse wordt Inge sloten in een \<opdracht: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="14002-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="14002-107">Als een cmdlet geen uitvoer genereert, gebruikt u deze sectie om aan te geven dat er geen uitvoer is.</span><span class="sxs-lookup"><span data-stu-id="14002-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="14002-108">Schrijf bijvoorbeeld ' geen ' in plaats van de naam van de klasse en geef een korte uitleg.</span><span class="sxs-lookup"><span data-stu-id="14002-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="14002-109">Als de cmdlet uitvoer voorwaarde genereert, gebruikt u dit knoop punt om de voor waarden uit te leggen en de voorwaardelijke uitvoer te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="14002-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="14002-110">Het schema bevat twee \<maml: Beschrijving > elementen in elke \<opdracht: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="14002-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="14002-111">Met de cmdlet `Get-Help` wordt echter alleen de inhoud van de \<opdracht weer gegeven: returnValue >/\<maml: Description > element.</span><span class="sxs-lookup"><span data-stu-id="14002-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="14002-112">Vanaf Windows Power Shell 3,0 wordt met de cmdlet `Get-Help` de inhoud van het element \<maml: URI > weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="14002-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="14002-113">Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="14002-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="14002-114">In het volgende XML-bestand worden de \<maml: returnValues > knoop punt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="14002-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="14002-115">In het volgende XML-bestand ziet u een voor beeld van het gebruik van de \<maml: returnValues > knoop punt om een uitvoer type te documenteren.</span><span class="sxs-lookup"><span data-stu-id="14002-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



