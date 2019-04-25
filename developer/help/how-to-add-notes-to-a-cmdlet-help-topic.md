---
title: Notities toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083413"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="0bd20-102">Notities toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="0bd20-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="0bd20-103">In deze sectie wordt beschreven hoe u een sectie met opmerkingen toevoegen aan een Windows PowerShell® cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="0bd20-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="0bd20-104">De sectie met opmerkingen wordt gebruikt om uit te leggen van de gegevens die niet zijn voor eenvoudig in de andere gestructureerde secties, zoals een meer gedetailleerde uitleg van een parameter geschikt.</span><span class="sxs-lookup"><span data-stu-id="0bd20-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="0bd20-105">Deze inhoud kan opmerkingen over de werking van de cmdlet met een specifieke provider, sommige unieke nog belangrijker, maakt gebruik van de cmdlet of manieren om te voorkomen dat mogelijk fouten bevatten.</span><span class="sxs-lookup"><span data-stu-id="0bd20-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="0bd20-106">Er zijn geen beperkingen voor het aantal opmerkingen in die u aan een sectie met opmerkingen toevoegen kunt.</span><span class="sxs-lookup"><span data-stu-id="0bd20-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="0bd20-107">Voor elke opmerking toevoegen een tweetal \<maml:alert > tags aan het \<maml:alertset > knooppunt.</span><span class="sxs-lookup"><span data-stu-id="0bd20-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="0bd20-108">De inhoud van elke opmerking wordt toegevoegd in een set \<maml:para > tags.</span><span class="sxs-lookup"><span data-stu-id="0bd20-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="0bd20-109">Gebruik leeg \<maml:para > tags voor afstand.</span><span class="sxs-lookup"><span data-stu-id="0bd20-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="0bd20-110">De volgende XML bevat een \<maml:alertset > knooppunt met opmerkingen bij de twee.</span><span class="sxs-lookup"><span data-stu-id="0bd20-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="0bd20-111">U ziet dat elke opmerking een optionele is \<maml:title > tag (titels kunnen worden gebruikt voor het groeperen van een set \<maml:alert > tags), en dat elke opmerking heeft een lege regel na de inhoud voor afstand.</span><span class="sxs-lookup"><span data-stu-id="0bd20-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



