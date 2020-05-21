---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
description: Biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.
title: DSC-groeps resource
ms.openlocfilehash: 99b9cafdd4d799e18e1b9b1f08d7dd41ec435711
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560335"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="0ac62-104">DSC-groeps resource</span><span class="sxs-lookup"><span data-stu-id="0ac62-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="0ac62-105">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="0ac62-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="0ac62-106">De **groeps** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="0ac62-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="0ac62-107">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [groeps bron](groupResource.md) aanroept voor elke groep die in de `GroupName` para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0ac62-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="0ac62-108">Gebruik deze resource als u dezelfde lijst met leden wilt toevoegen aan of verwijderen uit meer dan één groep, als u meer dan één groep wilt verwijderen of meer dan één groep met dezelfde lijst met leden wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0ac62-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ac62-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0ac62-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0ac62-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0ac62-110">Properties</span></span>

|<span data-ttu-id="0ac62-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="0ac62-111">Property</span></span> |<span data-ttu-id="0ac62-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0ac62-112">Description</span></span> |
|---|---|
|<span data-ttu-id="0ac62-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="0ac62-113">GroupName</span></span> |<span data-ttu-id="0ac62-114">De namen van de groepen waarvoor u een specifieke status wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="0ac62-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="0ac62-115">Leden</span><span class="sxs-lookup"><span data-stu-id="0ac62-115">Members</span></span> |<span data-ttu-id="0ac62-116">Gebruik deze eigenschap om het huidige groepslid maatschap te vervangen door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="0ac62-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="0ac62-117">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="0ac62-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="0ac62-118">Als u deze eigenschap in een configuratie instelt, moet u de eigenschap **MembersToExclude** of **MembersToInclude** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0ac62-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="0ac62-119">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0ac62-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="0ac62-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0ac62-120">Description</span></span> |<span data-ttu-id="0ac62-121">De beschrijving van de groep.</span><span class="sxs-lookup"><span data-stu-id="0ac62-121">The description of the group.</span></span> |
|<span data-ttu-id="0ac62-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="0ac62-122">MembersToInclude</span></span> |<span data-ttu-id="0ac62-123">Gebruik deze eigenschap om leden toe te voegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="0ac62-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="0ac62-124">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="0ac62-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="0ac62-125">Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0ac62-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="0ac62-126">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0ac62-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="0ac62-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="0ac62-127">MembersToExclude</span></span> |<span data-ttu-id="0ac62-128">Gebruik deze eigenschap om leden te verwijderen uit het bestaande lidmaatschap van de groepen.</span><span class="sxs-lookup"><span data-stu-id="0ac62-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="0ac62-129">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="0ac62-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="0ac62-130">Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0ac62-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="0ac62-131">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0ac62-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="0ac62-132">Referentie</span><span class="sxs-lookup"><span data-stu-id="0ac62-132">Credential</span></span> |<span data-ttu-id="0ac62-133">De referenties die nodig zijn voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="0ac62-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="0ac62-134">Dit account moet over de juiste Active Directory machtigingen beschikken om alle niet-lokale accounts aan de groep toe te voegen. anders treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="0ac62-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0ac62-135">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0ac62-135">Common properties</span></span>

|<span data-ttu-id="0ac62-136">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="0ac62-136">Property</span></span> |<span data-ttu-id="0ac62-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0ac62-137">Description</span></span> |
|---|---|
|<span data-ttu-id="0ac62-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0ac62-138">DependsOn</span></span> |<span data-ttu-id="0ac62-139">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="0ac62-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0ac62-140">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="0ac62-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0ac62-141">Zo</span><span class="sxs-lookup"><span data-stu-id="0ac62-141">Ensure</span></span> |<span data-ttu-id="0ac62-142">Hiermee wordt aangegeven of de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="0ac62-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="0ac62-143">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de groepen niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="0ac62-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="0ac62-144">**Als u** deze instelling inschakelt, zorgt u ervoor dat de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="0ac62-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="0ac62-145">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="0ac62-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="0ac62-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0ac62-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="0ac62-147">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="0ac62-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0ac62-148">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="0ac62-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0ac62-149">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0ac62-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="0ac62-150">Voor beeld 1: controleren of groepen aanwezig zijn</span><span class="sxs-lookup"><span data-stu-id="0ac62-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="0ac62-151">In het volgende voor beeld ziet u hoe u ervoor kunt zorgen dat twee groepen met de naam ' myGroup ' en ' myOtherGroup ' aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="0ac62-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="0ac62-152">In dit voor beeld worden Lees bare referenties gebruikt voor eenvoud.</span><span class="sxs-lookup"><span data-stu-id="0ac62-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="0ac62-153">Zie [het MOF-bestand beveiligen](../../../pull-server/secureMOF.md)voor meer informatie over het versleutelen van referenties in het MOF-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="0ac62-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
