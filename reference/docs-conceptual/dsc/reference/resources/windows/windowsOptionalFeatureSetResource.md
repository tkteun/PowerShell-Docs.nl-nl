---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsOptionalFeatureSet-resource
ms.openlocfilehash: 0930bd0c6d1955005ea607b610e004818c0ad06f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560148"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="2bbee-103">DSC WindowsOptionalFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="2bbee-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="2bbee-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="2bbee-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="2bbee-105">De **WindowsOptionalFeatureSet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="2bbee-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="2bbee-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [WindowsOptionalFeature-resource](windowsOptionalFeatureResource.md) aanroept voor elk onderdeel dat is opgegeven in de eigenschap **name** .</span><span class="sxs-lookup"><span data-stu-id="2bbee-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="2bbee-107">Gebruik deze resource als u een aantal optionele Windows-functies wilt configureren in dezelfde status.</span><span class="sxs-lookup"><span data-stu-id="2bbee-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="2bbee-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2bbee-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2bbee-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="2bbee-109">Properties</span></span>

|<span data-ttu-id="2bbee-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2bbee-110">Property</span></span> |<span data-ttu-id="2bbee-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2bbee-111">Description</span></span> |
|---|---|
|<span data-ttu-id="2bbee-112">Name</span><span class="sxs-lookup"><span data-stu-id="2bbee-112">Name</span></span> |<span data-ttu-id="2bbee-113">Hiermee geeft u de naam op van de functies die u wilt inschakelen, worden in-of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2bbee-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="2bbee-114">Bron</span><span class="sxs-lookup"><span data-stu-id="2bbee-114">Source</span></span> |<span data-ttu-id="2bbee-115">Niet geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="2bbee-115">Not implemented.</span></span> |
|<span data-ttu-id="2bbee-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="2bbee-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="2bbee-117">Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om functies in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="2bbee-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="2bbee-118">Als `$true` kan DISM geen contact opnemen met Wu.</span><span class="sxs-lookup"><span data-stu-id="2bbee-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="2bbee-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="2bbee-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="2bbee-120">Stel deze waarde in `$true` om alle bestanden te verwijderen die zijn **Ensure** gekoppeld aan de functies wanneer het is ingesteld op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="2bbee-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="2bbee-121">Logniveau</span><span class="sxs-lookup"><span data-stu-id="2bbee-121">LogLevel</span></span> |<span data-ttu-id="2bbee-122">Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken.</span><span class="sxs-lookup"><span data-stu-id="2bbee-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="2bbee-123">De geaccepteerde waarden zijn: **ErrorsOnly**, **ErrorsAndWarning**en **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="2bbee-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="2bbee-124">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="2bbee-124">LogPath</span></span> |<span data-ttu-id="2bbee-125">Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="2bbee-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2bbee-126">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="2bbee-126">Common properties</span></span>

|<span data-ttu-id="2bbee-127">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2bbee-127">Property</span></span> |<span data-ttu-id="2bbee-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2bbee-128">Description</span></span> |
|---|---|
|<span data-ttu-id="2bbee-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2bbee-129">DependsOn</span></span> |<span data-ttu-id="2bbee-130">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="2bbee-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2bbee-131">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="2bbee-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2bbee-132">Zo</span><span class="sxs-lookup"><span data-stu-id="2bbee-132">Ensure</span></span> |<span data-ttu-id="2bbee-133">Hiermee wordt aangegeven of de functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2bbee-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="2bbee-134">Stel deze eigenschap in op **inschakelen**om ervoor te zorgen dat de functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2bbee-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="2bbee-135">Stel de eigenschap in op **uitschakelen**om ervoor te zorgen dat de functies zijn uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2bbee-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="2bbee-136">De standaard waarde is **ingeschakeld**.</span><span class="sxs-lookup"><span data-stu-id="2bbee-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="2bbee-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2bbee-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="2bbee-138">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="2bbee-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="2bbee-139">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="2bbee-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="2bbee-140">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2bbee-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
