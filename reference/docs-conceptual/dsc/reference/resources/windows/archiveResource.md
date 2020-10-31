---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-archief resource
description: DSC-archief resource
ms.openlocfilehash: 28e2436683d7cb3b69f894ac75bb1a58b8eb1e8a
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142397"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="d2b9f-103">DSC-archief resource</span><span class="sxs-lookup"><span data-stu-id="d2b9f-103">DSC Archive Resource</span></span>

> <span data-ttu-id="d2b9f-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="d2b9f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d2b9f-105">De archief resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitpakken van archief bestanden (. zip) op een specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="d2b9f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2b9f-106">Syntax</span></span>

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d2b9f-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="d2b9f-107">Properties</span></span>

|<span data-ttu-id="d2b9f-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d2b9f-108">Property</span></span> |<span data-ttu-id="d2b9f-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d2b9f-109">Description</span></span> |
|---|---|
| <span data-ttu-id="d2b9f-110">Doel</span><span class="sxs-lookup"><span data-stu-id="d2b9f-110">Destination</span></span> | <span data-ttu-id="d2b9f-111">Hiermee geeft u de locatie op waar de archief inhoud moet worden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span> |
| <span data-ttu-id="d2b9f-112">Pad</span><span class="sxs-lookup"><span data-stu-id="d2b9f-112">Path</span></span> | <span data-ttu-id="d2b9f-113">Hiermee geeft u het bronpad van het archief bestand.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-113">Specifies the source path of the archive file.</span></span> |
| <span data-ttu-id="d2b9f-114">Controlesom</span><span class="sxs-lookup"><span data-stu-id="d2b9f-114">Checksum</span></span> | <span data-ttu-id="d2b9f-115">Hiermee wordt bepaald welk type moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="d2b9f-116">Als er geen **controlesom** is opgegeven, wordt alleen de naam van het bestand of de map gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-116">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="d2b9f-117">Geldige waarden zijn: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span><span class="sxs-lookup"><span data-stu-id="d2b9f-117">Valid values include: **SHA-1** , **SHA-256** , **SHA-512** , **createdDate** , **modifiedDate** .</span></span> <span data-ttu-id="d2b9f-118">Als u **controlesom** zonder **validatie** opgeeft, mislukt de configuratie.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-118">If you specify **Checksum** without **Validate** , the configuration will fail.</span></span> |
| <span data-ttu-id="d2b9f-119">Referentie</span><span class="sxs-lookup"><span data-stu-id="d2b9f-119">Credential</span></span> | <span data-ttu-id="d2b9f-120">De referentie van een gebruikers account met machtigingen voor toegang tot het opgegeven pad en de bestemming van het archief, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-120">The credential of a user account with permissions to access the specified archive path and destination if needed.</span></span> |
| <span data-ttu-id="d2b9f-121">Force</span><span class="sxs-lookup"><span data-stu-id="d2b9f-121">Force</span></span> | <span data-ttu-id="d2b9f-122">Bepaalde bestands bewerkingen (zoals het overschrijven van een bestand of het verwijderen van een map die niet leeg is), resulteren in een fout.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-122">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="d2b9f-123">Met behulp van de eigenschap **Force** worden dergelijke fouten genegeerd.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-123">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="d2b9f-124">De standaard waarde is **False** .</span><span class="sxs-lookup"><span data-stu-id="d2b9f-124">The default value is **False** .</span></span> |
| <span data-ttu-id="d2b9f-125">Valideren</span><span class="sxs-lookup"><span data-stu-id="d2b9f-125">Validate</span></span>| <span data-ttu-id="d2b9f-126">Maakt gebruik van de eigenschap **checksum** om te bepalen of het archief overeenkomt met de hand tekening.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-126">Uses the **Checksum** property to determine if the archive matches the signature.</span></span> <span data-ttu-id="d2b9f-127">Als u **controlesom** zonder **validatie** opgeeft, mislukt de configuratie.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-127">If you specify **Checksum** without **Validate** , the configuration will fail.</span></span> <span data-ttu-id="d2b9f-128">Als u **Validate** zonder **controlesom** opgeeft, wordt standaard een _SHA-256-_ **controlesom** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-128">If you specify **Validate** without **Checksum** , a _SHA-256_ **Checksum** is used by default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d2b9f-129">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="d2b9f-129">Common properties</span></span>

|<span data-ttu-id="d2b9f-130">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d2b9f-130">Property</span></span> |<span data-ttu-id="d2b9f-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d2b9f-131">Description</span></span> |
|---|---|
|<span data-ttu-id="d2b9f-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d2b9f-132">DependsOn</span></span> |<span data-ttu-id="d2b9f-133">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d2b9f-134">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="d2b9f-134">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d2b9f-135">Zo</span><span class="sxs-lookup"><span data-stu-id="d2b9f-135">Ensure</span></span> |<span data-ttu-id="d2b9f-136">Hiermee wordt bepaald of wordt gecontroleerd of de inhoud van het archief bestaat op de **bestemming** .</span><span class="sxs-lookup"><span data-stu-id="d2b9f-136">Determines whether to check if the content of the archive exists at the **Destination** .</span></span> <span data-ttu-id="d2b9f-137">Stel deze eigenschap in op **aanwezig** om te controleren of de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-137">Set this property to **Present** to ensure the contents exist.</span></span> <span data-ttu-id="d2b9f-138">Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-138">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="d2b9f-139">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="d2b9f-139">The default value is **Present** .</span></span> |
|<span data-ttu-id="d2b9f-140">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d2b9f-140">PsDscRunAsCredential</span></span> |<span data-ttu-id="d2b9f-141">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-141">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d2b9f-142">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-142">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d2b9f-143">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-143">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2b9f-144">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d2b9f-144">Example</span></span>

<span data-ttu-id="d2b9f-145">In het volgende voor beeld ziet u hoe u de archief resource gebruikt om ervoor te zorgen dat de inhoud van een archief bestand `Test.zip` bestaat en dat wordt geëxtraheerd op een bepaald doel met en gemachtigd.</span><span class="sxs-lookup"><span data-stu-id="d2b9f-145">The following example shows how to use the Archive resource to ensure that the contents of an archive file called `Test.zip` exist and are extracted at a given destination using and authorized.</span></span>

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```
