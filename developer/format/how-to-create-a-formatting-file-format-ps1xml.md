---
title: Over het maken van een opmaak-bestand (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065494"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="99088-102">Een opmaakbestand (.format.ps1xml) maken</span><span class="sxs-lookup"><span data-stu-id="99088-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="99088-103">In dit onderwerp wordt beschreven hoe u een opmaak bestand te maken (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="99088-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="99088-104">U kunt ook een opmaak bestand maken door een kopie van een van de bestanden die worden geleverd door Windows PowerShell te maken.</span><span class="sxs-lookup"><span data-stu-id="99088-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="99088-105">Als u bijvoorbeeld een kopie van een bestaand bestand, verwijder de bestaande digitale handtekening en uw eigen handtekening toevoegen aan het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="99088-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="99088-106">Maakt een. format.ps1xml-bestand.</span><span class="sxs-lookup"><span data-stu-id="99088-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="99088-107">Maak een tekstbestand (.txt) met behulp van een SMS-bericht zoals Kladblok.</span><span class="sxs-lookup"><span data-stu-id="99088-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="99088-108">Kopieer de volgende regels in de opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="99088-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="99088-109">De \<Configuration >\</Configuration > tags definiëren de hoofdmap `Configuration` knooppunt.</span><span class="sxs-lookup"><span data-stu-id="99088-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="99088-110">Alle andere XML-labels wordt ingesloten in dit knooppunt.</span><span class="sxs-lookup"><span data-stu-id="99088-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="99088-111">De <ViewDefinitions> </ViewDefinitions> tags definiëren de `ViewDefinitions` knooppunt.</span><span class="sxs-lookup"><span data-stu-id="99088-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="99088-112">Alle weergaven worden gedefinieerd in dit knooppunt.</span><span class="sxs-lookup"><span data-stu-id="99088-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="99088-113">Sla het bestand naar de installatiemap van Windows PowerShell, naar de modulemap van uw of naar een submap van de modulemap.</span><span class="sxs-lookup"><span data-stu-id="99088-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="99088-114">Gebruik de volgende indeling wanneer u het bestand opslaat: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="99088-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="99088-115">Opmaak bestanden moeten gebruiken de `.format.ps1xml` extensie.</span><span class="sxs-lookup"><span data-stu-id="99088-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="99088-116">U bent nu klaar weergaven toevoegen aan de opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="99088-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="99088-117">Er is geen limiet voor het aantal weergaven die kunnen worden gedefinieerd in een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="99088-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="99088-118">U kunt één weergave voor elk object, meerdere weergaven voor hetzelfde object of een enkelvoudige weergave die wordt gebruikt door meerdere objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="99088-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="99088-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="99088-119">See Also</span></span>

[<span data-ttu-id="99088-120">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="99088-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
