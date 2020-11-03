---
description: In Windows Power shell wordt een Windows-gebeurtenis logboek gemaakt met de naam Windows Power shell om Windows Power shell-gebeurtenissen vast te leggen. U kunt dit logboek weer geven in Logboeken of met behulp van cmdlets die gebeurtenissen ophalen, zoals de `Get-EventLog` cmdlet. Standaard worden de gebeurtenissen van de Windows Power shell-engine en provider vastgelegd in het gebeurtenis logboek, maar u kunt de voorkeurs variabelen voor gebeurtenis Logboeken gebruiken om het gebeurtenis logboek aan te passen. U kunt bijvoorbeeld gebeurtenissen over Windows Power shell-opdrachten toevoegen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252806"
---
# <a name="about-eventlogs"></a>Over gebeurtenis logboeken

## <a name="short-description"></a>Korte beschrijving

In Windows Power shell wordt een Windows-gebeurtenis logboek gemaakt met de naam Windows Power shell om Windows Power shell-gebeurtenissen vast te leggen. U kunt dit logboek weer geven in Logboeken of met behulp van cmdlets die gebeurtenissen ophalen, zoals de `Get-EventLog` cmdlet. Standaard worden de gebeurtenissen van de Windows Power shell-engine en provider vastgelegd in het gebeurtenis logboek, maar u kunt de voorkeurs variabelen voor gebeurtenis Logboeken gebruiken om het gebeurtenis logboek aan te passen. U kunt bijvoorbeeld gebeurtenissen over Windows Power shell-opdrachten toevoegen.

## <a name="long-description"></a>Lange beschrijving

In het gebeurtenis logboek van Windows Power shell worden gegevens van Windows Power shell-bewerkingen vastgelegd, zoals het starten en stoppen van de programma-engine en het starten en stoppen van de Windows Power shell-providers. U kunt ook informatie over Windows Power shell-opdrachten vastleggen in een logboek.

Het gebeurtenis logboek van Windows Power Shell bevindt zich in de groep toepassings-en service Logboeken. Het Windows Power shell-logboek is een klassiek gebeurtenis logboek dat geen gebruik maakt van de Windows eventing-technologie. Als u het logboek wilt weer geven, gebruikt u de cmdlets die zijn ontworpen voor klassieke gebeurtenis logboeken, zoals `Get-EventLog` .

## <a name="viewing-the-windows-powershell-event-log"></a>Het gebeurtenis logboek van Windows Power shell weer geven

U kunt het Windows Power shell-gebeurtenis logboek weer geven in Logboeken of met behulp van de- `Get-EventLog` en- `Get-WmiObject` cmdlets. Als u de inhoud van het Windows Power shell-logboek wilt weer geven, typt u:

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

Als u de gebeurtenissen en hun eigenschappen wilt bekijken, gebruikt u de `Sort-Object` cmdlet, de `Group-Object` cmdlet en de cmdlets die de `Format` opdracht (de `Format` cmdlets) bevatten.

Als u bijvoorbeeld de gebeurtenissen in het logboek wilt weer geven, gegroepeerd op gebeurtenis-ID, typt u:

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

Of typ:

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

Als u alle klassieke gebeurtenis logboeken wilt weer geven, typt u:

```powershell
Get-EventLog -List
```

U kunt de cmdlet ook gebruiken `Get-WmiObject` om de WMI-klassen (gebeurtenis-gerelateerde Windows Management Instrumentation) te gebruiken om het gebeurtenis logboek te onderzoeken. Als u bijvoorbeeld alle eigenschappen van het gebeurtenis logboek bestand wilt weer geven, typt u:

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

Als u de WMI-klassen wilt vinden die aan Win32-gebeurtenissen zijn gerelateerd, typt u:

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

Typ "Get-Help Get-EventLog" en "Get-Help Get-WmiObject" voor meer informatie.

## <a name="selecting-events-for-the-windows-powershell-event-log"></a>Gebeurtenissen selecteren voor het gebeurtenis logboek van Windows Power shell

U kunt de voorkeurs variabelen van gebeurtenis Logboeken gebruiken om te bepalen welke gebeurtenissen worden vastgelegd in het gebeurtenis logboek van Windows Power shell.

Er zijn zes voorkeurs variabelen voor gebeurtenis Logboeken. twee variabelen voor elk van de drie logboek registratie-onderdelen: de engine (het Windows Power shell-programma), de providers en de opdrachten. De LifeCycleEvent-variabelen registreren normaal starten en stoppen van gebeurtenissen. De status variabelen registreren fout gebeurtenissen.

De volgende tabel bevat de voorkeurs variabelen van gebeurtenis Logboeken.

|Variabele                  |Beschrijving                                    |
|--------------------------|-----------------------------------------------|
|$LogEngineLifeCycleEvent  |Registreert het starten en stoppen van Power shell          |
|$LogEngineHealthEvent     |Logboeken van Power shell-programma fouten                 |
|$LogProviderLifeCycleEvent|Registreert het starten en stoppen van Power shell-providers|
|$LogProviderHealthEvent   |Logboeken van Power shell-provider fouten                |
|$LogCommandLifeCycleEvent |Hiermee wordt het starten en volt ooien van opdrachten geregistreerd   |
|$LogCommandHealthEvent    |Registreert opdracht fouten                            |

