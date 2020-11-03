---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250611"
---
# <span data-ttu-id="68747-103">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="68747-103">New-LocalUser</span></span>

## <span data-ttu-id="68747-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="68747-104">SYNOPSIS</span></span>

<span data-ttu-id="68747-105">Hiermee maakt u een lokaal gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-105">Creates a local user account.</span></span>

## <span data-ttu-id="68747-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="68747-106">SYNTAX</span></span>

### <span data-ttu-id="68747-107">Wacht woord (standaard)</span><span class="sxs-lookup"><span data-stu-id="68747-107">Password (Default)</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="68747-108">Geen wacht woord</span><span class="sxs-lookup"><span data-stu-id="68747-108">NoPassword</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="68747-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="68747-109">DESCRIPTION</span></span>

<span data-ttu-id="68747-110">Met de `New-LocalUser` cmdlet maakt u een lokaal gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-110">The `New-LocalUser` cmdlet creates a local user account.</span></span> <span data-ttu-id="68747-111">Met deze cmdlet maakt u een lokaal gebruikers account of een lokaal gebruikers account dat is verbonden met een Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="68747-111">This cmdlet creates a local user account or a local user account that is connected to a Microsoft account.</span></span>

> [!NOTE]
> <span data-ttu-id="68747-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="68747-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="68747-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="68747-113">EXAMPLES</span></span>

### <span data-ttu-id="68747-114">Voor beeld 1: een gebruikers account maken</span><span class="sxs-lookup"><span data-stu-id="68747-114">Example 1: Create a user account</span></span>

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

<span data-ttu-id="68747-115">Met deze opdracht maakt u een lokaal gebruikers account en geeft u de para meters **AccountExpires** of **Password** niet op.</span><span class="sxs-lookup"><span data-stu-id="68747-115">This command creates a local user account and does not specify the **AccountExpires** or **Password** parameters.</span></span> <span data-ttu-id="68747-116">Daarom verloopt het account niet standaard of heeft het een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="68747-116">Therefore, the account doesn't expire or have a password by default.</span></span>

### <span data-ttu-id="68747-117">Voor beeld 2: een gebruikers account met een wacht woord maken</span><span class="sxs-lookup"><span data-stu-id="68747-117">Example 2: Create a user account that has a password</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

<span data-ttu-id="68747-118">Met de eerste opdracht wordt u gevraagd om een wacht woord met behulp van de- `Read-Host` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="68747-118">The first command prompts you for a password by using the `Read-Host` cmdlet.</span></span> <span data-ttu-id="68747-119">De opdracht slaat het wacht woord op als een beveiligde teken reeks in de `$Password` variabele.</span><span class="sxs-lookup"><span data-stu-id="68747-119">The command stores the password as a secure string in the `$Password` variable.</span></span>

<span data-ttu-id="68747-120">Met de tweede opdracht maakt u een lokaal gebruikers account met behulp van het wacht woord dat is opgeslagen in `$Password` .</span><span class="sxs-lookup"><span data-stu-id="68747-120">The second command creates a local user account by using the password stored in `$Password`.</span></span> <span data-ttu-id="68747-121">De opdracht geeft een gebruikers naam, volledige naam en beschrijving voor het gebruikers account op.</span><span class="sxs-lookup"><span data-stu-id="68747-121">The command specifies a user name, full name, and description for the user account.</span></span>

## <span data-ttu-id="68747-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="68747-122">PARAMETERS</span></span>

### <span data-ttu-id="68747-123">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="68747-123">-AccountExpires</span></span>

