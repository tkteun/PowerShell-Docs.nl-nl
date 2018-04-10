---
ms.date: 10/31/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Het MOF-bestand te beveiligen
ms.openlocfilehash: 80ef37ef1bdcb0a8b0ad343b4eab99f1bc66e116
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="securing-the-mof-file"></a>Het MOF-bestand te beveiligen

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC beheert de configuratie van de knooppunten door toe te passen de gegevens die zijn opgeslagen in een MOF-bestand, waarbij de lokale Configuration Manager (LCM) de status van de gewenste end implementeert.
Omdat dit bestand de details van de configuratie bevat, is het belangrijk beveiligd blijft.
In dit onderwerp wordt beschreven hoe zorg ervoor dat het doelknooppunt het bestand is versleuteld.

Vanaf versie 5.0 PowerShell is het gehele MOF-bestand is standaard versleuteld wanneer deze wordt toegepast op het knooppunt met behulp van de **Start DSCConfiguration** cmdlet.
De procedure beschreven in dit artikel is alleen vereist als voor het implementeren van een oplossing met behulp van het pull-service-protocol als certificaten worden niet beheerd, om ervoor te zorgen gedownload door het doelknooppunt configuraties kunnen worden ontsleuteld en gelezen door het systeem voordat ze worden toegepast (bijvoorbeeld de pull-service beschikbaar in Windows Server).
Knooppunten die zijn geregistreerd bij [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) automatisch certificaten geïnstalleerd en worden beheerd door de service met geen administratieve overhead vereist.

>**Opmerking:** in dit onderwerp worden de certificaten die worden gebruikt voor versleuteling.
>Voor versleuteling, een zelfondertekend certificaat volstaat, omdat de persoonlijke sleutel wordt altijd opgeslagen geheim en versleuteling betekent niet dat een vertrouwensrelatie van het document.
>Zelfondertekende certificaten moeten *niet* worden gebruikt voor verificatiedoeleinden.
>U moet een certificaat van een vertrouwde certificeringsinstantie (CA) gebruiken voor andere verificatiedoeleinden.

## <a name="prerequisites"></a>Vereisten

Voor het versleutelen met succes van de referenties gebruikt voor het beveiligen van een DSC-configuratie, zorg ervoor dat hebt u het volgende:

