---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250375"
---
# <span data-ttu-id="f6968-103">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="f6968-103">Send-MailMessage</span></span>

## <span data-ttu-id="f6968-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f6968-104">SYNOPSIS</span></span>
<span data-ttu-id="f6968-105">Hiermee verzendt u een e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-105">Sends an email message.</span></span>

## <span data-ttu-id="f6968-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f6968-106">SYNTAX</span></span>

### <span data-ttu-id="f6968-107">Alles</span><span class="sxs-lookup"><span data-stu-id="f6968-107">All</span></span>

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## <span data-ttu-id="f6968-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f6968-108">DESCRIPTION</span></span>

<span data-ttu-id="f6968-109">De `Send-MailMessage` cmdlet verzendt een e-mail bericht vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="f6968-109">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="f6968-110">U moet een Simple Mail Transfer Protocol-server (SMTP) opgeven of de `Send-MailMessage` opdracht mislukt.</span><span class="sxs-lookup"><span data-stu-id="f6968-110">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="f6968-111">Gebruik de para meter **SmtpServer** of stel de `$PSEmailServer` variabele in op een geldige SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="f6968-111">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="f6968-112">De waarde die is toegewezen aan `$PSEmailServer` , is de standaard instelling voor SMTP voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="f6968-112">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="f6968-113">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f6968-113">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="f6968-114">De `Send-MailMessage` cmdlet is verouderd.</span><span class="sxs-lookup"><span data-stu-id="f6968-114">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="f6968-115">Met deze cmdlet worden geen beveiligde verbindingen met SMTP-servers gegarandeerd.</span><span class="sxs-lookup"><span data-stu-id="f6968-115">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="f6968-116">Hoewel er geen directe vervanging beschikbaar is in Power shell, raden we u aan geen gebruik te maken van `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="f6968-116">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="f6968-117">Zie [platform Compatibility Note DE0005](https://aka.ms/SendMailMessage)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f6968-117">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="f6968-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f6968-118">EXAMPLES</span></span>

### <span data-ttu-id="f6968-119">Voor beeld 1: e-mail van een persoon naar een andere persoon verzenden</span><span class="sxs-lookup"><span data-stu-id="f6968-119">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="f6968-120">In dit voor beeld wordt een e-mail bericht van één persoon naar een andere persoon verzonden.</span><span class="sxs-lookup"><span data-stu-id="f6968-120">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="f6968-121">De para meters **from** , **to** en **subject** zijn vereist door `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="f6968-121">The **From** , **To** , and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="f6968-122">In dit voor beeld wordt de standaard `$PSEmailServer` variabele voor de SMTP-server gebruikt, dus de para meter **SmtpServer** is niet nodig.</span><span class="sxs-lookup"><span data-stu-id="f6968-122">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="f6968-123">De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven.</span><span class="sxs-lookup"><span data-stu-id="f6968-123">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="f6968-124">Met de para meter **to** wordt de ontvanger van het bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f6968-124">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="f6968-125">De **onderwerp** -para meter gebruikt de **test** bericht voor de tekst teken reeks, omdat de optionele **hoofd tekst** van de para meter niet is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="f6968-125">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="f6968-126">Voor beeld 2: een bijlage verzenden</span><span class="sxs-lookup"><span data-stu-id="f6968-126">Example 2: Send an attachment</span></span>

<span data-ttu-id="f6968-127">In dit voor beeld wordt een e-mail bericht met een bijlage verzonden.</span><span class="sxs-lookup"><span data-stu-id="f6968-127">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="f6968-128">De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven.</span><span class="sxs-lookup"><span data-stu-id="f6968-128">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="f6968-129">Met de para meter **to worden** de ontvangers van het bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f6968-129">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="f6968-130">De **onderwerps** parameter beschrijft de inhoud van het bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-130">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="f6968-131">De **hoofd tekst** van de para meter is de inhoud van het bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-131">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="f6968-132">Met de para meter **Attachments** geeft u het bestand in de huidige map op dat aan het e-mail bericht is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f6968-132">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="f6968-133">Met de **prioriteits** parameter wordt het bericht ingesteld op **hoge** prioriteit.</span><span class="sxs-lookup"><span data-stu-id="f6968-133">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="f6968-134">De para meter **-DeliveryNotificationOption** geeft twee waarden, **OnSuccess** en **OnFailure**.</span><span class="sxs-lookup"><span data-stu-id="f6968-134">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="f6968-135">De afzender ontvangt e-mail meldingen om te bevestigen dat de bericht bezorging is geslaagd of mislukt.</span><span class="sxs-lookup"><span data-stu-id="f6968-135">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="f6968-136">Met de para meter **SmtpServer** wordt de SMTP-server ingesteld op **SMTP.fabrikam.com**.</span><span class="sxs-lookup"><span data-stu-id="f6968-136">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="f6968-137">Voor beeld 3: een e-mail verzenden naar een adressen lijst</span><span class="sxs-lookup"><span data-stu-id="f6968-137">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="f6968-138">In dit voor beeld wordt een e-mail bericht verzonden naar een adressen lijst.</span><span class="sxs-lookup"><span data-stu-id="f6968-138">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="f6968-139">De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven.</span><span class="sxs-lookup"><span data-stu-id="f6968-139">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="f6968-140">Met de para meter **to worden** de ontvangers van het bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f6968-140">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="f6968-141">De **CC** -para meter stuurt een kopie van het bericht naar de opgegeven ontvanger.</span><span class="sxs-lookup"><span data-stu-id="f6968-141">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="f6968-142">De para meter **BCC** verzendt een blinde kopie van het bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-142">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="f6968-143">Een blinde kopie is een e-mail adres dat is verborgen voor de andere ontvangers.</span><span class="sxs-lookup"><span data-stu-id="f6968-143">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="f6968-144">De **subject** -para meter is het bericht omdat de optionele **Body** -para meter niet is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="f6968-144">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="f6968-145">De **referentie** parameter geeft aan dat de referenties van de domein beheerder worden gebruikt om het bericht te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f6968-145">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="f6968-146">De para meter **UseSsl** geeft aan dat SSL (Secure Socket Layer) een beveiligde verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="f6968-146">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="f6968-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6968-147">PARAMETERS</span></span>

