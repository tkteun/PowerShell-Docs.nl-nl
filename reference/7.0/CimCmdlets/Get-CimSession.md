---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: dbbbb352d1b3af8a0f05d2805fb42b7bb3ed27d3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249644"
---
# Get-CimSession

## SAMENVATTING
Hiermee haalt u de CIM-sessie objecten op uit de huidige sessie.

## SYNTAXIS

### ComputerNameSet (standaard)

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### SessionIdSet

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### InstanceIdSet

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### Naamset

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## BESCHRIJVING

Standaard worden alle CIM-sessies die zijn gemaakt in de huidige Power shell-sessie door de cmdlet opgehaald. U kunt de para meters van gebruiken `Get-CimSession` om de sessies op te halen voor bepaalde computers, of u kunt sessies identificeren met hun namen of andere id's. `Get-CimSession` ontvangt geen CIM-sessies die zijn gemaakt in andere Power shell-sessies of die zijn gemaakt op andere computers.

Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie over CIM-sessies.

## VOORBEELDEN

### Voor beeld 1: CIM-sessies ophalen uit de huidige Power shell-sessie

In dit voor beeld worden CIM-sessies gemaakt met [New-CimSession](New-CimSession.md)en worden vervolgens de CIM-sessies opgehaald met `Get-CimSession` .

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Voor beeld 2: de CIM-sessies op een specifieke computer ophalen

In dit voor beeld worden de CIM-sessies opgehaald die zijn verbonden met de computer met de naam **Server02**.

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Voor beeld 3: een lijst met CIM-sessies ophalen en vervolgens de lijst opmaken

In dit voor beeld worden alle CIM-sessies in de huidige Power shell-sessie opgehaald en wordt een tabel met alleen de eigenschappen **ComputerName** en **InstanceId** weer gegeven.

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### Voor beeld 4: alle CIM-sessies met specifieke namen ophalen

In dit voor beeld worden alle CIM-sessies opgehaald die namen hebben die met **Serviceart** beginnen.

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Voor beeld 5: een specifieke CIM-sessie ophalen

In dit voor beeld wordt de CIM-sessie met de **id** 2 opgehaald.

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## PARAMETERS

### -ComputerName

Hiermee geeft u de naam op van de computer waarop CIM-sessies moeten worden aangesloten. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

Hiermee geeft u de id op van de CIM-sessie die u wilt ophalen. Voor meerdere Id's gebruikt u komma's om de Id's van elkaar te scheiden of gebruikt u de operator Range ( `..` ) om een reeks id's op te geven. Een **id** is een geheel getal dat de CIM-sessie in de huidige Power shell-sessie uniek identificeert.

Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)voor meer informatie over de operator Range.

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-Id's op van de CIM-sessie die u wilt ophalen.

**InstanceId** is een GUID (Globally Unique Identifier) waarmee een CIM-sessie uniek wordt geïdentificeerd. De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.

De **InstanceId** wordt opgeslagen in de eigenschap **InstanceId** van het object dat een CIM-sessie vertegenwoordigt.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee worden een of meer CIM-sessies opgehaald die de opgegeven beschrijvende namen bevatten. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### Micro soft. Management. Infrastructure. CimSession

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Format-Table](../microsoft.powershell.utility/format-table.md)

[New-CimSession](New-CimSession.md)

[Remove-CimSession](remove-cimsession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
