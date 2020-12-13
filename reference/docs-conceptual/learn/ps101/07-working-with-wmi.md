---
title: Werken met WMI
description: Power Shell heeft cmdlets voor het werken met WMI sinds het begin.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436517"
---
# <a name="chapter-7---working-with-wmi"></a>Hoofd stuk 7: werken met WMI

## <a name="wmi-and-cim"></a>WMI en CIM

Power shell wordt standaard geleverd met-cmdlets voor het werken met andere technologieën zoals Windows Management Instrumentation (WMI). Er zijn verschillende systeem eigen WMI-cmdlets die beschikbaar zijn in Power shell zonder dat u extra software of modules hoeft te installeren.

Power Shell heeft cmdlets voor het werken met WMI sinds het begin. `Get-Command` kan worden gebruikt om te bepalen welke WMI-cmdlets bestaan in Power shell. De volgende resultaten zijn afkomstig van mijn Windows 10 Lab-computer waarop Power shell versie 5,1 wordt uitgevoerd. De resultaten kunnen variëren, afhankelijk van de Power shell-versie die u gebruikt.

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

Common Information Model (CIM)-cmdlets zijn geïntroduceerd in Power shell versie 3,0. De CIM-cmdlets zijn zodanig ontworpen dat ze kunnen worden gebruikt op zowel Windows-als niet-Windows-machines. De WMI-cmdlets zijn afgeschaft, zodat u aanbeveling hebt om de CIM-cmdlets te gebruiken in plaats van de oudere WMI.

De CIM-cmdlets zijn allemaal opgenomen in een module. Als u een lijst met de CIM-cmdlets wilt ophalen, gebruikt u `Get-Command` de para meter **module** , zoals in het volgende voor beeld wordt weer gegeven.

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

Met de CIM-cmdlets kunt u nog steeds met WMI werken, dus niet verwarren wanneer iemand de instructie maakt wanneer ik WMI Zoek met de Power shell-cmdlets...

Zoals eerder vermeld, is WMI een afzonderlijke technologie van Power shell en gebruikt u alleen de CIM-cmdlets voor toegang tot WMI. Mogelijk vindt u een oud VBScript waarin WMI Query Language (WQL) wordt gebruikt om een query uit te zoeken op WMI, zoals in het volgende voor beeld.

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

U kunt de WQL-query uit die VBScript halen en deze gebruiken met de cmdlet zonder dat u wijzigingen hoeft aan te brengen `Get-CimInstance` .

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Dat is niet hoe ik Norma liter een query uitvoeren op WMI met Power shell. Maar dit werkt wel en u kunt eenvoudig bestaande VBScripts migreren naar Power shell. Gebruik de volgende syntaxis wanneer ik een one-line-bewerking start om te zoeken in WMI.

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Als ik alleen het serie nummer wil, kan ik de uitvoer door sluizen naar `Select-Object` en alleen de eigenschap **serialnumber** opgeven.

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Standaard zijn er verschillende eigenschappen die worden opgehaald achter de scènes die nooit worden gebruikt.
Het is mogelijk niet erg belang rijk bij het uitvoeren van query's op de lokale computer. Maar zodra u het uitvoeren van een query op externe computers hebt gestart, is het niet alleen extra verwerkings tijd om die informatie te retour neren, maar ook aanvullende informatie die nodig is om over het netwerk te halen. `Get-CimInstance` heeft een **eigenschaps** parameter die de opgehaalde informatie beperkt. Hierdoor wordt de query op WMI efficiënter.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

De vorige resultaten hebben een object geretourneerd. Als u een eenvoudige teken reeks wilt retour neren, gebruikt u de para meter **ExpandProperty** .

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

U kunt ook de syntaxis met gestippelde opmaak gebruiken om een eenvoudige teken reeks te retour neren. Dit elimineert de nood zaak om te pipeen `Select-Object` .

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>Query's uitvoeren op externe computers met de CIM-cmdlets

Er wordt nog steeds Power shell uitgevoerd als lokale beheerder die een domein gebruiker is. Wanneer ik via de cmdlet gegevens van een externe computer probeer op te vragen `Get-CimInstance` , krijg ik een fout bericht over geweigerde toegang.

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

Veel mensen hebben problemen met de beveiliging van Power shell, maar de waarheid is dat u precies dezelfde machtigingen hebt in Power shell als in de gebruikers interface. Niet meer en niet minder. Het probleem in het vorige voor beeld is dat de gebruiker die Power shell uitvoert, geen rechten heeft om de WMI-gegevens van de DC01-server op te vragen. Ik kan Power shell opnieuw starten als een domein beheerder omdat deze geen `Get-CimInstance` para meter **Credential** heeft. Maar u kunt het beste een vertrouwens relatie geven, omdat vervolgens alles wat ik uit Power shell uitvoer, wordt uitgevoerd als een domein beheerder. Dit kan gevaarlijk zijn uit veiligheids oogpunt, afhankelijk van de situatie.

Met behulp van het principe van minimale bevoegdheden moet ik via de para meter Credential naar mijn domein beheerders account met behulp van de **referentie** parameter, als er een opdracht is. `Get-CimInstance` heeft geen **referentie** parameter, zodat de oplossing in dit scenario eerst een **CimSession** maakt. Vervolgens gebruikt u de **CimSession** in plaats van een computer naam voor het OPVRAGEN van WMI op de externe computer.

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

