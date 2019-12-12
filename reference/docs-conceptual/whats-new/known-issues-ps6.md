---
ms.date: 05/17/2018
keywords: Power shell, kern
title: Bekende problemen met Power shell 6,0
ms.openlocfilehash: e84dd2f7deefcc64aea09585e7ce24dc1e8515fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71692226"
---
# <a name="known-issues-for-powershell-60"></a>Bekende problemen met Power shell 6,0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Bekende problemen met Power shell op niet-Windows-platforms

Alfa releases van Power shell op Linux en macOS zijn voornamelijk functioneel, maar hebben wel enkele belang rijke beperkingen en problemen met de bruikbaarheid. Bèta releases van Power shell op Linux en macOS zijn meer functioneel en stabieler dan Alpha-Releases, maar kunnen nog steeds een aantal functies hebben en kunnen fouten bevatten. In sommige gevallen zijn deze problemen gewoon fouten die nog niet zijn opgelost. In andere gevallen (net als bij de standaard aliassen voor LS, CP, etc.) kijken we naar feedback van de community over de keuzes die we maken.

Opmerking: als gevolg van de overeenkomsten van een groot aantal onderliggende subsystemen biedt Power shell in Linux en macOS meestal hetzelfde niveau van de verval datum in zowel de functies als de bugs. Behalve zoals hieronder vermeld, zijn de problemen in deze sectie van toepassing op beide besturings systemen.

### <a name="case-sensitivity-in-powershell"></a>Hoofdletter gevoeligheid in Power shell

In het verleden is Power shell uniform niet hoofdletter gevoelig, met enkele uitzonde ringen. Op UNIX-achtige besturings systemen is het bestands systeem voornamelijk hoofdletter gevoelig en wordt Power shell gevolgd door de standaard van het bestands systeem. Dit wordt weer gegeven op een aantal manieren, duidelijk en niet duidelijk.

#### <a name="directly"></a>rechtstreeks

- Wanneer u een bestand opgeeft in Power shell, moet u de juiste Case gebruiken.

#### <a name="indirectly"></a>Indirect

- Als een script probeert een module te laden en de module naam niet correct is, zal de module laden mislukken. Dit kan een probleem met bestaande scripts veroorzaken als de naam waarmee de module wordt verwezen, niet overeenkomt met de werkelijke bestands naam.
- Het volt ooien van het tabblad wordt niet automatisch voltooid als het probleem met de bestands naam onjuist is. Het uit te voeren fragment moet correct zijn. (De voltooiing is hoofdletter gevoelig voor de type naam en de voltooiing van het type lid.)

### <a name="ps1-file-extensions"></a>. PS1-bestands extensies

Power shell-scripts moeten eindigen op `.ps1` voor de interpreter om te begrijpen hoe ze in het huidige proces kunnen worden geladen en uitgevoerd. Het uitvoeren van scripts in het huidige proces is het verwachte gebruikelijke gedrag voor Power shell. Het `#!` Magic-nummer kan worden toegevoegd aan een script dat geen `.ps1` extensie heeft, maar dit zorgt ervoor dat het script wordt uitgevoerd in een nieuw Power shell-exemplaar zodat het script niet goed werkt wanneer objecten worden gewijzigd. (Opmerking: dit kan het wenselijk gedrag zijn bij het uitvoeren van een Power shell-script van `bash` of een andere shell.)

### <a name="missing-command-aliases"></a>Ontbrekende opdracht aliassen

In Linux/macOS zijn de ' gebruiks vriendelijke aliassen ' voor de basis opdrachten `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` verwijderd. In Windows biedt Power shell een reeks aliassen die worden toegewezen aan linux-opdracht namen voor het gemak van de gebruiker. Deze aliassen zijn verwijderd uit de standaard Power shell op Linux/macOS-distributies, waardoor het systeem eigen uitvoer bare bestand kan worden uitgevoerd zonder een pad op te geven.

