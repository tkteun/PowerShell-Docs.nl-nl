---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251505"
---
# New-PSWorkflowExecutionOption

## SAMENVATTING

Hiermee maakt u een-object dat sessie configuratie opties bevat voor werk stroom sessies.

## SYNTAXIS

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

De `New-PSWorkflowExecutionOption` cmdlet maakt een object dat geavanceerde opties bevat voor werk stroom sessie configuraties. Dit zijn de sessie configuraties die zijn ontworpen voor het uitvoeren van Windows Power shell workflow-werk stromen.

U kunt het **New psworkflowexecutionoption** -object gebruiken dat `New-PSWorkflowExecutionOption` wordt gegenereerd als de waarde van de para meter **SessionTypeOption** van cmdlets waarmee een sessie configuratie wordt gemaakt of gewijzigd, zoals de- `Register-PSSessionConfiguration` en- `Set-PSSessionConfiguration` cmdlets.

Elke para meter van de `New-PSWorkflowExecutionOption` cmdlet vertegenwoordigt een eigenschap van het werk stroom sessie configuratie optie object dat door de cmdlet wordt geretourneerd. Als u een para meter weglaat, maakt de cmdlet het object met een standaard waarde voor de eigenschap.

De `New-PSWorkflowExecutionOption` cmdlet maakt deel uit van de werk stroom functie van Windows Power shell.

U kunt ook algemene werk stroom parameters toevoegen aan deze opdracht. Zie [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)voor meer informatie over algemene werk stroom parameters.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een werk stroom opties-object maken

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

Deze opdracht gebruikt de `New-PSWorkflowExecutionOption` cmdlet om de **MaxSessionsPerWorkflow** -waarde te verhogen tot 10 en de **MaxDisconnectedSessions** -waarde te verlagen tot 200.

De uitvoer toont het object dat door de cmdlet wordt geretourneerd.

### Voor beeld 2: een werk stroom opties-object gebruiken

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

Met de eerste twee opdrachten wordt een nieuw sessie configuratie object gemaakt en geregistreerd.

De derde opdracht gebruikt de `Get-PSSessionConfiguration` cmdlet voor het ophalen van de ITWorkflows-sessie configuratie en de `Format-List` om alle eigenschappen van de sessie configuratie in een lijst weer te geven. In de uitvoer ziet u dat de werk stroom opties in de sessie configuratie. De sessie configuratie heeft met name een eigenschap **MaxSessionsPerWorkflow** met de waarde 10 en een eigenschap **MaxDisconnectedSessions** met de waarde 200.

## PARAMETERS

### -ActivityProcessIdleTimeoutSec

Hiermee wordt bepaald hoe lang elk hostproces voor activiteiten wordt behouden nadat het proces inactief wordt. Wanneer het interval is verlopen, wordt het proces gesloten.

Voer een waarde in seconden in. De standaard waarde is 60.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowedActivity

Hiermee geeft u de activiteiten op die in de sessie mogen worden uitgevoerd.

Voer namen van naam ruimten in die in aanmerking komen, zoals `Microsoft.Powershell.HyperV.Activities.*` .
Joker tekens worden ondersteund. De standaard waarde, **PSDefaultActivities** , bevat de ingebouwde Windows Workflow Foundation activiteiten en de activiteiten die de kern-cmdlets van Windows Power shell vertegenwoordigen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableValidation

Hiermee wordt gecontroleerd of alle werk stroom activiteiten in de sessie zijn opgenomen in de lijst met toegestane activiteiten.

De standaard waarde is True. Als u validatie wilt uitschakelen, gebruikt u de volgende opdracht indeling: `-EnableValidation:$false` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxActivityProcesses

Hiermee geeft u het maximum aantal processen op dat in de sessie kan worden gemaakt voor de ondersteuning van werk stroom activiteiten. De standaard waarde is 5.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxConnectedSessions

Hiermee geeft u het maximum aantal externe sessies met een operationele status op. Dit quotum wordt toegepast op sessies die zijn verbonden met alle externe knoop punten (doel computers). De standaardwaarde is 100.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxDisconnectedSessions

