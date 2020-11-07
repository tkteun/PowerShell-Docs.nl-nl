---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 66ecd756eccbe60003304419da64d65b6c55dd01
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347734"
---
# Set-AuthenticodeSignature

## SAMENVATTING
Hiermee voegt u een [Authenticode](/windows-hardware/drivers/install/authenticode) -hand tekening toe aan een Power shell-script of een ander bestand.

## SYNTAXIS

### ByPath (standaard)

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByContent

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Set-AuthenticodeSignature` cmdlet voegt een Authenticode-hand tekening toe aan elk bestand dat ondersteuning biedt voor het object interface pakket (SIP).

In een Power shell-script bestand krijgt de hand tekening de vorm van een tekst blok dat het einde aangeeft van de instructies die worden uitgevoerd in het script. Als er een hand tekening in het bestand is wanneer deze cmdlet wordt uitgevoerd, wordt die hand tekening verwijderd.

## VOORBEELDEN

### Voor beeld 1: een script ondertekenen met een certificaat uit het lokale certificaat archief

Met deze opdrachten wordt een certificaat voor ondertekening van programma code opgehaald van de Power shell-certificaat provider en gebruikt om een Power shell-script te ondertekenen.

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

De eerste opdracht gebruikt de `Get-ChildItem` cmdlet en de Power shell-certificaat provider om de certificaten op te halen in de `Cert:\CurrentUser\My` submap van het certificaat archief. Het `Cert:` station is het station dat door de certificaat provider wordt weer gegeven. De **CodeSigningCert** -para meter, die alleen wordt ondersteund door de certificaat provider, beperkt de certificaten die worden opgehaald tot die met de instantie voor het ondertekenen van programma code. De opdracht slaat het resultaat op in de `$cert` variabele.

Met de tweede opdracht wordt de `Set-AuthenticodeSignature` cmdlet gebruikt om het script te ondertekenen `PSTestInternet2.ps1` . De para meter **filepath** wordt gebruikt om de naam van het script en de para meter **certificaat** op te geven om op te geven dat het certificaat is opgeslagen in de `$cert` variabele.

> [!NOTE]
> Het gebruik van de para meter **CodeSigningCert** met `Get-ChildItem` alleen certificaten met de instantie voor ondertekening van programma code en een persoonlijke sleutel bevatten. Als er geen persoonlijke sleutel is, kunnen de certificaten niet worden gebruikt voor het ondertekenen.

### Voor beeld 2: een script ondertekenen met een certificaat uit een PFX-bestand

Deze opdrachten gebruiken de `Get-PfxCertificate` cmdlet om een certificaat voor ondertekening van programma code te laden. Vervolgens gebruikt u het om een Power shell-script te ondertekenen.

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

De eerste opdracht gebruikt de `Get-PfxCertificate` cmdlet om het C:\Test\MySign.pfx-certificaat in de `$cert` variabele te laden.

De tweede opdracht wordt gebruikt `Set-AuthenticodeSignature` om het script te ondertekenen. De **filepath** para meter van het `Set-AuthenticodeSignature` pad naar het script bestand dat wordt ondertekend en de para meter **CERT** geeft de `$cert` variabele met het certificaat door `Set-AuthenticodeSignature` .

Als het certificaat bestand is beveiligd met een wacht woord, vraagt Power shell u om het wacht woord.

### Voor beeld 3: een hand tekening toevoegen die de basis instantie bevat

Met deze opdracht wordt een digitale hand tekening toegevoegd die de basis instantie in de vertrouwens keten bevat en is ondertekend door een tijds tempel server van derden.

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

De opdracht gebruikt de **filepath** -para meter om het script op te geven dat wordt ondertekend en de para meter **certificaat** om het certificaat op te geven dat is opgeslagen in de `$cert` variabele. De para meter **IncludeChain** wordt gebruikt voor het opnemen van alle hand tekeningen in de vertrouwens keten, met inbegrip van de basis certificerings instantie. De para meter **TimeStampServer** wordt ook gebruikt om een tijds tempel toe te voegen aan de hand tekening.
Zo voor komt u dat het script mislukt wanneer het certificaat verloopt.

## PARAMETERS

### -Certificaat

Hiermee geeft u het certificaat op dat wordt gebruikt voor het ondertekenen van het script of bestand. Voer een variabele in die een object opslaat dat het certificaat vertegenwoordigt, of een expressie die het certificaat ophaalt.

Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station. Als het certificaat ongeldig is of geen `code-signing` instantie heeft, mislukt de opdracht.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u het pad naar een bestand dat wordt ondertekend.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

Hiermee kan de cmdlet een hand tekening toevoegen aan een alleen-lezen bestand. Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HashAlgorithm

Hiermee geeft u het hash-algoritme op dat door Windows wordt gebruikt voor het berekenen van de digitale hand tekening voor het bestand.

Voor Power Shell 3,0 is de standaard waarde SHA256, het standaard hash-algoritme voor Windows. Voor Power Shell 2,0 is de standaard SHA1. Bestanden die zijn ondertekend met een ander hash-algoritme, worden mogelijk niet herkend op andere systemen. Welke algoritmen worden ondersteund, is afhankelijk van de versie van het besturings systeem.

Zie [HashAlgorithmName struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)voor een lijst met mogelijke waarden.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeChain

Hiermee wordt bepaald welke certificaten in de certificaat vertrouwens keten zijn opgenomen in de digitale hand tekening.
**NotRoot** is de standaard instelling.

Geldige waarden zijn:

- Ondertekenaar: bevat alleen het certificaat van de ondertekenaar.
- NotRoot: bevat alle certificaten in de certificaat keten, met uitzonde ring van de basis certificerings instantie.
- Alle: bevat alle certificaten in de certificaat keten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimestampServer

Gebruikt de opgegeven tijds tempel server om een tijds tempel toe te voegen aan de hand tekening. Typ de URL van de tijds tempel server als een teken reeks.

Het tijds tempel vertegenwoordigt de exacte tijd dat het certificaat is toegevoegd aan het bestand. Een tijds tempel voor komt dat het script mislukt als het certificaat verloopt omdat gebruikers en Program ma's kunnen controleren of het certificaat geldig is op het moment van ondertekening.

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

### -LiteralPath

Hiermee geeft u het pad naar een bestand dat wordt ondertekend. In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

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

### -SourcePathOrExtension

Het pad naar het bestand of het bestands type van de inhoud waarvoor de digitale hand tekening is toegevoegd. Deze para meter wordt gebruikt met **inhoud** waar bestands inhoud als een byte matrix wordt door gegeven.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Inhoud

Inhoud van een bestand als een byte matrix waarvoor de digitale hand tekening is toegevoegd. Deze para meter moet worden gebruikt met de para meter **SourcePathOrExtension** . De inhoud van het bestand moet de Unicode-indeling (UTF-16LE) hebben.

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

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

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die het bestandspad bevat door sluizen naar `Set-AuthenticodeSignature` .

## UITVOER

### System. Management. Automation. Signature

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

## GERELATEERDE KOPPELINGEN

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Get-pfx](Get-PfxCertificate.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
