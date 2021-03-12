---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 9425f72ce4002fa871ef6b687d76f92ddf6b489e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193897"
---
# <span data-ttu-id="e3c29-102">PSReadLine-module</span><span class="sxs-lookup"><span data-stu-id="e3c29-102">PSReadLine Module</span></span>

## <span data-ttu-id="e3c29-103">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e3c29-103">Description</span></span>

<span data-ttu-id="e3c29-104">De PSReadLine-module bevat cmdlets waarmee u de bewerkings omgeving van de opdracht regel in Power shell kunt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="e3c29-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="e3c29-105">In deze artikelen wordt de huidige bèta versie van PSReadLine v 2.2.0 document gedocumenteerd.</span><span class="sxs-lookup"><span data-stu-id="e3c29-105">These articles document the current beta version of PSReadLine v2.2.0.</span></span>

> [!NOTE]
> <span data-ttu-id="e3c29-106">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="e3c29-106">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="e3c29-107">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="e3c29-107">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="e3c29-108">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="e3c29-108">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="e3c29-109">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="e3c29-109">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="e3c29-110">PSReadLine-cmdlets</span><span class="sxs-lookup"><span data-stu-id="e3c29-110">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="e3c29-111">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="e3c29-111">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="e3c29-112">Het hoofd toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="e3c29-112">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="e3c29-113">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="e3c29-113">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="e3c29-114">Hiermee haalt u de gebonden-sleutel functies voor de PSReadLine-module op.</span><span class="sxs-lookup"><span data-stu-id="e3c29-114">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="e3c29-115">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="e3c29-115">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="e3c29-116">Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="e3c29-116">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="e3c29-117">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="e3c29-117">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="e3c29-118">Deze functie is het belangrijkste toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="e3c29-118">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="e3c29-119">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="e3c29-119">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="e3c29-120">Hiermee verwijdert u een sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="e3c29-120">Removes a key binding.</span></span>

### [<span data-ttu-id="e3c29-121">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="e3c29-121">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="e3c29-122">Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="e3c29-122">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="e3c29-123">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="e3c29-123">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="e3c29-124">Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.</span><span class="sxs-lookup"><span data-stu-id="e3c29-124">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

