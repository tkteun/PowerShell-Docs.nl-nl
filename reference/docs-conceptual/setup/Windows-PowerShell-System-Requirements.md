---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell-systeemvereisten
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 74c65a97a30227997c48a23c42b0431189f9ed76
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/25/2018
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell-systeemvereisten
Dit onderwerp worden de systeemvereisten voor Windows PowerShell 3.0, Windows PowerShell 4.0 en Windows PowerShell 5.0 en voor speciale functies, zoals Windows PowerShell Integrated Scripting Environment (ISE), CIM-opdrachten en werkstromen.

Windows® 8.1 en Windows Server® 2012 R2 moet u alle vereiste programma's bevatten. Dit onderwerp is bedoeld voor gebruikers van eerdere versies van Windows.

## <a name="operating-system-requirements"></a>Besturingssysteemvereisten
Windows PowerShell 5.0 wordt uitgevoerd op de volgende versies van Windows.

- Windows Server 2016 standaard geïnstalleerd

- WindowsServer 2012 R2 installeren [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) om uit te voeren van Windows PowerShell 5.0

- WindowsServer 2012 installeren [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) om uit te voeren van Windows PowerShell 5.0

- Windows Server 2008 R2 met Service Pack 1 installeert [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) om uit te voeren van Windows PowerShell 5.0

- Windows 8.1

- Windows 7 met Service Pack 1 installeert [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) om uit te voeren van Windows PowerShell 5.0

Windows PowerShell 4.0 wordt uitgevoerd op de volgende versies van Windows.

- Windows 8.1-, standaard geïnstalleerd

- Windows Server 2012 R2 is standaard geïnstalleerd

- Windows® 7 met Service Pack 1 installeert [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) om uit te voeren van Windows PowerShell 4.0

- Windows Server® 2008 R2 met Service Pack 1 installeert [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) om uit te voeren van Windows PowerShell 4.0

Windows PowerShell 3.0 wordt uitgevoerd op de volgende versies van Windows.

- Windows 8, standaard geïnstalleerd

- Windows Server 2012, standaard geïnstalleerd

- Windows® 7 met Service Pack 1 installeert [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) om uit te voeren van Windows PowerShell 3.0

- Windows Server® 2008 R2 met Service Pack 1 installeert [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) om uit te voeren van Windows PowerShell 3.0

- Installeren van Windows Server 2008 met Service Pack 2, [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) om uit te voeren van Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework-vereisten
Windows PowerShell 5.0 is de volledige installatie van Microsoft .NET Framework 4.5 vereist. Windows 8.1 en Windows Server 2012 R2 zijn Microsoft .NET Framework 4.5 standaard.

Windows PowerShell 4.0 is vereist voor de volledige installatie van Microsoft .NET Framework 4.5. Windows 8.1 en Windows Server 2012 R2 zijn Microsoft .NET Framework 4.5 standaard.

Windows PowerShell 3.0 is de volledige installatie van Microsoft .NET Framework 4 vereist. Windows 8 en Windows Server 2012 zijn Microsoft .NET Framework 4.5 standaard die voldoet aan deze vereiste.

Zie het installeren van Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919) op het Microsoft Download Center.