Er zijn voor-en nadelen. Als u de aliassen verwijdert, wordt de systeem eigen opdracht-ervaring voor de Power shell-gebruiker beschikbaar, maar vermindert de functionaliteit in de shell omdat de systeem eigen opdrachten teken reeksen retour neren in plaats van objecten.

> [!NOTE]
> Dit is een gebied waar het Power shell-team op zoek is naar feedback.
> Wat is de voor keur oplossing? Moeten we het blijven of de alias voor het gemak toevoegen? Zie [probleem #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Ondersteuning voor joker tekens ontbreekt (globbing)

Op dit moment voert Power shell alleen Joker uitbrei ding (globbing) uit voor ingebouwde cmdlets in Windows, en voor externe opdrachten of binaire bestanden, evenals cmdlets op Linux. Dit betekent dat een opdracht als `ls
*.txt` mislukt, omdat het sterretje niet kan worden uitgevouwen om te voldoen aan de bestands namen. U kunt dit probleem omzeilen door `ls (gci *.txt | % name)` of, meer te doen `gci *.txt` met behulp van de ingebouwde Power shell-equivalent voor `ls`.

Zie [#954](https://github.com/PowerShell/PowerShell/issues/954) om ons feedback te geven over het verbeteren van de globbing-ervaring op Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework vs .NET core Framework

Power shell op Linux/macOS gebruikt .NET core, een subset van de volledige .NET Framework in micro soft Windows. Dit is belang rijk omdat Power shell direct toegang biedt tot de onderliggende Framework typen, methoden, enzovoort. Als gevolg hiervan kunnen scripts die worden uitgevoerd op Windows niet worden uitgevoerd op niet-Windows-platforms vanwege de verschillen in de frameworks. Zie [dotnetfoundation.org](https://dotnetfoundation.org/)voor meer informatie over .net core Framework.

Met de komst van [.NET Standard 2.0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)brengt .net Core 2,0 een groot aantal van de traditionele typen en methoden die aanwezig zijn in de volledige .NET Framework. Dit betekent dat Power shell core veel traditionele Windows Power shell-modules zonder wijzigingen kan laden. U kunt [hier](https://github.com/PowerShell/PowerShell/projects/4)het gerelateerde .net Standard 2,0-werk volgen.

### <a name="redirection-issues"></a>Problemen met omleiding

Invoer omleiding wordt niet ondersteund in Power shell op een platform.
[Probleem #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Gebruik `Get-Content` om de inhoud van een bestand naar de pijp lijn te schrijven.

Omgeleide uitvoer bevat de Unicode-byte order mark (BOM) wanneer de standaard UTF-8-code ring wordt gebruikt. De stuk lijst zorgt voor problemen bij het werken met hulpprogram ma's die deze niet verwachten of wanneer ze worden toegevoegd aan een bestand. Gebruik `-Encoding Ascii` voor het schrijven van ASCII-tekst (die geen Unicode is, geen stuk lijst).

> [!Note]
> Zie [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) om ons feedback te geven over het verbeteren van de coderings ervaring voor Power shell Core op alle platforms. We werken met de ondersteuning van UTF-8 zonder een stuk lijst en kunnen de standaard waarden voor de code ring wijzigen voor verschillende cmdlets op verschillende platforms.

### <a name="job-control"></a>Taak beheer

Er is geen taak beheer ondersteuning in Power shell op Linux/macOS.
De opdrachten `fg` en `bg` zijn niet beschikbaar.

Voor deze tijd kunt u [Power shell-taken](/powershell/module/microsoft.powershell.core/about/about_jobs) gebruiken die op alle platforms werken.

### <a name="remoting-support"></a>Ondersteuning voor externe communicatie

Momenteel ondersteunt Power shell core Power shell Remoting (PSRP) via WSMan met basis verificatie voor macOS en Linux, en met NTLM-verificatie op Linux. (Verificatie op basis van Kerberos wordt niet ondersteund.)

Het werk voor externe toegang op basis van WSMan wordt uitgevoerd in de [PSL-Omi-provider](https://github.com/PowerShell/psl-omi-provider) opslag plaats.

Power shell core biedt ook ondersteuning voor externe communicatie van Power shell (PSRP) via SSH op alle platformen (Windows, macOS en Linux). Hoewel dit momenteel niet wordt ondersteund in de productie, kunt u [hier](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md)meer informatie vinden over het instellen hiervan.

### <a name="just-enough-administration-jea-support"></a>Just-voldoende beheer (JEA)-ondersteuning

De mogelijkheid om JEA-eind punten (congebonden beheer) te maken, is momenteel niet beschikbaar in Power shell op Linux/macOS. Deze functie is momenteel niet beschikbaar in het bereik van 6,0 en iets wat we als een aanzienlijk ontwerp moeten 6,0 beschouwen.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`en Power shell

Omdat Power shell de meeste opdrachten in het geheugen (zoals python of Ruby) uitvoert, kunt u sudo niet rechtstreeks gebruiken met Power shell-ingebouwde modules. (u kunt natuurlijk `pwsh` uitvoeren vanuit sudo.) Als het nodig is om een Power shell-cmdlet uit te voeren vanuit Power shell met sudo, bijvoorbeeld `sudo Set-Date 8/18/2016`, kunt u `sudo pwsh Set-Date 8/18/2016`. Op dezelfde manier kunt u niet rechtstreeks een Power shell-ingebouwde uitvoeren. In plaats daarvan moet u `exec pwsh item_to_exec`doen.

Dit probleem wordt momenteel bijgehouden als onderdeel van [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Ontbrekende cmdlets

Een groot aantal opdrachten (cmdlets) die normaal gesp roken beschikbaar zijn in Power shell zijn niet beschikbaar in Linux/macOS. In veel gevallen hebben deze opdrachten geen zin op deze platformen (bijvoorbeeld Windows-specifieke functies zoals het REGI ster). Andere opdrachten als service besturings opdrachten (Get/start/stop-service) zijn aanwezig, maar niet functioneel. In toekomstige releases worden deze problemen verholpen, worden de gebroken cmdlets gecorrigeerd en worden nieuwe berichten in de loop van de tijd toegevoegd.

### <a name="command-availability"></a>Beschik baarheid van opdracht

De volgende tabel bevat opdrachten die bekend zijn in Power shell op Linux/macOS.

|Opdrachten|Operationele status|Notities|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Niet beschikbaar.|Deze opdrachten worden niet herkend. Dit moet in een toekomstige release worden opgelost.|
|`Get-Acl`, `Set-Acl`|Niet beschikbaar.|Deze opdrachten worden niet herkend. Dit moet in een toekomstige release worden opgelost.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Niet beschikbaar.|Deze opdrachten worden niet herkend. Dit moet in een toekomstige release worden opgelost.|
|`Wait-Process`|Beschikbaar, werkt niet goed. |`Start-Process gvim -PassThru | Wait-Process` werkt bijvoorbeeld niet; Er kan niet worden gewacht op het proces.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Beschikbaar, maar werkt niet.|Schrijft een fout bericht dat aangeeft dat de opdrachten niet werken. Deze moeten worden opgelost in een toekomstige release.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Beschikbaar, maar er zijn geen gebeurtenis bronnen beschikbaar.|De opdrachten voor het uitvoeren van Power shell-gebeurtenissen zijn aanwezig, maar de meeste gebeurtenis bronnen die worden gebruikt met de opdrachten (zoals System. time-out. timer) zijn niet beschikbaar in Linux, waardoor de opdrachten overbodig zijn in de alpha-release.|
|`Set-ExecutionPolicy`|Beschikbaar, maar werkt niet.|Retourneert een bericht dat niet wordt ondersteund op dit platform. Uitvoerings beleid is een gebruikers gerichte "veiligheids gordel" waarmee wordt voor komen dat de gebruiker kost bare fouten kan maken. Het is geen beveiligings grens.|
|`New-PSSessionOption`, `New-PSTransportOption`|Beschikbaar, maar `New-PSSession` werken niet.|`New-PSSessionOption` en `New-PSTransportOption` momenteel niet worden gecontroleerd om `New-PSSession` nu te werken.|
