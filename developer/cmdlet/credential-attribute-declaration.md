---
title: Referentie-kenmerkdeclaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059249"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="bfd75-102">Declaratie van het kenmerk Referentie</span><span class="sxs-lookup"><span data-stu-id="bfd75-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="bfd75-103">De referentie-kenmerk is een optioneel kenmerk die kan worden gebruikt met de parameters van het type referentie [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) zodat een tekenreeks kan ook als een argument worden doorgegeven aan de parameter.</span><span class="sxs-lookup"><span data-stu-id="bfd75-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="bfd75-104">Wanneer dit kenmerk wordt toegevoegd aan een parameterdeclaratie, Windows PowerShell converteert de tekenreeksinvoer van de in een [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span><span class="sxs-lookup"><span data-stu-id="bfd75-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="bfd75-105">Bijvoorbeeld, de [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet maakt gebruik van dit kenmerk moet Windows PowerShell, genereren de [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object dat wordt geretourneerd door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bfd75-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfd75-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bfd75-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="bfd75-107">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bfd75-107">Remarks</span></span>

- <span data-ttu-id="bfd75-108">Meestal dit kenmerk wordt gebruikt door de parameters van het type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) zodat een tekenreeks kan ook als een argument worden doorgegeven aan de parameter.</span><span class="sxs-lookup"><span data-stu-id="bfd75-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="bfd75-109">Wanneer een [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object doorgegeven aan de parameter, de Windows PowerShell, gebeurt er niets.</span><span class="sxs-lookup"><span data-stu-id="bfd75-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="bfd75-110">Bij het maken van de [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object, Windows PowerShell maakt gebruik van de huidige Host om de juiste aanwijzingen voor de gebruiker weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bfd75-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="bfd75-111">Bijvoorbeeld, de standaard Host een prompt weergegeven voor een gebruikersnaam en wachtwoord wanneer dit kenmerk wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bfd75-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="bfd75-112">Als een aangepaste host wordt gebruikt die een verschillende prompt definieert en deze prompt zou worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bfd75-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="bfd75-113">Dit kenmerk wordt gebruikt met de Parameter-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="bfd75-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="bfd75-114">Zie voor meer informatie over dat kenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bfd75-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="bfd75-115">De referentie-kenmerk wordt gedefinieerd door de [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="bfd75-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfd75-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bfd75-116">See Also</span></span>

[<span data-ttu-id="bfd75-117">Parameter Aliases</span><span class="sxs-lookup"><span data-stu-id="bfd75-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="bfd75-118">Kenmerk parameterdeclaratie</span><span class="sxs-lookup"><span data-stu-id="bfd75-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="bfd75-119">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bfd75-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
