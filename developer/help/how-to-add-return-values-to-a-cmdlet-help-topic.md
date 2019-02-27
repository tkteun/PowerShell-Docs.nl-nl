---
title: Retour toevoegen aan een Cmdlet Help-onderwerp waarden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849215"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="c9607-102">Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="c9607-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c9607-103">In deze sectie wordt beschreven hoe u een uitvoersectie toevoegen aan een Windows PowerShell® cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="c9607-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="c9607-104">De uitvoer-sectie vindt u de .NET-klassen van objecten die de cmdlet retourneert of geeft u de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="c9607-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="c9607-105">Er is geen limiet voor het aantal klassen die u aan de sectie uitvoer toevoegen kunt.</span><span class="sxs-lookup"><span data-stu-id="c9607-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="c9607-106">De typen retourneren die van een cmdlet zijn ingesloten in een \<opdracht: returnValues > knooppunt, waarbij elke klasse die is ingesloten in een \<opdracht: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="c9607-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="c9607-107">Als een cmdlet wordt geen uitvoer gegenereerd, gebruikt u deze sectie om aan te geven dat er geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9607-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="c9607-108">Bijvoorbeeld, in plaats van de naam van de klasse schrijven 'None' en geef een korte uitleg.</span><span class="sxs-lookup"><span data-stu-id="c9607-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="c9607-109">Als de cmdlet voorwaardelijk uitvoer genereert, gebruik dit knooppunt te leggen van de voorwaarden en de voorwaardelijke uitvoer te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="c9607-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="c9607-110">Het schema bevat twee \<maml:description > elementen in elk \<opdracht: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="c9607-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="c9607-111">Echter, de `Get-Help` cmdlet wordt alleen de inhoud van de \<opdracht: returnValue > /\<maml:description > element.</span><span class="sxs-lookup"><span data-stu-id="c9607-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="c9607-112">Vanaf Windows PowerShell 3.0, de `Get-Help` cmdlet wordt de inhoud van de \<maml:uri > element.</span><span class="sxs-lookup"><span data-stu-id="c9607-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="c9607-113">Dit element kunt u gebruikers naar onderwerpen waarin wordt beschreven van de .NET-klasse.</span><span class="sxs-lookup"><span data-stu-id="c9607-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="c9607-114">De volgende XML bevat de \<maml:returnValues > knooppunt.</span><span class="sxs-lookup"><span data-stu-id="c9607-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="c9607-115">Het volgende XML-bestand toont een voorbeeld van het gebruik van de \<maml:returnValues > knooppunt aan het document een uitvoertype.</span><span class="sxs-lookup"><span data-stu-id="c9607-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



