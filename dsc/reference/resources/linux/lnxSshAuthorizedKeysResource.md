---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxSshAuthorizedKeys-Resource
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048336"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="be396-103">DSC voor Linux nxSshAuthorizedKeys-Resource</span><span class="sxs-lookup"><span data-stu-id="be396-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="be396-104">De **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van geautoriseerde ssh-sleutels voor een opgegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="be396-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="be396-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="be396-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="be396-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="be396-106">Properties</span></span>

|  <span data-ttu-id="be396-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="be396-107">Property</span></span> |  <span data-ttu-id="be396-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="be396-108">Description</span></span> |
|---|---|
| <span data-ttu-id="be396-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="be396-109">KeyComment</span></span>| <span data-ttu-id="be396-110">Een unieke Opmerking voor de sleutel.</span><span class="sxs-lookup"><span data-stu-id="be396-110">A unique comment for the key.</span></span> <span data-ttu-id="be396-111">Dit wordt gebruikt voor het aanduiden van sleutels.</span><span class="sxs-lookup"><span data-stu-id="be396-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="be396-112">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="be396-112">Ensure</span></span>| <span data-ttu-id="be396-113">Hiermee geeft u op of de sleutel is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="be396-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="be396-114">Deze eigenschap instellen op 'Ontbreekt' om te controleren of dat de sleutel bestaat niet in het geautoriseerde sleutelsbestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="be396-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="be396-115">Stel deze in op 'Aanwezig' om te controleren of dat de sleutel is gedefinieerd in de gemachtigde sleutelbestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="be396-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="be396-116">Gebruikersnaam</span><span class="sxs-lookup"><span data-stu-id="be396-116">Username</span></span>| <span data-ttu-id="be396-117">De gebruikersnaam voor het beheren van ssh-sleutels voor gemachtigd.</span><span class="sxs-lookup"><span data-stu-id="be396-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="be396-118">Als niet is gedefinieerd, is de standaardwaarde 'root'.</span><span class="sxs-lookup"><span data-stu-id="be396-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="be396-119">Toets</span><span class="sxs-lookup"><span data-stu-id="be396-119">Key</span></span>| <span data-ttu-id="be396-120">De inhoud van de sleutel.</span><span class="sxs-lookup"><span data-stu-id="be396-120">The contents of the key.</span></span> <span data-ttu-id="be396-121">Dit is vereist als **Zorg ervoor dat** is ingesteld op 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="be396-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="be396-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="be396-122">DependsOn</span></span> | <span data-ttu-id="be396-123">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="be396-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="be396-124">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="be396-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="be396-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="be396-125">Example</span></span>

<span data-ttu-id="be396-126">Het volgende voorbeeld definieert een openbare ssh gemachtigd voor de gebruiker 'monuser'.</span><span class="sxs-lookup"><span data-stu-id="be396-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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