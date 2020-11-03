---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 9a24cfc0e2312a5bb985084ffb9eb753f49cb8ea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251311"
---
# Get-CmsMessage

## SAMENVATTING
Hiermee wordt inhoud opgehaald die is versleuteld met de syntaxis voor cryptografische berichten.

## SYNTAXIS

### ByContent

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### ByPath

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### ByLiteralPath

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-CmsMessage` cmdlet haalt inhoud op die is versleuteld met de CMS-indeling (Cryptographic Message Syntax).

De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-indeling voor cryptografische beveiliging van berichten, zoals wordt beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).

De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel). Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens. Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld. Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

`Get-CmsMessage` Hiermee wordt inhoud opgehaald die is versleuteld in de CMS-indeling. De inhoud wordt niet ontsleuteld of beveiligd. U kunt deze cmdlet uitvoeren om inhoud op te halen die u hebt versleuteld door de cmdlet uit te voeren `Protect-CmsMessage` . U kunt inhoud opgeven die u wilt ontsleutelen als een teken reeks of op basis van het pad naar de versleutelde inhoud. U kunt de resultaten van `Get-CmsMessage` voor het `Unprotect-CmsMessage` ontsleutelen van de inhoud door geven, mits u informatie hebt over het certificaat voor document versleuteling dat is gebruikt voor het versleutelen van de inhoud.

Ondersteuning voor Linux en macOS is toegevoegd in Power shell 7,1.

## VOORBEELDEN

### Voor beeld 1: versleutelde inhoud ophalen

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

Met deze opdracht wordt versleutelde inhoud op C:\Users\Test\Documents\PowerShell\Future_Plans.txt opgehaald.

### Voor beeld 2: door pipe versleutelde inhoud naar Unprotect-CmsMessage

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

Met deze opdracht pipet u de resultaten van de `Get-CmsMessage` cmdlet van voor beeld 1 naar `Unprotect-CmsMessage` , om het bericht te ontsleutelen en te lezen in tekst zonder opmaak. In dit geval is de waarde van de para meter **aan** de waarde van de onderwerpregel van het versleutelde certificaat. Het gedecodeerde bericht ' Probeer de nieuwe opdracht alles afkraken ', is het resultaat.

## PARAMETERS

### -Inhoud

Hiermee geeft u een versleutelde teken reeks of een variabele met een versleutelde teken reeks op.

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op naar versleutelde inhoud die u wilt ophalen. In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u dit tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell niet-Inge sloten karakters mag interpreteren als escape-tekens.

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

### -Path

Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Protect-CmsMessage](Protect-CmsMessage.md)

[Beveiliging opheffen-CmsMessage](Unprotect-CmsMessage.md)

