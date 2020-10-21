---
title: Notities toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 10/20/2020
ms.openlocfilehash: 7f8be34a82de2c12cfd2a05deed139ddb30da95f
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298315"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="fdd83-102">Notities toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="fdd83-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="fdd83-103">In deze sectie wordt beschreven hoe u een sectie **notities** kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fdd83-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="fdd83-104">De sectie **notities** wordt gebruikt om de details te verklaren die niet eenvoudig in de andere gestructureerde secties passen, zoals een gedetailleerdere uitleg van een para meter.</span><span class="sxs-lookup"><span data-stu-id="fdd83-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="fdd83-105">Deze inhoud kan ook opmerkingen bevatten over de werking van de cmdlet met een specifieke provider, een unieke, nog belang rijke, gebruiks vorm van de cmdlet of manieren om mogelijke fout situaties te voor komen.</span><span class="sxs-lookup"><span data-stu-id="fdd83-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="fdd83-106">De sectie **notities** is gedefinieerd met behulp van één `<maml:alertset>` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="fdd83-106">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="fdd83-107">Er zijn geen beperkingen voor het aantal notities dat u kunt toevoegen aan een sectie Notities.</span><span class="sxs-lookup"><span data-stu-id="fdd83-107">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="fdd83-108">Voeg voor elke notitie een paar tags toe `<maml:alert>` aan het `<maml:alertset>` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="fdd83-108">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="fdd83-109">De inhoud van elke notitie wordt toegevoegd binnen een set met `<maml:para>` Tags.</span><span class="sxs-lookup"><span data-stu-id="fdd83-109">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="fdd83-110">Lege `<maml:para>` labels gebruiken voor afstand.</span><span class="sxs-lookup"><span data-stu-id="fdd83-110">Use blank `<maml:para>` tags for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
