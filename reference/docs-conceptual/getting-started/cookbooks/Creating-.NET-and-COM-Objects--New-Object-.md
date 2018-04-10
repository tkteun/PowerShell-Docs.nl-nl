---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: .NET- en COM-objecten Nieuw Object maken
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="creating-net-and-com-objects-new-object"></a>.NET- en COM-objecten (Nieuw Object) maken

Er zijn softwareonderdelen met .NET Framework en COM-interfaces waarmee u veel system-beheertaken uitvoeren. Windows PowerShell kunt u deze onderdelen te gebruiken zodat u niet beperkt tot de taken die kunnen worden uitgevoerd zijn met behulp van cmdlets. Veel van de cmdlets in de initiële versie van Windows PowerShell werkt niet op externe computers. Wordt gedemonstreerd hoe u deze beperking omzeilen bij het beheren van gebeurtenislogboeken met behulp van .NET Framework **System.Diagnostics.EventLog** klasse rechtstreeks vanuit Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Nieuw Object gebruiken voor gebeurtenislogboek-toegang

.NET Framework Class Library bevat een klasse met de naam **System.Diagnostics.EventLog** die kunnen worden gebruikt voor het beheren van gebeurtenislogboeken. U kunt een nieuw exemplaar van een .NET Framework-klasse maken met behulp van de **New-Object** cmdlet uit met de **TypeName** parameter. De volgende opdracht maakt bijvoorbeeld een verwijzing naar een gebeurtenislogboek:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Hoewel de opdracht een instantie van de klasse EventLog gemaakt heeft, bevatten het exemplaar geen gegevens. Dat komt doordat er een bepaald gebeurtenislogboek niet is opgegeven. Hoe krijg ik een echte gebeurtenislogboek?

#### <a name="using-constructors-with-new-object"></a>Met behulp van Constructors met nieuw Object

Om te verwijzen naar een specifiek gebeurtenislogboek, moet u de naam van het logboek opgeven. **Nieuw Object** heeft een **ArgumentList** parameter. De argumenten die u aan deze parameter als waarden doorgeven worden gebruikt door een speciale opstartmethode van het object. De methode wordt aangeroepen een *constructor* omdat deze wordt gebruikt om het object te maken. Bijvoorbeeld als u een verwijzing naar het toepassingslogboek, geeft u de tekenreeks 'Toepassing' als een argument:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Aangezien de meeste van de .NET Framework core-klassen zijn opgenomen in de naamruimte System, probeert Windows PowerShell automatisch te vinden van de klassen die u in de naamruimte System opgeeft als er een overeenkomst voor de typename die u opgeeft geen gevonden. Dit betekent dat u Diagnostics.EventLog in plaats van System.Diagnostics.EventLog kunt opgeven.

#### <a name="storing-objects-in-variables"></a>Opslaan van objecten in variabelen

Het is raadzaam voor het opslaan van een verwijzing naar een object, zodat u deze in de huidige shell gebruiken kunt. Hoewel Windows PowerShell u veel work met pijplijnen kunt, vermindering van de noodzaak van variabelen, maakt soms verwijzingen naar objecten opslaan in variabelen het eenvoudiger om deze objecten te bewerken.

Windows PowerShell kunt u variabelen maken die in principe zijn benoemde objecten. De uitvoer van een geldige Windows PowerShell-opdracht kan worden opgeslagen in een variabele. Namen van variabelen beginnen altijd met $. Als u wilt de verwijzing van het logboek Application opslaat in een variabele met de naam $AppLog, typ de naam van wordt de variabele, gevolgd door een gelijkteken en typ de opdracht die wordt gebruikt voor het maken van het toepassingsobject logboek:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Als u vervolgens $AppLog typt, ziet u dat deze het toepassingslogboek bevat:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Toegang tot een externe Nieuw Object-gebeurtenislogboek

De opdrachten in de vorige sectie gericht op de lokale computer; de **Get EventLog** cmdlet kunt dit doen. Voor toegang tot het toepassingslogboek op een externe computer, moet u zowel de naam van het logboek en een computernaam (of IP-adres) opgeven als argumenten.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Nu dat we een verwijzing naar een gebeurtenislogboek opgeslagen in de variabele $RemoteAppLog hebben, welke taken kunnen we op uitvoeren?

#### <a name="clearing-an-event-log-with-object-methods"></a>Wissen van een gebeurtenislogboek met objectmethoden

