---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxGroup-Resource
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048326"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="96fce-103">DSC voor Linux nxGroup-Resource</span><span class="sxs-lookup"><span data-stu-id="96fce-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="96fce-104">De **nxGroup** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="96fce-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="96fce-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="96fce-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="96fce-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="96fce-106">Properties</span></span>

|  <span data-ttu-id="96fce-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="96fce-107">Property</span></span> |  <span data-ttu-id="96fce-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="96fce-108">Description</span></span> |
|---|---|
| <span data-ttu-id="96fce-109">Groepsnaam</span><span class="sxs-lookup"><span data-stu-id="96fce-109">GroupName</span></span>| <span data-ttu-id="96fce-110">Hiermee geeft u de naam van de groep waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="96fce-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="96fce-111">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="96fce-111">Ensure</span></span>| <span data-ttu-id="96fce-112">Hiermee bepaalt u of om te controleren of de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="96fce-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="96fce-113">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="96fce-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="96fce-114">Stel deze in op 'Ontbreekt' om te controleren of dat de groep bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="96fce-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="96fce-115">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="96fce-115">The default value is "Present".</span></span>|
| <span data-ttu-id="96fce-116">Leden</span><span class="sxs-lookup"><span data-stu-id="96fce-116">Members</span></span>| <span data-ttu-id="96fce-117">Hiermee geeft u de leden die de groep.</span><span class="sxs-lookup"><span data-stu-id="96fce-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="96fce-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="96fce-118">MembersToInclude</span></span>| <span data-ttu-id="96fce-119">Hiermee geeft u de gebruikers die u wilt ervoor zorgen zijn leden van de groep.</span><span class="sxs-lookup"><span data-stu-id="96fce-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="96fce-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="96fce-120">MembersToExclude</span></span>| <span data-ttu-id="96fce-121">Hiermee geeft u de gebruikers die u wilt ervoor zorgen geen lid van de groep zijn.</span><span class="sxs-lookup"><span data-stu-id="96fce-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="96fce-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="96fce-122">PreferredGroupID</span></span>| <span data-ttu-id="96fce-123">Wordt indien mogelijk de groeps-id ingesteld op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="96fce-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="96fce-124">Als de groeps-id momenteel gebruikt wordt, worden de volgende beschikbare groeps-id wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="96fce-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="96fce-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="96fce-125">DependsOn</span></span> | <span data-ttu-id="96fce-126">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="96fce-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="96fce-127">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="96fce-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="96fce-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="96fce-128">Example</span></span>

<span data-ttu-id="96fce-129">Het volgende voorbeeld zorgt ervoor dat de gebruiker monuser bestaat en lid van de groep 'DBusers is'.</span><span class="sxs-lookup"><span data-stu-id="96fce-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
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