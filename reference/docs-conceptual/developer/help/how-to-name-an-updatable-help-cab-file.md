---
title: CAB-bestand voor een Help die kan worden bijgewerkt een naam geven
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892996"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="75237-102">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="75237-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="75237-103">In dit onderwerp wordt de vereiste naam indeling voor de bij te werken cab- `.CAB` bestanden () beschreven.</span><span class="sxs-lookup"><span data-stu-id="75237-103">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="75237-104">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="75237-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="75237-105">Een cab `.CAB` -bestand dat kan worden bijgewerkt, moet een naam hebben met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="75237-105">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="75237-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="75237-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="75237-107">`<ModuleName>` -De waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="75237-107">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="75237-108">`<ModuleGUID>` -De waarde van de **GUID** -sleutel in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="75237-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="75237-109">`<UICulture>` -De UI-cultuur van de Help-bestanden in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="75237-109">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="75237-110">Deze waarde moet overeenkomen met de waarde van een van de **uiCulture** -elementen in het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="75237-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="75237-111">Als de module naam bijvoorbeeld ' TestModule ' is, is de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 en de GEBRUIKERSINTERFACE cultuur ' en-US '. de naam van het CAB-bestand zou zijn:</span><span class="sxs-lookup"><span data-stu-id="75237-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
