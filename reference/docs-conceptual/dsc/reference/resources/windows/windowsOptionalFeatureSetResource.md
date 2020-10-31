---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsOptionalFeatureSet-resource
description: DSC WindowsOptionalFeatureSet-resource
ms.openlocfilehash: f72cc27bfc8847d2c87cfb289f3e2c729a21d1f4
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143038"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="bca99-103">DSC WindowsOptionalFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="bca99-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="bca99-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="bca99-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="bca99-105">De **WindowsOptionalFeatureSet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="bca99-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="bca99-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [WindowsOptionalFeature-resource](windowsOptionalFeatureResource.md) aanroept voor elk onderdeel dat is opgegeven in de eigenschap **name** .</span><span class="sxs-lookup"><span data-stu-id="bca99-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="bca99-107">Gebruik deze resource als u een aantal optionele Windows-functies wilt configureren in dezelfde status.</span><span class="sxs-lookup"><span data-stu-id="bca99-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="bca99-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="bca99-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="bca99-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="bca99-109">Properties</span></span>

|<span data-ttu-id="bca99-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bca99-110">Property</span></span> |<span data-ttu-id="bca99-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bca99-111">Description</span></span> |
|---|---|
|<span data-ttu-id="bca99-112">Naam</span><span class="sxs-lookup"><span data-stu-id="bca99-112">Name</span></span> |<span data-ttu-id="bca99-113">Hiermee geeft u de naam op van de functies die u wilt inschakelen, worden in-of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bca99-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="bca99-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="bca99-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="bca99-115">Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om functies in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="bca99-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="bca99-116">Als `$true` kan DISM geen contact opnemen met Wu.</span><span class="sxs-lookup"><span data-stu-id="bca99-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="bca99-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="bca99-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="bca99-118">Stel deze waarde in `$true` om alle bestanden te verwijderen die zijn **Ensure** gekoppeld aan de functies wanneer het is ingesteld op **afwezig** .</span><span class="sxs-lookup"><span data-stu-id="bca99-118">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent** .</span></span> |
|<span data-ttu-id="bca99-119">Logniveau</span><span class="sxs-lookup"><span data-stu-id="bca99-119">LogLevel</span></span> |<span data-ttu-id="bca99-120">Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken.</span><span class="sxs-lookup"><span data-stu-id="bca99-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="bca99-121">De geaccepteerde waarden zijn: **ErrorsOnly** , **ErrorsAndWarning** en **ErrorsAndWarningAndInformation** .</span><span class="sxs-lookup"><span data-stu-id="bca99-121">The accepted values are: **ErrorsOnly** , **ErrorsAndWarning** , and **ErrorsAndWarningAndInformation** .</span></span> |
|<span data-ttu-id="bca99-122">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="bca99-122">LogPath</span></span> |<span data-ttu-id="bca99-123">Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="bca99-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="bca99-124">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="bca99-124">Common properties</span></span>

|<span data-ttu-id="bca99-125">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bca99-125">Property</span></span> |<span data-ttu-id="bca99-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bca99-126">Description</span></span> |
|---|---|
|<span data-ttu-id="bca99-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bca99-127">DependsOn</span></span> |<span data-ttu-id="bca99-128">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="bca99-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bca99-129">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="bca99-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="bca99-130">Zo</span><span class="sxs-lookup"><span data-stu-id="bca99-130">Ensure</span></span> |<span data-ttu-id="bca99-131">Hiermee wordt aangegeven of de functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bca99-131">Specifies whether the features are enabled.</span></span> <span data-ttu-id="bca99-132">Stel deze eigenschap in op **inschakelen** om ervoor te zorgen dat de functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bca99-132">To ensure that the features are enabled, set this property to **Enable** .</span></span> <span data-ttu-id="bca99-133">Stel de eigenschap in op **uitschakelen** om ervoor te zorgen dat de functies zijn uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bca99-133">To ensure that the features are disabled, set the property to **Disable** .</span></span> <span data-ttu-id="bca99-134">De standaard waarde is **ingeschakeld** .</span><span class="sxs-lookup"><span data-stu-id="bca99-134">The default value is **Enable** .</span></span> |
|<span data-ttu-id="bca99-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bca99-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="bca99-136">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="bca99-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="bca99-137">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="bca99-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="bca99-138">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bca99-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