<span data-ttu-id="68747-124">Hiermee geeft u op wanneer het gebruikers account verloopt.</span><span class="sxs-lookup"><span data-stu-id="68747-124">Specifies when the user account expires.</span></span> <span data-ttu-id="68747-125">Gebruik de cmdlet om een **DateTime** -object te verkrijgen `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="68747-125">To obtain a **DateTime** object, use the `Get-Date` cmdlet.</span></span>
<span data-ttu-id="68747-126">Als u deze para meter niet opgeeft, verloopt het account niet.</span><span class="sxs-lookup"><span data-stu-id="68747-126">If you do not specify this parameter, the account does not expire.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-127">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="68747-127">-AccountNeverExpires</span></span>

<span data-ttu-id="68747-128">Geeft aan dat het account niet verloopt.</span><span class="sxs-lookup"><span data-stu-id="68747-128">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-129">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="68747-129">-Description</span></span>

<span data-ttu-id="68747-130">Hiermee geeft u een opmerking op voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-130">Specifies a comment for the user account.</span></span>
<span data-ttu-id="68747-131">De maximale lengte is 48 tekens.</span><span class="sxs-lookup"><span data-stu-id="68747-131">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-132">-Uitgeschakeld</span><span class="sxs-lookup"><span data-stu-id="68747-132">-Disabled</span></span>

<span data-ttu-id="68747-133">Hiermee wordt aangegeven dat de gebruikers account is uitgeschakeld met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="68747-133">Indicates that this cmdlet creates the user account as disabled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-134">-FullName</span><span class="sxs-lookup"><span data-stu-id="68747-134">-FullName</span></span>

<span data-ttu-id="68747-135">Hiermee geeft u de volledige naam voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-135">Specifies the full name for the user account.</span></span> <span data-ttu-id="68747-136">De volledige naam wijkt af van de gebruikers naam van het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-136">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-137">-Name</span><span class="sxs-lookup"><span data-stu-id="68747-137">-Name</span></span>

<span data-ttu-id="68747-138">Hiermee geeft u de gebruikers naam voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-138">Specifies the user name for the user account.</span></span>

<span data-ttu-id="68747-139">Als u een lokaal gebruikers account voor het lokale systeem maakt, mag de gebruikers naam Maxi maal 20 tekens of kleine letters bevatten.</span><span class="sxs-lookup"><span data-stu-id="68747-139">If you create a local user account for the local system, the user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="68747-140">Een gebruikers naam mag niet de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="68747-140">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="68747-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="68747-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

<span data-ttu-id="68747-142">Een gebruikers naam mag niet alleen uit punten `.` of spaties bestaan.</span><span class="sxs-lookup"><span data-stu-id="68747-142">A user name cannot consist only of periods `.` or spaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-143">-Geen wacht woord</span><span class="sxs-lookup"><span data-stu-id="68747-143">-NoPassword</span></span>

<span data-ttu-id="68747-144">Geeft aan dat het gebruikers account geen wacht woord heeft.</span><span class="sxs-lookup"><span data-stu-id="68747-144">Indicates that the user account does not have a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-145">-Password</span><span class="sxs-lookup"><span data-stu-id="68747-145">-Password</span></span>

<span data-ttu-id="68747-146">Hiermee geeft u een wacht woord voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-146">Specifies a password for the user account.</span></span> <span data-ttu-id="68747-147">U kunt `Read-Host -GetCredential` , `Get-Credential` , of `ConvertTo-SecureString` een **SecureString** -object maken voor het wacht woord.</span><span class="sxs-lookup"><span data-stu-id="68747-147">You can use `Read-Host -GetCredential`, `Get-Credential`, or `ConvertTo-SecureString` to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="68747-148">Als u de para meters **wacht woord** **en wacht woord** weglaat, wordt `New-LocalUser` u gevraagd om het wacht woord van de nieuwe gebruiker.</span><span class="sxs-lookup"><span data-stu-id="68747-148">If you omit the **Password** and **NoPassword** parameters, `New-LocalUser` prompts you for the new user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-149">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="68747-149">-PasswordNeverExpires</span></span>

<span data-ttu-id="68747-150">Hiermee wordt aangegeven of het wacht woord is verlopen.</span><span class="sxs-lookup"><span data-stu-id="68747-150">Indicates whether the password expires.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-151">-UserMayNotChangePassword</span><span class="sxs-lookup"><span data-stu-id="68747-151">-UserMayNotChangePassword</span></span>

<span data-ttu-id="68747-152">Geeft aan dat de gebruiker het wacht woord voor het gebruikers account niet kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="68747-152">Indicates that the user cannot change the password on the user account.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="68747-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="68747-153">-Confirm</span></span>

<span data-ttu-id="68747-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="68747-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="68747-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="68747-155">-WhatIf</span></span>

<span data-ttu-id="68747-156">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="68747-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="68747-157">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="68747-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="68747-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="68747-158">CommonParameters</span></span>

<span data-ttu-id="68747-159">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="68747-159">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="68747-160">Zie [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="68747-160">For more information, see [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="68747-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="68747-161">INPUTS</span></span>

### <span data-ttu-id="68747-162">System. String, System. DateTime, System. Boole, System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="68747-162">System.String, System.DateTime, System.Boolean, System.Security.SecureString</span></span>

<span data-ttu-id="68747-163">U kunt een teken reeks, een **DateTime** -object, een Booleaanse waarde of een beveiligde teken reeks door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="68747-163">You can pipe a string, a **DateTime** object, a boolean value, or a secure string to this cmdlet.</span></span>

## <span data-ttu-id="68747-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="68747-164">OUTPUTS</span></span>

### <span data-ttu-id="68747-165">System. Management. Automation. SecurityAccountsManager. Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-165">System.Management.Automation.SecurityAccountsManager.LocalUser</span></span>

<span data-ttu-id="68747-166">Met deze cmdlet wordt een **lokalegebruiker** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="68747-166">This cmdlet returns a **LocalUser** object.</span></span>
<span data-ttu-id="68747-167">Dit object bevat informatie over het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="68747-167">This object provides information about the user account.</span></span>

## <span data-ttu-id="68747-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="68747-168">NOTES</span></span>

- <span data-ttu-id="68747-169">Een gebruikers naam mag niet identiek zijn aan een andere gebruikers naam of groeps naam op de computer.</span><span class="sxs-lookup"><span data-stu-id="68747-169">A user name cannot be identical to any other user name or group name on the computer.</span></span> <span data-ttu-id="68747-170">Een gebruikers naam mag niet alleen uit punten `.` of spaties bestaan.</span><span class="sxs-lookup"><span data-stu-id="68747-170">A user name cannot consist only of periods `.` or spaces.</span></span> <span data-ttu-id="68747-171">Een gebruikers naam mag Maxi maal 20 tekens of kleine letters bevatten.</span><span class="sxs-lookup"><span data-stu-id="68747-171">A user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="68747-172">Een gebruikers naam mag niet de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="68747-172">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="68747-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="68747-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

- <span data-ttu-id="68747-174">Een wacht woord mag Maxi maal 127 tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="68747-174">A password can contain up to 127 characters.</span></span>
- <span data-ttu-id="68747-175">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="68747-175">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="68747-176">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="68747-176">The possible sources are as follows:</span></span>

  - <span data-ttu-id="68747-177">Lokaal</span><span class="sxs-lookup"><span data-stu-id="68747-177">Local</span></span>
  - <span data-ttu-id="68747-178">Active Directory</span><span class="sxs-lookup"><span data-stu-id="68747-178">Active Directory</span></span>
  - <span data-ttu-id="68747-179">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="68747-179">Azure Active Directory group</span></span>
  - <span data-ttu-id="68747-180">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="68747-180">Microsoft Account</span></span>

> [!NOTE]
> <span data-ttu-id="68747-181">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="68747-181">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="68747-182">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="68747-182">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="68747-183">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="68747-183">RELATED LINKS</span></span>

[<span data-ttu-id="68747-184">Disable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-184">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="68747-185">Enable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-185">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="68747-186">Get-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-186">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="68747-187">Remove-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-187">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="68747-188">Naam wijzigen-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-188">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="68747-189">Set-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="68747-189">Set-LocalUser</span></span>](Set-LocalUser.md)
