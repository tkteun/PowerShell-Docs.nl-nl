---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250845"
---
# <span data-ttu-id="3cd80-103">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3cd80-103">Set-LocalUser</span></span>

## <span data-ttu-id="3cd80-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3cd80-104">SYNOPSIS</span></span>
<span data-ttu-id="3cd80-105">Hiermee wijzigt u een lokaal gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="3cd80-105">Modifies a local user account.</span></span>

## <span data-ttu-id="3cd80-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3cd80-106">SYNTAX</span></span>

### <span data-ttu-id="3cd80-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="3cd80-107">Name (Default)</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3cd80-108">Input object</span><span class="sxs-lookup"><span data-stu-id="3cd80-108">InputObject</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3cd80-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="3cd80-109">SecurityIdentifier</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3cd80-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3cd80-110">DESCRIPTION</span></span>
<span data-ttu-id="3cd80-111">De cmdlet **set-lokalegebruiker** wijzigt een lokale gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="3cd80-111">The **Set-LocalUser** cmdlet modifies a local user account.</span></span>
<span data-ttu-id="3cd80-112">Met deze cmdlet kan het wacht woord van een lokaal gebruikers account opnieuw worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3cd80-112">This cmdlet can reset the password of a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="3cd80-113">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="3cd80-113">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="3cd80-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3cd80-114">EXAMPLES</span></span>

### <span data-ttu-id="3cd80-115">Voor beeld 1: een beschrijving van een gebruikers account wijzigen</span><span class="sxs-lookup"><span data-stu-id="3cd80-115">Example 1: Change a description of a user account</span></span>

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

<span data-ttu-id="3cd80-116">Met deze opdracht wordt de beschrijving van een gebruikers account met de naam Admin07 gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3cd80-116">This command changes the description of a user account named Admin07.</span></span>

### <span data-ttu-id="3cd80-117">Voor beeld 2: het wacht woord voor een account wijzigen</span><span class="sxs-lookup"><span data-stu-id="3cd80-117">Example 2: Change the password on an account</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

<span data-ttu-id="3cd80-118">Met de eerste opdracht wordt u gevraagd om een wacht woord met behulp van de cmdlet Read-Host.</span><span class="sxs-lookup"><span data-stu-id="3cd80-118">The first command prompts you for a password by using the Read-Host cmdlet.</span></span>
<span data-ttu-id="3cd80-119">De opdracht slaat het wacht woord op als een beveiligde teken reeks in de variabele $Password.</span><span class="sxs-lookup"><span data-stu-id="3cd80-119">The command stores the password as a secure string in the $Password variable.</span></span>

<span data-ttu-id="3cd80-120">Met de tweede opdracht wordt een gebruikers account met de naam User02 opgehaald door **Get-lokalegebruiker** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3cd80-120">The second command gets a user account named User02 by using **Get-LocalUser**.</span></span>
<span data-ttu-id="3cd80-121">De opdracht slaat het account op in de variabele $UserAccount.</span><span class="sxs-lookup"><span data-stu-id="3cd80-121">The command stores the account in the $UserAccount variable.</span></span>

<span data-ttu-id="3cd80-122">Met de derde opdracht wordt het nieuwe wacht woord ingesteld voor het gebruikers account dat is opgeslagen in $UserAccount.</span><span class="sxs-lookup"><span data-stu-id="3cd80-122">The third command sets the new password on the user account stored in $UserAccount.</span></span>

## <span data-ttu-id="3cd80-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3cd80-123">PARAMETERS</span></span>

### <span data-ttu-id="3cd80-124">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="3cd80-124">-AccountExpires</span></span>
<span data-ttu-id="3cd80-125">Hiermee geeft u op wanneer het gebruikers account verloopt.</span><span class="sxs-lookup"><span data-stu-id="3cd80-125">Specifies when the user account expires.</span></span>
<span data-ttu-id="3cd80-126">Als u een **DateTime** -object wilt ophalen, gebruikt u de cmdlet Get-Date.</span><span class="sxs-lookup"><span data-stu-id="3cd80-126">To obtain a **DateTime** object, use the Get-Date cmdlet.</span></span>

