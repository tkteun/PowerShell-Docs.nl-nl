---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Externe opdrachten uitvoeren
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133833"
---
# <a name="running-remote-commands"></a>Externe opdrachten uitvoeren

U kunt opdrachten uitvoeren op een of honderden computers met slechts één PowerShell-opdracht. Windows PowerShell biedt ondersteuning voor externe computing met behulp van verschillende technologieën, zoals WMI, RPC en WS-Management.

PowerShell Core biedt ondersteuning voor WMI, WS-Management en SSH voor externe toegang. RPC wordt niet meer ondersteund.

Zie voor meer informatie over externe communicatie in PowerShell Core, de volgende artikelen:

- [SSH in PowerShell Core voor externe toegang][ssh-remoting]
- [Externe communicatie van WSMan in PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Windows PowerShell voor externe toegang zonder configuratie

Veel Windows PowerShell-cmdlets hebben de parameter ComputerName waarmee u voor het verzamelen van gegevens en instellingen op een of meer externe computers wijzigen. Deze cmdlets gebruikt verschillende communicatieprotocollen en werkt op alle Windows-besturingssystemen zonder speciale configuratie.

Deze cmdlets zijn onder andere:

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Normaal gesproken cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie hebt de parameter ComputerName en hoeft de sessie-parameter. U vindt deze cmdlets in uw sessie, typt u:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell voor externe toegang

Windows PowerShell voor externe toegang kunt met behulp van het protocol WS-Management, u een Windows PowerShell-opdracht uitvoeren op een of meer externe computers. U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.

Voor het gebruik van Windows PowerShell voor externe toegang, moet de externe computer worden geconfigureerd voor extern beheer.
Zie voor meer informatie, inclusief instructies [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Nadat u Windows PowerShell voor externe toegang hebt geconfigureerd, worden veel externe communicatie van strategieën voor u beschikbaar zijn.
Dit artikel worden slechts enkele van deze. Zie voor meer informatie, [over externe](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Start een interactieve sessie

Gebruiken om een interactieve sessie starten met een externe computer, de [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.
Bijvoorbeeld, om een interactieve sessie starten met de externe computer Server01, typt u:

```powershell
Enter-PSSession Server01
```

De wijzigingen van de opdrachtprompt om weer te geven van de naam van de externe computer. Alle opdrachten die u typt u bij de opdrachtprompt worden uitgevoerd op de externe computer en de resultaten worden weergegeven op de lokale computer.

Als u de interactieve sessie beëindigen, typt u:

```powershell
Exit-PSSession
```

Zie voor meer informatie over de Enter-PSSession en afsluiten PSSession-cmdlets:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Afsluiten PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Een externe opdracht uitvoeren

Als u wilt een opdracht uitvoeren op een of meer computers, gebruiken de [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet. Bijvoorbeeld, om uit te voeren een [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) opdracht op de Server01 en Server02 externe computers, type:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

De uitvoer wordt geretourneerd naar de computer.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Een Script uitvoeren

Als u wilt een script uitvoeren op een of meer externe computers, gebruikt u de parameter van het bestandspad van de `Invoke-Command` cmdlet. Het script moet op of toegankelijk is voor uw lokale computer. De resultaten worden geretourneerd naar de lokale computer.

De volgende opdracht wordt bijvoorbeeld het DiskCollect.ps1-script uitgevoerd op de externe computers, Server01 en Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Een permanente verbinding tot stand brengen

Gebruik de `New-PSSession` cmdlet voor het maken van een permanente sessie op een externe computer. Het volgende voorbeeld wordt een externe sessies op Server01 en Server02. De sessieobjecten worden opgeslagen in de `$s` variabele.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nu dat de sessies tot stand worden gebracht, kunt u een opdracht uitvoeren in deze. En omdat de sessies persistent zijn, kunt u gegevens verzamelen in één opdracht en deze gebruiken in een andere opdracht.

Bijvoorbeeld een Get-HotFix-opdracht in de volgende opdracht wordt uitgevoerd in de sessies in de variabele $s en de resultaten worden opgeslagen in de variabele $h. De variabele $h in elk van de sessies in $s is gemaakt, maar deze nog niet bestaat in de lokale sessie.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nu kunt u de gegevens in de `$h` variabele met andere opdrachten in dezelfde sessie. De resultaten worden weergegeven op de lokale computer. Bijvoorbeeld:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Geavanceerde voor externe toegang

Windows PowerShell extern beheer alleen hier begint. Met behulp van de cmdlets die met Windows PowerShell is geïnstalleerd, kunt u tot stand brengen en externe sessies configureren bij de uiteinden lokale en externe maken van aangepaste en beperkte sessies, kunnen gebruikers opdrachten voor het importeren van een externe sessie die daadwerkelijk wordt uitgevoerd impliciet op de externe sessie, configureert u de beveiliging van een externe sessie en nog veel meer.

Windows PowerShell omvat een WSMan-provider. Hiermee maakt u de provider een `WSMAN:` station waarmee u navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.

Zie voor meer informatie over de WSMan-provider [WSMan-Provider](https://technet.microsoft.com/library/dd819476.aspx) en [over WS-Management-Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), of typ in de Windows PowerShell-console `Get-Help wsman`.

Zie voor meer informatie

- [Over veelgestelde vragen over externe](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Zie voor hulp bij externe communicatie van fouten, [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Zie ook

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan Provider](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md