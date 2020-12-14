---
description: WSMan
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan Provider
ms.openlocfilehash: 32baaaec3589fc9d6f4c2319f47d56bca777f738
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706007"
---
# <a name="wsman-provider"></a>WSMan Provider

## <a name="provider-name"></a>Provider naam

WSMan

## <a name="drives"></a>Aandrijfeenheden

`WSMan:`

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot de configuratie gegevens van webservices voor beheer (WS-Management).

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de **WSMan** -provider voor Power shell kunt u WS-Management configuratie gegevens op lokale of externe computers toevoegen, wijzigen, wissen en verwijderen.

De **WSMan** -provider geeft een Power Shell-station met een mapstructuur die overeenkomt met een logische groepering van WS-Management configuratie-instellingen. Deze groeperingen worden containers genoemd.

Vanaf Windows Power Shell 3,0 is de **WSMan** -provider bijgewerkt ter ondersteuning van nieuwe eigenschappen voor sessie configuraties, zoals **OutputBufferingMode**. De sessie configuraties worden weer gegeven als items in de map voor de invoeg toepassing van het `WSMan:` station en de eigenschappen worden weer gegeven als items in elke sessie configuratie.

De **WSMan** -provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> U kunt opdrachten in het `WSMan:` station gebruiken om de waarden van de nieuwe eigenschappen te wijzigen. U kunt het `WSMan:` station in Power shell 2,0 echter niet gebruiken voor het wijzigen van eigenschappen die zijn geïntroduceerd in Windows Power shell 3,0.
> Hoewel er geen fout wordt gegenereerd, zijn de opdrachten niet effectief om deze instellingen te wijzigen. gebruik het **WSMan** -station in Windows power Shell 3,0.

### <a name="organization-of-the-wsman-drive"></a>Organisatie van het WSMan: station

- **Client**: u kunt verschillende aspecten van de WS-Management-client configureren. De configuratie-informatie wordt opgeslagen in het REGI ster.

- **Service**: u kunt verschillende aspecten van de WS-Management-service configureren.
  De configuratie-informatie wordt opgeslagen in het REGI ster.
  > [!NOTE]
  > Service configuratie wordt soms ook wel server configuratie genoemd.

- **Shell**: u kunt verschillende aspecten van de WS-Management shell configureren, zoals de instelling voor het toestaan van externe shell toegang (**AllowRemoteShellAccess**) en het maximum aantal gelijktijdige gebruikers toegestaan (**MaxConcurrentUsers**).

- **Listener**: u kunt een listener maken en configureren. Een listener is een beheer service waarmee het WS-Management-protocol wordt geïmplementeerd om berichten te verzenden en te ontvangen.

- **Invoeg toepassing**: invoeg toepassingen worden geladen en gebruikt door de WS-Management-service om verschillende functies te bieden. Power shell biedt standaard drie invoeg toepassingen:
  - De invoeg toepassing voor het door sturen van gebeurtenissen.
  - De invoeg toepassing micro soft. Power shell.
  - De invoeg toepassing van de Windows Management Instrumentation provider (WMI).
  Deze drie invoeg toepassingen ondersteunen gebeurtenis door sturen, configureren en WMI-toegang.

- **ClientCertificate**: u kunt een client certificaat maken en configureren.
  Er wordt een client certificaat gebruikt wanneer de WS-Management-client is geconfigureerd voor het gebruik van verificatie via een certificaat.

### <a name="directory-hierarchy-of-the-wsman-provider"></a>Directory-hiërarchie van de WSMan-provider

De Directory-hiërarchie van de WSMan-provider voor de lokale computer is als volgt.

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

De Directory-hiërarchie van de WSMan-provider voor een externe computer is hetzelfde als een lokale computer. Om toegang te krijgen tot de configuratie-instellingen van een externe computer, moet u echter verbinding maken met de externe computer via [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan). Zodra een verbinding met een externe computer tot stand is gebracht, wordt de naam van de externe computer weer gegeven in de provider.

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a>Navigeren door het WSMan: station

Met deze opdracht wordt de `Set-Location` cmdlet gebruikt om de huidige locatie te wijzigen in het `WSMan:` station.

