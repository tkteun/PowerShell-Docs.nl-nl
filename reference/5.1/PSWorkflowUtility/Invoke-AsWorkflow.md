---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250286"
---
# Invoke-AsWorkflow

## SAMENVATTING
Hiermee wordt een opdracht of expressie uitgevoerd als een Windows Power shell-werk stroom.

## SYNTAXIS

### Opdracht (standaard)

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### Expression

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## BESCHRIJVING

De `Invoke-AsWorkflow` werk stroom voert een wille keurige opdracht of expressie uit als inline script in een werk stroom.
Deze werk stromen gebruiken de standaard werk stroom semantiek, hebben alle algemene werk stroom parameters en hebben alle voor delen van werk stromen, inclusief de mogelijkheid om te stoppen, te hervatten en te herstellen.

Werk stromen zijn ontworpen voor langlopende opdrachten die essentiële gegevens verzamelen, maar kunnen worden gebruikt om elke opdracht uit te voeren.
Zie [about_Workflows](../PSWorkflow/About/about_Workflows.md)voor meer informatie.

U kunt ook algemene werk stroom parameters toevoegen aan deze opdracht.
Zie [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md) voor meer informatie over algemene werk stroom parameters

Deze werk stroom is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een cmdlet uitvoeren als werk stroom

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

Met deze opdracht wordt de `Get-ExecutionPolicy` cmdlet op honderden computers uitgevoerd als een werk stroom.

De opdracht gebruikt de para meter **opdrachtnaam** om de cmdlet op te geven die in de werk stroom wordt uitgevoerd.
De gemeen schappelijke para meter **PSComputerName** workflow wordt gebruikt om de computers op te geven waarop de opdracht wordt uitgevoerd.
De waarde van de para meter **PSComputerName** is een `Get-Content` opdracht waarmee een lijst met computer namen uit het Servers.txt bestand wordt opgehaald.
De waarde van de para meter bevindt zich tussen haakjes om Windows Power shell te laten werken om de opdracht uit te voeren `Get-Command` voordat de waarde wordt gebruikt.

Net als bij alle externe opdrachten, als de opdracht wordt uitgevoerd op de lokale computer (als de waarde van de para meter PSComputerName de lokale computer bevat), moet u Windows Power shell starten met de optie als administrator uitvoeren.

### Voor beeld 2: een cmdlet met para meters uitvoeren

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

Met de eerste opdracht wordt de `Import-Csv` cmdlet gebruikt om een object te maken op basis van de inhoud in het Servers.csv-bestand. De opdracht gebruikt de `Header` para meter voor het maken van een `ServerName` eigenschap voor de kolom die de namen van de doel computers bevat, ook wel ' externe knoop punten ' genoemd. De opdracht slaat het resultaat op in de `$s` variabele.

Met de tweede opdracht wordt de `Invoke-AsWorkflow` werk stroom gebruikt om een opdracht uit te voeren `Get-ExecutionPolicy` op de computers in het Servers.csv-bestand. De opdracht gebruikt de para meter **opdrachtnaam** van `Invoke-AsWorkflow`  om de opdracht op te geven die in de werk stroom moet worden uitgevoerd. Hierbij wordt de para `Parameter` meter van gebruikt `Invoke-AsWorkflow` om de `Scope` para meter van de cmdlet op te geven `Get-ExecutionPolicy` met de waarde **process**. De opdracht gebruikt ook de `PSConnectionRetryCount` algemene werk stroom parameter om de opdracht te beperken tot vijf pogingen op elke computer en de `PSComputerName` algemene werk stroom parameter om de namen van de externe knoop punten (doel computers) op te geven. De waarde van de `PSComputerName` para meter is een expressie die de `ServerName` eigenschap van elk object in de variabele ophaalt `$s` .

Met deze opdrachten wordt een `Get-ExecutionPolicy` opdracht uitgevoerd als werk stroom op honderden computers.
De opdracht gebruikt de `Scope` para meter van de `Get-ExecutionPolicy` cmdlet met een waarde van het **proces** om het uitvoerings beleid in de huidige sessie op te halen.

### Voor beeld 3: een expressie als een werk stroom uitvoeren

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

Met deze opdracht wordt de `Invoke-AsWorkflow` werk stroom gebruikt om een ipconfig-opdracht uit te voeren als een werk stroom taak op de computers die worden vermeld in het DomainControllers.txt-bestand.

De opdracht gebruikt de `Expression` para meter om op te geven welke expressie moet worden uitgevoerd.
Er wordt gebruikgemaakt `PSComputerName` van de algemene werk stroom parameter om de namen van de externe knoop punten (doel computers) op te geven.

De opdracht gebruikt ook de `AsJob` `JobName` algemene para meters en werk stroom parameters om de werk stroom uit te voeren als een achtergrond taak op elke computer met de taak naam ' ipconfig '.

De opdracht retourneert een `ContainerParentJob` object ( `System.Management.Automation.ContainerParentJob` ) dat de werk stroom taken op elke computer bevat.

## PARAMETERS

### -Opdrachtnaam

Hiermee wordt de opgegeven cmdlet of geavanceerde functie uitgevoerd als een werk stroom.
Voer de cmdlet of functie naam in, zoals `Update-Help` , `Set-ExecutionPolicy` of `Set-NetFirewallRule` .

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expressie

Hiermee geeft u de expressie op die met deze cmdlet wordt uitgevoerd als een werk stroom.
Voer de expressie in als een teken reeks, zoals `"ipconfig /all"` .
Als de expressie spaties of speciale tekens bevat, plaatst u de expressie tussen aanhalings tekens.

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Para meter

Hiermee geeft u de para meters en parameter waarden op van de opdracht die is opgegeven in de `CommandName` para meter.
Voer een hash-tabel in waarin elke sleutel een parameter naam is en de waarde ervan de parameter waarde is, bijvoorbeeld `@{ExecutionPolicy="AllSigned"}` .

Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Wordt gebruikt om invoer van de pijp lijn toe te staan.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

### WorkflowCommonParameters

Deze cmdlet ondersteunt ook specifieke algemene para meters voor werk stromen.
Zie [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)voor meer informatie.

## INVOER

### System. object

U kunt elk object door sluizen naar de `InputObject` para meter.

## UITVOER

### Geen

Met deze opdracht wordt geen uitvoer gegenereerd.
De werk stroom wordt echter wel uitgevoerd, waardoor uitvoer kan worden gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[New-New psworkflowexecutionoption](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[New-PSWorkflowSession](../PSWorkflow/New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_Workflow_Common_Parameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)
