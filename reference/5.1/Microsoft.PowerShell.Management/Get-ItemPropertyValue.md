---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250795"
---
# Get-ItemPropertyValue

## SAMENVATTING
Hiermee wordt de waarde voor een of meer eigenschappen van een opgegeven item opgehaald.

## SYNTAXIS

### Pad (standaard)

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-ItemPropertyValue` haalt de huidige waarde op voor een eigenschap die u opgeeft wanneer u de para meter *name* gebruikt, die zich bevindt in een pad dat u opgeeft met de *pad* -of *LiteralPath* -para meters.

## VOORBEELDEN

### Voor beeld 1: de waarde van de eigenschap ProductID ophalen

Met deze opdracht wordt de waarde van de eigenschap **ProductID** van het object ' \SOFTWARE\Microsoft\Windows NT\CurrentVersion ' in de Windows-register provider opgehaald.

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### Voor beeld 2: de laatste schrijf tijd van een bestand of map ophalen

Met deze opdracht wordt de waarde van de eigenschap **LastWriteTime** opgehaald, of de laatste keer dat een bestand of map is gewijzigd, in de map "C:\Users\Test\Documents\ModuleToAssembly", die in de File System Provider werkt.

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### Voor beeld 3: meerdere eigenschaps waarden van een bestand of map ophalen

Met deze opdracht worden de waarden van de **LastWriteTime** -, **CreationTime** -en **root** -eigenschappen van een map opgehaald.
De eigenschapwaarden worden geretourneerd in de volg orde waarin u de eigenschapnamen hebt opgegeven.

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## PARAMETERS

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.
Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

> [!WARNING]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten van de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Hiermee geeft u een filter op in de indeling of taal van de provider.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .

De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.
Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.
In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar het item of de items.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie about_Transactions voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### System. Boolean, System. String, System. DateTime

Met deze cmdlet wordt een object geretourneerd voor elke eigenschaps waarde van een item die wordt opgehaald.
Het object type is afhankelijk van de eigenschaps waarde die wordt opgehaald.
In een bestandssysteem station kan de cmdlet bijvoorbeeld een bestand of map retour neren.

## OPMERKINGEN

Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Voer de cmdlet uit om de providers weer te geven die beschikbaar zijn in uw sessie `Get-PSProvider` . Zie about_Providers voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-item Property](Get-ItemProperty.md)

[Wissen-item Property](Clear-ItemProperty.md)

[Kopiëren-item Property](Copy-ItemProperty.md)

[Verplaatsen-item Property](Move-ItemProperty.md)

[Nieuw-item Property](New-ItemProperty.md)

[Verwijderen-item Property](Remove-ItemProperty.md)

[Naam wijzigen-item Property](Rename-ItemProperty.md)

[Set-item Property](Set-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)
