---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxPackage-resource
description: DSC voor Linux nxPackage-resource
ms.openlocfilehash: b84c7963297e8a88e729cd67611245b017c27fb7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648844"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="ad482-103">DSC voor Linux nxPackage-resource</span><span class="sxs-lookup"><span data-stu-id="ad482-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="ad482-104">De **nxPackage** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van pakketten op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="ad482-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad482-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad482-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="ad482-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ad482-106">Properties</span></span>

|<span data-ttu-id="ad482-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="ad482-107">Property</span></span> |<span data-ttu-id="ad482-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ad482-108">Description</span></span> |
|---|---|
|<span data-ttu-id="ad482-109">Naam</span><span class="sxs-lookup"><span data-stu-id="ad482-109">Name</span></span> |<span data-ttu-id="ad482-110">De naam van het pakket waarvoor u een specifieke status wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="ad482-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="ad482-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="ad482-111">PackageManager</span></span> |<span data-ttu-id="ad482-112">Ondersteunde waarden zijn **yum** , **apt** en **Zypper** .</span><span class="sxs-lookup"><span data-stu-id="ad482-112">Supported values are **yum** , **apt** , and **zypper** .</span></span> <span data-ttu-id="ad482-113">Hiermee geeft u op welke pakket beheer moet worden gebruikt bij het installeren van pakketten.</span><span class="sxs-lookup"><span data-stu-id="ad482-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="ad482-114">Als **filepath** is opgegeven, wordt het opgegeven pad gebruikt om het pakket te installeren.</span><span class="sxs-lookup"><span data-stu-id="ad482-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="ad482-115">Anders wordt een pakket beheer gebruikt om het pakket te installeren vanuit een vooraf geconfigureerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="ad482-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="ad482-116">Als geen van beide **PackageManager** of **filepath** wordt gegeven, wordt de standaard pakket beheerder voor het systeem gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ad482-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="ad482-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="ad482-117">PackageGroup</span></span> |<span data-ttu-id="ad482-118">Als `$true` de **naam** naar verwachting de naam van een pakket groep is voor gebruik met een **PackageManager** .</span><span class="sxs-lookup"><span data-stu-id="ad482-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager** .</span></span> <span data-ttu-id="ad482-119">**PackageGroup** is niet geldig voor het opgeven van een **bestandspad** .</span><span class="sxs-lookup"><span data-stu-id="ad482-119">**PackageGroup** is not valid when providing a **FilePath** .</span></span> |
|<span data-ttu-id="ad482-120">Argumenten</span><span class="sxs-lookup"><span data-stu-id="ad482-120">Arguments</span></span> |<span data-ttu-id="ad482-121">Een teken reeks argumenten die exact als opgegeven worden door gegeven aan het pakket.</span><span class="sxs-lookup"><span data-stu-id="ad482-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="ad482-122">Return code</span><span class="sxs-lookup"><span data-stu-id="ad482-122">ReturnCode</span></span> |<span data-ttu-id="ad482-123">De verwachte retour code.</span><span class="sxs-lookup"><span data-stu-id="ad482-123">The expected return code.</span></span> <span data-ttu-id="ad482-124">Als de daad werkelijke retour code niet overeenkomt met de verwachte waarde die hier wordt opgegeven, wordt er een fout geretourneerd door de configuratie.</span><span class="sxs-lookup"><span data-stu-id="ad482-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="ad482-125">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="ad482-125">FilePath</span></span> |<span data-ttu-id="ad482-126">Het bestandspad waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="ad482-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ad482-127">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ad482-127">Common properties</span></span>

|<span data-ttu-id="ad482-128">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="ad482-128">Property</span></span> |<span data-ttu-id="ad482-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ad482-129">Description</span></span> |
|---|---|
|<span data-ttu-id="ad482-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ad482-130">DependsOn</span></span> |<span data-ttu-id="ad482-131">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="ad482-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ad482-132">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="ad482-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ad482-133">Zo</span><span class="sxs-lookup"><span data-stu-id="ad482-133">Ensure</span></span> |<span data-ttu-id="ad482-134">Hiermee wordt bepaald of er wordt gecontroleerd of het pakket bestaat.</span><span class="sxs-lookup"><span data-stu-id="ad482-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="ad482-135">Stel deze eigenschap in op **aanwezig** om te controleren of het pakket bestaat.</span><span class="sxs-lookup"><span data-stu-id="ad482-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="ad482-136">Stel deze in op **afwezig** om ervoor te zorgen dat het pakket niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="ad482-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="ad482-137">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="ad482-137">The default value is **Present** .</span></span> |

## <a name="example"></a><span data-ttu-id="ad482-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ad482-138">Example</span></span>

<span data-ttu-id="ad482-139">In het volgende voor beeld wordt ervoor gezorgd dat het pakket met de naam ' httpd ' is geïnstalleerd op een Linux-computer met behulp van het pakket beheer ' yum '.</span><span class="sxs-lookup"><span data-stu-id="ad482-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```
