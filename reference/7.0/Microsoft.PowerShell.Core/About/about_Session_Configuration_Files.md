---
description: Hierin worden de configuratie bestanden voor de sessie beschreven, die worden gebruikt in een sessie configuratie (ook wel een ' eind punt ' genoemd) om de omgeving van sessies te definiëren die gebruikmaken van de sessie configuratie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 113c068022f37b22cbcc5dae61a6a5edf26187d8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252077"
---
# <a name="about-session-configuration-files"></a>Over sessie configuratie bestanden

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de configuratie bestanden voor de sessie beschreven, die worden gebruikt in een sessie configuratie (ook wel een ' eind punt ' genoemd) om de omgeving van sessies te definiëren die gebruikmaken van de sessie configuratie.

## <a name="long-description"></a>LANGE BESCHRIJVING

Een ' sessie configuratie bestand ' is een tekst bestand met de bestandsnaam extensie. pssc dat een hashtabel bevat van de eigenschappen en waarden van de sessie configuratie. U kunt een sessie configuratie bestand gebruiken om de eigenschappen van een sessie configuratie in te stellen. Hiermee definieert u de omgeving van elke Power shell-sessie die deze sessie configuratie gebruikt.

Met sessie configuratie bestanden kunt u eenvoudig aangepaste sessie configuraties maken zonder ingewikkelde C#-assembly's of-scripts te gebruiken.

