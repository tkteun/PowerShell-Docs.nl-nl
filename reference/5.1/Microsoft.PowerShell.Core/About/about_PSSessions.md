---
description: Hierin worden Windows Power shell-sessies (PSSessions) beschreven en wordt uitgelegd hoe u een permanente verbinding met een externe computer tot stand brengt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: 0bf3e24ca11108b5ab4739abd9be530243c50f11
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252778"
---
# <a name="about-pssessions"></a>Over PSSessions

## <a name="short-description"></a>Korte beschrijving

Hierin worden Windows Power shell-sessies (PSSessions) beschreven en wordt uitgelegd hoe u een permanente verbinding met een externe computer tot stand brengt.

## <a name="long-description"></a>Lange beschrijving

Als u Windows Power shell-opdrachten wilt uitvoeren op een externe computer, kunt u de para meter **ComputerName** van een cmdlet gebruiken, of u kunt een Windows Power shell-sessie (PSSession) maken en opdrachten uitvoeren in de PSSession.

Wanneer u een PSSession maakt, brengt Windows Power shell een permanente verbinding met de externe computer tot stand. Gebruik een PSSession om een reeks gerelateerde opdrachten uit te voeren op een externe computer. Opdrachten die worden uitgevoerd in dezelfde PSSession kunnen gegevens delen, zoals de waarden van variabelen, aliassen en functies.

U kunt ook een PSSession maken op de lokale computer en daar opdrachten op uitvoeren.
Een lokale PSSession maakt gebruik van de externe infra structuur van Windows Power shell om de PSSession te maken en te onderhouden.

Vanaf Windows Power Shell 3,0 zijn PSSessions onafhankelijk van de sessies waarin ze zijn gemaakt. Actieve PSSessions worden onderhouden op de externe computer (of de computer aan het externe einde of aan de server zijde van de verbinding). Als gevolg hiervan kunt u de verbinding met de PSSession verbreken en op een later tijdstip opnieuw verbinding maken vanaf dezelfde computer of vanaf een andere computer.

In dit onderwerp wordt uitgelegd hoe u PSSessions kunt maken, gebruiken, ophalen en verwijderen. Zie [about_PSSession_Details](about_PSSession_Details.md)voor meer informatie.

Opmerking: PSSessions de externe infra structuur van Windows Power shell gebruiken. Als u PSSessions wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.
Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.

In Windows Vista en latere versies van Windows moet u Windows Power shell starten met de optie als administrator uitvoeren om een PSSession te maken op een lokale computer.

## <a name="what-is-a-session"></a>Wat is een sessie?

Een sessie is een omgeving waarin Windows Power shell wordt uitgevoerd.

Telkens wanneer u Windows Power shell start, wordt er een sessie voor u gemaakt en kunt u opdrachten uitvoeren in de sessie. U kunt ook items toevoegen aan uw sessie, zoals modules en modules, en u kunt items maken, zoals variabelen, functies en aliassen. Deze items bestaan alleen in de sessie en worden verwijderd wanneer de sessie wordt beëindigd.

U kunt ook door gebruikers beheerde sessies (' Windows Power shell-sessies ' of ' PSSessions ') op de lokale computer of op een externe computer maken. Net als bij de standaard sessie kunt u opdrachten uitvoeren in een PSSession en items toevoegen en maken. Maar in tegens telling tot de sessie die automatisch wordt gestart, kunt u de PSSessions die u maakt, beheren. U kunt ze ophalen, maken, configureren en verwijderen, de verbinding verbreken en opnieuw verbinding maken en meerdere opdrachten uitvoeren in dezelfde PSSession. De PSSession blijft beschikbaar totdat u deze verwijdert of als er een time-out optreedt.

Normaal gesp roken maakt u een PSSession om een reeks gerelateerde opdrachten uit te voeren op een externe computer. Wanneer u een PSSession op een externe computer maakt, wordt door Windows Power shell een permanente verbinding met de externe computer tot stand gebracht voor de ondersteuning van de sessie.

