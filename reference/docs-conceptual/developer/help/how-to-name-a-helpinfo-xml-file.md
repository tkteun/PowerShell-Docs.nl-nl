---
ms.date: 09/12/2016
ms.topic: reference
title: Een naam geven aan een HelpInfo-XML-bestand
description: Een naam geven aan een HelpInfo-XML-bestand
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659043"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="dd681-103">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="dd681-103">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="dd681-104">In dit onderwerp wordt de vereiste naam indeling uitgelegd voor de Help-informatie bestanden die kunnen worden bijgewerkt, ook wel bekend als HelpInfo XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="dd681-104">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="dd681-105">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="dd681-105">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="dd681-106">Een HelpInfo XML-bestand moet een naam hebben met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="dd681-106">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="dd681-107">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="dd681-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="dd681-108">`<ModuleName>` -De waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dd681-108">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="dd681-109">`<ModuleGUID>` -De waarde van de **GUID** -sleutel in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="dd681-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="dd681-110">Als de module naam bijvoorbeeld ' TestModule ' is en de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, zou de naam van het HelpInfo XML-bestand voor de module er als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="dd681-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
