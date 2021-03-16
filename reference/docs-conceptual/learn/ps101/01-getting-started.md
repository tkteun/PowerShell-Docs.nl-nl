---
title: Aan de slag met PowerShell
description: Waar u kunt zoeken en hoe u Power shell kunt starten voor nieuwe gebruikers.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: cc634eb1732947dca953d7d91baedf8052edf718
ms.sourcegitcommit: 080c8b05a1242348c365fe1684457e873325f11e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483471"
---
# <a name="chapter-1---getting-started-with-powershell"></a>Hoofd stuk 1: aan de slag met Power shell

Ik vind vaak dat presentatoren bij conferenties en gebruikers groeps vergaderingen al Power shell uitvoeren bij het starten van presentaties op instap niveau. Dit boek begint met het beantwoorden van de vragen die ik heb gehoord en die Power shell nog niet eerder hebben gebruikt.

Dit hoofd stuk is specifiek gericht op het zoeken en starten van Power shell en het oplossen van enkele van de eerste knel punten die nieuwe gebruikers met Power shell ervaren. Zorg ervoor dat u de voor beelden die in dit hoofd stuk worden weer gegeven op uw computer met Windows 10 test omgeving volgt.

## <a name="what-do-i-need-to-get-started-with-powershell"></a>Wat heb ik nodig om aan de slag te gaan met Power shell?

Alle moderne versies van Windows-besturings systemen worden geleverd met Power shell geïnstalleerd. Als u een oudere versie dan 5,1 gebruikt, moet u de nieuwste versie installeren.

- Zie [bestaande Windows Power shell bijwerken][] als u een upgrade wilt uitvoeren naar Windows power shell 5,1
- Zie [Power Shell installeren][] voor informatie over het installeren van de meest recente versie van Power shell

## <a name="where-do-i-find-powershell"></a>Waar vind ik Power shell?

De eenvoudigste manier om Power shell te vinden in Windows 10 is **Power shell** in de zoek balk te typen, zoals weer gegeven in afbeelding 1-1.

![Afbeelding 1-1-zoeken naar Power shell in het menu Start](media/figure1-1.png)

U ziet dat er vier verschillende snelkoppelingen voor Power shell worden weer gegeven in afbeelding 1-1. Op de computer die wordt gebruikt voor demonstratie doeleinden in dit boek wordt de 64-bits versie van Windows 10 uitgevoerd, dus is er een 64-bits versie van de Power shell-console en de Power shell ISE (Integrated Scripting Environment), en een 32-bits versie van elk item, zoals aangeduid door het achtervoegsel (x86) op de snelkoppelingen. Als u een 32-bits versie van Windows 10 gebruikt, hebt u slechts twee snelkoppelingen. Deze items hebben niet het achtervoegsel (x86), maar zijn 32-bits versies. Als u een 64-bits besturings systeem hebt, is het raadzaam om de 64-bits versie van Power shell uit te voeren, tenzij u een specifieke reden hebt om de 32-bits versie uit te voeren.

Zie [Starting Windows Power shell][](Engelstalig) voor meer informatie over het starten van Power shell op andere versies van Windows.

## <a name="how-do-i-launch-powershell"></a>Hoe kan ik Power shell starten?

In de Enter prise-bedrijfs omgevingen die worden ondersteund, gebruiken we drie verschillende Active Directory gebruikers accounts. Ik heb deze accounts gespiegeld in de test omgeving die in dit boek wordt gebruikt. Meld u bij de Windows 10-computer aan als een domein gebruiker die geen domein of lokale beheerder is.

Ik heb de Power shell-console gestart door te klikken op de snelkoppeling Windows Power shell, zoals weer gegeven in afbeelding 1-1.

![Afbeelding 1-4-titel balk van het Power shell-venster](media/figure1-4.png)

U ziet dat de titel balk van de Power shell-console ' Windows Power shell ' aangeeft, zoals wordt weer gegeven in afbeelding 1-4. Sommige opdrachten worden prima uitgevoerd, maar Power shell kan niet deel nemen aan gebruikers Access Control (UAC). Dit betekent dat het niet mogelijk is om te vragen om benodigde bevoegdheden voor taken die de goed keuring van een beheerder vereisen.
Het volgende fout bericht wordt gegenereerd:

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