Als u de para meter **ComputerName** van de- `Invoke-Command` cmdlet gebruikt `Enter-PSSession` om een externe opdracht uit te voeren of een interactieve sessie te starten, wordt door Windows Power shell een tijdelijke sessie op de externe computer gemaakt en wordt de sessie gesloten zodra de opdracht is voltooid of zodra de interactieve sessie is beëindigd. U kunt deze tijdelijke sessies niet beheren en u kunt deze niet gebruiken voor meer dan één opdracht of één interactieve sessie.

In Windows Power shell is de ' huidige sessie ' de sessie waarin u werkt. De ' huidige sessie ' kan verwijzen naar een wille keurige sessie, met inbegrip van een tijdelijke sessie of een PSSession.

## <a name="why-use-a-pssession"></a>Waarom een PSSession gebruiken?

Gebruik een PSSession wanneer u een permanente verbinding met een externe computer nodig hebt.
Met een PSSession kunt u een reeks opdrachten uitvoeren die gegevens delen, zoals de waarde van variabelen, de inhoud van een functie of de definitie van een alias.

U kunt externe opdrachten uitvoeren zonder een PSSession te maken. Gebruik de para meter **ComputerName** van cmdlets voor externe ondersteuning om één opdracht uit te voeren of een reeks niet-gerelateerde opdrachten op een of meer computers.

Wanneer u de para meter **ComputerName** van `Invoke-Command` of gebruikt `Enter-PSSession` , wordt door Windows Power shell een tijdelijke verbinding met de externe computer tot stand gebracht en wordt vervolgens de verbinding gesloten zodra de opdracht is voltooid. Alle gegevens elementen die u maakt, gaan verloren wanneer de verbinding wordt gesloten.

Andere cmdlets die de para meter **ComputerName** hebben, zoals `Get-Eventlog` en `Get-WmiObject` , gebruiken verschillende externe technologieën om gegevens te verzamelen. Geen permanente verbinding maken, zoals een PSSession.

## <a name="how-to-create-a-pssession"></a>Een PSSession maken

Gebruik de cmdlet om een PSSession te maken `New-PSSession` . Als u de PSSession op een externe computer wilt maken, gebruikt u de para meter **ComputerName** van de `New-PSSession` cmdlet.

Met de volgende opdracht maakt u bijvoorbeeld een nieuwe PSSession op de Server01-computer.

```powershell
New-PSSession -ComputerName Server01
```

Wanneer u de opdracht verzendt, `New-PSSession` wordt de PSSession gemaakt en wordt een object geretourneerd dat staat voor de PSSession. U kunt het object opslaan in een variabele wanneer u de PSSession maakt, maar u kunt ook een `Get-PSSession` opdracht gebruiken om de PSSession op een later tijdstip op te halen.

Met de volgende opdracht maakt u bijvoorbeeld een nieuwe PSSession op de Server01-computer en slaat het resulterende object op in de variabele $ps.

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a>PSSessions maken op meerdere computers

Als u PSSessions op meerdere computers wilt maken, gebruikt u de para meter **ComputerName** van de `New-PSSession` cmdlet. Typ de namen van de externe computers in een lijst met door komma's gescheiden waarden.

Als u bijvoorbeeld PSSessions wilt maken op de Server01-, Server02-en Server03-computers, typt u:

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

`New-PSSession` Hiermee maakt u één PSSession op elke externe computer.

## <a name="how-to-get-pssessions"></a>PSSessions ophalen

Als u de PSSessions wilt ophalen die in uw huidige sessie zijn gemaakt, gebruikt u de `Get-PSSession` cmdlet zonder de para meter **ComputerName** . `Get-PSSession` retourneert hetzelfde type object dat `New-PSSession` retourneert.

Met de volgende opdracht worden alle PSSessions opgehaald die in de huidige sessie zijn gemaakt.

```powershell
Get-PSSession
```

De standaard weergave van de PSSessions toont de ID en een standaard weergave naam. Wanneer u de sessie maakt, kunt u een alternatieve weergave naam toewijzen.

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

