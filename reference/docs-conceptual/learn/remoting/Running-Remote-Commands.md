---
ms.date: 08/14/2018
keywords: Power shell, cmdlet
title: Externe opdrachten uitvoeren
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030309"
---
# <a name="running-remote-commands"></a>Externe opdrachten uitvoeren

U kunt opdrachten uitvoeren op een of honderden computers met één Power shell-opdracht. Windows Power shell ondersteunt extern computer gebruik met behulp van verschillende technologieën, waaronder WMI, RPC en WS-Management.

Power shell core ondersteunt WMI, WS-beheer en externe SSH-communicatie. RPC wordt niet meer ondersteund.

Raadpleeg de volgende artikelen voor meer informatie over externe communicatie in Power shell core:

- [Externe SSH-communicatie in Power shell core][ssh-remoting]
- [Externe WSMan-communicatie in Power shell core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Externe toegang tot Windows Power shell zonder configuratie

Veel Windows Power shell-cmdlets hebben de para meter ComputerName waarmee u gegevens kunt verzamelen en instellingen op een of meer externe computers wijzigt. Deze cmdlets gebruiken verschillende communicatie protocollen en werken zonder speciale configuratie op alle Windows-besturings systemen.

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

Doorgaans hebben cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie, de para meter ComputerName en hebben de sessie parameter niet. Als u deze cmdlets wilt vinden in uw sessie, typt u:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Externe toegang voor Windows Power shell

Met het protocol WS-Management kunt u met Windows Power shell voor externe toegang een Windows Power shell-opdracht uitvoeren op een of meer externe computers. U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.

Als u externe toegang tot Windows Power shell wilt gebruiken, moet u de computer configureren voor extern beheer.
Zie [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)voor meer informatie, waaronder instructies.

Wanneer u Windows Power shell Remoting hebt geconfigureerd, zijn veel externe strategieën voor u beschikbaar.
In dit artikel worden slechts enkele hiervan vermeld. Zie [over extern](/powershell/module/microsoft.powershell.core/about/about_remote)voor meer informatie.

### <a name="start-an-interactive-session"></a>Een interactieve sessie starten

Als u een interactieve sessie met één externe computer wilt starten, gebruikt u de cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .
Als u bijvoorbeeld een interactieve sessie met de externe computer Server01 wilt starten, typt u:

```powershell
Enter-PSSession Server01
```

De opdracht prompt wordt gewijzigd om de naam van de externe computer weer te geven. Alle opdrachten die u typt bij de prompt die worden uitgevoerd op de externe computer en de resultaten worden weer gegeven op de lokale computer.

Als u de interactieve sessie wilt beëindigen, typt u:

```powershell
Exit-PSSession
```

Zie voor meer informatie over de cmdlets Enter-PSSession en Exit-PSSession:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Afsluiten-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Een externe opdracht uitvoeren

Als u een opdracht op een of meer computers wilt uitvoeren, gebruikt u de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) . Als u bijvoorbeeld de opdracht [Get-uiCulture](/powershell/module/microsoft.powershell.utility/get-uiculture) wilt uitvoeren op de externe computers Server01 en Server02, typt u:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

De uitvoer wordt teruggestuurd naar uw computer.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Een script uitvoeren

Als u een script wilt uitvoeren op een of meer externe computers, gebruikt u de para `Invoke-Command` meter filepath van de cmdlet. Het script moet op of toegankelijk zijn voor uw lokale computer. De resultaten worden teruggestuurd naar de lokale computer.

Met de volgende opdracht wordt bijvoorbeeld het script DiskCollect. ps1 uitgevoerd op de externe computers, Server01 en Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Een permanente verbinding tot stand brengen

Gebruik de `New-PSSession` cmdlet om een permanente sessie te maken op een externe computer. In het volgende voor beeld worden externe sessies gemaakt op Server01 en Server02. De sessie objecten worden opgeslagen in de `$s` variabele.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nu u de sessies tot stand hebt gebracht, kunt u elke opdracht in ze uitvoeren. En omdat de sessies permanent zijn, kunt u gegevens verzamelen van de ene opdracht en deze gebruiken in een andere opdracht.

Met de volgende opdracht wordt bijvoorbeeld een Get-HotFix-opdracht uitgevoerd in de sessies in de variabele $s en worden de resultaten opgeslagen in de $h-variabele. De variabele $h wordt gemaakt in elk van de sessies in $s, maar deze komt niet voor in de lokale sessie.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nu kunt u de gegevens in de `$h` variabele gebruiken met andere opdrachten in dezelfde sessie. De resultaten worden weer gegeven op de lokale computer. Bijvoorbeeld:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Geavanceerde externe communicatie

Windows Power shell Remote Management begint hier gewoon. Door gebruik te maken van de cmdlets die zijn geïnstalleerd met Windows Power shell, kunt u externe sessies instellen en configureren op basis van de lokale en externe eind punten, aangepaste en beperkte sessies opstellen, gebruikers opdrachten laten importeren uit een externe sessie die daad werkelijk impliciet is uitgevoerd op de externe sessie, de beveiliging van een externe sessie configureren, en nog veel meer.

Windows Power shell bevat een WSMan-provider. De provider maakt een `WSMAN:` station waarmee u kunt navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.

Zie voor meer informatie over de WSMan-provider [wsman-provider](https://technet.microsoft.com/library/dd819476.aspx) en [over WS-Management-cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), of typ `Get-Help wsman`in de Windows Power shell-console.

Zie voor meer informatie:

- [Over externe Veelgestelde vragen](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Zie [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)voor hulp bij externe fouten.

## <a name="see-also"></a>Zie ook

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan Provider](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
