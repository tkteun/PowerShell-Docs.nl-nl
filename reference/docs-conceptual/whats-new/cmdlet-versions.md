---
ms.date: 02/03/2020
keywords: Power shell, kern
title: Release geschiedenis van modules en cmdlets
description: Dit artikel bevat een lijst met de modules en cmdlets die zijn opgenomen in verschillende versies van Power shell.
ms.openlocfilehash: e79735e516c9aaa485c6513fb80de623014f06f5
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810348"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Release geschiedenis van modules en cmdlets

Dit artikel bevat een lijst met de modules en cmdlets die zijn opgenomen in verschillende versies van Power shell. Dit is een overzicht van de informatie die is gevonden in de release opmerkingen. Meer gedetailleerde informatie vindt u in de opmerkingen bij de release:

- [Wat is er nieuw in PowerShell 7.0?](what-s-new-in-powershell-70.md)

Dit is een onderhanden werk. Help ons deze gegevens actueel te houden.

## <a name="module-release-history"></a>Release geschiedenis van de module

|         Module naam/PS-versie          |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Alleen in Windows |
| ISE (geïntroduceerd in 2,0)                   | &check; |         |         |         | Alleen in Windows |
| Micro soft. Power shell. Archive              | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. core                 | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. Diagnostics          | &check; | &check; | &check; | &check; | Alleen in Windows |
| Micro soft. Power shell. host                 | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. LocalAccounts        | &check; |         |         |         | Alleen in Windows |
| Micro soft. Power shell. Management           | &check; | &check; | &check; | &check; |              |
| Micro soft. Power shell. ODataUtils           | &check; |         |         |         | Alleen in Windows |
| Micro soft. Power shell. Operation. validatie | &check; |         |         |         | Alleen in Windows |
| Micro soft. Power shell. Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Micro soft. WsMan. Management                | &check; | &check; | &check; | &check; | Alleen in Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Alleen in Windows |
| PSReadline 1. x                            | &check; |         |         |         | Alleen in Windows |
| PSReadline 2,0                            |         | &check; | &check; |         |              |
| PSReadline 2,1                            |         |         |         | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Alleen in Windows |
| PSWorkflow                                | &check; |         |         |         | Alleen in Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Alleen in Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | Kan worden geïnstalleerd in Power shell 5,1 |

## <a name="cmdlet-release-history"></a>Release geschiedenis van de cmdlet

### <a name="cimcmdlets"></a>CimCmdlets

|         Naam van cmdlet         |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Alleen in Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Alleen in Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Alleen in Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Alleen in Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Alleen in Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Alleen in Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Alleen in Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Alleen in Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Alleen in Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Alleen in Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Alleen in Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Alleen in Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Alleen in Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Alleen in Windows |

### <a name="ise-introduced-in-20"></a>ISE (geïntroduceerd in 2,0)

|    Naam van cmdlet    |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Alleen in Windows |
| Import-IseSnippet | &check; |      |       |       | Alleen in Windows |
| New-IseSnippet    | &check; |      |       |       | Alleen in Windows |

### <a name="microsoftpowershellarchive"></a>Micro soft. Power shell. Archive

|   Naam van cmdlet    |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Micro soft. Power shell. core

|            Naam van cmdlet            |   5.1   |   6.x   |   7.0   |   7.1   |            Notitie            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Alleen in Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6,2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Enable-ExperimentalFeature        |         |   6,2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Alleen in Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6,2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Toegevoegde Linux-ondersteuning in 6,2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Alleen in Windows               |
| Get-Verb                          | &check; |         |         |         | Verplaatst naar micro soft. Power shell. Utility 6.0 + |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-opdracht                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Alleen in Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Alleen in Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Alleen in Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Alleen in Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Micro soft. Power shell. Diagnostics

|  Naam van cmdlet   |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Alleen in Windows |
| Get-Counter    | &check; |         | &check; | &check; | Alleen in Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Alleen in Windows |
| Import-Counter | &check; |         |         |         | Alleen in Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | Alleen in Windows |

### <a name="microsoftpowershellhost"></a>Micro soft. Power shell. host

|   Naam van cmdlet    |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Micro soft. Power shell. LocalAccounts

|       Naam van cmdlet       |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Alleen in Windows |
| Disable-LocalUser       | &check; |      |       |       | Alleen in Windows |
| Enable-LocalUser        | &check; |      |       |       | Alleen in Windows |
| Get-LocalGroup          | &check; |      |       |       | Alleen in Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Alleen in Windows |
| Get-LocalUser           | &check; |      |       |       | Alleen in Windows |
| New-LocalGroup          | &check; |      |       |       | Alleen in Windows |
| New-LocalUser           | &check; |      |       |       | Alleen in Windows |
| Remove-LocalGroup       | &check; |      |       |       | Alleen in Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Alleen in Windows |
| Remove-LocalUser        | &check; |      |       |       | Alleen in Windows |
| Rename-LocalGroup       | &check; |      |       |       | Alleen in Windows |
| Rename-LocalUser        | &check; |      |       |       | Alleen in Windows |
| Set-LocalGroup          | &check; |      |       |       | Alleen in Windows |
| Set-LocalUser           | &check; |      |       |       | Alleen in Windows |

### <a name="microsoftpowershellmanagement"></a>Micro soft. Power shell. Management