### <span data-ttu-id="f6968-148">-Bijlagen</span><span class="sxs-lookup"><span data-stu-id="f6968-148">-Attachments</span></span>

<span data-ttu-id="f6968-149">Hiermee geeft u het pad en de bestands namen op van bestanden die aan het e-mail bericht moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f6968-149">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="f6968-150">U kunt deze para meter gebruiken of de paden en bestands namen naar `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="f6968-150">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-151">-BCC</span><span class="sxs-lookup"><span data-stu-id="f6968-151">-Bcc</span></span>

<span data-ttu-id="f6968-152">Hiermee geeft u de e-mail adressen op die een kopie van het e-mail bericht ontvangen, maar die niet worden vermeld als ontvangers van het bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-152">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="f6968-153">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="f6968-153">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-154">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="f6968-154">-Body</span></span>

<span data-ttu-id="f6968-155">Hiermee geeft u de inhoud van het e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-155">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-156">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="f6968-156">-BodyAsHtml</span></span>

<span data-ttu-id="f6968-157">Hiermee geeft u op dat de waarde van de **Body** -para meter HTML bevat.</span><span class="sxs-lookup"><span data-stu-id="f6968-157">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-158">-CC</span><span class="sxs-lookup"><span data-stu-id="f6968-158">-Cc</span></span>

<span data-ttu-id="f6968-159">Hiermee geeft u de e-mail adressen waarnaar een Carbon Copy (CC) van het e-mail bericht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f6968-159">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="f6968-160">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="f6968-160">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="f6968-161">-Credential</span></span>

<span data-ttu-id="f6968-162">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f6968-162">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="f6968-163">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f6968-163">The default is the current user.</span></span>

<span data-ttu-id="f6968-164">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="f6968-164">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="f6968-165">U kunt ook een **PSCredential** -object, zoals een, opgeven in de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6968-165">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f6968-166">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f6968-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f6968-167">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="f6968-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-168">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="f6968-168">-DeliveryNotificationOption</span></span>

<span data-ttu-id="f6968-169">Hiermee geeft u de opties voor het bezorgings bericht voor het e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-169">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="f6968-170">U kunt meerdere waarden opgeven.</span><span class="sxs-lookup"><span data-stu-id="f6968-170">You can specify multiple values.</span></span>
<span data-ttu-id="f6968-171">Geen is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="f6968-171">None is the default value.</span></span> <span data-ttu-id="f6968-172">De alias voor deze para meter is **Dno**.</span><span class="sxs-lookup"><span data-stu-id="f6968-172">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="f6968-173">De bezorgings meldingen worden verzonden naar het adres in de para meter **from** .</span><span class="sxs-lookup"><span data-stu-id="f6968-173">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="f6968-174">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="f6968-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f6968-175">`None`: Geen melding.</span><span class="sxs-lookup"><span data-stu-id="f6968-175">`None`: No notification.</span></span>
- <span data-ttu-id="f6968-176">`OnSuccess`: U wordt gewaarschuwd als de levering is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="f6968-176">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="f6968-177">`OnFailure`: U wordt gewaarschuwd als de levering mislukt.</span><span class="sxs-lookup"><span data-stu-id="f6968-177">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="f6968-178">`Delay`: U wordt gewaarschuwd als de levering is vertraagd.</span><span class="sxs-lookup"><span data-stu-id="f6968-178">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="f6968-179">`Never`: Nooit waarschuwen.</span><span class="sxs-lookup"><span data-stu-id="f6968-179">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-180">-Encoding</span><span class="sxs-lookup"><span data-stu-id="f6968-180">-Encoding</span></span>