De oplossing voor dit probleem is om Power shell uit te voeren als een domein gebruiker die een lokale beheerder is.
Dit is hoe mijn tweede domein gebruikers account is geconfigureerd. Met het principe van minimale bevoegdheden moet dit account geen domein beheerder zijn of een verhoogde bevoegdheid hebben in het domein.

Sluit Power shell. Start de Power shell-console opnieuw, behalve deze tijd, klik met de rechter muisknop op de snelkoppeling **Windows Power shell** en selecteer als **administrator uitvoeren** , zoals weer gegeven in afbeelding 1-5.

![Afbeelding 1-5-context menu-als administrator uitvoeren](media/figure1-5.png)

Als u bent aangemeld als normale gebruiker bij Windows, wordt u gevraagd om referenties. Ik voer de referenties in voor mijn gebruikers account dat een domein gebruiker en een lokale beheerder is, zoals wordt weer gegeven in afbeelding 1-6.

![Afbeelding 1-6](media/figure1-6.png)

Zodra Power shell als beheerder opnieuw wordt gestart, moet de titel balk ' beheerder: Windows Power shell ' zeggen, zoals wordt weer gegeven in afbeelding 1-7.

![Afbeelding 1-7](media/figure1-7.png)

Nu Power shell wordt uitgevoerd als een lokale beheerder, is UAC niet meer een probleem wanneer een opdracht wordt uitgevoerd op de lokale computer waarvoor normaal gesp roken een prompt vereist. Denk eraan dat elke opdracht die wordt uitgevoerd vanuit dit verhoogde exemplaar van de Power shell-console, ook met verhoogde bevoegdheden kan worden uitgevoerd.

Als u Power shell wilt vereenvoudigen en als beheerder wilt starten, kunt u deze het beste vastmaken aan de taak balk en instellen dat deze automatisch wordt gestart als een beheerder telkens wanneer deze wordt uitgevoerd.

Zoek opnieuw naar Power shell, maar deze keer met de rechter muisknop op en selecteer ' aan taak balk vastmaken ', zoals wordt weer gegeven in afbeelding 1-8.

![Afbeelding 1-8](media/figure1-8.png)

Klik met de rechter muisknop op de Power shell-snelkoppeling die nu is vastgemaakt aan de taak balk en selecteer Eigenschappen, zoals weer gegeven in afbeelding 1-9.

![Afbeelding 1-9-gebruikers account beheer-referenties opgeven](media/figure1-9.png)

Klik op Geavanceerd als aangeduid door #1 in afbeelding 1-10, schakel het selectie vakje als administrator uitvoeren in zoals aangegeven door #2 in afbeelding 1-10, en klik vervolgens twee maal op OK om de wijzigingen te accepteren en af te sluiten van beide dialoog vensters.

![Afbeelding 1-10: titel balk met "beheerder"](media/figure1-10.png)

U hoeft zich nooit zorgen te maken over het vinden van Power shell of het al dan niet uitvoeren van een beheerder.

Het uitvoeren van Power shell is verhoogd als beheerder om te voor komen dat problemen met UAC alleen gevolgen hebben voor opdrachten die worden uitgevoerd op de lokale computer. Dit heeft geen invloed op opdrachten die op externe computers zijn gericht.

## <a name="what-version-of-powershell-am-i-running"></a>Welke versie van Power shell wordt uitgevoerd?

Er zijn een aantal automatische variabelen in Power shell die status informatie opslaan. Een van deze variabelen is `$PSVersionTable` , die een hashtabel bevat die kan worden gebruikt om de relevante informatie over de Power shell-versie weer te geven:

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Nieuwere versies van Windows Power shell worden gedistribueerd als onderdeel van het Windows Management Framework (WMF). Er is een specifieke versie van de .NET Framework vereist, afhankelijk van de versie van WMF. Zie [bestaande Windows Power shell bijwerken][]als u een upgrade wilt uitvoeren naar Windows power shell 5,1.

## <a name="execution-policy"></a>Uitvoerings beleid

In tegens telling tot populaire overtuiging is het uitvoerings beleid in Power shell geen beveiligings grens. Het is ontworpen om te voor komen dat een gebruiker onbewust een script uitvoert. Een bepaalde gebruiker kan het uitvoerings beleid eenvoudig overs laan in Power shell. In tabel 1-2 wordt het standaard uitvoerings beleid voor de huidige Windows-besturings systemen weer gegeven.

