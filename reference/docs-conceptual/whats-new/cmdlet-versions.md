---
ms.date: 02/03/2020
keywords: Power shell, kern
title: Release geschiedenis van modules en cmdlets
ms.openlocfilehash: 0a1a8b0e4b1460bbaeb30495262aff2b414a649b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564632"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Release geschiedenis van modules en cmdlets

In dit artikel vindt u een lijst met de modules en cmdlets die worden geleverd met verschillende versies van Power shell. Dit is een overzicht van de informatie die is gevonden in de release opmerkingen. Meer gedetailleerde informatie vindt u in de opmerkingen bij de release:

- [Wat is er nieuw in PowerShell Core 6.2?](what-s-new-in-powershell-core-62.md)
- [Wat is er nieuw in PowerShell Core 6.1?](what-s-new-in-powershell-core-61.md)
- [Wat is er nieuw in PowerShell Core 6.0?](what-s-new-in-powershell-core-60.md)
- [Wijzigingen in PowerShell Core 6.0 die fouten veroorzaken](breaking-changes-ps6.md)
- [Bekende problemen in PowerShell Core 6.0](known-issues-ps6.md)

Dit is een onderhanden werk. Help ons deze gegevens actueel te houden.

## <a name="module-release-history"></a>Release geschiedenis van de module

|         Module naam/PS-versie          |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Alleen op Windows |
| ISE (geïntroduceerd in 2,0)                   | &check; |         |         |         | Alleen op Windows |
| Micro soft. Power shell. Archive              | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. core                 | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. Diagnostics          | &check; | &check; | &check; | &check; | Alleen op Windows |
| Micro soft. Power shell. host                 | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. LocalAccounts        | &check; |         |         |         | Alleen op Windows |
| Micro soft. Power shell. Management           | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. ODataUtils           | &check; |         |         |         | Alleen op Windows |
| Micro soft. Power shell. Operation. validatie | &check; |         |         |         | Alleen op Windows |
| Micro soft. Power shell. Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Micro soft. WsMan. Management                | &check; | &check; | &check; | &check; | Alleen op Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Alleen op Windows |
| PSReadline 1. x                            | &check; |         |         |         | Alleen op Windows |
| PSReadline 2. x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Alleen op Windows |
| PSWorkflow                                | &check; |         |         |         | Alleen op Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Alleen op Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | Kan worden geïnstalleerd in Power shell 5,1 |

## <a name="cmdlet-release-history"></a>Release geschiedenis van de cmdlet

### <a name="cimcmdlets"></a>CimCmdlets

|         Naam van cmdlet         |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Exporteren-BinaryMiLog          | &check; | &check; | &check; | &check; | Alleen op Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Alleen op Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Alleen op Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Alleen op Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Alleen op Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Alleen op Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Alleen op Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Alleen op Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Alleen op Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Alleen op Windows |
| REGI ster-CimIndicationEvent | &check; | &check; | &check; | &check; | Alleen op Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Alleen op Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Alleen op Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Alleen op Windows |

### <a name="ise-introduced-in-20"></a>ISE (geïntroduceerd in 2,0)

|    Naam van cmdlet    |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Alleen op Windows |
| Import-IseSnippet | &check; |      |       |       | Alleen op Windows |
| New-IseSnippet    | &check; |      |       |       | Alleen op Windows |

### <a name="microsoftpowershellarchive"></a>Micro soft. Power shell. Archive

|   Naam van cmdlet    |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Comprimeren-archief | &check; | &check; | &check; | &check; |      |
| Uitvouwen-archief   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Micro soft. Power shell. core

