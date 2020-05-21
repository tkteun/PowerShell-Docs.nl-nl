---
title: De Help-informatie die kan worden bijgewerkt, testen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: 8dd3770a60ca56634ad1eb1ac8cf89d96c975c90
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560505"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="3bd0b-102">Help testen die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="3bd0b-102">How to Test Updatable Help</span></span>

<span data-ttu-id="3bd0b-103">In dit onderwerp worden benaderingen beschreven voor het testen van de Help-informatie voor een module.</span><span class="sxs-lookup"><span data-stu-id="3bd0b-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="3bd0b-104">Uitgebreide detectie gebruiken om fouten te detecteren</span><span class="sxs-lookup"><span data-stu-id="3bd0b-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="3bd0b-105">Nadat u het HelpInfo XML-bestand en de CAB-bestanden voor uw module hebt geüpload, test u de bestanden door de opdracht [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) uit te voeren met de para meter **uitgebreid** .</span><span class="sxs-lookup"><span data-stu-id="3bd0b-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="3bd0b-106">De para meter **uitgebreid** `Update-Help` om de kritieke stappen in de acties te melden, van het lezen van de sleutel **HelpInfoUri** in het manifest van de module voor het valideren van de bestands typen in het uitgepakte CAB-bestand en het plaatsen van de bestanden in de taalspecifieke module directory.</span><span class="sxs-lookup"><span data-stu-id="3bd0b-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="3bd0b-107">Wanneer alle uitgebreide berichten zijn opgelost, voert u een `Update-Help` opdracht uit met de para meter **debug** .</span><span class="sxs-lookup"><span data-stu-id="3bd0b-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="3bd0b-108">Met deze para meter moeten eventuele resterende problemen worden gedetecteerd met de Help-bestanden die kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="3bd0b-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
