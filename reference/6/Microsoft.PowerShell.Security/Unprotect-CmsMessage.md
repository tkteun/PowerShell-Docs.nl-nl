---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 7d33d6b5ffe9a2a4807d864c6acb2021fff88e01
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "93251423"
---
# Unprotect-CmsMessage

## SAMENVATTING
Ontsleutelt inhoud die is versleuteld met de syntaxis voor cryptografische berichten.

## SYNTAXIS

### ByWinEvent (standaard)

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### ByContent

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByPath

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Unprotect-CmsMessage` cmdlet ontsleutelt inhoud die is versleuteld met de CMS-indeling (Cryptographic Message Syntax).

De CMS-cmdlets ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor cryptografische berichten, zoals wordt beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).

De CMS-versleutelings standaard maakt gebruik van open bare-sleutel cryptografie, waarbij de sleutels worden gebruikt voor het versleutelen van inhoud (de open bare sleutel) en de sleutels die worden gebruikt voor het ontsleutelen van inhoud (de persoonlijke sleutel). Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens. Als er inhoud is versleuteld met deze open bare sleutel, kan alleen uw persoonlijke sleutel worden ontsleuteld. Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

`Unprotect-CmsMessage` ontsleutelt inhoud die is versleuteld in de CMS-indeling. U kunt deze cmdlet uitvoeren om inhoud te ontsleutelen die u hebt versleuteld door de cmdlet uit te voeren `Protect-CmsMessage` . U kunt inhoud opgeven die u wilt ontsleutelen als een teken reeks, op basis van het versleutelings gebeurtenis logboek record-ID-nummer of op pad naar de versleutelde inhoud. De `Unprotect-CmsMessage` cmdlet retourneert de ontsleutelde inhoud.

> [!NOTE]
> Deze cmdlet is alleen beschikbaar in Windows.

## VOORBEELDEN

### Voor beeld 1: een bericht ontsleutelen

In het volgende voor beeld ontsleutelt u inhoud die zich op het letterlijke pad bevindt `C:\Users\Test\Documents\PowerShell` . Voor de waarde van **de para meter** required gebruikt dit voor beeld de vinger afdruk van het certificaat dat is gebruikt om de versleuteling uit te voeren. Het gedecodeerde bericht ' Probeer de nieuwe opdracht alles afkraken ', is het resultaat.

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -EventLogRecord

Hiermee geeft u een record-ID van het gebeurtenis logboek op die een CMS-versleutelings bewerking vertegenwoordigt.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IncludeContext

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

### -LiteralPath

Hiermee geeft u het pad naar de versleutelde inhoud die u wilt ontsleutelen. In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
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
Position: 0
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

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Diagnostics. Event. Reader. EventLogRecord of System. String

U kunt een object dat versleutelde inhoud bevat door sluizen naar `Unprotect-CmsMessage` .

## UITVOER

### System. String

Het niet-versleutelde bericht.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Protect-CmsMessage](Protect-CmsMessage.md)