|            Naam van cmdlet            |   5.1   |   6.x   |   7.0   |   7.1   |            Notitie            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Toevoegen-geschiedenis                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Alleen op Windows               |
| Wissen-geschiedenis                     | &check; | &check; | &check; | &check; |                            |
| Wissen-host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Fout opsporing-taak                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Verbinding verbreken-PSSession              | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Afsluiten-PSHostProcess                | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Afsluiten-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Exporteren-console                    | &check; |         |         |         | Alleen op Windows               |
| Exporteren-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-geschiedenis                       | &check; | &check; | &check; | &check; |                            |
| Get-job                           | &check; | &check; | &check; | &check; |                            |
| Get-module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Alleen op Windows               |
| Get-term                          | &check; |         |         |         | Verplaatst naar micro soft. Power shell. Utility 6.0 + |
| Import-module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-opdracht                    | &check; | &check; | &check; | &check; |                            |
| Invoke-geschiedenis                    | &check; | &check; | &check; | &check; |                            |
| New-module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Alleen op Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-standaard                       | &check; | &check; | &check; | &check; |                            |
| Out-host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Alleen op Windows               |
| REGI ster-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Verwijderen-taak                        | &check; | &check; | &check; | &check; |                            |
| Remove-module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Alleen op Windows               |
| Resume-job                        | &check; |         |         |         |                            |
| Opslaan-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Begin taak                         | &check; | &check; | &check; | &check; |                            |
| Stoppen-taak                          | &check; | &check; | &check; | &check; |                            |
| Onderbreken-taak                       | &check; |         |         |         | Alleen op Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Registratie ongedaan maken-PSSessionConfiguration | &check; | &check; | &check; | &check; | Alleen op Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Micro soft. Power shell. Diagnostics

|  Naam van cmdlet   |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Exporteren-teller | &check; |         |         |         | Alleen op Windows |
| Get-teller    | &check; |         | &check; | &check; | Alleen op Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Alleen op Windows |
| Import teller | &check; |         |         |         | Alleen op Windows |
| New-Wine vent   | &check; | &check; | &check; | &check; | Alleen op Windows |

### <a name="microsoftpowershellhost"></a>Micro soft. Power shell. host

|   Naam van cmdlet    |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-transcript | &check; | &check; | &check; | &check; |      |
| Stoppen-transcriptie  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Micro soft. Power shell. LocalAccounts

|       Naam van cmdlet       |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Alleen op Windows |
| Disable-Lokalegebruiker       | &check; |      |       |       | Alleen op Windows |
| Enable-Lokalegebruiker        | &check; |      |       |       | Alleen op Windows |
| Get-LocalGroup          | &check; |      |       |       | Alleen op Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Alleen op Windows |
| Get-Lokalegebruiker           | &check; |      |       |       | Alleen op Windows |
| Nieuw-LocalGroup          | &check; |      |       |       | Alleen op Windows |
| New-Lokalegebruiker           | &check; |      |       |       | Alleen op Windows |
| Remove-LocalGroup       | &check; |      |       |       | Alleen op Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Alleen op Windows |
| Remove-Lokalegebruiker        | &check; |      |       |       | Alleen op Windows |
| Rename-LocalGroup       | &check; |      |       |       | Alleen op Windows |
| Naam wijzigen-Lokalegebruiker        | &check; |      |       |       | Alleen op Windows |
| Set-LocalGroup          | &check; |      |       |       | Alleen op Windows |
| Set-Lokalegebruiker           | &check; |      |       |       | Alleen op Windows |

### <a name="microsoftpowershellmanagement"></a>Micro soft. Power shell. Management