Hiermee geeft u het maximum aantal externe sessies in de status niet verbonden. Dit quotum wordt toegepast op sessies die zijn verbonden met alle externe knoop punten (doel computers). De standaardwaarde is 1000.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxPersistenceStoreSizeGB

Hiermee geeft u de maximale grootte, in gigabytes, op van de persistentie opslag die is toegewezen aan werk stromen die worden uitgevoerd in de sessie. Wanneer de grootte wordt overschreden, wordt de persistentie opslag uitgebreid om alle persistente gegevens op te slaan, maar er wordt een waarschuwing weer gegeven en er wordt een bericht naar het gebeurtenis logboek van de werk stroom geschreven. De standaardwaarde is 10.

Het persistentie archief bevat gegevens voor alle werk stroom taken. Met de mogelijkheid om gegevens op te slaan, kunnen de taken worden hervat zonder dat de status verloren gaat.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxRunningWorkflows

Hiermee geeft u op dat het maximum aantal werk stromen dat gelijktijdig kan worden uitgevoerd in de sessie.
De standaardwaarde is 30.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerRemoteNode

Hiermee geeft u het maximum aantal sessies op dat kan worden verbonden met elk extern knoop punt (doel computer). De standaard waarde is 5.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerWorkflow

Hiermee geeft u het maximum aantal sessies op dat kan worden gemaakt ter ondersteuning van elke werk stroom. De standaard waarde is 5.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutOfProcessActivity

Hiermee wordt bepaald welke toegestane activiteiten (opgegeven met de para meter **AllowedActivities** ) out-of-process worden uitgevoerd. De standaard waarde is **InlineScript**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistencePath

Hiermee geeft u de locatie op de schijf waarop de werk stroom status en-gegevens worden opgeslagen. Door de werk stroom status en-gegevens op te slaan, kunnen werk stromen worden onderbroken en hervat, en kunnen er onderbrekingen en netwerk fouten worden hersteld.

De standaardwaarde is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistWithEncryption

Geeft aan dat de werk stroom de gegevens in de opslag voor persistentie versleutelt. Overweeg het gebruik van deze functie bij het opslaan van persistentie gegevens in een netwerk share.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteNodeSessionIdleTimeoutSec

Hiermee geeft u op hoe lang een sessie die is verbonden met een extern knoop punt (doel computer) wordt onderhouden als deze niet actief is.

Voer een waarde in seconden in. De standaard waarde is 60.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionThrottleLimit

Hiermee geeft u op hoeveel bewerkingen worden gemaakt voor de ondersteuning van alle werk stromen die in de sessie zijn gestart. De standaardwaarde is 100.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkflowShutdownTimeoutMSec

Hiermee geeft u op hoe lang de sessie wordt behouden nadat alle werk stromen in de sessie geforceerd zijn onderbroken. Wanneer de time-out is verlopen, wordt de sessie door Windows Power shell gesloten, zelfs als alle werk stromen nog niet zijn onderbroken.

Voer een waarde in milliseconden in.
De standaardwaarde is 500.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. New psworkflowexecutionoption

## OPMERKINGEN

Wanneer de maximum waarde die is ingesteld met een optie wordt overschreden, mislukt de opdracht voor het maken van een instantie in de sessie, tenzij vermeld in de parameter beschrijving. Als de waarde van **MaxConnectedSessions** bijvoorbeeld 100 is. De opdracht voor het maken van de 101st-sessie naar een extern knoop punt (doel computer) is mislukt.

De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties. Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.

Met name de eigenschappen van sessie configuraties die een **PSWorkflowExecutionOptions** -object bevatten, variëren op basis van de waarden van de werk stroom optie. Als de sessie configuratie bijvoorbeeld een **PSWorkflowExecutionOptions** -object bevat dat een niet-standaard waarde voor de eigenschap **SessionThrottleLimit** instelt, heeft de sessie configuratie een **SessionThrottleLimit** -eigenschap. Anders is dit niet het geval.

## GERELATEERDE KOPPELINGEN

[New-PSWorkflowSession](New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
