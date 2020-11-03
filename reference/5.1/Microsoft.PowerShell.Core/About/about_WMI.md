---
description: Windows Management Instrumentation (WMI) gebruikt de Common Information Model (CIM) om systemen, toepassingen, netwerken, apparaten en andere beheer bare onderdelen van de moderne onderneming weer te geven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252731"
---
# <a name="about-wmi"></a><span data-ttu-id="5a102-104">Over WMI</span><span class="sxs-lookup"><span data-stu-id="5a102-104">About WMI</span></span>

## <a name="short-description"></a><span data-ttu-id="5a102-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5a102-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="5a102-106">Windows Management Instrumentation (WMI) gebruikt de Common Information Model (CIM) om systemen, toepassingen, netwerken, apparaten en andere beheer bare onderdelen van de moderne onderneming weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5a102-106">Windows Management Instrumentation (WMI) uses the Common Information Model (CIM) to represent systems, applications, networks, devices, and other manageable components of the modern enterprise.</span></span>

## <a name="long-description"></a><span data-ttu-id="5a102-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5a102-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="5a102-108">Windows Management Instrumentation (WMI) is de micro soft-implementatie van Web-Based Enter prise Management (WBEM), de industrie norm.</span><span class="sxs-lookup"><span data-stu-id="5a102-108">Windows Management Instrumentation (WMI) is Microsoft's implementation of Web-Based Enterprise Management (WBEM), the industry standard.</span></span>

<span data-ttu-id="5a102-109">Klassieke WMI maakt gebruik van DCOM om te communiceren met apparaten in het netwerk om externe systemen te beheren.</span><span class="sxs-lookup"><span data-stu-id="5a102-109">Classic WMI uses DCOM to communicate with networked devices to manage remote systems.</span></span> <span data-ttu-id="5a102-110">Windows Power Shell 3,0 introduceert een CIM-provider model dat gebruikmaakt van WinRM voor het verwijderen van de afhankelijkheid van DCOM.</span><span class="sxs-lookup"><span data-stu-id="5a102-110">Windows PowerShell 3.0 introduces a CIM provider model that uses WinRM to remove the dependency on DCOM.</span></span> <span data-ttu-id="5a102-111">In dit CIM-provider model worden ook nieuwe WMI-provider-Api's gebruikt waarmee ontwikkel aars Windows Power shell-cmdlets kunnen schrijven in systeem eigen code (C \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="5a102-111">This CIM provider model also uses new WMI provider APIs that enable developers to write Windows PowerShell cmdlets in native code (C\+\+).</span></span>

<span data-ttu-id="5a102-112">Verwar WMI-providers niet met Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="5a102-112">Do not confuse WMI providers with Windows PowerShell providers.</span></span> <span data-ttu-id="5a102-113">Voor veel Windows-onderdelen is een WMI-provider gekoppeld die de beheer mogelijkheden beschikbaar maakt.</span><span class="sxs-lookup"><span data-stu-id="5a102-113">Many Windows features have an associated WMI provider that exposes their management capabilities.</span></span> <span data-ttu-id="5a102-114">Als u WMI-providers wilt ophalen, voert u een WMI-query uit die exemplaren van de WMI-klasse __Provider, zoals de volgende query.</span><span class="sxs-lookup"><span data-stu-id="5a102-114">To get WMI providers, run a WMI query that gets instances of the __Provider WMI class, such as the following query.</span></span>

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a><span data-ttu-id="5a102-115">DRIE ONDERDELEN VAN WMI</span><span class="sxs-lookup"><span data-stu-id="5a102-115">THREE COMPONENTS OF WMI</span></span>

<span data-ttu-id="5a102-116">De volgende drie onderdelen van WMI communiceren met Windows Power shell: naam ruimten, providers en klassen.</span><span class="sxs-lookup"><span data-stu-id="5a102-116">The following three components of WMI interact with Windows PowerShell: Namespaces, Providers, and Classes.</span></span>