|          Naam van cmdlet          |   5.1   |   6.x   |   7.0   |   7.1   |               Notitie               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-computer                  | &check; |         |         |         | Alleen op Windows                     |
| Add-content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Alleen op Windows                     |
| Wissen-inhoud                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Alleen op Windows                     |
| Wissen-item                    | &check; | &check; | &check; | &check; |                                  |
| Wissen-item Property            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Alleen op Windows                     |
| Volt ooien-trans actie          | &check; |         |         |         | Alleen op Windows                     |
| Convert-pad                  | &check; | &check; | &check; | &check; |                                  |
| Kopie-item                     | &check; | &check; | &check; | &check; |                                  |
| Kopiëren-item Property             | &check; | &check; | &check; | &check; |                                  |
| Debug-proces                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Alleen op Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Alleen op Windows                     |
| Get-Child item                 | &check; | &check; | &check; | &check; |                                  |
| Get-klem bord                 | &check; |         | &check; | &check; | Niet ondersteund op macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Alleen op Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Alleen op Windows                     |
| Get-EventLog                  | &check; |         |         |         | Alleen op Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Alleen op Windows                     |
| Get-item                      | &check; | &check; | &check; | &check; |                                  |
| Get-item Property              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-locatie                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Get-time zone                  | &check; | &check; | &check; | &check; |                                  |
| Get-trans actie               | &check; |         |         |         | Alleen op Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Alleen op Windows                     |
| Invoke-item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Alleen op Windows                     |
| Pad voor samen voegen                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Alleen op Windows                     |
| Item verplaatsen                     | &check; | &check; | &check; | &check; |                                  |
| Verplaatsen-item Property             | &check; | &check; | &check; | &check; |                                  |
| Nieuw-gebeurtenis logboek                  | &check; |         |         |         | Alleen op Windows                     |
| Nieuw-item                      | &check; | &check; | &check; | &check; |                                  |
| Nieuw-item Property              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Alleen op Windows                     |
| Pop-locatie                  | &check; | &check; | &check; | &check; |                                  |
| Push-locatie                 | &check; | &check; | &check; | &check; |                                  |
| REGI ster-WmiEvent             | &check; |         |         |         | Alleen op Windows                     |
| Verwijderen-computer               | &check; |         |         |         | Alleen op Windows                     |
| Remove-EventLog               | &check; |         |         |         | Alleen op Windows                     |
| Verwijderen-item                   | &check; | &check; | &check; | &check; |                                  |
| Verwijderen-item Property           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Verwijderen-service                |         | &check; | &check; | &check; | Alleen op Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Alleen op Windows                     |
| Naam wijzigen-computer               | &check; | &check; | &check; | &check; |                                  |
| Naam wijzigen-item                   | &check; | &check; | &check; | &check; |                                  |
| Naam wijzigen-item Property           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Alleen op Windows                     |
| Oplossen-pad                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Herstellen-computer              | &check; |         |         |         | Alleen op Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Set-klem bord                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-item                      | &check; | &check; | &check; | &check; |                                  |
| Set-item Property              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Set-tijd zone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Alleen op Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Alleen op Windows                     |
| Weer geven-EventLog                 | &check; |         |         |         | Alleen op Windows                     |
| Split-pad                    | &check; | &check; | &check; | &check; |                                  |
| Start-process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Start-trans actie             | &check; |         |         |         | Alleen op Windows                     |
| Stop-computer                 | &check; | &check; | &check; | &check; | Toegevoegde ondersteuning voor Linux/macOS in 7,0 |
| Stoppen-proces                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Alleen op Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Alleen op Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-pad                     | &check; | &check; | &check; | &check; |                                  |
| Ongedaan maken-trans actie              | &check; |         |         |         | Alleen op Windows                     |
| Gebruik-trans actie               | &check; |         |         |         | Alleen op Windows                     |
| Wacht proces                  | &check; | &check; | &check; | &check; | Werkt niet in Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Alleen op Windows                     |

### <a name="microsoftpowershellodatautils"></a>Micro soft. Power shell. ODataUtils

|        Naam van cmdlet        |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Exporteren-ODataEndpointProxy | &check; |      |       |       | Alleen op Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Micro soft. Power shell. Operation. validatie

|        Naam van cmdlet         |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Alleen op Windows |
| Invoke-OperationValidation | &check; |      |       |       | Alleen op Windows |

### <a name="microsoftpowershellsecurity"></a>Micro soft. Power shell. Security

