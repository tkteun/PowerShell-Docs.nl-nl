---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "De hiërarchie ISE"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="e58a5-103">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="e58a5-103">The ISE Object Model Hierarchy</span></span>
<span data-ttu-id="e58a5-104">Dit onderwerp bevat de hiërarchie van objecten die deel uitmaken van Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="e58a5-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="e58a5-105">Windows PowerShell ISE is opgenomen in Windows PowerShell 3.0 en Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="e58a5-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="e58a5-106">Klik op een object waarmee u de documentatie bij de klasse die het object definieert.</span><span class="sxs-lookup"><span data-stu-id="e58a5-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="e58a5-107">$psISE object</span><span class="sxs-lookup"><span data-stu-id="e58a5-107">$psISE Object</span></span>

<span data-ttu-id="e58a5-108">De **$psISE** -object is de [hoofdobject](The-ObjectModelRoot-Object.md) van de hiërarchie van Windows PowerShell ISE-object.</span><span class="sxs-lookup"><span data-stu-id="e58a5-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="e58a5-109">Zich bevindt op het hoogste niveau, maakt de volgende objecten beschikbaar zijn voor het uitvoeren van scripts:</span><span class="sxs-lookup"><span data-stu-id="e58a5-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="e58a5-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="e58a5-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="e58a5-111">De **$psISE.CurrentFile** object is een exemplaar van de [ISEFile](The-ISEFile-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="e58a5-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="e58a5-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="e58a5-113">De **$psISE.CurrentPowerShellTab** object is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="e58a5-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="e58a5-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="e58a5-115">De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="e58a5-116">Deze vertegenwoordigt het geïnstalleerde invoegtoepassing hulpprogramma dat momenteel is gekoppeld aan de bovenkant van het Windows PowerShell ISE-venster.</span><span class="sxs-lookup"><span data-stu-id="e58a5-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="e58a5-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="e58a5-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="e58a5-118">De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="e58a5-119">Deze vertegenwoordigt het geïnstalleerde invoegtoepassing hulpprogramma dat momenteel is gekoppeld aan de rechterzijde van het Windows PowerShell ISE-venster.</span><span class="sxs-lookup"><span data-stu-id="e58a5-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="e58a5-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="e58a5-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="e58a5-121">De **$psISE.Options** object is een exemplaar van de [ISEOptions](The-ISEOptions-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="e58a5-122">Het object ISEOptions vertegenwoordigt diverse instellingen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e58a5-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="e58a5-123">Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="e58a5-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="e58a5-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="e58a5-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="e58a5-125">De **$psISE.PowerShellTabs** object is een exemplaar van de [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="e58a5-126">Er is een verzameling van alle geopende PowerShell tabbladen met daarin de beschikbare Windows PowerShell op de lokale computer of op externe computers verbonden omgevingen uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e58a5-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="e58a5-127">Elk lid in de verzameling is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.</span><span class="sxs-lookup"><span data-stu-id="e58a5-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e58a5-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e58a5-128">See Also</span></span>
- [<span data-ttu-id="e58a5-129">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="e58a5-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e58a5-130">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="e58a5-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
