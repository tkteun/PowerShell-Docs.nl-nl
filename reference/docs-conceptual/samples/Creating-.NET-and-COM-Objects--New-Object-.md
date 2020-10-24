---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: .NET-en COM-objecten maken nieuw object
description: Als een object-georiënteerde script taal ondersteunt Power shell zowel .NET-als COM-objecten. In dit artikel leest u hoe u deze objecten kunt maken en gebruiken.
ms.openlocfilehash: e6189ba465749dd045add7015fc82223c31c7e32
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500569"
---
# <a name="creating-net-and-com-objects-new-object"></a>.NET- en COM-objecten maken (New-Object)

Er zijn software onderdelen met .NET Framework en COM-interfaces waarmee u veel systeem beheer taken kunt uitvoeren. Met Windows Power shell kunt u deze onderdelen gebruiken, zodat u niet beperkt bent tot de taken die kunnen worden uitgevoerd met behulp van-cmdlets. Veel van de cmdlets in de eerste versie van Windows Power shell werken niet op externe computers. Er wordt gedemonstreerd hoe u deze beperking omzeilt bij het beheer van gebeurtenis logboeken met behulp van de klasse .NET Framework **System. Diagnostics. Eventlog** rechtstreeks vanuit Windows Power shell.

## <a name="using-new-object-for-event-log-access"></a>New-Object gebruiken voor toegang tot gebeurtenis logboeken

De .NET Framework Class-bibliotheek bevat een klasse met de naam **System. Diagnostics. Eventlog** die kan worden gebruikt om gebeurtenis logboeken te beheren. U kunt een nieuw exemplaar van een .NET Framework klasse maken met behulp van de cmdlet **New-object** met de para meter **TypeName** . Met de volgende opdracht maakt u bijvoorbeeld een verwijzing naar gebeurtenis logboek:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Hoewel de opdracht een exemplaar van de klasse Event Class heeft gemaakt, bevat het exemplaar geen gegevens. Dat komt omdat er geen specifiek gebeurtenis logboek is opgegeven. Hoe krijg ik een echt gebeurtenis logboek?

### <a name="using-constructors-with-new-object"></a>Constructors gebruiken met New-Object

Als u naar een specifiek gebeurtenis logboek wilt verwijzen, moet u de naam van het logboek opgeven. **New-object** heeft een **argument List** -para meter. De argumenten die u doorgeeft als waarden voor deze para meter worden gebruikt door een speciale opstart methode van het object. De methode wordt een *constructor* genoemd, omdat deze wordt gebruikt om het object samen te stellen. Als u bijvoorbeeld een verwijzing naar het toepassings logboek wilt ophalen, geeft u de teken reeks ' Application ' op als een argument:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Aangezien de meeste van de .NET Framework kern klassen zich in de systeem naam ruimte bevinden, probeert Windows Power shell automatisch klassen te zoeken die u opgeeft in de naam ruimte van het systeem als er geen overeenkomst kan worden gevonden voor de door u opgegeven TypeName. Dit betekent dat u Diagnostische gegevens. EventLog in plaats van System. Diagnostics. EventLog kunt opgeven.

### <a name="storing-objects-in-variables"></a>Objecten in variabelen opslaan

Mogelijk wilt u een verwijzing naar een object opslaan, zodat u deze in de huidige shell kunt gebruiken. Hoewel u met Windows Power shell veel werk met pijp lijnen kunt maken, is het niet meer nodig om variabelen op te slaan naar objecten in variabelen, waardoor het handiger is om deze objecten te manipuleren.

Met Windows Power shell kunt u variabelen maken die hoofd objecten worden genoemd. De uitvoer van een geldige Windows Power shell-opdracht kan worden opgeslagen in een variabele. Namen van variabelen beginnen altijd met $. Als u de verwijzing naar het toepassings logboek wilt opslaan in een variabele met de naam $AppLog, typt u de naam van de variabele, gevolgd door een gelijkteken en typt u vervolgens de opdracht die wordt gebruikt om het toepassings logboek object te maken:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Als u vervolgens $AppLog typt, ziet u dat deze het toepassings logboek bevat:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a>Toegang tot een extern gebeurtenis logboek met New-Object

De opdrachten die in de voor gaande sectie worden gebruikt, zijn gericht op de lokale computer. de cmdlet **get-eventlog** kan dat doen. Als u toegang wilt krijgen tot het toepassings logboek op een externe computer, moet u de naam van het logboek en een computer naam (of IP-adres) als argumenten opgeven.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Nu hebben we een verwijzing naar een gebeurtenis logboek dat is opgeslagen in de variabele $RemoteAppLog, welke taken kunnen we uitvoeren?

