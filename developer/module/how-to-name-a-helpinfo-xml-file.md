---
title: Naamconventies voor een HelpInfo XML-bestand | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848088"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="f59b0-102">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="f59b0-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="f59b0-103">In dit onderwerp wordt uitgelegd dat de vereiste indeling voor de bestanden bij te werken Help-informatie, bekend als HelpInfo XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="f59b0-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="f59b0-104">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="f59b0-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="f59b0-105">Een HelpInfo XML-bestand moet een naam met de volgende indeling hebben.</span><span class="sxs-lookup"><span data-stu-id="f59b0-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="f59b0-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="f59b0-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="f59b0-107">ModuleName de waarde van de **naam** eigenschap van de **ModuleInfo** object dat de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="f59b0-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="f59b0-108">De waarde van de **naam** eigenschap van de **ModuleInfo** object dat de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="f59b0-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="f59b0-109">ModuleGUID de waarde van de **GUID** sleutel in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="f59b0-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="f59b0-110">Bijvoorbeeld, als de modulenaam van de is 'TestModule' en de GUID-module 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 is, zou de naam van het HelpInfo XML-bestand voor de module zijn:</span><span class="sxs-lookup"><span data-stu-id="f59b0-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`