<span data-ttu-id="3cd80-127">Als u het account niet wilt laten verlopen, geeft u de para meter *AccountNeverExpires* op.</span><span class="sxs-lookup"><span data-stu-id="3cd80-127">If you do not want the account to expire, specify the *AccountNeverExpires* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-128">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="3cd80-128">-AccountNeverExpires</span></span>
<span data-ttu-id="3cd80-129">Geeft aan dat het account niet verloopt.</span><span class="sxs-lookup"><span data-stu-id="3cd80-129">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-130">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3cd80-130">-Description</span></span>
<span data-ttu-id="3cd80-131">Hiermee geeft u een opmerking op voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="3cd80-131">Specifies a comment for the user account.</span></span>
<span data-ttu-id="3cd80-132">De maximale lengte is 48 tekens.</span><span class="sxs-lookup"><span data-stu-id="3cd80-132">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-133">-FullName</span><span class="sxs-lookup"><span data-stu-id="3cd80-133">-FullName</span></span>
<span data-ttu-id="3cd80-134">Hiermee geeft u de volledige naam voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="3cd80-134">Specifies the full name for the user account.</span></span>
<span data-ttu-id="3cd80-135">De volledige naam wijkt af van de gebruikers naam van het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="3cd80-135">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-136">-Input object</span><span class="sxs-lookup"><span data-stu-id="3cd80-136">-InputObject</span></span>
<span data-ttu-id="3cd80-137">Hiermee geeft u het gebruikers account op dat met deze cmdlet wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3cd80-137">Specifies the user account that this cmdlet changes.</span></span>
<span data-ttu-id="3cd80-138">Gebruik de cmdlet Get-LocalUser om een gebruikers account te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="3cd80-138">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-139">-Name</span><span class="sxs-lookup"><span data-stu-id="3cd80-139">-Name</span></span>
<span data-ttu-id="3cd80-140">Hiermee geeft u de naam van het gebruikers account dat door deze cmdlet wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3cd80-140">Specifies the name of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-141">-Password</span><span class="sxs-lookup"><span data-stu-id="3cd80-141">-Password</span></span>
<span data-ttu-id="3cd80-142">Hiermee geeft u een wacht woord voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="3cd80-142">Specifies a password for the user account.</span></span>
<span data-ttu-id="3cd80-143">Als het gebruikers account is verbonden met een Microsoft-account, stelt u geen wacht woord in.</span><span class="sxs-lookup"><span data-stu-id="3cd80-143">If the user account is connected to a Microsoft account, do not set a password.</span></span>

<span data-ttu-id="3cd80-144">U kunt `Read-Host -GetCredential` , Get-Credential of ConvertTo-SecureString gebruiken om een **SecureString** -object voor het wacht woord te maken.</span><span class="sxs-lookup"><span data-stu-id="3cd80-144">You can use `Read-Host -GetCredential`, Get-Credential, or ConvertTo-SecureString to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="3cd80-145">Als u de para meters *wacht woord* en niet- *wacht woord* weglaat, **stelt u-lokalegebruiker** in om het wacht woord van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3cd80-145">If you omit the *Password* and *NoPassword* parameters, **Set-LocalUser** prompts you for the user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-146">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="3cd80-146">-PasswordNeverExpires</span></span>
<span data-ttu-id="3cd80-147">Hiermee wordt aangegeven of het wacht woord is verlopen.</span><span class="sxs-lookup"><span data-stu-id="3cd80-147">Indicates whether the password expires.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-148">-SID</span><span class="sxs-lookup"><span data-stu-id="3cd80-148">-SID</span></span>
<span data-ttu-id="3cd80-149">Hiermee geeft u de beveiligings-ID (SID) van het gebruikers account dat door deze cmdlet wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3cd80-149">Specifies the security ID (SID) of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-150">-UserMayChangePassword</span><span class="sxs-lookup"><span data-stu-id="3cd80-150">-UserMayChangePassword</span></span>
<span data-ttu-id="3cd80-151">Geeft aan dat de gebruiker het wacht woord voor het gebruikers account kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="3cd80-151">Indicates that the user can change the password on the user account.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3cd80-152">-Confirm</span></span>
<span data-ttu-id="3cd80-153">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3cd80-153">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3cd80-154">-WhatIf</span></span>
<span data-ttu-id="3cd80-155">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3cd80-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3cd80-156">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3cd80-156">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd80-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3cd80-157">CommonParameters</span></span>
<span data-ttu-id="3cd80-158">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3cd80-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3cd80-159">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3cd80-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3cd80-160">INVOER</span><span class="sxs-lookup"><span data-stu-id="3cd80-160">INPUTS</span></span>

### <span data-ttu-id="3cd80-161">System. Management. Automation. SecurityAccountsManager. Lokalegebruiker, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3cd80-161">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="3cd80-162">U kunt een lokale gebruiker, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3cd80-162">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="3cd80-163">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3cd80-163">OUTPUTS</span></span>

### <span data-ttu-id="3cd80-164">Geen</span><span class="sxs-lookup"><span data-stu-id="3cd80-164">None</span></span>
<span data-ttu-id="3cd80-165">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3cd80-165">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3cd80-166">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3cd80-166">NOTES</span></span>

* <span data-ttu-id="3cd80-167">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="3cd80-167">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="3cd80-168">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="3cd80-168">The possible sources are as follows:</span></span>

- <span data-ttu-id="3cd80-169">Lokaal</span><span class="sxs-lookup"><span data-stu-id="3cd80-169">Local</span></span>
- <span data-ttu-id="3cd80-170">Active Directory</span><span class="sxs-lookup"><span data-stu-id="3cd80-170">Active Directory</span></span>
- <span data-ttu-id="3cd80-171">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="3cd80-171">Azure Active Directory group</span></span>
- <span data-ttu-id="3cd80-172">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="3cd80-172">Microsoft Account</span></span>

<span data-ttu-id="3cd80-173">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="3cd80-173">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="3cd80-174">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="3cd80-174">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="3cd80-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3cd80-175">RELATED LINKS</span></span>

[<span data-ttu-id="3cd80-176">Disable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="3cd80-176">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="3cd80-177">Enable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="3cd80-177">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="3cd80-178">Get-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="3cd80-178">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="3cd80-179">New-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="3cd80-179">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="3cd80-180">Remove-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="3cd80-180">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="3cd80-181">Naam wijzigen-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="3cd80-181">Rename-LocalUser</span></span>](Rename-LocalUser.md)
