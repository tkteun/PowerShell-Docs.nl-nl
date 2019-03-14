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
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794804"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="afab4-102">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="afab4-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="afab4-103">In dit onderwerp wordt uitgelegd dat de vereiste indeling voor de bestanden bij te werken Help-informatie, bekend als HelpInfo XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="afab4-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="afab4-104">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="afab4-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="afab4-105">Een HelpInfo XML-bestand moet een naam met de volgende indeling hebben.</span><span class="sxs-lookup"><span data-stu-id="afab4-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="afab4-106">De elementen van de naam zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="afab4-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="afab4-107">ModuleName de waarde van de **naam** eigenschap van de **ModuleInfo** object dat de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="afab4-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="afab4-108">ModuleGUID de waarde van de **GUID** sleutel in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="afab4-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="afab4-109">Bijvoorbeeld, als de modulenaam van de is 'TestModule' en de GUID-module 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 is, zou de naam van het HelpInfo XML-bestand voor de module zijn:</span><span class="sxs-lookup"><span data-stu-id="afab4-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`