|          Naam van cmdlet          |   5.1   |   6.x   |   7.0   |   7.1   |               Notitie               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Alleen in Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Alleen in Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Alleen in Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Alleen in Windows                     |
| Complete-Transaction          | &check; |         |         |         | Alleen in Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Alleen in Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Alleen in Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | Niet ondersteund op macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Get-ComputerRestorePoint      | &check; |         |         |         | Alleen in Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Alleen in Windows                     |
| Get-EventLog                  | &check; |         |         |         | Alleen in Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Alleen in Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Get-Transaction               | &check; |         |         |         | Alleen in Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Alleen in Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Alleen in Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Alleen in Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Alleen in Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Alleen in Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Alleen in Windows                     |
| Remove-Computer               | &check; |         |         |         | Alleen in Windows                     |
| Remove-EventLog               | &check; |         |         |         | Alleen in Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Alleen in Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Alleen in Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Alleen in Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; | Toegevoegde ondersteuning voor Linux/macOS in 7,1 |
| Restart-Service               | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Restore-Computer              | &check; |         |         |         | Alleen in Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Set-WmiInstance               | &check; |         |         |         | Alleen in Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Alleen in Windows                     |
| Show-EventLog                 | &check; |         |         |         | Alleen in Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Start-Transaction             | &check; |         |         |         | Alleen in Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | Toegevoegde ondersteuning voor Linux/macOS in 7,1 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Alleen in Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Alleen in Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Alleen in Windows                     |
| Use-Transaction               | &check; |         |         |         | Alleen in Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | Werkt niet in Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Alleen in Windows                     |

### <a name="microsoftpowershellodatautils"></a>Micro soft. Power shell. ODataUtils

|        Naam van cmdlet        |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Alleen in Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Micro soft. Power shell. Operation. validatie

|        Naam van cmdlet         |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Alleen in Windows |
| Invoke-OperationValidation | &check; |      |       |       | Alleen in Windows |

### <a name="microsoftpowershellsecurity"></a>Micro soft. Power shell. Security

|        Naam van cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   |                  Notitie                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Alleen in Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Alleen in Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Ondersteuning voor Linux/macOS toegevoegd in 7,1    |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Retourneert **onbeperkt** op Linux/macOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Alleen in Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Ondersteuning voor Linux/macOS toegevoegd in 7,1    |
| Set-Acl                   | &check; | &check; | &check; | &check; | Alleen in Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Alleen in Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Doet niets in Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Alleen in Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Ondersteuning voor Linux/macOS toegevoegd in 7,1    |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Naam van cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   |                   Notitie                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; | Alleen in Windows                              |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; | Verplaatst van micro soft. Power shell. core     |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; | Alleen in Windows                              |
| Out-Printer               | &check; |         | &check; | &check; | Alleen in Windows                              |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; | Alleen in Windows                              |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | Er is ondersteuning toegevoegd voor macOS in 7,0            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Er zijn geen gebeurtenis bronnen beschikbaar in Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Micro soft. WsMan. Management

|      Naam van cmdlet       |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Alleen in Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Alleen in Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Alleen in Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Alleen in Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Alleen in Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Alleen in Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Alleen in Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Alleen in Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Alleen in Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Alleen in Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Alleen in Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Alleen in Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | Alleen in Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Naam van cmdlet        |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Naam van cmdlet           |   5.1   |   6.x   |   7.0   |   7.1   | Notitie |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Naam van cmdlet                 |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-DscDebug                           | &check; |         |         |         | Alleen in Windows |
| Enable-DscDebug                            | &check; |         |         |         | Alleen in Windows |
| Get-DscConfiguration                       | &check; |         |         |         | Alleen in Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Alleen in Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Alleen in Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Alleen in Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Alleen in Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Alleen in Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Alleen in Windows |
| Start-DscConfiguration                     | &check; |         |         |         | Alleen in Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Alleen in Windows |
| Test-DscConfiguration                      | &check; |         |         |         | Alleen in Windows |
| Update-DscConfiguration                    | &check; |         |         |         | Alleen in Windows |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Naam van cmdlet          |   5.1   |   6.x   |   7.0   |   7.1   |     Notitie     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6,2   | &check; | &check; | Alleen in Windows |
| Disable-PSWSManCombinedTrace | &check; |   6,2   | &check; | &check; | Alleen in Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Alleen in Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Alleen in Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Alleen in Windows |
| Enable-WSManTrace            | &check; |   6,2   | &check; | &check; | Alleen in Windows |
| Get-LogProperties            | &check; |   6,2   | &check; | &check; | Alleen in Windows |
| Set-LogProperties            | &check; |   6,2   | &check; | &check; | Alleen in Windows |
| Start-Trace                  | &check; |   6,2   | &check; | &check; | Alleen in Windows |
| Stop-Trace                   | &check; |   6,2   | &check; | &check; | Alleen in Windows |

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
| Add-JobTrigger          | &check; |      |       |       | Alleen in Windows |
| Disable-JobTrigger      | &check; |      |       |       | Alleen in Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Alleen in Windows |
| Enable-JobTrigger       | &check; |      |       |       | Alleen in Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Alleen in Windows |
| Get-JobTrigger          | &check; |      |       |       | Alleen in Windows |
| Get-ScheduledJob        | &check; |      |       |       | Alleen in Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Alleen in Windows |
| New-JobTrigger          | &check; |      |       |       | Alleen in Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Alleen in Windows |
| Register-ScheduledJob   | &check; |      |       |       | Alleen in Windows |
| Remove-JobTrigger       | &check; |      |       |       | Alleen in Windows |
| Set-JobTrigger          | &check; |      |       |       | Alleen in Windows |
| Set-ScheduledJob        | &check; |      |       |       | Alleen in Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Alleen in Windows |
| Unregister-ScheduledJob | &check; |      |       |       | Alleen in Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Naam van cmdlet          |   5.1   | 6.x  |  7.0  |  7.1  |     Notitie     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Alleen in Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Alleen in Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Alleen in Windows |

### <a name="threadjob"></a>ThreadJob

|   Naam van cmdlet   |  5.1  |   6.x   |   7.0   |   7.1   | Notitie |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | Kan worden geïnstalleerd in Power shell 5,1 |