(Zie [about_Providers](about_Providers.md)voor meer informatie over Windows Power shell-providers.)

Standaard worden alleen de volgende gebeurtenis typen ingeschakeld:

* $LogEngineLifeCycleEvent
* $LogEngineHealthEvent
* $LogProviderLifeCycleEvent
* $LogProviderHealthEvent

Als u een gebeurtenis type wilt inschakelen, stelt u de voorkeurs variabele voor dat gebeurtenis type in op $true. Als u bijvoorbeeld gebeurtenissen voor levens cyclus van opdrachten wilt inschakelen, typt u:

```powershell
$LogCommandLifeCycleEvent
```

Of typ:

```powershell
$LogCommandLifeCycleEvent = $true
```

Als u een gebeurtenis type wilt uitschakelen, stelt u de voorkeurs variabele voor dat gebeurtenis type in op $false. Als u bijvoorbeeld de opdracht levens cyclus gebeurtenissen wilt uitschakelen, typt u:

```powershell
$LogProviderLifeCycleEvent = $false
```

U kunt elke gebeurtenis uitschakelen, met uitzonde ring van de gebeurtenissen die aangeven dat de Windows Power shell-engine en de kern providers worden gestart. Deze gebeurtenissen worden gegenereerd voordat de Windows Power shell-profielen worden uitgevoerd en voordat het hostprogramma gereed is om opdrachten te accepteren.

De instellingen van de variabele zijn alleen van toepassing op de huidige Windows Power shell-sessie.
Als u deze wilt Toep assen op alle Windows Power shell-sessies, voegt u deze toe aan uw Windows Power shell-profiel.

## <a name="logging-module-events"></a>Logboek registratie module gebeurtenissen

Vanaf Windows Power Shell 3,0 kunt u uitvoerings gebeurtenissen vastleggen voor de cmdlets en functies in Windows Power shell-modules en-modules door de eigenschap LogPipelineExecutionDetails van modules en modules in te stellen op TRUE. In Windows Power Shell 2,0 is deze functie alleen beschikbaar voor modules.

Wanneer de waarde van de eigenschap LogPipelineExecutionDetails TRUE ( `$true` ) is, schrijft Windows Power shell cmdlet-en Function Execution-gebeurtenissen in de sessie naar de Windows Power shell-aanmeld Logboeken. De instelling is alleen effectief in de huidige sessie.

Als u logboek registratie van uitvoerings gebeurtenissen van cmdlets en functies in een module wilt inschakelen, gebruikt u de volgende opdracht reeks.

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

Als u logboek registratie van uitvoerings gebeurtenissen van cmdlets in een module wilt inschakelen, gebruikt u de volgende opdracht reeks.

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

Als u logboek registratie wilt uitschakelen, gebruikt u dezelfde opdracht reeks om de eigenschaps waarde in te stellen op FALSE ( `$false` ).

U kunt ook de instelling ' module logboek registratie inschakelen ' groepsbeleid gebruiken om module-en module logboek registratie in te scha kelen en uit te scha kelen. De beleids waarde bevat een lijst van module-en module namen. Joker tekens worden ondersteund.

Wanneer het inschakelen van module logboek registratie is ingesteld voor een module, is de waarde van de eigenschap LogPipelineExecutionDetails van de module in alle sessies waar en kan niet worden gewijzigd.

De groeps beleids instelling voor het inschakelen van module logboek registratie bevindt zich in de volgende groepsbeleid paden:

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

Het gebruikers configuratie beleid heeft voor rang op het computer configuratie beleid en beide beleids regels hebben voor keur boven de waarde van de eigenschap LogPipelineExecutionDetails van modules en modules.

Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie over deze Groepsbeleid instelling.

## <a name="security-and-auditing"></a>Beveiliging en controle

Het gebeurtenis logboek van Windows Power shell is ontworpen om activiteiten aan te duiden en operationele details te bieden voor het oplossen van problemen.

Net als de meeste Windows-logboeken voor toepassings gebeurtenissen is het Windows Power shell-gebeurtenis logboek echter niet ontworpen om beveiligd te zijn. Het mag niet worden gebruikt om de beveiliging te controleren of om vertrouwelijke of eigendoms gegevens vast te leggen.

Gebeurtenis logboeken zijn bedoeld om te worden gelezen en begrepen door gebruikers. Gebruikers kunnen lezen uit en schrijven naar het logboek. Een kwaadwillende gebruiker kan een gebeurtenis logboek op een lokale of externe computer lezen, onwaare gegevens opnemen en vervolgens voor komen dat hun activiteiten worden geregistreerd.

## <a name="notes"></a>Opmerkingen

Auteurs van module ontwerpers kunnen logboek functies toevoegen aan hun modules. Zie [een Windows Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Get-EventLog](xref:Microsoft.PowerShell.Management.Get-EventLog)

[Get-WmiObject](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Preference_Variables](about_Preference_Variables.md)
