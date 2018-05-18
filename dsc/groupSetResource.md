---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
description: Biedt een mechanisme voor het beheren van lokale groepen in het doelknooppunt.
title: DSC-GroupSet Resource
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="bec2c-104">DSC-GroupSet Resource</span><span class="sxs-lookup"><span data-stu-id="bec2c-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="bec2c-105">Van toepassing op: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bec2c-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="bec2c-106">De **GroupSet** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van lokale groepen in het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="bec2c-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="bec2c-107">Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [groep resource](groupResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.</span><span class="sxs-lookup"><span data-stu-id="bec2c-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="bec2c-108">Gebruik deze bron als u wilt toevoegen en/of verwijderen van dezelfde lijst met leden aan meer dan één groep, meer dan één groep te verwijderen of toevoegen van meer dan één groep met dezelfde lijst met leden.</span><span class="sxs-lookup"><span data-stu-id="bec2c-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="bec2c-109">Syntaxis ##</span><span class="sxs-lookup"><span data-stu-id="bec2c-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="bec2c-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="bec2c-110">Properties</span></span>

|  <span data-ttu-id="bec2c-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bec2c-111">Property</span></span>  |  <span data-ttu-id="bec2c-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bec2c-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="bec2c-113">Groepsnaam</span><span class="sxs-lookup"><span data-stu-id="bec2c-113">GroupName</span></span>| <span data-ttu-id="bec2c-114">De namen van de groepen waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="bec2c-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="bec2c-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="bec2c-115">MembersToExclude</span></span>| <span data-ttu-id="bec2c-116">Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groepen.</span><span class="sxs-lookup"><span data-stu-id="bec2c-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="bec2c-117">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="bec2c-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bec2c-118">Als u deze eigenschap in een configuratie instellen, gebruikt u niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bec2c-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="bec2c-119">Hierdoor wordt een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bec2c-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="bec2c-120">referentie</span><span class="sxs-lookup"><span data-stu-id="bec2c-120">Credential</span></span>| <span data-ttu-id="bec2c-121">De referenties die zijn vereist voor toegang tot externe bronnen.</span><span class="sxs-lookup"><span data-stu-id="bec2c-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="bec2c-122">**Opmerking**: dit account de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep moet hebben; anders wordt een fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="bec2c-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="bec2c-123">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="bec2c-123">Ensure</span></span>| <span data-ttu-id="bec2c-124">Hiermee wordt aangegeven of de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="bec2c-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="bec2c-125">Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groepen bestaan niet.</span><span class="sxs-lookup"><span data-stu-id="bec2c-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="bec2c-126">Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groepen bestaan.</span><span class="sxs-lookup"><span data-stu-id="bec2c-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="bec2c-127">Leden</span><span class="sxs-lookup"><span data-stu-id="bec2c-127">Members</span></span>| <span data-ttu-id="bec2c-128">Gebruik deze eigenschap het lidmaatschap van de huidige vervangt door de opgegeven leden.</span><span class="sxs-lookup"><span data-stu-id="bec2c-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="bec2c-129">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="bec2c-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bec2c-130">Als u deze eigenschap in een configuratie hebt ingesteld, geen gebruik van ofwel de **MembersToExclude** of **MembersToInclude** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bec2c-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="bec2c-131">Hierdoor wordt een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bec2c-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="bec2c-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="bec2c-132">MembersToInclude</span></span>| <span data-ttu-id="bec2c-133">Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep.</span><span class="sxs-lookup"><span data-stu-id="bec2c-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="bec2c-134">De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*.</span><span class="sxs-lookup"><span data-stu-id="bec2c-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="bec2c-135">Als u deze eigenschap in een configuratie instellen, gebruikt u niet de **leden** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="bec2c-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="bec2c-136">Hierdoor wordt een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bec2c-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="bec2c-137">dependsOn</span><span class="sxs-lookup"><span data-stu-id="bec2c-137">DependsOn</span></span> | <span data-ttu-id="bec2c-138">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="bec2c-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bec2c-139">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.</span><span class="sxs-lookup"><span data-stu-id="bec2c-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="bec2c-140">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="bec2c-140">Example 1</span></span>

<span data-ttu-id="bec2c-141">Het volgende voorbeeld laat zien hoe om ervoor te zorgen dat er twee groepen genaamd 'myGroup' en 'myOtherGroup' aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="bec2c-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

><span data-ttu-id="bec2c-142">**Opmerking:** in dit voorbeeld gebruikt de referenties van de tekst zonder opmaak voor eenvoud.</span><span class="sxs-lookup"><span data-stu-id="bec2c-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="bec2c-143">Zie voor meer informatie over het coderen van referenties in het MOF-bestand voor configuratie [beveiligen van het MOF-bestand](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="bec2c-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>