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
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353310"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="a0117-102">Notities toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="a0117-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a0117-103">In deze sectie wordt beschreven hoe u een sectie notities kunt toevoegen aan het Help-onderwerp van een Windows Power shell®-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0117-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="a0117-104">De sectie Notities wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter.</span><span class="sxs-lookup"><span data-stu-id="a0117-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="a0117-105">Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.</span><span class="sxs-lookup"><span data-stu-id="a0117-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="a0117-106">Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities.</span><span class="sxs-lookup"><span data-stu-id="a0117-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="a0117-107">Voeg voor elke notitie een paar \<maml: alert > Tags toe aan het knoop punt \<maml: > alertset.</span><span class="sxs-lookup"><span data-stu-id="a0117-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="a0117-108">De inhoud van elke notitie wordt toegevoegd in een set \<maml: para codes >.</span><span class="sxs-lookup"><span data-stu-id="a0117-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="a0117-109">Gebruik blank \<maml: para > Tags voor afstand.</span><span class="sxs-lookup"><span data-stu-id="a0117-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="a0117-110">In het volgende XML-bestand wordt een \<maml: alertset-> knoop punt met twee notities weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a0117-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="a0117-111">U ziet dat elke notitie een optioneel \<maml: title > tag (titels kan worden gebruikt voor het groeperen van een wille keurige set \<maml: alarm > Tags) en dat elke notitie een lege regel heeft die de inhoud voor de tussen ruimte bevat.</span><span class="sxs-lookup"><span data-stu-id="a0117-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



