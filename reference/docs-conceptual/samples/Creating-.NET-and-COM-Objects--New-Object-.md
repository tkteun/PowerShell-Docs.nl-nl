---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: .NET- en COM-objecten Nieuw Object maken
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: ef8215303aacd90536d3c2ae57bc3629e202f318
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984309"
---
# <a name="creating-net-and-com-objects-new-object"></a>.NET- en COM-objecten (New-Object) maken

Er zijn softwareonderdelen met .NET Framework en COM-interface waarmee u veel system-beheertaken kunt uitvoeren. Windows PowerShell kunt u deze onderdelen te gebruiken, zodat u niet beperkt tot de taken die kunnen worden uitgevoerd bent met behulp van cmdlets. Veel van de in de eerste release van Windows PowerShell-cmdlets werken niet op basis van externe computers. Er wordt gedemonstreerd hoe u deze beperking omzeilen bij het beheren van gebeurtenislogboeken met behulp van .NET Framework **System.Diagnostics.EventLog** klasse rechtstreeks vanuit Windows PowerShell.

## <a name="using-new-object-for-event-log-access"></a>Met behulp van New-Object voor de Event Log-toegang

De .NET Framework-klassenbibliotheek bevat een klasse met de naam **System.Diagnostics.EventLog** die kunnen worden gebruikt voor het beheren van gebeurtenislogboeken. U kunt een nieuw exemplaar van een .NET Framework-klasse maken met behulp van de **New-Object** cmdlet met de **TypeName** parameter. De volgende opdracht maakt bijvoorbeeld een gebeurtenislogboek-verwijzing:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Hoewel de opdracht een exemplaar van de klasse EventLog gemaakt heeft, wordt het exemplaar geen gegevens bevatten. Dat komt doordat we een bepaald gebeurtenislogboek niet is opgegeven. Hoe ontvang ik een echte gebeurtenislogboek?

### <a name="using-constructors-with-new-object"></a>Met behulp van Constructors met New-Object

Om te verwijzen naar een specifiek gebeurtenislogboek, moet u de naam van het logboek op te geven. **New-Object** heeft een **ArgumentList** parameter. De argumenten die u aan deze parameter als waarden doorgeven worden gebruikt door een speciale opstartmethode van het object. De methode wordt aangeroepen een *constructor* omdat deze wordt gebruikt om het object te maken. Bijvoorbeeld, als u een verwijzing naar het toepassingslogboek, geeft u de tekenreeks 'Application' als een argument:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Omdat de meeste van de .NET Framework core-klassen zijn opgenomen in de naamruimte System, probeert Windows PowerShell automatisch te vinden van de klassen die u in de naamruimte System opgeeft als er een overeenkomst voor de typename die u opgeeft niet kunt vinden. Dit betekent dat u Diagnostics.EventLog in plaats van System.Diagnostics.EventLog kunt opgeven.

### <a name="storing-objects-in-variables"></a>Opslaan van objecten in de variabelen

Het is raadzaam om op te slaan een verwijzing naar een object, zodat u deze in de huidige shell gebruiken kunt. Hoewel Windows PowerShell u zich veel werk met pijplijnen kunt, vermindering van de noodzaak van variabelen, maakt soms ook verwijzingen naar objecten opslaan in de variabelen het eenvoudiger om deze objecten te bewerken.

Windows PowerShell kunt u variabelen maken die in feite objecten benoemde zijn. De uitvoer van een geldige Windows PowerShell-opdracht kan worden opgeslagen in een variabele. Namen van variabelen begint altijd met $. Als u wilt de toepassing-logboek: naslag opslaan in een variabele met de naam $AppLog, typ de naam van wordt de variabele, gevolgd door een gelijkteken en typ vervolgens de opdracht die wordt gebruikt voor het maken van het toepassingsobject logboek:

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

### <a name="accessing-a-remote-event-log-with-new-object"></a>Toegang tot een externe gebeurtenislogboek met New-Object

De opdrachten in de voorgaande sectie gericht op de lokale computer. de **Get-EventLog** cmdlet kunt dat doen. Voor toegang tot het toepassingslogboek op een externe computer, moet u zowel de naam van het logboek en een computernaam (of IP-adres) opgeven als argumenten.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Nu dat we een verwijzing naar een gebeurtenislogboek die zijn opgeslagen in de variabele $RemoteAppLog hebben, welke taken kunnen we op uitvoeren?

