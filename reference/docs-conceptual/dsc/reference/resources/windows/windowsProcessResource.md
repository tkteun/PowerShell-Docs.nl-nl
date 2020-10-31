---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsProcess-resource
description: DSC WindowsProcess-resource
ms.openlocfilehash: 3076e9cb857b78953c164253351b23e7da9b40c6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143004"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="4e401-103">DSC WindowsProcess-resource</span><span class="sxs-lookup"><span data-stu-id="4e401-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="4e401-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="4e401-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4e401-105">De **WindowsProcess** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="4e401-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="4e401-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e401-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="4e401-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="4e401-107">Properties</span></span>

|<span data-ttu-id="4e401-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="4e401-108">Property</span></span> |<span data-ttu-id="4e401-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4e401-109">Description</span></span> |
|---|---|
|<span data-ttu-id="4e401-110">Argumenten</span><span class="sxs-lookup"><span data-stu-id="4e401-110">Arguments</span></span> |<span data-ttu-id="4e401-111">Hiermee wordt een reeks argumenten aangegeven die moeten worden door gegeven aan het proces.</span><span class="sxs-lookup"><span data-stu-id="4e401-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="4e401-112">Als u meerdere argumenten wilt door geven, plaatst u deze allemaal in deze teken reeks.</span><span class="sxs-lookup"><span data-stu-id="4e401-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="4e401-113">Pad</span><span class="sxs-lookup"><span data-stu-id="4e401-113">Path</span></span> |<span data-ttu-id="4e401-114">Het pad naar het uitvoer bare proces bestand.</span><span class="sxs-lookup"><span data-stu-id="4e401-114">The path to the process executable.</span></span> <span data-ttu-id="4e401-115">Als de bestands naam van het uitvoer bare bestand (niet het volledig gekwalificeerde pad) is, zoekt de DSC-resource de omgevings `$env:Path` variabele om het uitvoer bare bestand te vinden.</span><span class="sxs-lookup"><span data-stu-id="4e401-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="4e401-116">Als de waarde van deze eigenschap een volledig gekwalificeerd pad is, gebruikt DSC de variabele niet `$env:Path` om het bestand te vinden en wordt er een fout gegenereerd als het pad niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="4e401-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="4e401-117">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="4e401-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="4e401-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="4e401-118">Credential</span></span> |<span data-ttu-id="4e401-119">Geeft de referenties voor het starten van het proces aan.</span><span class="sxs-lookup"><span data-stu-id="4e401-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="4e401-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="4e401-120">StandardErrorPath</span></span> |<span data-ttu-id="4e401-121">Hiermee wordt het mappad aangegeven voor het schrijven van de standaard fout.</span><span class="sxs-lookup"><span data-stu-id="4e401-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="4e401-122">Eventuele bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="4e401-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="4e401-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="4e401-123">StandardInputPath</span></span> |<span data-ttu-id="4e401-124">Hiermee wordt de standaard invoer locatie aangegeven.</span><span class="sxs-lookup"><span data-stu-id="4e401-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="4e401-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="4e401-125">StandardOutputPath</span></span> |<span data-ttu-id="4e401-126">Hiermee wordt de locatie aangegeven waarop de standaard uitvoer moet worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="4e401-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="4e401-127">Eventuele bestaande bestanden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="4e401-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="4e401-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="4e401-128">WorkingDirectory</span></span> |<span data-ttu-id="4e401-129">Hiermee wordt de locatie aangegeven die wordt gebruikt als de huidige werkmap voor het proces.</span><span class="sxs-lookup"><span data-stu-id="4e401-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4e401-130">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="4e401-130">Common properties</span></span>

|<span data-ttu-id="4e401-131">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="4e401-131">Property</span></span> |<span data-ttu-id="4e401-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4e401-132">Description</span></span> |
|---|---|
|<span data-ttu-id="4e401-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4e401-133">DependsOn</span></span> |<span data-ttu-id="4e401-134">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="4e401-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4e401-135">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="4e401-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4e401-136">Zo</span><span class="sxs-lookup"><span data-stu-id="4e401-136">Ensure</span></span> |<span data-ttu-id="4e401-137">Hiermee wordt aangegeven of het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="4e401-137">Indicates if the process exists.</span></span> <span data-ttu-id="4e401-138">Stel deze eigenschap in op **aanwezig** om te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="4e401-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="4e401-139">Als dat niet het geval is, stelt u deze in op **afwezig** .</span><span class="sxs-lookup"><span data-stu-id="4e401-139">Otherwise, set it to **Absent** .</span></span> <span data-ttu-id="4e401-140">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="4e401-140">The default value is **Present** .</span></span> |
|<span data-ttu-id="4e401-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4e401-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="4e401-142">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="4e401-142">Sets the credential for running the entire resource as.</span></span> |
