---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxSshAuthorizedKeys Resource
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222034"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="d53aa-103">DSC voor Linux nxSshAuthorizedKeys Resource</span><span class="sxs-lookup"><span data-stu-id="d53aa-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="d53aa-104">De **nxAuthorizedKeys** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van geautoriseerd ssh-sleutels voor een opgegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d53aa-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="d53aa-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d53aa-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d53aa-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="d53aa-106">Properties</span></span>

|  <span data-ttu-id="d53aa-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d53aa-107">Property</span></span> |  <span data-ttu-id="d53aa-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d53aa-108">Description</span></span> |
|---|---|
| <span data-ttu-id="d53aa-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="d53aa-109">KeyComment</span></span>| <span data-ttu-id="d53aa-110">Een unieke Opmerking voor de sleutel.</span><span class="sxs-lookup"><span data-stu-id="d53aa-110">A unique comment for the key.</span></span> <span data-ttu-id="d53aa-111">Dit wordt gebruikt om sleutels uniek te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d53aa-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="d53aa-112">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="d53aa-112">Ensure</span></span>| <span data-ttu-id="d53aa-113">Hiermee geeft u op of de sleutel is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d53aa-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="d53aa-114">Deze eigenschap instellen op 'Ontbreekt' om te controleren of dat de sleutel bestaat niet in het gebruikersbestand geautoriseerde sleutels.</span><span class="sxs-lookup"><span data-stu-id="d53aa-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="d53aa-115">Stel deze in op 'Aanwezig' om te controleren of dat de sleutel is gedefinieerd in het geautoriseerde sleutelbestand van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d53aa-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="d53aa-116">Gebruikersnaam</span><span class="sxs-lookup"><span data-stu-id="d53aa-116">Username</span></span>| <span data-ttu-id="d53aa-117">De gebruikersnaam voor het beheren van de ssh-sleutels voor gemachtigd.</span><span class="sxs-lookup"><span data-stu-id="d53aa-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="d53aa-118">Als geen gedefinieerd, is de standaardgebruiker 'root'.</span><span class="sxs-lookup"><span data-stu-id="d53aa-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="d53aa-119">Toets</span><span class="sxs-lookup"><span data-stu-id="d53aa-119">Key</span></span>| <span data-ttu-id="d53aa-120">De inhoud van de sleutel.</span><span class="sxs-lookup"><span data-stu-id="d53aa-120">The contents of the key.</span></span> <span data-ttu-id="d53aa-121">Dit is vereist als **Zorg ervoor dat** is ingesteld op 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="d53aa-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="d53aa-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="d53aa-122">DependsOn</span></span> | <span data-ttu-id="d53aa-123">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="d53aa-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d53aa-124">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d53aa-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="d53aa-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d53aa-125">Example</span></span>

<span data-ttu-id="d53aa-126">Het volgende voorbeeld definieert een ssh geautoriseerd openbare sleutel voor de gebruiker 'monuser'.</span><span class="sxs-lookup"><span data-stu-id="d53aa-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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