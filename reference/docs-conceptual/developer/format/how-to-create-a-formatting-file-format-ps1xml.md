---
ms.date: 09/13/2016
ms.topic: reference
title: Een opmaakbestand (.format.ps1xml) maken
description: Een opmaakbestand (.format.ps1xml) maken
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652009"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="3d5ff-103">Een opmaakbestand (.format.ps1xml) maken</span><span class="sxs-lookup"><span data-stu-id="3d5ff-103">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="3d5ff-104">In dit onderwerp wordt beschreven hoe u een opmaak bestand maakt (.format.ps1XML).</span><span class="sxs-lookup"><span data-stu-id="3d5ff-104">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="3d5ff-105">U kunt ook een opmaak bestand maken door een kopie te maken van een van de bestanden die worden meegeleverd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-105">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="3d5ff-106">Als u een kopie van een bestaand bestand maakt, verwijdert u de bestaande digitale hand tekening en voegt u uw eigen hand tekening toe aan het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-106">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="3d5ff-107">Een .format.ps1XML-bestand maken.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-107">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="3d5ff-108">Maak een tekst bestand (. txt) met behulp van een tekst editor zoals Klad blok.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-108">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="3d5ff-109">Kopieer de volgende regels naar het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-109">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="3d5ff-110">De `<Configuration></Configuration>` Tags definiëren het hoofd `Configuration` knooppunt.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-110">The `<Configuration></Configuration>` tags define the root `Configuration` node.</span></span> <span data-ttu-id="3d5ff-111">Alle extra XML-tags worden inge sloten binnen dit knoop punt.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-111">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="3d5ff-112">De `<ViewDefinitions></ViewDefinitions>` Tags bepalen het `ViewDefinitions` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-112">The `<ViewDefinitions></ViewDefinitions>` tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="3d5ff-113">Alle weer gaven worden binnen dit knoop punt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-113">All views are defined within this node.</span></span>

3. <span data-ttu-id="3d5ff-114">Sla het bestand op naar de installatiemap van Windows Power shell, naar de map module, of naar een submap van de map module.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-114">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="3d5ff-115">Gebruik de volgende naam indeling wanneer u het bestand opslaat:  `MyFile.format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="3d5ff-115">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="3d5ff-116">Het format teren van bestanden moet de `.format.ps1xml` extensie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-116">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="3d5ff-117">U bent nu klaar om weer gaven toe te voegen aan het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-117">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="3d5ff-118">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-118">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="3d5ff-119">U kunt één weer gave voor elk object, meerdere weer gaven voor hetzelfde object of één weer gave die wordt gebruikt door meerdere objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3d5ff-119">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d5ff-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3d5ff-120">See Also</span></span>

[<span data-ttu-id="3d5ff-121">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3d5ff-121">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
