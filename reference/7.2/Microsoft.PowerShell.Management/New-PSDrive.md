---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 54b65a636fe05ed82d4f022b5bb8cbf8acaf7bab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705476"
---
# New-PSDrive

## SAMENVATTING
Hiermee worden tijdelijke en permanente toegewezen netwerk stations gemaakt.

## SYNTAXIS

### Alles

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `New-PSDrive` cmdlet maakt tijdelijke en permanente stations die zijn toegewezen aan of gekoppeld aan een locatie in een gegevens archief, zoals een netwerk station, een map op de lokale computer of een register sleutel, en permanente Windows-toegewezen netwerk stations die zijn gekoppeld aan een bestandssysteem locatie op een externe computer.

Tijdelijke schijven bestaan alleen in de huidige Power shell-sessie en in sessies die u in de huidige sessie maakt. Ze kunnen een wille keurige naam hebben die geldig is in Power shell en kan worden toegewezen aan een lokale of externe bron. U kunt tijdelijke Power Shell-stations gebruiken om toegang te krijgen tot gegevens in het bijbehorende gegevens archief, net zoals u dat zou doen met een toegewezen netwerk station. U kunt locaties wijzigen in het station, met behulp `Set-Location` van en toegang tot de inhoud van het station met behulp van `Get-Item` of `Get-ChildItem` .

Omdat tijdelijke stations alleen bekend zijn bij Power shell, hebt u geen toegang tot de schijven met behulp van bestanden Verkenner, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework of met hulpprogram ma's zoals **net use**.

De volgende functies zijn toegevoegd aan `New-PSDrive` in Power shell 3,0:

- Toegewezen netwerk stations. U kunt de para meter **persistent** van gebruiken `New-PSDrive` om toegewezen Windows-netwerk stations te maken. In tegens telling tot tijdelijke Power Shell-stations zijn Windows toegewezen netwerk stations niet specifiek voor een bepaalde sessie. Ze worden opgeslagen in Windows en kunnen worden beheerd met behulp van standaard Windows-hulpprogram ma's, zoals bestanden Verkenner en **net-gebruik**. Toegewezen netwerk stations moeten een stationsletter naam hebben en moeten zijn verbonden met een locatie op een extern bestands systeem. Als uw opdracht lokaal is, zonder punt, blijft de para meter **persistent** het maken van een **PSDrive** buiten het bereik waarin de opdracht wordt uitgevoerd, niet behouden. Als u `New-PSDrive` in een script werkt en u wilt dat het station voor onbepaalde tijd blijft bestaan, moet u het script naar een punt schrijven. Voor de beste resultaten kunt u een nieuw station geforceerd voor onbepaalde tijd blijven toevoegen door de para meter **bereik** toe te voegen aan uw opdracht en de waarde ervan in te stellen op **Global**. Zie [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)voor meer informatie over dot-sourcing.
- Externe stations. Wanneer een extern station is verbonden met de computer, voegt Power shell automatisch een **PSDrive** toe aan het bestands systeem dat het nieuwe station vertegenwoordigt. U hoeft Power shell niet opnieuw te starten. Op dezelfde manier verwijdert Power shell automatisch de **PSDrive** die de verwijderde schijf vertegenwoordigt wanneer een extern station wordt losgekoppeld van de computer.
- Referenties voor UNC-paden (Universal Naming Convention).

Wanneer de waarde van de **hoofd** parameter een UNC-pad is, zoals `\\Server\Share` , wordt de referentie die is opgegeven in de waarde van de para meter **Credential** , gebruikt om de **PSDrive** te maken. Anders is de **referentie** niet effectief wanneer u nieuwe stations voor het bestands systeem maakt.

Sommige code voorbeelden gebruiken splatting om de lengte van de lijn te verkleinen en de Lees baarheid te verbeteren. Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een tijdelijk station maken dat is toegewezen aan een netwerk share

In dit voor beeld maakt u een tijdelijk Power Shell-station dat is toegewezen aan een netwerk share.

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

`New-PSDrive` maakt gebruik van de para meter **name** om een Power Shell-station met `Public` de naam en de para meter **PSProvider** op te geven voor de Power shell- `FileSystem` provider. Met de para meter **root** wordt het UNC-pad van de netwerk share opgegeven.

