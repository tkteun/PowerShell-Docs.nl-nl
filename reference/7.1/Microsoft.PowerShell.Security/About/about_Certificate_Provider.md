---
description: Certificaat
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certificaat provider
ms.openlocfilehash: 6d78c587f79bb09c66700fb71519fe0f32318386
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252918"
---
# <a name="certificate-provider"></a>Certificaat provider

## <a name="provider-name"></a>Provider naam

Certificaat

## <a name="drives"></a>Aandrijfeenheden

`Cert:`

## <a name="capabilities"></a>Functies

**ShouldProcess**

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot X. 509-certificaat archieven en-certificaten in Power shell.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de Power shell- **certificaat** provider kunt u certificaten en certificaat archieven ophalen, toevoegen, wijzigen, wissen en verwijderen in Power shell.

Het **certificaat** station is een hiërarchische naam ruimte met de certificaat archieven en certificaten op uw computer.

De **certificaat** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Item verplaatsen](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-item Property](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Wissen-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

Het certificaat station bevat de volgende typen.

- Opslag locaties (micro soft. Power shell. commands. X509StoreLocation), die bestaan uit containers met een hoog niveau waarmee de certificaten voor de huidige gebruiker en voor alle gebruikers worden gegroepeerd. Elk systeem heeft een opslag locatie van het object CurrentUser en LocalMachine (alle gebruikers).

- Certificaat archieven (System. Security. Cryptography. X509Certificates. X509Store), die fysieke winkels zijn waarin certificaten worden opgeslagen en beheerd.

- X. 509 **System. Security. Cryptography. X509Certificates. X509Certificate2** -certificaten, die elk een X. 509-certificaat op de computer vertegenwoordigen.
  Certificaten worden geïdentificeerd aan de hand van hun vinger afdrukken.

## <a name="navigating-the-certificate-drive"></a>Navigeren door het certificaat station

De **certificaat** provider geeft de naam ruimte van het certificaat weer als het `Cert:` station in Power shell. Met deze opdracht wordt de `Set-Location` opdracht voor het wijzigen van de huidige locatie naar het basis certificaat archief in de LocalMachine-opslag locatie. Gebruik een back slash ( \\ ) of een slash (/) om een niveau van het station aan te geven `Cert:` .

```powershell
Set-Location Cert:
```

U kunt ook met de certificaat provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een alias vanuit een andere locatie, gebruikt u de `Cert:` naam van het station in het pad.

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld:

```powershell
Set-Location C:
```

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).
> en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="displaying-the-contents-of-the-cert-drive"></a>De inhoud van het certificaat wordt weer gegeven: station

Met deze opdracht wordt de `Get-ChildItem` cmdlet gebruikt voor het weer geven van de certificaat archieven in de locatie van het certificaat archief van het CurrentUser.

Als u zich niet in het station bevindt `Cert:` , gebruikt u een absoluut pad.

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a>Certificaat eigenschappen weer geven in het certificaat: station

In dit voor beeld wordt een certificaat met opgehaald `Get-Item` en opgeslagen in een variabele.
In het voor beeld worden de nieuwe eigenschappen van het certificaat script ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) gebruikt `Select-Object` .

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a>Alle ontwerp certificaten zoeken

Deze opdracht maakt gebruik van de **CodeSigningCert** **en de** para meters van de `Get-ChildItem` cmdlet om alle certificaten op de computer te verkrijgen die dienst hebben voor de ondertekening van de programma code.

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a>Verlopen certificaten zoeken

Met deze opdracht wordt de para meter **ExpiringInDays** van de `Get-ChildItem` cmdlet gebruikt om certificaten op te halen die binnen de komende 30 dagen verlopen.

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a>SSL-certificaten voor server zoeken

Met deze opdracht wordt de para meter **SSLServerAuthentication** van de `Get-ChildItem` cmdlet gebruikt om alle SSL-certificaten van de server op te halen in de winkels van mijn en webhosting.

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a>Verlopen certificaten zoeken op externe computers

