---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsOptionalFeature-resource
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942431"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="55a73-103">DSC WindowsOptionalFeature-resource</span><span class="sxs-lookup"><span data-stu-id="55a73-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="55a73-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="55a73-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="55a73-105">De **WindowsOptionalFeature** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="55a73-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="55a73-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="55a73-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="55a73-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="55a73-107">Properties</span></span>

|<span data-ttu-id="55a73-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="55a73-108">Property</span></span> |<span data-ttu-id="55a73-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="55a73-109">Description</span></span> |
|---|---|
|<span data-ttu-id="55a73-110">Naam</span><span class="sxs-lookup"><span data-stu-id="55a73-110">Name</span></span> |<span data-ttu-id="55a73-111">Hiermee wordt de naam aangegeven van de functie die u wilt inschakelen, is ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="55a73-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="55a73-112">Bron</span><span class="sxs-lookup"><span data-stu-id="55a73-112">Source</span></span> |<span data-ttu-id="55a73-113">Niet geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="55a73-113">Not implemented.</span></span> |
|<span data-ttu-id="55a73-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="55a73-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="55a73-115">Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om een functie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="55a73-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="55a73-116">Als `$true`kan DISM geen contact opnemen met Wu.</span><span class="sxs-lookup"><span data-stu-id="55a73-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="55a73-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="55a73-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="55a73-118">Stel deze `$true` optie in om alle bestanden te verwijderen die zijn gekoppeld aan de functie als u **zeker weet dat** deze is ingesteld op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="55a73-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="55a73-119">Logniveau</span><span class="sxs-lookup"><span data-stu-id="55a73-119">LogLevel</span></span> |<span data-ttu-id="55a73-120">Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken.</span><span class="sxs-lookup"><span data-stu-id="55a73-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="55a73-121">De geaccepteerde waarden zijn: **ErrorsOnly**, **ErrorsAndWarning**en **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="55a73-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="55a73-122">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="55a73-122">LogPath</span></span> |<span data-ttu-id="55a73-123">Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="55a73-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="55a73-124">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="55a73-124">Common properties</span></span>

|<span data-ttu-id="55a73-125">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="55a73-125">Property</span></span> |<span data-ttu-id="55a73-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="55a73-126">Description</span></span> |
|---|---|
|<span data-ttu-id="55a73-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="55a73-127">DependsOn</span></span> |<span data-ttu-id="55a73-128">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="55a73-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="55a73-129">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="55a73-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="55a73-130">Zo</span><span class="sxs-lookup"><span data-stu-id="55a73-130">Ensure</span></span> |<span data-ttu-id="55a73-131">Hiermee wordt aangegeven of de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="55a73-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="55a73-132">Stel deze eigenschap in op _inschakelen_om ervoor te zorgen dat de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="55a73-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="55a73-133">Om ervoor te zorgen dat de functie is uitgeschakeld, stelt u de eigenschap in op _uitschakelen_.</span><span class="sxs-lookup"><span data-stu-id="55a73-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="55a73-134">De standaard waarde is _ingeschakeld_.</span><span class="sxs-lookup"><span data-stu-id="55a73-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="55a73-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="55a73-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="55a73-136">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="55a73-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="55a73-137">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="55a73-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="55a73-138">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="55a73-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>