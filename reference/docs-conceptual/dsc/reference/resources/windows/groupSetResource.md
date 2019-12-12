---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
description: Biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.
title: DSC-groeps resource
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941402"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="524dd-104">DSC-groeps resource</span><span class="sxs-lookup"><span data-stu-id="524dd-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="524dd-105">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="524dd-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="524dd-106">De **groeps** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="524dd-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="524dd-107">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [groeps bron](groupResource.md) aanroept voor elke groep die is opgegeven in de para meter `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="524dd-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="524dd-108">Gebruik deze resource als u dezelfde lijst met leden wilt toevoegen aan of verwijderen uit meer dan één groep, als u meer dan één groep wilt verwijderen of meer dan één groep met dezelfde lijst met leden wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="524dd-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="524dd-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="524dd-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="524dd-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="524dd-110">Properties</span></span>

|<span data-ttu-id="524dd-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="524dd-111">Property</span></span> |<span data-ttu-id="524dd-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="524dd-112">Description</span></span> |
|---|---|
|<span data-ttu-id="524dd-113">groupName</span><span class="sxs-lookup"><span data-stu-id="524dd-113">GroupName</span></span> |<span data-ttu-id="524dd-114">De namen van de groepen waarvoor u een specifieke status wilt controleren.</span><span class="sxs-lookup"><span data-stu-id="524dd-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="524dd-115">Leden</span><span class="sxs-lookup"><span data-stu-id="524dd-115">Members</span></span> |<span data-ttu-id="524dd-116">Gebruik deze eigenschap om het huidige groepslid maatschap te vervangen door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="524dd-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="524dd-117">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="524dd-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="524dd-118">Als u deze eigenschap in een configuratie instelt, moet u de eigenschap **MembersToExclude** of **MembersToInclude** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="524dd-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="524dd-119">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="524dd-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="524dd-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="524dd-120">Description</span></span> |<span data-ttu-id="524dd-121">De beschrijving van de groep.</span><span class="sxs-lookup"><span data-stu-id="524dd-121">The description of the group.</span></span> |
|<span data-ttu-id="524dd-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="524dd-122">MembersToInclude</span></span> |<span data-ttu-id="524dd-123">Gebruik deze eigenschap om leden toe te voegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="524dd-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="524dd-124">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="524dd-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="524dd-125">Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="524dd-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="524dd-126">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="524dd-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="524dd-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="524dd-127">MembersToExclude</span></span> |<span data-ttu-id="524dd-128">Gebruik deze eigenschap om leden te verwijderen uit het bestaande lidmaatschap van de groepen.</span><span class="sxs-lookup"><span data-stu-id="524dd-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="524dd-129">De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName`.</span><span class="sxs-lookup"><span data-stu-id="524dd-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="524dd-130">Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="524dd-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="524dd-131">Als u dit doet, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="524dd-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="524dd-132">Referentie</span><span class="sxs-lookup"><span data-stu-id="524dd-132">Credential</span></span> |<span data-ttu-id="524dd-133">De referenties die nodig zijn voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="524dd-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="524dd-134">Dit account moet over de juiste Active Directory machtigingen beschikken om alle niet-lokale accounts aan de groep toe te voegen. anders treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="524dd-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="524dd-135">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="524dd-135">Common properties</span></span>

|<span data-ttu-id="524dd-136">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="524dd-136">Property</span></span> |<span data-ttu-id="524dd-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="524dd-137">Description</span></span> |
|---|---|
|<span data-ttu-id="524dd-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="524dd-138">DependsOn</span></span> |<span data-ttu-id="524dd-139">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="524dd-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="524dd-140">Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="524dd-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="524dd-141">Zo</span><span class="sxs-lookup"><span data-stu-id="524dd-141">Ensure</span></span> |<span data-ttu-id="524dd-142">Hiermee wordt aangegeven of de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="524dd-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="524dd-143">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de groepen niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="524dd-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="524dd-144">**Als u** deze instelling inschakelt, zorgt u ervoor dat de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="524dd-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="524dd-145">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="524dd-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="524dd-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="524dd-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="524dd-147">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="524dd-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="524dd-148">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="524dd-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="524dd-149">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="524dd-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="524dd-150">Voor beeld 1: controleren of groepen aanwezig zijn</span><span class="sxs-lookup"><span data-stu-id="524dd-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="524dd-151">In het volgende voor beeld ziet u hoe u ervoor kunt zorgen dat twee groepen met de naam ' myGroup ' en ' myOtherGroup ' aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="524dd-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="524dd-152">In dit voor beeld worden Lees bare referenties gebruikt voor eenvoud.</span><span class="sxs-lookup"><span data-stu-id="524dd-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="524dd-153">Zie [het MOF-bestand beveiligen](../../../pull-server/secureMOF.md)voor meer informatie over het versleutelen van referenties in het MOF-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="524dd-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>