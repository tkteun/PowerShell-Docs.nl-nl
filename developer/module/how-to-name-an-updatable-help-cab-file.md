---
title: Naamconventies voor een CAB-bestand bij te werken Help | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794754"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="651b0-102">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="651b0-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="651b0-103">Dit onderwerp wordt uitgelegd dat de vereiste indeling voor het bij te werken Help CAB-bestand (. CAB-bestanden).</span><span class="sxs-lookup"><span data-stu-id="651b0-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="651b0-104">CAB-bestand voor een Help die kan worden bijgewerkt een naam geven</span><span class="sxs-lookup"><span data-stu-id="651b0-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="651b0-105">Bij te werken CAB-bestand (. CAB-bestand)-bestand moet een naam met de volgende indeling hebben.</span><span class="sxs-lookup"><span data-stu-id="651b0-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="651b0-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="651b0-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="651b0-107">ModuleName de waarde van de **naam** eigenschap van de **ModuleInfo** object dat de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="651b0-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="651b0-108">ModuleGUID de waarde van de **GUID** sleutel in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="651b0-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="651b0-109">De gebruikersinterface van UICulture cultuur van de help-bestanden in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="651b0-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="651b0-110">Deze waarde moet overeenkomen met de waarde van een van de **UICulture** elementen in het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="651b0-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="651b0-111">Bijvoorbeeld als naam van de module "TestModule", 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, is de GUID van de module wordt en de gebruikersinterfacecultuur 'en-US' is, is de naam van het CAB-bestand:</span><span class="sxs-lookup"><span data-stu-id="651b0-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`