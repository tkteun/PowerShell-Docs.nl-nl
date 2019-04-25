---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxScript Resource
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077820"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="fb099-103">DSC voor Linux nxScript Resource</span><span class="sxs-lookup"><span data-stu-id="fb099-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="fb099-104">De **nxScript** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het Linux-scripts uitvoeren op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="fb099-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb099-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fb099-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="fb099-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fb099-106">Properties</span></span>

|  <span data-ttu-id="fb099-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fb099-107">Property</span></span> |  <span data-ttu-id="fb099-108">Description</span><span class="sxs-lookup"><span data-stu-id="fb099-108">Description</span></span> |
|---|---|
| <span data-ttu-id="fb099-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="fb099-109">GetScript</span></span>| <span data-ttu-id="fb099-110">Biedt een script dat wordt uitgevoerd wanneer u aanroepen de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb099-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="fb099-111">Het script moet beginnen met een shebang, zoals #! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="fb099-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="fb099-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="fb099-112">SetScript</span></span>| <span data-ttu-id="fb099-113">Bevat een script.</span><span class="sxs-lookup"><span data-stu-id="fb099-113">Provides a script.</span></span> <span data-ttu-id="fb099-114">Wanneer u aanroepen de [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, de **TestScript** als eerste wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="fb099-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="fb099-115">Als de **TestScript** blok retourneert een afsluitcode dan 0, de **SetScript** blok wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb099-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="fb099-116">Als de **TestScript** retourneert een afsluitcode 0, de **SetScript** kan niet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb099-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="fb099-117">Het script moet beginnen met een shebang zoals `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="fb099-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="fb099-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="fb099-118">TestScript</span></span>| <span data-ttu-id="fb099-119">Bevat een script.</span><span class="sxs-lookup"><span data-stu-id="fb099-119">Provides a script.</span></span> <span data-ttu-id="fb099-120">Wanneer u aanroepen de [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, met dit script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb099-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="fb099-121">Als deze een afsluitcode dan 0 retourneert, wordt de SetScript wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb099-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="fb099-122">Als deze een afsluitcode 0 retourneert, de **SetScript** kan niet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb099-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="fb099-123">De **TestScript** wordt ook uitgevoerd wanneer u aanroepen de [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb099-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="fb099-124">Echter, in dit geval de **SetScript** niet wordt uitgevoerd, ongeacht welke afsluitcode wordt geretourneerd vanaf de **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="fb099-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="fb099-125">De **TestScript** moet retourneert een afsluitcode 0 als de feitelijke configuratie komt overeen met de huidige configuratie van gewenste status en een afsluiten code dan 0 als deze niet overeenkomt.</span><span class="sxs-lookup"><span data-stu-id="fb099-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="fb099-126">(De huidige configuratie van gewenste status is de laatste configuratie van kracht op het knooppunt dat van DSC gebruikmaakt).</span><span class="sxs-lookup"><span data-stu-id="fb099-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="fb099-127">Het script moet beginnen met een shebang, zoals 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="fb099-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="fb099-128">Gebruiker</span><span class="sxs-lookup"><span data-stu-id="fb099-128">User</span></span>| <span data-ttu-id="fb099-129">De gebruiker het script als uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="fb099-129">The user to run the script as.</span></span>|
| <span data-ttu-id="fb099-130">Groep</span><span class="sxs-lookup"><span data-stu-id="fb099-130">Group</span></span>| <span data-ttu-id="fb099-131">De groep het script als uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="fb099-131">The group to run the script as.</span></span>|
| <span data-ttu-id="fb099-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fb099-132">DependsOn</span></span> | <span data-ttu-id="fb099-133">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="fb099-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fb099-134">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fb099-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="fb099-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fb099-135">Example</span></span>

<span data-ttu-id="fb099-136">Het volgende voorbeeld ziet u het gebruik van de **nxScript** resource die u wilt het beheer van aanvullende configuratie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="fb099-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

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