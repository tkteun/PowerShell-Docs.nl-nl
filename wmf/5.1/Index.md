---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Releaseopmerkingen WMF 5.1
ms.openlocfilehash: 3512d2e80501a596e1fd6d7b33d4d75286cef1b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189785"
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="e465a-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="e465a-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="e465a-104">WMF biedt gebruikers de mogelijkheid bestaande Windows-systemen bij te werken naar de versies van de PowerShell-, WMI-, WinRM- en Software Inventory Logging (SIL)-onderdelen die zijn uitgebracht met Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="e465a-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="e465a-105">WMF 5.1 kan worden geïnstalleerd op Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 en 2012 R2 en biedt een aantal verbeteringen ten opzichte van WMF 5.0 RTM, waaronder:</span><span class="sxs-lookup"><span data-stu-id="e465a-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="e465a-106">Nieuwe cmdlets: lokale gebruikers en groepen; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="e465a-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="e465a-107">PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules</span><span class="sxs-lookup"><span data-stu-id="e465a-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="e465a-108">Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten</span><span class="sxs-lookup"><span data-stu-id="e465a-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="e465a-109">Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="e465a-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="e465a-110">Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="e465a-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="e465a-111">Antwoorden op een aantal gebruikersaanvragen en -problemen</span><span class="sxs-lookup"><span data-stu-id="e465a-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="e465a-112">Raadpleeg voor meer informatie over wat er nieuw is in deze release de onderwerpen onder [Nieuwe scenario's en onderdelen](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="e465a-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="e465a-113">In de sectie [Installeren en configureren](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) vindt u de vereisten en installatie-instructies voor WMF.</span><span class="sxs-lookup"><span data-stu-id="e465a-113">The [Install and Configure](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="e465a-114">De sectie [Compatibiliteit](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) behandelt welke versies van WMF kunnen worden geïnstalleerd op welke Windows-versies.</span><span class="sxs-lookup"><span data-stu-id="e465a-114">The [Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="e465a-115">De sectie [Productcompatibiliteit](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) geeft aan welke Microsoft-toepassingen op dit moment niet zijn goedgekeurd voor gebruik met WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="e465a-115">[Product Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="e465a-116">Voor meer informatie over de onderdelen van WMF raadpleegt u de MSDN-documentatie:</span><span class="sxs-lookup"><span data-stu-id="e465a-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="e465a-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e465a-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/en-us/powershell/)
- <span data-ttu-id="e465a-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e465a-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="e465a-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e465a-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="e465a-120">[Registratie van software-inventaris](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="e465a-120">[Software Inventory Logging](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span></span>