U kunt de PSSessions ook opslaan in een variabele. Met de volgende opdracht wordt de PSSessions opgehaald en opgeslagen in de \$ variabele ps123.

```powershell
$ps123 = Get-PSSession
```

Wanneer u de PSSession-cmdlets gebruikt, kunt u naar een PSSession verwijzen met de bijbehorende ID, met de naam of met de ID van het exemplaar (een GUID). Met de volgende opdracht wordt een PSSession op basis van de ID opgehaald en opgeslagen in de \$ variabele PS01.

```powershell
$ps01 = Get-PSSession -Id 1
```

Vanaf Windows Power Shell 3,0 worden PSSessions onderhouden op de externe computer. Gebruik de para meter **ComputerName** van de cmdlet om PSSessions op te halen die u op bepaalde externe computers hebt gemaakt `Get-PSSession` . Met de volgende opdracht wordt de PSSessions opgehaald die u hebt gemaakt op de externe computer met Server01. Dit omvat PSSessions die zijn gemaakt in de huidige sessie en in andere sessies op de lokale computer of op andere computers.

```powershell
Get-PSSession -ComputerName Server01
```

In Windows Power Shell 2,0 worden `Get-PSSession` alleen de PSSessions opgehaald die in de huidige sessie zijn gemaakt. Er worden geen PSSessions opgehaald die zijn gemaakt in andere sessies of op andere computers, zelfs als de sessies zijn verbonden met en opdrachten op de lokale computer worden uitgevoerd.

## <a name="how-to-run-commands-in-a-pssession"></a>Opdrachten uitvoeren in een PSSession

Als u een opdracht wilt uitvoeren in een of meer PSSessions, gebruikt u de `Invoke-Command` cmdlet.
Gebruik de para meter Session om de PSSessions en de para meter **script Block** op te geven om de opdracht op te geven.

Als u bijvoorbeeld een `Get-ChildItem` opdracht ' dir ' wilt uitvoeren in elk van de drie PSSessions die zijn opgeslagen in de variabele $ps 123, typt u:

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a>PSSessions verwijderen

Wanneer u klaar bent met de PSSession, gebruikt u de `Remove-PSSession` cmdlet om de PSSession te verwijderen en om de resources vrij te geven die het gebruikt.

```powershell
Remove-PSSession -Session $ps
```

of

```powershell
Remove-PSSession -Id 1
```

Als u een PSSession van een externe computer wilt verwijderen, gebruikt u de para meter **ComputerName** van de `Remove-PSSession` cmdlet.

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

Als u de PSSession niet verwijdert, blijft de PSSession beschikbaar voor gebruik totdat er een time-out optreedt.

U kunt ook de para meter **IdleTimeout** van de `New-PSSessionOption` cmdlet gebruiken om een verval tijd in te stellen voor een niet-actieve PSSession. Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie.

## <a name="the-pssession-cmdlets"></a>De PSSession-cmdlets

Voor een lijst met PSSession-cmdlets typt u:

```powershell
Get-Help *-PSSession
```

- Connect-PSSession: verbindt een PSSession met de huidige sessie
- Disconnect-PSSession: de verbinding van een PSSession met de huidige sessie wordt verbroken
- Enter-PSSession: start een interactieve sessie
- Afsluiten-PSSession: Hiermee wordt een interactieve sessie beëindigd
- Get-PSSession: Hiermee wordt de PSSessions in de huidige sessie opgehaald
- New-PSSession: maakt een nieuwe PSSession op een lokale of externe computer
- Receive-PSSession: Hiermee worden de resultaten opgehaald van opdrachten die zijn uitgevoerd in een verbroken sessie
- Remove-PSSession: Hiermee wordt de PSSessions in de huidige sessie verwijderd

## <a name="for-more-information"></a>Meer informatie

Zie [about_PSSession_Details](about_PSSession_Details.md)voor meer informatie over PSSessions.

## <a name="see-also"></a>Zie ook

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Verbinding verbreken-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Afsluiten-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)
