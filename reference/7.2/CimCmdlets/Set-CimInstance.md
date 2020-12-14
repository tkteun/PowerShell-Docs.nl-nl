---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 041ef2d5b5541c250b98003099fe58018df155c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705390"
---
# Set-CimInstance

## SAMENVATTING
Wijzigt een CIM-exemplaar op een CIM-server door het aanroepen van de methode ModifyInstance van de CIM-klasse.

## SYNTAXIS

### CimInstanceComputerSet (standaard)

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QuerySessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet wordt een CIM-exemplaar op een CIM-server gewijzigd.

Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.
- Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .

Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.
- Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter **CimSession** of **ComputerName** . Dit is niet zeer gebruikelijk.

## VOORBEELDEN

### Voor beeld 1: het CIM-exemplaar instellen

In dit voor beeld wordt de waarde van de eigenschap **VariableValue** ingesteld op **ABCD** met behulp van de **query** parameter. U kunt exemplaren die overeenkomen met een WQL-query (Windows Management Instrumentation Query Language) wijzigen.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### Voor beeld 2: de CIM-instantie-eigenschap instellen met behulp van de pijp lijn

In dit voor beeld wordt het CIM-exemplaar object opgehaald dat is gefilterd door de **query** parameter met behulp van de `Get-CimInstance` cmdlet. `Set-CimInstance`Met de cmdlet wordt de waarde van de eigenschap **VariableValue** gewijzigd in **ABCD**.

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### Voor beeld 3: de eigenschap CIM-exemplaar instellen met behulp van een invoer object

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

In dit voor beeld worden de CIM-exemplaar objecten die worden gefilterd door de query parameter in naar een variabele `$x` die `Get-CimInstance` wordt gebruikt, opgehaald en wordt de inhoud van de variabele door gegeven aan de `Set-CimInstance` cmdlet. `Set-CimInstance` wijzigt vervolgens de eigenschap **VariableValue** in **eenwaarde**. Omdat de para meter **PassThru** wordt gebruikt, wordt in dit voor beeld een gewijzigd CIM-exemplaar object geretourneerd.

### Voor beeld 4: de eigenschap CIM-exemplaar instellen

In dit voor beeld wordt het CIM-exemplaar object dat in de **query** parameter is opgegeven, opgehaald in een variabele `$x` met de `Get-CimInstance` cmdlet en wordt de waarde van de eigenschap **VariableValue** van het object gewijzigd in gewijzigd. Het object CIM-exemplaar wordt vervolgens opgeslagen met de `Set-CimInstance` cmdlet.
Omdat de para meter **PassThru** wordt gebruikt, wordt in dit voor beeld een gewijzigd CIM-exemplaar object geretourneerd.

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### Voor beeld 5: de lijst met CIM-instanties weer geven die u kunt wijzigen met behulp van WhatIf

In dit voor beeld wordt gebruikgemaakt van de algemene para meter **WhatIf** om op te geven dat de wijziging niet moet worden uitgevoerd, maar alleen output wat er zou gebeuren als deze is uitgevoerd.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### Voor beeld 6: het CIM-exemplaar instellen na bevestiging van de gebruiker

In dit voor beeld wordt de gemeen schappelijke **para meter** gebruikt om op te geven dat de wijziging alleen moet worden uitgevoerd na de bevestiging van de gebruiker.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### Voor beeld 7: het gemaakte CIM-exemplaar instellen

In dit voor beeld wordt een CIM-exemplaar met de opgegeven eigenschappen gemaakt met de `New-CimInstance` cmdlet en wordt de inhoud ervan opgehaald in een variabele `$x` . De variabele wordt vervolgens door gegeven aan de `Set-CimInstance` cmdlet, waarmee de waarde van de eigenschap **VariableValue** wordt gewijzigd in **eenwaarde**.
Omdat de para meter **PassThru** wordt gebruikt, wordt in dit voor beeld een gewijzigd CIM-exemplaar object geretourneerd.

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## PARAMETERS

### -CimSession

De cmdlets worden uitgevoerd op een externe computer. Voer een computer naam of een sessie object in, zoals de uitvoer van een- `New-CimSession` of- `Get-CimSession` cmdlet.

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

Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.

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

Hiermee geeft u een CIM-exemplaar object op dat moet worden gebruikt als invoer.

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

### -Naam ruimte

Hiermee geeft u de naam ruimte voor de CIM-bewerking op. De standaard naam ruimte is root-cimv2. U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
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

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Eigenschap

Hiermee geeft u de eigenschappen van het CIM-exemplaar op als een hash-tabel (met behulp van naam/waarde-paren). Alleen de eigenschappen die zijn opgegeven met deze para meter, worden gewijzigd. Andere eigenschappen van het CIM-exemplaar worden niet gewijzigd.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server om CIM-instanties op te halen waarop de cmdlet moet worden uitgevoerd. U kunt het query dialect opgeven met behulp van de para meter QueryDialect.

Als de opgegeven waarde dubbele aanhalings tekens ( `"` ), enkele aanhalings tekens ( `'` ) of een back slash ( `\` ) bevat, moet u deze tekens weglaten door ze te voorzien van een back slash ( `\` )-teken. Als de opgegeven waarde gebruikmaakt van de WQL **like** -operator, moet u de volgende tekens door geven tussen vier Kante haken ( `[]` ): procent ( `%` ), onderstrepings teken () `_` of vier Kante haak openen ( `[` ).

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op. De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.

ResourceURI kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter ComputerName, waarmee een CIM-sessie wordt gemaakt met behulp van WSMan. Als u deze para meter opgeeft zonder de para meter ComputerName op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter ResourceURI niet ondersteunt.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Micro soft. Management. Infrastructure. CimInstance

## UITVOER

### Micro soft. Management. Infrastructure. CimInstance

Wanneer de para meter **PassThru** is opgegeven, retourneert deze cmdlet een gewijzigd object CIM-exemplaar.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimInstance](get-ciminstance.md)

[New-CimInstance](New-CimInstance.md)

[Remove-CimInstance](remove-ciminstance.md)

