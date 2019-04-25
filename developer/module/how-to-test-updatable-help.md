---
title: Bij te werken Help testen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082323"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="64dcf-102">Help testen die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="64dcf-102">How to Test Updatable Help</span></span>

<span data-ttu-id="64dcf-103">Dit onderwerp beschrijft de methoden voor het testen van de bij te werken Help voor een module.</span><span class="sxs-lookup"><span data-stu-id="64dcf-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="64dcf-104">Met behulp van uitgebreide voor het detecteren van fouten</span><span class="sxs-lookup"><span data-stu-id="64dcf-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="64dcf-105">Na het uploaden van de HelpInfo XML-bestand en het CAB-bestanden voor de module, kunt u de bestanden testen door het uitvoeren van een [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) opdracht met de **uitgebreid** parameter.</span><span class="sxs-lookup"><span data-stu-id="64dcf-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="64dcf-106">De **uitgebreid** parameter stuurt `Update-Help` voor het rapporteren van de belangrijke stappen in de acties van lezen de **HelpInfoUri** sleutel in de module-manifest voor het valideren van de bestandstypen in de uitgepakte CAB-bestand en de bestanden in de modulemap taalspecifieke plaatsen.</span><span class="sxs-lookup"><span data-stu-id="64dcf-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="64dcf-107">Wanneer alle uitgebreide berichten opgelost worden, voert een `Update-Help` opdracht met de **Debug** parameter.</span><span class="sxs-lookup"><span data-stu-id="64dcf-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="64dcf-108">Deze parameter moet eventuele resterende problemen met de bestanden bij te werken Help detecteren.</span><span class="sxs-lookup"><span data-stu-id="64dcf-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>