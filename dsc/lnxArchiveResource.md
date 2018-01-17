---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxArchive Resource
ms.openlocfilehash: e91ef5bcf4bdf413844c23d1d3bd823a535b536f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="40313-103">DSC voor Linux nxArchive Resource</span><span class="sxs-lookup"><span data-stu-id="40313-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="40313-104">De **nxArchive** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het uitpakken van bestanden te archiveren (tar, .zip) op een specifiek pad op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="40313-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="40313-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="40313-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="40313-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="40313-106">Properties</span></span>

|  <span data-ttu-id="40313-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="40313-107">Property</span></span> |  <span data-ttu-id="40313-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="40313-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="40313-109">SourcePath</span><span class="sxs-lookup"><span data-stu-id="40313-109">SourcePath</span></span>| <span data-ttu-id="40313-110">Hiermee geeft u het bronpad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="40313-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="40313-111">Dit moet een tar .zip, of..GZ-bestand.</span><span class="sxs-lookup"><span data-stu-id="40313-111">This should be a .tar, .zip, or .tar.gz file.</span></span> | 
| <span data-ttu-id="40313-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="40313-112">DestinationPath</span></span>| <span data-ttu-id="40313-113">Hiermee geeft u de locatie waar u Zorg ervoor dat de inhoud van het archief worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="40313-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>| 
| <span data-ttu-id="40313-114">Controlesom</span><span class="sxs-lookup"><span data-stu-id="40313-114">Checksum</span></span>| <span data-ttu-id="40313-115">Definieert het type moet worden gebruikt bij het bepalen of de bron-archief is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="40313-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="40313-116">Waarden zijn: 'ctime', 'mtime' of 'md5'.</span><span class="sxs-lookup"><span data-stu-id="40313-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="40313-117">De standaardwaarde is 'md5'.</span><span class="sxs-lookup"><span data-stu-id="40313-117">The default value is "md5".</span></span>| 
| <span data-ttu-id="40313-118">Force</span><span class="sxs-lookup"><span data-stu-id="40313-118">Force</span></span>| <span data-ttu-id="40313-119">Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een map die is niet leeg) leidt tot een fout opgetreden.</span><span class="sxs-lookup"><span data-stu-id="40313-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="40313-120">Met behulp van de **Force** eigenschap heeft een dergelijke fouten.</span><span class="sxs-lookup"><span data-stu-id="40313-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="40313-121">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="40313-121">The default value is **$false**.</span></span>| 
| <span data-ttu-id="40313-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="40313-122">DependsOn</span></span> | <span data-ttu-id="40313-123">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="40313-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="40313-124">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="40313-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="40313-125">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="40313-125">Ensure</span></span>| <span data-ttu-id="40313-126">Hiermee bepaalt u of Controleer of de inhoud van het archief bestaat op de **bestemming**.</span><span class="sxs-lookup"><span data-stu-id="40313-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="40313-127">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="40313-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="40313-128">Stel deze in op 'Ontbreekt' om te controleren of dat ze bestaan niet.</span><span class="sxs-lookup"><span data-stu-id="40313-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="40313-129">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="40313-129">The default value is "Present".</span></span>| 

## <a name="example"></a><span data-ttu-id="40313-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="40313-130">Example</span></span>

<span data-ttu-id="40313-131">Het volgende voorbeeld ziet u hoe u de **nxArchive** resource om ervoor te zorgen dat de inhoud van een archiefbestand aangeroepen `website.tar` bestaan en op een bepaalde bestemming worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="40313-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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

