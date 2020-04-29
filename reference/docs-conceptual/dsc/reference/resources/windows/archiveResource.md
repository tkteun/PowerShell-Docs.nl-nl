---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-archief resource
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942515"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="9635d-103">DSC-archief resource</span><span class="sxs-lookup"><span data-stu-id="9635d-103">DSC Archive Resource</span></span>

> <span data-ttu-id="9635d-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="9635d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="9635d-105">De archief resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitpakken van archief bestanden (. zip) op een specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="9635d-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="9635d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9635d-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="9635d-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="9635d-107">Properties</span></span>

|<span data-ttu-id="9635d-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9635d-108">Property</span></span> |<span data-ttu-id="9635d-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9635d-109">Description</span></span> |
|---|---|
|<span data-ttu-id="9635d-110">Doel</span><span class="sxs-lookup"><span data-stu-id="9635d-110">Destination</span></span> |<span data-ttu-id="9635d-111">Hiermee geeft u de locatie op waar de archief inhoud moet worden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="9635d-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
|<span data-ttu-id="9635d-112">Pad</span><span class="sxs-lookup"><span data-stu-id="9635d-112">Path</span></span> |<span data-ttu-id="9635d-113">Hiermee geeft u het bronpad van het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="9635d-113">Specifies the source path of the archive file.</span></span> |
|<span data-ttu-id="9635d-114">Controlesom</span><span class="sxs-lookup"><span data-stu-id="9635d-114">Checksum</span></span> |<span data-ttu-id="9635d-115">Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="9635d-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="9635d-116">Als er geen **controlesom** is opgegeven, wordt alleen de naam van het bestand of de map gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="9635d-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="9635d-117">Geldige waarden zijn: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="9635d-117">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> <span data-ttu-id="9635d-118">Als u **controlesom** zonder **validatie**opgeeft, mislukt de configuratie.</span><span class="sxs-lookup"><span data-stu-id="9635d-118">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> |
|<span data-ttu-id="9635d-119">Force</span><span class="sxs-lookup"><span data-stu-id="9635d-119">Force</span></span> |<span data-ttu-id="9635d-120">Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout.</span><span class="sxs-lookup"><span data-stu-id="9635d-120">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="9635d-121">Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9635d-121">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="9635d-122">De standaard waarde is **False**.</span><span class="sxs-lookup"><span data-stu-id="9635d-122">The default value is **False**.</span></span> |
|<span data-ttu-id="9635d-123">Valideren</span><span class="sxs-lookup"><span data-stu-id="9635d-123">Validate</span></span>| <span data-ttu-id="9635d-124">Maakt gebruik van de eigenschap **checksum** om te bepalen of het archief overeenkomt met de hand tekening.</span><span class="sxs-lookup"><span data-stu-id="9635d-124">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="9635d-125">Als u **controlesom** zonder **validatie**opgeeft, mislukt de configuratie.</span><span class="sxs-lookup"><span data-stu-id="9635d-125">If you specify **Checksum** without **Validate**, the configuration will fail.</span></span> <span data-ttu-id="9635d-126">Als u **Validate** zonder **controlesom**opgeeft, wordt standaard een _SHA-256-_ **controlesom** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9635d-126">If you specify **Validate** without **Checksum**, a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9635d-127">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="9635d-127">Common properties</span></span>

|<span data-ttu-id="9635d-128">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9635d-128">Property</span></span> |<span data-ttu-id="9635d-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9635d-129">Description</span></span> |
|---|---|
|<span data-ttu-id="9635d-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9635d-130">DependsOn</span></span> |<span data-ttu-id="9635d-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="9635d-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9635d-132">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="9635d-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="9635d-133">Zo</span><span class="sxs-lookup"><span data-stu-id="9635d-133">Ensure</span></span> |<span data-ttu-id="9635d-134">Hiermee wordt bepaald of wordt gecontroleerd of de inhoud van het archief bestaat op de **bestemming**.</span><span class="sxs-lookup"><span data-stu-id="9635d-134">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="9635d-135">Stel deze eigenschap in op **aanwezig** om te controleren of de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="9635d-135">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="9635d-136">Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="9635d-136">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="9635d-137">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="9635d-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="9635d-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9635d-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="9635d-139">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="9635d-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="9635d-140">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="9635d-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="9635d-141">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9635d-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="9635d-142">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9635d-142">Example</span></span>

<span data-ttu-id="9635d-143">In het volgende voor beeld ziet u hoe u de archief resource gebruikt om ervoor te zorgen dat de inhoud `Test.zip` van een archief bestand bestaat en op een bepaalde bestemming wordt geëxtraheerd.</span><span class="sxs-lookup"><span data-stu-id="9635d-143">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```