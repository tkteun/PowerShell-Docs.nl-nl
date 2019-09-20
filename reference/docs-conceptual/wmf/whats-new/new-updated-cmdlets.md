---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Nieuwe en bijgewerkte cmdlets
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145024"
---
# <a name="new-and-updated-cmdlets"></a>Nieuwe en bijgewerkte cmdlets

We hebben nieuwe en bijgewerkte bestaande cmdlets toegevoegd op basis van feedback van de community.

## <a name="archive-cmdlets"></a>Archief-cmdlets

`Compress-Archive` Met twee nieuwe cmdlets en `Expand-Archive`kunt u zip-bestanden comprimeren en uitvouwen.

Zie de documentatie over de module [micro soft. Power shell. Archive](/powershell/module/microsoft.powershell.archive/) voor meer informatie.

## <a name="catalog-cmdlets"></a>Catalogus-cmdlets

Er zijn twee nieuwe cmdlets toegevoegd in de module micro soft. Power shell. Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Deze genereren en valideren Windows-catalogus bestanden.

## <a name="clipboard-cmdlets"></a>Klembord-cmdlets

`Get-Clipboard`en `Set-Clipboard` Maak het eenvoudiger voor u om inhoud over te dragen van en naar een Windows Power shell-sessie. De Klembord-cmdlets ondersteunen installatie kopieën, audio bestanden, bestands lijsten en tekst.

Zie voor meer informatie

- [Get-klem bord](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-klem bord](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlets voor cryptografische bericht syntaxis (CMS)

De syntaxis cmdlets van cryptografische berichten ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het cryptografisch beveiligen van berichten zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652.html).

De CMS Encryption Standard implementeert open bare-sleutel cryptografie, waarbij de sleutel die wordt gebruikt voor het versleutelen van inhoud (de *open bare sleutel*) en de sleutel die wordt gebruikt voor het ontsleutelen van inhoud (de *persoonlijke sleutel*), gescheiden zijn.

Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens. Alle inhoud die is versleuteld met de open bare sleutel kan alleen worden ontsleuteld met de persoonlijke sleutel. Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

Zie voor meer informatie:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Beveiliging opheffen-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

Certificaten vereisen een unieke sleutel gebruiks-id (EKU), zoals ' hand tekening bij programma code ' of ' versleutelde E-mail ', om ze te identificeren als certificaten voor gegevens versleuteling in Power shell. Als u certificaten voor document versleuteling in de certificaat provider wilt weer geven, kunt u de para `Get-ChildItem`meter DocumentEncryptionCert Dynamic gebruiken van:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Gestructureerde objecten uit teken reeks inhoud extra heren en parseren

### <a name="convertfrom-string"></a>ConvertFrom-teken reeks

De nieuwe `ConvertFrom-String` cmdlet ondersteunt twee modi:

- Basis delimite parsering
- Automatisch gegenereerd voor beeld-aangedreven parsering

Met een scheidings teken voor het parseren wordt standaard de invoer gesplitst in witruimte en worden eigenschapnamen toegewezen aan de resulterende groepen.

De **UpdateTemplate** para meter slaat de resultaten van het leer algoritme op in een opmerking in het sjabloon bestand. Dit maakt het leer proces (het langzaamste stadium) één eenmalige kosten. Het `ConvertFrom-String` uitvoeren van een sjabloon die het algoritme voor gecodeerde lessen bevat, is nu bijna direct.

Zie [ConvertFrom-string (](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)Engelstalig) voor meer informatie.

### <a name="convert-string"></a>Convert-String

`Convert-String`Hiermee kunt u vóór en na voor beelden opgeven hoe tekst eruit moet zien. De cmdlet formatteert uw tekst automatisch.

Zie [Convert-string](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)(Engelstalig) voor meer informatie.

## <a name="updates-to-fileinfo-object"></a>Updates voor FileInfo-object

Informatie over de bestands versie kan misleidend zijn, met name in gevallen waarin het bestand is gerepareerd. WMF 5,0 voegt nieuwe **FileVersionRaw** -en **ProductVersionRaw** -script eigenschappen toe aan **file info** -objecten.
Dit zijn de eigenschappen die worden weer gegeven voor Power shell. exe (ervan uitgaande dat $pid de ID is van het Power Shell-proces):

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

`Format-Hex`Hiermee kunt u tekst of binaire gegevens in hexadecimale indeling weer geven.

Zie [Format-hex](/powershell/module/microsoft.powershell.utility/format-hex)voor meer informatie.

## <a name="get-childitem-has--depth-parameter"></a>Get-Child item heeft para meter-Depth

`Get-ChildItem`heeft nu een **diepte** parameter voor gebruik met **recursie** om de recursie te beperken:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Modules ondersteunen voor het declareren van versie bereiken (1. *, etc.)

U kunt nu **MinimumVersion** en **MaximumVersion** combi neren om module te importeren binnen een bepaald bereik. De para meters ondersteunen ook joker tekens.

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

Er zijn veel scenario's waarbij youneed voor een unieke id. De `New-GUID` cmdlet biedt een eenvoudige manier om een nieuwe GUID te maken.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>De para meter voor een nieuwe regel