Met deze opdracht wordt de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Get-ChildItem` op de Srv01-en Srv02-computers. Als de waarde nul (0) is in de para meter **ExpiringInDays** , worden certificaten opgehaald op de Srv01-en Srv02-computers die zijn verlopen.

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a>Filters combi neren om een specifieke set certificaten te zoeken

Met deze opdracht worden alle certificaten in de LocalMachine-opslag locatie opgehaald met de volgende kenmerken:

- ' fabrikam ' in de DNS-naam
- ' Client verificatie ' in hun EKU
- een waarde van `$true` voor de eigenschap **SendAsTrustedIssuer**
- verloopt niet binnen de komende 30 dagen.

De eigenschap **NotAfter** slaat de verval datum van het certificaat op.

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a>De MMC-module Certificaten openen

`Invoke-Item`Met de cmdlet wordt de standaard toepassing gebruikt voor het openen van een pad dat u opgeeft. Voor certificaten is de standaard toepassing de MMC-module Certificaten.

Met deze opdracht wordt de MMC-module Certificaten geopend om het opgegeven certificaat te beheren.

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a>Certificaten kopiëren

Het kopiëren van certificaten wordt niet ondersteund door de **certificaat** provider. Wanneer u een certificaat probeert te kopiëren, wordt deze fout weer geven.

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a>Certificaten verplaatsen

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a>Alle SSL-server verificatie certificaten verplaatsen naar de webhosting-Store

Met deze opdracht wordt de `Move-Item` cmdlet gebruikt om een certificaat uit de mijn Store te verplaatsen naar het webhosting-archief.

`Move-Item` certificaat archieven worden niet verplaatst en er worden geen certificaten naar een andere opslag locatie verplaatst, zoals het verplaatsen van een certificaat van LocalMachine naar CurrentUser. Met de `Move-Item` cmdlet worden certificaten verplaatst, maar worden persoonlijke sleutels niet verplaatst.

Met deze opdracht wordt de para meter **SSLServerAuthentication** van de `Get-ChildItem` cmdlet gebruikt om certificaten voor SSL-server verificatie op te halen in het certificaat archief.

De geretourneerde certificaten worden door gegeven aan de `Move-Item` cmdlet, waardoor de certificaten worden verplaatst naar het webhosting-archief.

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a>Certificaten en persoonlijke sleutels verwijderen

`Remove-Item`Met de cmdlet worden de door u opgegeven certificaten verwijderd. Met de `-DeleteKey` dynamische para meter wordt de persoonlijke sleutel verwijderd.

### <a name="delete-a-certificate-from-the-ca-store"></a>Een certificaat verwijderen uit het CA-archief

Met deze opdracht wordt een certificaat uit het CA-certificaat archief verwijderd, maar wordt de gekoppelde persoonlijke sleutel intact gelaten.

In het `Cert:` station ondersteunt de `Remove-Item` cmdlet alleen de para meters **DeleteKey** , **Path** , **WhatIf** en **confirm** . Alle andere para meters worden genegeerd.

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a>Een certificaat verwijderen met een Joker teken in de DNS-naam

Met deze opdracht worden alle certificaten verwijderd die een DNS-naam hebben die ' fabrikam ' bevat. De para meter **DNSName** van de cmdlet wordt gebruikt `Get-ChildItem` voor het ophalen van de certificaten en de `Remove-Item` cmdlet om deze te verwijderen.

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a>Persoonlijke sleutels van een externe computer verwijderen

Met deze reeks opdrachten wordt delegering ingeschakeld en wordt het certificaat en de bijbehorende persoonlijke sleutel op een externe computer verwijderd. Als u een persoonlijke sleutel op een externe computer wilt verwijderen, moet u gedelegeerde referenties gebruiken.

Gebruik de- `Enable-WSManCredSSP` cmdlet om CredSSP-verificatie (Credential Security service provider) in te scha kelen op een client op de externe computer S1.
CredSSP staat gedelegeerde verificatie toe.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

Gebruik de `Connect-WSMan` cmdlet om de computer S1 te verbinden met de WinRM-service op de lokale computer. Wanneer deze opdracht is voltooid, wordt de computer S1 weer gegeven in het lokale `WSMan:` station in Power shell.

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

U kunt nu de cmdlet Set-Item gebruiken in het station WSMan: om het kenmerk CredSSP voor de WinRM-service in te scha kelen.

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

Start een externe sessie op de computer S1 met de `New-PSSession` cmdlet en geef CredSSP-verificatie op. Hiermee wordt de sessie in de `$s` variabele opgeslagen.

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

Ten slotte gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Remove-Item` in de sessie in de `$s` variabele. De `Remove-Item` opdracht gebruikt de para meter **DeleteKey** om de persoonlijke sleutel samen met het opgegeven certificaat te verwijderen.

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a>Verlopen certificaten verwijderen

