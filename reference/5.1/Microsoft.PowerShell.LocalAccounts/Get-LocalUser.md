---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249923"
---
# <span data-ttu-id="30c9e-103">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c9e-103">Get-LocalUser</span></span>

## <span data-ttu-id="30c9e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="30c9e-104">SYNOPSIS</span></span>
<span data-ttu-id="30c9e-105">Hiermee haalt u lokale gebruikers accounts op.</span><span class="sxs-lookup"><span data-stu-id="30c9e-105">Gets local user accounts.</span></span>

## <span data-ttu-id="30c9e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="30c9e-106">SYNTAX</span></span>

### <span data-ttu-id="30c9e-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="30c9e-107">Default (Default)</span></span>

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="30c9e-108">Behoren</span><span class="sxs-lookup"><span data-stu-id="30c9e-108">SecurityIdentifier</span></span>

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="30c9e-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="30c9e-109">DESCRIPTION</span></span>

<span data-ttu-id="30c9e-110">De `Get-LocalUser` cmdlet haalt lokale gebruikers accounts op.</span><span class="sxs-lookup"><span data-stu-id="30c9e-110">The `Get-LocalUser` cmdlet gets local user accounts.</span></span> <span data-ttu-id="30c9e-111">Deze cmdlet krijgt standaard ingebouwde gebruikers accounts, lokale gebruikers accounts die u hebt gemaakt en lokale accounts die u hebt verbonden met micro soft-accounts.</span><span class="sxs-lookup"><span data-stu-id="30c9e-111">This cmdlet gets default built-in user accounts, local user accounts that you created, and local accounts that you connected to Microsoft accounts.</span></span>

> [!NOTE]
> <span data-ttu-id="30c9e-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="30c9e-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="30c9e-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="30c9e-113">EXAMPLES</span></span>

### <span data-ttu-id="30c9e-114">Voor beeld 1: een account ophalen met behulp van de naam</span><span class="sxs-lookup"><span data-stu-id="30c9e-114">Example 1: Get an account by using its name</span></span>

<span data-ttu-id="30c9e-115">In dit voor beeld wordt een gebruikers account met de naam AdminContoso02 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30c9e-115">This example gets a user account named AdminContoso02.</span></span>

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### <span data-ttu-id="30c9e-116">Voor beeld 2: een account ophalen dat is verbonden met een Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="30c9e-116">Example 2: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="30c9e-117">In dit voor beeld wordt een gebruikers account opgehaald dat is verbonden met een Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="30c9e-117">This example gets a user account that is connected to a Microsoft account.</span></span> <span data-ttu-id="30c9e-118">In dit voor beeld wordt een tijdelijke aanduiding voor de gebruikers naam van een account op Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="30c9e-118">This example uses a placeholder value for the username of an account at Outlook.com.</span></span>

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### <span data-ttu-id="30c9e-119">Voor beeld 3: een account ophalen dat is verbonden met een Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="30c9e-119">Example 3: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="30c9e-120">In dit voor beeld wordt een lokale gebruikers account met de opgegeven SID opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30c9e-120">This example gets a local user account that has the specified SID.</span></span>

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## <span data-ttu-id="30c9e-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30c9e-121">PARAMETERS</span></span>

### <span data-ttu-id="30c9e-122">-Name</span><span class="sxs-lookup"><span data-stu-id="30c9e-122">-Name</span></span>

<span data-ttu-id="30c9e-123">Hiermee geeft u een matrix met namen van gebruikers accounts op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30c9e-123">Specifies an array of names of user accounts that this cmdlet gets.</span></span> <span data-ttu-id="30c9e-124">U kunt het Joker teken gebruiken.</span><span class="sxs-lookup"><span data-stu-id="30c9e-124">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="30c9e-125">-SID</span><span class="sxs-lookup"><span data-stu-id="30c9e-125">-SID</span></span>

<span data-ttu-id="30c9e-126">Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van gebruikers accounts die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30c9e-126">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="30c9e-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30c9e-127">CommonParameters</span></span>

<span data-ttu-id="30c9e-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30c9e-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30c9e-129">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30c9e-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30c9e-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="30c9e-130">INPUTS</span></span>

### <span data-ttu-id="30c9e-131">System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="30c9e-131">System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="30c9e-132">U kunt een teken reeks of SID door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30c9e-132">You can pipe a string or SID to this cmdlet.</span></span>

## <span data-ttu-id="30c9e-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="30c9e-133">OUTPUTS</span></span>

### <span data-ttu-id="30c9e-134">System. Management. Automation. SecurityAccountsManager. Lokalegebruiker []</span><span class="sxs-lookup"><span data-stu-id="30c9e-134">System.Management.Automation.SecurityAccountsManager.LocalUser[]</span></span>

<span data-ttu-id="30c9e-135">Met deze cmdlet worden lokale gebruikers accounts geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="30c9e-135">This cmdlet returns local user accounts.</span></span>

## <span data-ttu-id="30c9e-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="30c9e-136">NOTES</span></span>

<span data-ttu-id="30c9e-137">De eigenschap **PrincipalSource** in de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** beschrijft de bron van het object.</span><span class="sxs-lookup"><span data-stu-id="30c9e-137">The **PrincipalSource** property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects describes the source of the object.</span></span> <span data-ttu-id="30c9e-138">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="30c9e-138">The possible sources are as follows:</span></span>

- <span data-ttu-id="30c9e-139">Lokaal</span><span class="sxs-lookup"><span data-stu-id="30c9e-139">Local</span></span>
- <span data-ttu-id="30c9e-140">Active Directory</span><span class="sxs-lookup"><span data-stu-id="30c9e-140">Active Directory</span></span>
- <span data-ttu-id="30c9e-141">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="30c9e-141">Azure Active Directory group</span></span>
- <span data-ttu-id="30c9e-142">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="30c9e-142">Microsoft Account</span></span>

<span data-ttu-id="30c9e-143">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="30c9e-143">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="30c9e-144">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="30c9e-144">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="30c9e-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="30c9e-145">RELATED LINKS</span></span>

[<span data-ttu-id="30c9e-146">Disable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="30c9e-146">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="30c9e-147">Enable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="30c9e-147">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="30c9e-148">New-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="30c9e-148">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="30c9e-149">Remove-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="30c9e-149">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="30c9e-150">Naam wijzigen-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="30c9e-150">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="30c9e-151">Set-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="30c9e-151">Set-LocalUser</span></span>](Set-LocalUser.md)