`Out-File`, `Add-Content`en `Set-Content` nu een nieuwe optie voor het wijzigen van een nieuwe **nieuwe** regel, waardoor er na de uitvoer niet meer wordt gelaat. Bijvoorbeeld:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

Zonder dat de **nieuwe** regel wordt opgegeven, zou elk fragment op een afzonderlijke regel staan:

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Communiceren met symbolische koppelingen met verbeterde item-cmdlets

De cmdlet item en enkele verwante cmdlets zijn uitgebreid ter ondersteuning van symbolische koppelingen.

### <a name="symbolic-link-files"></a>Symbolische koppelings bestanden

In dit voor beeld maken we een nieuw symbolische koppelings bestand met de naam MySymLinkFile. txt in C:\Temp dat is gekoppeld aan $pshome \profile.ps1. Alle drie de voor beelden produceren hetzelfde resultaat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Symbolische koppelings mappen

In dit voor beeld maken we een nieuwe symbolische koppeling map met de naam MySymLinkDir in C:\Temp die aan de $pshome map is gekoppeld. Alle drie de voor beelden produceren hetzelfde resultaat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Vaste koppelingen

Dezelfde combi Naties van **pad** en **naam** zijn toegestaan zoals hierboven is beschreven.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Adreslijst koppelingen

Dezelfde combi Naties van **pad** en **naam** zijn toegestaan zoals hierboven is beschreven.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-Child item

`Get-ChildItem`in wordt nu een ' l ' weer gegeven in de eigenschap **mode** om een symbolische koppelings bestand of-map aan te geven.

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

### <a name="remove-item"></a>Verwijderen-item

Het verwijderen van symbolische koppelingen werkt zoals bij het verwijderen van een ander item type.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Gebruik de para meter **Force** om de bestanden in de doel directory en de symbolische koppeling te verwijderen.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Soms moet u in uw scripts een tijdelijk bestand maken. U kunt dit nu doen met de `New-TemporaryFile` cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Beheer van netwerkswitch met PowerShell

Met de netwerk switch-cmdlets, die zijn geïntroduceerd in WMF 5,0, kunt u switch, virtuele LAN (VLAN) en elementaire laag 2-netwerk switch poort configuratie Toep assen op Windows Server 2012 R2 logo-gecertificeerde netwerk switches. Met deze cmdlets kunt u het volgende doen:

- Algemene switch configuratie, zoals:
  - Hostnaam instellen
  - Banner voor switch instellen
  - Configuratie behouden
  - Functie in-of uitschakelen

- VLAN-configuratie:
  - VLAN maken of verwijderen
  - VLAN in-of uitschakelen
  - VLAN opsommen
  - Beschrijvende naam voor een VLAN instellen

- Configuratie van laag 2-poort:
  - Poorten opsommen
  - Poorten in-of uitschakelen
  - Poort modi en eigenschappen instellen
  - VLAN toevoegen aan of koppelen aan de trunk of toegang op de poort

Zie de [NetworkSwitchManager](/powershell/module/networkswitchmanager/) -documentatie voor meer informatie.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Power shell-cmdlets genereren op basis van een OData-eind punt met ODataUtils

Met de ODataUtils-module kunnen Power shell-cmdlets van REST-eind punten worden gegenereerd die OData ondersteunen. De module micro soft. Power shell. ODataUtils bevat de volgende functies:

- Meer informatie over het kanaal aan aan de client zijde van het eind punt van de server.
- Ondersteuning voor paginering aan client zijde
- Filters aan de server zijde met behulp van de para meter-Select
- Ondersteuning voor webaanvraag headers

De proxy-cmdlets die door `Export-ODataEndPointProxy` de cmdlet worden gegenereerd, bieden aanvullende informatie van het OData-eind punt aan de server zijde in de **informatie** stroom.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

In het volgende voor beeld wordt het beste product opgehaald en wordt de uitvoer in de `$infoStream` variabele vastgelegd.

Door de para meter **IncludeTotalResponseCount** op te geven, wordt het totale aantal beschik bare **product** records op de server opgehaald.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

U kunt de records ophalen van de server in batches met de ondersteuning voor paginering aan client zijde. Dit is handig wanneer u een grote hoeveelheid gegevens van de server via het netwerk moet verkrijgen.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

De gegenereerde proxy-cmdlets ondersteunen de **Select** -para meter die wordt gebruikt als filter om alleen de record eigenschappen te ontvangen die de client nodig heeft. Het filter vindt plaats op de server, waardoor de hoeveelheid gegevens die via het netwerk wordt overgedragen, kleiner wordt.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

De `Export-ODataEndpointProxy` cmdlet en de proxy-cmdlets die door worden gegenereerd, ondersteunen nu de para meter **headers** . De header kan worden gebruikt om aanvullende informatie die wordt verwacht door het OData-eind punt te kanaal te kanalen.

In het volgende voor beeld wordt een hash-tabel met een abonnements sleutel aan de para meter **headers** door gegeven. Dit is een typisch voor beeld van services waarvoor een abonnements sleutel voor verificatie wordt verwacht.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
