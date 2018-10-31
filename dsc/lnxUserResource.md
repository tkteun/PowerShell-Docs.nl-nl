---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxUser-Resource
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226029"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="fd8d5-103">DSC voor Linux nxUser-Resource</span><span class="sxs-lookup"><span data-stu-id="fd8d5-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="fd8d5-104">De **nxUser** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikers op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd8d5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fd8d5-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="fd8d5-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fd8d5-106">Properties</span></span>

|  <span data-ttu-id="fd8d5-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fd8d5-107">Property</span></span> |  <span data-ttu-id="fd8d5-108">Geeft de accountnaam waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="fd8d5-109">UserName</span><span class="sxs-lookup"><span data-stu-id="fd8d5-109">UserName</span></span>| <span data-ttu-id="fd8d5-110">Hiermee geeft u de locatie waar u om te controleren of de status van een bestand of map.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="fd8d5-111">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="fd8d5-111">Ensure</span></span>| <span data-ttu-id="fd8d5-112">Hiermee geeft u op of het account bestaat.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-112">Specifies whether the account exists.</span></span> <span data-ttu-id="fd8d5-113">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="fd8d5-114">Volledige naam</span><span class="sxs-lookup"><span data-stu-id="fd8d5-114">FullName</span></span>| <span data-ttu-id="fd8d5-115">Een tekenreeks zijn met de volledige naam moet worden gebruikt voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="fd8d5-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd8d5-116">Description</span></span>| <span data-ttu-id="fd8d5-117">De beschrijving voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-117">The description for the user account.</span></span>|
| <span data-ttu-id="fd8d5-118">Wachtwoord</span><span class="sxs-lookup"><span data-stu-id="fd8d5-118">Password</span></span>| <span data-ttu-id="fd8d5-119">De hash van het wachtwoord van de gebruiker in de juiste vorm voor de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="fd8d5-120">Dit is meestal een gezouten SHA-256, of een hash van SHA-512.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="fd8d5-121">Op Debian en Ubuntu Linux, kan deze waarde worden gegenereerd met de opdracht mkpasswd.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="fd8d5-122">Voor andere Linux-distributies, kan de crypt-methode van de Python-Crypt-bibliotheek worden gebruikt voor het genereren van de hash.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="fd8d5-123">Disabled</span><span class="sxs-lookup"><span data-stu-id="fd8d5-123">Disabled</span></span>| <span data-ttu-id="fd8d5-124">Geeft aan of het account is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="fd8d5-125">Deze eigenschap instellen op **$true** om ervoor te zorgen dat dit account is uitgeschakeld, en stel deze in op **$false** om ervoor te zorgen dat deze is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="fd8d5-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="fd8d5-126">PasswordChangeRequired</span></span>| <span data-ttu-id="fd8d5-127">Geeft aan of de gebruiker het wachtwoord kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="fd8d5-128">Deze eigenschap instellen op **$true** om ervoor te zorgen dat de gebruiker kan niet het wachtwoord wijzigen en stel deze in op **$false** zodat de gebruiker het wachtwoord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="fd8d5-129">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-129">The default value is **$false**.</span></span> <span data-ttu-id="fd8d5-130">Deze eigenschap wordt alleen beoordeeld als het gebruikersaccount niet aanwezig waren en wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="fd8d5-131">Basismap</span><span class="sxs-lookup"><span data-stu-id="fd8d5-131">HomeDirectory</span></span>| <span data-ttu-id="fd8d5-132">De basismap voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-132">The home directory for the user.</span></span>|
| <span data-ttu-id="fd8d5-133">Groeps-id</span><span class="sxs-lookup"><span data-stu-id="fd8d5-133">GroupID</span></span>| <span data-ttu-id="fd8d5-134">De primaire groeps-ID voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="fd8d5-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fd8d5-135">DependsOn</span></span> | <span data-ttu-id="fd8d5-136">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fd8d5-137">Bijvoorbeeld, als de ID van het scriptblok voor resource-configuratie die u wilt uitvoeren 'ResourceName' voor het eerst is en het type is 'ResourceType', de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="fd8d5-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fd8d5-138">Example</span></span>

<span data-ttu-id="fd8d5-139">Het volgende voorbeeld zorgt ervoor dat de gebruiker "monuser" bestaat en lid van de groep 'DBusers is'.</span><span class="sxs-lookup"><span data-stu-id="fd8d5-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```