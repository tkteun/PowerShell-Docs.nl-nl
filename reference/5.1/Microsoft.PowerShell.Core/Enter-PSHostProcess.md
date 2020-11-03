---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 56b8cef1911d1365f9568483921bfb49fbc32451
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249969"
---
# Enter-PSHostProcess

## SAMENVATTING
Hiermee maakt u verbinding met en voert u een interactieve sessie in met een lokaal proces.

## SYNTAXIS

### ProcessIdParameterSet (standaard)

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessParameterSet

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### PSHostProcessInfoParameterSet

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

`Enter-PSHostProcess`Met de cmdlet maakt u verbinding met en voert u een interactieve sessie in met een lokaal proces.

In plaats van een nieuw proces te maken voor het hosten van Power shell en het uitvoeren van een externe sessie, wordt de externe, interactieve sessie uitgevoerd in een bestaand proces dat Power shell al uitvoert. Wanneer u met een externe sessie op een opgegeven proces werkt, kunt u het uitvoeren van runspaces opsommen en vervolgens een runs Pace voor fout opsporing selecteren door ofwel of toe te voeren `Debug-Runspace` `Enable-RunspaceDebug` .

Het proces dat u wilt invoeren, moet de Power shell (System.Management.Automation.dll) hosten.
U moet lid zijn van de groep Administrators op de computer waarop het proces is gevonden, of u moet de gebruiker zijn die het script uitvoert waarmee het proces is gestart.

Nadat u een runs Pace hebt geselecteerd om fouten op te sporen, wordt een sessie voor fout opsporing op afstand geopend voor de runs Pace als dit op dit moment een opdracht wordt uitgevoerd of wordt gestopt in het fout opsporingsprogramma. U kunt vervolgens fouten opsporen in het runs Pace-script op dezelfde manier als u fouten opspoort voor andere externe sessie scripts.

Loskoppelen van een foutopsporingssessie en vervolgens de interactieve sessie met het proces, door twee keer af te sluiten of de uitvoering van het script te stoppen door de bestaande opdracht debug afsluiten uit te voeren.

Als u een proces opgeeft met de para meter **name** en er slechts één proces met de opgegeven naam wordt gevonden, wordt het proces ingevoerd. Als er meer dan één proces met de opgegeven naam wordt gevonden, retourneert Power shell een fout en worden alle processen vermeld die met de opgegeven naam zijn gevonden.

Ter ondersteuning van het koppelen van processen op externe computers, `Enter-PSHostProcess` wordt de cmdlet ingeschakeld in een opgegeven externe computer, zodat u kunt koppelen aan een lokaal proces binnen een externe Power shell-sessie.

## VOORBEELDEN

### Voor beeld 1: fouten opsporen in een runs Pace binnen het Power shell ISE-proces

In dit voor beeld voert u `Enter-PSHostProcess` uit vanuit de Power shell-console om het Power shell ISE-proces in te voeren. In de resulterende interactieve sessie kunt u een runs Pace vinden die u wilt debuggen door uit te voeren `Get-Runspace` en vervolgens fouten opsporen in de runs Pace.

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## PARAMETERS

### -AppDomainName

Hiermee geeft u de naam van een toepassings domein waarmee verbinding moet worden gemaakt als u dit weglaat, wordt **DefaultAppDomain** gebruikt. Gebruiken `Get-PSHostProcessInfo` om de namen van de toepassings domeinen weer te geven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostProcessInfo

Hiermee geeft u een **PSHostProcessInfo** -object op dat kan worden verbonden met Power shell. Gebruiken `Get-PSHostProcessInfo` om het object op te halen.

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een proces met de proces-ID op. Voer de cmdlet uit om een proces-ID op te halen `Get-Process` .

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een proces op met de proces naam. Voer de cmdlet uit om een proces naam op te halen `Get-Process` . U kunt ook proces namen ophalen uit het dialoog venster Eigenschappen van een proces in taak beheer.

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proces

Hiermee geeft u een proces op voor het proces object. De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een `Get-Process` opdracht die het proces retourneert dat u in een variabele wilt invoeren, en vervolgens geeft u de variabele op als de waarde van deze para meter.

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Diagnostics. process

## UITVOER

## OPMERKINGEN

`Enter-PSHostProcess` kan het proces van de Power shell-sessie niet invoeren waarin de opdracht wordt uitgevoerd. U kunt echter wel het proces van een andere Power shell-sessie invoeren, of een Power shell ISE-sessie die wordt uitgevoerd op hetzelfde moment als de sessie waarin u uitvoert `Enter-PSHostProcess` .

`Enter-PSHostProcess` alleen de processen die Power shell hosten, kunnen worden ingevoerd. Dat wil zeggen dat ze de Power shell-Engine hebben geladen.

Als u een proces wilt afsluiten vanuit het proces, typt u **Exit** en drukt u vervolgens op <kbd>Enter</kbd>.

## GERELATEERDE KOPPELINGEN

[Afsluiten-PSHostProcess](Exit-PSHostProcess.md)

[Get-PSHostProcessInfo](Get-PSHostProcessInfo.md)