|        Naam van cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   |                  Notitie                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-ACL                   | &check; | &check; | &check; | &check; | Alleen op Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Alleen op Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Ondersteuning voor Linux/macOS toegevoegd in 7,1    |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Retourneert **onbeperkt** op Linux/macOS |
| Get-pfx        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Alleen op Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Ondersteuning voor Linux/macOS toegevoegd in 7,1    |
| Set-ACL                   | &check; | &check; | &check; | &check; | Alleen op Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Alleen op Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Doet niets in Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Alleen op Windows                            |
| Beveiliging opheffen-CmsMessage      | &check; | &check; | &check; | &check; | Ondersteuning voor Linux/macOS toegevoegd in 7,1    |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Naam van cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   |                   Notitie                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Lid toevoegen                | &check; | &check; | &check; | &check; |                                           |
| Add-type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-variabele            | &check; | &check; | &check; | &check; |                                           |
| Compare-object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-CSV           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-JSON          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-prijs verlaging      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-teken reeks        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Fout opsporing-runs Pace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Exporteren-alias              | &check; | &check; | &check; | &check; |                                           |
| Exporteren-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Exporteren-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Exporteren-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-cultuur               | &check; | &check; | &check; | &check; |                                           |
| Ophalen datum                  | &check; | &check; | &check; | &check; |                                           |
| Get-fout                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Ophalen-wille keurig                | &check; | &check; | &check; | &check; |                                           |
| Get-runs Pace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-uptime                |         | &check; | &check; | &check; |                                           |
| Get-variabele              | &check; | &check; | &check; | &check; |                                           |
| Get-term                  |         | &check; | &check; | &check; |                                           |
| Groep-object              | &check; | &check; | &check; | &check; |                                           |
| Import-alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-expressie         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Samen voegen-teken reeks               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Meting object            | &check; | &check; | &check; | &check; |                                           |
| Nieuwe alias                 | &check; | &check; | &check; | &check; |                                           |
| Nieuw-gebeurtenis                 | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| Nieuw-time span              | &check; | &check; | &check; | &check; |                                           |
| Nieuwe variabele              | &check; | &check; | &check; | &check; |                                           |
| Out-file                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; | Alleen op Windows                              |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-teken reeks                | &check; | &check; | &check; | &check; |                                           |
| Read-host                 | &check; | &check; | &check; | &check; |                                           |
| REGI ster-EngineEvent      | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| REGI ster-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Alias verwijderen              |         | &check; | &check; | &check; |                                           |
| Remove-gebeurtenis              | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-variabele           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Selecteer teken reeks             | &check; | &check; | &check; | &check; |                                           |
| Select-XML                | &check; | &check; | &check; | &check; |                                           |
| Bericht verzenden          | &check; | &check; | &check; | &check; |                                           |
| Set-alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-variabele              | &check; | &check; | &check; | &check; |                                           |
| Weer geven-opdracht              | &check; |         | &check; | &check; |                                           |
| Weer geven-prijs verlaging             |         |   6.1   | &check; | &check; |                                           |
| Sorteer object               | &check; | &check; | &check; | &check; |                                           |
| Start-slaap stand               | &check; | &check; | &check; | &check; |                                           |
| T-object                | &check; | &check; | &check; | &check; |                                           |
| Test-JSON                 |         | &check; | &check; | &check; |                                           |
| Tracering-opdracht             | &check; | &check; | &check; | &check; |                                           |
| Blok kering van bestand opheffen              | &check; | &check; | &check; | &check; | Er is ondersteuning toegevoegd voor macOS in 7,0            |
| Registratie ongedaan maken-gebeurtenis          | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wacht debugger             | &check; | &check; | &check; | &check; |                                           |
| Wachten gebeurtenis                | &check; | &check; | &check; | &check; |                                           |
| Schrijf fouten opsporen               | &check; | &check; | &check; | &check; |                                           |
| Schrijf fout               | &check; | &check; | &check; | &check; |                                           |
| Write-host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-output              | &check; | &check; | &check; | &check; |                                           |
| Schrijf voortgang            | &check; | &check; | &check; | &check; |                                           |
| Write-verbose             | &check; | &check; | &check; | &check; |                                           |
| Waarschuwing voor schrijven             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Micro soft. WsMan. Management