De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path Public:`

### Voor beeld 2: een tijdelijk station maken dat is toegewezen aan een lokale map

In dit voor beeld wordt een tijdelijk Power Shell-station gemaakt dat toegang biedt tot een map op de lokale computer.

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

Splatting maakt de parameter sleutels en-waarden. De para meter **name** specificeert de naam van het station, **MyDocs**. De **PSProvider** para meter geeft u de Power shell- `FileSystem` provider op. **Root** Hiermee geeft u de map van de lokale computer. De **beschrijvings** parameter beschrijft het doel van het station. `New-PSDrive` maakt gebruik van de splatted-para meters om het station te maken `MyDocs` .

De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path MyDocs:`

### Voor beeld 3: een tijdelijke schijf maken voor een register sleutel

In dit voor beeld wordt een tijdelijk Power Shell-station gemaakt dat toegang biedt tot een register sleutel. Er wordt een station gemaakt met de naam mijn bedrijf die is toegewezen aan de `HKLM:\Software\MyCompany` register sleutel.

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

`New-PSDrive` maakt gebruik van de para meter **name** om een Power Shell-station met `MyCompany` de naam en de para meter **PSProvider** op te geven voor de Power shell- `Registry` provider. Met de para meter **root** wordt de register locatie opgegeven.

De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path MyCompany:`

### Voor beeld 4: een permanent toegewezen netwerk station maken met behulp van referenties

In dit voor beeld wordt een netwerk station toegewezen dat is geverifieerd met de referenties van een domein service account.
Zie de beschrijving van de **referentie** parameter voor meer informatie over het **PSCredential** -object waarin referenties worden opgeslagen en hoe wacht woorden worden opgeslagen als **SecureString**.

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> Houd er rekening mee dat als u het bovenstaande fragment in een script gebruikt, de waarde voor de **bereik** parameter instelt op ' globaal ' om ervoor te zorgen dat het station zich buiten het huidige bereik bevindt.

De `$cred` variabele bevat een **PSCredential** -object met de referenties van het service account. `Get-Credential` Hiermee wordt u gevraagd het wacht woord in te voeren dat is opgeslagen in een **SecureString**.

`New-PSDrive` Hiermee maakt u het toegewezen netwerk station met behulp van verschillende para meters. **Naam** Hiermee geeft u de stationsletter op `S` die door Windows wordt geaccepteerd. en **root** definieert `\\Server01\Scripts` als de locatie op een externe computer. Met **persistent** maakt u een Windows-toegewezen netwerk station dat is opgeslagen op de lokale computer. **PSProvider** Hiermee geeft u de `FileSystem` provider op. **Referentie** gebruikt de `$cred` variabele om de referenties van het service account voor verificatie op te halen.

Het toegewezen station kan worden weer gegeven op de lokale computer in Power shell-sessies, bestanden Verkenner en met hulpprogram ma's zoals **net use**. De inhoud van een Power shell-sessie weer geven: `Get-ChildItem -Path S:`

### Voor beeld 5: permanente en tijdelijke stations maken

In dit voor beeld ziet u het verschil tussen een permanent toegewezen netwerk station en een tijdelijk Power Shell-station dat is toegewezen aan dezelfde netwerk share.

Als u de Power shell-sessie sluit en vervolgens een nieuwe sessie opent, is de tijdelijke `PSDrive:` schijf niet beschikbaar, maar is het permanente `X:` station beschikbaar. Wanneer u bepaalt welke methode u moet gebruiken voor het toewijzen van netwerk stations, kunt u overwegen hoe u het station gebruikt. Bijvoorbeeld of het permanent moet blijven en of het station zichtbaar moet zijn voor andere Windows-onderdelen.

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## PARAMETERS

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Sinds Power Shell 3,0, wanneer de waarde van de **hoofd** parameter een UNC-pad is, kunt u referenties gebruiken om bestandssysteem stations te maken.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Beschrijving

Hiermee geeft u een korte beschrijving van het station. Typ een wille keurige teken reeks.

Als u de beschrijvingen van alle stations van de sessie wilt zien, gaat u naar `Get-PSDrive | Format-Table Name, Description` .

Als u de beschrijving van een bepaald station wilt weer geven, typt u `(Get-PSDrive <DriveName>).Description` .

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

### -Name

Hiermee geeft u een naam op voor het nieuwe station. Voor permanente toegewezen netwerk stations gebruikt u een stationsletter. Voor tijdelijke Power Shell-stations bent u niet beperkt tot stationsletters. gebruik een geldige teken reeks.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Persistent

Geeft aan dat met deze cmdlet een Windows-toegewezen netwerk station wordt gemaakt. De para meter **persistent** is alleen beschikbaar in Windows.

Toegewezen netwerk stations worden opgeslagen in Windows op de lokale computer. Ze zijn permanent, niet voor sessie-specifiek en kunnen worden weer gegeven en beheerd in Verkenner en andere hulpprogram ma's.

Wanneer u de opdracht lokaal en zonder punt-sourcing bereikt, blijft de para meter **persistent** het maken van een **PSDrive** buiten het bereik waarin u de opdracht uitvoert niet behouden. Als u `New-PSDrive` in een script uitvoert en u wilt dat het nieuwe station voor onbepaalde tijd blijft bestaan, moet u het script op de gewenste punt zetten. Als u de beste resultaten wilt afdwingen, geeft u **globaal** op als de waarde van de **bereik** parameter en neemt u **persistent** op in de opdracht.

De naam van het station moet een letter zijn, zoals `D` of `E` . De waarde van de **hoofd** parameter moet een UNC-pad van een andere computer zijn. De waarde van de para meter **PSProvider** moet zijn `FileSystem` .

Gebruik de cmdlet om een Windows-toegewezen netwerk station te verbreken `Remove-PSDrive` . Wanneer u een Windows-toegewezen netwerk station verbreekt, wordt de toewijzing permanent verwijderd van de computer, niet alleen verwijderd uit de huidige sessie.

Toegewezen netwerk stations zijn specifiek voor een gebruikers account. Toegewezen stations die zijn gemaakt in verhoogde sessies of sessies met de referenties van een andere gebruiker zijn niet zichtbaar in sessies die zijn gestart met andere referenties.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Hiermee geeft u de Power shell-provider op die ondersteuning biedt voor stations van dit type.

Als het station bijvoorbeeld is gekoppeld aan een netwerk share of een map van het bestands systeem, is de Power shell-provider `FileSystem` . Als het station is gekoppeld aan een register sleutel, is de provider `Registry` .

Tijdelijke Power Shell-stations kunnen worden gekoppeld aan elke Power shell-provider. Toegewezen netwerk stations kunnen alleen worden gekoppeld met de `FileSystem` provider.

Als u een lijst met providers in uw Power shell-sessie wilt zien, gebruikt u de `Get-PSProvider` cmdlet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Root

Hiermee geeft u de locatie van het gegevens archief waaraan een Power Shell-station is toegewezen.

Geef bijvoorbeeld een netwerk share op, zoals `\\Server01\Public` een lokale map, zoals `C:\Program Files` of een register sleutel, zoals `HKLM:\Software\Microsoft` .

Tijdelijke Power Shell-stations kunnen worden gekoppeld aan een lokale of externe locatie op elk ondersteund provider-station. Toegewezen netwerk stations kunnen alleen worden gekoppeld aan een bestandssysteem locatie op een externe computer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u een bereik voor het station. De acceptabele waarden voor deze para meter zijn: **Global**, **Local** en **script**, of een getal dat relatief is ten opzichte van het huidige bereik. Bereiken nummer 0 tot het aantal bereiken. Het huidige bereik nummer is 0 en de bovenliggende waarde is 1. Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen pijplijn invoer voor deze cmdlet.

## UITVOER

### System.Management.Automation.PSDriveInfo

## OPMERKINGEN

`New-PSDrive` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Gebruik om een lijst weer te geven van de providers die beschikbaar zijn in uw sessie `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie over providers.

Toegewezen netwerk stations zijn specifiek voor een gebruikers account. Toegewezen stations die zijn gemaakt in verhoogde sessies of sessies met de referenties van een andere gebruiker zijn niet zichtbaar in sessies die zijn gestart met andere referenties.

## GERELATEERDE KOPPELINGEN

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PSDrive](Get-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

