---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Grondbeginselen van Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: 7b5cdfce876aa7d5559fe772379829011b275a02
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="d05b9-103">Grondbeginselen van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d05b9-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="d05b9-104">Grafische gebruikersinterfaces gebruiken aantal basisconcepten die bekend bij de meeste computergebruikers.</span><span class="sxs-lookup"><span data-stu-id="d05b9-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="d05b9-105">Gebruikers, is afhankelijk van de kennis van deze interfaces voor het uitvoeren van taken.</span><span class="sxs-lookup"><span data-stu-id="d05b9-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="d05b9-106">Besturingssystemen huidige gebruikers met een grafische weergave van items die kunnen worden bekeken, meestal met vervolgkeuzemenu's voor toegang tot bepaalde functionaliteit en context menu's voor toegang tot specifieke context-functies.</span><span class="sxs-lookup"><span data-stu-id="d05b9-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="d05b9-107">Een opdrachtregelinterface (CLI), zoals Windows PowerShell, moet een andere benadering gebruiken om informatie weer te geven omdat er geen menu's of grafische systemen om te helpen de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d05b9-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="d05b9-108">U moet weten opdrachtnamen voordat u ze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d05b9-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="d05b9-109">Hoewel u kunt complexe opdrachten die equivalent aan de functies in een omgeving met GUI zijn typt, moet u meer vertrouwd raken met veelgebruikte opdrachten en opdrachtparameters.</span><span class="sxs-lookup"><span data-stu-id="d05b9-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="d05b9-110">De meeste CLIs hoeft geen patronen die kunnen helpen bij de gebruiker voor meer informatie over de interface.</span><span class="sxs-lookup"><span data-stu-id="d05b9-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="d05b9-111">Omdat CLIs de eerste besturingssysteem houders zijn, zijn veel namen van opdrachten en parameternamen geselecteerd willekeurig.</span><span class="sxs-lookup"><span data-stu-id="d05b9-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="d05b9-112">Beknopte opdrachtnamen zijn over het algemeen over wissen cijfers gekozen.</span><span class="sxs-lookup"><span data-stu-id="d05b9-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="d05b9-113">Hoewel help-systemen en opdracht ontwerpstandaarden worden geïntegreerd in de meeste CLIs, ze zijn doorgaans ontworpen voor compatibiliteit met de vroegste opdrachten, zodat de opdrachtenset nog steeds wordt gevormd door beslissingen tientallen jaren geleden.</span><span class="sxs-lookup"><span data-stu-id="d05b9-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="d05b9-114">Windows PowerShell is ontworpen om te profiteren van een gebruiker historische kennis van CLIs.</span><span class="sxs-lookup"><span data-stu-id="d05b9-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="d05b9-115">In dit hoofdstuk wordt waar het over enkele eenvoudige hulpprogramma's en concepten die u gebruiken kunt voor meer informatie over Windows PowerShell snel.</span><span class="sxs-lookup"><span data-stu-id="d05b9-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="d05b9-116">Ze omvatten:</span><span class="sxs-lookup"><span data-stu-id="d05b9-116">They include:</span></span>

- <span data-ttu-id="d05b9-117">Met behulp van de opdracht Get</span><span class="sxs-lookup"><span data-stu-id="d05b9-117">Using Get-Command</span></span>

- <span data-ttu-id="d05b9-118">Met behulp van Cmd.exe- en UNIX-opdrachten</span><span class="sxs-lookup"><span data-stu-id="d05b9-118">Using Cmd.exe and UNIX commands</span></span>

- <span data-ttu-id="d05b9-119">Met behulp van externe opdrachten</span><span class="sxs-lookup"><span data-stu-id="d05b9-119">Using External Commands</span></span>

- <span data-ttu-id="d05b9-120">Met behulp van tabblad voltooiing</span><span class="sxs-lookup"><span data-stu-id="d05b9-120">Using Tab-Completion</span></span>

- <span data-ttu-id="d05b9-121">Gebruik Get-Help</span><span class="sxs-lookup"><span data-stu-id="d05b9-121">Using Get-Help</span></span>

