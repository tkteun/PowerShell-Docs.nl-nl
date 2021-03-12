---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113630
Help Version: 7.0.1.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: fc059318507b7a875eedf47692c1b6e3572efbbc
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195551"
---
# <span data-ttu-id="7e3da-103">PSReadLine-module</span><span class="sxs-lookup"><span data-stu-id="7e3da-103">PSReadLine Module</span></span>

## <span data-ttu-id="7e3da-104">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7e3da-104">Description</span></span>

<span data-ttu-id="7e3da-105">De PSReadLine-module bevat cmdlets waarmee u de bewerkings omgeving van de opdracht regel in Power shell kunt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="7e3da-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="7e3da-106">Deze artikelen documenteren PSReadLine v 2.0.</span><span class="sxs-lookup"><span data-stu-id="7e3da-106">These articles document PSReadLine v2.0.</span></span> <span data-ttu-id="7e3da-107">Deze versie wordt geleverd in Power shell V6 en de update voor Windows 10 oktober 2018 (build 1809).</span><span class="sxs-lookup"><span data-stu-id="7e3da-107">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="7e3da-108">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="7e3da-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="7e3da-109">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="7e3da-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="7e3da-110">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="7e3da-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="7e3da-111">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="7e3da-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="7e3da-112">PSReadLine-cmdlets</span><span class="sxs-lookup"><span data-stu-id="7e3da-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="7e3da-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="7e3da-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="7e3da-114">Het hoofd toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="7e3da-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="7e3da-115">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7e3da-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="7e3da-116">Hiermee worden de sleutel bindingen voor de PSReadLine-module opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7e3da-116">Gets the key bindings for the PSReadLine module.</span></span>

### [<span data-ttu-id="7e3da-117">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7e3da-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="7e3da-118">Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="7e3da-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="7e3da-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="7e3da-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="7e3da-120">Deze functie is het belangrijkste toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="7e3da-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="7e3da-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7e3da-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="7e3da-122">Hiermee verwijdert u een sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="7e3da-122">Removes a key binding.</span></span>

### [<span data-ttu-id="7e3da-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7e3da-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="7e3da-124">Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="7e3da-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="7e3da-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7e3da-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="7e3da-126">Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.</span><span class="sxs-lookup"><span data-stu-id="7e3da-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

