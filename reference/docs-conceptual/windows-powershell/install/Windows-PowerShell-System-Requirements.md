---
ms.date: 12/06/2019
keywords: powershell,cmdlet
title: Windows PowerShell-systeemvereisten
ms.openlocfilehash: 7c6e055cda8493651a7838b4ffc9a933032d9c0f
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809985"
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell-systeemvereisten

In dit artikel vindt u een overzicht van de systeem vereisten voor Windows Power Shell 3,0, Windows Power Shell 4,0, Windows Power shell 5,0 en Windows Power shell 5,1. En speciale functies, zoals Windows Power shell Integrated Scripting Environment (ISE), Common Information Model (CIM)-opdrachten en werk stromen.

Windows® 8,1 en Windows Server® 2012 R2 bevatten alle vereiste Program ma's. Dit artikel is bedoeld voor gebruikers van eerdere versies van Windows.

## <a name="operating-system-requirements"></a>Vereisten voor het besturingssysteem

### <a name="windows-powershell-51"></a>Windows Power shell 5,1

Windows Power shell 5,1 wordt uitgevoerd op de volgende versies van Windows. Als u Windows Power shell 5,1 wilt uitvoeren, installeert u Windows Management Framework 5,1. Zie [WMF 5,1 installeren en configureren](../wmf/setup/install-configure.md)voor meer informatie.

|              Windows-versie               |                           Systeemvereiste                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | Standaard geïnstalleerd                                                    |
| Windows Server 2016                        | Standaard geïnstalleerd                                                    |
| Windows Server 2012 R2                     | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 met Service Pack 1 | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 10 versie 1607 en hoger             | Standaard geïnstalleerd                                                    |
| Windows 10 versie 1507, 1511              | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 8.1                                | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 7 met Service Pack 1              | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-50"></a>Windows PowerShell 5.0

Windows Power shell 5,0 wordt uitgevoerd op de volgende versies van Windows. Als u Windows Power shell 5,0 wilt uitvoeren, installeert u Windows Management Framework 5,1. Zie [WMF 5,1 installeren en configureren](../wmf/setup/install-configure.md)voor meer informatie. Windows Management Framework 5,1 vervangt Windows Management Framework 5,0.

