---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxGroup-resource
ms.openlocfilehash: f196c74b94ec27818d58b59d1e489facd8ab0a65
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464431"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="1f06f-103">DSC voor Linux nxGroup-resource</span><span class="sxs-lookup"><span data-stu-id="1f06f-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="1f06f-104">De **nxGroup** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="1f06f-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f06f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f06f-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="1f06f-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="1f06f-106">Properties</span></span>

|<span data-ttu-id="1f06f-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1f06f-107">Property</span></span> |<span data-ttu-id="1f06f-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1f06f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="1f06f-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="1f06f-109">GroupName</span></span> |<span data-ttu-id="1f06f-110">Hiermee geeft u de naam van de groep waarvoor u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="1f06f-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="1f06f-111">Leden</span><span class="sxs-lookup"><span data-stu-id="1f06f-111">Members</span></span> |<span data-ttu-id="1f06f-112">Hiermee geeft u de leden op die de groep vormen.</span><span class="sxs-lookup"><span data-stu-id="1f06f-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="1f06f-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="1f06f-113">MembersToInclude</span></span> |<span data-ttu-id="1f06f-114">Hiermee geeft u de gebruikers die u wilt controleren, lid zijn van de groep.</span><span class="sxs-lookup"><span data-stu-id="1f06f-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="1f06f-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="1f06f-115">MembersToExclude</span></span> |<span data-ttu-id="1f06f-116">Hiermee geeft u de gebruikers die u wilt controleren, geen lid zijn van de groep.</span><span class="sxs-lookup"><span data-stu-id="1f06f-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="1f06f-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="1f06f-117">PreferredGroupID</span></span> |<span data-ttu-id="1f06f-118">Hiermee stelt u de groeps-id in op de gegeven waarde, indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="1f06f-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="1f06f-119">Als de groeps-id momenteel in gebruik is, wordt de volgende beschik bare groeps-id gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1f06f-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1f06f-120">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="1f06f-120">Common properties</span></span>

|<span data-ttu-id="1f06f-121">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1f06f-121">Property</span></span> |<span data-ttu-id="1f06f-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1f06f-122">Description</span></span> |
|---|---|
|<span data-ttu-id="1f06f-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1f06f-123">DependsOn</span></span> |<span data-ttu-id="1f06f-124">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1f06f-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1f06f-125">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="1f06f-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1f06f-126">Zo</span><span class="sxs-lookup"><span data-stu-id="1f06f-126">Ensure</span></span> |<span data-ttu-id="1f06f-127">Hiermee wordt bepaald of er wordt gecontroleerd of de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="1f06f-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="1f06f-128">Stel deze eigenschap in op **presen teren** om te controleren of de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="1f06f-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="1f06f-129">Stel deze in op **afwezig** om te controleren of de groep niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="1f06f-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="1f06f-130">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="1f06f-130">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="1f06f-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1f06f-131">Example</span></span>

<span data-ttu-id="1f06f-132">In het volgende voor beeld wordt ervoor gezorgd dat de gebruiker ' monuser ' bestaat en lid is van de groep ' DBusers '.</span><span class="sxs-lookup"><span data-stu-id="1f06f-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```
