---
description: Hierin worden de volledige en relatieve padnaam-indelingen in Power shell beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: b58fdd62803bfb654c9c69acda390d63341aacd9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252706"
---
# <a name="about-path-syntax"></a><span data-ttu-id="a4ed8-104">Syntaxis van pad</span><span class="sxs-lookup"><span data-stu-id="a4ed8-104">About Path Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="a4ed8-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a4ed8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a4ed8-106">Hierin worden de volledige en relatieve padnaam-indelingen in Power shell beschreven.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-106">Describes the full and relative path name formats in  PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a4ed8-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a4ed8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a4ed8-108">Alle items in een gegevens opslag die toegankelijk zijn via een Power shell-provider, kunnen uniek worden aangeduid met hun padnamen.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-108">All items in a data store accessible through a PowerShell provider can be uniquely identified by their path names.</span></span> <span data-ttu-id="a4ed8-109">Een padnaam is een combi natie van de naam van het item, de container en de subcontainers waarin het item zich bevindt en het Power Shell-station waarmee de containers worden geopend.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-109">A path name is a combination of the item name, the container and subcontainers in which the item is located, and the PowerShell drive through which the containers are accessed.</span></span>

<span data-ttu-id="a4ed8-110">In Power shell worden padnamen onderverdeeld in een van de volgende twee typen: volledig gekwalificeerd en relatief.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-110">In PowerShell, path names are divided into one of two types: fully qualified and relative.</span></span> <span data-ttu-id="a4ed8-111">Een volledig gekwalificeerde padnaam bestaat uit alle elementen die een pad vormen.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-111">A fully qualified path name consists of all elements that make up a path.</span></span> <span data-ttu-id="a4ed8-112">Met de volgende syntaxis worden de elementen in een volledig gekwalificeerde padnaam weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="a4ed8-112">The following syntax shows the elements in a fully qualified path name:</span></span>

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

<span data-ttu-id="a4ed8-113">De \<provider\> tijdelijke aanduiding verwijst naar de Power shell-provider waarmee u toegang hebt tot het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-113">The \<provider\> placeholder refers to the PowerShell provider through which you access the data store.</span></span> <span data-ttu-id="a4ed8-114">Zo kunt u met de File System provider toegang krijgen tot de bestanden en mappen op uw computer.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-114">For example, the FileSystem provider allows you to access the files and directories on your computer.</span></span> <span data-ttu-id="a4ed8-115">Dit element van de syntaxis is optioneel en is nooit nodig omdat de namen van de stations uniek zijn voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-115">This element of the syntax is optional and is never needed because the drive names are unique across all providers.</span></span>

<span data-ttu-id="a4ed8-116">De \<drive\> tijdelijke aanduiding verwijst naar het Power Shell-station dat wordt ondersteund door een bepaalde Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-116">The \<drive\> placeholder refers to the PowerShell drive that is supported by a particular PowerShell provider.</span></span> <span data-ttu-id="a4ed8-117">In het geval van de bestandssysteem provider wordt de Power shell-schijf toegewezen aan de Windows-stations die zijn geconfigureerd op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-117">In the case of the FileSystem provider, the PowerShell drives map to the Windows drives that are configured on your system.</span></span> <span data-ttu-id="a4ed8-118">Als uw systeem bijvoorbeeld een station en een C: station bevat, maakt de File System Provider dezelfde stations in Power shell.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-118">For example, if your system includes an A: drive and a C: drive, the FileSystem provider creates the same drives in PowerShell.</span></span>

<span data-ttu-id="a4ed8-119">Nadat u het station hebt opgegeven, moet u alle containers en subcontainers opgeven die het item bevatten.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-119">After you have specified the drive, you must specify any containers and subcontainers that contain the item.</span></span> <span data-ttu-id="a4ed8-120">De containers moeten worden opgegeven in de hiërarchische volg orde waarin ze voor komen in de gegevens opslag.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-120">The containers must be specified in the hierarchical order in which they exist in the data store.</span></span> <span data-ttu-id="a4ed8-121">Met andere woorden, u moet beginnen met de bovenliggende container, vervolgens de onderliggende container in die bovenliggende container, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-121">In other words, you must start with the parent container, then the child container in that parent container, and so on.</span></span> <span data-ttu-id="a4ed8-122">Daarnaast moet elke container worden voorafgegaan door een back slash.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-122">In addition, each container must be preceded by a backslash.</span></span> <span data-ttu-id="a4ed8-123">(Houd er rekening mee dat Power shell voorwaartse slashes voor compatibiliteit met andere Power shells kan gebruiken.)</span><span class="sxs-lookup"><span data-stu-id="a4ed8-123">(Note that PowerShell allows you to use forward slashes for compatibility with other PowerShells.)</span></span>

