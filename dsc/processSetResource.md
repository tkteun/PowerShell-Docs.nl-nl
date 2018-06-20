---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-ProcessSet Resource
ms.openlocfilehash: 412cf1076996126f0d9b7a9a8ebbc9bdb7ecf377
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189921"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="5eb59-103">DSC-WindowsProcess Resource</span><span class="sxs-lookup"><span data-stu-id="5eb59-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="5eb59-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5eb59-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5eb59-105">De **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van de processen in een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="5eb59-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="5eb59-106">Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [WindowsProcess resource](windowsProcessResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.</span><span class="sxs-lookup"><span data-stu-id="5eb59-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="5eb59-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5eb59-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="5eb59-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5eb59-108">Properties</span></span>
|  <span data-ttu-id="5eb59-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5eb59-109">Property</span></span>  |  <span data-ttu-id="5eb59-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5eb59-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="5eb59-111">Argumenten</span><span class="sxs-lookup"><span data-stu-id="5eb59-111">Arguments</span></span>| <span data-ttu-id="5eb59-112">Een tekenreeks met argumenten worden doorgegeven aan het proces als-is.</span><span class="sxs-lookup"><span data-stu-id="5eb59-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="5eb59-113">Als u moet enkele argumenten doorgegeven, plaatst u deze allemaal in deze tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="5eb59-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="5eb59-114">Pad</span><span class="sxs-lookup"><span data-stu-id="5eb59-114">Path</span></span>| <span data-ttu-id="5eb59-115">De paden naar het proces uitvoerbare bestanden.</span><span class="sxs-lookup"><span data-stu-id="5eb59-115">The paths to the process executables.</span></span> <span data-ttu-id="5eb59-116">Als dit zijn de namen van de uitvoerbare bestanden (niet de volledig gekwalificeerde paden), zoekt de DSC-resource de omgeving **pad** variabele (`$env:Path`) om de bestanden te zoeken.</span><span class="sxs-lookup"><span data-stu-id="5eb59-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="5eb59-117">Als de waarden van deze eigenschap volledig gekwalificeerde paden zijn, DSC niet wordt gebruikt de **pad** omgevingsvariabele om de bestanden te zoeken en genereert een fout als de paden niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="5eb59-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="5eb59-118">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="5eb59-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="5eb59-119">referentie</span><span class="sxs-lookup"><span data-stu-id="5eb59-119">Credential</span></span>| <span data-ttu-id="5eb59-120">Hiermee geeft u de referenties voor het starten van het proces.</span><span class="sxs-lookup"><span data-stu-id="5eb59-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="5eb59-121">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="5eb59-121">Ensure</span></span>| <span data-ttu-id="5eb59-122">Geeft aan of de processen bestaat.</span><span class="sxs-lookup"><span data-stu-id="5eb59-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="5eb59-123">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="5eb59-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="5eb59-124">Anders wordt deze ingesteld op 'Afwezig'.</span><span class="sxs-lookup"><span data-stu-id="5eb59-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="5eb59-125">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="5eb59-125">The default is "Present".</span></span>|
| <span data-ttu-id="5eb59-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="5eb59-126">StandardErrorPath</span></span>| <span data-ttu-id="5eb59-127">Het pad waaraan de processen standaardfout schrijven.</span><span class="sxs-lookup"><span data-stu-id="5eb59-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="5eb59-128">Er een bestaand bestand worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="5eb59-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="5eb59-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="5eb59-129">StandardInputPath</span></span>| <span data-ttu-id="5eb59-130">De stroom van waaruit het proces standaardinvoer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="5eb59-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="5eb59-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="5eb59-131">StandardOutputPath</span></span>| <span data-ttu-id="5eb59-132">Het pad van het bestand waarvoor de processen standaarduitvoer schrijven.</span><span class="sxs-lookup"><span data-stu-id="5eb59-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="5eb59-133">Er een bestaand bestand worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="5eb59-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="5eb59-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="5eb59-134">WorkingDirectory</span></span>| <span data-ttu-id="5eb59-135">De locatie die wordt gebruikt als de huidige werkmap voor de processen.</span><span class="sxs-lookup"><span data-stu-id="5eb59-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="5eb59-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5eb59-136">DependsOn</span></span> | <span data-ttu-id="5eb59-137">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="5eb59-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5eb59-138">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **_ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.</span><span class="sxs-lookup"><span data-stu-id="5eb59-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|