| Versie van het Windows-besturings systeem | Standaard uitvoerings beleid |
| -------------------------------- | ------------------------ |
| Server 2019                      | Externe hand tekening            |
| Server 2016                      | Externe hand tekening            |
| Windows 10                       | Beperkt               |

Ongeacht de instelling voor het uitvoerings beleid, kan elke Power shell-opdracht interactief worden uitgevoerd. Het uitvoerings beleid is alleen van invloed op opdrachten die worden uitgevoerd in een script. De `Get-ExecutionPolicy` cmdlet wordt gebruikt om te bepalen wat de huidige uitvoerings beleids instelling is en de `Set-ExecutionPolicy` cmdlet wordt gebruikt om het uitvoerings beleid te wijzigen. Mijn aanbeveling is het **RemoteSigned** -beleid te gebruiken. hiervoor moeten gedownloade scripts worden ondertekend door een vertrouwde uitgever om te worden uitgevoerd.

Controleer het huidige uitvoerings beleid:

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

Power shell-scripts kunnen niet worden uitgevoerd als het uitvoerings beleid is ingesteld op **beperkt**. Dit is de standaard instelling op alle Windows client-besturings systemen. Als u het probleem wilt demonstreren, slaat u de volgende code op als een bestand met de `.ps1` naam `Stop-TimeService.ps1` .

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

Deze opdracht wordt interactief uitgevoerd zonder fouten zolang Power shell wordt uitgevoerd als beheerder. Maar zodra het is opgeslagen als een script bestand en u het script probeert uit te voeren, wordt er een fout gegenereerd:

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

U ziet dat de fout die wordt weer gegeven in de vorige set resultaten precies aangeeft wat het probleem is (het uitvoeren van scripts is uitgeschakeld op dit systeem). Wanneer u een opdracht uitvoert in Power shell waarmee een fout bericht wordt gegenereerd, lees dan het fout bericht in plaats van de opdracht opnieuw uit te voeren en stel in dat het programma met succes wordt uitgevoerd.

Wijzig het Power shell-uitvoerings beleid in extern ondertekend.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

Lees de waarschuwing die wordt weer gegeven wanneer u het uitvoerings beleid wijzigt. U wordt ook aangeraden de [about_Execution_Policies][] Help-onderwerp te bekijken om te controleren of u de beveiligings implicaties van het wijzigen van het uitvoerings beleid begrijpt.

Nu het uitvoerings beleid is ingesteld op **RemoteSigned**, `Stop-TimeService.ps1` wordt het script zonder fouten beschikbaar.

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

Zorg ervoor dat u de Windows Time-service start voordat u doorgaat, anders kunt u onverwachte problemen ondervinden.

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd hoe u Power shell kunt vinden en starten, en hoe u een snelkoppeling maakt waarmee Power shell als beheerder wordt gestart. U hebt ook geleerd over het standaard uitvoerings beleid en hoe u dit kunt wijzigen.

## <a name="review"></a>Beoordelen

1. Hoe kunt u bepalen welke Power shell-versie op een computer wordt uitgevoerd?
1. Waarom is het belang rijk om Power shell met verhoogde bevoegdheid als beheerder te starten?
1. Hoe kunt u het huidige Power shell-uitvoerings beleid bepalen?
1. Wat voor komt het standaard beleid voor Power shell-uitvoering op Windows-client computers?
1. Hoe wijzigt u het Power shell-uitvoerings beleid?

## <a name="recommended-reading"></a>Aanbevolen documentatie

Voor degenen die meer informatie willen over de onderwerpen die in dit hoofd stuk worden behandeld, raden we u aan de volgende Help-onderwerpen voor Power shell te lezen.

- [about_Automatic_Variables][]
- [about_Hash_Tables][]
- [about_Execution_Policies][]

In het volgende hoofd stuk vindt u informatie over de vind baarheid van opdrachten in Power shell. Een van de dingen die worden behandeld, is het bijwerken van Power shell, zodat deze Help-onderwerpen direct vanuit Power shell kunnen worden weer gegeven in plaats van ze op internet te hoeven bekijken.

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[Bestaande Windows Power shell bijwerken]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[PowerShell installeren]: /powershell/scripting/install/installing-powershell
[Windows PowerShell starten]: /powershell/scripting/windows-powershell/starting-windows-powershell