### <a name="clearing-an-event-log-with-object-methods"></a>Een gebeurtenis logboek wissen met object methoden

Objecten bevatten vaak methoden die kunnen worden aangeroepen om taken uit te voeren. U kunt **Get-member** gebruiken om de methoden weer te geven die zijn gekoppeld aan een object. De volgende opdracht en de geselecteerde uitvoer tonen een aantal methoden van de klasse Event Class:

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

De methode **Clear ()** kan worden gebruikt om het gebeurtenis logboek te wissen. Wanneer u een methode aanroept, moet u altijd de naam van de methode door haakjes volgen, zelfs als de methode geen argumenten vereist. Hiermee kan Windows Power shell onderscheid maken tussen de methode en een mogelijke eigenschap met dezelfde naam. Typ het volgende om de methode **Clear** aan te roepen:

```
PS> $RemoteAppLog.Clear()
```

Typ het volgende om het logboek weer te geven. U ziet dat het gebeurtenis logboek is gewist en nu 0 vermeldingen bevat in plaats van 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a>COM-objecten maken met New-Object
U kunt **New-object** gebruiken om te werken met component object model-onderdelen (com). Onderdelen variëren van de verschillende bibliotheken die zijn opgenomen in Windows Script Host (WSH) tot ActiveX-toepassingen, zoals Internet Explorer, die op de meeste systemen zijn geïnstalleerd.

**New-object** maakt gebruik van .NET Framework Runtime-Callable wrappers om COM-objecten te maken, zodat deze dezelfde beperkingen heeft als .NET Framework bij het aanroepen van COM-objecten. Als u een COM-object wilt maken, moet u de para meter **ComObject** opgeven met de programmatische id of *ProgID* van de COM-klasse die u wilt gebruiken. Een volledige bespreking van de beperkingen van het COM-gebruik en het bepalen van de beschik bare Progid's op een systeem valt buiten het bereik van deze gebruikers handleiding, maar de meeste bekende objecten van omgevingen zoals WSH kunnen worden gebruikt in Windows Power shell.

U kunt de WSH-objecten maken door deze progid's op te geven: **WScript. shell**, **WScript. Network**, **Scripting. Dictionary**en **Scripting. File System object**. Met de volgende opdrachten maakt u deze objecten:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Hoewel de meeste functies van deze klassen op andere manieren beschikbaar worden gesteld in Windows Power shell, zijn een aantal taken, zoals het maken van snelkoppelingen, nog eenvoudiger te gebruiken met de WSH-klassen.

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Een snelkoppeling op het bureau blad maken met WScript. shell

Een taak die snel kan worden uitgevoerd met een COM-object, is het maken van een snelkoppeling. Stel dat u een snelkoppeling op het bureau blad wilt maken die is gekoppeld aan de basismap voor Windows Power shell. Eerst moet u een verwijzing naar **WScript. shell**maken, die we in een variabele met de naam **$WshShell**opslaan:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member werkt met COM-objecten, zodat u de leden van het object kunt verkennen door het volgende te typen:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-member** heeft een optionele **input object** -para meter die u kunt gebruiken in plaats van sluizen om invoer te leveren voor **Get-member**. U krijgt dezelfde uitvoer zoals hierboven wordt weer gegeven als u in plaats daarvan de opdracht **Get-member-input object $WshShell**hebt gebruikt. Als u **input object**gebruikt, wordt het argument als één item beschouwd. Dit betekent dat als u meerdere objecten in een variabele hebt, **Get-member** ze als een matrix met objecten behandelt. Bijvoorbeeld:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

De **WScript. shell CreateShortcut** -methode accepteert één argument, het pad naar het snelkoppelings bestand dat moet worden gemaakt. We kunnen het volledige pad naar het bureau blad typen, maar er is een eenvoudiger manier. Het bureau blad wordt gewoonlijk vertegenwoordigd door een map met de naam bureau blad in de basismap van de huidige gebruiker. Windows Power Shell heeft een variabele **$Home** die het pad naar deze map bevat. We kunnen het pad naar de basismap opgeven met behulp van deze variabele, en vervolgens de naam van de map Bureau blad en de naam voor de snelkoppeling toevoegen door te typen:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Wanneer u iets gebruikt dat lijkt op een naam van een variabele binnen dubbele aanhalings tekens, probeert Windows Power shell een overeenkomende waarde te vervangen. Als u gebruikmaakt van enkele aanhalings tekens, wordt de waarde van de variabele niet vervangen door Windows Power shell. Typ bijvoorbeeld de volgende opdrachten:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

