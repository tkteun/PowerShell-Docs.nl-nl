---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250973"
---
# Get-CimClass

## SAMENVATTING
Hiermee wordt een lijst met CIM-klassen in een specifieke naam ruimte opgehaald.

## SYNTAXIS

### Computerset (standaard)

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### Sessieset

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-CimClass` cmdlet haalt een lijst met CIM-klassen op in een specifieke naam ruimte. Als er geen klassen naam is opgegeven, retourneert de cmdlet alle klassen in de naam ruimte. In tegens telling tot een CIM-instantie bevatten CIM-klassen niet de CIM-sessie of de computer naam van waaruit ze worden opgehaald.

## VOORBEELDEN

### Voor beeld 1: alle klassedefinities ophalen

In dit voor beeld worden alle klassedefinities in het **hoofd-cimv2** van de naam ruimte opgehaald.

```powershell
Get-CimClass
```

### Voor beeld 2: de klassen met een specifieke naam ophalen

In dit voor beeld worden de klassen met de woord **schijf** in hun naam opgehaald.

```powershell
Get-CimClass -ClassName *disk*
```

### Voor beeld 3: de klassen met een specifieke methode naam ophalen

In dit voor beeld worden de klassen opgehaald die beginnen met de naam **Win32** en een methode naam hebben die begint met een **term**.

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### Voor beeld 4: de klassen met een specifieke eigenschaps naam ophalen

In dit voor beeld worden de klassen opgehaald die beginnen met de naam **Win32** en beschikken over een eigenschap met de naam **handle**.

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### Voor beeld 5: de klassen met een specifieke kwalificatie naam ophalen

In dit voor beeld worden de klassen opgehaald die beginnen met de naam **Win32** , het woord **Disk** in hun namen bevatten en de opgegeven kwalificatie **koppeling** hebben.

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### Voor beeld 6: de klassedefinities van een specifieke naam ruimte ophalen

In dit voor beeld worden de klassedefinities opgehaald die het woord **net** in hun namen bevatten van de opgegeven naam ruimte **root/standardCimv2**.

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### Voor beeld 7: de klassedefinities ophalen van een externe server

In dit voor beeld worden de klassedefinities opgehaald die de woord **schijf** in hun namen bevatten van de opgegeven externe servers **Server01** en **Server02**.

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### Voor beeld 8: de klassen ophalen met behulp van een CIM-sessie

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

Met deze reeks opdrachten maakt u een sessie met meerdere computers en slaat u deze op in een variabele `$s` met de `New-CimSession` cmdlet. vervolgens worden de klassen met de `Get-CimClass` cmdlet opgehaald.

## PARAMETERS

### -CimSession

Voert de cmdlet uit in een externe sessie of op een externe computer. Voer een computer naam of een sessie object in, zoals de uitvoer van een- `New-CimSession` of- `Get-CimSession` cmdlet. De standaard waarde is de huidige sessie op de lokale computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Hiermee geeft u de naam op van de CIM-klasse waarvoor de bewerking moet worden uitgevoerd. U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ComputerName

Hiermee geeft u de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN) een NetBIOS-naam of een IP-adres opgeven.

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.

Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, biedt het gebruik van een CIM-sessie betere prestaties.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MethodName

Zoekt de klassen die een methode hebben die overeenkomt met deze naam. U kunt joker tekens gebruiken met deze para meter.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Naam ruimte

Hiermee geeft u de naam ruimte voor de CIM-bewerking op. De standaard naam ruimte is **root-cimv2**. U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer. Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.

Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PropertyName

Zoekt de klassen die een eigenschap hebben die overeenkomt met deze naam. U kunt joker tekens gebruiken met deze para meter.

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

### -Kwalificatienaam

Hiermee worden klassen gefilterd op klassen niveau kwalificatie naam. U kunt joker tekens gebruiken met deze para meter.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### Micro soft. Management. Infrastructure. CimClass

Met deze cmdlet wordt een CIM-klasse-object geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[New-CimSession](New-CimSession.md)
