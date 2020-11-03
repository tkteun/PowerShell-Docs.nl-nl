---
description: Hierin worden nieuwe functies beschreven die zijn opgenomen in Windows Power shell 5,1.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253156"
---
# <a name="about_windows_powershell_51"></a>about_Windows_PowerShell_5.1

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden nieuwe functies beschreven die zijn opgenomen in Windows Power shell 5,1.

## <a name="long-description"></a>LANGE BESCHRIJVING

Windows Power shell 5,1 bevat belang rijke nieuwe functies die het gebruik ervan uitbreiden, de bruikbaarheid verbeteren en u in staat stellen om op Windows gebaseerde omgevingen eenvoudiger en uitgebreid te beheren.

Windows Power shell 5,1 is achterwaarts compatibel. Cmdlets, providers, modules, invoeg toepassingen, scripts, functies en profielen die zijn ontworpen voor Windows Power Shell 4,0, Windows Power Shell 3,0 en Windows Power Shell 2,0, werken doorgaans in Windows Power shell 5,1 zonder wijzigingen.

- Nieuwe cmdlets: lokale gebruikers en groepen; Get-ComputerInfo
- PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules
- Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten
- Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen
- Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets
- Antwoorden op een aantal gebruikersaanvragen en -problemen

Windows Power shell 5,1 wordt standaard geïnstalleerd op Windows Server 2016 en Windows 10. Zie [WMF-5,1 installeren en configureren](/powershell/scripting/wmf/setup/install-configure)als u Windows power shell 5,1 wilt installeren op windows server 2012 R2, Windows 8,1 ENTER prise of Windows 8,1 Pro.
Lees de Download gegevens en zorg ervoor dat aan alle systeem vereisten wordt voldaan voordat u Windows Management Framework 5,1 installeert.

U kunt ook lezen over wijzigingen in Windows Power shell 5,1 in [Wat is er nieuw in Windows Power shell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).

## <a name="new-scenarios-and-features-in-wmf-51"></a>Nieuwe Scenario's en functies in WMF 5,1

> Opmerking: deze informatie is voorlopig en kan worden gewijzigd.

### <a name="powershell-editions"></a>PowerShell-edities
Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
- **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

**Meer informatie over het gebruik van Power shell-edities**

- [De actieve editie van Power shell bepalen met behulp van $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Get-Module resultaten filteren op CompatiblePSEditions met behulp van de PSEdition-para meter](/powershell/module/microsoft.powershell.core/get-module)
- [Uitvoering van scripts voor komen tenzij uitgevoerd op een compatibele editie van Power shell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [De compatibiliteit van een module met specifieke Power shell-versies declareren](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a>Catalogus-cmdlets

Er zijn twee nieuwe cmdlets toegevoegd in de module [micro soft. Power shell. Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) . Deze genereren en valideren Windows-catalogus bestanden.

#### <a name="new-filecatalog"></a>New-FileCatalog

New-FileCatalog maakt een Windows-catalogus bestand voor een set mappen en bestanden.
Dit catalogus bestand bevat hashes voor alle bestanden in opgegeven paden. Gebruikers kunnen de set mappen distribueren samen met het bijbehorende catalogus bestand dat deze mappen vertegenwoordigt. Deze informatie is nuttig om te controleren of er wijzigingen zijn aangebracht in de mappen sinds de aanmaak tijd van de catalogus.

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Catalogus versies 1 en 2 worden ondersteund. Versie 1 maakt gebruik van het SHA1-hash-algoritme om bestands-hashes te maken. versie 2 maakt gebruik van SHA256. Catalogus versie 2 wordt niet ondersteund in *Windows Server 2008 R2* of *Windows 7*. U moet Catalog versie 2 gebruiken voor *Windows 8* , *Windows Server 2012* en latere besturings systemen.

Als u de integriteit van het catalogus bestand (Pester.cat in het bovenstaande voor beeld) wilt controleren, moet u dit ondertekenen met de cmdlet [set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) .

#### <a name="test-filecatalog"></a>Test-FileCatalog

Test-FileCatalog valideert de catalogus die een set mappen vertegenwoordigt.

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

Met deze cmdlet worden alle bestanden-hashes en hun relatieve paden gevonden die in de *catalogus* met die op *schijf* zijn aangetroffen. Als wordt gedetecteerd dat de bestands-hashes en de paden niet overeenkomen, wordt de status als *ValidationFailed* geretourneerd. Gebruikers kunnen al deze gegevens ophalen met behulp van de *-gedetailleerde* para meter. Ook wordt de status van de ondertekening weer gegeven in de *handtekening* eigenschap, die gelijk is aan het aanroepen van de cmdlet [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) in het catalogus bestand. Gebruikers kunnen ook bestanden overs Laan tijdens de validatie met behulp van de para meter *-FilesToSkip* .

### <a name="module-analysis-cache"></a>Module analyse cache

Vanaf WMF 5,1 biedt Power shell controle over het bestand dat wordt gebruikt voor het opslaan van gegevens over een module, zoals de opdrachten die worden geëxporteerd.

Deze cache wordt standaard opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` . De cache wordt doorgaans tijdens het opstarten gelezen tijdens het zoeken naar een opdracht en wordt ergens op een achtergrond thread geschreven nadat een module is geïmporteerd.

Als u de standaard locatie van de cache wilt wijzigen, stelt u de `$env:PSModuleAnalysisCachePath` omgevings variabele in voordat u Power shell start. Wijzigingen aan deze omgevings variabele worden alleen toegepast op onderliggende processen. De waarde moet een volledig pad (inclusief bestands naam) zijn dat Power shell toestemming heeft om bestanden te maken en te schrijven. Als u de bestands cache wilt uitschakelen, stelt u deze waarde in op een ongeldige locatie, bijvoorbeeld:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermee stelt u het pad naar een ongeldig apparaat in. Als Power shell het pad niet kan schrijven, wordt er geen fout geretourneerd, maar u kunt fout rapportage zien met behulp van een tracering:

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

Wanneer u de cache afschrijft, controleert Power shell op modules die niet meer bestaan om een onnodig grote cache te voor komen. Soms zijn deze controles niet gewenst, in welk geval u ze kunt uitschakelen door het volgende in te stellen:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Het instellen van deze omgevings variabele wordt direct van kracht in het huidige proces.

### <a name="specifying-module-version"></a>Module versie opgeven

In WMF 5,1 `using module` gedraagt zich op dezelfde manier als andere module constructies in Power shell. U had eerder geen manier om een bepaalde module versie op te geven. Als er meerdere versies aanwezig zijn, resulteert dit in een fout.

In WMF 5,1:

* U kunt de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor)gebruiken.
  Deze hash-tabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName` .

  **Voor beeld:**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Als er meerdere versies van de module zijn, maakt Power shell gebruik van **dezelfde oplossings logica** als `Import-Module` en wordt er geen fout geretourneerd--hetzelfde gedrag als `Import-Module` en `Import-DscResource` .

### <a name="improvements-to-pester"></a>Verbeteringen aan de ziekte

In WMF 5,1 is de versie van de ziekte die wordt geleverd met Power shell, bijgewerkt van 3.3.5 naar 3.4.0, met toevoeging van GitHub [PR # 484](https://github.com/pester/Pester/pull/484), waardoor het gedrag van de ziekte op nano server beter is.

U kunt de wijzigingen in versies 3.3.5 in 3.4.0 controleren door het ChangeLog.md-bestand te controleren op: https://github.com/pester/Pester/blob/master/CHANGELOG.md

## <a name="keywords"></a>WOORD

Wat is er nieuw in Windows Power shell 5,1
