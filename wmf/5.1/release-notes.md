---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Releaseopmerkingen WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055578"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="43556-103">Windows Management Framework (WMF) 5.1 Release Notes</span><span class="sxs-lookup"><span data-stu-id="43556-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span>

<span data-ttu-id="43556-104">WMF 5.1 omvat de PowerShell-, WMI-, WinRM- en Software Inventory Logging (SIL)-onderdelen die zijn uitgebracht met Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="43556-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="43556-105">WMF 5.1 kan worden geïnstalleerd op Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 en 2012 R2 en biedt een aantal verbeteringen ten opzichte van WMF 5.0 RTM, waaronder:</span><span class="sxs-lookup"><span data-stu-id="43556-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="43556-106">Nieuwe cmdlets: lokale gebruikers en groepen; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="43556-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="43556-107">PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules</span><span class="sxs-lookup"><span data-stu-id="43556-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="43556-108">Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten</span><span class="sxs-lookup"><span data-stu-id="43556-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="43556-109">Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="43556-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="43556-110">Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="43556-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="43556-111">Antwoorden op een aantal gebruikersaanvragen en -problemen</span><span class="sxs-lookup"><span data-stu-id="43556-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="43556-112">**Belangrijke opmerkingen:**</span><span class="sxs-lookup"><span data-stu-id="43556-112">**Important notes:**</span></span>

- <span data-ttu-id="43556-113">**WMF 5.1 vereist .NET Framework 4.5.2** (of hoger).</span><span class="sxs-lookup"><span data-stu-id="43556-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="43556-114">Installatie wordt voltooid, maar de belangrijkste functies mislukken als .NET 4.5.2 (of hoger) is niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="43556-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="43556-115">Instructies zijn beschikbaar in de [installeren en configureren van WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) onderwerp.</span><span class="sxs-lookup"><span data-stu-id="43556-115">Instructions are available in the [Install and Configure WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="43556-116">Preview-versie van WMF 5.1 moet worden verwijderd voordat de installatie van WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="43556-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="43556-117">WMF 5.1 kan rechtstreeks via WMF 5.0 of WMF 4.0 worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="43556-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="43556-118">Het is __niet vereist__ WMF 4.0 installeren voordat u WMF 5.1 installeert op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="43556-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="43556-119">Dat is een probleem voor de WMF 5.1 Preview-versie en is opgelost.</span><span class="sxs-lookup"><span data-stu-id="43556-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>
