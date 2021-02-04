---
title: Inleiding
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: Dit is de introductie van het boek Power shell 101 van Mike F. Robbins.
ms.openlocfilehash: bb6ab1a95404b5d6d5595d62df136a937a1faee4
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216170"
---
# <a name="introduction"></a><span data-ttu-id="34cef-103">Introductie</span><span class="sxs-lookup"><span data-stu-id="34cef-103">Introduction</span></span>

<table>
  <tr><td>
  <a href="https://leanpub.com/powershell101">
  <img src="media/powershell101-150x194.png" alt="PowerShell 101 (the book)" />
  </a>
  </td>
  <td colspan=2>
<span data-ttu-id="34cef-104">Deze inhoud werd oorspronkelijk weer gegeven in de boek- <em>Power shell 101</em> door Mike F Robbins.</span><span class="sxs-lookup"><span data-stu-id="34cef-104">This content originally appeared in the book <em>PowerShell 101</em> by Mike F Robbins.</span></span> <span data-ttu-id="34cef-105">Bedankt voor het verlenen van ons toestemming om de inhoud hier opnieuw te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="34cef-105">We thank Mike for granting us permission to reuse his content here.</span></span> <span data-ttu-id="34cef-106">De inhoud is bewerkt vanuit de oorspronkelijke publicatie.</span><span class="sxs-lookup"><span data-stu-id="34cef-106">The content has been edited from the original publication.</span></span> <span data-ttu-id="34cef-107">U kunt nog steeds het oorspronkelijke boek ophalen van Leanpub in <a href="https://leanpub.com/powershell101">Power shell 101</a>.</span><span class="sxs-lookup"><span data-stu-id="34cef-107">You can still get the original book from Leanpub at <a href="https://leanpub.com/powershell101">PowerShell 101</a>.</span></span>
  </td></tr>
</table>

## <a name="who-is-this-book-for"></a><span data-ttu-id="34cef-108">Wie is dit boek voor?</span><span class="sxs-lookup"><span data-stu-id="34cef-108">Who is this book for?</span></span>

<span data-ttu-id="34cef-109">Dit is een post-level-boek voor iedereen die Power shell wilt leren kennen.</span><span class="sxs-lookup"><span data-stu-id="34cef-109">This is an entry-level book for anyone wanting to learn PowerShell.</span></span>

<span data-ttu-id="34cef-110">Dit boek richt zich op de Power shell-versie 5,1 die wordt uitgevoerd op Windows 10 en Windows Server 2016 in een micro soft Active Directory-domein omgeving.</span><span class="sxs-lookup"><span data-stu-id="34cef-110">This book focuses on PowerShell version 5.1 running on Windows 10 and Windows Server 2016 in a Microsoft Active Directory domain environment.</span></span> <span data-ttu-id="34cef-111">De basis concepten zijn echter van toepassing op alle versies van Power shell die worden uitgevoerd op elk ondersteund platform.</span><span class="sxs-lookup"><span data-stu-id="34cef-111">However, the basic concepts apply to all versions of PowerShell running on any supported platform.</span></span>

## <a name="about-this-book"></a><span data-ttu-id="34cef-112">Over dit boek</span><span class="sxs-lookup"><span data-stu-id="34cef-112">About this book</span></span>

<span data-ttu-id="34cef-113">Dit boek is een verzameling van wat ik wil weten wanneer ik Power shell begon te leren, samen met de tips, trucs en aanbevolen procedures die ik heb geleerd tijdens het gebruik van Power shell in de afgelopen tien jaar.</span><span class="sxs-lookup"><span data-stu-id="34cef-113">This book is a collection of what I wish someone would have told me when I started learning PowerShell, along with the tips, tricks, and best practices that I've learned while using PowerShell during the past 10 years.</span></span>

<span data-ttu-id="34cef-114">In plaats van een enorme hoeveelheid informatie te bieden, probeert dit boek een evenwicht te bieden met voldoende informatie om te slagen voor iemand die net aan de slag gaat met Power shell.</span><span class="sxs-lookup"><span data-stu-id="34cef-114">Instead of providing an enormous amount of information, this book attempts to provide a balance of enough information to be successful for someone who is just getting started with PowerShell.</span></span> <span data-ttu-id="34cef-115">Elk hoofd stuk bevat koppelingen naar specifieke Help-onderwerpen voor personen die meer informatie willen over de onderwerpen die in dat hoofd stuk worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="34cef-115">Each chapter contains links to specific help topics for those who want more information about the topics covered in that chapter.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="34cef-116">Over de auteur</span><span class="sxs-lookup"><span data-stu-id="34cef-116">About the author</span></span>

<span data-ttu-id="34cef-117">Mike F Robbins is een voormalige micro soft MVP, coauthor van _Windows Power shell tfm 4e Edition_ en een bijdragende auteur in het _Power shell-diep gaande Dives_ Book.</span><span class="sxs-lookup"><span data-stu-id="34cef-117">Mike F Robbins is a former Microsoft MVP, co-author of _Windows PowerShell TFM 4th Edition_, and a contributing author in the _PowerShell Deep Dives_ book.</span></span> <span data-ttu-id="34cef-118">Mike is een krachtige ondersteunings functie van de Power shell-Community en is nu de lead schrijver voor [Azure PowerShell][] bij micro soft.</span><span class="sxs-lookup"><span data-stu-id="34cef-118">Mike has been a strong supporter of the PowerShell community and is now the lead writer for [Azure PowerShell][] at Microsoft.</span></span> <span data-ttu-id="34cef-119">De blogs op [mikefrobbins.com][] en zijn te vinden op Twitter [@mikefrobbins][] .</span><span class="sxs-lookup"><span data-stu-id="34cef-119">He blogs at [mikefrobbins.com][] and can be found on twitter [@mikefrobbins][].</span></span>

## <a name="lab-environment"></a><span data-ttu-id="34cef-120">Test omgeving</span><span class="sxs-lookup"><span data-stu-id="34cef-120">Lab environment</span></span>

<span data-ttu-id="34cef-121">De voor beelden in dit boek zijn ontworpen en getest op Windows 10 jubileum Edition (build 1607) en Windows Server 2016 met behulp van Power shell-versie 5,1.</span><span class="sxs-lookup"><span data-stu-id="34cef-121">The examples in this book were designed and tested on Windows 10 Anniversary Edition (build 1607) and Windows Server 2016 using PowerShell version 5.1.</span></span> <span data-ttu-id="34cef-122">Als u een andere versie van Power shell of het besturings systeem gebruikt, kunnen de resultaten afwijken van die hier worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="34cef-122">If you're using a different version of PowerShell or operating system, your results may differ from those shown here.</span></span>

<!-- link references -->
[@mikefrobbins]: https://twitter.com/mikefrobbins
[mikefrobbins.com]: http://mikefrobbins.com/
[PowerShell 101]: https://leanpub.com/powershell101
[Azure PowerShell]: /powershell/azure
