---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 300fc3dee2e0d625e5aea42bfdcf45ea2e8b5a7f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251627"
---
# Get-PSSessionConfiguration

## SAMENVATTING
Hiermee worden de geregistreerde sessie configuraties op de computer opgehaald.

## SYNTAXIS

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-PSSessionConfiguration` cmdlet haalt de sessie configuraties op die zijn geregistreerd op de lokale computer. Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.

Vanaf Power Shell 3,0 kunt u de eigenschappen van een sessie configuratie definiëren met behulp van een sessie configuratie bestand (. pssc). Met deze functie kunt u aangepaste en beperkte sessies maken zonder dat u een computer programma hoeft te schrijven. Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.

Daarnaast zijn er vanaf Power Shell 3,0 nieuwe notitie-eigenschappen toegevoegd aan het sessie configuratie object dat `Get-PSSessionConfiguration` retourneert. Deze eigenschappen maken het gemakkelijker voor gebruikers en sessie configuratie ontwerpers om sessie configuraties te onderzoeken en vergelijken.

Als u een sessie configuratie wilt maken en registreren, gebruikt u de `Register-PSSessionConfiguration` cmdlet.
Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

## VOORBEELDEN

### Voor beeld 1: sessie configuraties op de lokale computer ophalen

```powershell
Get-PSSessionConfiguration
```

### Voor beeld 2: de twee standaard sessie configuraties ophalen

De opdracht gebruikt de para meter **name** van `Get-PSSessionConfiguration` om alleen de sessie configuraties op te halen met namen die beginnen met ' micro soft '.

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### Voor beeld 3: de eigenschappen en waarden van een sessie configuratie ophalen

In dit voor beeld worden de eigenschappen en eigenschaps waarden weer gegeven van een sessie configuratie die is gemaakt met behulp van een configuratie bestand voor de sessie.

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

In het voor beeld wordt de `Get-PSSessionConfiguration` cmdlet gebruikt om de volledige sessie configuratie op te halen. Een pijplijn operator verzendt de volledige sessie configuratie naar de `Format-List` cmdlet. Met de **eigenschaps** parameter met de waarde `*` (all) `Format-List` worden alle eigenschappen en waarden van het object in een lijst weer gegeven.

De uitvoer bevat nuttige informatie, waaronder de auteur van de sessie configuratie, het sessie type, de taal modus en het uitvoerings beleid van sessies die zijn gemaakt met deze sessie configuratie, sessie quota en het volledige pad naar het sessie configuratie bestand.

Deze weer gave van een sessie configuratie wordt gebruikt voor sessies die een sessie configuratie bestand bevatten.
Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.

### Voor beeld 4: een andere manier om de sessie configuraties te bekijken

In dit voor beeld wordt de `Get-ChildItem` cmdlet (alias `dir` ) in het station WSMan: provider gebruikt om de inhoud van het knoop punt van de invoeg toepassing te bekijken. Dit is een andere manier om de sessie configuraties op de computer te bekijken.

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

Het knoop punt van de **invoeg toepassing** bevat **ContainerElement** -objecten (micro soft. WSMan. Management. WSManConfigContainerElement) die de geregistreerde Power shell-sessie configuraties vertegenwoordigen, samen met andere invoeg toepassingen voor WS-Management.

### Voor beeld 6: sessie configuraties op een externe computer weer geven

In dit voor beeld ziet u hoe u de WSMan-provider kunt gebruiken om de sessie configuraties op een externe computer weer te geven. Deze methode biedt niet zoveel informatie als een `Get-PSSessionConfiguration` opdracht, maar de gebruiker hoeft geen lid te zijn van de groep Administrators om deze cmdlet uit te voeren.

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

De `Connect-WSMan` cmdlet maakt verbinding met de WinRM-service op de externe Server01-computer. De `Get-ChildItem` cmdlet (alias `dir` ) van het WSMan: station haalt de items op in het pad **Server01\Plugin** . In de uitvoer ziet u de items in de map voor de invoeg toepassing op de computer Server01. De items omvatten de sessie configuraties, die een type WSMan-invoeg toepassing zijn, samen met andere typen invoeg toepassingen op de computer.

### Voor beeld 7: gedetailleerde sessie configuraties van een externe computer ophalen

In dit voor beeld ziet u hoe u een `Get-PSSessionConfiguration` opdracht op een externe computer uitvoert. Voor de opdracht is vereist dat CredSSP delegering is ingeschakeld in de client instellingen op de lokale computer en in de service-instellingen op de externe computer.

Als u de opdrachten in dit voor beeld wilt uitvoeren, moet u lid zijn van de groep Administrators op de lokale en externe computers en moet u Power shell starten met de optie **als administrator uitvoeren** .

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

`Enable-WSManCredSSP`Met de cmdlet schakelt u **CredSSP** -delegering in op Server01, de lokale computer. De `Connect-WSMan` cmdlet maakt verbinding met de Server02-computer. Met deze actie wordt een knoop punt voor Server02 toegevoegd aan het WSMan:-station op de lokale computer, zodat u de WS-Management instellingen op de Server02-computer kunt weer geven en wijzigen. Met de `Set-Item` cmdlet wordt de waarde van het **CredSSP** -item in het knoop punt service van de Server02-computer gewijzigd in **True**. Hiermee configureert u de service-instellingen op de externe computer. De `Invoke-Command` cmdlet voert de `Get-PSSessionConfiguration` opdracht uit op de Server02-computer. De opdracht gebruikt de para meter **Credential** en gebruikt de **verificatie** parameter met de waarde **CredSSP**. In de uitvoer ziet u de sessie configuraties op de externe computer Server02.

### Voor beeld 8: de bron-URI van een sessie configuratie ophalen

Dit voor beeld is handig voor het instellen van de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele, die een resource-URI gebruikt.

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

De `$PSSessionConfigurationName` variabele geeft de standaard configuratie op die wordt gebruikt bij het maken van een sessie. Deze variabele is ingesteld op de lokale computer, maar Hiermee wordt een configuratie op de externe computer opgegeven. Zie about_Preference_Variables voor meer informatie over de `$PSSessionConfiguration` variabele [about_Preference_Variables](About/about_Preference_Variables.md).

## PARAMETERS

### -Force

Onderdrukt de prompt om de WinRM-service opnieuw te starten als de service nog niet wordt uitgevoerd.

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

### -Name

Hiermee worden alleen de sessie configuraties met het opgegeven naam-of naam patroon opgehaald. Voer een of meer sessie configuratie namen in. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration

## OPMERKINGEN

- Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .

- Als u de sessie configuraties op de computer wilt weer geven, moet u lid zijn van de groep Administrators op de computer.

- Als u een `Get-PSSessionConfiguration` opdracht op een externe computer wilt uitvoeren, moet de CredSSP-verificatie (Credential Security service provider) zijn ingeschakeld in de client instellingen op de lokale computer (met behulp van de `Enable-WSManCredSSP` cmdlet) en in de service-instellingen op de externe computer. U moet ook de **CredSSP** -waarde van de **verificatie** parameter gebruiken bij het tot stand brengen van de externe sessie. Anders wordt de toegang geweigerd.

- De notitie-eigenschappen van het object die `Get-PSSessionConfiguration` worden geretourneerd, worden alleen weer gegeven op het object wanneer ze een waarde hebben. Alleen sessie configuraties die zijn gemaakt met behulp van een sessie configuratie bestand hebben alle gedefinieerde eigenschappen.

- De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties. Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.

- U kunt opdrachten in WSMan: drive gebruiken om de eigenschappen van sessie configuraties te wijzigen.
  U kunt echter niet het WSMan:-station in Power Shell 2,0 gebruiken om de eigenschappen van de sessie configuratie te wijzigen die zijn geïntroduceerd in Power Shell 3,0, zoals **OutputBufferingMode**. Power Shell 2,0-opdrachten genereren geen fout, maar zijn niet effectief. Als u eigenschappen wilt wijzigen die zijn geïntroduceerd in Power Shell 3,0, gebruikt u het station WSMan: in Power Shell 3,0.

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)

