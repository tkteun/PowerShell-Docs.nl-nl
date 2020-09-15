---
title: Invoertypen toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/12/2016
ms.openlocfilehash: d41c49ff48cf361c2ba694d11576e84a9367eef5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893421"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="4f9e3-102">Invoertypen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="4f9e3-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="4f9e3-103">In deze sectie wordt beschreven hoe u een **invoer** sectie kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-103">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="4f9e3-104">De sectie **invoer** geeft een lijst van de .net-klassen van objecten die de cmdlet accepteert als invoer van de pijp lijn, hetzij op waarde hetzij op basis van eigenschaps naam.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-104">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="4f9e3-105">Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan een **invoer** sectie.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-105">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="4f9e3-106">De invoer typen bevinden zich in een `<command:inputTypes>` knoop punt, waarbij elke klasse wordt Inge sloten in een- `<command:inputType>` element.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-106">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="4f9e3-107">Het schema bevat twee `<maml:description>` elementen in elk- `<command:inputType>` element.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-107">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="4f9e3-108">`Get-Help`Met de cmdlet wordt echter alleen de inhoud van het `<command:inputType>/<maml:description>` element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-108">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="4f9e3-109">Vanaf Power Shell 3,0 wordt de `Get-Help` inhoud van het element weer gegeven met de cmdlet `<maml:uri>` .</span><span class="sxs-lookup"><span data-stu-id="4f9e3-109">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="4f9e3-110">Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="4f9e3-111">Het knoop punt wordt weer gegeven in de volgende XML-code `<maml:inputTypes>` .</span><span class="sxs-lookup"><span data-stu-id="4f9e3-111">The following XML shows the `<maml:inputTypes>` node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="4f9e3-112">De volgende XML-code toont een voor beeld van het gebruik van het `<maml:inputTypes>` knoop punt om een invoer type te documenteren.</span><span class="sxs-lookup"><span data-stu-id="4f9e3-112">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
