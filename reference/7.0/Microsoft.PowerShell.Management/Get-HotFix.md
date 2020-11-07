---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 277dd2678b54c9e708d09f6ca27d82ab9afd4c1c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347615"
---
# Get-HotFix

## SAMENVATTING
Hiermee worden de hotfixes opgehaald die op lokale of externe computers zijn geïnstalleerd.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### Beschrijving

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## BESCHRIJVING

De `Get-Hotfix` cmdlet ontvangt hotfixes of updates die zijn geïnstalleerd op de lokale computer of opgegeven externe computers. De updates kunnen worden geïnstalleerd door Windows Update, Microsoft Update, Windows Server Update Services of hand matig geïnstalleerd.

## VOORBEELDEN

### Voor beeld 1: alle hotfixes op de lokale computer ophalen

De `Get-Hotfix` cmdlet haalt alle hotfixes op die op de lokale computer zijn geïnstalleerd.

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### Voor beeld 2: hotfixes ophalen van meerdere computers gefilterd op een teken reeks

De `Get-Hotfix` opdracht maakt gebruik van para meters voor het ophalen van hotfixes die op externe computers zijn geïnstalleerd. De resultaten worden gefilterd op een opgegeven beschrijvings teken reeks.

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

`Get-Hotfix` Hiermee wordt de uitvoer gefilterd met de para meter **Description** en de teken reeks **beveiliging** die het sterretje ( `*` )-Joker teken bevat. De para meter **ComputerName** bevat een door komma's gescheiden teken reeks met namen van externe computers. De **referentie** parameter geeft u een gebruikers account op dat is gemachtigd voor toegang tot de externe computers en om opdrachten uit te voeren.

### Voor beeld 3: controleren of een update is geïnstalleerd en computer namen naar een bestand schrijven

Met de opdrachten in dit voor beeld wordt gecontroleerd of een bepaalde update is geïnstalleerd. Als de update niet is geïnstalleerd, wordt de naam van de computer naar een tekst bestand geschreven.

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

De `$A` variabele bevat computer namen die zijn verkregen door `Get-Content` vanuit een tekst bestand. De objecten in `$A` worden naar beneden verzonden in de pijp lijn `ForEach-Object` . Een `if` instructie gebruikt de `Get-Hotfix` cmdlet met de **id-** para meter en een specifiek id-nummer voor elke computer naam. Als op een computer de opgegeven hotfix-id niet is geïnstalleerd, `Add-Content` schrijft de cmdlet de computer naam naar een bestand.

### Voor beeld 4: de meest recente hotfix ophalen op de lokale computer

In dit voor beeld wordt de meest recente hotfix opgehaald die op een computer is geïnstalleerd.

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-Hotfix` Hiermee worden de objecten van de pijp lijn naar de `Sort-Object` cmdlet verzonden. `Sort-Object` objecten worden gesorteerd op oplopende volg orde en de para meter **Property** wordt gebruikt om elke **InstalledOn** -datum te evalueren. De matrix notatie `[-1]` selecteert de meest recente geïnstalleerde hotfix.

## PARAMETERS

### -ComputerName

Hiermee geeft u een externe computer. Typ de NetBIOS-naam, een Internet Protocol (IP-adres) of een Fully Qualified Domain Name (FQDN) van een externe computer.

Wanneer de para meter **ComputerName** niet is opgegeven, `Get-Hotfix` wordt uitgevoerd op de lokale computer.

De para meter **ComputerName** is niet gebaseerd op externe communicatie met Windows Power shell. Als uw computer niet is geconfigureerd voor het uitvoeren van externe opdrachten, gebruikt u de para meter **ComputerName** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren. De standaard waarde is de huidige gebruiker

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

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
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beschrijving

`Get-HotFix` maakt gebruik van de **beschrijvings** parameter om typen hotfixes op te geven. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Id

Hiermee worden de `Get-HotFix` resultaten voor specifieke hotfix-id's gefilterd. Joker tekens worden niet geaccepteerd.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Tekenreeks

U kunt een of meer computer namen door geven om-HotFix op te halen.

## UITVOER

### System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering

`Get-HotFix` retourneert objecten die de hotfixes op de computer vertegenwoordigen.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

De **Win32_QuickFixEngineering** [WMI-klasse](/windows/desktop/WmiSdk/retrieving-a-class) Win32_QuickFixEngineering vertegenwoordigt een kleine update van het hele systeem, vaak een QFE-update (Quick-Fix Engineering) genoemd, toegepast op het huidige besturings systeem. Deze klasse retourneert alleen de updates die zijn geleverd door CBS (Component Based Servicing). Deze updates worden niet vermeld in het REGI ster. Updates die zijn geleverd door Microsoft Windows Installer (MSI) of de [Windows Update](https://update.microsoft.com) -site, worden niet door **Win32_QuickFixEngineering** geretourneerd. Zie [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)voor meer informatie.

De `Get-HotFix` uitvoer kan variëren op verschillende besturings systemen.

## GERELATEERDE KOPPELINGEN

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Add-content](Add-Content.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Win32_QuickFixEngineering klasse](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
