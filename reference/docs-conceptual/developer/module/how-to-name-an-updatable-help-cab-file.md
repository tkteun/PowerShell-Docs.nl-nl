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
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560556"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="1f0ab-102">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="1f0ab-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="1f0ab-103">In dit onderwerp wordt de vereiste naam indeling voor het Help-Cabinet dat kan worden bijgewerkt (. CAB-bestanden).</span><span class="sxs-lookup"><span data-stu-id="1f0ab-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="1f0ab-104">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="1f0ab-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="1f0ab-105">Een CAB-archief dat kan worden bijgewerkt (. CAB-bestand moet een naam hebben met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="1f0ab-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="1f0ab-107">Module naam de waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="1f0ab-108">ModuleGUID de waarde van de **GUID** -sleutel in het manifest van de module.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="1f0ab-109">UICulture de UI-cultuur van de Help-bestanden in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="1f0ab-110">Deze waarde moet overeenkomen met de waarde van een van de **uiCulture** -elementen in het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="1f0ab-111">Als de module naam bijvoorbeeld ' TestModule ' is, is de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 en de GEBRUIKERSINTERFACE cultuur ' en-US '. de naam van het CAB-bestand zou zijn:</span><span class="sxs-lookup"><span data-stu-id="1f0ab-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
