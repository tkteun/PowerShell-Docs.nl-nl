---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxSshAuthorizedKeys-resource
description: DSC voor Linux nxSshAuthorizedKeys-resource
ms.openlocfilehash: 881e94aa583a745cdac7f01b6e445352ef4ca937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662755"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="d30f6-103">DSC voor Linux nxSshAuthorizedKeys-resource</span><span class="sxs-lookup"><span data-stu-id="d30f6-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="d30f6-104">De **nxAuthorizedKeys** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van geautoriseerde SSH-sleutels voor een opgegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d30f6-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="d30f6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d30f6-105">Syntax</span></span>

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="d30f6-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="d30f6-106">Properties</span></span>

|<span data-ttu-id="d30f6-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d30f6-107">Property</span></span> |<span data-ttu-id="d30f6-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d30f6-108">Description</span></span> |
|---|---|
|<span data-ttu-id="d30f6-109">Opmerkingaanwijzer</span><span class="sxs-lookup"><span data-stu-id="d30f6-109">KeyComment</span></span> |<span data-ttu-id="d30f6-110">Een unieke opmerking voor de sleutel.</span><span class="sxs-lookup"><span data-stu-id="d30f6-110">A unique comment for the key.</span></span> <span data-ttu-id="d30f6-111">Dit wordt gebruikt om sleutels uniek te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d30f6-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="d30f6-112">Gebruikersnaam</span><span class="sxs-lookup"><span data-stu-id="d30f6-112">Username</span></span> |<span data-ttu-id="d30f6-113">De gebruikers naam voor het beheren van geautoriseerde SSH-sleutels voor.</span><span class="sxs-lookup"><span data-stu-id="d30f6-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="d30f6-114">Als dit niet is gedefinieerd, is de standaard gebruiker **root** .</span><span class="sxs-lookup"><span data-stu-id="d30f6-114">If not defined, the default user is **root** .</span></span> |
|<span data-ttu-id="d30f6-115">Sleutel</span><span class="sxs-lookup"><span data-stu-id="d30f6-115">Key</span></span> |<span data-ttu-id="d30f6-116">De inhoud van de sleutel.</span><span class="sxs-lookup"><span data-stu-id="d30f6-116">The contents of the key.</span></span> <span data-ttu-id="d30f6-117">Dit is vereist als **dat** is ingesteld op **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="d30f6-117">This is required if **Ensure** is set to **Present** .</span></span>|

## <a name="common-properties"></a><span data-ttu-id="d30f6-118">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="d30f6-118">Common properties</span></span>

|<span data-ttu-id="d30f6-119">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d30f6-119">Property</span></span> |<span data-ttu-id="d30f6-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d30f6-120">Description</span></span> |
|---|---|
|<span data-ttu-id="d30f6-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d30f6-121">DependsOn</span></span> |<span data-ttu-id="d30f6-122">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="d30f6-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d30f6-123">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="d30f6-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d30f6-124">Zo</span><span class="sxs-lookup"><span data-stu-id="d30f6-124">Ensure</span></span> |<span data-ttu-id="d30f6-125">Hiermee wordt aangegeven of de sleutel is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d30f6-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="d30f6-126">Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de sleutel niet bestaat in het geautoriseerde sleutel bestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d30f6-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="d30f6-127">Stel deze in op **aanwezig** om te controleren of de sleutel is gedefinieerd in het geautoriseerde sleutel bestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d30f6-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="d30f6-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d30f6-128">Example</span></span>

<span data-ttu-id="d30f6-129">In het volgende voor beeld wordt een open bare SSH-sleutel gedefinieerd voor de gebruiker ' monuser '.</span><span class="sxs-lookup"><span data-stu-id="d30f6-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```
