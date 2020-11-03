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
ms.openlocfilehash: e14d322fb2f964f06c064c1f9878dc3033947520
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2020
ms.locfileid: "93252029"
---
# <span data-ttu-id="88000-103">PSReadLine-module</span><span class="sxs-lookup"><span data-stu-id="88000-103">PSReadLine Module</span></span>

## <span data-ttu-id="88000-104">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="88000-104">Description</span></span>

<span data-ttu-id="88000-105">De PSReadLine-module bevat cmdlets waarmee u de bewerkings omgeving van de opdracht regel in Power shell kunt aanpassen.</span><span class="sxs-lookup"><span data-stu-id="88000-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="88000-106">In deze artikelen worden PSReadLine v 2.0 gedocumenteerd.</span><span class="sxs-lookup"><span data-stu-id="88000-106">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="88000-107">Deze versie wordt geleverd in Power shell V6 en de update voor Windows 10 oktober 2018 (build 1809).</span><span class="sxs-lookup"><span data-stu-id="88000-107">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="88000-108">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="88000-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="88000-109">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="88000-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="88000-110">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="88000-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="88000-111">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="88000-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="88000-112">PSReadLine-cmdlets</span><span class="sxs-lookup"><span data-stu-id="88000-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="88000-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="88000-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="88000-114">Het hoofd toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="88000-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="88000-115">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="88000-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="88000-116">Hiermee worden de sleutel bindingen voor de PSReadLine-module opgehaald.</span><span class="sxs-lookup"><span data-stu-id="88000-116">Gets the key bindings for the PSReadLine module.</span></span>

### [<span data-ttu-id="88000-117">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="88000-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="88000-118">Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="88000-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="88000-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="88000-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="88000-120">Deze functie is het belangrijkste toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="88000-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="88000-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="88000-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="88000-122">Hiermee verwijdert u een sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="88000-122">Removes a key binding.</span></span>

### [<span data-ttu-id="88000-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="88000-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="88000-124">Koppelt sleutels aan door de gebruiker gedefinieerde of PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="88000-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="88000-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="88000-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="88000-126">Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.</span><span class="sxs-lookup"><span data-stu-id="88000-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

