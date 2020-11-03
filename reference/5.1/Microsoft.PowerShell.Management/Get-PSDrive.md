---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: 7a37857d9a4fb9eb18869ef78dc0ac19dc26367f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250794"
---
# Get-PSDrive

## SAMENVATTING
Hiermee worden de stations in de huidige sessie opgehaald.

## SYNTAXIS

### Naam (standaard)

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

### Letterlijke waarde

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

## BESCHRIJVING

De- `Get-PSDrive` cmdlet haalt de stations in de huidige sessie op. U kunt een bepaald station of alle stations in de sessie ophalen.

Met deze cmdlet worden de volgende typen stations opgehaald:

- Logische Windows-stations op de computer, inclusief stations die zijn toegewezen aan netwerk shares.
- Schijven die beschikbaar worden gesteld door Power shell-providers (zoals het certificaat:, de functie: en alias: stations) en de HKLM: en HKCU: stations die worden weer gegeven door de Windows Power shell-register provider.
- Door de sessie opgegeven tijdelijke stations en permanente toegewezen netwerk stations die u maakt met behulp van de cmdlet New-PSDrive.

Vanaf Windows Power Shell 3,0 kan de **persistente** para meter van de `New-PSDrive` cmdlet toegewezen netwerk stations maken die op de lokale computer zijn opgeslagen en in andere sessies beschikbaar zijn. Zie New-PSDrive voor meer informatie.

Vanuit Windows Power Shell 3,0, wanneer een extern station is verbonden met de computer, wordt in Windows Power shell automatisch een PSDrive toegevoegd aan het bestands systeem dat het nieuwe station vertegenwoordigt.
U hoeft Windows Power shell niet opnieuw op te starten. Op dezelfde manier verwijdert Windows Power shell automatisch de PSDrive die de verwijderde schijf vertegenwoordigt wanneer een extern station wordt losgekoppeld van de computer.

## VOORBEELDEN

### Voor beeld 1: stations in de huidige sessie ophalen

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

Met deze opdracht worden de stations in de huidige sessie opgehaald.

In de uitvoer ziet u de harde schijf (C:), het CD-ROM-station (D:) en de stations die worden weer gegeven door de Windows Power shell-providers (alias:, CERT:, env:, function:, HKCU:, HKLM: en variable:).

### Voor beeld 2: een station op de computer ophalen

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

Met deze opdracht wordt het station D: op de computer opgehaald. Houd er rekening mee dat de stationsletter in de opdracht niet wordt gevolgd door een dubbele punt.

### Voor beeld 3: alle stations ophalen die worden ondersteund door de Windows Power shell File System-Provider

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

Met deze opdracht worden alle stations opgehaald die worden ondersteund door de Windows Power shell-bestandssysteem provider. Dit omvat vaste stations, logische partities, toegewezen netwerk stations en tijdelijke stations die u maakt met behulp van de New-PSDrive-cmdlet.

### Voor beeld 4: controleren of een station wordt gebruikt als een Windows Power shell-stationsnaam

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

Met deze opdracht wordt gecontroleerd of het X-station al in gebruik is als de naam van een Windows Power Shell-station.
Als dat niet het geval is, gebruikt de opdracht de `New-PSDrive` cmdlet om een tijdelijke schijf te maken die is toegewezen aan de register sleutel HKLM: \ software.

### Voor beeld 5: de typen bestanden vergelijken systeem stations

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

In dit voor beeld worden de typen bestandssysteem stations vergeleken die worden weer gegeven met `Get-PSDrive` behulp van andere methoden. In dit voor beeld ziet u verschillende manieren om stations weer te geven in Windows Power shell en ziet u dat sessie-specifieke stations die zijn gemaakt met behulp van de New-PSDrive cmdlet alleen toegankelijk zijn in Windows Power shell.

De eerste opdracht wordt gebruikt `Get-PSDrive` om alle bestandssysteem stations in de sessie op te halen. Dit omvat de vaste stations (C: en D:), een toegewezen netwerk station (G:) dat is gemaakt met behulp van de **persistente** para meter van `New-PSDrive` en een Power Shell-station (T:) die is gemaakt met `New-PSDrive` zonder de para meter **persistent** .

Met de opdracht **net use** worden Windows toegewezen netwerk stations weer gegeven, in dit geval alleen het station G. De X:-station dat is gemaakt door, wordt niet weer gegeven `New-PSDrive` . U ziet dat het station G: ook is toegewezen aan \\ \\ Muziek- \\ GratefulDead.

De derde opdracht maakt gebruik van de methode **GetDrives** van de klasse Microsoft .NET Framework **System. io. DriveInfo** . Met deze opdracht worden de stations van het Windows-Bestands systeem met inbegrip van station G: opgehaald, maar worden de stations die worden gemaakt door niet opgehaald `New-PSDrive` .

De vierde opdracht gebruikt de `Get-CimInstance` cmdlet om de exemplaren van de klasse **Win32_LogicalDisk** op te halen. Het retourneert de stations A:, C:, D:, E: en G:, maar niet de stations die zijn gemaakt door `New-PSDrive` .

De laatste opdracht gebruikt de `Get-CimInstance` cmdlet om de instanties van de **Win32_NetworkConnection** -klasse weer te geven. Net zoals **net use** retourneert het alleen het permanente G: station dat is gemaakt door `New-PSDrive` .

## PARAMETERS

### -Literal-waarde

Hiermee geeft u de naam van het station.

De waarde van **literal** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als de naam escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u als een teken reeks matrix de naam of de naam van de stations die met deze cmdlet worden opgehaald in de bewerking.
Typ de naam van het station of de letter zonder een dubbele punt (:).

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Hiermee wordt de Windows Power shell-provider opgegeven als een teken reeks matrix. Met deze cmdlet worden alleen de stations opgehaald die door deze provider worden ondersteund. Typ de naam van een provider, zoals File System, Registry of Certificate.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het bereik op waarin met deze cmdlet de stations worden opgehaald.

De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope). ' Local ' is de standaard instelling.

Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie. Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd. Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### System.Management.Automation.PSDriveInfo

Deze cmdlet retourneert objecten die de stations in de sessie vertegenwoordigen.

## OPMERKINGEN

* Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Gebruik de cmdlet om de providers weer te geven die beschikbaar zijn in uw sessie `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.
* Toegewezen netwerk stations die worden gemaakt met behulp van de para meter **persistent** van de cmdlet New-PSDrive, zijn specifiek voor een gebruikers account. Toegewezen netwerk stations die u maakt in sessies die worden gestart met de optie als administrator uitvoeren of met de referenties van een andere gebruiker, zijn niet zichtbaar in sessies die worden gestart zonder expliciete referenties of met de referenties van de huidige gebruiker.

## GERELATEERDE KOPPELINGEN

[New-PSDrive](New-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

[Get-PSProvider](Get-PSProvider.md)
