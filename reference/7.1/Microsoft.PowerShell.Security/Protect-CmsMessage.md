---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: d7f58bb8dc496b13db264ae0bbc275723f367047
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250042"
---
# Protect-CmsMessage

## SAMENVATTING
Versleutelt inhoud met behulp van de syntaxis voor cryptografische berichten.

## SYNTAXIS

### ByContent (standaard)

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### ByPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### ByLiteralPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Protect-CmsMessage` cmdlet versleutelt inhoud door gebruik te maken van de indeling voor de syntaxis van cryptografische berichten (CMS).

De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-indeling zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652.html).

De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel). Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens. Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld. Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

Voordat u de cmdlet kunt uitvoeren `Protect-CmsMessage` , moet u een versleutelings certificaat instellen.
Om te worden herkend in Power shell, is voor versleutelings certificaten een unieke[EKU](/windows/desktop/SecCrypto/eku)-id (Extended Key Usage) vereist om ze te identificeren als certificaten voor gegevens versleuteling (zoals de Id's voor ondertekening van programma code en versleutelde e-mail). Zie voor beeld 1 in dit onderwerp voor een voor beeld van een certificaat dat kan worden gebruikt voor het versleutelen van documenten.

Ondersteuning voor Linux en macOS is toegevoegd in Power shell 7,1.

## VOORBEELDEN

### Voor beeld 1: een certificaat maken voor het versleutelen van inhoud

Voordat u de cmdlet kunt uitvoeren `Protect-CmsMessage` , moet u een versleutelings certificaat maken. Gebruik de volgende tekst om de naam op de regel onderwerp te wijzigen in uw naam, e-mail adres of andere id en sla het certificaat op in een bestand (zoals `DocumentEncryption.inf` in dit voor beeld).

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### Voor beeld 2: een bericht versleutelen dat via e-mail is verzonden

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

In het volgende voor beeld versleutelt u een bericht, ' Hallo wereld ', door het te sluizen naar de `Protect-CmsMessage` cmdlet en vervolgens het versleutelde bericht in een variabele op te slaan. De para meter **to** gebruikt de waarde van de regel onderwerp in het certificaat.

### Voor beeld 3: document versleutelings certificaten weer geven

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

Als u certificaten voor document versleuteling in de certificaat provider wilt weer geven, kunt u de dynamische para meter **DocumentEncryptionCert** van [Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)toevoegen, die alleen beschikbaar is wanneer de certificaat provider wordt geladen.

## PARAMETERS

### -Inhoud

Hiermee geeft u een **PSObject** die inhoud bevat die u wilt versleutelen. U kunt bijvoorbeeld de inhoud van een gebeurtenis bericht versleutelen en vervolgens de variabele met het bericht ( `$Event` in dit voor beeld) gebruiken als de waarde van de para meter **Content** : `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` . U kunt de cmdlet ook gebruiken `Get-Content` om de inhoud van een bestand, zoals een micro soft Word-document, op te halen en de inhoud in een variabele op te slaan die u als de waarde van de para meter **Content** gebruikt.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad naar de inhoud die u wilt versleutelen. In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Outfile

Hiermee geeft u het pad en de bestands naam van een bestand waarnaar u de versleutelde inhoud wilt verzenden.

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

### -Path

Hiermee geeft u het pad naar de inhoud die u wilt versleutelen.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naar

Hiermee geeft u een of meer CMS-bericht ontvangers, aangeduid met een van de volgende indelingen:

- Een echt certificaat (zoals opgehaald van de certificaat provider).
- Het pad naar het bestand met het certificaat.
- Pad naar een map met het certificaat.
- Vinger afdruk van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).
- De onderwerpnaam van het certificaat (dat wordt gebruikt om te zoeken in het certificaat archief).

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Beveiliging opheffen-CmsMessage](Unprotect-CmsMessage.md)

