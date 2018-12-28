---
ms.date: 10/31/2017
keywords: DSC, powershell, configuratie en installatie
title: Het MOF-bestand te beveiligen
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404310"
---
# <a name="securing-the-mof-file"></a>Het MOF-bestand te beveiligen

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC wordt de configuratie van server-knooppunten beheerd door toe te passen die zijn opgeslagen in een MOF-bestand, waarbij de lokale Configuration Manager (LCM) de status van de gewenste end implementeert.
Omdat dit bestand de details van de configuratie bevat, is het belangrijk om veilig te houden.
In dit onderwerp wordt beschreven hoe om te controleren of het doelknooppunt het bestand is versleuteld.

Beginnen met de PowerShell-versie 5.0, het gehele MOF-bestand is standaard versleuteld wanneer deze wordt toegepast op het knooppunt met behulp van de `Start-DSCConfiguration` cmdlet.
De procedure beschreven in dit artikel is vereist alleen bij het implementeren van een oplossing met behulp van de pull-service-protocol als certificaten niet worden beheerd, om te controleren of de configuraties die zijn gedownload door het doelknooppunt kunnen worden ontsleuteld en worden gelezen door het systeem voordat ze worden toegepast (bijvoorbeeld de pull-service beschikbaar is in Windows Server).
Knooppunten die zijn geregistreerd bij [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) automatisch certificaten geïnstalleerd en beheerd door de service met geen administratieve overhead vereist.

> [!NOTE]
> In dit onderwerp worden de certificaten die worden gebruikt voor versleuteling.
> Voor versleuteling, wordt een zelfondertekend certificaat voldoende is, omdat de persoonlijke sleutel wordt altijd bewaard geheim en versleuteling impliceert geen vertrouwen in het document.
> Zelfondertekende certificaten moeten *niet* worden gebruikt voor verificatiedoeleinden wordt gebruikt.
> U moet een certificaat van een vertrouwde certificeringsinstantie (CA) gebruiken voor verificatiedoeleinden.

## <a name="prerequisites"></a>Vereisten

Voor het versleutelen is van de referenties die worden gebruikt voor het beveiligen van een DSC-configuratie, zorg ervoor dat u het volgende:

