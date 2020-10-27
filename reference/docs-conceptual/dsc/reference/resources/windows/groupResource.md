---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-groeps resource
description: DSC-groeps resource
ms.openlocfilehash: 9e8931fe1227f3ac258c46fb1aecf4586958de66
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650529"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="4583f-103">DSC-groeps resource</span><span class="sxs-lookup"><span data-stu-id="4583f-103">DSC Group Resource</span></span>

> <span data-ttu-id="4583f-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="4583f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4583f-105">De **groeps** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="4583f-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4583f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4583f-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4583f-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="4583f-107">Properties</span></span>

|<span data-ttu-id="4583f-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="4583f-108">Property</span></span> |<span data-ttu-id="4583f-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4583f-109">Description</span></span> |
|---|---|
|<span data-ttu-id="4583f-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="4583f-110">GroupName</span></span> |<span data-ttu-id="4583f-111">De naam van de groep waarvoor u een specifieke status wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="4583f-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="4583f-112">Referentie</span><span class="sxs-lookup"><span data-stu-id="4583f-112">Credential</span></span> |<span data-ttu-id="4583f-113">De referenties die nodig zijn voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="4583f-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="4583f-114">Dit account moet over de juiste Active Directory machtigingen beschikken om alle niet-lokale accounts aan de groep toe te voegen. anders treedt er een fout op wanneer de configuratie wordt uitgevoerd op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="4583f-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="4583f-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4583f-115">Description</span></span> |<span data-ttu-id="4583f-116">De beschrijving van de groep.</span><span class="sxs-lookup"><span data-stu-id="4583f-116">The description of the group.</span></span> |
|<span data-ttu-id="4583f-117">Leden</span><span class="sxs-lookup"><span data-stu-id="4583f-117">Members</span></span> |<span data-ttu-id="4583f-118">Gebruik deze eigenschap om het huidige groepslid maatschap te vervangen door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="4583f-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="4583f-119">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="4583f-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="4583f-120">Als u deze eigenschap in een configuratie instelt, moet u de eigenschap **MembersToExclude** of **MembersToInclude** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4583f-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="4583f-121">Hierdoor wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4583f-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="4583f-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="4583f-122">MembersToExclude</span></span> |<span data-ttu-id="4583f-123">Gebruik deze eigenschap om leden te verwijderen uit het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="4583f-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="4583f-124">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="4583f-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="4583f-125">Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4583f-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4583f-126">Hierdoor wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4583f-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="4583f-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="4583f-127">MembersToInclude</span></span> |<span data-ttu-id="4583f-128">Gebruik deze eigenschap om leden toe te voegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="4583f-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="4583f-129">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="4583f-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="4583f-130">Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4583f-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4583f-131">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4583f-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4583f-132">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="4583f-132">Common properties</span></span>

|<span data-ttu-id="4583f-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="4583f-133">Property</span></span> |<span data-ttu-id="4583f-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4583f-134">Description</span></span> |
|---|---|
|<span data-ttu-id="4583f-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4583f-135">DependsOn</span></span> |<span data-ttu-id="4583f-136">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="4583f-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4583f-137">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="4583f-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4583f-138">Zo</span><span class="sxs-lookup"><span data-stu-id="4583f-138">Ensure</span></span> |<span data-ttu-id="4583f-139">Hiermee wordt aangegeven of de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="4583f-139">Indicates if the group exists.</span></span> <span data-ttu-id="4583f-140">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de groep niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="4583f-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="4583f-141">**Als u** deze instelling inschakelt, zorgt u ervoor dat de groep bestaat.</span><span class="sxs-lookup"><span data-stu-id="4583f-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="4583f-142">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="4583f-142">The default value is **Present** .</span></span> |
|<span data-ttu-id="4583f-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4583f-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="4583f-144">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="4583f-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4583f-145">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="4583f-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4583f-146">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4583f-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="4583f-147">Voor beeld 1: ervoor zorgen dat groep niet aanwezig is</span><span class="sxs-lookup"><span data-stu-id="4583f-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="4583f-148">In het volgende voor beeld ziet u hoe u ervoor kunt zorgen dat een groep met de naam ' TestGroup ' ontbreekt.</span><span class="sxs-lookup"><span data-stu-id="4583f-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="4583f-149">Voor beeld 2: domein gebruiker toevoegen aan lokale groep</span><span class="sxs-lookup"><span data-stu-id="4583f-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="4583f-150">In het volgende voor beeld ziet u hoe u een Active Directory gebruiker toevoegt aan de lokale groep Administrators als onderdeel van een test omgeving voor meerdere machines waar u al een PSCredential gebruikt voor het lokale beheerders account.</span><span class="sxs-lookup"><span data-stu-id="4583f-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="4583f-151">Aangezien dit ook wordt gebruikt voor het domein beheerders account (na domein promotie), moeten we deze bestaande PSCredential converteren naar een gebruiks vriendelijke domein referentie.</span><span class="sxs-lookup"><span data-stu-id="4583f-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="4583f-152">Vervolgens kunnen we een domein gebruiker toevoegen aan de lokale groep Administrators op de lidserver.</span><span class="sxs-lookup"><span data-stu-id="4583f-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="4583f-153">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="4583f-153">Example 3</span></span>

<span data-ttu-id="4583f-154">In het volgende voor beeld ziet u hoe u ervoor zorgt dat een lokale groep TigerTeamAdmins op de server TigerTeamSource.Contoso.Com geen bepaald domein account bevat Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="4583f-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```