Met deze opdracht wordt de para meter **ExpiringInDays** van de `Get-ChildItem` cmdlet met de waarde 0 gebruikt om certificaten in de webhosting Store te verkrijgen die zijn verlopen.

De variabele met de geretourneerde certificaten wordt naar de cmdlet gesluisd `Remove-Item` , waardoor deze wordt verwijderd. De opdracht maakt gebruik van de para meter **DeleteKey** voor het verwijderen van de persoonlijke sleutel en het certificaat.

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a>Certificaten maken

De `New-Item` cmdlet maakt geen nieuwe certificaten in de **certificaat** provider. Gebruik de cmdlet [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) om een certificaat voor test doeleinden te maken.

## <a name="creating-certificate-stores"></a>Certificaat archieven maken

In het certificaat: station maakt de `New-Item` cmdlet certificaat archieven op de opslag locatie van de LocalMachine. De para meters **name** , **Path** , **WhatIf** en **confirm** worden ondersteund. Alle andere para meters worden genegeerd. De opdracht retourneert een **System. Security. Cryptography. X509Certificates. X509Store** dat het nieuwe certificaat archief vertegenwoordigt.

Met deze opdracht maakt u een nieuw certificaat archief met de naam ' CustomStore ' in de opslag locatie van LocalMachine.

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a>Een nieuw certificaat archief maken op een externe computer

Met deze opdracht maakt u een nieuw certificaat archief met de naam ' HostingStore ' in de opslag locatie LocalMachine op de Server01-computer.

De opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `New-Item` op de computer Server01. De opdracht retourneert een **System. Security. Cryptography. X509Certificates. X509Store** dat het nieuwe certificaat archief vertegenwoordigt.

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a>Client certificaten maken voor WS-Man

Met deze opdracht maakt u een item voor **ClientCertificate** dat kan worden gebruikt door de **WS-Management** -client. De nieuwe **ClientCertificate** wordt weer gegeven in de map **ClientCertificate** als "ClientCertificate_1234567890". Alle para meters zijn verplicht. De **Uitgever** moet een vinger afdruk van het certificaat van de certificerings instantie zijn.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a>Certificaat archieven verwijderen

### <a name="delete-a-certificate-store-from-a-remote-computer"></a>Een certificaat archief verwijderen van een externe computer

