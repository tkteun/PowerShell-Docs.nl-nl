---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxSshAuthorizedKeys-Resource
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077690"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="a005a-103">DSC voor Linux nxSshAuthorizedKeys-Resource</span><span class="sxs-lookup"><span data-stu-id="a005a-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="a005a-104">De **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van geautoriseerde ssh-sleutels voor een opgegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a005a-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="a005a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a005a-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="a005a-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a005a-106">Properties</span></span>

|  <span data-ttu-id="a005a-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="a005a-107">Property</span></span> |  <span data-ttu-id="a005a-108">Description</span><span class="sxs-lookup"><span data-stu-id="a005a-108">Description</span></span> |
|---|---|
| <span data-ttu-id="a005a-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="a005a-109">KeyComment</span></span>| <span data-ttu-id="a005a-110">Een unieke Opmerking voor de sleutel.</span><span class="sxs-lookup"><span data-stu-id="a005a-110">A unique comment for the key.</span></span> <span data-ttu-id="a005a-111">Dit wordt gebruikt voor het aanduiden van sleutels.</span><span class="sxs-lookup"><span data-stu-id="a005a-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="a005a-112">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="a005a-112">Ensure</span></span>| <span data-ttu-id="a005a-113">Hiermee geeft u op of de sleutel is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a005a-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="a005a-114">Deze eigenschap instellen op 'Ontbreekt' om te controleren of dat de sleutel bestaat niet in het geautoriseerde sleutelsbestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a005a-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="a005a-115">Stel deze in op 'Aanwezig' om te controleren of dat de sleutel is gedefinieerd in de gemachtigde sleutelbestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a005a-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="a005a-116">Gebruikersnaam</span><span class="sxs-lookup"><span data-stu-id="a005a-116">Username</span></span>| <span data-ttu-id="a005a-117">De gebruikersnaam voor het beheren van ssh-sleutels voor gemachtigd.</span><span class="sxs-lookup"><span data-stu-id="a005a-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="a005a-118">Als niet is gedefinieerd, is de standaardwaarde 'root'.</span><span class="sxs-lookup"><span data-stu-id="a005a-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="a005a-119">Sleutel</span><span class="sxs-lookup"><span data-stu-id="a005a-119">Key</span></span>| <span data-ttu-id="a005a-120">De inhoud van de sleutel.</span><span class="sxs-lookup"><span data-stu-id="a005a-120">The contents of the key.</span></span> <span data-ttu-id="a005a-121">Dit is vereist als **Zorg ervoor dat** is ingesteld op 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="a005a-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="a005a-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a005a-122">DependsOn</span></span> | <span data-ttu-id="a005a-123">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="a005a-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a005a-124">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a005a-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a005a-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a005a-125">Example</span></span>

<span data-ttu-id="a005a-126">Het volgende voorbeeld definieert een openbare ssh gemachtigd voor de gebruiker 'monuser'.</span><span class="sxs-lookup"><span data-stu-id="a005a-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```