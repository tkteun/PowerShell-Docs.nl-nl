---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Nieuwe en bijgewerkte cmdlets
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298655"
---
# <a name="new-and-updated-cmdlets"></a>Nieuwe en bijgewerkte cmdlets

We hebben nieuwe en bijgewerkte bestaande cmdlets op basis van feedback van de community toegevoegd.

## <a name="archive-cmdlets"></a>Archief-cmdlets

Twee nieuwe cmdlets `Compress-Archive` en `Expand-Archive`laat u comprimeren en vouw ZIP-bestanden.

Zie voor meer informatie de [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module-documentatie.

## <a name="catalog-cmdlets"></a>Catalogus-Cmdlets

Twee nieuwe cmdlets toegevoegd in de module Microsoft.PowerShell.Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Deze genereren en bestanden van Windows-catalogus te valideren.

## <a name="clipboard-cmdlets"></a>Klembord-cmdlets

`Get-Clipboard` en `Set-Clipboard` maken het gemakkelijker voor u om inhoud naar en van een Windows PowerShell-sessie te brengen. De Klembord-cmdlets bieden ondersteuning voor afbeeldingen, audio-bestanden, bestandslijsten en tekst.

Zie voor meer informatie

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlets voor Cryptographic Message-syntaxis (CMS)

De cmdlets voor Cryptographic Message-syntaxis ondersteunt versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het beveiligen van berichten cryptografisch zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652.html).

De standaard CMS-versleuteling implementeert openbare-sleutelcryptografie, waarbij de sleutel wordt gebruikt voor het versleutelen van inhoud (de *openbare sleutel*) en de sleutel die wordt gebruikt om inhoud te ontsleutelen (de *privésleutel*) zijn gescheiden.

