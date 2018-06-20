---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxUser Resource
ms.openlocfilehash: ca77bcd1f23a78ddb9e2ac988e4aadfec504bbbe
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218923"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="a52d3-103">DSC voor Linux nxUser Resource</span><span class="sxs-lookup"><span data-stu-id="a52d3-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="a52d3-104">De **nxUser** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme op voor het beheren van lokale gebruikers op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="a52d3-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a52d3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a52d3-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a52d3-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a52d3-106">Properties</span></span>

|  <span data-ttu-id="a52d3-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="a52d3-107">Property</span></span> |  <span data-ttu-id="a52d3-108">Geeft de accountnaam waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="a52d3-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="a52d3-109">UserName</span><span class="sxs-lookup"><span data-stu-id="a52d3-109">UserName</span></span>| <span data-ttu-id="a52d3-110">Hiermee geeft u de locatie op waar u om te controleren of de status voor een bestand of map.</span><span class="sxs-lookup"><span data-stu-id="a52d3-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="a52d3-111">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="a52d3-111">Ensure</span></span>| <span data-ttu-id="a52d3-112">Geeft aan of het account bestaat.</span><span class="sxs-lookup"><span data-stu-id="a52d3-112">Specifies whether the account exists.</span></span> <span data-ttu-id="a52d3-113">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="a52d3-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="a52d3-114">Volledige naam</span><span class="sxs-lookup"><span data-stu-id="a52d3-114">FullName</span></span>| <span data-ttu-id="a52d3-115">Een tekenreeks met de volledige naam moet worden gebruikt voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="a52d3-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="a52d3-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a52d3-116">Description</span></span>| <span data-ttu-id="a52d3-117">De beschrijving voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="a52d3-117">The description for the user account.</span></span>|
| <span data-ttu-id="a52d3-118">Wachtwoord</span><span class="sxs-lookup"><span data-stu-id="a52d3-118">Password</span></span>| <span data-ttu-id="a52d3-119">De hash van het wachtwoord van gebruikers in de juiste vorm voor de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="a52d3-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="a52d3-120">Dit is meestal een gezouten SHA-256 of SHA-512 hash.</span><span class="sxs-lookup"><span data-stu-id="a52d3-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="a52d3-121">Voor Debian en Ubuntu Linux, kan deze waarde met de opdracht mkpasswd worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a52d3-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="a52d3-122">Voor andere Linux-distributies, kan de methode crypt van Python Crypt bibliotheek worden gebruikt voor het genereren van de hash.</span><span class="sxs-lookup"><span data-stu-id="a52d3-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="a52d3-123">Disabled</span><span class="sxs-lookup"><span data-stu-id="a52d3-123">Disabled</span></span>| <span data-ttu-id="a52d3-124">Hiermee wordt aangegeven of het account is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="a52d3-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="a52d3-125">Deze eigenschap instellen op **$true** om ervoor te zorgen dat dit account is uitgeschakeld en stel deze in op **$false** om ervoor te zorgen dat deze is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="a52d3-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="a52d3-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="a52d3-126">PasswordChangeRequired</span></span>| <span data-ttu-id="a52d3-127">Hiermee wordt aangegeven of de gebruiker het wachtwoord kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a52d3-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="a52d3-128">Deze eigenschap instellen op **$true** om ervoor te zorgen dat de gebruiker kan het wachtwoord wijzigen en stel deze in op **$false** zodat de gebruiker het wachtwoord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a52d3-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="a52d3-129">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="a52d3-129">The default value is **$false**.</span></span> <span data-ttu-id="a52d3-130">Deze eigenschap wordt alleen beoordeeld als het gebruikersaccount niet aanwezig waren en wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a52d3-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="a52d3-131">Basismap</span><span class="sxs-lookup"><span data-stu-id="a52d3-131">HomeDirectory</span></span>| <span data-ttu-id="a52d3-132">De basismap voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a52d3-132">The home directory for the user.</span></span>|
| <span data-ttu-id="a52d3-133">Groeps-id</span><span class="sxs-lookup"><span data-stu-id="a52d3-133">GroupID</span></span>| <span data-ttu-id="a52d3-134">De primaire groeps-ID voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a52d3-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="a52d3-135">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a52d3-135">DependsOn</span></span> | <span data-ttu-id="a52d3-136">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="a52d3-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a52d3-137">Bijvoorbeeld, als de ID van het scriptblok voor resource configuratie die u wilt uitvoeren eerst is 'ResourceName' en het type is 'ResourceType', de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a52d3-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a52d3-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a52d3-138">Example</span></span>

<span data-ttu-id="a52d3-139">Het volgende voorbeeld zorgt ervoor dat de gebruiker "monuser" bestaat en lid van de groep 'DBusers is'.</span><span class="sxs-lookup"><span data-stu-id="a52d3-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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