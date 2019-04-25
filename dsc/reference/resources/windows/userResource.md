---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Gebruiker van de DSC-Resource
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076891"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="44066-103">Gebruiker van de DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="44066-103">DSC User Resource</span></span>

<span data-ttu-id="44066-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="44066-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="44066-105">De **gebruiker** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikersaccounts op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="44066-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="44066-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="44066-106">Syntax</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="44066-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="44066-107">Properties</span></span>

|  <span data-ttu-id="44066-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="44066-108">Property</span></span>  |  <span data-ttu-id="44066-109">Description</span><span class="sxs-lookup"><span data-stu-id="44066-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="44066-110">UserName</span><span class="sxs-lookup"><span data-stu-id="44066-110">UserName</span></span>| <span data-ttu-id="44066-111">Geeft de accountnaam waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="44066-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="44066-112">Description</span><span class="sxs-lookup"><span data-stu-id="44066-112">Description</span></span>| <span data-ttu-id="44066-113">Geeft aan dat de beschrijving die u wilt gebruiken voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="44066-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="44066-114">Uitgeschakeld</span><span class="sxs-lookup"><span data-stu-id="44066-114">Disabled</span></span>| <span data-ttu-id="44066-115">Geeft aan of het account is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="44066-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="44066-116">Deze eigenschap instellen op `$true` om ervoor te zorgen dat dit account is uitgeschakeld, en stel deze in op `$false` om ervoor te zorgen dat deze is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="44066-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="44066-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="44066-117">Ensure</span></span>| <span data-ttu-id="44066-118">Geeft aan of het account bestaat.</span><span class="sxs-lookup"><span data-stu-id="44066-118">Indicates if the account exists.</span></span> <span data-ttu-id="44066-119">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="44066-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="44066-120">Volledige naam</span><span class="sxs-lookup"><span data-stu-id="44066-120">FullName</span></span>| <span data-ttu-id="44066-121">Hiermee geeft u een tekenreeks zijn met de volledige naam die u wilt gebruiken voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="44066-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="44066-122">Wachtwoord</span><span class="sxs-lookup"><span data-stu-id="44066-122">Password</span></span>| <span data-ttu-id="44066-123">Geeft het wachtwoord die u wilt gebruiken voor dit account.</span><span class="sxs-lookup"><span data-stu-id="44066-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="44066-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="44066-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="44066-125">Hiermee wordt aangegeven als de gebruiker het wachtwoord kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44066-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="44066-126">Deze eigenschap instellen op `$true` om ervoor te zorgen dat de gebruiker kan niet het wachtwoord wijzigen en stel deze in op `$false` zodat de gebruiker het wachtwoord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44066-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="44066-127">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="44066-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="44066-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="44066-128">PasswordChangeRequired</span></span>| <span data-ttu-id="44066-129">Hiermee wordt aangegeven als de gebruiker het wachtwoord bij de volgende aanmelding moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44066-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="44066-130">Deze eigenschap instellen op `$true` als de gebruiker het wachtwoord moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44066-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="44066-131">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="44066-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="44066-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="44066-132">PasswordNeverExpires</span></span>| <span data-ttu-id="44066-133">Hiermee wordt aangegeven als het wachtwoord verloopt.</span><span class="sxs-lookup"><span data-stu-id="44066-133">Indicates if the password will expire.</span></span> <span data-ttu-id="44066-134">Om ervoor te zorgen dat het wachtwoord voor dit account nooit verloopt, deze eigenschap instellen op `$true`, en stel deze in op `$false` als het wachtwoord verloopt.</span><span class="sxs-lookup"><span data-stu-id="44066-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="44066-135">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="44066-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="44066-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="44066-136">DependsOn</span></span> | <span data-ttu-id="44066-137">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="44066-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="44066-138">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="44066-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="44066-139">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="44066-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```