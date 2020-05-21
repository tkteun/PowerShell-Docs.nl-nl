---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxUser-resource
ms.openlocfilehash: 4cf8080fbfa58e082ed007d42d6aa2648d1cf58a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557172"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="456d9-103">DSC voor Linux nxUser-resource</span><span class="sxs-lookup"><span data-stu-id="456d9-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="456d9-104">De **nxUser** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikers op een Linux-knoop punt.</span><span class="sxs-lookup"><span data-stu-id="456d9-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="456d9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="456d9-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="456d9-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="456d9-106">Properties</span></span>

|<span data-ttu-id="456d9-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="456d9-107">Property</span></span> |<span data-ttu-id="456d9-108">Hiermee wordt de account naam aangegeven waarvoor u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="456d9-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="456d9-109">UserName</span><span class="sxs-lookup"><span data-stu-id="456d9-109">UserName</span></span> |<span data-ttu-id="456d9-110">Hiermee geeft u de locatie op waar u de status van een bestand of map wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="456d9-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="456d9-111">FullName</span><span class="sxs-lookup"><span data-stu-id="456d9-111">FullName</span></span> |<span data-ttu-id="456d9-112">Een teken reeks die de volledige naam bevat die moet worden gebruikt voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="456d9-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="456d9-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="456d9-113">Description</span></span> |<span data-ttu-id="456d9-114">De beschrijving voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="456d9-114">The description for the user account.</span></span> |
|<span data-ttu-id="456d9-115">Wachtwoord</span><span class="sxs-lookup"><span data-stu-id="456d9-115">Password</span></span> |<span data-ttu-id="456d9-116">De hash van het wacht woord van de gebruiker in het juiste formulier voor de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="456d9-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="456d9-117">Normaal gesp roken is dit een gezouten SHA-256-of SHA-512-hash.</span><span class="sxs-lookup"><span data-stu-id="456d9-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="456d9-118">Op Debian en Ubuntu Linux kan deze waarde worden gegenereerd met de `mkpasswd` opdracht.</span><span class="sxs-lookup"><span data-stu-id="456d9-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="456d9-119">Voor andere Linux-distributies kan de cryptografie methode van de cryptografie bibliotheek van python worden gebruikt voor het genereren van de hash.</span><span class="sxs-lookup"><span data-stu-id="456d9-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="456d9-120">Uitgeschakeld</span><span class="sxs-lookup"><span data-stu-id="456d9-120">Disabled</span></span> |<span data-ttu-id="456d9-121">Hiermee wordt aangegeven of het account is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="456d9-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="456d9-122">Stel deze eigenschap in op `$true` om ervoor te zorgen dat dit account is uitgeschakeld en stel dit in op `$false` om ervoor te zorgen dat deze is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="456d9-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="456d9-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="456d9-123">PasswordChangeRequired</span></span> |<span data-ttu-id="456d9-124">Hiermee wordt aangegeven of de gebruiker het wacht woord kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="456d9-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="456d9-125">Stel deze eigenschap in op `$true` om ervoor te zorgen dat de gebruiker het wacht woord niet kan wijzigen en stel in om de gebruiker in staat te stellen `$false` het wacht woord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="456d9-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="456d9-126">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="456d9-126">The default value is `$false`.</span></span> <span data-ttu-id="456d9-127">Deze eigenschap wordt alleen geëvalueerd als het gebruikers account niet eerder bestaat en wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="456d9-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="456d9-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="456d9-128">HomeDirectory</span></span> |<span data-ttu-id="456d9-129">De basismap voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="456d9-129">The home directory for the user.</span></span> |
|<span data-ttu-id="456d9-130">Groep</span><span class="sxs-lookup"><span data-stu-id="456d9-130">GroupID</span></span> |<span data-ttu-id="456d9-131">De primaire groeps-ID voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="456d9-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="456d9-132">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="456d9-132">Common properties</span></span>

|<span data-ttu-id="456d9-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="456d9-133">Property</span></span> |<span data-ttu-id="456d9-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="456d9-134">Description</span></span> |
|---|---|
|<span data-ttu-id="456d9-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="456d9-135">DependsOn</span></span> |<span data-ttu-id="456d9-136">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="456d9-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="456d9-137">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="456d9-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="456d9-138">Zo</span><span class="sxs-lookup"><span data-stu-id="456d9-138">Ensure</span></span> |<span data-ttu-id="456d9-139">Hiermee geeft u op of het account bestaat.</span><span class="sxs-lookup"><span data-stu-id="456d9-139">Specifies whether the account exists.</span></span> <span data-ttu-id="456d9-140">Stel deze eigenschap in op aanwezig om er zeker van te **zijn** dat het account bestaat en stel het in op **afwezig** om ervoor te zorgen dat het account niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="456d9-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="456d9-141">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="456d9-141">Example</span></span>

<span data-ttu-id="456d9-142">In het volgende voor beeld wordt ervoor gezorgd dat de gebruiker ' monuser ' bestaat en lid is van de groep ' DBusers '.</span><span class="sxs-lookup"><span data-stu-id="456d9-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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
