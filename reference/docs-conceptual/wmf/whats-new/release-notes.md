---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Opmerkingen bij de WMF 5.x-release
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "79406844"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Opmerkingen bij de release van Windows Management Framework (WMF) 5. x

## <a name="wmf-50-changes"></a>WMF 5,0-wijzigingen

- Power shell 5,0 voegt een nieuwe gestructureerde **informatie** stroom toe
- Verbeteringen in DSC, met inbegrip van vier nieuwe DSC-resources:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Er is net genoeg beheer toegevoegd om op rollen gebaseerd beheer via externe communicatie van Power shell in te scha kelen
- Power shell 5,0 breidt de taal uit voor het toevoegen van door de gebruiker gedefinieerde klassen en inventarisaties
- Verbeterde functies voor fout opsporing in Power shell ISE en het toevoegen van externe fout opsporing
- De modules PowerShellGet en Package Management zijn toegevoegd
- Verbeterde logboek registratie en transcripten van Power shell-scripts
- Syntaxis-cmdlets voor cryptografische berichten toevoegen
- WMF 5,0 bevat de NetworkSwitchManager-module voor Windows
- De module micro soft. Power shell. ODataUtils is toegevoegd
- Er is ondersteuning toegevoegd voor logboek registratie van software-inventaris (SIL)
- Nieuwe of update-cmdlets in reactie op gebruikers aanvragen en problemen

## <a name="wmf-51-changes"></a>WMF 5,1-wijzigingen

WMF 5,1 bevat de onderdelen van Power shell, WMI, WinRM en Software Inventory logging (SIL) die zijn uitgebracht met Windows Server 2016. WMF 5,1 kan worden geïnstalleerd op Windows 7, Windows 8,1, Windows Server 2008 R2, 2012 en 2012 R2, en biedt verschillende verbeteringen ten opzichte van WMF-5,0, waaronder:

- Nieuwe cmdLets
- PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules
- Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten
- Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen
- Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets
- Antwoorden op een aantal gebruikersaanvragen en -problemen

> [!IMPORTANT]
> Voordat u WMF 5,1 installeert op Windows Server 2008 of Windows 7, controleert u of WMF 3,0 niet is geïnstalleerd. Zie voor meer informatie [WMF 5,1-vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>PowerShell-edities

Vanaf versie 5,1 is Power shell beschikbaar in verschillende edities waarin verschillende functie sets en platform compatibiliteit worden aangegeven.

- **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
- **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Meer informatie over het gebruik van Power shell-edities

- [De actieve editie van Power shell bepalen met behulp van $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Get-module resultaten filteren op CompatiblePSEditions met behulp van de PSEdition-para meter](/powershell/module/microsoft.powershell.core/get-module)
- [Uitvoering van scripts voor komen tenzij uitgevoerd op een compatibele editie van Power shell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [De compatibiliteit van een module met specifieke Power shell-versies declareren](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Module analyse cache

Vanaf WMF 5,1 biedt Power shell controle over het bestand dat wordt gebruikt voor het opslaan van gegevens over een module, zoals de opdrachten die worden geëxporteerd.

Deze cache wordt standaard opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. De cache wordt doorgaans tijdens het opstarten gelezen tijdens het zoeken naar een opdracht en wordt ergens op een achtergrond thread geschreven nadat een module is geïmporteerd.

Als u de standaard locatie van de cache wilt wijzigen, `$env:PSModuleAnalysisCachePath` stelt u de omgevings variabele in voordat u Power shell start. Wijzigingen aan deze omgevings variabele worden alleen toegepast op onderliggende processen. De waarde moet een volledig pad (inclusief bestands naam) zijn dat Power shell toestemming heeft om bestanden te maken en te schrijven. Als u de bestands cache wilt uitschakelen, stelt u deze waarde in op een ongeldige locatie, bijvoorbeeld:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermee stelt u het pad naar een ongeldig apparaat in. Als Power shell het pad niet kan schrijven, wordt er geen fout geretourneerd, maar u kunt fout rapportage zien met behulp van een tracering:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Wanneer u de cache afschrijft, controleert Power shell op modules die niet meer bestaan om een onnodig grote cache te voor komen. Soms zijn deze controles niet gewenst, in welk geval u ze kunt uitschakelen door het volgende in te stellen:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Het instellen van deze omgevings variabele wordt direct van kracht in het huidige proces.

## <a name="specifying-module-version"></a>Module versie opgeven

In WMF 5,1 `using module` gedraagt zich op dezelfde manier als andere module constructies in Power shell.
U had eerder geen manier om een bepaalde module versie op te geven. Als er meerdere versies aanwezig zijn, resulteert dit in een fout.

In WMF 5,1:

- U kunt de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)gebruiken.

  Deze hash-tabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName`.

  **Voor beeld:**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Als er meerdere versies van de module zijn, maakt Power shell gebruik van **dezelfde oplossings logica** als `Import-Module` en wordt er geen fout geretourneerd-- `Import-Module` hetzelfde `Import-DscResource`gedrag als en.

## <a name="improvements-to-pester"></a>Verbeteringen aan de ziekte

In WMF 5,1 is de versie van de ziekte die wordt geleverd met Power shell, bijgewerkt van 3.3.5 naar 3.4.0.
Deze update zorgt voor een betere werking van een ziekte op nano server.

U kunt de wijzigingen in parasiet controleren door de [wijzigingen logboek](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in de GitHub-opslag plaats te controleren.
