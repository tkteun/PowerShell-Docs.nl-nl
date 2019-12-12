---
title: Fout informatie weer geven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359367"
---
# <a name="displaying-error-information"></a><span data-ttu-id="de6c4-102">Foutgegevens weergeven</span><span class="sxs-lookup"><span data-stu-id="de6c4-102">Displaying Error Information</span></span>

<span data-ttu-id="de6c4-103">In dit onderwerp worden de manieren beschreven waarop gebruikers fout gegevens kunnen weer geven.</span><span class="sxs-lookup"><span data-stu-id="de6c4-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="de6c4-104">Wanneer de cmdlet een fout tegen komt, is de presentatie van de fout informatie standaard vergelijkbaar met de volgende fout uitvoer.</span><span class="sxs-lookup"><span data-stu-id="de6c4-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="de6c4-105">Gebruikers kunnen echter fouten op categorie bekijken door de `$ErrorView` variabele in te stellen op `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="de6c4-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="de6c4-106">In de categorie weergave worden specifieke gegevens uit de fout record weer gegeven in plaats van een vrije-tekst beschrijving van de fout.</span><span class="sxs-lookup"><span data-stu-id="de6c4-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="de6c4-107">Deze weer gave kan nuttig zijn als u een lange lijst met fouten wilt scannen.</span><span class="sxs-lookup"><span data-stu-id="de6c4-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="de6c4-108">In de categorie weergave wordt het vorige fout bericht als volgt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="de6c4-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="de6c4-109">Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout categorieën.</span><span class="sxs-lookup"><span data-stu-id="de6c4-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de6c4-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="de6c4-110">See Also</span></span>

[<span data-ttu-id="de6c4-111">Windows Power Shell-fout records</span><span class="sxs-lookup"><span data-stu-id="de6c4-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="de6c4-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="de6c4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
