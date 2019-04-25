---
title: Invoertypen toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083430"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="32a9e-102">Invoertypen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="32a9e-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="32a9e-103">In deze sectie wordt beschreven hoe u een sectie invoer toevoegen aan een Windows PowerShell® cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="32a9e-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="32a9e-104">De invoer-sectie vindt u de .NET-klassen van objecten die de cmdlet als invoer van de pijplijn door de waarde of door de naam van eigenschap accepteert.</span><span class="sxs-lookup"><span data-stu-id="32a9e-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="32a9e-105">Er is geen limiet voor het aantal klassen die u aan een sectie invoer toevoegen kunt.</span><span class="sxs-lookup"><span data-stu-id="32a9e-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="32a9e-106">De invoertypen zijn ingesloten in een \<opdracht: inputTypes > knooppunt, waarbij elke klasse die is ingesloten in een \<opdracht: inputType > element.</span><span class="sxs-lookup"><span data-stu-id="32a9e-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="32a9e-107">Het schema bevat twee \<maml:description > elementen in elk \<opdracht: inputType > element.</span><span class="sxs-lookup"><span data-stu-id="32a9e-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="32a9e-108">Echter, de `Get-Help` cmdlet wordt alleen de inhoud van de \<opdracht: inputType > /\<maml:description >) element.</span><span class="sxs-lookup"><span data-stu-id="32a9e-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="32a9e-109">Vanaf Windows PowerShell 3.0, de `Get-Help` cmdlet wordt de inhoud van de \<maml:uri > element.</span><span class="sxs-lookup"><span data-stu-id="32a9e-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="32a9e-110">Dit element kunt u gebruikers naar onderwerpen waarin wordt beschreven van de .NET-klasse.</span><span class="sxs-lookup"><span data-stu-id="32a9e-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="32a9e-111">De volgende XML bevat de \<maml:inputTypes > knooppunt.</span><span class="sxs-lookup"><span data-stu-id="32a9e-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="32a9e-112">Het volgende XML-bestand toont een voorbeeld van het gebruik van de \<maml:inputTypes > knooppunt vastleggen van een type gebruikersinvoer.</span><span class="sxs-lookup"><span data-stu-id="32a9e-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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