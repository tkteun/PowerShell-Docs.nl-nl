---
description: Hierin wordt beschreven hoe Power shell-providers toegang bieden tot gegevens en onderdelen die anders niet eenvoudig toegankelijk zijn via de opdracht regel. De gegevens worden weer gegeven in een consistente indeling die lijkt op een bestandssysteem station.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: c0ae976c9f82a8a7481eda2bad136e7ba2689a44
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252092"
---
# <a name="about-providers"></a>Over providers

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe Power shell-providers toegang bieden tot gegevens en onderdelen die anders niet eenvoudig toegankelijk zijn via de opdracht regel.
De gegevens worden weer gegeven in een consistente indeling die lijkt op een bestandssysteem station.

## <a name="long-description"></a>Lange beschrijving

Power shell-providers zijn .NET-Program ma's die toegang bieden tot gespecialiseerde gegevens archieven, zodat ze eenvoudiger kunnen worden bekeken en beheerd. De gegevens worden weer gegeven in een station en u hebt toegang tot de gegevens in een pad zoals u zou doen op een harde schijf. U kunt een van de ingebouwde cmdlets gebruiken die door de provider worden ondersteund voor het beheren van de gegevens in het provider station. En u kunt aangepaste cmdlets gebruiken die speciaal zijn ontworpen voor de gegevens.

De providers kunnen ook dynamische para meters toevoegen aan de ingebouwde cmdlets. Deze para meters zijn alleen beschikbaar wanneer u de cmdlet met de provider gegevens gebruikt.

## <a name="built-in-providers"></a>Ingebouwde providers

Power shell bevat een set ingebouwde providers die u kunt gebruiken om toegang te krijgen tot de verschillende typen gegevens archieven.

| Provider   |   Station (s)  |Type                                                    |
|----------- |------------ |--------------------------------------------------------------|
|Alias       |Toe       |System. Management. Automation. AliasInfo                        |
|Certificaat |Certificaat        |Micro soft. Power shell. commands. X509StoreLocation               |
|            |             |System. Security. Cryptography. X509Certificates. X509Certificate2|
|Omgeving |Envelop         |System. Collections. Dictionary entry                            |
|Bestandssysteem  |C: (*)       |System. IO. file info                                            |
|            |             |System. IO. DirectoryInfo                                       |
|Functie    |Functieassembly    |System. Management. Automation. FunctionInfo                     |
|Register    |HKLM: HKCU:  |Microsoft. Win32. RegistryKey                                   |
|Variabele    |Variabeletype    |System. Management. Automation. PSVariable                       |
|WSMan       |WSMan       |Micro soft. WSMan. Management. WSManConfigContainerElement        |

(*) De stations van het bestands systeem variëren per systeem.

U kunt ook uw eigen Power shell-providers maken en u kunt providers installeren die anderen ontwikkelen. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u:

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a>Providers installeren en verwijderen

Providers worden doorgaans geïnstalleerd via Power shell-modules. Als u de module importeert, wordt de provider in uw sessie geladen. U kunt de ingebouwde providers niet verwijderen. U kunt de door andere modules geladen providers verwijderen.

U kunt een provider uit de huidige sessie verwijderen met de `Remove-Module` cmdlet. Met deze cmdlet wordt de provider niet verwijderd, maar wordt de provider niet beschikbaar in de sessie.

U kunt ook de `Remove-PSDrive` cmdlet gebruiken om een station uit de huidige sessie te verwijderen. Deze gegevens op het station worden niet beïnvloed, maar het station is niet meer beschikbaar in die sessie.

## <a name="viewing-providers"></a>Providers weer geven

Als u de Power shell-providers op uw computer wilt weer geven, typt u:

```powershell
Get-PSProvider
```

De uitvoer bevat een lijst met de ingebouwde providers en de providers die u hebt toegevoegd aan de sessie.

## <a name="the-provider-cmdlets"></a>De provider-cmdlets

De volgende cmdlets zijn ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. U kunt dezelfde cmdlets op dezelfde manier gebruiken voor het beheren van de verschillende typen gegevens die providers beschikbaar maken. Wanneer u de gegevens van een provider hebt beheerd, kunt u dezelfde procedures gebruiken met de gegevens van een provider.

Met de `New-Item` cmdlet maakt u bijvoorbeeld een nieuw item. In het `C:` station dat door de **File System** provider wordt ondersteund, kunt u gebruiken `New-Item` om een nieuw bestand of nieuwe map te maken. In de stations die worden ondersteund door de **register** provider, kunt u gebruiken `New-Item` om een nieuwe register sleutel te maken. In het `Alias:` station kunt u gebruiken `New-Item` om een nieuwe alias te maken.

Voor gedetailleerde informatie over een van de volgende cmdlets, typt u:

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a>Child item-cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a>Cmdlets voor inhoud

