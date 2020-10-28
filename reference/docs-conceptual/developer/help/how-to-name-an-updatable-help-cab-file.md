---
ms.date: 09/12/2016
ms.topic: reference
title: CAB-bestand voor een Help die kan worden bijgewerkt een naam geven
description: CAB-bestand voor een Help die kan worden bijgewerkt een naam geven
ms.openlocfilehash: 57ea188d07a382d1a986a49c9ae22c5919dafa8e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658913"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="5b177-103">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="5b177-103">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="5b177-104">In dit onderwerp wordt de vereiste naam indeling voor de bij te werken cab- `.CAB` bestanden () beschreven.</span><span class="sxs-lookup"><span data-stu-id="5b177-104">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="5b177-105">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="5b177-105">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="5b177-106">Een cab `.CAB` -bestand dat kan worden bijgewerkt, moet een naam hebben met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="5b177-106">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="5b177-107">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="5b177-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="5b177-108">`<ModuleName>` -De waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5b177-108">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="5b177-109">`<ModuleGUID>` -De waarde van de **GUID** -sleutel in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="5b177-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="5b177-110">`<UICulture>` -De UI-cultuur van de Help-bestanden in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="5b177-110">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="5b177-111">Deze waarde moet overeenkomen met de waarde van een van de **uiCulture** -elementen in het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="5b177-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="5b177-112">Als de module naam bijvoorbeeld ' TestModule ' is, is de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 en de GEBRUIKERSINTERFACE cultuur ' en-US '. de naam van het CAB-bestand zou zijn:</span><span class="sxs-lookup"><span data-stu-id="5b177-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
