---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 691ba3396fee5a32e81ade5979cb5a5ac4bd88eb
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251638"
---
# Invoke-CimMethod

## SAMENVATTING
Hiermee wordt een methode van een CIM-klasse aangeroepen.

## SYNTAXIS

### ClassNameComputerSet (standaard)

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ResourceUriComputerSet

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimInstanceComputerSet

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimClassComputerSet

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QueryComputerSet

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QuerySessionSet

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Invoke-CimMethod` cmdlet roept een methode aan van een CIM-klasse of CIM-exemplaar met behulp van de naam/waarde-paren die zijn opgegeven met de para meter **Arguments** .

Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.
- Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .

Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.
- Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter **CimSession** of **ComputerName** . Dit is geen gebruikelijk scenario.

## VOORBEELDEN

### Voor beeld 1: een methode aanroepen

In dit voor beeld wordt de methode **Terminate** van de klasse **Win32_Process** aangeroepen.

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### Voor beeld 2: een methode aanroepen met een CIM instance-object

In dit voor beeld wordt het CIM-exemplaar object opgehaald en opgeslagen in een variabele `$x` met de naam met behulp van de `Get-CimInstance` cmdlet. De inhoud van de variabele wordt vervolgens gebruikt als de **input object** voor de `Invoke-CimMethod` cmdlet. De methode **GetOwner** wordt aangeroepen voor de **CimInstance**.

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### Voor beeld 3: een statische methode aanroepen met behulp van argumenten

In dit voor beeld wordt de **Create** -methode aangeroepen met de para meter **Arguments** .

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### Voor beeld 4: validatie aan de client zijde

In dit voor beeld wordt validatie aan de client zijde uitgevoerd voor de methode **xyz** door een **CimClass** -object door te geven aan `Invoke-CimMethod` .

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## PARAMETERS

### -Argumenten

Hiermee geeft u de para meters op die worden door gegeven aan de aangeroepen methode. Geef de waarden voor deze para meter op als naam/waarde-paren, opgeslagen in een hash-tabel. De volg orde van de ingevoerde waarden is niet belang rijk.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimClass

Hiermee geeft u een CIM-klasse-object op dat een CIM-klassen definitie op de server vertegenwoordigt. Gebruik deze para meter bij het aanroepen van een statische methode van een klasse.

U kunt de `Get-CimClass` cmdlet gebruiken om een klassedefinitie van de server op te halen.

Als u deze para meter gebruikt, worden de validaties van het schema aan de client zijde verbeterd.

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimSession

De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie. Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de `New-CimSession` of cmdlets, maakt of ontvangt `Get-CimSession` . Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Hiermee geeft u de naam op van de CIM-klasse waarvoor de bewerking moet worden uitgevoerd. Deze para meter wordt alleen gebruikt voor statische methoden. U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.

Wanneer u deze para meter gebruikt, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol. Anders voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Verbinding maken met behulp van een CIM-sessie voor betere prestaties wanneer er meerdere bewerkingen worden uitgevoerd op dezelfde computer.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u een CIM-exemplaar object op dat als invoer moet worden gebruikt om een methode aan te roepen. Deze para meter kan alleen worden gebruikt voor het aanroepen van instantie-methoden. Voor het aanroepen van klasse statische methoden gebruikt u de para meter **Class** of de para meter **CimClass** .

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MethodName

Hiermee geeft u de naam op van de CIM-methode die moet worden aangeroepen. Deze para meter is verplicht en mag niet null of leeg zijn. Voor het aanroepen van een statische methode van een CIM-klasse gebruikt u de **className** of de **CimClass** -para meter.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u de naam ruimte voor de CIM-bewerking op. De standaard naam ruimte is **root-cimv2**. U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer. Standaard is de waarde 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.

Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de standaard time-out voor het opnieuw proberen van drie minuten, kunnen netwerk storingen die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server. Een methode wordt aangeroepen voor de instanties die zijn ontvangen als resultaat van de query. U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .

Als de opgegeven waarde dubbele aanhalings tekens ( `"` ), enkele aanhalings tekens ( `'` ) of een back slash ( `\` ) bevat, moet u deze tekens weglaten door ze te voorzien van een back slash ( `\` )-teken. Als de opgegeven waarde gebruikmaakt van de WQL LIKE-operator, moet u de volgende tekens door geven tussen vier Kante haken ( `[]` ): procent ( `%` ), onderstrepings teken () `_` of vier Kante haak openen ( `[` ).

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter. De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**.

De standaard waarde is **WQL**.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.
De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.

**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.

Wanneer u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of wanneer u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, wordt er een fout melding weer geven. Het DCOM-protocol biedt geen ondersteuning voor de para meter **ResourceURI** .

Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### CIM-klasse

Met deze cmdlet wordt een CIM-klasse geaccepteerd als invoer object.

### CIM-instantie

Met deze cmdlet wordt een CIM-exemplaar geaccepteerd als invoer object.

## UITVOER

### System. Management. Automation. PSCustomObject

Met deze cmdlet wordt een object geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

