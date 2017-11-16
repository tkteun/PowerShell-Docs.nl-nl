---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-gebruikersbron
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
#<a name="dsc-user-resource"></a><span data-ttu-id="375d4-103">Gebruiker van de DSC-Resource #</span><span class="sxs-lookup"><span data-stu-id="375d4-103">DSC User Resource#</span></span>

 
><span data-ttu-id="375d4-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="375d4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="375d4-105">De __gebruiker__ in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van lokale gebruikersaccounts in het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="375d4-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="375d4-106">Syntaxis ##</span><span class="sxs-lookup"><span data-stu-id="375d4-106">Syntax##</span></span>

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

## <a name="properties"></a><span data-ttu-id="375d4-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="375d4-107">Properties</span></span>
|  <span data-ttu-id="375d4-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="375d4-108">Property</span></span>  |  <span data-ttu-id="375d4-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="375d4-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="375d4-110">UserName</span><span class="sxs-lookup"><span data-stu-id="375d4-110">UserName</span></span>| <span data-ttu-id="375d4-111">Geeft de accountnaam waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="375d4-111">Indicates the account name for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="375d4-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="375d4-112">Description</span></span>| <span data-ttu-id="375d4-113">Hiermee geeft u de beschrijving die u wilt gebruiken voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="375d4-113">Indicates the description you want to use for the user account.</span></span>| 
| <span data-ttu-id="375d4-114">Disabled</span><span class="sxs-lookup"><span data-stu-id="375d4-114">Disabled</span></span>| <span data-ttu-id="375d4-115">Hiermee wordt aangegeven of het account is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="375d4-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="375d4-116">Deze eigenschap instellen op __$true__ om ervoor te zorgen dat dit account is uitgeschakeld en stel deze in op __$false__ om ervoor te zorgen dat deze is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="375d4-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="375d4-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="375d4-117">Ensure</span></span>| <span data-ttu-id="375d4-118">Hiermee wordt aangegeven of het account bestaat.</span><span class="sxs-lookup"><span data-stu-id="375d4-118">Indicates if the account exists.</span></span> <span data-ttu-id="375d4-119">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="375d4-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="375d4-120">Volledige naam</span><span class="sxs-lookup"><span data-stu-id="375d4-120">FullName</span></span>| <span data-ttu-id="375d4-121">Hiermee geeft u een tekenreeks met de volledige naam die u wilt gebruiken voor het gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="375d4-121">Represents a string with the full name you want to use for the user account.</span></span>| 
| <span data-ttu-id="375d4-122">Wachtwoord</span><span class="sxs-lookup"><span data-stu-id="375d4-122">Password</span></span>| <span data-ttu-id="375d4-123">Geeft het wachtwoord dat u wilt gebruiken voor dit account.</span><span class="sxs-lookup"><span data-stu-id="375d4-123">Indicates the password you want to use for this account.</span></span> | 
| <span data-ttu-id="375d4-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="375d4-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="375d4-125">Hiermee wordt aangegeven als de gebruiker het wachtwoord kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="375d4-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="375d4-126">Deze eigenschap instellen op __$true__ om ervoor te zorgen dat de gebruiker kan het wachtwoord wijzigen en stel deze in op __$false__ zodat de gebruiker het wachtwoord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="375d4-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="375d4-127">De standaardwaarde is __$false__.</span><span class="sxs-lookup"><span data-stu-id="375d4-127">The default value is __$false__.</span></span>| 
| <span data-ttu-id="375d4-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="375d4-128">PasswordChangeRequired</span></span>| <span data-ttu-id="375d4-129">Hiermee wordt aangegeven als de gebruiker bij de volgende aanmelding in het wachtwoord moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="375d4-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="375d4-130">Deze eigenschap instellen op __$true__ als de gebruiker het wachtwoord moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="375d4-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="375d4-131">De standaardwaarde is __$true__.</span><span class="sxs-lookup"><span data-stu-id="375d4-131">The default value is __$true__.</span></span>| 
| <span data-ttu-id="375d4-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="375d4-132">PasswordNeverExpires</span></span>| <span data-ttu-id="375d4-133">Hiermee wordt aangegeven als het wachtwoord vervalt.</span><span class="sxs-lookup"><span data-stu-id="375d4-133">Indicates if the password will expire.</span></span> <span data-ttu-id="375d4-134">Om ervoor te zorgen dat het wachtwoord voor dit account nooit verloopt, deze eigenschap instellen op __$true__, en wordt ingesteld op __$false__ als het wachtwoord verloopt.</span><span class="sxs-lookup"><span data-stu-id="375d4-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="375d4-135">De standaardwaarde is __$false__.</span><span class="sxs-lookup"><span data-stu-id="375d4-135">The default value is __$false__.</span></span>| 
| <span data-ttu-id="375d4-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="375d4-136">DependsOn</span></span> | <span data-ttu-id="375d4-137">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="375d4-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="375d4-138">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="375d4-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="375d4-139">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="375d4-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

