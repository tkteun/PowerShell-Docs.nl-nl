---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxArchive-resource
description: DSC voor Linux nxArchive-resource
ms.openlocfilehash: 2705829ccae0c1baa27324030433340e7f3949c1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648859"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="cbf7f-103">DSC voor Linux nxArchive-resource</span><span class="sxs-lookup"><span data-stu-id="cbf7f-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="cbf7f-104">De **nxArchive** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitpakken van archief bestanden (. tar,. zip) op een specifiek pad op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbf7f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cbf7f-105">Syntax</span></span>

```Syntax
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="cbf7f-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="cbf7f-106">Properties</span></span>

|<span data-ttu-id="cbf7f-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="cbf7f-107">Property</span></span> |<span data-ttu-id="cbf7f-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cbf7f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="cbf7f-109">Bronpad</span><span class="sxs-lookup"><span data-stu-id="cbf7f-109">SourcePath</span></span> |<span data-ttu-id="cbf7f-110">Hiermee geeft u het bronpad van het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="cbf7f-111">Dit moet een. tar-,. zip-of. tar. gz-bestand zijn.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
|<span data-ttu-id="cbf7f-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="cbf7f-112">DestinationPath</span></span> |<span data-ttu-id="cbf7f-113">Hiermee geeft u de locatie op waar de archief inhoud moet worden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="cbf7f-114">Controlesom</span><span class="sxs-lookup"><span data-stu-id="cbf7f-114">Checksum</span></span> |<span data-ttu-id="cbf7f-115">Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of het bron archief is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="cbf7f-116">Waarden zijn: **ctime** , **mtime** of **MD5** .</span><span class="sxs-lookup"><span data-stu-id="cbf7f-116">Values are: **ctime** , **mtime** , or **md5** .</span></span> <span data-ttu-id="cbf7f-117">De standaard waarde is **MD5** .</span><span class="sxs-lookup"><span data-stu-id="cbf7f-117">The default value is **md5** .</span></span> |
|<span data-ttu-id="cbf7f-118">Force</span><span class="sxs-lookup"><span data-stu-id="cbf7f-118">Force</span></span> |<span data-ttu-id="cbf7f-119">Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="cbf7f-120">Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="cbf7f-121">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-121">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="cbf7f-122">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="cbf7f-122">Common properties</span></span>

|<span data-ttu-id="cbf7f-123">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="cbf7f-123">Property</span></span> |<span data-ttu-id="cbf7f-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cbf7f-124">Description</span></span> |
|---|---|
|<span data-ttu-id="cbf7f-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cbf7f-125">DependsOn</span></span> |<span data-ttu-id="cbf7f-126">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cbf7f-127">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="cbf7f-127">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="cbf7f-128">Zo</span><span class="sxs-lookup"><span data-stu-id="cbf7f-128">Ensure</span></span> |<span data-ttu-id="cbf7f-129">Hiermee wordt bepaald of wordt gecontroleerd of de inhoud van het archief bestaat op de **bestemming** .</span><span class="sxs-lookup"><span data-stu-id="cbf7f-129">Determines whether to check if the content of the archive exists at the **Destination** .</span></span> <span data-ttu-id="cbf7f-130">Stel deze eigenschap in op **aanwezig** om te controleren of de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-130">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="cbf7f-131">Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-131">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="cbf7f-132">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="cbf7f-132">The default value is **Present** .</span></span> |

## <a name="example"></a><span data-ttu-id="cbf7f-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="cbf7f-133">Example</span></span>

<span data-ttu-id="cbf7f-134">In het volgende voor beeld ziet u hoe u de **nxArchive** -resource kunt gebruiken om ervoor te zorgen dat de inhoud van een archief bestand met de naam `website.tar` Exists wordt geëxtraheerd op een bepaalde bestemming.</span><span class="sxs-lookup"><span data-stu-id="cbf7f-134">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```powershell
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = "http://release.contoso.com/releases/website.tar"
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = "mtime"
}

nxArchive SyncWebDir
{
   SourcePath = "/usr/release/staging/website.tar"
   DestinationPath = "/usr/local/apache2/htdocs/"
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```