<span data-ttu-id="a4ed8-124">Nadat de container en de subcontainers zijn opgegeven, moet u de naam van het item opgeven, voorafgegaan door een back slash.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-124">After the container and subcontainers have been specified, you must provide the item name, preceded by a backslash.</span></span> <span data-ttu-id="a4ed8-125">De volledig gekwalificeerde padnaam voor het Shell.dll bestand in de map C: \\ Windows \\ System32 is bijvoorbeeld als volgt:</span><span class="sxs-lookup"><span data-stu-id="a4ed8-125">For example, the fully qualified path name for the Shell.dll file in the C:\\Windows\\System32 directory is as follows:</span></span>

```powershell
C:\Windows\System32\Shell.dll
```

<span data-ttu-id="a4ed8-126">In dit geval is het station waarmee de containers worden geopend, het station C:, de container op het hoogste niveau Windows, is de subcontainer System32 (in de Windows-container) en wordt het item Shell.dll.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-126">In this case, the drive through which the containers are accessed is the C: drive, the top-level container is Windows, the subcontainer is System32 (located within the Windows container), and the item is Shell.dll.</span></span>

<span data-ttu-id="a4ed8-127">In sommige gevallen hoeft u geen volledig gekwalificeerde pad naam op te geven en kunt u in plaats daarvan een relatieve padnaam gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-127">In some situations, you do not need to specify a fully qualified path name and can instead use a relative path name.</span></span> <span data-ttu-id="a4ed8-128">De naam van een relatief pad is gebaseerd op de huidige werk locatie.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-128">A relative path name is based on the current working location.</span></span> <span data-ttu-id="a4ed8-129">Met Power shell kunt u een item identificeren op basis van de locatie relatief ten opzichte van de huidige werk locatie.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-129">PowerShell allows you to identify an item based on its location relative to the current working location.</span></span> <span data-ttu-id="a4ed8-130">U kunt relatieve padnamen opgeven door speciale tekens te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-130">You can specify relative path names by using special characters.</span></span> <span data-ttu-id="a4ed8-131">In de volgende tabel worden deze tekens beschreven en vindt u voor beelden van relatieve padnamen en volledige padnamen.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-131">The following table describes each of these characters and provides examples of relative path names and fully qualified path names.</span></span> <span data-ttu-id="a4ed8-132">De voor beelden in de tabel zijn gebaseerd op de huidige werkmap die is ingesteld op C:\Windows.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-132">The examples in the table are based on the current working directory being set to C:\Windows.</span></span>

|<span data-ttu-id="a4ed8-133">Symbool</span><span class="sxs-lookup"><span data-stu-id="a4ed8-133">Symbol</span></span>|<span data-ttu-id="a4ed8-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4ed8-134">Description</span></span>               |<span data-ttu-id="a4ed8-135">Relatief pad</span><span class="sxs-lookup"><span data-stu-id="a4ed8-135">Relative path</span></span>    |<span data-ttu-id="a4ed8-136">Volledig pad</span><span class="sxs-lookup"><span data-stu-id="a4ed8-136">Full path</span></span>          |
|------|--------------------------|-----------------|-------------------|
|<span data-ttu-id="a4ed8-137">.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-137">.</span></span>     |<span data-ttu-id="a4ed8-138">Huidige locatie</span><span class="sxs-lookup"><span data-stu-id="a4ed8-138">Current location</span></span>          |<span data-ttu-id="a4ed8-139">.\\ Opgehaald</span><span class="sxs-lookup"><span data-stu-id="a4ed8-139">.\\System</span></span>        |<span data-ttu-id="a4ed8-140">c: \\ Windows- \\ systeem</span><span class="sxs-lookup"><span data-stu-id="a4ed8-140">c:\\Windows\\System</span></span>|
|<span data-ttu-id="a4ed8-141">..</span><span class="sxs-lookup"><span data-stu-id="a4ed8-141">..</span></span>    |<span data-ttu-id="a4ed8-142">Bovenliggend item van huidige locatie</span><span class="sxs-lookup"><span data-stu-id="a4ed8-142">Parent of current location</span></span>|<span data-ttu-id="a4ed8-143">..\\ Programma bestanden</span><span class="sxs-lookup"><span data-stu-id="a4ed8-143">..\\Program Files</span></span>|<span data-ttu-id="a4ed8-144">c: \\ Program Files</span><span class="sxs-lookup"><span data-stu-id="a4ed8-144">c:\\Program Files</span></span>  |
|\     |<span data-ttu-id="a4ed8-145">Hoofdmap van huidige station</span><span class="sxs-lookup"><span data-stu-id="a4ed8-145">Drive root of current</span></span>     |<span data-ttu-id="a4ed8-146">\\Programma 's</span><span class="sxs-lookup"><span data-stu-id="a4ed8-146">\\Program Files</span></span>  |<span data-ttu-id="a4ed8-147">c: \\ Program Files</span><span class="sxs-lookup"><span data-stu-id="a4ed8-147">c:\\Program Files</span></span>  |
|      |<span data-ttu-id="a4ed8-148">location</span><span class="sxs-lookup"><span data-stu-id="a4ed8-148">location</span></span>                  |                 |                   |
|<span data-ttu-id="a4ed8-149">geen</span><span class="sxs-lookup"><span data-stu-id="a4ed8-149">[none]</span></span>|<span data-ttu-id="a4ed8-150">Geen speciale tekens</span><span class="sxs-lookup"><span data-stu-id="a4ed8-150">No special characters</span></span>     |<span data-ttu-id="a4ed8-151">Systeem</span><span class="sxs-lookup"><span data-stu-id="a4ed8-151">System</span></span>           |<span data-ttu-id="a4ed8-152">c: \\ Windows- \\ systeem</span><span class="sxs-lookup"><span data-stu-id="a4ed8-152">c:\\Windows\\System</span></span>|