|      Naam van cmdlet       |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Alleen op Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Alleen op Windows |
| Verbinding verbreken-WSMan       | &check; | &check; | &check; | &check; | Alleen op Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Alleen op Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Alleen op Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Alleen op Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Alleen op Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Alleen op Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Alleen op Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Alleen op Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Alleen op Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Alleen op Windows |
| Testen-WSMan             | &check; | &check; | &check; | &check; | Alleen op Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Naam van cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Zoeken-pakket             | &check; | &check; | &check; | &check; |      |
| Zoeken-package provider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-package provider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-package provider  | &check; | &check; | &check; | &check; |      |
| REGI ster-PackageSource   | &check; | &check; | &check; | &check; |      |
| Opslaan-pakket             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-pakket        | &check; | &check; | &check; | &check; |      |
| Registratie ongedaan maken-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Naam van cmdlet           |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Zoeken-opdracht                    | &check; | &check; | &check; | &check; |      |
| Zoeken-Dscresource bieden                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Zoeken-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Zoeken-script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Installatie-module                  | &check; | &check; | &check; | &check; |      |
| Install-script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| REGI ster-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-module                | &check; | &check; | &check; | &check; |      |
| Uninstall-script                | &check; | &check; | &check; | &check; |      |
| Registratie ongedaan maken-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Naam van cmdlet                 |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-DscDebug                           | &check; |         |         |         | Alleen op Windows |
| Enable-DscDebug                            | &check; |         |         |         | Alleen op Windows |
| Get-DscConfiguration                       | &check; |         |         |         | Alleen op Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Alleen op Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Alleen op Windows |
| Get-Dscresource bieden                            | &check; | &check; | &check; | &check; |              |
| Invoke-Dscresource bieden                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Alleen op Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Alleen op Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Alleen op Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Alleen op Windows |
| Start-DscConfiguration                     | &check; |         |         |         | Alleen op Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Alleen op Windows |
| Test-DscConfiguration                      | &check; |         |         |         | Alleen op Windows |
| Update-DscConfiguration                    | &check; |         |         |         | Alleen op Windows |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Naam van cmdlet          |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Alleen op Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Alleen op Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Alleen op Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Alleen op Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Alleen op Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Alleen op Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Alleen op Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Alleen op Windows |
| Start-traceren                  | &check; |   6.2   | &check; | &check; | Alleen op Windows |
| Stoppen-traceren                   | &check; |   6.2   | &check; | &check; | Alleen op Windows |

### <a name="psreadline"></a>PSReadline

|         Naam van cmdlet         |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Naam van cmdlet       |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Alleen op Windows |
| Disable-JobTrigger      | &check; |      |       |       | Alleen op Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Alleen op Windows |
| Enable-JobTrigger       | &check; |      |       |       | Alleen op Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Alleen op Windows |
| Get-JobTrigger          | &check; |      |       |       | Alleen op Windows |
| Get-ScheduledJob        | &check; |      |       |       | Alleen op Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Alleen op Windows |
| New-JobTrigger          | &check; |      |       |       | Alleen op Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Alleen op Windows |
| REGI ster-ScheduledJob   | &check; |      |       |       | Alleen op Windows |
| Remove-JobTrigger       | &check; |      |       |       | Alleen op Windows |
| Set-JobTrigger          | &check; |      |       |       | Alleen op Windows |
| Set-ScheduledJob        | &check; |      |       |       | Alleen op Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Alleen op Windows |
| Registratie ongedaan maken-ScheduledJob | &check; |      |       |       | Alleen op Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Naam van cmdlet          |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-New psworkflowexecutionoption | &check; |      |       |       | Alleen op Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Alleen op Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Alleen op Windows |

### <a name="threadjob"></a>ThreadJob

|   Naam van cmdlet   |  5.1  |   6.x   |   7.0   |   7.1   | Notitie |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | Kan worden geïnstalleerd in Power shell 5,1 |
