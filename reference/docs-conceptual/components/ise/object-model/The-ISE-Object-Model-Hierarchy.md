---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057720"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="b85c1-103">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="b85c1-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="b85c1-104">Dit onderwerp bevat de hiërarchie van objecten die deel uitmaken van Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="b85c1-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="b85c1-105">Windows PowerShell ISE is opgenomen in Windows PowerShell 3.0 en Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="b85c1-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="b85c1-106">Klik op een object waarmee u de referentiedocumentatie voor de klasse die het object definieert.</span><span class="sxs-lookup"><span data-stu-id="b85c1-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="b85c1-107">$psISE Object</span><span class="sxs-lookup"><span data-stu-id="b85c1-107">$psISE Object</span></span>

<span data-ttu-id="b85c1-108">De **$psISE** -object is de [hoofdobject](The-ObjectModelRoot-Object.md) van de hiërarchie van Windows PowerShell ISE-object.</span><span class="sxs-lookup"><span data-stu-id="b85c1-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="b85c1-109">Op het hoogste niveau bevindt, wordt de volgende objecten beschikbaar zijn voor het uitvoeren van scripts:</span><span class="sxs-lookup"><span data-stu-id="b85c1-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="b85c1-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="b85c1-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="b85c1-111">De **$psISE.CurrentFile** object is een exemplaar van de [ISEFile](The-ISEFile-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="b85c1-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="b85c1-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="b85c1-113">De **$psISE.CurrentPowerShellTab** object is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="b85c1-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="b85c1-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="b85c1-115">De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="b85c1-116">Staat voor het hulpprogramma geïnstalleerde invoegtoepassingen die momenteel is gekoppeld aan de bovenkant van de Windows PowerShell ISE-venster.</span><span class="sxs-lookup"><span data-stu-id="b85c1-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="b85c1-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="b85c1-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="b85c1-118">De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="b85c1-119">Staat voor het hulpprogramma geïnstalleerde invoegtoepassingen die momenteel is gekoppeld aan de rechterzijde van de Windows PowerShell ISE-venster.</span><span class="sxs-lookup"><span data-stu-id="b85c1-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="b85c1-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="b85c1-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="b85c1-121">De **$psISE.Options** object is een exemplaar van de [ISEOptions](The-ISEOptions-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="b85c1-122">Het ISEOptions-object vertegenwoordigt diverse instellingen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b85c1-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="b85c1-123">Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="b85c1-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="b85c1-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="b85c1-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="b85c1-125">De **$psISE.PowerShellTabs** object is een exemplaar van de [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="b85c1-126">Er is een verzameling van alle geopende PowerShell tabbladen die staan voor de beschikbare Windows PowerShell op de lokale computer of op externe computers verbonden omgevingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b85c1-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="b85c1-127">Elk lid in de verzameling is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="b85c1-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b85c1-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b85c1-128">See Also</span></span>

- [<span data-ttu-id="b85c1-129">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b85c1-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b85c1-130">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="b85c1-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)