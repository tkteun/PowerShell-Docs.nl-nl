---
title: Notities toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893404"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="bd013-102">Notities toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="bd013-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="bd013-103">In deze sectie wordt beschreven hoe u een sectie **notities** kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd013-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="bd013-104">De sectie **notities** wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter.</span><span class="sxs-lookup"><span data-stu-id="bd013-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="bd013-105">Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.</span><span class="sxs-lookup"><span data-stu-id="bd013-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="bd013-106">Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities.</span><span class="sxs-lookup"><span data-stu-id="bd013-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="bd013-107">Voeg voor elke notitie een paar tags toe `<maml:alert>` aan het `<maml:alertset>` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="bd013-107">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="bd013-108">De inhoud van elke notitie wordt toegevoegd binnen een set met `<maml:para>` Tags.</span><span class="sxs-lookup"><span data-stu-id="bd013-108">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="bd013-109">Lege `<maml:para>` labels gebruiken voor afstand.</span><span class="sxs-lookup"><span data-stu-id="bd013-109">Use blank `<maml:para>` tags for spacing.</span></span>

<span data-ttu-id="bd013-110">De volgende XML-code bevat een `<maml:alertset>` knoop punt met twee notities.</span><span class="sxs-lookup"><span data-stu-id="bd013-110">The following XML shows an `<maml:alertset>` node with two notes.</span></span> <span data-ttu-id="bd013-111">U ziet dat elke notitie een optionele `<maml:title>` tag heeft (titels kunnen worden gebruikt voor het groeperen van een wille keurige set `<maml:alert>` Tags) en dat elke notitie een lege regel heeft na de inhoud voor afstand.</span><span class="sxs-lookup"><span data-stu-id="bd013-111">Notice that each note has an optional `<maml:title>` tag (titles can be used to group any set of `<maml:alert>` tags), and that each note has a blank line following the content for spacing.</span></span>

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