Uw openbare-sleutelcertificaat grote schaal kan worden gedeeld en is geen gevoelige gegevens. Alle inhoud die is versleuteld met de openbare sleutel kan alleen worden ontsleuteld met behulp van de persoonlijke sleutel. Zie voor meer informatie, [openbare-sleutelcryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

Zie voor meer informatie:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

Certificaten vereist de id van een unieke sleutelgebruik (EKU), zoals 'Handtekening bij programmacode' of 'Versleuteld Mail', om te bepalen of deze gegevens versleutelingscertificaten in PowerShell. Als u wilt weergeven versleutelingscertificaten document in de certificaatprovider, kunt u de **DocumentEncryptionCert** dynamische parameter van `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Gestructureerd objecten uit de inhoud van de tekenreeks uitpakken en parseren

### <a name="convertfrom-string"></a>ConvertFrom-String

De nieuwe `ConvertFrom-String` cmdlet ondersteunt twee modi:

- Basic gescheiden parseren
- Automatisch gegenereerde voorbeeld gebaseerde parseren

Gescheiden parseren, standaard, splitst de invoer op witruimte en namen van eigenschappen aan de resulterende groepen toegewezen.

De **UpdateTemplate** parameter slaat de resultaten van het learning-algoritme in een opmerking in het sjabloonbestand. Dit maakt het learning verwerken (de traagste fase) een eenmalige kosten. Met `ConvertFrom-String` met een sjabloon met het gecodeerde learning-algoritme is nu bijna onmiddellijk.

Zie voor meer informatie, [ConvertFrom-tekenreeks](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` kunt u bieden voor en na voorbeelden van hoe u tekst om te zoeken. De cmdlet wordt de tekst automatisch opgemaakt.

Zie voor meer informatie, [Convert-tekenreeks](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Updates voor FileInfo-object

Informatie over de bestandsversie kan misleidend zijn, met name in gevallen waar het bestand is hersteld. WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** eigenschappen gewijzigd in een script **FileInfo** objecten.
Hier zijn de eigenschappen als worden weergegeven voor de powershell.exe (ervan uitgaande dat $pid is de ID van de PowerShell-proces):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` kunt u tekst of binaire gegevens weergeven in hexadecimale notatie.

Zie voor meer informatie, [indeling hexadecimaal](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem heeft parameter - Depth

`Get-ChildItem` heeft nu een **diepte** parameter voor gebruik met **Recurse** de recursie beperken:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Module-ondersteuning voor declareren versiebereiken (1.*, enzovoort)

U kunt nu gecombineerd **MinimumVersion** en **MaximumVersion** module binnen een bepaald bereik te importeren. De parameters bieden ook ondersteuning voor jokertekens.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Er zijn veel scenario's waarbij youneed voor de unieke id. De `New-GUID` cmdlet biedt een eenvoudige manier om te maken van een nieuwe GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>Parameter NoNewLine

`Out-File`, `Add-Content`, en `Set-Content` hebben nu een nieuwe **NoNewline** switch die een nieuwe regel na de uitvoer wordt weggelaten. Bijvoorbeeld:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

Zonder **NoNewline** opgegeven, wordt elk fragment zou worden op een afzonderlijke regel:

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interactie met symbolische koppelingen met verbeterde Item-cmdlets

De cmdlet Item en een aantal verwante cmdlets zijn uitgebreid ter ondersteuning van symbolische koppelingen.

### <a name="symbolic-link-files"></a>Bestanden van de symbolische koppeling

In dit voorbeeld maken we een nieuwe symbolische koppeling-bestand met de naam MySymLinkFile.txt in C:\Temp die is gekoppeld aan $pshome\profile.ps1. Alle drie de voorbeelden opleveren hetzelfde resultaat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Symbolische koppelingsmappen

In dit voorbeeld maken we een nieuwe symbolische koppeling-map met de naam MySymLinkDir in C:\Temp die is gekoppeld aan de map $pshome. Alle drie de voorbeelden opleveren hetzelfde resultaat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Vaste koppelingen

De dezelfde combinaties van **pad** en **naam** toegestaan, zoals hierboven beschreven.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Directory-koppelingen

De dezelfde combinaties van **pad** en **naam** toegestaan, zoals hierboven beschreven.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` een 'l' wordt nu weergegeven de **modus** eigenschap om aan te geven van een symbolische koppelingsbestand of map.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Item verwijderen

Symbolische koppelingen verwijderen werkt net als elk ander itemtype verwijderen.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Gebruik de **Force** parameter voor het verwijderen van de bestanden in de doelmap en de symbolische koppeling.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Soms moet u een tijdelijk bestand maken in uw scripts. U kunt nu doet dit met de `New-TemporaryFile` cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Beheer van netwerkswitch met PowerShell

De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie toepassen op Windows Server 2012 R2-logo gecertificeerde netwerkswitches. Met deze cmdlets die u kunt uitvoeren:

- Globale switch configuratie, zoals:
  - Set-hostnaam
  - Set-switch banner
  - Configuratie blijven behouden
  - Functie- of uitschakelen

- VLAN-configuratie:
  - Maken of verwijderen van VLAN
  - In- of uitschakelen van VLAN
  - VLAN opsommen
  - Beschrijvende naam van de set met een VLAN

- Configuratie van de laag-2-poort:
  - Poorten inventariseren
  - In- of uitschakelen van poorten
  - Set-poort-modi en eigenschappen
  - Toevoegen of koppelen van de VLAN Trunk of toegang op de poort

Zie voor meer informatie de [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentatie.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>PowerShell-cmdlets op basis van een OData-eindpunt met ODataUtils genereren

De module ODataUtils kunt genereren van PowerShell-cmdlets van REST-eindpunten die ondersteuning bieden voor OData. De module Microsoft.PowerShell.ODataUtils bevat de volgende functies:

- Aanvullende informatie van server-side-eindpunt voor client-side-Channel.
- Client-side-ondersteuning voor paginering
- Serverzijde filteren met behulp van de - Select-parameters
- Ondersteuning voor web-aanvraagheaders

De proxy-cmdlets die worden gegenereerd door de `Export-ODataEndPointProxy` cmdlet bevatten aanvullende informatie van het eindpunt van de OData-serverzijde op de **informatie** stream.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

In het volgende voorbeeld zijn we bij het ophalen van de beste product en het vastleggen van de uitvoer in de `$infoStream` variabele.

Door op te geven **IncludeTotalResponseCount** parameter, krijgen we het totale aantal van alle de **Product** records beschikbaar op de server.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

U kunt de records van de server in batches met behulp van de client-side-ondersteuning voor paginering ophalen. Dit is handig als u een grote hoeveelheid gegevens uit de server via het netwerk ophalen moet.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

De gegenereerde proxy-cmdlets bieden ondersteuning voor de **Selecteer** parameter die wordt gebruikt als een filter voor het ontvangen van de recordeigenschappen die de client nodig heeft. Het filter vindt plaats op de server, waardoor de hoeveelheid gegevens die via het netwerk wordt overgedragen.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

De `Export-ODataEndpointProxy` -cmdlet en de webtoepassingsproxy-cmdlets die worden gegenereerd door, bieden nu ondersteuning voor de **Headers** parameter. De header kan worden gebruikt om aanvullende informatie die wordt verwacht door het OData-eindpunt-channel.

In het volgende voorbeeld wordt een hash-tabel met de abonnementssleutel van een wordt geleverd aan de **Headers** parameter. Dit is een typisch voorbeeld voor services die een abonnementssleutel voor verificatie verwacht.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
