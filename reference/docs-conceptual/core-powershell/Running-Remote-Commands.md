---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Externe opdrachten uitvoeren
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 43f07abd642e7de235647fa151537c46ebe86cae
ms.sourcegitcommit: 6aed37d7f0c9652ae09bb8c11928da7e4783ed7f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2018
---
# <a name="running-remote-commands"></a>Externe opdrachten uitvoeren

U kunt de opdrachten uitvoeren op een of honderden computers met een enkele Windows PowerShell-opdracht. Windows PowerShell biedt ondersteuning voor externe verwerking met behulp van verschillende technologieën, zoals WMI, RPC en WS-Management.

## <a name="remoting-in-powershell-core"></a>Externe toegang in PowerShell-kern

PowerShell-Core, de nieuwere versie van PowerShell op Windows-, Mac OS- en Linux, WMI, ondersteunt WS-Management en SSH voor externe toegang.
(RPC wordt niet langer ondersteund.)

Zie voor meer informatie op om in te stellen:

* [SSH Remoting in PowerShell Core] [de ssh-remoting]
* [WinRM Remoting in PowerShell Core] [winrm remoting]

## <a name="remoting-without-configuration"></a>Externe toegang zonder configuratie
Veel Windows PowerShell-cmdlets hebben de parameter ComputerName waarmee u kunt het verzamelen van gegevens en instellingen op een of meer externe computers wijzigen. Ze verschillende technologieën voor communicatie en veel werk op alle Windows-besturingssystemen die ondersteuning biedt zonder speciale configuratie voor Windows PowerShell gebruiken.

Deze cmdlets zijn onder andere:

* [Computer opnieuw opstarten](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Verbinding testen](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Schakel EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-gebeurtenislogboek](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Set-Service](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Normaal gesproken cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie hebt de parameter ComputerName en hoeft niet de sessie-parameter. Om deze cmdlets in uw sessie, typt u:

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell voor externe toegang
Windows PowerShell op afstand, die gebruikmaakt van het protocol WS-Management, kunt u een Windows PowerShell-opdracht uitvoeren op een of meer externe computers. Hiermee kunt u permanente verbindingen tot stand brengen, 1:1 interactieve sessies starten en scripts uitvoeren op meerdere computers.

Voor het gebruik van Windows PowerShell op afstand, moet de externe computer worden geconfigureerd voor extern beheer. Zie voor meer informatie, waaronder instructies [over vereisten voor externe](https://technet.microsoft.com/en-us/library/dd315349.aspx).

Nadat u Windows PowerShell voor externe toegang hebt geconfigureerd, worden veel remoting strategieën voor u beschikbaar zijn. De rest van dit document vindt u enkele van deze. Zie voor meer informatie [over externe](https://technet.microsoft.com/en-us/library/dd347744.aspx) en [over veelgestelde vragen over extern](https://technet.microsoft.com/en-us/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Een interactieve sessie starten
Gebruikt u een interactieve sessie starten met een externe computer, de [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.
Bijvoorbeeld, u een interactieve sessie starten met de externe computer Server01, typt u:

```
Enter-PSSession Server01
```

De wijzigingen in de opdrachtprompt om weer te geven van de naam van de computer waarop u bent verbonden. Daarna alle opdrachten die u typt u bij de opdrachtprompt op de externe computer uitvoeren en de resultaten worden weergegeven op de lokale computer.

Als u wilt de interactieve sessie beëindigen, typt u:

```
Exit-PSSession
```

Zie voor meer informatie over de cmdlets Enter-PSSession en afsluiten-PSSession [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) en [afsluiten-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Een externe opdracht wordt uitgevoerd
Wilt willekeurige opdracht uitvoeren op een of meer externe computers, gebruikt de [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.
Bijvoorbeeld, om uit te voeren een [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) opdracht op de Server01 en Server02 externe computers, type:

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

De uitvoer wordt geretourneerd naar de computer.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
Zie voor meer informatie over de cmdlet Invoke-Command [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Een Script uitvoeren
U kunt een script uitvoeren op een of meer externe computers door de parameter bestandspad van de cmdlet Invoke-Command te gebruiken. Het script moet op of toegankelijk is voor uw lokale computer. De resultaten worden geretourneerd naar de lokale computer.

De volgende opdracht wordt het script DiskCollect.ps1 uitgevoerd op de externe computers Server01 en Server02.

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Zie voor meer informatie over de cmdlet Invoke-Command [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Een permanente verbinding tot stand brengen
Voor het uitvoeren van een reeks van verwante opdrachten die gegevens delen, sessie op de externe computer maken en gebruik vervolgens de cmdlet Invoke-Command opdrachten kunt uitvoeren in de sessie die u maakt. Gebruik de cmdlet New-PSSession voor het maken van een externe sessie.

De volgende opdracht maakt bijvoorbeeld een externe sessie op de computer Server01 en een andere externe sessie op de computer Server02. De sessieobjecten worden opgeslagen in de variabele $s.

```
$s = New-PSSession -ComputerName Server01, Server02
```

Nu dat de sessies tot stand gebracht worden, kunt u elke opdracht uitvoeren in ze. En omdat de sessies persistent zijn, kunt u worden verzameld in één opdracht en deze in de volgende opdracht gebruiken.

Bijvoorbeeld de volgende opdracht wordt een opdracht Get-HotFix uitgevoerd in de sessies in de variabele $s en de resultaten worden opgeslagen in de variabele $h. De variabele $h in elk van de sessies in $s is gemaakt, maar deze niet bestaat in de lokale sessie.

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nu kunt u de gegevens in de variabele $h in de volgende opdrachten, zoals de volgende. De resultaten worden weergegeven op de lokale computer.

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Geavanceerde voor externe toegang
Windows PowerShell extern beheer begint alleen hier. Met behulp van de geïnstalleerd met Windows PowerShell-cmdlets, kunt u tot stand brengen en externe sessies configureren van de lokale en externe is afgelopen, maken van aangepaste en beperkte sessies, kunnen gebruikers opdrachten voor het importeren vanuit een externe sessie die daadwerkelijk worden uitgevoerd impliciet op de externe sessie, configureert u de beveiliging van een externe sessie en nog veel meer.

Windows PowerShell omvat te vergemakkelijken externe configuratie, een WSMan-provider. De WSMAN: station dat de provider maakt, kunt u navigeren door een hiërarchie van configuratie-instellingen op de lokale computer en externe computers.
Zie voor meer informatie over de WSMan-provider [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) en [over WS-Management-Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), of typ 'Get-Help wsman' in de Windows PowerShell-console.

Zie voor meer informatie
- [Over externe Veelgestelde vragen](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Zie voor meer informatie over fouten voor externe toegang, [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## <a name="see-also"></a>Zie ook
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [Nieuwe-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan-Provider](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-resmoting]: SSH-Remoting-in-PowerShell-Core.md