```powershell
Set-Location WSMan:
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld.

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a>Navigeren naar een externe systeem archief locatie

Met deze opdracht wordt de `Set-Location` opdracht voor het wijzigen van de huidige locatie naar de hoofd locatie in de externe systeem opslag locatie. Gebruik een back slash `\` of slash `/` om een niveau van het station aan te geven `WSMan:` .

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> De bovenstaande opdracht gaat ervan uit dat er al een verbinding met het externe systeem bestaat.

## <a name="displaying-the-contents-of-the-wsman-drive"></a>De inhoud van het WSMan: station weer geven

Met deze opdracht wordt de `Get-Childitem` cmdlet gebruikt voor het weer geven van de WS-Management-archieven in de locatie van de localhost-opslag.

```powershell
Get-ChildItem -path WSMan:\Localhost
```

Als u zich in het station bevindt `WSMan:` , kunt u de naam van het station weglaten.

Met deze opdracht wordt de `Get-Childitem` cmdlet gebruikt om de WS-Management-archieven in de archief locatie ' SERVER01 ' van de externe computer weer te geven.

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> De bovenstaande opdracht gaat ervan uit dat er al een verbinding met het externe systeem bestaat.

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a>De waarde van items instellen in WSMAN: station

U kunt de `Set-Item` cmdlet gebruiken om de configuratie-instellingen in het station te wijzigen `WSMAN` . In het volgende voor beeld wordt de **TrustedHosts** -waarde ingesteld om alle hosts met het achtervoegsel ' contoso.com ' te accepteren.

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

De `Set-Item` cmdlet biedt ondersteuning voor een extra para meter `-Concatenate` waarmee een waarde wordt toegevoegd in plaats van deze te wijzigen. In het volgende voor beeld wordt een nieuwe waarde ' *. domain2.com ' toegevoegd aan de oude waarde die is opgeslagen in `TrustedHost:`

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a>Items maken in het WSMAN: station

### <a name="creating-a-new-listener"></a>Een nieuwe listener maken

Met de `New-Item` cmdlet worden items in een provider station gemaakt. Elke provider heeft verschillende item typen die u kunt maken. In het `WSMAN:` station kunt u *listeners* maken die u configureert om externe aanvragen te ontvangen en erop te reageren. Met de volgende opdracht maakt u een nieuwe HTTP-listener met behulp van de- `New-Item` cmdlet.

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a>Een nieuwe invoeg toepassing maken

Met deze opdracht wordt een invoeg toepassing voor de WS-Management-service gemaakt (geregistreerd).

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a>Nieuwe resource-invoer maken

Met deze opdracht maakt u een bron vermelding in de map resources van een TestPlugin. Bij deze opdracht wordt ervan uitgegaan dat er een TestPlugin is gemaakt met behulp van een afzonderlijke opdracht.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a>Een nieuwe beveiligings vermelding voor een resource maken

Met deze opdracht maakt u een beveiligings vermelding in de map Security van Resource_5967683 (een specifieke resource). Bij deze opdracht wordt ervan uitgegaan dat de bron vermelding is gemaakt met een afzonderlijke opdracht.

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a>Een nieuw client certificaat maken

Met deze opdracht maakt u een item voor **ClientCertificate** dat kan worden gebruikt door de WS-Management-client. De nieuwe **ClientCertificate** wordt weer gegeven in de map **ClientCertificate** als "ClientCertificate_1234567890". Alle para meters zijn verplicht. De **Uitgever** moet een vinger afdruk van het certificaat van de certificerings instantie zijn.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a>Een nieuwe initialisatie parameter maken

Met deze opdracht maakt u een initialisatie parameter met de naam ' testparametername ' in de map ' InitializationParameters '. Bij deze opdracht wordt ervan uitgegaan dat de ' TestPlugin ' is gemaakt met behulp van een afzonderlijke opdracht.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.

### <a name="address-string"></a>Help \<String\>

Hiermee geeft u het adres op waarvoor deze listener is gemaakt. De waarde kan één van de volgende zijn:

- De letterlijke teken reeks "*". (Met het Joker teken ( `*` ) wordt de opdracht alle IP-adressen op alle netwerk adapters gebonden.)
- De letterlijke teken reeks ' IP: ' gevolgd door een geldig IP-adres in IPv4-decimale notatie of in een IPv6-gekloonde hexadecimale indeling.
- De letterlijke teken reeks ' MAC: ' gevolgd door het MAC-adres van een adapter.
  Bijvoorbeeld: MAC: 32-a3-58 -90-CC.

> [!NOTE]
> De adres waarde wordt ingesteld bij het maken van een listener.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a>Voorzieningen \<Enumeration\>

Bij het werken met *invoeg toepassingen* geeft deze para meter een bewerking aan die wordt ondersteund voor deze URI (Uniform Resource Identifier). U moet één vermelding maken voor elk type bewerking dat door de URI wordt ondersteund. U kunt geldige kenmerken voor een bepaalde bewerking opgeven als de bewerking deze ondersteunt.

Deze kenmerken zijn onder andere **SupportsFiltering** en **SupportsFragment**.

- **Maken**: Create-bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment**  wordt gebruikt als de bewerking Create het concept ondersteunt.
  - Het kenmerk **SupportFiltering** is niet geldig voor Create-bewerkingen en moet worden ingesteld op ' false '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Verwijderen**: Verwijder bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt gebruikt als de bewerking delete het concept ondersteunt.
  - Het kenmerk **SupportFiltering** is niet geldig voor Delete-bewerkingen en moet worden ingesteld op ' false '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Opsommen**: opsommings bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt niet ondersteund voor opsommings bewerkingen en moet worden ingesteld op false.
  - Het kenmerk **SupportFiltering** is geldig en als de invoeg toepassing filteren ondersteunt, moet dit kenmerk worden ingesteld op ' True '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Get**: Get-bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt gebruikt als de Get-bewerking het concept ondersteunt.
  - Het kenmerk **SupportFiltering** is niet geldig voor Get-bewerkingen en moet worden ingesteld op false.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Invoke**: bewerkingen aanroepen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt niet ondersteund voor invoke-bewerkingen en moet worden ingesteld op false.
  - Het kenmerk **SupportFiltering** is ongeldig en moet worden ingesteld op ' false '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Put**: put-bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt gebruikt als de put-bewerking het concept ondersteunt.
  - Het kenmerk **SupportFiltering** is niet geldig voor put-bewerkingen en moet worden ingesteld op ' false '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Abonneren**: Abonneer bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt niet ondersteund voor Abonneer bewerkingen en moet worden ingesteld op false.
  - Het kenmerk **SupportFiltering** is niet geldig voor abonnements bewerkingen en moet worden ingesteld op ' false '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.
- **Shell**: shell-bewerkingen worden ondersteund op de URI.
  - Het kenmerk **SupportFragment** wordt niet ondersteund voor shell-bewerkingen en moet worden ingesteld op ' false '.
  - Het kenmerk **SupportFiltering** is niet geldig voor shell-bewerkingen en moet worden ingesteld op ' false '.
  > [!NOTE]
  > Deze bewerking is niet geldig voor een URI als een andere bewerking ook wordt ondersteund.
  > [!NOTE]
  > Als een shell-bewerking is geconfigureerd voor een URI, worden Get-, put-, Create-, Delete-, Invoke-en Enumeratable-bewerkingen intern verwerkt in de WS-Management-service (WinRM) voor het beheren van shells. Als gevolg hiervan kan de invoeg toepassing de bewerkingen niet afhandelen.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a>CertificateThumbprint \<String\>

Hiermee geeft u de vinger afdruk van het service certificaat.

Deze waarde vertegenwoordigt de reeks hexadecimale waarden van twee cijfers in het veld vinger afdruk van het certificaat. Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts. Gebruik de `Get-Item` `Get-ChildItem` cmdlets in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a>Ingeschakeld \<Boolean\>

Hiermee geeft u op of de listener is in-of uitgeschakeld. De standaard waarde is True.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a>Bestands naam (invoeg toepassing) \<String\>

Hiermee geeft u de bestands naam van de invoeg toepassing voor bewerkingen. Alle omgevings variabelen die in dit item worden geplaatst, worden uitgevouwen in de context van de gebruiker wanneer een aanvraag wordt ontvangen. Omdat elke gebruiker een andere versie van dezelfde omgevings variabele kan hebben, kan elke gebruiker een andere invoeg toepassing hebben. Deze vermelding mag niet leeg zijn en moet verwijzen naar een geldige invoeg toepassing.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a>Hostnaam \<String\>

Hiermee geeft u de hostnaam op van de computer waarop de WS-Management-service (WinRM) wordt uitgevoerd.

De waarde moet een Fully Qualified Domain Name, een letterlijke IPv4-of een IPv6-teken reeks of een Joker teken zijn.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a>Verlener \<String\>

Hiermee geeft u de naam van de certificerings instantie die het certificaat heeft uitgegeven.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a>Invoeg toepassing \<\> WS-Management-invoeg toepassingen zijn systeem eigen Dynamic Link Libraries (dll's)

waarmee u de functionaliteit van WS-Management insluit en uitbreidt. De WSW-Management-invoeg toepassing biedt functionaliteit waarmee een gebruiker invoeg toepassingen kan schrijven door bepaalde Api's te implementeren voor ondersteunde bron-Uri's en bewerkingen. Nadat de invoeg toepassingen zijn geconfigureerd voor de WS-Management-service (WinRM) of voor Internet Information Services (IIS), worden de invoeg toepassingen respectievelijk geladen in de WS-Management host of in de IIS-host. Externe aanvragen worden doorgestuurd naar deze invoer punten om bewerkingen uit te voeren.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a>Importeer \<Unsigned Short Integer\>

Hiermee geeft u de TCP-poort waarvoor deze listener is gemaakt. U kunt een waarde van 1 tot en met 65535 opgeven.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

Hiermee geeft u een eind punt op dat een afzonderlijk type beheer bewerking of-waarde vertegenwoordigt. Een service stelt een of meer resources beschikbaar en sommige resources kunnen meer dan één exemplaar hebben. Een beheer bron is vergelijkbaar met een WMI-klasse of een database tabel, en een exemplaar is vergelijkbaar met een instantie van de klasse of van een rij in de tabel. De klasse **Win32_LogicalDisk** vertegenwoordigt bijvoorbeeld een resource. `Win32_LogicalDisk="C:\\"` is een specifiek exemplaar van de resource.

Een URI (Uniform Resource Identifier) bevat een voor voegsel en een pad naar een resource.
Bijvoorbeeld:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

Hiermee geeft u de URI (Uniform Resource Identifier) op die een specifiek type resource identificeert, zoals een schijf of een proces, op een computer.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a>SDKVersion \<String\>

Hiermee geeft u de versie van de SDK van de WS-Management-invoeg toepassing. De enige geldige waarde is
1.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a>Onderwerp \<String\>

Hiermee geeft u de entiteit op die wordt geïdentificeerd door het certificaat.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a>Portmap \<String\>

Hiermee geeft u het Trans Port op dat moet worden gebruikt voor het verzenden en ontvangen van WS-Management protocol aanvragen en-antwoorden. De waarde moet HTTP of HTTPS zijn.

Opmerking: de transport waarde is ingesteld bij het maken van een listener.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a>URI \<String\>

Hiermee wordt de URI aangegeven waarvoor toegang is toegestaan op basis van de waarde van de SDDL-para meter.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a>URLPrefix \<String\>

Een URL-voor voegsel voor het accepteren van HTTP-of HTTPS-aanvragen. Dit is een teken reeks met alleen de tekens `[a-z]` , `[A-Z]` ,, `[9-0]` onderstrepen ( `_` ) en back slash ( `/` ). De teken reeks mag niet beginnen met of eindigen op een back slash ( `/` ). Als de computer naam bijvoorbeeld ' SampleComputer ' is, geeft de WS-Management-client `http://SampleMachine/URLPrefix` op in het doel adres.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a>Value \<String\>

Hiermee geeft u de waarde van een initialisatie parameter op, een waarde die specifiek is voor een invoeg toepassing die wordt gebruikt om configuratie opties op te geven.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a>XMLRenderingType \<String\>

Hiermee geeft u de indeling op waarin XML wordt door gegeven aan invoeg toepassingen via het **WSMAN_DATA** -object. De volgende waarden zijn geldig:

- Tekst: inkomende XML-gegevens bevinden zich in een **WSMAN_DATA_TYPE_TEXT** structuur, die de XML vertegenwoordigt als een **PCWSTR** -geheugen buffer.
- XMLReader: inkomende XML-gegevens bevinden zich in een **WSMAN_DATA_TYPE_WS_XML_READER** -structuur, die de XML vertegenwoordigt als een **XmlReader** -object, dat is gedefinieerd in het header-bestand ' webservices. h '.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>De pijp lijn gebruiken

Provider-cmdlets accepteren de invoer van de pijp lijn. U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.
Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.

## <a name="getting-help"></a>Ondersteuning vragen

Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.

Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a>Zie ook

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

