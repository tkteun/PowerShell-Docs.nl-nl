---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
description: Biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.
title: DSC GroupSet-Resource
ms.openlocfilehash: 6fa8e9637da896848e859dc60a42add12e973b34
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226114"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="ae12a-104">DSC GroupSet-Resource</span><span class="sxs-lookup"><span data-stu-id="ae12a-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="ae12a-105">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ae12a-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ae12a-106">De **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="ae12a-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="ae12a-107">Deze resource is een [samengestelde resource](authoringResourceComposite.md) die roept de [groep resource](groupResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.</span><span class="sxs-lookup"><span data-stu-id="ae12a-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="ae12a-108">Gebruik deze resource als u wilt toevoegen en/of verwijderen van de dezelfde lijst met leden aan meer dan één groep, meer dan één groep te verwijderen of toevoegen van meer dan één groep met dezelfde lijst met leden.</span><span class="sxs-lookup"><span data-stu-id="ae12a-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae12a-109">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ae12a-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ae12a-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ae12a-110">Properties</span></span>

|  <span data-ttu-id="ae12a-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="ae12a-111">Property</span></span>  |  <span data-ttu-id="ae12a-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ae12a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="ae12a-113">Groepsnaam</span><span class="sxs-lookup"><span data-stu-id="ae12a-113">GroupName</span></span>| <span data-ttu-id="ae12a-114">De namen van de groepen waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="ae12a-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="ae12a-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="ae12a-115">MembersToExclude</span></span>| <span data-ttu-id="ae12a-116">Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groepen.</span><span class="sxs-lookup"><span data-stu-id="ae12a-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="ae12a-117">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="ae12a-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="ae12a-118">Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="ae12a-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="ae12a-119">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ae12a-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="ae12a-120">Referentie</span><span class="sxs-lookup"><span data-stu-id="ae12a-120">Credential</span></span>| <span data-ttu-id="ae12a-121">De referenties die zijn vereist voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="ae12a-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="ae12a-122">**Houd er rekening mee**: dit account moet de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep hebben; anders wordt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="ae12a-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="ae12a-123">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="ae12a-123">Ensure</span></span>| <span data-ttu-id="ae12a-124">Geeft aan of de groepen zijn.</span><span class="sxs-lookup"><span data-stu-id="ae12a-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="ae12a-125">Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groepen niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="ae12a-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="ae12a-126">Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="ae12a-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="ae12a-127">Leden</span><span class="sxs-lookup"><span data-stu-id="ae12a-127">Members</span></span>| <span data-ttu-id="ae12a-128">Gebruik deze eigenschap om het lidmaatschap van de huidige vervangen door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="ae12a-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="ae12a-129">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="ae12a-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="ae12a-130">Als u deze eigenschap in een configuratie hebt ingesteld, mag niet een gebruiken de **MembersToExclude** of **MembersToInclude** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="ae12a-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="ae12a-131">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ae12a-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="ae12a-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="ae12a-132">MembersToInclude</span></span>| <span data-ttu-id="ae12a-133">Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="ae12a-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="ae12a-134">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="ae12a-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="ae12a-135">Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="ae12a-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="ae12a-136">In dat geval wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ae12a-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="ae12a-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ae12a-137">DependsOn</span></span> | <span data-ttu-id="ae12a-138">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="ae12a-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ae12a-139">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="ae12a-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="ae12a-140">Voorbeeld 1: Ervoor zorgen dat groepen aanwezig zijn</span><span class="sxs-lookup"><span data-stu-id="ae12a-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="ae12a-141">Het volgende voorbeeld ziet hoe u om ervoor te zorgen dat er twee groepen met de naam "myGroup" en "myOtherGroup" aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="ae12a-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="ae12a-142">In dit voorbeeld maakt gebruik van referenties zonder gecodeerde tekst voor het gemak.</span><span class="sxs-lookup"><span data-stu-id="ae12a-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="ae12a-143">Zie voor meer informatie over het versleutelen van de referenties in het MOF-configuratiebestand [beveiligen van het MOF-bestand](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="ae12a-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>
