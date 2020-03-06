---
ms.date: 02/03/2020
keywords: Power shell, kern
title: Release geschiedenis van modules en cmdlets
ms.openlocfilehash: 9b7c769198fa2a39d8efcc9602f2a913c041289c
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404967"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Release geschiedenis van modules en cmdlets

In dit artikel vindt u een lijst met de modules en cmdlets die worden geleverd met verschillende versies van Power shell. Dit is een overzicht van de informatie die is gevonden in de release opmerkingen. Meer gedetailleerde informatie vindt u in de opmerkingen bij de release:

- [Wat is er nieuw in Power shell Core 6,2](what-s-new-in-powershell-core-62.md)
- [Wat is er nieuw in Power shell Core 6,1](what-s-new-in-powershell-core-61.md)
- [Wat is er nieuw in Power shell Core 6,0](what-s-new-in-powershell-core-60.md)
- [Belang rijke wijzigingen in Power shell Core 6,0](breaking-changes-ps6.md)
- [Bekende problemen in Power shell Core 6,0](known-issues-ps6.md)

Dit is een onderhanden werk. Help ons deze gegevens actueel te houden.

## <a name="module-release-history"></a>Release geschiedenis van de module

|         Module naam/PS-versie          |   5,1   |   6.x   |   7.0   |   7.1   |     Opmerking     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Alleen Windows |
| ISE (geïntroduceerd in 2,0)                   | &check; |         |         |         | Alleen Windows |
| Micro soft. Power shell. Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Alleen Windows |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. LocalAccounts        | &check; |         |         |         | Alleen Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. ODataUtils           | &check; |         |         |         | Alleen Windows |
| Micro soft. Power shell. Operation. validatie | &check; |         |         |         | Alleen Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Micro soft. WsMan. Management                | &check; | &check; | &check; | &check; | Alleen Windows |
| Package Management                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Alleen Windows |
| PSReadline 1. x                            | &check; |         |         |         | Alleen Windows |
| PSReadline 2. x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Alleen Windows |
| PSWorkflow                                | &check; |         |         |         | Alleen Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Alleen Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | Kan worden geïnstalleerd in Power shell 5,1 |

## <a name="cmdlet-release-history"></a>Release geschiedenis van de cmdlet

### <a name="cimcmdlets"></a>CimCmdlets

|         Naam van cmdlet         |   5,1   |   6.x   |   7.0   |   7.1   |     Opmerking     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Alleen Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Alleen Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Alleen Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Alleen Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Alleen Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Alleen Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Alleen Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Alleen Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Alleen Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Alleen Windows |
| REGI ster-CimIndicationEvent | &check; | &check; | &check; | &check; | Alleen Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Alleen Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Alleen Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Alleen Windows |

### <a name="ise-introduced-in-20"></a>ISE (geïntroduceerd in 2,0)

|    Naam van cmdlet    |   5,1   | 6.x  |  7.0  |  7.1  |     Opmerking     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Alleen Windows |
| Import-IseSnippet | &check; |      |       |       | Alleen Windows |
| New-IseSnippet    | &check; |      |       |       | Alleen Windows |


### <a name="microsoftpowershellarchive"></a>Micro soft. Power shell. Archive

|   Naam van cmdlet    |   5,1   |   6.x   |   7.0   |   7.1   | Opmerking |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Comprimeren-archief | &check; | &check; | &check; | &check; |      |
| Uitvouwen-archief   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Naam van cmdlet            |   5,1   |   6.x   |   7.0   |   7.1   |            Opmerking            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Alleen Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Wissen-host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Alleen Windows               |
| Fout opsporing-taak                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Alleen Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Alleen Windows               |
| Verbinding verbreken-PSSession              | &check; | &check; | &check; | &check; | Alleen Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Alleen Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Alleen Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Afsluiten-PSHostProcess                | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Alleen Windows               |
| Exporteren-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-job                           | &check; | &check; | &check; | &check; |                            |
| Get-module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Alleen Windows               |
| Get-term                          | &check; |         |         |         | Verplaatst naar micro soft. Power shell. Utility 6.0 + |
| Import-module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-opdracht                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Alleen Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-standaard                       | &check; | &check; | &check; | &check; |                            |
| Out-host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Alleen Windows               |
| REGI ster-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| REGI ster-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Alleen Windows               |
| Verwijderen-taak                        | &check; | &check; | &check; | &check; |                            |
| Remove-module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Alleen Windows               |
| Resume-job                        | &check; |         |         |         |                            |
| Help opslaan                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Alleen Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Begin taak                         | &check; | &check; | &check; | &check; |                            |
| Stoppen-taak                          | &check; | &check; | &check; | &check; |                            |
| Onderbreken-taak                       | &check; |         |         |         | Alleen Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Alleen Windows               |
| Registratie ongedaan maken-PSSessionConfiguration | &check; | &check; | &check; | &check; | Alleen Windows               |
| Help bijwerken                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Naam van cmdlet   |   5,1   |   6.x   |   7.0   |   7.1   |     Opmerking     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Exporteren-teller | &check; |         |         |         | Alleen Windows |
| Get-teller    | &check; |         | &check; | &check; | Alleen Windows |
| Get-Wine vent   | &check; | &check; | &check; | &check; | Alleen Windows |
| Import teller | &check; |         |         |         | Alleen Windows |
| New-Wine vent   | &check; | &check; | &check; | &check; | Alleen Windows |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Naam van cmdlet    |   5,1   |   6.x   |   7.0   |   7.1   | Opmerking |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Micro soft. Power shell. LocalAccounts