<span data-ttu-id="5a102-117">WMI-naam ruimten worden WMI-providers en WMI-klassen in groepen verwante onderdelen ingedeeld.</span><span class="sxs-lookup"><span data-stu-id="5a102-117">WMI Namespaces organize WMI providers and WMI classes into groups of related components.</span></span> <span data-ttu-id="5a102-118">Op deze manier zijn ze vergelijkbaar met .NET Framework naam ruimten.</span><span class="sxs-lookup"><span data-stu-id="5a102-118">In this way, they are similar to .NET Framework namespaces.</span></span>
<span data-ttu-id="5a102-119">Naam ruimten zijn geen fysieke locaties, maar zijn meer dan logische data bases.</span><span class="sxs-lookup"><span data-stu-id="5a102-119">Namespaces are not physical locations, but are more like logical databases.</span></span>
<span data-ttu-id="5a102-120">Alle WMI-naam ruimten zijn exemplaren van de klasse __Namespace systeem.</span><span class="sxs-lookup"><span data-stu-id="5a102-120">All WMI namespaces are instances of the __Namespace system class.</span></span> <span data-ttu-id="5a102-121">De standaard-WMI-naam ruimte is root \/ CIMV2 (sinds micro soft Windows 2000).</span><span class="sxs-lookup"><span data-stu-id="5a102-121">The default WMI namespace is Root\/CIMV2 (since Microsoft Windows 2000).</span></span> <span data-ttu-id="5a102-122">Als u Windows Power shell wilt gebruiken om WMI-naam ruimten in de huidige sessie op te halen, gebruikt u een opdracht met de volgende indeling.</span><span class="sxs-lookup"><span data-stu-id="5a102-122">To use Windows PowerShell to get WMI namespaces in the current session, use a command with the following format.</span></span>

```powershell
Get-WmiObject -Class __Namespace
```

<span data-ttu-id="5a102-123">Als u WMI-naam ruimten in andere naam ruimten wilt ophalen, gebruikt u de para meter naam ruimte om de locatie van de zoek opdracht te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5a102-123">To get WMI namespaces in other namespaces, use the Namespace parameter to change the location of the search.</span></span> <span data-ttu-id="5a102-124">Met de volgende opdracht vindt u WMI-naam ruimten die zich in de hoofdmap/Cimv2/toepassings naam ruimte bevinden.</span><span class="sxs-lookup"><span data-stu-id="5a102-124">The following command finds WMI namespaces that reside in the Root/Cimv2/Applications namespace.</span></span>

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

<span data-ttu-id="5a102-125">WMI-naam ruimten zijn hiërarchisch.</span><span class="sxs-lookup"><span data-stu-id="5a102-125">WMI namespaces are hierarchical.</span></span> <span data-ttu-id="5a102-126">Daarom moet het verkrijgen van een lijst met alle naam ruimten op een bepaald systeem een recursieve query starten, beginnend bij de hoofd naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="5a102-126">Therefore, obtaining a list of all namespaces on a particular system requires performing a recursive query starting at the root namespace.</span></span>

<span data-ttu-id="5a102-127">WMI-providers bieden informatie over Windows-beheer bare objecten.</span><span class="sxs-lookup"><span data-stu-id="5a102-127">WMI Providers expose information about Windows manageable objects.</span></span> <span data-ttu-id="5a102-128">Een provider haalt gegevens op uit een-onderdeel en geeft die gegevens door aan een beheer toepassing, zoals Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="5a102-128">A provider retrieves data from a component, and passes that data through WMI to a management application, such as Windows PowerShell.</span></span> <span data-ttu-id="5a102-129">De meeste WMI-providers zijn dynamische providers. Dit betekent dat ze de gegevens dynamisch kunnen ophalen wanneer deze worden aangevraagd via de beheer toepassing.</span><span class="sxs-lookup"><span data-stu-id="5a102-129">Most WMI providers are dynamic providers, which means that they obtain the data dynamically when it is requested through the management application.</span></span>

