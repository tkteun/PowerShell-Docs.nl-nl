---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxEnvironment-resource
ms.openlocfilehash: 2f673dfbc3b6e93d7e186e4a63b75d16a31b5181
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463683"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="311e5-103">DSC voor Linux nxEnvironment-resource</span><span class="sxs-lookup"><span data-stu-id="311e5-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="311e5-104">De **nxEnvironment** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="311e5-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="311e5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="311e5-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="311e5-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="311e5-106">Properties</span></span>

|<span data-ttu-id="311e5-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="311e5-107">Property</span></span> |<span data-ttu-id="311e5-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="311e5-108">Description</span></span> |
|---|---|
|<span data-ttu-id="311e5-109">Naam</span><span class="sxs-lookup"><span data-stu-id="311e5-109">Name</span></span> |<span data-ttu-id="311e5-110">Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="311e5-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="311e5-111">Waarde</span><span class="sxs-lookup"><span data-stu-id="311e5-111">Value</span></span> |<span data-ttu-id="311e5-112">De waarde die moet worden toegewezen aan de omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="311e5-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="311e5-113">Pad</span><span class="sxs-lookup"><span data-stu-id="311e5-113">Path</span></span> |<span data-ttu-id="311e5-114">Hiermee definieert u de omgevings variabele die wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="311e5-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="311e5-115">Stel deze eigenschap in op `$true` als de variabele een **padvariabele** is. anders stelt u deze in op `$false` .</span><span class="sxs-lookup"><span data-stu-id="311e5-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="311e5-116">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="311e5-116">The default is `$false`.</span></span> <span data-ttu-id="311e5-117">Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="311e5-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="311e5-118">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="311e5-118">Common properties</span></span>

|<span data-ttu-id="311e5-119">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="311e5-119">Property</span></span> |<span data-ttu-id="311e5-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="311e5-120">Description</span></span> |
|---|---|
|<span data-ttu-id="311e5-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="311e5-121">DependsOn</span></span> |<span data-ttu-id="311e5-122">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="311e5-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="311e5-123">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="311e5-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="311e5-124">Zo</span><span class="sxs-lookup"><span data-stu-id="311e5-124">Ensure</span></span> |<span data-ttu-id="311e5-125">Hiermee wordt bepaald of er wordt gecontroleerd of de variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="311e5-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="311e5-126">Stel deze eigenschap in op **presen teren** om ervoor te zorgen dat de variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="311e5-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="311e5-127">Stel deze in op **afwezig** om te controleren of de variabele niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="311e5-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="311e5-128">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="311e5-128">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="311e5-129">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="311e5-129">Additional Information</span></span>

- <span data-ttu-id="311e5-130">Als het **pad** ontbreekt of is ingesteld op `$false` , worden omgevings variabelen beheerd in `/etc/environment` .</span><span class="sxs-lookup"><span data-stu-id="311e5-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="311e5-131">Uw Program ma's of scripts kunnen de configuratie van het `/etc/environment` bestand vereisen om toegang te krijgen tot de variabelen van de beheerde omgeving.</span><span class="sxs-lookup"><span data-stu-id="311e5-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="311e5-132">Als **Path** is ingesteld op `$true` , wordt de omgevings variabele in het bestand beheerd `/etc/profile.d/DSCenvironment.sh` .</span><span class="sxs-lookup"><span data-stu-id="311e5-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="311e5-133">Dit bestand wordt gemaakt als het niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="311e5-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="311e5-134">Als het is ingesteld op **afwezig** en **pad** **is ingesteld** op `$true` , wordt een bestaande omgevings variabele alleen uit `/etc/profile.d/DSCenvironment.sh` andere bestanden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="311e5-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="311e5-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="311e5-135">Example</span></span>

<span data-ttu-id="311e5-136">In het volgende voor beeld ziet u hoe u de **nxEnvironment** -resource gebruikt om ervoor te zorgen dat **TestEnvironmentVariable** aanwezig is en de waarde test-value heeft.</span><span class="sxs-lookup"><span data-stu-id="311e5-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="311e5-137">Als **TestEnvironmentVariable** niet aanwezig is, wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="311e5-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
