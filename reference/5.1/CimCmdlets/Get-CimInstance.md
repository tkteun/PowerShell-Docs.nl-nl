---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 468b0e62925774fb838263b9bd9aea6a74151b5f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251460"
---
# Get-CimInstance

## SAMENVATTING
Hiermee worden de CIM-exemplaren van een klasse opgehaald van een CIM-server.

## SYNTAXIS

### ClassNameComputerSet (standaard)

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QuerySessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### CimInstanceComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### ResourceUriComputerSet

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QueryComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Get-CimInstance` cmdlet haalt de CIM-exemplaren van een klasse van een CIM-server op. U kunt de naam van de klasse of een query voor deze cmdlet opgeven. Deze cmdlet retourneert een of meer CIM-instantie objecten die een moment opname van de CIM-exemplaren vertegenwoordigen die aanwezig zijn op de CIM-server.

Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.
- Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .

Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.
- Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter CimSession of **ComputerName** .

## VOORBEELDEN

### Voor beeld 1: de CIM-instanties van een opgegeven klasse ophalen

In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_Process** opgehaald.

```powershell
Get-CimInstance -ClassName Win32_Process
```

### Voor beeld 2: een lijst met naam ruimten van een WMI-server ophalen

In dit voor beeld wordt een lijst met naam ruimten in de **hoofd** naam ruimte op een WMI-server opgehaald.

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### Voor beeld 3: instanties van een klasse die is gefilterd, ophalen met behulp van een query

In dit voor beeld worden alle CIM-instanties opgehaald die beginnen met de letter **P** van een klasse met de naam **Win32_Process** met behulp van de query die is opgegeven door een **query** parameter.

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### Voor beeld 4: instanties van een klasse die worden gefilterd, ophalen met behulp van een klassen naam en een filter expressie

In dit voor beeld worden alle CIM-instanties opgehaald die beginnen met de letter **P** van een klasse met de naam **Win32_Process** met behulp van de para meter filter.

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### Voor beeld 5: de CIM-instanties ophalen waarvoor alleen sleutel eigenschappen zijn ingevuld

In dit voor beeld wordt een nieuw CIM-exemplaar in het geheugen gemaakt voor een klasse met de naam **Win32_Process** met de sleutel eigenschap `@{ "Handle"=0 }` en wordt deze opgeslagen in een variabele met de naam `$x` . De variabele wordt door gegeven als een CIM-exemplaar aan de `Get-CimInstance` cmdlet om een bepaald exemplaar op te halen.

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### Voor beeld 6: CIM-instanties ophalen en opnieuw gebruiken

In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_Process** opgehaald en opgeslagen in de variabelen `$x` en `$y` . De variabele `$x` wordt vervolgens opgemaakt in een tabel die alleen de eigenschappen **name** en **KernelModeTime** bevat, de tabel die is ingesteld op **AutoSize**.

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### Voor beeld 7: CIM-instanties ophalen van een externe computer

In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_ComputerSystem** opgehaald van de externe computers met de naam **Server01** en **Server02**.

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### Voor beeld 8: alleen de sleutel eigenschappen ophalen, in plaats van alle eigenschappen

In dit voor beeld worden alleen de sleutel eigenschappen opgehaald, waardoor de grootte van het object en het netwerk verkeer wordt verminderd.

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### Voor beeld 9: er wordt slechts een subset van eigenschappen opgehaald, in plaats van alle eigenschappen

In dit voor beeld wordt slechts een subset van eigenschappen opgehaald, waardoor de grootte van het object en het netwerk verkeer wordt verminderd.

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

Het exemplaar dat is opgehaald met de para meter **Property** kan worden gebruikt om andere CIM-bewerkingen uit te voeren, bijvoorbeeld `Set-CimInstance` of `Invoke-CimMethod` .

### Voor beeld 10: het CIM-exemplaar met behulp van CIM-sessie ophalen

In dit voor beeld wordt een CIM-sessie gemaakt op de computers met de naam **Server01** en **Server02** met behulp van de- `New-CimSession` cmdlet en worden de sessie gegevens opgeslagen in een variabele met de naam `$s` . De inhoud van de variabele wordt vervolgens door gegeven aan met `Get-CimInstance` behulp van de para meter **CimSession** om de CIM-exemplaren van de klasse met de naam **Win32_ComputerSystem** op te halen.

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## PARAMETERS

### -CimSession

Hiermee geeft u de CIM-sessie op die moet worden gebruikt voor deze cmdlet. Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de- `New-CimSession` of-cmdlets, maakt of ontvangt `Get-CimSession` . Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Hiermee geeft u de naam op van de CIM-klasse waarvoor de CIM-exemplaren moeten worden opgehaald. U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven. Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.

Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, kunt u verbinding maken met behulp van een CIM-sessie voor betere prestaties.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u een WHERE-component moet worden gebruikt als een filter. Geef de component op in de **WQL** of de **CQL** -query taal. Neem het `WHERE` sleutel woord niet op in de waarde van de para meter.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u een CIM-exemplaar object op dat moet worden gebruikt als invoer.

Als u al met een CIM-instantie object werkt, kunt u deze para meter gebruiken om het object CIM-exemplaar door te geven om de meest recente moment opname van de CIM-server op te halen. Wanneer u een CIM-instantie object als invoer `Get-CimInstance` doorgeeft, retourneert het object van de server met behulp van een CIM-bewerking ophalen in plaats van een opsommings-of query bewerking. Het gebruik van een CIM-bewerking ophalen is efficiënter dan wanneer alle instanties worden opgehaald en vervolgens worden gefilterd.

Als de CIM-klasse de Get-bewerking niet implementeert, wordt er een fout geretourneerd door de para meter **input object** op te geven.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Alleen-alleen

Geeft aan dat alleen objecten met de sleutel eigenschappen worden geretourneerd. Het opgeven van de para meter **alleen** waarde beperkt de hoeveelheid gegevens die via het netwerk worden overgedragen.

Gebruik de **alleen** -sleutel parameter alleen een klein deel van het object dat kan worden gebruikt voor andere bewerkingen, zoals de-of- `Set-CimInstance` `Get-CimAssociatedInstance` cmdlets.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u de naam ruimte van de CIM-klasse op.

De standaard naam ruimte is **root-cimv2**. U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### -Eigenschap

Hiermee geeft u een set exemplaar eigenschappen op die moeten worden opgehaald. Gebruik deze para meter als u de grootte van het geretourneerde object wilt verkleinen, hetzij in het geheugen of via het netwerk. Het geretourneerde object bevat ook de sleutel eigenschappen, zelfs als u deze niet hebt weer gegeven met de para meter **Property** . Andere eigenschappen van de klasse zijn aanwezig, maar ze worden niet ingevuld.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server. Als de opgegeven waarde dubbele aanhalings tekens `"` , enkele aanhalings tekens `'` of een back slash bevat `\` , moet u deze tekens weglaten door ze voor te plaatsen met het back slash-teken. Als de opgegeven waarde gebruikmaakt van de WQL **like** -operator, moet u de volgende tekens door geven tussen vier Kante haken `[]` : percentage `%` , onderstrepings teken `_` of vier kant haakje openen `[` .

