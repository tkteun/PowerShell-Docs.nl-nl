---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsProcess Resource
ms.openlocfilehash: ec77209637d574a0e530f4cce283e1ad98701cdb
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="581bd-103">DSC-WindowsProcess Resource</span><span class="sxs-lookup"><span data-stu-id="581bd-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="581bd-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="581bd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="581bd-105">De **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van de processen in een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="581bd-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="581bd-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="581bd-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="581bd-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="581bd-107">Properties</span></span>
|  <span data-ttu-id="581bd-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="581bd-108">Property</span></span>  |  <span data-ttu-id="581bd-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="581bd-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="581bd-110">Argumenten</span><span class="sxs-lookup"><span data-stu-id="581bd-110">Arguments</span></span>| <span data-ttu-id="581bd-111">Geeft een reeks van argumenten worden doorgegeven aan het proces als-is.</span><span class="sxs-lookup"><span data-stu-id="581bd-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="581bd-112">Als u moet enkele argumenten doorgegeven, plaatst u deze allemaal in deze tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="581bd-112">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="581bd-113">Pad</span><span class="sxs-lookup"><span data-stu-id="581bd-113">Path</span></span>| <span data-ttu-id="581bd-114">Het pad naar het uitvoerbare bestand van het proces.</span><span class="sxs-lookup"><span data-stu-id="581bd-114">The path to the process executable.</span></span> <span data-ttu-id="581bd-115">Als dit de bestandsnaam van het uitvoerbare bestand (niet de volledig gekwalificeerde pad), de DSC-resource zoekt de omgeving **pad** variabele (`$env:Path`) naar het uitvoerbare bestand niet vinden.</span><span class="sxs-lookup"><span data-stu-id="581bd-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="581bd-116">Als de waarde van deze eigenschap een volledig gekwalificeerde pad is, DSC niet wordt gebruikt de **pad** omgevingsvariabele het bestand te vinden en genereert een fout als het pad niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="581bd-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="581bd-117">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="581bd-117">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="581bd-118">referentie</span><span class="sxs-lookup"><span data-stu-id="581bd-118">Credential</span></span>| <span data-ttu-id="581bd-119">Hiermee geeft u de referenties voor het starten van het proces.</span><span class="sxs-lookup"><span data-stu-id="581bd-119">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="581bd-120">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="581bd-120">Ensure</span></span>| <span data-ttu-id="581bd-121">Hiermee wordt aangegeven of het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="581bd-121">Indicates if the process exists.</span></span> <span data-ttu-id="581bd-122">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="581bd-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="581bd-123">Anders wordt deze ingesteld op 'Afwezig'.</span><span class="sxs-lookup"><span data-stu-id="581bd-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="581bd-124">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="581bd-124">The default is "Present".</span></span>| 
| <span data-ttu-id="581bd-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="581bd-125">DependsOn</span></span> | <span data-ttu-id="581bd-126">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="581bd-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="581bd-127">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.</span><span class="sxs-lookup"><span data-stu-id="581bd-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>| 
| <span data-ttu-id="581bd-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="581bd-128">StandardErrorPath</span></span>| <span data-ttu-id="581bd-129">Geeft het pad de standaardfout worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="581bd-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="581bd-130">Er een bestaand bestand worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="581bd-130">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="581bd-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="581bd-131">StandardInputPath</span></span>| <span data-ttu-id="581bd-132">Hiermee wordt de locatie van de standaard invoer.</span><span class="sxs-lookup"><span data-stu-id="581bd-132">Indicates the standard input location.</span></span>| 
| <span data-ttu-id="581bd-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="581bd-133">StandardOutputPath</span></span>| <span data-ttu-id="581bd-134">Geeft de locatie voor het schrijven van de standaarduitvoer.</span><span class="sxs-lookup"><span data-stu-id="581bd-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="581bd-135">Er een bestaand bestand worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="581bd-135">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="581bd-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="581bd-136">WorkingDirectory</span></span>| <span data-ttu-id="581bd-137">Geeft de locatie die wordt gebruikt als de huidige werkmap voor het proces.</span><span class="sxs-lookup"><span data-stu-id="581bd-137">Indicates the location that will be used as the current working directory for the process.</span></span>| 