|              Windows-versie               |                           Systeemvereiste                            |
| ------------------------------------------ | ----------------------------------------------------------------------- |
| Windows Server 2019                        | Standaard is een hogere versie geïnstalleerd                                     |
| Windows Server 2016                        | Standaard is een hogere versie geïnstalleerd                                     |
| Windows Server 2012 R2                     | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2012                        | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows Server 2008 R2 met Service Pack 1 | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 10 versie 1607 en hoger             | Standaard is een hogere versie geïnstalleerd                                     |
| Windows 10 versie 1507, 1511              | Standaard geïnstalleerd                                                    |
| Windows 8.1                                | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |
| Windows 7 met Service Pack 1              | Installeer [Windows Management Framework 5,1](https://aka.ms/wmf5download) |

### <a name="windows-powershell-40"></a>Windows PowerShell 4.0

Windows Power Shell 4,0 wordt uitgevoerd op de volgende versies van Windows. Als u Windows Power Shell 4,0 wilt uitvoeren, installeert u de opgegeven versie van het Windows Management Framework voor uw besturings systeem.

|               Windows-versie               |                                             Systeemvereiste                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8.1                                 | Standaard geïnstalleerd                                                                                       |
| Windows Server 2012 R2                      | Standaard geïnstalleerd                                                                                       |
| Windows® 7 met Service Pack 1              | Installeer [Windows Management Framework 4,0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |
| Windows Server® 2008 R2 met Service Pack 1 | Installeer [Windows Management Framework 4,0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) |

### <a name="windows-powershell-30"></a>Windows PowerShell 3.0

Windows Power Shell 3,0 wordt uitgevoerd op de volgende versies van Windows. Als u Windows Power Shell 3,0 wilt uitvoeren, installeert u de opgegeven versie van het Windows Management Framework voor uw besturings systeem.

|               Windows-versie               |                                             Systeemvereiste                                             |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Windows 8                                   | Standaard geïnstalleerd                                                                                       |
| Windows Server 2012                         | Standaard geïnstalleerd                                                                                       |
| Windows® 7 met Service Pack 1              | Installeer [Windows Management Framework 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server® 2008 R2 met Service Pack 1 | Installeer [Windows Management Framework 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |
| Windows Server 2008 met Service Pack 2     | Installeer [Windows Management Framework 3,0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) |

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework-vereisten

De volgende tabel bevat de .NET Framework vereisten voor Windows Power shell.

|        Versie         |                                                                                 .NET-vereiste                                                                                  |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Windows Power shell 5,1 | Vereist de volledige installatie van Microsoft .NET Framework 4,5. Windows 8,1 en Windows Server 2012 R2 bevatten standaard Microsoft .NET Framework 4,5.                           |
| Windows PowerShell 5.0 | Vereist de volledige installatie van Microsoft .NET Framework 4,5. Windows 8,1 en Windows Server 2012 R2 bevatten standaard Microsoft .NET Framework 4,5.                           |
| Windows PowerShell 4.0 | Vereist de volledige installatie van Microsoft .NET Framework 4,5. Windows 8,1 en Windows Server 2012 R2 bevatten standaard Microsoft .NET Framework 4,5.                           |
| Windows PowerShell 3.0 | Vereist de volledige installatie van Microsoft .NET Framework 4. Windows 8 en Windows Server 2012 bevatten standaard Microsoft .NET Framework 4,5, waarmee aan deze vereiste wordt voldaan. |

Gebruik de volgende koppelingen om Microsoft .NET Framework te downloaden van het micro soft Download centrum.

|                     Versie                      |                                                     Koppeling                                                     |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| .NET Framework 4,5 ( `dotNetFx45_Full_setup.exe` ) | [Microsoft .NET Framework 4.5](https://go.microsoft.com/fwlink/?LinkID=242919)                               |
| .NET Framework 4 ( `dotNetFx40_Full_setup.exe` )   | [Microsoft .NET Framework 4 (Webinstallatie)](https://www.microsoft.com/en-us/download/details.aspx?id=17851) |

## <a name="windows-management-framework-40"></a>Windows Management Framework 4,0

Windows Power shell 5,0 vereist dat Windows Management Framework 4,0 vooraf is geïnstalleerd op Windows Server 2008 R2 SP1 en Windows 7 SP1.

## <a name="ws-management-30"></a>WS-Management 3,0

Windows Power Shell 3,0 en Windows Power Shell 4,0 vereisen WS-Management 3,0, dat ondersteuning biedt voor de WinRM-service en het WSMan-protocol. Dit programma is opgenomen in Windows 8,1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4,0 en Windows Management Framework 3,0.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3,0

Windows Power Shell 3,0 en Windows Power Shell 4,0 vereisen Windows Management Instrumentation 3,0 (WMI). Dit programma is opgenomen in Windows 8,1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4,0 en Windows Management Framework 3,0. Als dit programma niet is geïnstalleerd op de computer, worden functies waarvoor WMI is vereist, zoals CIM-opdrachten, niet uitgevoerd.

## <a name="common-language-runtime-40"></a>Common language runtime 4,0

Windows Power Shell 3,0, Windows Power Shell 4,0 en Windows Power shell 5,0 worden gecompileerd op basis van common language runtime (CLR) 4,0.

## <a name="graphical-user-interface-requirements"></a>Vereisten voor grafische gebruikers interface

Windows Power shell is een op een console gebaseerde toepassing waarvoor geen Graphical User Interface nodig is.
Het is goed geschikt voor computers die geen schermen of monitors hebben, of een gebruikers interface, zoals de Server Core-installatie opties van Windows Server 2012 R2 of Windows Server 2012.

Voor sommige items is een Graphical User Interface vereist. Zie het Help-artikel voor elk item voor meer informatie.

- Windows Power shell Integrated Scripting Environment (ISE). Zie [Inleiding tot de Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise)voor meer informatie.
- Cmdlets
  - [Out-GridView](/powershell/module/microsoft.powershell.utility/out-gridview)
  - [Weer geven-opdracht](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)
  - [Show-ControlPanelItem](/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)
  - [Weer geven-EventLog](/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)
- Parameters
  - De **ShowWindow** -para meter van de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) .
  - De para meter **ShowSecurityDescriptorUI** van de cmdlets [REGI ster-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) en [set-PSSessionConfiguration](/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) .

## <a name="windows-powershell-engine-requirements"></a>Windows Power shell-engine vereisten

Windows Power Shell 4,0 is ontworpen om achterwaarts compatibel te zijn met Windows Power Shell 3,0 en Windows Power Shell 2,0. Cmdlets, providers, modules, modules en scripts die zijn geschreven voor Windows Power Shell 2,0 en Windows Power Shell 3,0 worden ongewijzigd uitgevoerd in Windows Power Shell 4,0.

Vanwege een wijziging in het runtime-activerings beleid in Microsoft .NET Framework 4 worden Windows Power shell-host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en gecompileerd met common language runtime (CLR) 2,0 niet uitgevoerd zonder aanpassing in Windows Power Shell 3,0, dat is gecompileerd met CLR 4,0.

De minimale vereiste van de Windows Power Shell 2,0-engine is Microsoft .NET Framework 2.0.50727. Aan deze eis wordt voldaan door Microsoft .NET Framework 3,5 Service Pack 1. Aan deze eis wordt niet voldaan door Microsoft .NET Framework 4 en latere releases van Microsoft .NET Framework.

Zie [Installing the Windows Power shell 2,0 engine](Installing-the-Windows-PowerShell-2.0-Engine.md)(Engelstalig) voor meer informatie over het toevoegen of installeren van de Windows power Shell 2,0-engine en het toevoegen of installeren van de vereiste versies van het Microsoft .NET-Framework. Zie [Start the Windows Power shell 2,0 engine](../Starting-the-Windows-PowerShell-2.0-Engine.md)(Engelstalig) voor meer informatie over het starten van de Windows power Shell 2,0-engine.

## <a name="windows-preinstallation-environment"></a>Windows Preinstallation Environment

Windows Power Shell 2,0, Windows Power Shell 3,0 en Windows Power Shell 4,0 worden uitgevoerd in de Windows Preinstallation Environment (Windows PE). De volgende cmdlets worden echter niet ondersteund.

- Background Intelligent Transfer Service-cmdlets (BITS). Zie [BitsTransfer](/powershell/module/bitstransfer/?view=win10-ps)voor meer informatie.
- [Get-EventLog](/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)
- [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)
- [Opslaan-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)
- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)

De **WinRM** -service is niet aanwezig in Windows PE.

## <a name="see-also"></a>Zie ook

[Windows PowerShell installeren](Installing-Windows-PowerShell.md)

[Windows PowerShell starten](../Starting-Windows-PowerShell.md)

[Windows Management Framework](../wmf/overview.md)
