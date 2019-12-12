---
title: Invoer typen toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353289"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="7389b-102">Invoertypen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="7389b-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7389b-103">In deze sectie wordt beschreven hoe u een invoer sectie toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7389b-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7389b-104">De sectie invoer geeft een lijst van de .NET-klassen van objecten die de cmdlet accepteert als invoer van de pijp lijn, hetzij op waarde hetzij op basis van eigenschaps naam.</span><span class="sxs-lookup"><span data-stu-id="7389b-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="7389b-105">Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan een invoer sectie.</span><span class="sxs-lookup"><span data-stu-id="7389b-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="7389b-106">De invoer typen bevinden zich in een \<opdracht: inputTypes > knoop punt, waarbij elke klasse wordt Inge sloten in een \<opdracht: input type > element.</span><span class="sxs-lookup"><span data-stu-id="7389b-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="7389b-107">Het schema bevat twee \<maml: Beschrijving > elementen in elke \<opdracht: input type > element.</span><span class="sxs-lookup"><span data-stu-id="7389b-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="7389b-108">Met de cmdlet `Get-Help` wordt echter alleen de inhoud van de \<opdracht weer gegeven: input type >/\<maml: Description >-element.</span><span class="sxs-lookup"><span data-stu-id="7389b-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="7389b-109">Vanaf Windows Power Shell 3,0 wordt met de cmdlet `Get-Help` de inhoud van het element \<maml: URI > weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7389b-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="7389b-110">Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="7389b-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="7389b-111">Het volgende XML-bestand bevat het \<maml: inputTypes >-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="7389b-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="7389b-112">In het volgende XML-bestand ziet u een voor beeld van het gebruik van het knoop punt \<maml: inputTypes > om een invoer type te documenteren.</span><span class="sxs-lookup"><span data-stu-id="7389b-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```