Objecten hebben vaak methoden die kunnen worden aangeroepen als taken wilt uitvoeren. U kunt **Get-lid** om de methoden die zijn gekoppeld aan een object weer te geven. De volgende opdracht en de geselecteerde uitvoer zijn voorbeelden de methoden van de EventLog-klasse:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

De **Clear()** methode kan worden gebruikt om te wissen van het gebeurtenislogboek. Wanneer u een methode aanroept, moet u altijd de methodenaam volgen door haakjes, zelfs als de methode geen argumenten vereist. Hiermee kunt Windows PowerShell onderscheid maken tussen de methode en een mogelijke eigenschap met dezelfde naam. Typ het volgende aan te roepen de **wissen** methode:

```
PS> $RemoteAppLog.Clear()
```

Typ het volgende om het logboek weer te geven. U ziet dat het gebeurtenislogboek is uitgeschakeld en nu 0 vermeldingen in plaats van 262 is:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>COM-objecten maken met een nieuw Object
U kunt **New-Object** werken met onderdelen van de Component Object Model (COM). Het bereik van de onderdelen van de verschillende bibliotheken opgenomen ActiveX-toepassingen zoals Internet Explorer die zijn geïnstalleerd op de meeste systemen met Windows Script Host (WSH).

**Nieuw Object** gebruikmaakt van .NET Framework Runtime-Callable-Wrappers COM-objecten te maken, zodat deze dezelfde beperkingen als .NET Framework biedt heeft bij het aanroepen van COM-objecten. Voor het maken van een COM-object, moet u opgeven de **ComObject** parameter met de programma-id of *ProgId* van de COM-klasse die u wilt gebruiken. Een uitgebreide bespreking van de beperkingen van de COM-gebruik en het bepalen van wat ProgID's zijn beschikbaar op een systeem valt buiten het bereik van deze handleiding, maar het meest bekende objecten uit omgevingen zoals WSH kunnen worden gebruikt in Windows PowerShell.

U kunt de objecten WSH maken door op te geven deze ProgID: **instantie**, **WScript.Network**, **Scripting.Dictionary**, en  **Scripting.FileSystemObject**. De volgende opdrachten maakt deze objecten:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Hoewel de meeste functionaliteit van deze klassen beschikbaar zijn op andere manieren in Windows PowerShell wordt gemaakt, zijn een paar taken, zoals het maken van snelkoppeling nog steeds gemakkelijker te doen met behulp van de klassen WSH.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Maken van een snelkoppeling op het bureaublad met instantie

Een taak die snel kan worden uitgevoerd met een COM-object met het maken van een snelkoppeling. Stel dat u wilt een snelkoppeling op het bureaublad maken die verwijst naar de basismap voor Windows PowerShell. U moet eerst maakt u een verwijzing naar **instantie**, die wordt opgeslagen in een variabele met de naam **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-lid werkt met COM-objecten, zodat u op de leden van het object door te typen vindt:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-lid** is een optionele **InputObject** parameter kunt u in plaats van piping om te voorzien van gegevens **Get-lid**. Krijgt u hetzelfde uitvoer zoals hierboven als u in plaats daarvan de opdracht gebruikt **lid zijn van Get - InputObject $WshShell**. Als u **InputObject**, worden behandeld als het argument als één item. Dit betekent dat als er meerdere objecten in een variabele, **Get-lid** ze worden beschouwd als een matrix met objecten. Bijvoorbeeld:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

De **instantie CreateShortcut** methode accepteert één argument, het pad naar het snelkoppelingsbestand maken. We kunnen typt in het volledige pad naar het bureaublad, maar er is een eenvoudigere manier. Het bureaublad wordt normaal gesproken vertegenwoordigd door een map met de naam Desktop binnen de basismap van de huidige gebruiker. Windows PowerShell is een variabele **$Home** die het pad naar deze map bevat. We kunnen het pad naar de basismap opgeven met behulp van deze variabele en voeg vervolgens de naam van de map bureaublad en de naam voor de snelkoppeling maken door te typen:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Wanneer u iets dat op de naam van een variabele binnen dubbele aanhalingstekens lijkt gebruikt, wordt Windows PowerShell probeert te vervangen door een overeenkomende waarde. Als u één aanhalingstekens gebruikt, probeert Windows PowerShell niet vervangen door de variabele waarde. Probeer bijvoorbeeld de volgende opdrachten te typen:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

