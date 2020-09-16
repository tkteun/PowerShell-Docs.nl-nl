---
title: Verwijzing kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a6deca52fa6c9e46138ae92401f58ac5dbd15852
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784364"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="7ecf5-102">Declaratie van het kenmerk Referentie</span><span class="sxs-lookup"><span data-stu-id="7ecf5-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="7ecf5-103">Het referentie kenmerk is een optioneel kenmerk dat kan worden gebruikt met referentie parameters van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , zodat een teken reeks ook als argument kan worden door gegeven aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="7ecf5-104">Wanneer dit kenmerk wordt toegevoegd aan een parameter declaratie, wordt de invoer van de teken reeks door Windows Power shell geconverteerd naar een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="7ecf5-105">De cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) gebruikt dit kenmerk bijvoorbeeld om Windows Power shell het [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object te laten genereren dat door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ecf5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ecf5-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="7ecf5-107">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7ecf5-107">Remarks</span></span>

- <span data-ttu-id="7ecf5-108">Dit kenmerk wordt doorgaans gebruikt door para meters van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , zodat een teken reeks ook als argument kan worden door gegeven aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="7ecf5-109">Wanneer een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object wordt door gegeven aan de para meter, doet Windows Power shell niets.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="7ecf5-110">Bij het maken van het [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object gebruikt Windows Power shell de huidige host om de juiste prompts voor de gebruiker weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="7ecf5-111">De standaard host geeft bijvoorbeeld een vraag naar een gebruikers naam en wacht woord wanneer dit kenmerk wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="7ecf5-112">Als er echter een aangepaste host wordt gebruikt die een andere prompt definieert, wordt de prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="7ecf5-113">Dit kenmerk wordt gebruikt met het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="7ecf5-114">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over dat kenmerk.</span><span class="sxs-lookup"><span data-stu-id="7ecf5-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="7ecf5-115">Het referentie kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="7ecf5-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ecf5-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7ecf5-116">See Also</span></span>

[<span data-ttu-id="7ecf5-117">Parameteraliassen</span><span class="sxs-lookup"><span data-stu-id="7ecf5-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="7ecf5-118">Declaratie van het kenmerk Parameter</span><span class="sxs-lookup"><span data-stu-id="7ecf5-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="7ecf5-119">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="7ecf5-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