|       Naam van cmdlet       |   5,1   | 6.x  |  7.0  |  7.1  |     Opmerking     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Alleen Windows |
| Disable-Lokalegebruiker       | &check; |      |       |       | Alleen Windows |
| Enable-Lokalegebruiker        | &check; |      |       |       | Alleen Windows |
| Get-LocalGroup          | &check; |      |       |       | Alleen Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Alleen Windows |
| Get-Lokalegebruiker           | &check; |      |       |       | Alleen Windows |
| Nieuw-LocalGroup          | &check; |      |       |       | Alleen Windows |
| New-Lokalegebruiker           | &check; |      |       |       | Alleen Windows |
| Remove-LocalGroup       | &check; |      |       |       | Alleen Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Alleen Windows |
| Remove-Lokalegebruiker        | &check; |      |       |       | Alleen Windows |
| Rename-LocalGroup       | &check; |      |       |       | Alleen Windows |
| Naam wijzigen-Lokalegebruiker        | &check; |      |       |       | Alleen Windows |
| Set-LocalGroup          | &check; |      |       |       | Alleen Windows |
| Set-Lokalegebruiker           | &check; |      |       |       | Alleen Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Naam van cmdlet          |   5,1   |   6.x   |   7.0   |   7.1   |               Opmerking               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Alleen Windows                     |
| Add-content                   | &check; | &check; | &check; | &check; |                                  |
| Controle punt-computer           | &check; |         |         |         | Alleen Windows                     |
| Wissen-inhoud                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Alleen Windows                     |
| Wissen-item                    | &check; | &check; | &check; | &check; |                                  |
| Wissen-item Property            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Alleen Windows                     |
| Complete-Transaction          | &check; |         |         |         | Alleen Windows                     |
| Convert-pad                  | &check; | &check; | &check; | &check; |                                  |
| Kopie-item                     | &check; | &check; | &check; | &check; |                                  |
| Kopiëren-item Property             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Alleen Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Alleen Windows                     |
| Get-Child item                 | &check; | &check; | &check; | &check; |                                  |
| Get-klem bord                 | &check; |         | &check; | &check; | Niet ondersteund op macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Alleen Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Alleen Windows                     |
| Get-EventLog                  | &check; |         |         |         | Alleen Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Alleen Windows                     |
| Get-item                      | &check; | &check; | &check; | &check; |                                  |
| Get-item Property              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-locatie                  | &check; | &check; | &check; | &check; |                                  |
| Ophalen-proces                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-service                   | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Get-time zone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | Alleen Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Alleen Windows                     |
| Invoke-item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Alleen Windows                     |
| Pad voor samen voegen                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Alleen Windows                     |
| Item verplaatsen                     | &check; | &check; | &check; | &check; |                                  |
| Verplaatsen-item Property             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Alleen Windows                     |
| Nieuw-item                      | &check; | &check; | &check; | &check; |                                  |
| Nieuw-item Property              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Nieuwe service                   | &check; | &check; | &check; | &check; | Alleen Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Alleen Windows                     |
| Pop-locatie                  | &check; | &check; | &check; | &check; |                                  |
| Push-locatie                 | &check; | &check; | &check; | &check; |                                  |
| REGI ster-WmiEvent             | &check; |         |         |         | Alleen Windows                     |
| Remove-Computer               | &check; |         |         |         | Alleen Windows                     |
| Remove-EventLog               | &check; |         |         |         | Alleen Windows                     |
| Verwijderen-item                   | &check; | &check; | &check; | &check; |                                  |
| Verwijderen-item Property           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Verwijderen-service                |         | &check; | &check; | &check; | Alleen Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Alleen Windows                     |
| Naam wijzigen-computer               | &check; | &check; | &check; | &check; |                                  |
| Naam wijzigen-item                   | &check; | &check; | &check; | &check; |                                  |
| Naam wijzigen-item Property           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Alleen Windows                     |
| Oplossen-pad                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-service               | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Herstellen-computer              | &check; |         |         |         | Alleen Windows                     |
| Hervatten-service                | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Set-klem bord                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-item                      | &check; | &check; | &check; | &check; |                                  |
| Set-item Property              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-service                   | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Set-tijd zone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Alleen Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Alleen Windows                     |
| Show-EventLog                 | &check; |         |         |         | Alleen Windows                     |
| Split-pad                    | &check; | &check; | &check; | &check; |                                  |
| Start-process                 | &check; | &check; | &check; | &check; |                                  |
| Start-service                 | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Start-Transaction             | &check; |         |         |         | Alleen Windows                     |
| Stop-computer                 | &check; | &check; | &check; | &check; | Toegevoegde ondersteuning voor Linux/macOS in 7,0 |
| Stoppen-proces                  | &check; | &check; | &check; | &check; |                                  |
| Stoppen-service                  | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Suspend-service               | &check; | &check; | &check; | &check; | Alleen Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Alleen Windows                     |
| Testen: verbinding               | &check; | &check; | &check; | &check; |                                  |
| Test-pad                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Alleen Windows                     |
| Use-Transaction               | &check; |         |         |         | Alleen Windows                     |
| Wacht proces                  | &check; | &check; | &check; | &check; | Werkt niet in Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Alleen Windows                     |

