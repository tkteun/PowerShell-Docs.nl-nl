---
title: Fout informatie weer geven | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774572"
---
# <a name="displaying-error-information"></a><span data-ttu-id="7b197-102">Foutgegevens weergeven</span><span class="sxs-lookup"><span data-stu-id="7b197-102">Displaying Error Information</span></span>

<span data-ttu-id="7b197-103">In dit onderwerp worden de manieren beschreven waarop gebruikers fout gegevens kunnen weer geven.</span><span class="sxs-lookup"><span data-stu-id="7b197-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="7b197-104">Wanneer de cmdlet een fout tegen komt, is de presentatie van de fout informatie standaard vergelijkbaar met de volgende fout uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7b197-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="7b197-105">Gebruikers kunnen echter fouten op categorie bekijken door de `$ErrorView` variabele in te stellen `"CategoryView"` op.</span><span class="sxs-lookup"><span data-stu-id="7b197-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="7b197-106">In de categorie weergave worden specifieke gegevens uit de fout record weer gegeven in plaats van een vrije-tekst beschrijving van de fout.</span><span class="sxs-lookup"><span data-stu-id="7b197-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="7b197-107">Deze weer gave kan nuttig zijn als u een lange lijst met fouten wilt scannen.</span><span class="sxs-lookup"><span data-stu-id="7b197-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="7b197-108">In de categorie weergave wordt het vorige fout bericht als volgt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7b197-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="7b197-109">Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout categorieën.</span><span class="sxs-lookup"><span data-stu-id="7b197-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b197-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7b197-110">See Also</span></span>

[<span data-ttu-id="7b197-111">Windows PowerShell-foutrecords</span><span class="sxs-lookup"><span data-stu-id="7b197-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="7b197-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="7b197-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
