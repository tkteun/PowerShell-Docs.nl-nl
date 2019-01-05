---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
description: Biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.
title: DSC GroupSet-Resource
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048300"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="6f3e0-104">DSC GroupSet-Resource</span><span class="sxs-lookup"><span data-stu-id="6f3e0-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="6f3e0-105">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6f3e0-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6f3e0-106">De **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="6f3e0-107">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [groep resource](groupResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="6f3e0-108">Gebruik deze resource als u wilt toevoegen en/of verwijderen van de dezelfde lijst met leden aan meer dan één groep, meer dan één groep te verwijderen of toevoegen van meer dan één groep met dezelfde lijst met leden.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f3e0-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6f3e0-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6f3e0-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6f3e0-110">Properties</span></span>

|  <span data-ttu-id="6f3e0-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6f3e0-111">Property</span></span>  |  <span data-ttu-id="6f3e0-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6f3e0-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="6f3e0-113">Groepsnaam</span><span class="sxs-lookup"><span data-stu-id="6f3e0-113">GroupName</span></span>| <span data-ttu-id="6f3e0-114">De namen van de groepen waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="6f3e0-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="6f3e0-115">MembersToExclude</span></span>| <span data-ttu-id="6f3e0-116">Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groepen.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="6f3e0-117">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="6f3e0-118">Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="6f3e0-119">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="6f3e0-120">Referentie</span><span class="sxs-lookup"><span data-stu-id="6f3e0-120">Credential</span></span>| <span data-ttu-id="6f3e0-121">De referenties die zijn vereist voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="6f3e0-122">**Houd er rekening mee**: Dit account moet hebben tot de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep. anders wordt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="6f3e0-123">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="6f3e0-123">Ensure</span></span>| <span data-ttu-id="6f3e0-124">Geeft aan of de groepen zijn.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="6f3e0-125">Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groepen niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="6f3e0-126">Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="6f3e0-127">Leden</span><span class="sxs-lookup"><span data-stu-id="6f3e0-127">Members</span></span>| <span data-ttu-id="6f3e0-128">Gebruik deze eigenschap om het lidmaatschap van de huidige vervangen door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="6f3e0-129">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="6f3e0-130">Als u deze eigenschap in een configuratie hebt ingesteld, mag niet een gebruiken de **MembersToExclude** of **MembersToInclude** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="6f3e0-131">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="6f3e0-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="6f3e0-132">MembersToInclude</span></span>| <span data-ttu-id="6f3e0-133">Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="6f3e0-134">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="6f3e0-135">Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="6f3e0-136">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="6f3e0-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6f3e0-137">DependsOn</span></span> | <span data-ttu-id="6f3e0-138">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6f3e0-139">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="6f3e0-140">Voorbeeld 1: Ervoor zorgen dat groepen zijn aanwezig</span><span class="sxs-lookup"><span data-stu-id="6f3e0-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="6f3e0-141">Het volgende voorbeeld ziet hoe u om ervoor te zorgen dat er twee groepen met de naam "myGroup" en "myOtherGroup" aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="6f3e0-142">In dit voorbeeld maakt gebruik van referenties zonder gecodeerde tekst voor het gemak.</span><span class="sxs-lookup"><span data-stu-id="6f3e0-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="6f3e0-143">Zie voor meer informatie over het versleutelen van de referenties in het MOF-configuratiebestand [beveiligen van het MOF-bestand](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="6f3e0-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
