---
title: Een CAB-bestand voor bijwerk bare Help-namen geven | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357433"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="0117f-102">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="0117f-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="0117f-103">In dit onderwerp wordt de vereiste naam indeling voor het Help-Cabinet dat kan worden bijgewerkt (. CAB-bestanden).</span><span class="sxs-lookup"><span data-stu-id="0117f-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="0117f-104">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="0117f-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="0117f-105">Een CAB-archief dat kan worden bijgewerkt (. CAB-bestand moet een naam hebben met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="0117f-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="0117f-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="0117f-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="0117f-107">Module naam de waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0117f-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="0117f-108">ModuleGUID de waarde van de **GUID** -sleutel in het manifest van de module.</span><span class="sxs-lookup"><span data-stu-id="0117f-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="0117f-109">UICulture de UI-cultuur van de Help-bestanden in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="0117f-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="0117f-110">Deze waarde moet overeenkomen met de waarde van een van de **uiCulture** -elementen in het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="0117f-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="0117f-111">Als de module naam bijvoorbeeld ' TestModule ' is, is de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 en de GEBRUIKERSINTERFACE cultuur ' en-US '. de naam van het CAB-bestand zou zijn:</span><span class="sxs-lookup"><span data-stu-id="0117f-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`