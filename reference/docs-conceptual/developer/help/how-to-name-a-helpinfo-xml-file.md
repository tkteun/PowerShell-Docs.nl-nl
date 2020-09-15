---
title: Een naam geven aan een HelpInfo-XML-bestand
ms.date: 09/12/2016
ms.openlocfilehash: 9505a7f66852a569d25ac0c1be86e68f870a7930
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892928"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="16d86-102">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="16d86-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="16d86-103">In dit onderwerp wordt de vereiste naam indeling uitgelegd voor de Help-informatie bestanden die kunnen worden bijgewerkt, ook wel bekend als HelpInfo XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="16d86-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="16d86-104">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="16d86-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="16d86-105">Een HelpInfo XML-bestand moet een naam hebben met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="16d86-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="16d86-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="16d86-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="16d86-107">`<ModuleName>` -De waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="16d86-107">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="16d86-108">`<ModuleGUID>` -De waarde van de **GUID** -sleutel in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="16d86-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="16d86-109">Als de module naam bijvoorbeeld ' TestModule ' is en de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, zou de naam van het HelpInfo XML-bestand voor de module er als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="16d86-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