### <a name="microsoftpowershellodatautils"></a>Micro soft. Power shell. ODataUtils

|        Naam van cmdlet        |   5,1   | 6.x  |  7.0  |  7.1  |     Opmerking     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Exporteren-ODataEndpointProxy | &check; |      |       |       | Alleen Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Micro soft. Power shell. Operation. validatie

|        Naam van cmdlet         |   5,1   | 6.x  |  7.0  |  7.1  |     Opmerking     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Alleen Windows |
| Invoke-OperationValidation | &check; |      |       |       | Alleen Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Naam van cmdlet        |   5,1   |   6.x   |   7.0   |   7.1   |                  Opmerking                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Retourneert **onbeperkt** op Linux/macOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Set-ACL                   | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Doet niets in Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Alleen Windows                            |
| Beveiliging opheffen-CmsMessage      | &check; | &check; | &check; | &check; | Alleen Windows                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Naam van cmdlet        |   5,1   |   6.x   |   7.0   |   7.1   |                   Opmerking                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Lid toevoegen                | &check; | &check; | &check; | &check; |                                           |
| Add-type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
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
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Exporteren-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Exporteren-CSV                | &check; | &check; | &check; | &check; |                                           |
| Exporteren-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Exporteren-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
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
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-term                  |         | &check; | &check; | &check; |                                           |
| Groep-object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-CSV                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-expressie         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Samen voegen-teken reeks               |         | &check; | &check; | &check; |                                           |
| Meting-opdracht           | &check; | &check; | &check; | &check; |                                           |
| Meting object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| Nieuw-object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| Nieuw-time span              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-file                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; | Alleen Windows                              |
| Out-printer               | &check; |         | &check; | &check; |                                           |
| Out-teken reeks                | &check; | &check; | &check; | &check; |                                           |
| Read-host                 | &check; | &check; | &check; | &check; |                                           |
| REGI ster-EngineEvent      | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| REGI ster-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Alias verwijderen              |         | &check; | &check; | &check; |                                           |
| Remove-gebeurtenis              | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Selecteer teken reeks             | &check; | &check; | &check; | &check; |                                           |
| Select-XML                | &check; | &check; | &check; | &check; |                                           |
| Bericht verzenden          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Weer geven-opdracht              | &check; |         | &check; | &check; |                                           |
| Weer geven-prijs verlaging             |         |   6.1   | &check; | &check; |                                           |
| Sorteer object               | &check; | &check; | &check; | &check; |                                           |
| Start-slaap stand               | &check; | &check; | &check; | &check; |                                           |
| T-object                | &check; | &check; | &check; | &check; |                                           |
| Test-JSON                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Blok kering van bestand opheffen              | &check; | &check; | &check; | &check; | Er is ondersteuning toegevoegd voor macOS in 7,0            |
| Registratie ongedaan maken-gebeurtenis          | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-lijst               | &check; |         | &check; | &check; |                                           |
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

