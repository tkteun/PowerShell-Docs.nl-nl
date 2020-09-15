---
ms.date: 07/16/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsProcess-resource
ms.openlocfilehash: a1f8840a5894049efd27c5d213a66363cd8dbebc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464125"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="fa7c7-103">DSC WindowsProcess-resource</span><span class="sxs-lookup"><span data-stu-id="fa7c7-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="fa7c7-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="fa7c7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="fa7c7-105">De **WindowsProcess** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa7c7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fa7c7-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="fa7c7-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fa7c7-107">Properties</span></span>

|<span data-ttu-id="fa7c7-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fa7c7-108">Property</span></span> |<span data-ttu-id="fa7c7-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fa7c7-109">Description</span></span> |
|---|---|
|<span data-ttu-id="fa7c7-110">Argumenten</span><span class="sxs-lookup"><span data-stu-id="fa7c7-110">Arguments</span></span> |<span data-ttu-id="fa7c7-111">Hiermee wordt een reeks argumenten aangegeven die moeten worden door gegeven aan het proces.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="fa7c7-112">Als u meerdere argumenten wilt door geven, plaatst u deze allemaal in deze teken reeks.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="fa7c7-113">Pad</span><span class="sxs-lookup"><span data-stu-id="fa7c7-113">Path</span></span> |<span data-ttu-id="fa7c7-114">Het pad naar het uitvoer bare proces bestand.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-114">The path to the process executable.</span></span> <span data-ttu-id="fa7c7-115">Als de bestands naam van het uitvoer bare bestand (niet het volledig gekwalificeerde pad) is, zoekt de DSC-resource de omgevings `$env:Path` variabele om het uitvoer bare bestand te vinden.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="fa7c7-116">Als de waarde van deze eigenschap een volledig gekwalificeerd pad is, gebruikt DSC de variabele niet `$env:Path` om het bestand te vinden en wordt er een fout gegenereerd als het pad niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="fa7c7-117">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="fa7c7-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="fa7c7-118">Credential</span></span> |<span data-ttu-id="fa7c7-119">Geeft de referenties voor het starten van het proces aan.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="fa7c7-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="fa7c7-120">StandardErrorPath</span></span> |<span data-ttu-id="fa7c7-121">Hiermee wordt het mappad aangegeven voor het schrijven van de standaard fout.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="fa7c7-122">Eventuele bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="fa7c7-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="fa7c7-123">StandardInputPath</span></span> |<span data-ttu-id="fa7c7-124">Hiermee wordt de standaard invoer locatie aangegeven.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="fa7c7-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="fa7c7-125">StandardOutputPath</span></span> |<span data-ttu-id="fa7c7-126">Hiermee wordt de locatie aangegeven waarop de standaard uitvoer moet worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="fa7c7-127">Eventuele bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="fa7c7-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="fa7c7-128">WorkingDirectory</span></span> |<span data-ttu-id="fa7c7-129">Hiermee wordt de locatie aangegeven die wordt gebruikt als de huidige werkmap voor het proces.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fa7c7-130">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fa7c7-130">Common properties</span></span>

|<span data-ttu-id="fa7c7-131">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fa7c7-131">Property</span></span> |<span data-ttu-id="fa7c7-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fa7c7-132">Description</span></span> |
|---|---|
|<span data-ttu-id="fa7c7-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fa7c7-133">DependsOn</span></span> |<span data-ttu-id="fa7c7-134">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fa7c7-135">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="fa7c7-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fa7c7-136">Zo</span><span class="sxs-lookup"><span data-stu-id="fa7c7-136">Ensure</span></span> |<span data-ttu-id="fa7c7-137">Hiermee wordt aangegeven of het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-137">Indicates if the process exists.</span></span> <span data-ttu-id="fa7c7-138">Stel deze eigenschap in op **aanwezig** om te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="fa7c7-139">Als dat niet het geval is, stelt u deze in op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="fa7c7-140">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="fa7c7-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fa7c7-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="fa7c7-142">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="fa7c7-142">Sets the credential for running the entire resource as.</span></span> |
