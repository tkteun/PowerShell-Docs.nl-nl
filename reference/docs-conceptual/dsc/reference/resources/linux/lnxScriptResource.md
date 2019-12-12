---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxScript-resource
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941409"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="fd4c3-103">DSC voor Linux nxScript-resource</span><span class="sxs-lookup"><span data-stu-id="fd4c3-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="fd4c3-104">De **nxScript** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Linux-scripts op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd4c3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fd4c3-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="fd4c3-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fd4c3-106">Properties</span></span>

|<span data-ttu-id="fd4c3-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fd4c3-107">Property</span></span> |<span data-ttu-id="fd4c3-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd4c3-108">Description</span></span> |
|---|---|
|<span data-ttu-id="fd4c3-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="fd4c3-109">GetScript</span></span> |<span data-ttu-id="fd4c3-110">Biedt een script om de huidige status van de machine te retour neren.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="fd4c3-111">Dit script wordt uitgevoerd wanneer u het script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="fd4c3-112">Het script moet beginnen met een shebang, zoals `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="fd4c3-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="fd4c3-113">SetScript</span></span> |<span data-ttu-id="fd4c3-114">Bevat een script dat de computer in de juiste status plaatst.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="fd4c3-115">Wanneer u het script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept, wordt eerst de **TestScript** uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="fd4c3-116">Als het **TestScript** -blok een andere afsluit code dan 0 retourneert, wordt het blok **SetScript** uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="fd4c3-117">Als de **TestScript** de afsluit code 0 retourneert, wordt de **SetScript** niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="fd4c3-118">Het script moet beginnen met een shebang, zoals `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="fd4c3-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="fd4c3-119">TestScript</span></span> |<span data-ttu-id="fd4c3-120">Voorziet in een script dat evalueert of het knoop punt momenteel de juiste status heeft.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="fd4c3-121">Wanneer u het script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept, wordt dit script uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="fd4c3-122">Als het een andere afsluit code dan 0 retourneert, wordt de **SetScript** uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="fd4c3-123">Als de methode de afsluit code 0 retourneert, wordt de **SetScript** niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="fd4c3-124">De **TestScript** wordt ook uitgevoerd wanneer u het script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="fd4c3-125">In dit geval wordt de **SetScript** echter niet uitgevoerd, ongeacht de afsluit code die wordt geretourneerd door de **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="fd4c3-126">De **TestScript** moet inhoud bevatten en moet een afsluit code van 0 retour neren als de werkelijke configuratie overeenkomt met de huidige gewenste status configuratie en een andere afsluit code dan 0 als deze niet overeenkomt.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="fd4c3-127">De huidige gewenste status configuratie is de laatste configuratie die is uitgevaardigd op het knoop punt dat gebruikmaakt van DSC.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="fd4c3-128">Het script moet beginnen met een shebang, zoals `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="fd4c3-129">Gebruiker</span><span class="sxs-lookup"><span data-stu-id="fd4c3-129">User</span></span> |<span data-ttu-id="fd4c3-130">De gebruiker voor het uitvoeren van het script als.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-130">The user to run the script as.</span></span> |
|<span data-ttu-id="fd4c3-131">Groep</span><span class="sxs-lookup"><span data-stu-id="fd4c3-131">Group</span></span> |<span data-ttu-id="fd4c3-132">De groep waarop het script moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fd4c3-133">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fd4c3-133">Common properties</span></span>

|<span data-ttu-id="fd4c3-134">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fd4c3-134">Property</span></span> |<span data-ttu-id="fd4c3-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd4c3-135">Description</span></span> |
|---|---|
|<span data-ttu-id="fd4c3-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fd4c3-136">DependsOn</span></span> |<span data-ttu-id="fd4c3-137">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fd4c3-138">Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="fd4c3-139">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fd4c3-139">Example</span></span>

<span data-ttu-id="fd4c3-140">In het volgende voor beeld wordt het gebruik van de **nxScript** -resource voor het uitvoeren van extra configuratie beheer gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="fd4c3-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
