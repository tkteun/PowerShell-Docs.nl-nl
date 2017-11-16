---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxPackage Resource
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="88bd0-103">DSC voor Linux nxPackage Resource</span><span class="sxs-lookup"><span data-stu-id="88bd0-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="88bd0-104">De **nxPackage** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van pakketten op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="88bd0-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="88bd0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="88bd0-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## <a name="properties"></a><span data-ttu-id="88bd0-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="88bd0-106">Properties</span></span>

|  <span data-ttu-id="88bd0-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="88bd0-107">Property</span></span> |  <span data-ttu-id="88bd0-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="88bd0-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="88bd0-109">Naam</span><span class="sxs-lookup"><span data-stu-id="88bd0-109">Name</span></span>| <span data-ttu-id="88bd0-110">De naam van het pakket waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="88bd0-110">The name of the package for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="88bd0-111">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="88bd0-111">Ensure</span></span>| <span data-ttu-id="88bd0-112">Bepaalt of Controleer of het pakket bestaat.</span><span class="sxs-lookup"><span data-stu-id="88bd0-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="88bd0-113">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het pakket bestaat.</span><span class="sxs-lookup"><span data-stu-id="88bd0-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="88bd0-114">Stel deze in op 'Ontbreekt' om te controleren of dat het pakket bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="88bd0-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="88bd0-115">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="88bd0-115">The default value is "Present".</span></span>|  
| <span data-ttu-id="88bd0-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="88bd0-116">PackageManager</span></span>| <span data-ttu-id="88bd0-117">Ondersteunde waarden zijn 'yum', 'apt' en 'zypper'.</span><span class="sxs-lookup"><span data-stu-id="88bd0-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="88bd0-118">Hiermee geeft u de package manager te gebruiken bij het installeren van pakketten.</span><span class="sxs-lookup"><span data-stu-id="88bd0-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="88bd0-119">Als **FilePath** is opgegeven, wordt het opgegeven pad wordt gebruikt om het pakket te installeren.</span><span class="sxs-lookup"><span data-stu-id="88bd0-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="88bd0-120">Een Package Manager anders wordt gebruikt voor het installeren van het pakket van een vooraf geconfigureerde opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="88bd0-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="88bd0-121">Als geen van beide **PackageManager** noch **FilePath** zijn opgegeven, de standaard package manager voor het systeem wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="88bd0-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>| 
| <span data-ttu-id="88bd0-122">filePath</span><span class="sxs-lookup"><span data-stu-id="88bd0-122">FilePath</span></span>| <span data-ttu-id="88bd0-123">Het pad waar het pakket zich bevindt</span><span class="sxs-lookup"><span data-stu-id="88bd0-123">The file path where the package resides</span></span>| 
| <span data-ttu-id="88bd0-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="88bd0-124">PackageGroup</span></span>| <span data-ttu-id="88bd0-125">Als **$true**, wordt de **naam** wordt verwacht dat de naam van de groep van een pakket voor gebruik met een **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="88bd0-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="88bd0-126">**PacakgeGroup** is niet geldig bij het opgeven van een **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="88bd0-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>| 
| <span data-ttu-id="88bd0-127">Argumenten</span><span class="sxs-lookup"><span data-stu-id="88bd0-127">Arguments</span></span>| <span data-ttu-id="88bd0-128">Een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies zoals opgegeven.</span><span class="sxs-lookup"><span data-stu-id="88bd0-128">A string of arguments that will be passed to the package exactly as provided.</span></span>| 
| <span data-ttu-id="88bd0-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="88bd0-129">ReturnCode</span></span>| <span data-ttu-id="88bd0-130">De verwachte retourcode.</span><span class="sxs-lookup"><span data-stu-id="88bd0-130">The expected return code.</span></span> <span data-ttu-id="88bd0-131">Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde opgegeven, dat wordt de configuratie een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="88bd0-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>| 
| <span data-ttu-id="88bd0-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="88bd0-132">DependsOn</span></span> | <span data-ttu-id="88bd0-133">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="88bd0-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="88bd0-134">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="88bd0-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="88bd0-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="88bd0-135">Example</span></span>

<span data-ttu-id="88bd0-136">Het volgende voorbeeld zorgt ervoor dat het pakket met de naam 'httpd' op een Linux-computer, met behulp van de 'Yum' package manager is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="88bd0-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```

