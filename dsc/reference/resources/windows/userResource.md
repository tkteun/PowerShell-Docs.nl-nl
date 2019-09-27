---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-gebruikers resource
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324056"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="00cb5-103">DSC-gebruikers resource</span><span class="sxs-lookup"><span data-stu-id="00cb5-103">DSC User Resource</span></span>

> <span data-ttu-id="00cb5-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="00cb5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="00cb5-105">De **gebruikers** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikers accounts op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="00cb5-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="00cb5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="00cb5-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="00cb5-107">properties</span><span class="sxs-lookup"><span data-stu-id="00cb5-107">Properties</span></span>

|<span data-ttu-id="00cb5-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="00cb5-108">Property</span></span> |<span data-ttu-id="00cb5-109">Description</span><span class="sxs-lookup"><span data-stu-id="00cb5-109">Description</span></span> |
|---|---|
|<span data-ttu-id="00cb5-110">UserName</span><span class="sxs-lookup"><span data-stu-id="00cb5-110">UserName</span></span> |<span data-ttu-id="00cb5-111">Hiermee wordt de account naam aangegeven waarvoor u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="00cb5-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="00cb5-112">Description</span><span class="sxs-lookup"><span data-stu-id="00cb5-112">Description</span></span> |<span data-ttu-id="00cb5-113">Hiermee geeft u de beschrijving op die u wilt gebruiken voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="00cb5-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="00cb5-114">Uitgeschakeld</span><span class="sxs-lookup"><span data-stu-id="00cb5-114">Disabled</span></span> |<span data-ttu-id="00cb5-115">Hiermee wordt aangegeven of het account is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="00cb5-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="00cb5-116">Stel deze eigenschap in `$true` op om ervoor te zorgen dat dit account is uitgeschakeld en stel `$false` dit in op om ervoor te zorgen dat deze is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="00cb5-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="00cb5-117">Volledige naam</span><span class="sxs-lookup"><span data-stu-id="00cb5-117">FullName</span></span> |<span data-ttu-id="00cb5-118">Hiermee geeft u een teken reeks met de volledige naam die u wilt gebruiken voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="00cb5-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="00cb5-119">Wachtwoord</span><span class="sxs-lookup"><span data-stu-id="00cb5-119">Password</span></span> |<span data-ttu-id="00cb5-120">Hiermee geeft u het wacht woord op dat u wilt gebruiken voor dit account.</span><span class="sxs-lookup"><span data-stu-id="00cb5-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="00cb5-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="00cb5-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="00cb5-122">Hiermee wordt aangegeven of de gebruiker het wacht woord kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="00cb5-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="00cb5-123">Stel deze eigenschap in `$true` op om ervoor te zorgen dat de gebruiker het wacht woord niet kan wijzigen `$false` en stel in om de gebruiker in staat te stellen het wacht woord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="00cb5-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="00cb5-124">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="00cb5-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="00cb5-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="00cb5-125">PasswordChangeRequired</span></span> |<span data-ttu-id="00cb5-126">Hiermee wordt aangegeven of de gebruiker het wacht woord moet wijzigen bij de volgende aanmelding.</span><span class="sxs-lookup"><span data-stu-id="00cb5-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="00cb5-127">Stel deze eigenschap in `$true` op als de gebruiker het wacht woord moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="00cb5-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="00cb5-128">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="00cb5-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="00cb5-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="00cb5-129">PasswordNeverExpires</span></span> |<span data-ttu-id="00cb5-130">Hiermee wordt aangegeven of het wacht woord verloopt.</span><span class="sxs-lookup"><span data-stu-id="00cb5-130">Indicates if the password will expire.</span></span> <span data-ttu-id="00cb5-131">Stel deze eigenschap in `$true`op om ervoor te zorgen dat het wacht woord voor dit account nooit verloopt.</span><span class="sxs-lookup"><span data-stu-id="00cb5-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="00cb5-132">Stel deze waarde `$false` in op als het wacht woord verloopt.</span><span class="sxs-lookup"><span data-stu-id="00cb5-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="00cb5-133">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="00cb5-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="00cb5-134">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="00cb5-134">Common properties</span></span>

|<span data-ttu-id="00cb5-135">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="00cb5-135">Property</span></span> |<span data-ttu-id="00cb5-136">Description</span><span class="sxs-lookup"><span data-stu-id="00cb5-136">Description</span></span> |
|---|---|
|<span data-ttu-id="00cb5-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="00cb5-137">DependsOn</span></span> |<span data-ttu-id="00cb5-138">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="00cb5-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="00cb5-139">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="00cb5-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="00cb5-140">Zo</span><span class="sxs-lookup"><span data-stu-id="00cb5-140">Ensure</span></span> |<span data-ttu-id="00cb5-141">Hiermee wordt aangegeven of het account bestaat.</span><span class="sxs-lookup"><span data-stu-id="00cb5-141">Indicates if the account exists.</span></span> <span data-ttu-id="00cb5-142">Stel deze eigenschap in op aanwezig om er zeker van te **zijn** dat het account bestaat en stel het in op **afwezig** om ervoor te zorgen dat het account niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="00cb5-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="00cb5-143">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="00cb5-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="00cb5-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="00cb5-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="00cb5-145">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="00cb5-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="00cb5-146">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="00cb5-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="00cb5-147">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00cb5-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="00cb5-148">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="00cb5-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```