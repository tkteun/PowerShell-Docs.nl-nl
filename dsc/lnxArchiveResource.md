---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxArchive Resource
ms.openlocfilehash: 142f0317914f1bd3a0523d706b19662f3f64c8b6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="395cd-103">DSC voor Linux nxArchive Resource</span><span class="sxs-lookup"><span data-stu-id="395cd-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="395cd-104">De **nxArchive** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het uitpakken van bestanden te archiveren (tar, .zip) op een specifiek pad op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="395cd-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="395cd-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="395cd-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="395cd-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="395cd-106">Properties</span></span>

|  <span data-ttu-id="395cd-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="395cd-107">Property</span></span> |  <span data-ttu-id="395cd-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="395cd-108">Description</span></span> |
|---|---|
| <span data-ttu-id="395cd-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="395cd-109">SourcePath</span></span>| <span data-ttu-id="395cd-110">Hiermee geeft u het bronpad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="395cd-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="395cd-111">Dit moet een tar .zip, of..GZ-bestand.</span><span class="sxs-lookup"><span data-stu-id="395cd-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="395cd-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="395cd-112">DestinationPath</span></span>| <span data-ttu-id="395cd-113">Hiermee geeft u de locatie waar u Zorg ervoor dat de inhoud van het archief worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="395cd-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="395cd-114">Controlesom</span><span class="sxs-lookup"><span data-stu-id="395cd-114">Checksum</span></span>| <span data-ttu-id="395cd-115">Definieert het type moet worden gebruikt bij het bepalen of de bron-archief is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="395cd-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="395cd-116">Waarden zijn: 'ctime', 'mtime' of 'md5'.</span><span class="sxs-lookup"><span data-stu-id="395cd-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="395cd-117">De standaardwaarde is 'md5'.</span><span class="sxs-lookup"><span data-stu-id="395cd-117">The default value is "md5".</span></span>|
| <span data-ttu-id="395cd-118">Force</span><span class="sxs-lookup"><span data-stu-id="395cd-118">Force</span></span>| <span data-ttu-id="395cd-119">Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een map die is niet leeg) leidt tot een fout opgetreden.</span><span class="sxs-lookup"><span data-stu-id="395cd-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="395cd-120">Met behulp van de **Force** eigenschap heeft een dergelijke fouten.</span><span class="sxs-lookup"><span data-stu-id="395cd-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="395cd-121">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="395cd-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="395cd-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="395cd-122">DependsOn</span></span> | <span data-ttu-id="395cd-123">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="395cd-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="395cd-124">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="395cd-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="395cd-125">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="395cd-125">Ensure</span></span>| <span data-ttu-id="395cd-126">Hiermee bepaalt u of Controleer of de inhoud van het archief bestaat op de **bestemming**.</span><span class="sxs-lookup"><span data-stu-id="395cd-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="395cd-127">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="395cd-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="395cd-128">Stel deze in op 'Ontbreekt' om te controleren of dat ze bestaan niet.</span><span class="sxs-lookup"><span data-stu-id="395cd-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="395cd-129">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="395cd-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="395cd-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="395cd-130">Example</span></span>

<span data-ttu-id="395cd-131">Het volgende voorbeeld ziet u hoe u de **nxArchive** resource om ervoor te zorgen dat de inhoud van een archiefbestand aangeroepen `website.tar` bestaan en op een bepaalde bestemming worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="395cd-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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