- [Add-content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Wissen-inhoud](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a>Cmdlets voor items

- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Kopie-item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Item verplaatsen](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Naam wijzigen-item](xref:Microsoft.PowerShell.Management.Rename-Item)
- [Set-item](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a>Item Property-cmdlets

- [Wissen-item Property](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Kopiëren-item Property](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [Get-item Property](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Verplaatsen-item Property](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [Nieuw-item Property](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [Verwijderen-item Property](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Naam wijzigen-item Property](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [Set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a>Locatie-cmdlets

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Pop-locatie](xref:Microsoft.PowerShell.Management.Pop-Location)
- [Push-locatie](xref:Microsoft.PowerShell.Management.Push-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a>Pad-cmdlets

- [Pad voor samen voegen](xref:Microsoft.PowerShell.Management.Join-Path)
- [Convert-pad](xref:Microsoft.PowerShell.Management.Convert-Path)
- [Split-pad](xref:Microsoft.PowerShell.Management.Split-Path)
- [Oplossen-pad](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [Test-pad](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a>PSDrive-cmdlets

- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [New-PSDrive](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [Remove-PSDrive](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a>PSProvider-cmdlets

- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a>Provider gegevens weer geven

Het belangrijkste voor deel van een provider is dat de gegevens op een vertrouwde en consistente manier beschikbaar worden gesteld. Het model voor gegevens presentatie is een bestandssysteem station.

Met de provider kunt u items in het gegevens archief weer geven, navigeren en wijzigen, alsof deze gegevens in een bestands systeem waren. Het gegevens archief wordt geopend met de naam van het station dat wordt ondersteund.

Het station wordt weer gegeven in de standaard weergave van de `Get-PSProvider` cmdlet, maar u kunt informatie over het provider station verkrijgen met de `Get-PSDrive` cmdlet. Als u bijvoorbeeld alle eigenschappen van de functie wilt ophalen: station, typt u:

```powershell
Get-PSDrive Function | Format-List *
```

U kunt de gegevens in een provider station bekijken en verplaatsen op dezelfde manier als op een bestandssysteem station.

Als u de inhoud van een provider station wilt weer geven, gebruikt u de Get-Item-of Get-ChildItem-cmdlets. Typ de naam van het station gevolgd door een dubbele punt (:). Als u bijvoorbeeld de inhoud van de alias wilt bekijken: station, typt u:

```powershell
Get-Item alias:
```

U kunt de gegevens in een wille keurig station weer geven en beheren vanaf een ander station door de naam van het station in het pad op te nemen. Als u bijvoorbeeld de register sleutel HKLM\Software in het HKLM: station van een ander station wilt weer geven, typt u:

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

Als u het station wilt openen, gebruikt u de cmdlet Set-Location. Onthoud de dubbele punt wanneer u het stationspad opgeeft. Als u bijvoorbeeld de locatie wilt wijzigen in de hoofdmap van het certificaat: station, typt u:

```powershell
Set-Location cert:
```

Om de inhoud van het certificaat te bekijken: station, typt u:

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a>Overstappen op hiërarchische gegevens

U kunt een provider station verplaatsen op dezelfde manier als een harde schijf.
Als de gegevens in een hiërarchie van items binnen items zijn gerangschikt, gebruikt u een back slash ( `\` ) om een onderliggend item aan te duiden. Gebruik de volgende indeling:

```
drive:\location\child-location\...
```

Als u bijvoorbeeld uw locatie wilt wijzigen in de register sleutel HKLM\Software, typt u een Set-Location opdracht, bijvoorbeeld:

```powershell
Set-Location HKLM:\SOFTWARE\
```

Als een element in de volledig gekwalificeerde naam spaties bevat, moet u de naam tussen dubbele aanhalings tekens ( `"` ) plaatsen. In het volgende voor beeld ziet u een volledig gekwalificeerd pad dat spaties bevat.

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

U kunt ook relatieve verwijzingen naar locaties gebruiken. Een punt ( `.` ) staat voor de huidige locatie. Als u bijvoorbeeld in de `HKLM:\Software\Microsoft` register sleutel bent en u de registersubsleutels in de sleutel wilt weer geven `HKLM:\Software\Microsoft\PowerShell` , typt u de volgende opdracht:

```powershell
Get-ChildItem .\PowerShell
```

Dubbele punten ( `..` ) verwijst ook naar de map of container direct boven uw huidige locatie. U kunt dubbele punten () gebruiken `..` om te navigeren door een provider hiërarchie.

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a>Start pagina van provider

Providers hebben ook een **thuis** locatie.  Deze locatie wordt gedeeld door `PSDrives` de provider. Het kan worden opgehaald door de **Start** -eigenschap van de provider weer te geven.

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

De **File System** provider is de enige provider met een standaard waarde voor **Home**. Dit is dezelfde waarde als `$Home` . Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.

U kunt de **basis** Directory voor een provider voor de huidige sessie instellen met behulp van de eigenschap.

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

Het `~` teken kan worden gebruikt om de basismap van de provider weer te geven.
Als er geen **thuis** locatie is ingesteld voor de provider, ziet u een fout melding.

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a>Dynamische para meters zoeken

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd aan een cmdlet door een provider. Deze para meters zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt met de provider die deze heeft toegevoegd.

Het `Cert:` station voegt bijvoorbeeld de para meter **CodeSigningCert** toe aan de `Get-Item` `Get-ChildItem` cmdlets en. U kunt deze para meter alleen gebruiken wanneer u `Get-Item` of `Get-ChildItem` in het `Cert:` station gebruikt.

Zie het Help-bestand voor de provider voor een lijst met de dynamische para meters die een provider ondersteunt. Type:

```
Get-Help <provider-name>
```

Bijvoorbeeld:

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a>Informatie over providers

Hoewel alle provider gegevens worden weer gegeven in stations en u dezelfde methoden gebruikt om ze te door lopen, wordt de overeenkomst daar gestopt. De gegevens archieven die de provider beschikbaar maakt, kunnen variëren als Active Directory locaties en post vakken van micro soft Exchange Server.

Voor informatie over afzonderlijke Power shell-providers typt u:

```
Get-Help <ProviderName>
```

Bijvoorbeeld:

```powershell
Get-Help registry
```

Voor een lijst met Help-onderwerpen over de providers, typt u:

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a>Zie ook

[about_Locations](about_Locations.md)

[about_Path_Syntax](about_Path_Syntax.md)
