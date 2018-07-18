---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsProcess-Resource
ms.openlocfilehash: 3c4e6d8377c3dcbf4f1db87a603d5483b8caafb8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093732"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="272f5-103">DSC WindowsProcess-Resource</span><span class="sxs-lookup"><span data-stu-id="272f5-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="272f5-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="272f5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="272f5-105">De **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="272f5-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="272f5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="272f5-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="272f5-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="272f5-107">Properties</span></span>

|  <span data-ttu-id="272f5-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="272f5-108">Property</span></span>  |  <span data-ttu-id="272f5-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="272f5-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="272f5-110">Argumenten</span><span class="sxs-lookup"><span data-stu-id="272f5-110">Arguments</span></span>| <span data-ttu-id="272f5-111">Geeft een reeks van argumenten worden doorgegeven aan de proces-is.</span><span class="sxs-lookup"><span data-stu-id="272f5-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="272f5-112">Als u meerdere argumenten doorgeven wilt, plaatst u ze allemaal op deze tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="272f5-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="272f5-113">Pad</span><span class="sxs-lookup"><span data-stu-id="272f5-113">Path</span></span>| <span data-ttu-id="272f5-114">Het pad naar het uitvoerbare bestand.</span><span class="sxs-lookup"><span data-stu-id="272f5-114">The path to the process executable.</span></span> <span data-ttu-id="272f5-115">Als dit de naam van het uitvoerbare bestand (niet de volledig gekwalificeerde pad), de DSC-resource wordt zoeken in de omgeving **pad** variabele (`$env:Path`) naar het uitvoerbare bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="272f5-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="272f5-116">Als de waarde van deze eigenschap een volledig gekwalificeerde pad is, DSC niet gebruiken de **pad** omgevingsvariabele het bestand te vinden en genereert een fout als het pad niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="272f5-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="272f5-117">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="272f5-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="272f5-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="272f5-118">Credential</span></span>| <span data-ttu-id="272f5-119">Geeft aan dat de referenties voor het starten van het proces.</span><span class="sxs-lookup"><span data-stu-id="272f5-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="272f5-120">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="272f5-120">Ensure</span></span>| <span data-ttu-id="272f5-121">Geeft aan of het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="272f5-121">Indicates if the process exists.</span></span> <span data-ttu-id="272f5-122">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="272f5-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="272f5-123">Anders wordt deze ingesteld op 'Ontbreekt'.</span><span class="sxs-lookup"><span data-stu-id="272f5-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="272f5-124">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="272f5-124">The default is "Present".</span></span>|
| <span data-ttu-id="272f5-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="272f5-125">DependsOn</span></span> | <span data-ttu-id="272f5-126">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="272f5-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="272f5-127">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="272f5-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="272f5-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="272f5-128">StandardErrorPath</span></span>| <span data-ttu-id="272f5-129">Geeft het pad voor het schrijven van de standard-fout.</span><span class="sxs-lookup"><span data-stu-id="272f5-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="272f5-130">Er een bestaand bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="272f5-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="272f5-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="272f5-131">StandardInputPath</span></span>| <span data-ttu-id="272f5-132">Geeft de locatie van de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="272f5-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="272f5-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="272f5-133">StandardOutputPath</span></span>| <span data-ttu-id="272f5-134">Geeft de locatie voor het schrijven van de standaarduitvoer.</span><span class="sxs-lookup"><span data-stu-id="272f5-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="272f5-135">Er een bestaand bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="272f5-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="272f5-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="272f5-136">WorkingDirectory</span></span>| <span data-ttu-id="272f5-137">Geeft de locatie die wordt gebruikt als de huidige werkmap voor het proces.</span><span class="sxs-lookup"><span data-stu-id="272f5-137">Indicates the location that will be used as the current working directory for the process.</span></span>|