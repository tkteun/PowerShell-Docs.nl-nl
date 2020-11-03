---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: f236956b1da5f9632ff163cbf8a818bf190fd29a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251514"
---
# Remove-CimInstance

## SAMENVATTING
Hiermee verwijdert u een CIM-exemplaar van een computer.

## SYNTAXIS

### CimInstanceComputerSet (standaard)

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QuerySessionSet

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet wordt een CIM-exemplaar van een CIM-server verwijderd. U kunt opgeven dat het CIM-exemplaar moet worden verwijderd met behulp van een CIM-instantie object dat wordt opgehaald door de `Get-CimInstance` cmdlet of door een query op te geven.

Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.
- Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .

## VOORBEELDEN

### Voor beeld 1: het CIM-exemplaar verwijderen

In dit voor beeld gebruikt u de **query** parameter om CIM-instanties te verwijderen uit de klasse met de naam **Win32_Environment** die beginnen met de teken reeks **TestVar** .

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### Voor beeld 2: het CIM-exemplaar verwijderen met een CIM instance-object

In dit voor beeld worden de CIM-exemplaar objecten die worden gefilterd door de **query** parameter opgehaald en opgeslagen in een variabele `$var` met de `Get-CimInstance` cmdlet. De inhoud van de variabele wordt vervolgens door gegeven aan de `Remove-CimInstance` cmdlet, waardoor de CIM-instanties worden verwijderd.

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## PARAMETERS

### -CimSession

De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie. Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de `New-CimSession` of cmdlets, maakt of ontvangt `Get-CimSession` . Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.

Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u een CIM-exemplaar object op dat van de CIM-server moet worden verwijderd. Het object dat aan de cmdlet is door gegeven, is niet gewijzigd, alleen het exemplaar in de CIM-server wordt verwijderd.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u de naam ruimte voor de CIM-bewerking op. De standaard naam ruimte is **root-cimv2**. U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
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
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server. U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .

Als de opgegeven waarde dubbele aanhalings tekens ( `"` ), enkele aanhalings tekens ( `'` ) of een back slash ( `\` ) bevat, moet u deze tekens weglaten door ze te voorzien van een back slash ( `\` )-teken. Als de opgegeven waarde gebruikmaakt van de WQL LIKE-operator, moet u de volgende tekens door geven tussen vier Kante haken ( `[]` ): procent ( `%` ), onderstrepings teken () `_` of vier Kante haak openen ( `[` ).

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter. De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**. De standaard waarde is **WQL**.

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

Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op. De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.

ResourceURI kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter ComputerName, waarmee een CIM-sessie wordt gemaakt met behulp van WSMan. Als u deze para meter opgeeft zonder de para meter ComputerName op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, treedt er een fout op omdat het DCOM-protocol de para meter ResourceURI niet ondersteunt.

Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
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

### Geen

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### Geen

Deze cmdlet produceert geen uitvoer.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[New-CimInstance](New-CimInstance.md)

[Get-CimInstance](get-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)

