---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxArchive-Resource
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078041"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="de832-103">DSC voor Linux nxArchive-Resource</span><span class="sxs-lookup"><span data-stu-id="de832-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="de832-104">De **nxArchive** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het uitpakken van bestanden te archiveren (.tar, .zip) op een specifiek pad op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="de832-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="de832-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="de832-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="de832-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="de832-106">Properties</span></span>

|  <span data-ttu-id="de832-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="de832-107">Property</span></span> |  <span data-ttu-id="de832-108">Description</span><span class="sxs-lookup"><span data-stu-id="de832-108">Description</span></span> |
|---|---|
| <span data-ttu-id="de832-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="de832-109">SourcePath</span></span>| <span data-ttu-id="de832-110">Hiermee geeft u het bronpad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="de832-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="de832-111">Dit moet een .tar .zip, of..GZ-bestand.</span><span class="sxs-lookup"><span data-stu-id="de832-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="de832-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="de832-112">DestinationPath</span></span>| <span data-ttu-id="de832-113">Hiermee geeft u de locatie waar u om te controleren of de dat inhoud van het archief worden geëxtraheerd.</span><span class="sxs-lookup"><span data-stu-id="de832-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="de832-114">Controlesom</span><span class="sxs-lookup"><span data-stu-id="de832-114">Checksum</span></span>| <span data-ttu-id="de832-115">Definieert het type te gebruiken bij het bepalen of de bron-archief is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="de832-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="de832-116">Waarden zijn: 'ctime","mtime"of 'md5'.</span><span class="sxs-lookup"><span data-stu-id="de832-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="de832-117">De standaardwaarde is 'md5'.</span><span class="sxs-lookup"><span data-stu-id="de832-117">The default value is "md5".</span></span>|
| <span data-ttu-id="de832-118">Force</span><span class="sxs-lookup"><span data-stu-id="de832-118">Force</span></span>| <span data-ttu-id="de832-119">Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt.</span><span class="sxs-lookup"><span data-stu-id="de832-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="de832-120">Met behulp van de **Force** eigenschap heeft voorrang op dergelijke fouten.</span><span class="sxs-lookup"><span data-stu-id="de832-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="de832-121">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="de832-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="de832-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="de832-122">DependsOn</span></span> | <span data-ttu-id="de832-123">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="de832-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="de832-124">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="de832-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="de832-125">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="de832-125">Ensure</span></span>| <span data-ttu-id="de832-126">Hiermee bepaalt u of om te controleren of de inhoud van het archief bestaat op de **bestemming**.</span><span class="sxs-lookup"><span data-stu-id="de832-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="de832-127">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="de832-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="de832-128">Stel deze in op 'Ontbreekt' om te controleren of dat ze bestaan niet.</span><span class="sxs-lookup"><span data-stu-id="de832-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="de832-129">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="de832-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="de832-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="de832-130">Example</span></span>

<span data-ttu-id="de832-131">Het volgende voorbeeld ziet u hoe u de **nxArchive** resource om ervoor te zorgen dat de inhoud van een archiefbestand genoemd `website.tar` bestaan en op een bepaalde bestemming worden geëxtraheerd.</span><span class="sxs-lookup"><span data-stu-id="de832-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```