We hebben nu een variabele met de naam **$lnk** die een nieuwe snelkoppeling referentie bevat. Als u de leden wilt zien, kunt u deze door sluizen naar **Get-lid**. De onderstaande uitvoer toont de leden die we nodig hebben om het maken van de snelkoppeling te volt ooien:

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

We moeten het **TargetPath**opgeven, de toepassingsmap voor Windows Power shell, en vervolgens de snelkoppeling opslaan **$lnk** door de methode **Save** aan te roepen. Het pad naar de map van de Windows Power shell-toepassing wordt opgeslagen in de variabele **$PSHome**, dus we kunnen dit doen door het volgende te typen:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a>Internet Explorer gebruiken vanuit Windows Power shell

Veel toepassingen (met inbegrip van de Microsoft Office-familie van toepassingen en Internet Explorer) kunnen worden geautomatiseerd met behulp van COM. Internet Explorer illustreert enkele van de typische technieken en problemen die betrekking hebben op het werken met op COM gebaseerde toepassingen.

U maakt een Internet Explorer-exemplaar door de Internet Explorer ProgId, **InternetExplorer. toepassing**, op te geven:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Met deze opdracht start u Internet Explorer, maar wordt het niet weer gegeven. Als u Get-process typt, ziet u dat er een proces met de naam Iexplore wordt uitgevoerd. Als u Windows Power shell afsluit, wordt het proces nog steeds uitgevoerd. U moet de computer opnieuw opstarten of een hulp programma als taak beheer gebruiken om het Iexplore-proces te beëindigen.

> [!NOTE]
> COM-objecten die als afzonderlijke processen worden gestart, ook wel *ActiveX-uitvoer bare bestanden*genoemd, kunnen een gebruikers interface venster niet weer geven wanneer ze worden opgestart. Als ze een venster maken, maar dit niet zichtbaar maken, zoals Internet Explorer, wordt de focus meestal verplaatst naar het Windows-bureau blad en moet u het venster zichtbaar maken om ermee te communiceren.

Door $ie te typen **| Get-lid**, u kunt eigenschappen en methoden voor Internet Explorer weer geven. Als u het venster Internet Explorer wilt weer geven, stelt u de eigenschap Visible in op $true door het volgende te typen:

```powershell
$ie.Visible = $true
```

U kunt vervolgens naar een specifiek webadres navigeren met behulp van de methode Navigate:

```powershell
$ie.Navigate("https://devblogs.microsoft.com/scripting/")
```

Met andere leden van het object model van Internet Explorer kunt u tekst inhoud ophalen van de webpagina. Met de volgende opdracht wordt de HTML-tekst in de hoofd tekst van de huidige webpagina weer gegeven:

```powershell
$ie.Document.Body.InnerText
```

Als u Internet Explorer wilt sluiten in Power shell, roept u de methode Quit () aan:

```powershell
$ie.Quit()
```

Hiermee wordt het sluiten afgedwongen. De variabele $ie heeft geen geldige verwijzing meer, zelfs als deze nog steeds een COM-object is. Als u dit probeert te gebruiken, wordt er een automatiserings fout weer geven:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

U kunt de resterende verwijzing verwijderen met een opdracht als $ie = $null of de variabele volledig verwijderen door het volgende te typen:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Er is geen algemene standaard voor of ActiveX-uitvoer bare bestanden worden afgesloten of blijven worden uitgevoerd wanneer u een verwijzing naar een verwijdert. Afhankelijk van de omstandigheden zoals of de toepassing zichtbaar is, of er een bewerkte document wordt uitgevoerd en zelfs of Windows Power shell nog steeds wordt uitgevoerd, wordt de toepassing mogelijk niet afgesloten. Daarom moet u het beëindigings gedrag testen voor elk ActiveX-uitvoerbaar bestand dat u wilt gebruiken in Windows Power shell.

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Waarschuwingen ontvangen over .NET Framework-Wrapped COM-objecten

In sommige gevallen kan een COM-object zijn gekoppeld aan een .NET Framework *runtime-aanroep bare wrapper* of RCW. dit wordt gebruikt door **Nieuw-object**. Aangezien het gedrag van de RCW kan afwijken van het gedrag van het normale COM-object, heeft **New-object** een **strikte** para meter om u te waarschuwen over RCW-toegang. Als u de **strikte** para meter opgeeft en vervolgens een COM-object maakt dat gebruikmaakt van een RCW, wordt er een waarschuwings bericht weer gegeven:

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

Hoewel het object nog wordt gemaakt, wordt u gewaarschuwd dat het geen standaard-COM-object is.