Een ' sessie configuratie ' of ' eind punt ' is een verzameling lokale computer instellingen die de dingen bepalen waarmee gebruikers sessies op de computer kunnen maken. welke opdrachten gebruikers in deze sessies kunnen uitvoeren; en of de sessie moet worden uitgevoerd als een privileged virtueel account. Zie [about_Session_Configurations](about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

Er zijn sessie configuraties geïntroduceerd in Windows Power Shell 2,0 en sessie configuratie bestanden zijn geïntroduceerd in Windows Power Shell 3,0. U moet Windows Power Shell 3,0 gebruiken voor het toevoegen van een sessie configuratie bestand in een sessie configuratie. Gebruikers van Windows Power Shell 2,0 (en hoger) worden echter beïnvloed door de instellingen in de sessie configuratie.

## <a name="creating-custom-sessions"></a>Aangepaste sessies maken

U kunt een groot aantal functies van een Power shell-sessie aanpassen door sessie-eigenschappen in een sessie configuratie op te geven. U kunt een sessie aanpassen door een C#-programma te schrijven dat een aangepaste runs Pace definieert, of u kunt een sessie configuratie bestand gebruiken om de eigenschappen te definiëren van sessies die zijn gemaakt met behulp van de sessie configuratie. In het algemeen is het eenvoudiger om het sessie configuratie bestand te gebruiken dan om een C#-programma te schrijven.

U kunt een sessie configuratie bestand gebruiken om items te maken, zoals volledig werkende sessies voor zeer vertrouwde gebruikers. vergrendelde sessies die minimale toegang toestaan; sessies die zijn ontworpen met name en die alleen de modules bevatten die nodig zijn voor deze taken; en sessies waarbij niet-gemachtigde gebruikers alleen specifieke opdrachten kunnen uitvoeren als een bevoegd account.

Daarnaast kunt u beheren of gebruikers van de sessie Power shell-taal elementen zoals script blokken kunnen gebruiken, of dat ze alleen opdrachten kunnen uitvoeren. U kunt de versie van Power shell-gebruikers beheren in de sessie. beheren welke modules in de sessie worden geïmporteerd; en beheren welke cmdlets, functies en aliassen sessie gebruikers kunnen uitvoeren. Wanneer u het veld RoleDefinitions gebruikt, kunt u gebruikers verschillende mogelijkheden geven in de sessie op basis van groepslid maatschap.

Zie het Help-onderwerp voor de cmdlet New-PSRoleCapabilityFile voor meer informatie over RoleDefinitions en het definiëren van deze waarde.

## <a name="creating-a-session-configuration-file"></a>Een configuratie bestand voor de sessie maken

De eenvoudigste manier om een sessie configuratie bestand te maken, is met behulp van de cmdlet New-PSSessionConfigurationFile. Met deze cmdlet wordt een bestand gegenereerd dat gebruikmaakt van de juiste syntaxis en indeling en dat veel eigenschaps waarden van het configuratie bestand automatisch verifieert.

Zie het Help-onderwerp voor de cmdlet New-PSSessionConfigurationFile voor gedetailleerde beschrijvingen van de eigenschappen die u in een sessie configuratie bestand kunt instellen.

Met de volgende opdracht maakt u een sessie configuratie bestand dat gebruikmaakt van de standaard waarden. In het resulterende configuratie bestand worden alleen de standaard waarden gebruikt omdat er geen para meters zijn met uitzonde ring van de para meter Path (waarmee het bestandspad wordt opgegeven):

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

Als u het nieuwe configuratie bestand in de standaard tekst editor wilt weer geven, gebruikt u de volgende opdracht:

```powershell
Invoke-Item -Path .\Defaults.pssc
```

Als u een sessie configuratie wilt maken voor sessies waarin de gebruiker opdrachten kan uitvoeren, maar geen andere elementen van de Power shell-taal, typt u:

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

In de voor gaande opdracht stelt u de para meter LanguageMode in op geen taal, voor komt u dat gebruikers dingen doen als schrijven of uitvoeren van scripts of met behulp van variabelen.

Voor het maken van een sessie configuratie voor sessies waarin gebruikers alleen cmdlets kunnen gebruiken, typt u:

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

In het vorige voor beeld stelt u de para meter VisibleCmdlets in op Get-* om gebruikers te beperken tot cmdlets met een naam die begint met de teken reeks waarde ' Get-'.

Als u een sessie configuratie wilt maken voor sessies die worden uitgevoerd onder een privileged Virtual account in plaats van de referenties van de gebruiker, typt u:

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

Als u een sessie configuratie wilt maken voor sessies waarin de opdrachten die zichtbaar zijn voor de gebruiker worden opgegeven in een bestand met functie mogelijkheden, typt u:

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a>Een sessie configuratie bestand gebruiken

U kunt een sessie configuratie bestand toevoegen wanneer u een sessie configuratie maakt of toevoegt. u kunt een bestand op een later tijdstip toevoegen aan de sessie configuratie.

Als u een sessie configuratie bestand wilt toevoegen bij het maken van een sessie configuratie, gebruikt u de para meter Path van de cmdlet Register-PSSessionConfiguration.

Met de volgende opdracht wordt bijvoorbeeld het bestand pssc gebruikt wanneer er een configuratie voor een niet-getaalde sessie wordt gemaakt.

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

Wanneer een nieuwe niet-taal sessie wordt gestart, hebben gebruikers alleen toegang tot Power shell-opdrachten.

Als u een sessie configuratie bestand wilt toevoegen aan een bestaande sessie configuratie, gebruikt u de cmdlet Set-PSSessionConfiguration en de para meter Path. Dit is van invloed op nieuwe sessies die zijn gemaakt met de opgegeven sessie configuratie. Houd er rekening mee dat de cmdlet Set-PSSessionConfiguration de sessie zelf wijzigt en het sessie configuratie bestand niet wijzigt.

Met de volgende opdracht wordt bijvoorbeeld het bestand ' pssc ' toegevoegd aan de configuratie van de LockedDown-sessie.

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

Wanneer gebruikers de configuratie van de LockedDown-sessie gebruiken om een sessie te maken, kunnen ze cmdlets uitvoeren, maar ze kunnen geen variabelen maken of gebruiken, waarden toewijzen of andere Power shell-taal elementen gebruiken.

De volgende opdracht maakt gebruik van de New-PSSession cmdlet om een sessie te maken op de computer Srv01 die gebruikmaakt van de configuratie van de LockedDown-sessie, waarbij een object verwijzing naar de sessie in de $s variabele wordt opgeslagen. De ACL (toegangs beheer lijst) van de sessie configuratie bepaalt wie deze kan gebruiken om een sessie te maken.

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

Omdat de niet-taal beperkingen zijn toegevoegd aan de LockedDown-sessie configuratie, kunnen gebruikers in LockedDown-sessies alleen Power shell-opdrachten en-cmdlets uitvoeren. De volgende twee opdrachten gebruiken bijvoorbeeld de cmdlet Invoke-Command om opdrachten uit te voeren in de sessie waarnaar wordt verwezen in de $s-variabele. De eerste opdracht, waarmee de cmdlet Get-UICulture wordt uitgevoerd en geen variabelen gebruikt, slaagt. De tweede opdracht, waarmee de waarde van de variabele $PSUICulture wordt opgehaald, mislukt.

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a>Een sessie configuratie bestand bewerken

Alle instellingen in een sessie configuratie, met uitzonde ring van RunAsVirtualAccount en RunAsVirtualAccountGroups, kunnen worden gewijzigd door het sessie configuratie bestand te bewerken dat door de sessie configuratie wordt gebruikt. Om dit te doen, moet u eerst de actieve kopie van het sessie configuratie bestand zoeken.

Wanneer u een sessie configuratie bestand in een sessie configuratie gebruikt, maakt Power shell een actieve kopie van het sessie configuratie bestand en slaat deze op in de \$ \\ map pshome SessionConfig op de lokale computer.

De locatie van de actieve kopie van een sessie configuratie bestand wordt opgeslagen in de eigenschap ConfigFilePath van het object voor sessie configuratie.

Met de volgende opdracht wordt de locatie van het sessie configuratie bestand voor de configuratie van de niet-getaalde sessie opgehaald.

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

Met deze opdracht wordt een bestandspad geretourneerd dat er ongeveer als volgt uitziet:

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

U kunt het. pssc-bestand bewerken in een tekst editor. Nadat het bestand is opgeslagen, wordt het gebruikt door alle nieuwe sessies die gebruikmaken van de sessie configuratie.

Als u de instellingen voor RunAsVirtualAccount of RunAsVirtualAccountGroups moet wijzigen, moet u de registratie van de sessie configuratie ongedaan maken en een sessie configuratie bestand dat de bewerkte waarden bevat, opnieuw registreren.

## <a name="testing-a-session-configuration-file"></a>Een configuratie bestand voor een sessie testen

Gebruik de cmdlet Test-PSSessionConfigurationFile om hand matig bewerkte sessie configuratie bestanden te testen. Dat is belang rijk: als de syntaxis en waarden van het bestand niet geldig zijn, kunnen gebruikers de sessie configuratie niet gebruiken om een sessie te maken.

Met de volgende opdracht wordt bijvoorbeeld het configuratie bestand van de actieve sessie van de configuratie van de niet-taal sessie getest.

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

Als de syntaxis en waarden in het configuratie bestand geldig zijn Test-PSSessionConfigurationFile retourneert True. Als de syntaxis en waarden niet geldig zijn, retourneert de cmdlet false.

U kunt Test-PSSessionConfigurationFile gebruiken om een sessie configuratie bestand te testen, inclusief bestanden die door de New-PSSessionConfiguration-cmdlet worden gemaakt. Zie het Help-onderwerp voor de cmdlet Test-PSSessionConfigurationFile voor meer informatie.

## <a name="removing-a-session-configuration-file"></a>Een sessie configuratie bestand verwijderen

U kunt een sessie configuratie bestand niet verwijderen uit een sessie configuratie.
U kunt het bestand echter vervangen door een nieuw bestand dat de standaard instellingen gebruikt. Hiermee worden de instellingen die worden gebruikt door het oorspronkelijke configuratie bestand in feite geannuleerd.

Als u een configuratie bestand voor de sessie wilt vervangen, maakt u een nieuw sessie configuratie bestand dat gebruikmaakt van de standaard instellingen en gebruikt u vervolgens de cmdlet Set-PSSessionConfiguration om het aangepaste sessie configuratie bestand te vervangen door het nieuwe bestand.

Met de volgende opdrachten maakt u bijvoorbeeld een standaard sessie configuratie bestand en vervangt u vervolgens het configuratie bestand van de actieve sessie in de configuratie van de niet-taal sessie.

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

Als deze opdrachten zijn voltooid, biedt de configuratie van de sessie zonder taal de volledige taal ondersteuning (de standaard instelling) voor alle sessies die zijn gemaakt met die sessie configuratie.

Het weer geven van de eigenschappen van een sessie configuratie de sessie configuratie objecten die sessie configuraties vertegenwoordigen met behulp van sessie configuratie bestanden hebben extra eigenschappen waarmee u de sessie configuratie eenvoudig kunt detecteren en analyseren. (Houd er rekening mee dat de hieronder weer gegeven type naam een opmaak definitie bevat.) U kunt de eigenschappen weer geven door de Get-PSSessionConfiguration-cmdlet uit te voeren en de geretourneerde gegevens te sluizen naar de Get-Member-cmdlet:

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

Met deze eigenschappen kunt u eenvoudig zoeken naar specifieke sessie configuraties.
U kunt bijvoorbeeld de eigenschap ExecutionPolicy gebruiken om een sessie configuratie te vinden die ondersteuning biedt voor sessies met het beleid voor het uitvoeren van RemoteSigned.
Houd er rekening mee dat, omdat de eigenschap ExecutionPolicy alleen bestaat voor sessies die gebruikmaken van sessie configuratie bestanden, de opdracht mogelijk niet alle in aanmerking komende sessie configuraties retourneert.

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

Met de volgende opdracht worden de sessie configuraties opgehaald waarin de RunAsUser de Exchange-beheerder is.

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

Gebruik de cmdlet Get-PSSessionCapability om informatie weer te geven over de roldefinities die aan een configuratie zijn gekoppeld. Met deze cmdlet kunt u de opdrachten en omgeving bepalen die beschikbaar zijn voor specifieke gebruikers in specifieke eind punten.

## <a name="notes"></a>OPMERKINGEN

Sessie configuraties bieden ook ondersteuning voor een type sessie dat een ' lege ' sessie wordt genoemd. Met een leeg sessie type kunt u aangepaste sessies maken met geselecteerde opdrachten. Als u geen modules, functies of scripts aan een lege sessie toevoegt, is de sessie beperkt tot expressies en is deze mogelijk niet van praktisch gebruik. De eigenschap SessionType vertelt u of u met een lege sessie werkt.

## <a name="see-also"></a>ZIE OOK

[about_Session_Configurations](about_Session_Configurations.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Registratie ongedaan maken-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[Get-PSSessionCapability](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[New-PSRoleCapabilityFile](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)
