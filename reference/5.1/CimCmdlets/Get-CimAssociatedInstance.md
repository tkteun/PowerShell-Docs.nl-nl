---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: 10790507b24bc4212db062589cf76d5260554b30
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251458"
---
# Get-CimAssociatedInstance

## SAMENVATTING
Hiermee haalt u de CIM-exemplaren op die zijn verbonden met een specifiek CIM-exemplaar door een koppeling.

## SYNTAXIS

### Computerset (standaard)

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### Sessieset

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-CimAssociatedInstance` cmdlet haalt de CIM-instanties op die zijn verbonden met een specifiek CIM-exemplaar, het bron exemplaar, door een koppeling.

In een koppeling heeft elk CIM-exemplaar een benoemde rol en hetzelfde CIM-exemplaar kan deel nemen aan een koppeling in verschillende rollen.

Als de para meter input object niet is opgegeven, werkt de cmdlet op een van de volgende manieren:

- Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.
- Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .

## VOORBEELDEN

### Voor beeld 1: alle gekoppelde exemplaren van een specifiek exemplaar ophalen

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

Met deze reeks opdrachten worden de exemplaren van de klasse met de naam Win32_LogicalDisk opgehaald en worden de gegevens opgeslagen in een variabele `$disk` met de naam met behulp van de `Get-CimInstance` cmdlet. Het eerste exemplaar van de logische schijf in de variabele wordt vervolgens gebruikt als het invoer object voor de `Get-CimAssociatedInstance` cmdlet om alle gekoppelde CIM-exemplaren van het opgegeven CIM-exemplaar op te halen.

### Voor beeld 2: alle gekoppelde exemplaren van een specifiek type ophalen

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

Met deze reeks opdrachten worden alle exemplaren van de klasse **Win32_LogicalDisk** opgehaald en opgeslagen in een variabele met de naam `$disk` . Het eerste exemplaar van de logische schijf in de variabele wordt vervolgens gebruikt als het invoer object voor de `Get-CimAssociatedInstance` cmdlet om alle gekoppelde exemplaren op te halen die zijn gekoppeld via de opgegeven koppelings klasse **Win32_DiskPartition**.

### Voor beeld 3: alle gekoppelde exemplaren ophalen via een kwalificatie van een specifieke klasse

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

Met deze reeks opdrachten worden de services opgehaald die afhankelijk zijn van de WMI-service en opgeslagen in een variabele met de naam `$s` . De naam van de koppelings klasse voor de **Win32_DependentService** wordt opgehaald met de `Get-CimClass` cmdlet door een **koppeling** op te geven als de kwalificatie en vervolgens met $s aan de cmdlet wordt door gegeven `Get-CimAssociatedInstance` om alle gekoppelde exemplaren van de opgehaalde Association-klasse op te halen.

## PARAMETERS

### -Association

Hiermee geeft u de naam van de koppelings klasse op. Als u deze para meter niet opgeeft, retourneert de cmdlet alle bestaande koppelings objecten van elk type.

Als klasse A bijvoorbeeld is gekoppeld aan klasse B via twee koppelingen, AB1 en AB2, dan kan deze para meter worden gebruikt om het type koppeling op te geven, hetzij AB1 of AB2.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimSession

De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie. Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie maakt of ontvangt, zoals `New-CimSession` of `Get-CimSession` . Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.

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

### -ComputerName

Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.

Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de invoer voor deze cmdlet op. U kunt deze para meter gebruiken, of u kunt de invoer door sluizen naar deze cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Alleen-alleen

Retourneert objecten waarvoor alleen sleutel eigenschappen zijn ingevuld. Dit vermindert de hoeveelheid gegevens die via het netwerk wordt overgedragen.

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

### -Naam ruimte

Hiermee geeft u de naam ruimte voor de CIM-bewerking op. De standaard naam ruimte is root-cimv2.

> [!NOTE]
> U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

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

### -ResourceUri

Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op. De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.

**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman. Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, treedt er een fout op omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.

Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultClassName

Hiermee geeft u de naam van de klasse van de gekoppelde exemplaren. Een CIM-exemplaar kan worden gekoppeld aan een of meer CIM-exemplaren. Alle bijbehorende CIM-instanties worden geretourneerd als u de naam van de resultaat klasse niet opgeeft.

Standaard is de waarde van deze para meter Null en alle bijbehorende CIM-instanties worden geretourneerd.

U kunt de koppelings resultaten filteren zodat deze overeenkomen met de naam van een specifieke klasse. Er wordt gefilterd op de-server. Als deze para meter niet wordt opgegeven, worden `Get-CIMAssociatedInstance` alle bestaande koppelingen geretourneerd. Als klasse A bijvoorbeeld is gekoppeld aan klassen B, C en D, dan kan deze para meter worden gebruikt om de uitvoer te beperken tot een specifiek type (B, C of D).

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### System. object

Met deze cmdlet wordt een object geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)
