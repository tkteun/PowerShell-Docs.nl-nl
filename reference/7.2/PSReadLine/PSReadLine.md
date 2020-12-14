---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: da71d4ef896befaadd7ed64f9a013dc19508a54c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705579"
---
# <span data-ttu-id="a6eff-102">PSReadLine-module</span><span class="sxs-lookup"><span data-stu-id="a6eff-102">PSReadLine Module</span></span>

## <span data-ttu-id="a6eff-103">Description</span><span class="sxs-lookup"><span data-stu-id="a6eff-103">Description</span></span>

<span data-ttu-id="a6eff-104">De PSReadLine-module bevat cmdlets waarmee u de bewerkings omgeving van de opdracht regel in Power shell kunt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="a6eff-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="a6eff-105">In deze artikelen worden PSReadLine v 2.0 gedocumenteerd.</span><span class="sxs-lookup"><span data-stu-id="a6eff-105">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="a6eff-106">Deze versie wordt geleverd in Power shell V6 en de update voor Windows 10 oktober 2018 (build 1809).</span><span class="sxs-lookup"><span data-stu-id="a6eff-106">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="a6eff-107">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="a6eff-107">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="a6eff-108">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="a6eff-108">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="a6eff-109">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="a6eff-109">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="a6eff-110">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="a6eff-110">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="a6eff-111">PSReadLine-cmdlets</span><span class="sxs-lookup"><span data-stu-id="a6eff-111">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="a6eff-112">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="a6eff-112">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="a6eff-113">Het hoofd toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a6eff-113">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="a6eff-114">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="a6eff-114">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="a6eff-115">Hiermee haalt u de gebonden-sleutel functies voor de PSReadLine-module op.</span><span class="sxs-lookup"><span data-stu-id="a6eff-115">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="a6eff-116">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="a6eff-116">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="a6eff-117">Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="a6eff-117">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="a6eff-118">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="a6eff-118">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="a6eff-119">Deze functie is het belangrijkste toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a6eff-119">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="a6eff-120">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="a6eff-120">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="a6eff-121">Hiermee verwijdert u een sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="a6eff-121">Removes a key binding.</span></span>

### [<span data-ttu-id="a6eff-122">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="a6eff-122">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="a6eff-123">Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a6eff-123">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="a6eff-124">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="a6eff-124">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="a6eff-125">Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.</span><span class="sxs-lookup"><span data-stu-id="a6eff-125">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

