---
title: Een opmaak bestand (. Format. ps1xml) maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354955"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="f336f-102">Een opmaakbestand (.format.ps1xml) maken</span><span class="sxs-lookup"><span data-stu-id="f336f-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="f336f-103">In dit onderwerp wordt beschreven hoe u een opmaak bestand (. Format. ps1xml) maakt.</span><span class="sxs-lookup"><span data-stu-id="f336f-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="f336f-104">U kunt ook een opmaak bestand maken door een kopie te maken van een van de bestanden die worden meegeleverd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="f336f-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="f336f-105">Als u een kopie van een bestaand bestand maakt, verwijdert u de bestaande digitale hand tekening en voegt u uw eigen hand tekening toe aan het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="f336f-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="f336f-106">Maken van een. Format. ps1xml-bestand.</span><span class="sxs-lookup"><span data-stu-id="f336f-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="f336f-107">Maak een tekst bestand (. txt) met behulp van een tekst editor zoals Klad blok.</span><span class="sxs-lookup"><span data-stu-id="f336f-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="f336f-108">Kopieer de volgende regels naar het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f336f-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="f336f-109">Met de \<Configuration >\</configuratie > Tags wordt het hoofd knooppunt `Configuration` gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f336f-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="f336f-110">Alle extra XML-tags worden inge sloten binnen dit knoop punt.</span><span class="sxs-lookup"><span data-stu-id="f336f-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="f336f-111">De <ViewDefinitions></ViewDefinitions> labels definiëren het `ViewDefinitions` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="f336f-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="f336f-112">Alle weer gaven worden binnen dit knoop punt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f336f-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="f336f-113">Sla het bestand op naar de installatiemap van Windows Power shell, naar de map module, of naar een submap van de map module.</span><span class="sxs-lookup"><span data-stu-id="f336f-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="f336f-114">Gebruik de volgende naam indeling wanneer u het bestand opslaat: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="f336f-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="f336f-115">Het format teren van bestanden moet de extensie `.format.ps1xml` gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f336f-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="f336f-116">U bent nu klaar om weer gaven toe te voegen aan het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f336f-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="f336f-117">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f336f-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="f336f-118">U kunt één weer gave voor elk object, meerdere weer gaven voor hetzelfde object of één weer gave die wordt gebruikt door meerdere objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="f336f-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f336f-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f336f-119">See Also</span></span>

[<span data-ttu-id="f336f-120">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f336f-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
