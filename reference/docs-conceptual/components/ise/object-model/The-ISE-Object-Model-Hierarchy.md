---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737029"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="cd87b-103">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="cd87b-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="cd87b-104">In dit onderwerp wordt de hiërarchie weer gegeven van objecten die deel uitmaken van Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="cd87b-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="cd87b-105">Windows PowerShell ISE is opgenomen in Windows Power Shell 3,0, 4,0 en 5,1.</span><span class="sxs-lookup"><span data-stu-id="cd87b-105">Windows PowerShell ISE is included in Windows PowerShell 3.0, 4.0, and 5.1.</span></span> <span data-ttu-id="cd87b-106">Klik op een object om naar de referentie documentatie te gaan voor de klasse die het object definieert.</span><span class="sxs-lookup"><span data-stu-id="cd87b-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="cd87b-107">$psISE-object</span><span class="sxs-lookup"><span data-stu-id="cd87b-107">$psISE Object</span></span>

<span data-ttu-id="cd87b-108">Het `$psISE`-object is het [hoofd object](The-ObjectModelRoot-Object.md) van de object hiërarchie Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cd87b-108">The `$psISE` object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="cd87b-109">Op het hoogste niveau worden de volgende objecten beschikbaar gemaakt voor het uitvoeren van scripts:</span><span class="sxs-lookup"><span data-stu-id="cd87b-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="cd87b-110">$psISE. CurrentFile</span><span class="sxs-lookup"><span data-stu-id="cd87b-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="cd87b-111">Het `$psISE.CurrentFile`-object is een instantie van de klasse [ISEFile](The-ISEFile-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-111">The `$psISE.CurrentFile` object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="cd87b-112">$psISE. CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="cd87b-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="cd87b-113">Het `$psISE.CurrentPowerShellTab`-object is een instantie van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-113">The `$psISE.CurrentPowerShellTab` object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="cd87b-114">$psISE. CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="cd87b-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="cd87b-115">Het `$psISE.CurrentVisibleHorizontalTool`-object is een instantie van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-115">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="cd87b-116">Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de bovenrand van het Windows PowerShell ISE-venster.</span><span class="sxs-lookup"><span data-stu-id="cd87b-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="cd87b-117">$psISE. CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="cd87b-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="cd87b-118">Het `$psISE.CurrentVisibleHorizontalTool`-object is een instantie van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-118">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="cd87b-119">Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de rechter rand van het Windows PowerShell ISE-venster.</span><span class="sxs-lookup"><span data-stu-id="cd87b-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="cd87b-120">$psISE. opties</span><span class="sxs-lookup"><span data-stu-id="cd87b-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="cd87b-121">Het `$psISE.Options`-object is een instantie van de klasse [ISEOptions](The-ISEOptions-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-121">The `$psISE.Options` object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span> <span data-ttu-id="cd87b-122">Het ISEOptions-object vertegenwoordigt verschillende instellingen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cd87b-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="cd87b-123">Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="cd87b-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="cd87b-124">$psISE. PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="cd87b-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="cd87b-125">Het `$psISE.PowerShellTabs`-object is een instantie van de klasse [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-125">The `$psISE.PowerShellTabs` object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="cd87b-126">Het is een verzameling van alle momenteel geopende Power shell-tabbladen die de beschik bare Windows Power shell-omgevingen voor uitvoeren op de lokale computer of op verbonden externe computers vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cd87b-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="cd87b-127">Elk lid van de verzameling is een exemplaar van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="cd87b-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd87b-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cd87b-128">See Also</span></span>

- [<span data-ttu-id="cd87b-129">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="cd87b-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cd87b-130">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="cd87b-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
