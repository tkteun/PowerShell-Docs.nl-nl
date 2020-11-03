---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 1be3034b1fb44b1dce1a592ea5a2c1622b54d28f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250499"
---
# Get-PfxCertificate

## SAMENVATTING
Haalt informatie op over PFX-certificaat bestanden op de computer.

## SYNTAXIS

### ByPath (standaard)

```
Get-PfxCertificate [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-PfxCertificate -LiteralPath <String[]> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-PfxCertificate` cmdlet haalt een object op dat staat voor elk opgegeven pfx-certificaat bestand.
Een PFX-bestand bevat zowel het certificaat als een persoonlijke sleutel.

## VOORBEELDEN

### Voor beeld 1: een PFX-certificaat ophalen

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

Met deze opdracht wordt informatie opgehaald over het bestand test. pfx op het systeem.

### Voor beeld 2: een PFX-certificaat ophalen van een externe computer

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

Met deze opdracht wordt een PFX-certificaat bestand opgehaald van de externe computer Server01. Het gebruikt `Invoke-Command` om een `Get-PfxCertificate` opdracht op afstand uit te voeren.

Wanneer het PFX-certificaat bestand niet met een wacht woord is beveiligd, moet de waarde van de **authenticatie** parameter van `Invoke-Command` CredSSP zijn.

## PARAMETERS

### -FilePath

Hiermee geeft u het volledige pad naar het PFX-bestand van het beveiligde bestand. Als u een waarde voor deze para meter opgeeft, hoeft u niet `-FilePath` op de opdracht regel te typen.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Het volledige pad naar het PFX-bestand van het beveiligde bestand. In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die een bestandspad bevat, door sluizen naar `Get-PfxCertificate` .

## UITVOER

### System. Security. Cryptography. X509Certificates. X509Certificate2

`Get-PfxCertificate` retourneert een object voor elk certificaat dat wordt opgehaald.

## OPMERKINGEN

Wanneer u de `Invoke-Command` cmdlet gebruikt om een `Get-PfxCertificate` opdracht extern uit te voeren en het pfx-certificaat bestand niet met een wacht woord is beveiligd, moet de waarde van de **authenticatie** parameter van `Invoke-Command` CredSSP zijn.

## GERELATEERDE KOPPELINGEN

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)