### <a name="clearing-an-event-log-with-object-methods"></a>Een gebeurtenislogboek dat u met de methoden van het Object uit te schakelen

Objecten hebben vaak methoden die kunnen worden aangeroepen voor het uitvoeren van taken. U kunt **Get-Member** om de methoden die zijn gekoppeld aan een object weer te geven. De volgende opdracht en de geselecteerde uitvoer tonen enkele de methoden van de klasse gebeurtenislogboek:

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

De **Clear()** methode kan worden gebruikt om te wissen van het gebeurtenislogboek wordt geschreven. Bij het aanroepen van een methode, moet u altijd de methodenaam door haakjes, volgen, zelfs als de methode geen argumenten vereist. Hiermee kunt Windows PowerShell onderscheid maken tussen de methoden en een mogelijke eigenschappen met dezelfde naam. Typ het volgende om aan te roepen de **wissen** methode:

```
PS> $RemoteAppLog.Clear()
```

Typ het volgende om het logboek weer te geven. U ziet dat het gebeurtenislogboek is gewist en nu 0 items in plaats van 262 is:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a>Het maken van de COM-objecten met New-Object
U kunt **New-Object** om te werken met onderdelen van de Component Object Model (COM). Onderdelen van het bereik van de verschillende bibliotheken opgenomen ActiveX-toepassingen, zoals Internet Explorer die zijn geïnstalleerd op de meeste systemen met Windows Script Host (WSH).

**New-Object** maakt gebruik van .NET Framework Runtime aanroepbare Wrappers te maken van COM-objecten, zodat deze dezelfde beperkingen die door .NET Framework worden ondersteund heeft bij het aanroepen van COM-objecten. Voor het maken van een COM-object, moet u opgeven de **ComObject** parameter met de programma-id of *ProgId* van de COM-klasse die u wilt gebruiken. Een volledige bespreking van de beperkingen van COM-gebruik en het bepalen van wat programma-id's zijn beschikbaar op een systeem is buiten het bereik van deze handleiding, maar meest bekende objecten uit omgevingen zoals WSH kunnen worden gebruikt in Windows PowerShell.

U kunt de WSH-objecten maken door op te geven deze ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**. De volgende opdrachten maakt deze objecten:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Hoewel de meeste van de functionaliteit van deze klassen beschikbaar op andere manieren in Windows PowerShell wordt gemaakt, zijn een paar taken, zoals het maken van snelkoppeling nog steeds gemakkelijker te doen met behulp van de klassen WSH.

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Het maken van een snelkoppeling op het bureaublad met instantie

Een taak die snel kan worden uitgevoerd met een COM-object is een snelkoppeling maken. Stel dat u wilt maken een snelkoppeling op het bureaublad die verwijst naar de basismap voor Windows PowerShell. U moet eerst maken een verwijzing naar **instantie**, waarbij we wordt opgeslagen in een variabele met de naam **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member werkt met COM-objecten, zodat u de leden van het object door te typen verkennen kunt:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** is een optionele **InputObject** parameter die u in plaats van doorsluizen gebruiken kunt voor invoer naar **Get-Member**. U krijgt dezelfde uitvoer zoals hierboven als u in plaats daarvan de opdracht gebruikt **Get-Member - InputObject $WshShell**. Als u **InputObject**, worden behandeld als het argument als één item. Dit betekent dat als er meerdere objecten in een variabele, **Get-Member** wordt deze beschouwd als een matrix met objecten. Bijvoorbeeld:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

De **instantie CreateShortcut** methode accepteert één argument, het pad naar het snelkoppelingsbestand te maken. We typen in het volledige pad naar het bureaublad, maar er is een eenvoudigere manier. Het bureaublad wordt normaal gesproken vertegenwoordigd door een map met de naam Desktop in de basismap van de huidige gebruiker. Windows PowerShell is een variabele **$Home** die het pad naar deze map bevat. We kunnen het pad naar de basismap opgeven met behulp van deze variabele en voeg de naam van de map op het bureaublad en de naam van de snelkoppeling maken door te typen:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Wanneer u iets dat lijkt op de naam van een variabele tussen dubbele aanhalingstekens gebruikt, wordt Windows PowerShell probeert te vervangen door een overeenkomende waarde. Als u enkele aanhalingstekens gebruikt, probeert Windows PowerShell niet vervangen door de variabele waarde. Probeer bijvoorbeeld de volgende opdrachten te typen:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

