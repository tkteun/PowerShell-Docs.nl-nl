---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-Processet-resource
description: DSC-Processet-resource
ms.openlocfilehash: 46e2cf8409448c2d4b7adb4da4fb51a5779c7c8f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664240"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="08238-103">DSC-Processet-resource</span><span class="sxs-lookup"><span data-stu-id="08238-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="08238-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="08238-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="08238-105">De **processet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="08238-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="08238-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="08238-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="08238-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="08238-107">Properties</span></span>

|<span data-ttu-id="08238-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="08238-108">Property</span></span> |<span data-ttu-id="08238-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="08238-109">Description</span></span> |
|---|---|
|<span data-ttu-id="08238-110">Pad</span><span class="sxs-lookup"><span data-stu-id="08238-110">Path</span></span> |<span data-ttu-id="08238-111">Het pad naar het uitvoer bare proces bestand.</span><span class="sxs-lookup"><span data-stu-id="08238-111">The path to the process executable.</span></span> <span data-ttu-id="08238-112">Als dit de namen zijn van de uitvoer bare bestanden (niet volledig gekwalificeerde paden), zal de DSC-resource de omgevings `$env:Path` variabele doorzoeken om de bestanden te vinden.</span><span class="sxs-lookup"><span data-stu-id="08238-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="08238-113">Als de waarden van deze eigenschap volledig gekwalificeerde paden zijn, wordt de `$env:Path` omgevings variabele niet gebruikt om de bestanden te vinden en wordt er een fout gegenereerd als een van de paden niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="08238-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="08238-114">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="08238-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="08238-115">Referentie</span><span class="sxs-lookup"><span data-stu-id="08238-115">Credential</span></span> |<span data-ttu-id="08238-116">Geeft de referenties voor het starten van het proces aan.</span><span class="sxs-lookup"><span data-stu-id="08238-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="08238-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="08238-117">StandardErrorPath</span></span> |<span data-ttu-id="08238-118">Het pad naar de standaard fout voor het schrijven van processen.</span><span class="sxs-lookup"><span data-stu-id="08238-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="08238-119">Eventuele bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="08238-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="08238-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="08238-120">StandardInputPath</span></span> |<span data-ttu-id="08238-121">De stroom van waaruit het proces standaard invoer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="08238-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="08238-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="08238-122">StandardOutputPath</span></span> |<span data-ttu-id="08238-123">Het pad van het bestand waarnaar de standaard uitvoer van de processen wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="08238-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="08238-124">Eventuele bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="08238-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="08238-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="08238-125">WorkingDirectory</span></span> |<span data-ttu-id="08238-126">De locatie die wordt gebruikt als de huidige werkmap voor de processen.</span><span class="sxs-lookup"><span data-stu-id="08238-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="08238-127">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="08238-127">Common properties</span></span>

|<span data-ttu-id="08238-128">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="08238-128">Property</span></span> |<span data-ttu-id="08238-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="08238-129">Description</span></span> |
|---|---|
|<span data-ttu-id="08238-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="08238-130">DependsOn</span></span> |<span data-ttu-id="08238-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="08238-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="08238-132">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="08238-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="08238-133">Zo</span><span class="sxs-lookup"><span data-stu-id="08238-133">Ensure</span></span> |<span data-ttu-id="08238-134">Hiermee geeft u op of de processen bestaan.</span><span class="sxs-lookup"><span data-stu-id="08238-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="08238-135">Stel deze eigenschap in op **aanwezig** om te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="08238-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="08238-136">Als dat niet het geval is, stelt u deze in op **afwezig** .</span><span class="sxs-lookup"><span data-stu-id="08238-136">Otherwise, set it to **Absent** .</span></span> <span data-ttu-id="08238-137">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="08238-137">The default value is **Present** .</span></span> |
|<span data-ttu-id="08238-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="08238-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="08238-139">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="08238-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="08238-140">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="08238-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="08238-141">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="08238-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
