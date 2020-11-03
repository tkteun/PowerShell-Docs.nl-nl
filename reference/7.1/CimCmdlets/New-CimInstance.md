---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: 7cd9d27eb291358fb4d2ee93d0a1e5ade3467249
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251517"
---
# New-CimInstance

## SAMENVATTING
Hiermee maakt u een CIM-exemplaar.

## SYNTAXIS

### ClassNameComputerSet (standaard)

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ClassNameSessionSet

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriComputerSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassComputerSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`New-CimInstance`Met de cmdlet maakt u een instantie van een CIM-klasse op basis van de klassedefinitie op de lokale computer of een externe computer. Standaard `New-CimInstance` maakt de cmdlet een instantie op de lokale computer.

## VOORBEELDEN

### Voor beeld 1: een exemplaar van een CIM-klasse maken

In dit voor beeld wordt een exemplaar gemaakt van een CIM-klasse met de naam win32_environment in de naam ruimte root/cimv2 op de computer.

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

Er wordt geen validatie aan de client zijde uitgevoerd als de klasse niet bestaat, de eigenschappen onjuist zijn of als de server de aanroep weigert. Als het exemplaar is gemaakt, wordt het zojuist gemaakte exemplaar uitgevoerd met de cmdlet.

### Voor beeld 2: een exemplaar van een CIM-klasse maken met behulp van een klassen schema

In dit voor beeld wordt een CIM-klassen object opgehaald en opgeslagen in een variabele met de naam `$class` . De inhoud van de variabele wordt vervolgens door gegeven aan de `New-CimInstance` cmdlet.

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### Voor beeld 3: een dynamisch exemplaar maken op de client

In dit voor beeld wordt een dynamisch exemplaar gemaakt van een CIM-klasse met de naam **Win32_Process** op de client computer zonder het exemplaar van de server op te halen. De nieuwe instantie wordt opgeslagen in de variabele `$a` . Dit dynamische exemplaar kan worden gebruikt om bewerkingen uit te voeren als het exemplaar met deze sleutel op de server bestaat.

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

De `Get-CimInstance` cmdlet haalt vervolgens een bepaald enkel exemplaar op. De `Invoke-CimMethod` cmdlet roept de methode **GetOwner** aan voor het opgehaalde exemplaar.

### Voor beeld 4: een exemplaar maken voor een CIM-klasse van een specifieke naam ruimte

In dit voor beeld wordt een instantie van een CIM-klasse met de naam **MSFT_Something** in de naam ruimte **root/ergens** opgehaald en opgeslagen in een variabele met de naam `$class` . De variabele wordt door gegeven aan de `New-CimInstance` cmdlet om een nieuw CIM-exemplaar te maken en de validatie aan de client zijde op het nieuwe exemplaar uit te voeren.

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

In dit voor beeld wordt met behulp van de para meter **CimClass** in plaats van de para meter **className** gecontroleerd of **Prop1** en **Prop2** werkelijk bestaan en dat de sleutels correct zijn gemarkeerd.

U kunt de para meter **ComputerName** of **CimSession** niet gebruiken met de para meter **ClientOnly** .

## PARAMETERS

### -CimClass

Hiermee geeft u een CIM-klasse-object op dat het type van het exemplaar vertegenwoordigt. Gebruik de `Get-CimClass` cmdlet om de klassen declaratie van een computer op te halen. Als u deze para meter gebruikt, worden de validaties van het schema aan de client zijde verbeterd.

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
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
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Hiermee geeft u de naam op van de CIM-klasse waarvan de bewerking een exemplaar maakt. Opmerking: u kunt het volt ooien van het tabblad gebruiken om door de lijst met klassen te bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.

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

### -ClientOnly

Geeft aan dat het exemplaar alleen wordt gemaakt in Power shell zonder naar de CIM-server te gaan. U kunt deze para meter gebruiken om een CIM-exemplaar in het geheugen te maken voor gebruik in volgende Power shell-bewerkingen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WSMan-protocol.

Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).

Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Sleutel

Hiermee geeft u de eigenschappen op die als sleutels worden gebruikt. **CimSession** en **ComputerName** kunnen niet worden gebruikt als de **sleutel** is opgegeven.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u de naam ruimte van de klasse voor het nieuwe exemplaar. De standaard naam ruimte is **root-cimv2**.
U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de CIM-server. Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt. Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.

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

Hiermee geeft u de eigenschappen van het CIM-exemplaar op met behulp van een hash-tabel (naam/waarde-paren).

Als u de para meter **CimClass** opgeeft, `New-CimInstance` voert de cmdlet een validatie van eigenschappen op de client uit om ervoor te zorgen dat de opgegeven eigenschappen consistent zijn met de klassen declaratie op de-server. Als de para meter **CimClass** niet is opgegeven, wordt de eigenschaps validatie uitgevoerd op de server.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op. De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.

**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman. Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.

Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### System. object

Met deze cmdlet wordt een object geretourneerd dat de informatie van het CIM-exemplaar bevat.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)

