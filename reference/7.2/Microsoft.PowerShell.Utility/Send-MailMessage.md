---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: e1363b2f30420c130093fd92d4da2f7c8037d640
ms.sourcegitcommit: c91f79576bc54e162bcc7adf78026417b2776687
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274322"
---
# <span data-ttu-id="bd3d8-102">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="bd3d8-102">Send-MailMessage</span></span>

## <span data-ttu-id="bd3d8-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="bd3d8-103">Synopsis</span></span>
<span data-ttu-id="bd3d8-104">Hiermee verzendt u een e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-104">Sends an email message.</span></span>

## <span data-ttu-id="bd3d8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bd3d8-105">Syntax</span></span>

### <span data-ttu-id="bd3d8-106">Alles</span><span class="sxs-lookup"><span data-stu-id="bd3d8-106">All</span></span>

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="bd3d8-107">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd3d8-107">Description</span></span>

<span data-ttu-id="bd3d8-108">De `Send-MailMessage` cmdlet verzendt een e-mail bericht vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-108">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="bd3d8-109">U moet een Simple Mail Transfer Protocol-server (SMTP) opgeven of de `Send-MailMessage` opdracht mislukt.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-109">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="bd3d8-110">Gebruik de para meter **SmtpServer** of stel de `$PSEmailServer` variabele in op een geldige SMTP-server.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-110">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="bd3d8-111">De waarde die is toegewezen aan `$PSEmailServer` , is de standaard instelling voor SMTP voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-111">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="bd3d8-112">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-112">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="bd3d8-113">De `Send-MailMessage` cmdlet is verouderd.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-113">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="bd3d8-114">Met deze cmdlet worden geen beveiligde verbindingen met SMTP-servers gegarandeerd.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-114">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="bd3d8-115">Hoewel er geen directe vervanging beschikbaar is in Power shell, raden we u aan geen gebruik te maken van `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-115">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="bd3d8-116">Zie [platform Compatibility Note DE0005](https://aka.ms/SendMailMessage)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-116">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="bd3d8-117">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="bd3d8-117">Examples</span></span>

### <span data-ttu-id="bd3d8-118">Voor beeld 1: e-mail van een persoon naar een andere persoon verzenden</span><span class="sxs-lookup"><span data-stu-id="bd3d8-118">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="bd3d8-119">In dit voor beeld wordt een e-mail bericht van één persoon naar een andere persoon verzonden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-119">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="bd3d8-120">De para meters **from**, **to** en **subject** zijn vereist door `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-120">The **From**, **To**, and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="bd3d8-121">In dit voor beeld wordt de standaard `$PSEmailServer` variabele voor de SMTP-server gebruikt, dus de para meter **SmtpServer** is niet nodig.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-121">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="bd3d8-122">De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-122">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="bd3d8-123">Met de para meter **to** wordt de ontvanger van het bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-123">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="bd3d8-124">De **onderwerp** -para meter gebruikt de **test** bericht voor de tekst teken reeks, omdat de optionele **hoofd tekst** van de para meter niet is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-124">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="bd3d8-125">Voor beeld 2: een bijlage verzenden</span><span class="sxs-lookup"><span data-stu-id="bd3d8-125">Example 2: Send an attachment</span></span>

<span data-ttu-id="bd3d8-126">In dit voor beeld wordt een e-mail bericht met een bijlage verzonden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-126">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="bd3d8-127">De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-127">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="bd3d8-128">Met de para meter **to worden** de ontvangers van het bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-128">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="bd3d8-129">De **onderwerps** parameter beschrijft de inhoud van het bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-129">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="bd3d8-130">De **hoofd tekst** van de para meter is de inhoud van het bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-130">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="bd3d8-131">Met de para meter **Attachments** geeft u het bestand in de huidige map op dat aan het e-mail bericht is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-131">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="bd3d8-132">Met de **prioriteits** parameter wordt het bericht ingesteld op **hoge** prioriteit.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-132">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="bd3d8-133">De para meter **-DeliveryNotificationOption** geeft twee waarden, **OnSuccess** en **OnFailure**.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-133">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="bd3d8-134">De afzender ontvangt e-mail meldingen om te bevestigen dat de bericht bezorging is geslaagd of mislukt.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-134">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="bd3d8-135">Met de para meter **SmtpServer** wordt de SMTP-server ingesteld op **SMTP.fabrikam.com**.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-135">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="bd3d8-136">Voor beeld 3: een e-mail verzenden naar een adressen lijst</span><span class="sxs-lookup"><span data-stu-id="bd3d8-136">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="bd3d8-137">In dit voor beeld wordt een e-mail bericht verzonden naar een adressen lijst.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-137">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="bd3d8-138">De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-138">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="bd3d8-139">Met de para meter **to worden** de ontvangers van het bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-139">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="bd3d8-140">De **CC** -para meter stuurt een kopie van het bericht naar de opgegeven ontvanger.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-140">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="bd3d8-141">De para meter **BCC** verzendt een blinde kopie van het bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-141">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="bd3d8-142">Een blinde kopie is een e-mail adres dat is verborgen voor de andere ontvangers.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-142">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="bd3d8-143">De **subject** -para meter is het bericht omdat de optionele **Body** -para meter niet is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-143">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="bd3d8-144">De **referentie** parameter geeft aan dat de referenties van de domein beheerder worden gebruikt om het bericht te verzenden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-144">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="bd3d8-145">De para meter **UseSsl** geeft aan dat SSL (Secure Socket Layer) een beveiligde verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-145">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="bd3d8-146">Parameters</span><span class="sxs-lookup"><span data-stu-id="bd3d8-146">Parameters</span></span>

### <span data-ttu-id="bd3d8-147">-Bijlagen</span><span class="sxs-lookup"><span data-stu-id="bd3d8-147">-Attachments</span></span>

<span data-ttu-id="bd3d8-148">Hiermee geeft u het pad en de bestands namen op van bestanden die aan het e-mail bericht moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-148">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="bd3d8-149">U kunt deze para meter gebruiken of de paden en bestands namen naar `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-149">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-150">-BCC</span><span class="sxs-lookup"><span data-stu-id="bd3d8-150">-Bcc</span></span>

<span data-ttu-id="bd3d8-151">Hiermee geeft u de e-mail adressen op die een kopie van het e-mail bericht ontvangen, maar die niet worden vermeld als ontvangers van het bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-151">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="bd3d8-152">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-152">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-153">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="bd3d8-153">-Body</span></span>

<span data-ttu-id="bd3d8-154">Hiermee geeft u de inhoud van het e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-154">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-155">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="bd3d8-155">-BodyAsHtml</span></span>

<span data-ttu-id="bd3d8-156">Hiermee geeft u op dat de waarde van de **Body** -para meter HTML bevat.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-156">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-157">-CC</span><span class="sxs-lookup"><span data-stu-id="bd3d8-157">-Cc</span></span>

<span data-ttu-id="bd3d8-158">Hiermee geeft u de e-mail adressen waarnaar een Carbon Copy (CC) van het e-mail bericht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-158">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="bd3d8-159">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-159">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="bd3d8-160">-Credential</span></span>

<span data-ttu-id="bd3d8-161">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-161">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="bd3d8-162">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-162">The default is the current user.</span></span>

<span data-ttu-id="bd3d8-163">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-163">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="bd3d8-164">U kunt ook een **PSCredential** -object, zoals een, opgeven in de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-164">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="bd3d8-165">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="bd3d8-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bd3d8-166">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-167">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="bd3d8-167">-DeliveryNotificationOption</span></span>

<span data-ttu-id="bd3d8-168">Hiermee geeft u de opties voor het bezorgings bericht voor het e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-168">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="bd3d8-169">U kunt meerdere waarden opgeven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-169">You can specify multiple values.</span></span>
<span data-ttu-id="bd3d8-170">Geen is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-170">None is the default value.</span></span> <span data-ttu-id="bd3d8-171">De alias voor deze para meter is **Dno**.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-171">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="bd3d8-172">De bezorgings meldingen worden verzonden naar het adres in de para meter **from** .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-172">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="bd3d8-173">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="bd3d8-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bd3d8-174">`None`: Geen melding.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-174">`None`: No notification.</span></span>
- <span data-ttu-id="bd3d8-175">`OnSuccess`: U wordt gewaarschuwd als de levering is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-175">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="bd3d8-176">`OnFailure`: U wordt gewaarschuwd als de levering mislukt.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-176">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="bd3d8-177">`Delay`: U wordt gewaarschuwd als de levering is vertraagd.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-177">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="bd3d8-178">`Never`: Nooit waarschuwen.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-178">`Never`: Never notify.</span></span>

<span data-ttu-id="bd3d8-179">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-179">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="bd3d8-180">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-180">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="bd3d8-181">De waarden kunnen worden door gegeven aan de **DeliveryNotification** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-181">The values can be passed to the **DeliveryNotification** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="bd3d8-182">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-182">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="bd3d8-183">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-183">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-184">-Encoding</span><span class="sxs-lookup"><span data-stu-id="bd3d8-184">-Encoding</span></span>

<span data-ttu-id="bd3d8-185">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-185">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="bd3d8-186">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-186">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="bd3d8-187">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="bd3d8-187">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bd3d8-188">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="bd3d8-188">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="bd3d8-189">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-189">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bd3d8-190">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-190">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bd3d8-191">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-191">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="bd3d8-192">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-192">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="bd3d8-193">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-193">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="bd3d8-194">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-194">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="bd3d8-195">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="bd3d8-195">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bd3d8-196">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="bd3d8-196">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bd3d8-197">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-197">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="bd3d8-198">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-198">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="bd3d8-199">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-199">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-200">-Van</span><span class="sxs-lookup"><span data-stu-id="bd3d8-200">-From</span></span>

<span data-ttu-id="bd3d8-201">De para meter **from** is vereist.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-201">The **From** parameter is required.</span></span> <span data-ttu-id="bd3d8-202">Met deze para meter geeft u het e-mail adres van de afzender op.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-202">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="bd3d8-203">Voer een naam (optioneel) en e-mail adres in, zoals `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-203">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-204">-Port</span><span class="sxs-lookup"><span data-stu-id="bd3d8-204">-Port</span></span>

<span data-ttu-id="bd3d8-205">Hiermee geeft u een alternatieve poort op de SMTP-server op.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-205">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="bd3d8-206">De standaard waarde is 25, de standaard-SMTP-poort.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-206">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-207">-Prioriteit</span><span class="sxs-lookup"><span data-stu-id="bd3d8-207">-Priority</span></span>

<span data-ttu-id="bd3d8-208">Hiermee geeft u de prioriteit van het e-mail bericht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-208">Specifies the priority of the email message.</span></span> <span data-ttu-id="bd3d8-209">Normaal is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-209">Normal is the default.</span></span> <span data-ttu-id="bd3d8-210">De acceptabele waarden voor deze para meter zijn normaal, hoog en laag.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-210">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-211">-ReplyTo</span><span class="sxs-lookup"><span data-stu-id="bd3d8-211">-ReplyTo</span></span>

<span data-ttu-id="bd3d8-212">Hiermee geeft u aanvullende e-mail adressen (met uitzonde ring van het van-adres) op die moeten worden gebruikt om dit bericht te beantwoorden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-212">Specifies additional email addresses (other than the From address) to use to reply to this message.</span></span>
<span data-ttu-id="bd3d8-213">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-213">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

<span data-ttu-id="bd3d8-214">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-214">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-215">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="bd3d8-215">-SmtpServer</span></span>

<span data-ttu-id="bd3d8-216">Hiermee geeft u de naam van de SMTP-server die het e-mail bericht verzendt.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-216">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="bd3d8-217">De standaard waarde is de waarde van de `$PSEmailServer` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-217">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="bd3d8-218">Als de voorkeurs variabele niet is ingesteld en deze para meter niet wordt gebruikt, `Send-MailMessage` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-218">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-219">-Onderwerp</span><span class="sxs-lookup"><span data-stu-id="bd3d8-219">-Subject</span></span>

<span data-ttu-id="bd3d8-220">De **onderwerp** -para meter is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-220">The **Subject** parameter isn't required.</span></span> <span data-ttu-id="bd3d8-221">Met deze para meter wordt het onderwerp van het e-mail bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-221">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-222">-Naar</span><span class="sxs-lookup"><span data-stu-id="bd3d8-222">-To</span></span>

<span data-ttu-id="bd3d8-223">De **to** -para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-223">The **To** parameter is required.</span></span> <span data-ttu-id="bd3d8-224">Met deze para meter wordt het e-mail adres van de ontvanger opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-224">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="bd3d8-225">Als er meerdere ontvangers zijn, scheidt u hun adressen met een komma ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="bd3d8-225">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="bd3d8-226">Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-226">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd3d8-227">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="bd3d8-227">-UseSsl</span></span>

<span data-ttu-id="bd3d8-228">Het Secure Sockets Layer-Protocol (SSL) wordt gebruikt om een beveiligde verbinding met de externe computer tot stand te brengen om e-mail te verzenden.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-228">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="bd3d8-229">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-229">By default, SSL is not used.</span></span>

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

### <span data-ttu-id="bd3d8-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd3d8-230">CommonParameters</span></span>

<span data-ttu-id="bd3d8-231">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-231">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd3d8-232">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-232">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd3d8-233">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="bd3d8-233">Inputs</span></span>

### <span data-ttu-id="bd3d8-234">System. String</span><span class="sxs-lookup"><span data-stu-id="bd3d8-234">System.String</span></span>

<span data-ttu-id="bd3d8-235">U kunt het pad en de bestands namen van bijlagen door sluizen naar `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bd3d8-235">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="bd3d8-236">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="bd3d8-236">Outputs</span></span>

### <span data-ttu-id="bd3d8-237">Geen</span><span class="sxs-lookup"><span data-stu-id="bd3d8-237">None</span></span>

<span data-ttu-id="bd3d8-238">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bd3d8-238">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bd3d8-239">Notities</span><span class="sxs-lookup"><span data-stu-id="bd3d8-239">Notes</span></span>

## <span data-ttu-id="bd3d8-240">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="bd3d8-240">Related Links</span></span>

[<span data-ttu-id="bd3d8-241">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="bd3d8-241">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="bd3d8-242">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="bd3d8-242">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

