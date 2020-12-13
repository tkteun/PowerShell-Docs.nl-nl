---
ms.date: 09/12/2016
ms.topic: reference
title: Help testen die kan worden bijgewerkt
description: Help testen die kan worden bijgewerkt
ms.openlocfilehash: 47873089bfa1b918ea9970915e829a22aa7254c5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667620"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="bd717-103">Help testen die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="bd717-103">How to Test Updatable Help</span></span>

<span data-ttu-id="bd717-104">In dit onderwerp worden benaderingen beschreven voor het testen van de Help-informatie voor een module.</span><span class="sxs-lookup"><span data-stu-id="bd717-104">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="bd717-105">Uitgebreide detectie gebruiken om fouten te detecteren</span><span class="sxs-lookup"><span data-stu-id="bd717-105">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="bd717-106">Nadat u het HelpInfo XML-bestand en de CAB-bestanden voor uw module hebt geüpload, test u de bestanden door de opdracht [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) uit te voeren met de para meter **uitgebreid** .</span><span class="sxs-lookup"><span data-stu-id="bd717-106">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="bd717-107">De para meter **uitgebreid** `Update-Help` om de kritieke stappen in de acties te melden, van het lezen van de sleutel **HelpInfoUri** in het manifest van de module voor het valideren van de bestands typen in het uitgepakte CAB-bestand en het plaatsen van de bestanden in de taalspecifieke module directory.</span><span class="sxs-lookup"><span data-stu-id="bd717-107">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="bd717-108">Wanneer alle uitgebreide berichten zijn opgelost, voert u een `Update-Help` opdracht uit met de para meter **debug** .</span><span class="sxs-lookup"><span data-stu-id="bd717-108">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span>
<span data-ttu-id="bd717-109">Met deze para meter moeten eventuele resterende problemen worden gedetecteerd met de Help-bestanden die kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="bd717-109">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
