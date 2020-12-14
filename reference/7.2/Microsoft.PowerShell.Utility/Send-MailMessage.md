---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 0a68c665e8a0b504cfef416134374c5598ba55a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704735"
---
# Send-MailMessage

## SAMENVATTING
Hiermee verzendt u een e-mail bericht.

## SYNTAXIS

### Alles

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Send-MailMessage` cmdlet verzendt een e-mail bericht vanuit Power shell.

U moet een Simple Mail Transfer Protocol-server (SMTP) opgeven of de `Send-MailMessage` opdracht mislukt. Gebruik de para meter **SmtpServer** of stel de `$PSEmailServer` variabele in op een geldige SMTP-server.
De waarde die is toegewezen aan `$PSEmailServer` , is de standaard instelling voor SMTP voor Power shell. Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.

> [!WARNING]
> De `Send-MailMessage` cmdlet is verouderd. Met deze cmdlet worden geen beveiligde verbindingen met SMTP-servers gegarandeerd. Hoewel er geen directe vervanging beschikbaar is in Power shell, raden we u aan geen gebruik te maken van `Send-MailMessage` . Zie [platform Compatibility Note DE0005](https://aka.ms/SendMailMessage)(Engelstalig) voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: e-mail van een persoon naar een andere persoon verzenden

In dit voor beeld wordt een e-mail bericht van één persoon naar een andere persoon verzonden.

De para meters **from**, **to** en **subject** zijn vereist door `Send-MailMessage` . In dit voor beeld wordt de standaard `$PSEmailServer` variabele voor de SMTP-server gebruikt, dus de para meter **SmtpServer** is niet nodig.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven. Met de para meter **to** wordt de ontvanger van het bericht opgegeven. De **onderwerp** -para meter gebruikt de **test** bericht voor de tekst teken reeks, omdat de optionele **hoofd tekst** van de para meter niet is opgenomen.

### Voor beeld 2: een bijlage verzenden

In dit voor beeld wordt een e-mail bericht met een bijlage verzonden.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven. Met de para meter **to worden** de ontvangers van het bericht opgegeven. De **onderwerps** parameter beschrijft de inhoud van het bericht. De **hoofd tekst** van de para meter is de inhoud van het bericht.

Met de para meter **Attachments** geeft u het bestand in de huidige map op dat aan het e-mail bericht is gekoppeld. Met de **prioriteits** parameter wordt het bericht ingesteld op **hoge** prioriteit. De para meter **-DeliveryNotificationOption** geeft twee waarden, **OnSuccess** en **OnFailure**. De afzender ontvangt e-mail meldingen om te bevestigen dat de bericht bezorging is geslaagd of mislukt.
Met de para meter **SmtpServer** wordt de SMTP-server ingesteld op **SMTP.fabrikam.com**.

### Voor beeld 3: een e-mail verzenden naar een adressen lijst

In dit voor beeld wordt een e-mail bericht verzonden naar een adressen lijst.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

De `Send-MailMessage` cmdlet gebruikt de para meter **from** om de afzender van het bericht op te geven. Met de para meter **to worden** de ontvangers van het bericht opgegeven. De **CC** -para meter stuurt een kopie van het bericht naar de opgegeven ontvanger. De para meter **BCC** verzendt een blinde kopie van het bericht. Een blinde kopie is een e-mail adres dat is verborgen voor de andere ontvangers. De **subject** -para meter is het bericht omdat de optionele **Body** -para meter niet is opgenomen.

De **referentie** parameter geeft aan dat de referenties van de domein beheerder worden gebruikt om het bericht te verzenden. De para meter **UseSsl** geeft aan dat SSL (Secure Socket Layer) een beveiligde verbinding maakt.

## PARAMETERS

### -Bijlagen

Hiermee geeft u het pad en de bestands namen op van bestanden die aan het e-mail bericht moeten worden toegevoegd. U kunt deze para meter gebruiken of de paden en bestands namen naar `Send-MailMessage` .

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

### -BCC

Hiermee geeft u de e-mail adressen op die een kopie van het e-mail bericht ontvangen, maar die niet worden vermeld als ontvangers van het bericht. Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .

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

### -Hoofd tekst

Hiermee geeft u de inhoud van het e-mail bericht.

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

### -BodyAsHtml

Hiermee geeft u op dat de waarde van de **Body** -para meter HTML bevat.

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

### -CC

Hiermee geeft u de e-mail adressen waarnaar een Carbon Copy (CC) van het e-mail bericht wordt verzonden. Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .

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

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**. U kunt ook een **PSCredential** -object, zoals een, opgeven in de `Get-Credential` cmdlet.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

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

### -DeliveryNotificationOption

Hiermee geeft u de opties voor het bezorgings bericht voor het e-mail bericht. U kunt meerdere waarden opgeven.
Geen is de standaard waarde. De alias voor deze para meter is **Dno**.

De bezorgings meldingen worden verzonden naar het adres in de para meter **from** .

De acceptabele waarden voor deze para meter zijn als volgt:

- `None`: Geen melding.
- `OnSuccess`: U wordt gewaarschuwd als de levering is geslaagd.
- `OnFailure`: U wordt gewaarschuwd als de levering mislukt.
- `Delay`: U wordt gewaarschuwd als de levering is vertraagd.
- `Never`: Nooit waarschuwen.

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

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `utf8NoBOM`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

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

### -Van

De para meter **from** is vereist. Met deze para meter geeft u het e-mail adres van de afzender op. Voer een naam (optioneel) en e-mail adres in, zoals `Name <someone@fabrikam.com>` .

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

### -Port

Hiermee geeft u een alternatieve poort op de SMTP-server op. De standaard waarde is 25, de standaard-SMTP-poort.

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

### -Prioriteit

Hiermee geeft u de prioriteit van het e-mail bericht. Normaal is de standaard instelling. De acceptabele waarden voor deze para meter zijn normaal, hoog en laag.

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

### -ReplyTo

Hiermee geeft u aanvullende e-mail adressen (met uitzonde ring van het van-adres) op die moeten worden gebruikt om dit bericht te beantwoorden.
Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .

Deze para meter is geïntroduceerd in Power shell 6,2.

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

### -SmtpServer

Hiermee geeft u de naam van de SMTP-server die het e-mail bericht verzendt.

De standaard waarde is de waarde van de `$PSEmailServer` Voorkeurs variabele. Als de voorkeurs variabele niet is ingesteld en deze para meter niet wordt gebruikt, `Send-MailMessage` mislukt de opdracht.

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

### -Onderwerp

De **onderwerp** -para meter is niet vereist. Met deze para meter wordt het onderwerp van het e-mail bericht opgegeven.

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

### -Naar

De **to** -para meter is vereist. Met deze para meter wordt het e-mail adres van de ontvanger opgegeven. Als er meerdere ontvangers zijn, scheidt u hun adressen met een komma ( `,` ). Voer namen (optioneel) en het e-mail adres in, bijvoorbeeld `Name <someone@fabrikam.com>` .

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

### -UseSsl

Het Secure Sockets Layer-Protocol (SSL) wordt gebruikt om een beveiligde verbinding met de externe computer tot stand te brengen om e-mail te verzenden. Standaard wordt SSL niet gebruikt.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt het pad en de bestands namen van bijlagen door sluizen naar `Send-MailMessage` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