<span data-ttu-id="f6968-181">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="f6968-181">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="f6968-182">De standaardwaarde is `Default`.</span><span class="sxs-lookup"><span data-stu-id="f6968-182">The default value is `Default`.</span></span>

<span data-ttu-id="f6968-183">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="f6968-183">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f6968-184">`ASCII` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="f6968-184">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f6968-185">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="f6968-185">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="f6968-186">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="f6968-186">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="f6968-187">`OEM` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="f6968-187">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="f6968-188">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="f6968-188">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="f6968-189">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f6968-189">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="f6968-190">`UTF8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f6968-190">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="f6968-191">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="f6968-191">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-192">-Van</span><span class="sxs-lookup"><span data-stu-id="f6968-192">-From</span></span>

<span data-ttu-id="f6968-193">De para meter **from** is vereist.</span><span class="sxs-lookup"><span data-stu-id="f6968-193">The **From** parameter is required.</span></span> <span data-ttu-id="f6968-194">Met deze para meter geeft u het e-mail adres van de afzender op.</span><span class="sxs-lookup"><span data-stu-id="f6968-194">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="f6968-195">Voer een naam (optioneel) en e-mail adres in, zoals `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="f6968-195">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-196">-Port</span><span class="sxs-lookup"><span data-stu-id="f6968-196">-Port</span></span>

<span data-ttu-id="f6968-197">Hiermee geeft u een alternatieve poort op de SMTP-server op.</span><span class="sxs-lookup"><span data-stu-id="f6968-197">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="f6968-198">De standaard waarde is 25, de standaard-SMTP-poort.</span><span class="sxs-lookup"><span data-stu-id="f6968-198">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-199">-Prioriteit</span><span class="sxs-lookup"><span data-stu-id="f6968-199">-Priority</span></span>

<span data-ttu-id="f6968-200">Hiermee geeft u de prioriteit van het e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="f6968-200">Specifies the priority of the email message.</span></span> <span data-ttu-id="f6968-201">Normaal is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="f6968-201">Normal is the default.</span></span> <span data-ttu-id="f6968-202">De acceptabele waarden voor deze para meter zijn normaal, hoog en laag.</span><span class="sxs-lookup"><span data-stu-id="f6968-202">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-203">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="f6968-203">-SmtpServer</span></span>

<span data-ttu-id="f6968-204">Hiermee geeft u de naam van de SMTP-server die het e-mail bericht verzendt.</span><span class="sxs-lookup"><span data-stu-id="f6968-204">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="f6968-205">De standaard waarde is de waarde van de `$PSEmailServer` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="f6968-205">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="f6968-206">Als de voorkeurs variabele niet is ingesteld en deze para meter niet wordt gebruikt, `Send-MailMessage` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f6968-206">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-207">-Onderwerp</span><span class="sxs-lookup"><span data-stu-id="f6968-207">-Subject</span></span>

<span data-ttu-id="f6968-208">De **onderwerps** parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="f6968-208">The **Subject** parameter is required.</span></span> <span data-ttu-id="f6968-209">Met deze para meter wordt het onderwerp van het e-mail bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f6968-209">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-210">-Naar</span><span class="sxs-lookup"><span data-stu-id="f6968-210">-To</span></span>

<span data-ttu-id="f6968-211">De **to** -para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="f6968-211">The **To** parameter is required.</span></span> <span data-ttu-id="f6968-212">Met deze para meter wordt het e-mail adres van de ontvanger opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f6968-212">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="f6968-213">Als er meerdere ontvangers zijn, scheidt u hun adressen met een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="f6968-213">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="f6968-214">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="f6968-214">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6968-215">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="f6968-215">-UseSsl</span></span>

<span data-ttu-id="f6968-216">Het Secure Sockets Layer-Protocol (SSL) wordt gebruikt om een beveiligde verbinding met de externe computer tot stand te brengen om e-mail te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f6968-216">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="f6968-217">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f6968-217">By default, SSL is not used.</span></span>

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

### <span data-ttu-id="f6968-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6968-218">CommonParameters</span></span>

<span data-ttu-id="f6968-219">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f6968-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f6968-220">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f6968-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f6968-221">INVOER</span><span class="sxs-lookup"><span data-stu-id="f6968-221">INPUTS</span></span>

### <span data-ttu-id="f6968-222">System. String</span><span class="sxs-lookup"><span data-stu-id="f6968-222">System.String</span></span>

<span data-ttu-id="f6968-223">U kunt het pad en de bestands namen van bijlagen door sluizen naar `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="f6968-223">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="f6968-224">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f6968-224">OUTPUTS</span></span>

### <span data-ttu-id="f6968-225">Geen</span><span class="sxs-lookup"><span data-stu-id="f6968-225">None</span></span>

<span data-ttu-id="f6968-226">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f6968-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f6968-227">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f6968-227">NOTES</span></span>

## <span data-ttu-id="f6968-228">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f6968-228">RELATED LINKS</span></span>

[<span data-ttu-id="f6968-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="f6968-229">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="f6968-230">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f6968-230">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