|      Naam van cmdlet       |   5,1   |   6.x   |   7.0   |   7.1   |     Opmerking     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Alleen Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Alleen Windows |
| Verbinding verbreken-WSMan       | &check; | &check; | &check; | &check; | Alleen Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Alleen Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Alleen Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Alleen Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Alleen Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Alleen Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Alleen Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Alleen Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Alleen Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Alleen Windows |
| Testen-WSMan             | &check; | &check; | &check; | &check; | Alleen Windows |

### <a name="packagemanagement"></a>Package Management

|       Naam van cmdlet        |   5,1   |   6.x   |   7.0   |   7.1   | Opmerking |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Zoeken-pakket             | &check; | &check; | &check; | &check; |      |
| Zoeken-package provider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-package provider   | &check; | &check; | &check; | &check; |      |
| Installeren-pakket          | &check; | &check; | &check; | &check; |      |
| Install-package provider  | &check; | &check; | &check; | &check; |      |
| REGI ster-PackageSource   | &check; | &check; | &check; | &check; |      |
| Opslaan-pakket             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-pakket        | &check; | &check; | &check; | &check; |      |
| Registratie ongedaan maken-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Naam van cmdlet           |   5,1   |   6.x   |   7.0   |   7.1   | Opmerking |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Zoeken-opdracht                    | &check; | &check; | &check; | &check; |      |
| Zoeken-Dscresource bieden                | &check; | &check; | &check; | &check; |      |
| Zoek module                     | &check; | &check; | &check; | &check; |      |
| Zoeken-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Zoeken-script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Installatie-module                  | &check; | &check; | &check; | &check; |      |
| Install-script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-module                  | &check; | &check; | &check; | &check; |      |
| Publiceren-script                  | &check; | &check; | &check; | &check; |      |
| REGI ster-PSRepository           | &check; | &check; | &check; | &check; |      |
| Opslaan-module                     | &check; | &check; | &check; | &check; |      |
| Opslaan-script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-module                | &check; | &check; | &check; | &check; |      |
| Uninstall-script                | &check; | &check; | &check; | &check; |      |
| Registratie ongedaan maken-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Naam van cmdlet                 |   5,1   |   6.x   |   7.0   |   7.1   |     Opmerking     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Alleen Windows |
| Enable-DscDebug                            | &check; |         |         |         | Alleen Windows |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Alleen Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Alleen Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Alleen Windows |
| Get-Dscresource bieden                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialisatie-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-Dscresource bieden                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Alleen Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Alleen Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Alleen Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Alleen Windows |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Alleen Windows |
| Stoppen-DscConfiguration                      | &check; |         |         |         | Alleen Windows |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Alleen Windows |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | Alleen Windows |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Schrijf logboek                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Naam van cmdlet          |   5,1   |   6.x   |   7.0   |   7.1   |     Opmerking     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Alleen Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Alleen Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Alleen Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Alleen Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Alleen Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Alleen Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Alleen Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Alleen Windows |
| Start-traceren                  | &check; |   6.2   | &check; | &check; | Alleen Windows |
| Stoppen-traceren                   | &check; |   6.2   | &check; | &check; | Alleen Windows |

### <a name="psreadline"></a>PSReadline

|         Naam van cmdlet         |   5,1   |   6.x   |   7.0   |   7.1   | Opmerking |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Naam van cmdlet       |   5,1   | 6.x  |  7.0  |  7.1  |     Opmerking     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Alleen Windows |
| Disable-JobTrigger      | &check; |      |       |       | Alleen Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Alleen Windows |
| Enable-JobTrigger       | &check; |      |       |       | Alleen Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Alleen Windows |
| Get-JobTrigger          | &check; |      |       |       | Alleen Windows |
| Get-ScheduledJob        | &check; |      |       |       | Alleen Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Alleen Windows |
| New-JobTrigger          | &check; |      |       |       | Alleen Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Alleen Windows |
| REGI ster-ScheduledJob   | &check; |      |       |       | Alleen Windows |
| Remove-JobTrigger       | &check; |      |       |       | Alleen Windows |
| Set-JobTrigger          | &check; |      |       |       | Alleen Windows |
| Set-ScheduledJob        | &check; |      |       |       | Alleen Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Alleen Windows |
| Registratie ongedaan maken-ScheduledJob | &check; |      |       |       | Alleen Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Naam van cmdlet          |   5,1   | 6.x  |  7.0  |  7.1  |     Opmerking     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-New psworkflowexecutionoption | &check; |      |       |       | Alleen Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Alleen Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Alleen Windows |

### <a name="threadjob"></a>ThreadJob

|   Naam van cmdlet   |  5,1  |   6.x   |   7.0   |   7.1   | Opmerking |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | Kan worden geïnstalleerd in Power shell 5,1 |