Met deze opdracht wordt de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Remove-Item` op de computers S1 en S2. De `Remove-Item` opdracht bevat de **recursieve** para meter, waarmee de certificaten in de Store worden verwijderd voordat het archief wordt verwijderd.

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld. Deze para meters zijn geldig in alle submappen van de certificaat provider, maar zijn alleen effectief op certificaten.

> [!NOTE]
> Para meters die filteren op de `EnhancedKeyUsageList` eigenschap, retour neren ook items met een lege `EnhancedKeyUsageList` eigenschaps waarde.
> Certificaten met een lege **EnhancedKeyUsageList** kunnen voor alle doel einden worden gebruikt.

De volgende certificaat Provider parameters zijn opnieuw geïntroduceerd in Power shell 7,1.

- DNSName
- DocumentEncryptionCert
- SLEUTEL
- ExpiringInDays
- SSLServerAuthentication

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a>CodeSigningCert <System. Management. Automation. SwitchParameter>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Met deze para meter worden certificaten opgehaald waarvoor ' hand tekening bij programma code ' is in de waarde van de eigenschap **EnhancedKeyUsageList** .

### <a name="deletekey-systemmanagementautomationswitchparameter"></a>DeleteKey <System. Management. Automation. SwitchParameter>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)

Met deze para meter wordt de bijbehorende persoonlijke sleutel verwijderd wanneer het certificaat wordt verwijderd.

> [!IMPORTANT]
> Als u een persoonlijke sleutel die is gekoppeld aan een gebruikers certificaat in het `Cert:\CurrentUser` Archief op een externe computer wilt verwijderen, moet u gedelegeerde referenties gebruiken. De `Invoke-Command` cmdlet ondersteunt het overdragen van referenties met behulp van de **CredSSP** -para meter. U moet rekening houden met eventuele beveiligings Risico's voordat u `Remove-Item` met `Invoke-Command` en de overdracht van referenties.

Deze para meter is opnieuw geïntroduceerd in Power shell 7,1

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a>DnsName <Microsoft. Power shell. commands. DnsNameRepresentation>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Met deze para meter worden certificaten opgehaald die het opgegeven domein naam of naam patroon hebben in de eigenschap **DNSNameList** van het certificaat. De waarde van deze para meter kan ' Unicode ' of ' ASCII ' zijn. Punycode waarden worden geconverteerd naar Unicode. Joker tekens ( `*` ) zijn toegestaan.

Deze para meter is opnieuw geïntroduceerd in Power shell 7,1

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a>DocumentEncryptionCert <System. Management. Automation. SwitchParameter>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Met deze para meter worden certificaten opgehaald die ' document Encryption ' hebben in de waarde van de eigenschap **EnhancedKeyUsageList** .

### <a name="eku-systemstring"></a>EKU <System. String>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Met deze para meter worden certificaten opgehaald die het opgegeven tekst-of tekst patroon hebben in de `EnhancedKeyUsageList` eigenschap van het certificaat. Joker tekens ( `*` ) zijn toegestaan. De `EnhancedKeyUsageList` eigenschap bevat de beschrijvende naam en de OID-velden van de EKU.

Deze para meter is opnieuw geïntroduceerd in Power shell 7,1

### <a name="expiringindays-systemint32"></a>ExpiringInDays <System. Int32>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Met deze para meter worden certificaten opgehaald die in of vóór het opgegeven aantal dagen verlopen. Met de waarde 0 (nul) worden certificaten opgehaald die zijn verlopen.

Deze para meter is opnieuw geïntroduceerd in Power shell 7,1

### <a name="itemtype-string"></a>Item type \<String\>

Met deze para meter kunt u het type item opgeven dat wordt gemaakt door `New-Item` .

In een `Certificate` station zijn de volgende waarden toegestaan:

- Certificaat provider
- Certificaat
- Opslaan
- StoreLocation

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a>SSLServerAuthentication <System. Management. Automation. SwitchParameter>

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

Hiermee worden alleen server certificaten voor SSL-webhosting opgehaald. Met deze para meter worden certificaten opgehaald die "server authenticatie" hebben in de `EnhancedKeyUsageList` eigenschaps waarde.

Deze para meter is opnieuw geïntroduceerd in Power shell 7,1

## <a name="script-properties"></a>Script eigenschappen

Er zijn nieuwe script eigenschappen toegevoegd aan het **x509Certificate2** -object dat de certificaten vertegenwoordigt, zodat u de certificaten eenvoudig kunt zoeken en beheren.

- `DnsNameList`: Als u de `DnsNameList` eigenschap wilt vullen, kopieert de certificaat provider de inhoud van de DNSName-vermelding in de SubjectAlternativeName-extensie (San). Als de SAN-extensie leeg is, wordt de eigenschap gevuld met inhoud uit het veld onderwerp van het certificaat.

- `EnhancedKeyUsageList`: Als u de `EnhancedKeyUsageList` eigenschap wilt vullen, kopieert de certificaat provider de OID-eigenschappen van het veld EnhancedKeyUsage (EKU) in het certificaat en wordt er een beschrijvende naam voor gemaakt.

- `SendAsTrustedIssuer`: Als u de `SendAsTrustedIssuer` eigenschap wilt vullen, kopieert de certificaat provider de `SendAsTrustedIssuer` eigenschap van het certificaat.  Zie [beheer van vertrouwde verleners voor client verificatie](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)voor meer informatie.

Met deze nieuwe functies kunt u zoeken naar certificaten op basis van de DNS-namen en verval datums en certificaten voor client-en Server verificatie onderscheiden door de waarde van de eigenschappen van de Enhanced Key Usage (EKU).

## <a name="using-the-pipeline"></a>De pijp lijn gebruiken

Provider-cmdlets accepteren de invoer van de pijp lijn. U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.
Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.

## <a name="getting-help"></a>Ondersteuning vragen

Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.

Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter van `Get-Help` om een bestandssysteem station op te geven.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a>Zie ook

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Signing](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Get-pfx](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