* **Een manier van uitgeven en distribueren van certificaten**. In dit onderwerp en de voorbeelden wordt ervan uitgegaan dat u gebruikmaakt van Active Directory-certificeringsinstantie. Zie voor meer achtergrondinformatie over Active Directory Certificate Services, [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) en [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Beheerderstoegang tot het doelknooppunt of knooppunten**.
* **Elk doelknooppunt heeft een versleuteling geschikt certificaat het persoonlijke archief opgeslagen**. In Windows PowerShell is het pad naar het archief Cert: \LocalMachine\My. Gebruik de sjabloon 'verificatie van werkstation', die u (samen met andere certificaatsjablonen vinden kunt) van de voorbeelden in dit onderwerp op [standaardcertificaatsjablonen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Als u deze configuratie op een andere computer dan het doelknooppunt uitvoert **Exporteer de openbare sleutel van het certificaat**, en vervolgens importeren naar de computer u de configuratie van voert. Zorg ervoor dat u alleen exporteert de **openbare** sleutel; de persoonlijke sleutel te beveiligen.

## <a name="overall-process"></a>Algemene proces

 1. Instellen van de certificaten, sleutels en vingerafdrukken, om ervoor te zorgen dat elk doelknooppunt kopieën van het certificaat heeft en de computer configuratie de openbare sleutel en vingerafdruk heeft.
 2. Maak een configuratie-gegevensblok dat het pad en de vingerafdruk van de openbare sleutel bevat.
 3. Een configuratiescript dat de gewenste configuratie voor het doelknooppunt definieert en ontsleuteling op de doelknooppunten ingesteld door de lokale configuratie bestuurt manager voor het ontsleutelen van de configuratiegegevens met behulp van het certificaat en de vingerafdruk maken.
 4. Voer de configuratie, waarmee u de instellingen voor de lokale Configuration Manager en start de DSC-configuratie.

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Certificaatvereisten

Als u wilt nemen versleuteling van referenties, een openbare-sleutelcertificaat moet beschikbaar zijn op de _doelknooppunt_ die **vertrouwde** door de computer die wordt gebruikt voor het schrijven van de DSC-configuratie.
Deze openbare-sleutelcertificaat bevat de specifieke vereisten om te worden gebruikt voor versleuteling van de DSC-referenties:
 1. **Sleutelgebruik**:
   - Moet bevatten: 'KeyEncipherment' en 'DataEncipherment'.
   - Moet _niet_ bevatten: 'Digitale handtekening'.
 2. **Uitgebreid sleutelgebruik**:
   - Moet bevatten: documentbeveiliging (1.3.6.1.4.1.311.80.1).
   - Moet _niet_ bevatten: clientverificatie (1.3.6.1.5.5.7.3.2) en verificatie van de Server (1.3.6.1.5.5.7.3.1).
 3. De persoonlijke sleutel voor het certificaat is beschikbaar op de * Node_ doel.
 4. De **Provider** voor het certificaat moet 'Microsoft RSA SChannel Cryptographic Provider'.

>**Aanbevolen:** Hoewel u een certificaat met een Sleutelgebruik 'Digitale handtekening' of een van de clientverificatie-EKU die gebruiken kunt, Hiermee schakelt u de versleutelingssleutel moet eenvoudiger misbruik en kwetsbaar voor aanvallen. Het is daarom raadzaam om een certificaat gemaakt specifiek voor het beveiligen van DSC-referenties die worden weggelaten deze sleutelgebruik en EKU's te gebruiken.

Alle bestaande certificaten op de _doelknooppunt_ dat voldoet aan deze criteria kunnen worden gebruikt voor veilige DSC-referenties.

## <a name="certificate-creation"></a>Maken van het certificaat

Er zijn twee manieren maken en gebruiken van het vereiste certificaat voor codering (openbaar / persoonlijk sleutelpaar).

1. Deze maken op de **doelknooppunt** en exporteer de openbare sleutel voor de **knooppunt ontwerpen**
2. Deze maken op de **Authoring knooppunt** en exporteren van de volledige-sleutelpaar de **doelknooppunt**

Methode 1 wordt aanbevolen omdat de persoonlijke sleutel voor het ontsleutelen van referenties in het MOF in het doelknooppunt te allen tijde blijft.


### <a name="creating-the-certificate-on-the-target-node"></a>Maken van het certificaat in het doelknooppunt

De persoonlijke sleutel geheim moet blijven, omdat het wordt gebruikt voor het ontsleutelen van de MOF op de **doelknooppunt** het gemakkelijkst dat het certificaat met persoonlijke sleutel maken op de **doelknooppunt**, en kopieer de  **openbare-sleutelcertificaat** op de computer die wordt gebruikt voor het schrijven van de DSC-configuratie naar een MOF-bestand.
Het volgende voorbeeld:
 1. maakt een certificaat op de **doelknooppunt**
 2. de openbare-sleutelcertificaat exporteert op de **doelknooppunt**.
 3. geïmporteerd certificaat met de openbare sleutel in de **mijn** certificaatarchief op de **ontwerpen knooppunt**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>In het doelknooppunt: maken en het certificaat exporteren
>Doelknooppunt: De WindowsServer 2016 en Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Eenmaal is geëxporteerd, de ```DscPublicKey.cer``` zou moeten worden gekopieerd naar de **Authoring knooppunt**.

>Doelknooppunt: Windows Server 2012 R2/Windows 8.1 en oudere versies

Omdat de cmdlet New-SelfSignedCertificate op Windows-besturingssystemen vóór Windows 10 en Windows Server 2016 bieden geen ondersteuning voor de **Type** parameter, een alternatieve methode voor het maken van dit certificaat is vereist voor deze besturingssystemen.
In dit geval kunt u ```makecert.exe``` of ```certutil.exe``` om het certificaat te maken.

Is een alternatieve methode [downloaden van het script New-SelfSignedCertificateEx.ps1 van Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en deze gebruiken voor het maken van het certificaat in plaats daarvan:
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Eenmaal is geëxporteerd, de ```DscPublicKey.cer``` zou moeten worden gekopieerd naar de **Authoring knooppunt**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>Op het knooppunt ontwerpen: openbare sleutel van het certificaat importeren
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Maken van het certificaat op het knooppunt ontwerpen
U kunt ook het versleutelingscertificaat kan worden gemaakt op de **Authoring knooppunt**, geëxporteerde met de **persoonlijke sleutel** als een PFX-bestand en klik vervolgens geïmporteerd op de **doelknooppunt**.
Dit is de huidige methode voor het implementeren van DSC-referentieversleuteling op _Nano Server_.
Hoewel de PFX is beveiligd met een wachtwoord moet het worden beveiligd tijdens de overdracht.
Het volgende voorbeeld:
 1. maakt een certificaat op de **ontwerpen knooppunt**.
 2. het certificaat op met inbegrip van de persoonlijke sleutel exporteert de **ontwerpen knooppunt**.
 3. Hiermee verwijdert u de persoonlijke sleutel uit de **ontwerpen knooppunt**, maar blijft de openbare-sleutelcertificaat de **mijn** opslaan.
 4. het certificaat met persoonlijke sleutel in het basiscertificaatarchief geïmporteerd op de **doelknooppunt**.
   - Deze moet worden toegevoegd aan het basisarchief zodat deze worden vertrouwd door de **doelknooppunt**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>Op het knooppunt ontwerpen: maken en het certificaat exporteren
>Doelknooppunt: De WindowsServer 2016 en Windows 10

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
Eenmaal is geëxporteerd, de ```DscPrivateKey.pfx``` zou moeten worden gekopieerd naar de **doelknooppunt**.

>Doelknooppunt: Windows Server 2012 R2/Windows 8.1 en oudere versies

Omdat de cmdlet New-SelfSignedCertificate op Windows-besturingssystemen vóór Windows 10 en Windows Server 2016 bieden geen ondersteuning voor de **Type** parameter, een alternatieve methode voor het maken van dit certificaat is vereist voor deze besturingssystemen.
In dit geval kunt u ```makecert.exe``` of ```certutil.exe``` om het certificaat te maken.

Is een alternatieve methode [downloaden van het script New-SelfSignedCertificateEx.ps1 van Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en deze gebruiken voor het maken van het certificaat in plaats daarvan:
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>In het doelknooppunt: de persoonlijke sleutel van het certificaat als een vertrouwde basiscertificeringsinstantie importeren
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Configuratiegegevens

Het gegevensblok configuratie wordt gedefinieerd welke doelknooppunten te bewerken, of of niet voor het versleutelen van de referenties, de wijze van versleuteling en andere informatie. Zie voor meer informatie over het gegevensblok configuratie [scheiden van configuratie en omgevingsgegevens](configData.md).

De elementen die kunnen worden geconfigureerd voor elk knooppunt die gerelateerd zijn aan de versleuteling van referenties zijn:
* **NodeName** -de naam van het doelknooppunt die voor de referentieversleuteling wordt geconfigureerd.
* **PsDscAllowPlainTextPassword** - of niet-versleutelde referenties mag worden doorgegeven aan dit knooppunt. Dit is **niet aanbevolen**.
* **Vingerafdruk** -de vingerafdruk van het certificaat dat wordt gebruikt voor het ontsleutelen van de referenties in de DSC-configuratie op de _doelknooppunt_. **Dit certificaat moet zich in het certificaatarchief van de lokale computer op het doelknooppunt.**
* **CertificateFile** - het certificaatbestand (met alleen de openbare sleutel) die moet worden gebruikt voor het versleutelen van de referenties voor de _doelknooppunt_. Dit moet ofwel een DER encoded binary X.509 of Base-64 gecodeerde x.509-indeling-certificaatbestand.

Dit voorbeeld toont een configuratie-gegevensblok die een doelknooppunt om te fungeren voor benoemde targetNode, het pad naar het openbare-sleutelcertificaat-bestand aangeeft (met de naam targetNode.cer) en de vingerafdruk voor de openbare sleutel.

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

In het configuratiescript zelf, gebruikt u de `PsCredential` parameter om ervoor te zorgen dat de referenties voor de kortst mogelijke tijd worden opgeslagen. Wanneer u het opgegeven voorbeeld uitvoert, wordt DSC vraagt u om referenties en deze vervolgens versleutelen het MOF-bestand met behulp van de CertificateFile die is gekoppeld aan het doelknooppunt in het gegevensblok configuratie. Dit codevoorbeeld wordt een bestand gekopieerd van een share die wordt beveiligd voor een gebruiker.

```
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

## <a name="setting-up-decryption"></a>Ontsleuteling instellen

Voordat u [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) kunt werken, hebt u zien of de lokale Configuration Manager op elk doelknooppunt welk certificaat moet worden gebruikt voor het decoderen van de referenties met behulp van de resource CertificateID om te controleren of de vingerafdruk van het certificaat. Deze voorbeeldfunctie vindt u de juiste lokale certificaatarchief (mogelijk moet aanpassen zodat deze wordt gevonden en het exacte certificaat dat u wilt gebruiken):

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

Met het certificaat dat wordt geïdentificeerd door de vingerafdruk, kan het configuratiescript worden bijgewerkt als de waarde wilt gebruiken:

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

Op dit moment kunt u de configuratie, die de gegevens uit twee bestanden uitvoeren:

 * A *. meta.mof-bestand dat de lokale Configuration Manager voor het ontsleutelen van de referenties met het certificaat dat is opgeslagen op het lokale computerarchief en geïdentificeerd door de vingerafdruk configureert. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) van toepassing is de *. meta.mof-bestand.
 * Een MOF-bestand dat daadwerkelijk de configuratie geldt. Start DscConfiguration geldt de configuratie.

Deze opdrachten worden die stappen uitvoeren:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

In dit voorbeeld zou de DSC-configuratie pushen naar het doelknooppunt.
De DSC-configuratie kan ook worden toegepast met behulp van een DSC-Pull-Server als deze beschikbaar is.

Zie [instellen van een DSC-pull-client](pullClient.md) voor meer informatie over het toepassen van DSC-configuraties met behulp van een DSC-Pull-Server.

## <a name="credential-encryption-module-example"></a>Voorbeeld van de referentie-versleuteling-Module

Hier volgt een voorbeeld van een volledige waarin alle deze stappen, plus een helper-cmdlet die worden geëxporteerd en kopieert de openbare sleutels:

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