- **Een manier van uitgeven en distribueren van certificaten**. In dit onderwerp en de voorbeelden wordt ervan uitgegaan dat u gebruikmaakt van Active Directory-certificeringsinstantie. Zie voor meer achtergrondinformatie over Active Directory Certificate Services, [overzicht van Active Directory Certificate Services](https://technet.microsoft.com/library/hh831740.aspx) en [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Beheerderstoegang tot het doelknooppunt of knooppunten**.
- **Elk doelknooppunt heeft een versleuteling geschikt certificaat opgeslagen van de persoonlijke Store**. In Windows PowerShell is het pad naar de store Cert: \LocalMachine\My. De voorbeelden in dit onderwerp gebruikt u de sjabloon "verificatie van werkstation" die u (samen met andere certificaatsjablonen vinden kunt) op [standaardcertificaatsjablonen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Als u deze configuratie op een andere computer dan het doelknooppunt uitvoert **Exporteer de openbare sleutel van het certificaat**, en vervolgens importeren naar de computer die u de configuratie wordt uitgevoerd. Zorg ervoor dat u alleen exporteert de **openbare** sleutel; de persoonlijke sleutel te beveiligen.

## <a name="overall-process"></a>Algehele proces

 1. Instellen van de certificaten, sleutels en vingerafdrukken, ervoor te zorgen dat elk doelknooppunt kopieën van het certificaat heeft en de configuratie-computer de openbare sleutel en de vingerafdruk heeft.
 2. Maak een configuratie-gegevensblokken die het pad en de vingerafdruk van de openbare sleutel bevat.
 3. Maakt een configuratiescript die definieert de gewenste configuratie op voor het doelknooppunt en decodering van de doelknooppunten ingesteld door de lokale configuratie appautonomie manager om de van configuratiegegevens met behulp van het certificaat en de vingerafdruk te ontsleutelen.
 4. Voer de configuratie, waardoor de Local Configuration Manager-instellingen en start de DSC-configuratie.

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Vereisten voor certificaten

Als u wilt gerapporteerd versleuteling van referenties, een openbare-sleutelcertificaat moet beschikbaar zijn op de _doelknooppunt_ dat wil zeggen **vertrouwde** door de computer die wordt gebruikt voor het maken van de DSC-configuratie.
Deze openbare-sleutelcertificaat dat heeft specifieke vereisten voor de oplossing worden gebruikt voor versleuteling van de DSC-referenties:

1. **Sleutelgebruik**:
   - Moet bevatten: 'Keyencipherment-bit' en 'DataEncipherment'.
   - Moet _niet_ bevatten: 'De digitale handtekening'.
2. **Enhanced Key Usage**:
   - Moet bevatten: Document-versleuteling (1.3.6.1.4.1.311.80.1).
   - Moet _niet_ bevatten: Clientverificatie (1.3.6.1.5.5.7.3.2) en serververificatie (1.3.6.1.5.5.7.3.1).
3. De persoonlijke sleutel voor het certificaat is beschikbaar op de * Node_ doel.
4. De **Provider** voor het certificaat moet 'Microsoft RSA SChannel Cryptographic Provider'.

> [!IMPORTANT]
> Maar u een certificaat gebruiken kunt met die van een Sleutelgebruik 'Digitale handtekening' of een van de clientverificatie-EKU, schakelt Hiermee u de versleutelingssleutel moet eenvoudiger misbruik en kwetsbaar voor aanvallen. Het is dus aanbevolen procedure om een certificaat gemaakt voor de beveiliging van de DSC-referenties die worden weggelaten deze sleutelgebruik en EKU's te gebruiken.

Alle bestaande certificaten op de _doelknooppunt_ dat voldoet aan deze criteria kunnen worden gebruikt voor beveiligde DSC-referenties.

## <a name="certificate-creation"></a>Het maken van certificaten

Er zijn twee manieren om te maken en gebruiken van het vereiste certificaat voor versleuteling (openbaar / persoonlijk sleutelpaar).

1. Maken door op de **doelknooppunt** en exporteren van de openbare sleutel voor de **knooppunt ontwerpen**
2. Maken door op de **ontwerpen knooppunt** en exporteren van het gehele sleutelpaar aan de **doelknooppunt**

Methode 1 wordt aanbevolen omdat de persoonlijke sleutel voor het ontsleutelen van de referenties in het MOF op het doelknooppunt te allen tijde blijft.

### <a name="creating-the-certificate-on-the-target-node"></a>Het maken van het certificaat op het doelknooppunt

De privésleutel geheim moet blijven, omdat wordt gebruikt voor het ontsleutelen van de MOF op de **doelknooppunt** de eenvoudigste manier om dat te doen is om te maken van het certificaat met persoonlijke sleutel op de **doelknooppunt**, en kopieer de  **openbare-sleutelcertificaat** op de computer die wordt gebruikt voor het maken van de DSC-configuratie naar een MOF-bestand.
Het volgende voorbeeld:

1. Hiermee maakt u een certificaat op de **doelknooppunt**
2. Hiermee exporteert u de openbare-sleutelcertificaat dat op de **doelknooppunt**.
3. de invoer van de openbare-sleutelcertificaat dat in de **mijn** certificaatarchief op de **ontwerpen knooppunt**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>Op het doelknooppunt: maken en exporteren van het certificaat

> Doelknooppunt: WindowsServer 2016 en Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Eenmaal hebt geëxporteerd, de `DscPublicKey.cer` moet worden gekopieerd naar de **ontwerpen knooppunt**.

> Doelknooppunt: Windows Server 2012 R2/Windows 8.1 en oudere versies
> [!WARNING]
> Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturingssystemen vóór Windows 10 en Windows Server 2016 bieden geen ondersteuning voor de **Type** parameter, een alternatieve methode voor het maken van dit certificaat is vereist op deze besturingssystemen.
>
> In dit geval kunt u `makecert.exe` of `certutil.exe` om het certificaat te maken.
>
>Is een alternatieve methode [het script New-SelfSignedCertificateEx.ps1 downloaden vanaf Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en voor het maken van het certificaat in plaats daarvan het:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Eenmaal hebt geëxporteerd, de ```DscPublicKey.cer``` moet worden gekopieerd naar de **ontwerpen knooppunt**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>Op het knooppunt ontwerpen: de openbare sleutel van het certificaat importeren

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Het maken van het certificaat op het knooppunt ontwerpen

U kunt ook het versleutelingscertificaat dat kan worden gemaakt op de **ontwerpen knooppunt**, geëxporteerd met de **privésleutel** als een PFX-bestand en vervolgens worden geïmporteerd op de **doelknooppunt**.
Dit is de huidige methode voor het implementeren van DSC-referentieversleuteling op _Nano Server_.
Hoewel de PFX is beveiligd met een wachtwoord moet het worden gehouden beveiligd tijdens de overdracht.
Het volgende voorbeeld:

1. Hiermee maakt u een certificaat op de **ontwerpen knooppunt**.
2. Hiermee exporteert u het certificaat met inbegrip van de persoonlijke sleutel op de **ontwerpen knooppunt**.
3. Hiermee verwijdert u de persoonlijke sleutel van de **ontwerpen knooppunt**, maar houdt u de openbare-sleutelcertificaat dat de **mijn** opslaan.
4. het certificaat met persoonlijke sleutel wordt geïmporteerd in het certificaatarchief My(Personal) op de **doelknooppunt**.
   - Deze moet worden toegevoegd aan het basisarchief zodat deze worden vertrouwd door de **doelknooppunt**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>Op het knooppunt ontwerpen: maken en exporteren van het certificaat

> Doelknooppunt: WindowsServer 2016 en Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

Eenmaal hebt geëxporteerd, de `DscPrivateKey.pfx` moet worden gekopieerd naar de **doelknooppunt**.

> Doelknooppunt: Windows Server 2012 R2/Windows 8.1 en oudere versies
> [!WARNING]
> Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturingssystemen vóór Windows 10 en Windows Server 2016 bieden geen ondersteuning voor de **Type** parameter, een alternatieve methode voor het maken van dit certificaat is vereist op deze besturingssystemen.
>
> In dit geval kunt u `makecert.exe` of `certutil.exe` om het certificaat te maken.
>
> Is een alternatieve methode [het script New-SelfSignedCertificateEx.ps1 downloaden vanaf Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en voor het maken van het certificaat in plaats daarvan het:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>Op het doelknooppunt: de persoonlijke sleutel van het certificaat als een vertrouwd basiscertificaat importeren

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Configuratiegegevens

Het gegevensblok configuratie definieert welke doelknooppunten bewerkingen uitvoeren, of of niet voor het versleutelen van de referenties, de wijze van versleuteling en andere informatie. Zie voor meer informatie over het gegevensblok configuratie [scheiden van configuratie- en omgevingsgegevens](../configurations/configData.md).

De elementen die kunnen worden geconfigureerd voor elk knooppunt die gerelateerd zijn aan de versleuteling van referenties zijn:

- **Knooppuntnaam** -de naam van het doelknooppunt die voor de versleuteling van referenties wordt geconfigureerd.
- **PsDscAllowPlainTextPassword** - of niet-versleutelde referenties worden doorgegeven aan dit knooppunt kunnen worden. Dit is **niet aanbevolen**.
- **Vingerafdruk** -de vingerafdruk van het certificaat dat wordt gebruikt voor het ontsleutelen van de referenties in de DSC-configuratie op de _doelknooppunt_. **Dit certificaat moet zich in het certificaatarchief van lokale computer op het doelknooppunt.**
- **CertificateFile** - het certificaatbestand (met alleen de openbare sleutel) die moet worden gebruikt voor het versleutelen van de referenties voor de _doelknooppunt_. Dit moet ofwel een DER encoded binary X.509 of Base-64 gecodeerde x.509-certificaat indelingsbestand.

Dit voorbeeld toont een configuratie-gegevensblokken die Hiermee geeft u een doelknooppunt om te reageren op met de naam targetNode, het pad naar het openbare-sleutelcertificaat dat bestand (met de naam targetNode.cer) en de vingerafdruk voor de openbare sleutel.

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a>Het script voor configuratie

In het configuratiescript zelf, gebruikt u de `PsCredential` parameter om ervoor te zorgen dat de referenties voor de kortst mogelijke tijd worden opgeslagen. Wanneer u het opgegeven voorbeeld uitvoert, wordt DSC u gevraagd om referenties en deze vervolgens versleutelen het MOF-bestand met behulp van de CertificateFile die is gekoppeld aan het doelknooppunt in het gegevensblok configuratie. Dit codevoorbeeld wordt een bestand gekopieerd van een share die wordt beveiligd voor een gebruiker.

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a>Instellen van ontsleuteling

Voordat u [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) kunt werken, hebt u vertelt de Local Configuration Manager op elk doelknooppunt welk certificaat moet worden gebruikt voor het decoderen van de referenties met behulp van de resource CertificateID om te controleren of de vingerafdruk van het certificaat. Deze voorbeeldfunctie vindt u de juiste lokale certificaatarchief (mogelijk moet u deze aanpassen, dus het exacte certificaat dat u wilt gebruiken):

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

Met het certificaat dat wordt geïdentificeerd door de vingerafdruk, kan het configuratiescript worden bijgewerkt om de waarde te gebruiken:

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a>De configuratie wordt uitgevoerd

Op dit moment kunt u de configuratie, die wordt uitgevoerd twee bestanden uitvoeren:

- Een *. meta.mof-bestand dat Hiermee configureert u de Local Configuration Manager voor het ontsleutelen van de referenties met behulp van het certificaat dat is opgeslagen in het archief van de lokale computer en die worden vermeld op basis van de miniatuur. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) van toepassing is de *. meta.mof-bestand.
- Een MOF-bestand dat de configuratie geldt. Start-DscConfiguration geldt de configuratie.

Deze opdrachten wordt deze stappen uitvoeren:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

In dit voorbeeld zou de DSC-configuratie om het doelknooppunt te pushen.
De DSC-configuratie kan ook worden toegepast met behulp van een DSC-Pull-Server als deze beschikbaar is.

Zie [instellen van een DSC-pull-client](pullClient.md) voor meer informatie over het toepassen van DSC-configuraties met behulp van een DSC-Pull-Server.

## <a name="credential-encryption-module-example"></a>Voorbeeld van de Module referentie-codering

Hier volgt een compleet voorbeeld waarin al deze stappen, plus een helper-cmdlet die worden geëxporteerd en de openbare sleutels worden gekopieerd:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