We hebt nu een variabele met de naam **$lnk** die een nieuwe snelkoppeling-verwijzing bevat. Als u zien van de leden wilt, kunt u het doorsluizen naar **Get-lid**. De onderstaande uitvoer ziet u de leden moeten we onze snelkoppeling gebruiken:

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

Moeten we geven de **TargetPath**, dit is de toepassingsmap voor Windows PowerShell en sla de snelkoppeling **$lnk** door het aanroepen van de **opslaan** methode. Het pad van de Windows PowerShell-toepassing wordt opgeslagen in de variabele **$PSHome**, zodat we dit door te typen doen kunt:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Met behulp van Internet Explorer vanuit Windows PowerShell

Veel toepassingen (met inbegrip van de Microsoft Office-familie van toepassingen en Internet Explorer) kunnen worden geautomatiseerd met behulp van COM. Internet Explorer ziet u enkele van de gangbare technieken en problemen die zijn betrokken bij het werken met COM gebaseerde toepassingen.

U een exemplaar van Internet Explorer maken door de Internet Explorer ProgId **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Met deze opdracht Start Internet Explorer, maar is niet zichtbaar maken. Als u een Get-Process typt, ziet u dat een proces met de naam iexplore wordt uitgevoerd. Zelfs als u Windows PowerShell afsluit, blijft het proces actief. U moet de computer opnieuw opstarten of een hulpprogramma zoals Taakbeheer gebruiken om de iexplore proces te beëindigen.

> [!NOTE]
> COM-objecten die worden gestart als afzonderlijke processen genoemd *uitvoerbare bestanden ActiveX*, kan of kunnen niet een gebruikersinterface-venster weergeven wanneer deze opgestart worden. Als ze geen venster maken, maar maak niet wordt weergegeven, zoals Internet Explorer, de focus in het algemeen wordt verplaatst naar het Windows-bureaublad en moet u het venster zichtbaar ermee te maken.

Door te typen **$ie | Get-lid**, kunt u eigenschappen en methoden voor Internet Explorer weergeven. Stel de eigenschap Visible op $true door te voeren overzicht van de Internet Explorer-venster:

```powershell
$ie.Visible = $true
```

U kunt vervolgens naar een specifieke webadres navigeren met behulp van de methode navigeren:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Met andere leden van het Internet Explorer-objectmodel, is het mogelijk tekstinhoud ophalen van de webpagina. De volgende opdracht worden de HTML-tekst in de hoofdtekst van de huidige webpagina weergegeven:

```powershell
$ie.Document.Body.InnerText
```

Roep de methode Quit() Internet Explorer uit in PowerShell om af te sluiten:

```powershell
$ie.Quit()
```

Deze toepassing nu afsluiten. Een geldige verwijzing naar bevat de ie-variabele $ niet langer zelfs als deze nog steeds lijkt te zijn van een COM-object. Als u probeert te gebruiken, krijgt u een automatiseringsfout:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

U kunt een verwijderen ie naar de resterende verwijzen met een opdracht zoals $ = $null of volledig verwijderen van de variabele door te typen:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Er is geen algemene standaard voor uitvoerbare bestanden ActiveX sluiten of worden uitgevoerd wanneer u een verwijzing naar een verwijdert. Afhankelijk van de omstandigheden zoals bepaalt of de toepassing zichtbaar is, of een bewerkte document erin wordt uitgevoerd en zelfs of Windows PowerShell wordt nog steeds uitgevoerd, wordt de toepassing kan of kan niet worden afgesloten. Daarom moet u beëindiging gedrag testen voor elke ActiveX uitvoerbare dat u wilt gebruiken in Windows PowerShell.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Waarschuwingen over .NET Framework ingepakt COM-objecten

In sommige gevallen kan een COM-object een bijbehorende .NET Framework wellicht *Runtime-Callable Wrapper* RCW en dit wordt gebruikt door **New-Object**. Omdat het gedrag van de RCW van het gedrag van het normale COM-object afwijken kan **New-Object** heeft een **Strict** parameter om u te waarschuwen over RCW toegang. Als u opgeeft de **Strict** parameter en maak vervolgens een COM-object dat gebruikmaakt van een RCW, wordt er een waarschuwing weergegeven:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Hoewel het object nog steeds gemaakt is, wordt u gewaarschuwd dat het niet standaard COM-object is.