We hebben nu een variabele met de naam **$lnk** die een nieuwe snelkoppeling verwijzing bevat. Als u zien van de leden ervan wilt, kunt u het doorgeven aan **Get-Member**. De onderstaande uitvoer ziet u de leden moeten we onze snelkoppeling gebruiken:

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

We moeten om op te geven de **TargetPath**, dit is de toepassingsmap voor Windows PowerShell en sla de snelkoppeling naar de **$lnk** door het aanroepen van de **opslaan** methode. Het pad van de Windows PowerShell-toepassing is opgeslagen in de variabele **$PSHome**, zodat we dit door te typen doen kunnen:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a>Met behulp van Internet Explorer vanuit Windows PowerShell

Veel toepassingen (met inbegrip van de Microsoft Office-familie van toepassingen en Internet Explorer) kunnen worden geautomatiseerd met behulp van COM. Internet Explorer ziet u enkele van de typische technieken en problemen die betrokken zijn bij het werken met COM gebaseerde toepassingen.

Maken van een Internet Explorer-instantie door op te geven de Internet Explorer ProgId, **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Met deze opdracht Internet Explorer te starten, maar wordt deze niet zichtbaar. Als u Get-Process typt, ziet u dat een proces met de naam iexplore wordt uitgevoerd. Als u Windows PowerShell sluit, wordt in feite het proces om uit te voeren blijven. U moet de computer opnieuw opstarten of gebruik een hulpprogramma zoals Taakbeheer om de iexplore-proces te beëindigen.

> [!NOTE]
> COM-objecten die worden gestart als afzonderlijke processen, doorgaans aangeduid *uitvoerbare bestanden ActiveX*, kan of kunnen niet een gebruikersinterface-venster weergeven wanneer ze worden opgestart. Als ze geen venster maken, maar kunnen deze niet zichtbaar, zoals Internet Explorer, de focus in het algemeen wordt verplaatst naar het Windows-bureaublad en moet u het venster om te communiceren met het zichtbaar maken.

Door te typen **$ie | Get-Member**, kunt u eigenschappen en methoden voor Internet Explorer weergeven. Als u wilt de Internet Explorer-venster wordt weergegeven, moet u de zichtbaar eigenschap instellen op $true door te typen:

```powershell
$ie.Visible = $true
```

U kunt vervolgens met behulp van de methode navigeren naar een specifieke webadres navigeren:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Met andere leden van het objectmodel van Internet Explorer, is het mogelijk om op te halen van de tekstinhoud van de webpagina. De volgende opdracht wordt de HTML-tekst weergeven in de hoofdtekst van de huidige webpagina wordt weergegeven:

```powershell
$ie.Document.Body.InnerText
```

Om Internet Explorer uit in PowerShell sluit, moet u de Quit()-methode aanroept:

```powershell
$ie.Quit()
```

Dit wordt gedwongen om te sluiten. De ie variabele $ bevat niet langer een geldige verwijzing zelfs als deze nog steeds wordt weergegeven om te worden van een COM-object. Als u probeert om het te gebruiken, ontvangt u een automatiseringsfout:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

U kunt een verwijderen de resterende verwijzen met een opdracht zoals $ie = $null of verwijder de variabele door te typen:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Er is geen algemene standaard voor uitvoerbare bestanden ActiveX afsluiten of blijven werken wanneer u een verwijzing naar een verwijderen. Afhankelijk van de omstandigheden, zoals of de toepassing zichtbaar is, of een bewerkte document wordt uitgevoerd in het en zelfs of Windows PowerShell wordt nog steeds uitgevoerd, wordt de toepassing kan of kan niet afsluiten. Daarom moet u beëindiging gedrag testen voor elk uitvoerbaar bestand dat u wilt gebruiken in Windows PowerShell.

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Waarschuwingen over .NET Framework-verpakt COM-objecten ophalen

In sommige gevallen mogelijk een COM-object een bijbehorende .NET Framework *Runtime aanroepbare Wrapper* RCW en deze wordt gebruikt door **New-Object**. Omdat het gedrag van de RCW van het gedrag van het normale COM-object afwijken kan, **New-Object** heeft een **strikt** parameter om u te waarschuwen over RCW toegang. Als u opgeeft de **strikt** parameter en maak vervolgens een COM-object dat gebruikmaakt van een RCW, krijgt u een waarschuwingsbericht wordt weergegeven:

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