U kunt geen meta gegevens query gebruiken om een lijst met klassen of een gebeurtenis query op te halen. Als u een lijst met klassen wilt ophalen, gebruikt u de `Get-CimClass` cmdlet. Gebruik de cmdlet om een gebeurtenis query op te halen `Register-CimIndicationEvent` .

U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .

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

Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter. De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**. De standaard waarde is **WQL**.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
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

**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman. Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.

Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Recente

Geeft aan dat de instanties van een klasse worden geretourneerd zonder de exemplaren van onderliggende klassen op te nemen. De cmdlet retourneert standaard de exemplaren van een klasse en de onderliggende klassen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Management. Infrastructure. CimInstance

Deze cmdlet accepteert een invoer object dat is opgegeven met de para meter input object.

## UITVOER

### Micro soft. Management. Infrastructure. CimInstance

Met deze cmdlet worden een of meer CIM-instantie objecten geretourneerd die een moment opname van de CIM-exemplaren op de CIM-server vertegenwoordigen.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Format-Table](../microsoft.powershell.utility/format-table.md)

[Get-CimAssociatedInstance](Get-CimAssociatedInstance.md)

[Get-CimClass](Get-CimClass.md)

[Invoke-CimMethod](invoke-cimmethod.md)

[New-CimInstance](New-CimInstance.md)

[REGI ster-CimIndicationEvent](Register-CimIndicationEvent.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