De CIM-sessie is opgeslagen in een variabele met de naam `$CimSession` . U kunt ook de `Get-Credential` cmdlet tussen haakjes opgeven, zodat deze eerst wordt uitgevoerd, waarbij u wordt gevraagd naar alternatieve referenties voordat u de nieuwe sessie maakt. In dit hoofd stuk ziet u een een efficiëntere manier om alternatieve referenties op te geven, maar is het belang rijk dat u dit basis concept kent voordat u het complex maakt.

De CIM-sessie die in het vorige voor beeld is gemaakt, kan nu worden gebruikt met de `Get-CimInstance` cmdlet voor het opvragen van de BIOS-gegevens van WMI op de externe computer.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

Er zijn verschillende extra voor delen voor het gebruik van CIM-sessies in plaats van alleen een computer naam op te geven. Wanneer u meerdere query's uitvoert op dezelfde computer, is het gebruik van een CIM-sessie efficiënter dan het gebruik van de computer naam voor elke query. Als u een CIM-sessie maakt, wordt de verbinding slechts eenmaal ingesteld.
Vervolgens gebruiken meerdere query's diezelfde sessie om informatie op te halen. Als u de computer naam gebruikt, moeten de cmdlets de verbinding met elke afzonderlijke query instellen en afbreken.

De `Get-CimInstance` cmdlet maakt standaard gebruik van het WSMan-protocol, wat betekent dat de externe computer Power shell-versie 3,0 of hoger nodig heeft om verbinding te maken. Het is in werkelijkheid niet de Power shell-versie die van belang is, de stack versie. De stack versie kan worden bepaald met behulp van de `Test-WSMan` cmdlet.
Dit moet versie 3,0 zijn. Dat is de versie die u vindt in Power shell versie 3,0 en hoger.

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

De oudere WMI-cmdlets gebruiken het DCOM-protocol, dat compatibel is met oudere versies van Windows. DCOM wordt doorgaans geblokkeerd door de firewall op nieuwere versies van Windows. `New-CimSessionOption`Met de cmdlet kunt u een DCOM-protocol verbinding maken voor gebruik met `New-CimSession` . Op deze manier kan de `Get-CimInstance` cmdlet worden gebruikt om te communiceren met windows 2000 Server-versies als verouderd. Dit betekent ook dat Power shell niet is vereist op de externe computer wanneer de `Get-CimInstance` cmdlet wordt gebruikt met een CimSession die is geconfigureerd voor het gebruik van het DCOM-protocol.

Maak de DCOM-protocol optie met de `New-CimSessionOption` cmdlet en sla deze op in een variabele.

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

Voor efficiëntie kunt u uw domein beheerder of verhoogde referenties in een variabele opslaan, zodat u deze niet voortdurend hoeft in te voeren voor elke opdracht.

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

Ik heb een server met de naam SQL03 waarop Windows Server 2008 (niet-R2) wordt uitgevoerd. Het is het nieuwste Windows Server-besturings systeem waarop Power shell niet standaard is geïnstalleerd.

Een **CimSession** maken voor SQL03 met behulp van het DCOM-protocol.

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

In de vorige opdracht is deze keer de variabele opgegeven met de naam `$Cred` voor de para meter **Credential** in plaats van deze hand matig opnieuw in te voeren.

De uitvoer van de query is hetzelfde, ongeacht het gebruikte onderliggende protocol.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

De `Get-CimSession` cmdlet wordt gebruikt om te zien welke **CimSessions** momenteel zijn verbonden en welke protocollen ze gebruiken.

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

Haal de eerder gemaakte **CimSessions** op in een variabele met de naam en sla deze op `$CimSession` .

```powershell
$CimSession = Get-CimSession
```

Een query uitvoeren op beide computers met één opdracht, een met het WSMan-protocol en de andere met DCOM.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

Ik heb talloze blog artikelen geschreven over de WMI-en CIM-cmdlets. Een van de meest nuttige voor waarden is over een functie die ik heb gemaakt om automatisch te bepalen of WSMan of DCOM moet worden gebruikt en de CIM-sessie automatisch instellen zonder dat deze hand matig moet worden uitgesteld. Dit blog artikel heet [Power shell-functie voor het maken van CimSessions op externe computers met terugval naar DCOM][].

Wanneer u klaar bent met de CIM-sessies, moet u deze verwijderen met de `Remove-CimSession` cmdlet. Als u alle CIM-sessies wilt verwijderen, hoeft u alleen maar naar de pipe `Get-CimSession` te verplaatsen `Remove-CimSession` .

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd hoe u Power shell gebruikt voor het werken met WMI op lokale en externe computers. U hebt ook geleerd hoe u de CIM-cmdlets gebruikt om te werken met externe computers met het WSMan-of DCOM-protocol.

## <a name="review"></a>Beoordelen

1. Wat is het verschil in de WMI-en CIM-cmdlets?
1. Welk protocol `Get-CimInstance` gebruikt de cmdlet standaard?
1. Wat zijn de voor delen van het gebruik van een CIM-sessie in plaats van een computer naam op te geven `Get-CimInstance` ?
1. Hoe kunt u een ander ander protocol dan de standaard instelling opgeven voor gebruik met `Get-CimInstance` ?
1. Hoe sluit of verwijdert u CIM-sessies?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [CimCmdlets-module][]
- [Video: CIM-cmdlets en CIM-sessies gebruiken][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets-module]: /powershell/module/cimcmdlets/
[Video: CIM-cmdlets en CIM-sessies gebruiken]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Power shell-functie voor het maken van CimSessions op externe computers met terugval naar DCOM]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