## <a name="finding-wmi-classes"></a><span data-ttu-id="5a102-130">WMI-KLASSEN ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="5a102-130">FINDING WMI CLASSES</span></span>

<span data-ttu-id="5a102-131">In een standaard installatie van Windows 8 zijn er meer dan 1.100 WMI-klassen in de hoofdmap \/ Cimv2.</span><span class="sxs-lookup"><span data-stu-id="5a102-131">In a default installation of Windows 8, there are more than 1,100 WMI classes in Root\/Cimv2.</span></span> <span data-ttu-id="5a102-132">Met dit aantal WMI-klassen wordt de uitdaging de juiste WMI-klasse voor het uitvoeren van een specifieke taak geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="5a102-132">With this many WMI classes, the challenge becomes identifying the appropriate WMI class to use to perform a specific task.</span></span> <span data-ttu-id="5a102-133">Windows Power Shell 3,0 biedt twee manieren om WMI-klassen te vinden die betrekking hebben op een specifiek onderwerp.</span><span class="sxs-lookup"><span data-stu-id="5a102-133">Windows PowerShell 3.0 provides two ways to find WMI classes that are related to a specific topic.</span></span>

<span data-ttu-id="5a102-134">Als u bijvoorbeeld WMI-klassen in de \\ WMI-naam ruimte root CIMV2 wilt vinden die gerelateerd zijn aan schijven, kunt u een query gebruiken zoals die hier wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a102-134">For example,to find WMI classes in the root\\CIMV2 WMI namespace that are related to disks, you can use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *disk*
```

<span data-ttu-id="5a102-135">Als u WMI-klassen wilt vinden die gerelateerd zijn aan het geheugen, kunt u gebruikmaken van een query zoals die hier wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a102-135">To find WMI classes that are related to memory, you might use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *memory*
```

<span data-ttu-id="5a102-136">De CIM-cmdlets bieden ook de mogelijkheid om WMI-klassen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="5a102-136">The CIM cmdlets also provide the ability to discover WMI classes.</span></span> <span data-ttu-id="5a102-137">U kunt dit doen met behulp van de cmdlet Get-CIMClass.</span><span class="sxs-lookup"><span data-stu-id="5a102-137">To do this, use the Get-CIMClass cmdlet.</span></span> <span data-ttu-id="5a102-138">De opdracht die hier wordt weer gegeven, bevat WMI-klassen die betrekking hebben op video.</span><span class="sxs-lookup"><span data-stu-id="5a102-138">The command shown here lists WMI classes related to video.</span></span>

```powershell
Get-CimClass *video*
```

<span data-ttu-id="5a102-139">Tabblad uitbreiding werkt bij het wijzigen van WMI-naam ruimten en daarom kunnen subwmi-naam ruimten gemakkelijk worden gedetecteerd met behulp van een tabblad uitbreiding.</span><span class="sxs-lookup"><span data-stu-id="5a102-139">Tab expansion works when changing WMI namespaces, and therefore use of tab expansion makes sub-WMI namespaces easily discoverable.</span></span> <span data-ttu-id="5a102-140">In het volgende voor beeld geeft de cmdlet Get-CimClass WMI-klassen weer die zijn gerelateerd aan energie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="5a102-140">In the following example, the Get-CimClass cmdlet lists WMI classes related to power settings.</span></span>
<span data-ttu-id="5a102-141">Als u wilt zoeken, typt u de `root/CIMV2/` naam ruimte en drukt u enkele keren op de tab-toets totdat de energie naam ruimte wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a102-141">To find it, type the `root/CIMV2/` namespace and then press the Tab key several times until the power namespace appears.</span></span> <span data-ttu-id="5a102-142">Dit is de opdracht:</span><span class="sxs-lookup"><span data-stu-id="5a102-142">Here is the command:</span></span>

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
