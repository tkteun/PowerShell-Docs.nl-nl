---
title: Opmerkingen toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 1a365a167c245006bb882a542aedb5c43cfc4c96
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557104"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="f7186-102">Notities toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="f7186-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="f7186-103">In deze sectie wordt beschreven hoe u een sectie notities kunt toevoegen aan het Help-onderwerp van een Windows Power shell®-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7186-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="f7186-104">De sectie Notities wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter.</span><span class="sxs-lookup"><span data-stu-id="f7186-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="f7186-105">Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.</span><span class="sxs-lookup"><span data-stu-id="f7186-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="f7186-106">Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities.</span><span class="sxs-lookup"><span data-stu-id="f7186-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="f7186-107">Voeg voor elke notitie een paar \< maml: alert> tags toe aan het \< knoop punt maml:> waarschuwingset.</span><span class="sxs-lookup"><span data-stu-id="f7186-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="f7186-108">De inhoud van elke notitie wordt toegevoegd in een set \< maml: para> Tags.</span><span class="sxs-lookup"><span data-stu-id="f7186-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="f7186-109">Gebruik lege \< maml: para> Tags voor de afstand.</span><span class="sxs-lookup"><span data-stu-id="f7186-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="f7186-110">In het volgende XML-bestand ziet u een \< maml: alertset-> knoop punt met twee notities.</span><span class="sxs-lookup"><span data-stu-id="f7186-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="f7186-111">U ziet dat elke notitie een optionele \< maml: title> tag (titels kan worden gebruikt om een wille keurige set van \< maml: alert> Tags te groeperen), en dat elke notitie een lege regel heeft na de inhoud voor afstand.</span><span class="sxs-lookup"><span data-stu-id="f7186-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```
