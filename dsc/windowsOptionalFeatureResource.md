---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsOptionalFeature-Resource
ms.openlocfilehash: 1866bc9cd2194a62de23eaabee8a9c5049a84946
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="af804-103">DSC-WindowsOptionalFeature-Resource</span><span class="sxs-lookup"><span data-stu-id="af804-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="af804-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="af804-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="af804-105">De **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat de optionele functies zijn ingeschakeld op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="af804-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="af804-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="af804-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="af804-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="af804-107">Properties</span></span>

|  <span data-ttu-id="af804-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="af804-108">Property</span></span>  |  <span data-ttu-id="af804-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="af804-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="af804-110">Naam</span><span class="sxs-lookup"><span data-stu-id="af804-110">Name</span></span>| <span data-ttu-id="af804-111">Geeft de naam van de functie die u wilt zorgen is ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="af804-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="af804-112">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="af804-112">Ensure</span></span>| <span data-ttu-id="af804-113">Hiermee geeft u op of de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="af804-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="af804-114">Om ervoor te zorgen dat de functie is ingeschakeld, stel deze eigenschap in op 'Inschakelen' om ervoor te zorgen dat de functie is uitgeschakeld, de eigenschap instellen op 'Uitschakelen'.</span><span class="sxs-lookup"><span data-stu-id="af804-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="af804-115">Bron</span><span class="sxs-lookup"><span data-stu-id="af804-115">Source</span></span>| <span data-ttu-id="af804-116">Niet geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="af804-116">Not implemented.</span></span>|
| <span data-ttu-id="af804-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="af804-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="af804-118">Hiermee geeft u op of DISM neemt contact op met Windows Update (WU) bij het zoeken naar de bronbestanden van een functie in te schakelen.</span><span class="sxs-lookup"><span data-stu-id="af804-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="af804-119">Als $true, DISM niet contact opneemt met WU.</span><span class="sxs-lookup"><span data-stu-id="af804-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="af804-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="af804-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="af804-121">Ingesteld op **$true** verwijderen van alle bestanden die zijn gekoppeld aan de functie wanneer deze is uitgeschakeld (dat wil zeggen, wanneer **Zorg ervoor dat** is ingesteld op 'Afwezig').</span><span class="sxs-lookup"><span data-stu-id="af804-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="af804-122">Logniveau</span><span class="sxs-lookup"><span data-stu-id="af804-122">LogLevel</span></span>| <span data-ttu-id="af804-123">Het maximale uitvoerniveau op die wordt weergegeven in de logboeken.</span><span class="sxs-lookup"><span data-stu-id="af804-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="af804-124">De toegestane waarden zijn: 'ErrorsOnly' (alleen fouten worden geregistreerd), 'ErrorsAndWarning' (fouten en waarschuwingen worden geregistreerd), en 'ErrorsAndWarningAndInformation' (fouten, waarschuwingen en foutopsporingsinformatie worden geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="af804-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="af804-125">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="af804-125">LogPath</span></span>| <span data-ttu-id="af804-126">Het pad naar een logboekbestand waar u de resourceprovider aan te melden van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="af804-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="af804-127">dependsOn</span><span class="sxs-lookup"><span data-stu-id="af804-127">DependsOn</span></span>| <span data-ttu-id="af804-128">Specificeert dat de configuratie van een andere resource moet worden uitgevoerd voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="af804-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="af804-129">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="af804-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|