<span data-ttu-id="a4ed8-153">Wanneer u een padnaam in een opdracht gebruikt, voert u deze naam op dezelfde manier in als u een volledig gekwalificeerde padnaam of een relatief pad gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-153">When using a path name in a command, you enter that name in the same way whether you use a fully qualified path name or a relative one.</span></span> <span data-ttu-id="a4ed8-154">Stel bijvoorbeeld dat uw huidige werkmap C:\Windows. is</span><span class="sxs-lookup"><span data-stu-id="a4ed8-154">For example, suppose that your current working directory is C:\Windows.</span></span> <span data-ttu-id="a4ed8-155">Met de volgende Get-ChildItem opdracht worden alle items in de C:\Techdocs-map opgehaald:</span><span class="sxs-lookup"><span data-stu-id="a4ed8-155">The following Get-ChildItem command retrieves all items in the C:\Techdocs directory:</span></span>

```powershell
Get-ChildItem \techdocs
```

<span data-ttu-id="a4ed8-156">De back slash geeft aan dat de hoofdmap van het station van de huidige werk locatie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-156">The backslash indicates that the drive root of the current working location should be used.</span></span> <span data-ttu-id="a4ed8-157">De werkmap is C: \\ Windows, de hoofdmap van het station is station c:.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-157">Because the working directory is C:\\Windows, the drive root is the C: drive.</span></span> <span data-ttu-id="a4ed8-158">Omdat de TechDocs-map zich in de hoofdmap bevindt, hoeft u alleen de back slash op te geven.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-158">Because the techdocs directory is located off the root, you need to specify only the backslash.</span></span>

<span data-ttu-id="a4ed8-159">U kunt dezelfde resultaten krijgen met behulp van de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="a4ed8-159">You can achieve the same results by using the following command:</span></span>

```powershell
Get-ChildItem c:\techdocs
```

<span data-ttu-id="a4ed8-160">Ongeacht of u een volledig gekwalificeerde padnaam of een relatief pad-naam gebruikt, is een padnaam belang rijk, omdat hiermee een item wordt gevonden, maar ook omdat het item op unieke wijze wordt geïdentificeerd, zelfs als dat item dezelfde naam heeft als een ander item in een andere container.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-160">Regardless of whether you use a fully qualified path name or a relative path name, a path name is important not only because it locates an item but also because it uniquely identifies the item even if that item shares the same name as another item in a different container.</span></span>

<span data-ttu-id="a4ed8-161">Stel bijvoorbeeld dat u twee bestanden hebt die elk een naam hebben Results.txt.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-161">For instance, suppose that you have two files that are each named Results.txt.</span></span>
<span data-ttu-id="a4ed8-162">Het eerste bestand bevindt zich in een map met de naam C: \\ TechDocs \\ januari en het tweede bestand bevindt zich in een map met de naam c: \\ TechDocs \\ feb. Met de padnaam voor het eerste bestand (C: \\ TechDocs \\ Jan \\Results.txt) en de padnaam voor het tweede bestand (c: \\ TechDocs \\ februari \\Results.txt) kunt u duidelijk onderscheid maken tussen de twee bestanden.</span><span class="sxs-lookup"><span data-stu-id="a4ed8-162">The first file is in a directory named C:\\Techdocs\\Jan, and the second file is in a directory named C:\\Techdocs\\Feb. The path name for the first file (C:\\Techdocs\\Jan\\Results.txt) and the path name for the second file (C:\\Techdocs\\Feb\\Results.txt) allow you to clearly distinguish between the two files.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4ed8-163">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="a4ed8-163">SEE ALSO</span></span>

[<span data-ttu-id="a4ed8-164">about_Locations</span><span class="sxs-lookup"><span data-stu-id="a4ed8-164">about_Locations</span></span>](about_Locations.md)