Zie het installeren van de volledige installatie van Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) [Microsoft .NET Framework 4 (webinstallatie)](http://go.microsoft.com/fwlink/?LinkID=212931) op het Microsoft Download Center.

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 vereist Windows Management Framework 4.0 moet worden geïnstalleerd op Windows Server 2008 R2 SP1 en Windows 7 SP1.

## <a name="ws-management-30"></a>3.0 WS-Management
Windows PowerShell 3.0 en Windows PowerShell 4.0 vereist WS-Management-3.0, die ondersteuning biedt voor de WinRM-service en de WSMan-protocol. Dit programma is opgenomen in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 en Windows Management Framework 3.0.

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 en Windows PowerShell 4.0 vereist Windows Management Instrumentation 3.0 (WMI). Dit programma is opgenomen in Windows 8.1, Windows Server 2012 R2, Windows 8, Windows Server 2012, Windows Management Framework 4.0 en Windows Management Framework 3.0. Als dit programma is niet geïnstalleerd op de computer, functies waarvoor WMI, zoals CIM-opdrachten, niet uitgevoerd.

## <a name="common-language-runtime-40"></a>Common Language Runtime 4.0
Windows PowerShell 3.0, Windows PowerShell 4.0 en Windows PowerShell 5.0 worden gecompileerd tegen Common Language Runtime (CLR) 4.0.

## <a name="graphical-user-interface-requirements"></a>Grafische gebruikersinterface
Windows PowerShell is een console-toepassing waarvoor een grafische gebruikersinterface niet. Als zodanig is het ook geschikt voor computers waarop geen schermen of monitors of een gebruikersinterface, zoals de Server Core-installatieopties van Windows Server 2012 R2 of Windows Server 2012.

Echter bepaalde items, zoals de volgende, vereisen een grafische gebruikersinterface. Zie voor meer informatie het help-onderwerp voor elk item.

- Windows PowerShell ISE (Integrated Scripting Environment)

- Cmdlets

    1.  [Out-GridView](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Opdracht weergeven](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Weergeven ControlPanelItem](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Weergeven EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- Parameters

    1.  **ShowWindow** parameter van de [Get-Help](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.

    2.  **ShowSecurityDescriptorUI** parameter van de [Register-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) en [Set-PSSessionConfiguration](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlets.

## <a name="windows-powershell-engine-requirements"></a>Vereisten voor Windows PowerShell-Engine
Windows PowerShell 4.0 is ontworpen voor achterwaartse compatibiliteit met Windows PowerShell 3.0 en Windows PowerShell 2.0. Cmdlets, providers, -modules, modules en scripts die zijn geschreven voor Windows PowerShell 2.0 en Windows PowerShell 3.0 ongewijzigd in Windows PowerShell 4.0 worden uitgevoerd.

Echter, vanwege een wijziging in de runtime activering-beleid in Microsoft .NET Framework 4, Windows PowerShell-host-programma's die zijn geschreven voor Windows PowerShell 2.0 en gecompileerd met Common Language Runtime (CLR) 2.0 kunnen niet worden uitgevoerd zonder aanpassingen in Windows PowerShell 3.0, die is gecompileerd met CLR-4.0.

De engine voor Windows PowerShell 2.0 vereist Microsoft .NET Framework 2.0.50727 minimaal. Deze vereiste wordt voldaan door de Microsoft .NET Framework 3.5 servicepack 1. Deze vereiste wordt niet voldaan door de Microsoft .NET Framework 4 en latere versies van Microsoft .NET Framework.

Zie voor meer informatie over het toevoegen of installeren van de Windows PowerShell 2.0-engine en toe te voegen of installeren van de vereiste versie van Microsoft .NET Framework [installeren van de Windows PowerShell 2.0-Engine](Installing-the-Windows-PowerShell-2.0-Engine.md). Zie voor meer informatie over het starten van de Windows PowerShell 2.0-engine [starten van de Windows PowerShell 2.0 motor](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="windows-preinstallation-environment"></a>Windows Preinstallation Environment
Windows PowerShell 2.0, Windows PowerShell 3.0 en Windows PowerShell 4.0 worden uitgevoerd in de Windows Preinstallation Environment (Windows PE). De volgende cmdlets worden echter niet ondersteund.

- [Cmdlets van Background Intelligent Transfer Service (BITS)](http://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Help opslaan](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Help bijwerken](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Update-Help)

Ook de **WinRM** service is niet aanwezig is op Windows PE.

## <a name="see-also"></a>Zie ook
- [Aan de slag met Windows PowerShell](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [Windows PowerShell installeren](Installing-Windows-PowerShell.md)
- [Windows PowerShell starten](Starting-Windows-PowerShell.md)