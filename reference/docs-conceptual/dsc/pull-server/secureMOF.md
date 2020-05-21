---
ms.date: 10/31/2017
keywords: DSC, Power shell, configuratie, installatie
title: Het MOF-bestand beveiligen
ms.openlocfilehash: 30b7ff276781b398aeae94e710c810f5fccafdfb
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83556384"
---
# <a name="securing-the-mof-file"></a>Het MOF-bestand beveiligen

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

DSC beheert de configuratie van server knooppunten door gegevens die zijn opgeslagen in een MOF-bestand toe te passen, waarbij de lokale Configuration Manager (LCM) de gewenste eind status implementeert. Omdat dit bestand de details van de configuratie bevat, is het belang rijk om het beveiligd te blijven. In dit onderwerp wordt beschreven hoe u ervoor zorgt dat het bestand is versleuteld met het doel knooppunt.

Vanaf Power shell versie 5,0 wordt het volledige MOF-bestand standaard versleuteld wanneer het wordt toegepast op het knoop punt met behulp van de- `Start-DSCConfiguration` cmdlet. Het proces dat in dit artikel wordt beschreven, is alleen vereist bij het implementeren van een oplossing met het pull-service protocol als certificaten niet worden beheerd, om ervoor te zorgen dat de configuraties die door het doel knooppunt worden gedownload, kunnen worden ontsleuteld en gelezen voordat ze worden toegepast (bijvoorbeeld de pull-service die beschikbaar is in Windows Server). Knoop punten die zijn geregistreerd bij [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) , hebben automatisch certificaten geïnstalleerd en beheerd door de service zonder dat er administratieve overhead nodig is.

> [!NOTE]
> In dit onderwerp worden de certificaten beschreven die worden gebruikt voor versleuteling. Voor versleuteling is een zelfondertekend certificaat voldoende, omdat de persoonlijke sleutel altijd geheim is en versleuteling niet het vertrouwen van het document impliceert. Zelfondertekende certificaten mogen *niet* worden gebruikt voor verificatie doeleinden. U moet een certificaat van een vertrouwde certificerings instantie (CA) gebruiken voor verificatie doeleinden.

## <a name="prerequisites"></a>Vereisten

Zorg ervoor dat u over het volgende beschikt om de referenties te versleutelen die worden gebruikt voor het beveiligen van een DSC-configuratie:

- **Een aantal manieren om certificaten te verlenen en te distribueren**. In dit onderwerp en de voor beelden wordt ervan uitgegaan dat u Active Directory certificerings instantie gebruikt. Zie [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx)(Engelstalig) voor meer achtergrond informatie over Active Directory Certificate Services.
- **Beheerders toegang tot het doel knooppunt of de knoop punten**.
- **Elk doel knooppunt heeft een persoonlijk archief dat geschikt is voor versleuteling**. Het pad naar de Store van Windows Power shell is certificaat: \ LocalMachine\My. In de voor beelden in dit onderwerp wordt gebruikgemaakt van de sjabloon voor verificatie van werk station, die u kunt vinden (samen met andere certificaat sjablonen) op [standaard certificaat sjablonen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Als u deze configuratie op een andere computer dan het doel knooppunt wilt uitvoeren, **exporteert u de open bare sleutel van het certificaat**en importeert u het vervolgens naar de computer waarop u de configuratie wilt uitvoeren. Zorg ervoor dat u alleen de **open bare** sleutel exporteert. Zorg ervoor dat de persoonlijke sleutel is beveiligd.

## <a name="overall-process"></a>Algemeen proces

 1. Stel de certificaten, sleutels en vinger afdrukken in om ervoor te zorgen dat elk doel knooppunt kopieën van het certificaat heeft en de configuratie computer de open bare sleutel en vinger afdruk heeft.
 2. Maak een blok met configuratie gegevens dat het pad en de vinger afdruk van de open bare sleutel bevat.
 3. Maak een configuratie script dat uw gewenste configuratie definieert voor het doel knooppunt en stelt ontsleuteling in voor de doel knooppunten door de lokale Configuration Manager te gebruiken om de configuratie gegevens te ontsleutelen met behulp van het certificaat en de vinger afdruk.
 4. Voer de configuratie uit, waarmee de lokale Configuration Manager instellingen worden ingesteld en de DSC-configuratie wordt gestart.

![Diagram1](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Certificaatvereisten

Als u referentie versleuteling wilt instellen, moet er een certificaat met een open bare sleutel beschikbaar zijn op het _doel knooppunt_ dat wordt **vertrouwd** door de computer die wordt gebruikt voor het ontwerpen van de DSC-configuratie. Aan deze open bare-sleutel certificaat kunnen specifieke vereisten worden gebruikt voor het versleutelen van DSC-referenties:

1. **Sleutel gebruik**:
   - Moet het volgende bevatten: ' KeyEncipherment ' en ' DataEncipherment '.
   - Mag _niet_ bevatten: ' digitale hand tekening '.
2. **Uitgebreid sleutel gebruik**:
   - Moet het volgende bevatten: document Encryption (1.3.6.1.4.1.311.80.1).
   - Mag _niet_ bevatten: Client verificatie (1.3.6.1.5.5.7.3.2) en Server verificatie (1.3.6.1.5.5.7.3.1).
3. De persoonlijke sleutel voor het certificaat is beschikbaar op de * doel-Node_.
4. De **provider** van het certificaat moet micro soft RSA SChannel Cryptographic Provider zijn.

> [!IMPORTANT]
> Hoewel u een certificaat met een sleutel gebruik van digitale hand tekening of een van de EKU voor authenticatie kunt gebruiken, is het mogelijk dat de versleutelings sleutel eenvoudiger te gebruiken is en kwetsbaar is voor aanvallen. Het is dus best practice een certificaat te gebruiken dat specifiek is gemaakt voor het beveiligen van DSC-referenties die deze sleutel gebruik en Eku's weglaten.

Elk bestaand certificaat op het _doel knooppunt_ dat voldoet aan deze criteria kan worden gebruikt voor het beveiligen van DSC-referenties.

## <a name="certificate-creation"></a>Certificaat maken

Er zijn twee benaderingen die u kunt nemen om het vereiste versleutelings certificaat (openbaar-persoonlijk sleutel paar) te maken en te gebruiken.

1. Maken op het **doel knooppunt** en alleen de open bare sleutel exporteren naar het **ontwerp knooppunt**
2. Maken op het **ontwerp knooppunt** en het volledige sleutel paar exporteren naar het **doel knooppunt**

Methode 1 wordt aanbevolen omdat de persoonlijke sleutel die wordt gebruikt voor het ontsleutelen van referenties in de MOF te allen tijde op het doel knooppunt blijft.

### <a name="creating-the-certificate-on-the-target-node"></a>Het certificaat maken op het doel knooppunt

De persoonlijke sleutel moet geheim blijven, omdat deze wordt gebruikt voor het ontsleutelen van de MOF op het **doel knooppunt** de eenvoudigste manier om dat te doen, is door het certificaat voor de persoonlijke sleutel te maken op het **doel knooppunt**en het certificaat van de **open bare sleutel** te kopiëren naar de computer die wordt gebruikt om de DSC-configuratie te schrijven naar een MOF-bestand. Het volgende voor beeld:

1. Hiermee maakt u een certificaat op het **doel knooppunt**
2. exporteert het certificaat van de open bare sleutel op het **doel knooppunt**.
3. Hiermee wordt het certificaat van de open bare sleutel in **het certificaat archief van het** **ontwerp knooppunt**geïmporteerd.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>Op het doel knooppunt: het certificaat maken en exporteren

> Doel knooppunt: Windows Server 2016 en Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Na het exporteren `DscPublicKey.cer` moet de worden gekopieerd naar het **ontwerp knooppunt**.

> Doel knooppunt: Windows Server 2012 R2/Windows 8,1 en eerder
> [!WARNING]
> Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturings systemen vóór Windows 10 en Windows Server 2016 niet de **type** parameter ondersteunt, is een alternatieve methode voor het maken van dit certificaat vereist op deze besturings systemen. In dit geval kunt u `makecert.exe` of gebruiken `certutil.exe` om het certificaat te maken. Een alternatieve methode is [het script New-SelfSignedCertificateEx. ps1 te downloaden uit het micro soft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en dit te gebruiken om in plaats daarvan het certificaat te maken:

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

Na het exporteren ```DscPublicKey.cer``` moet de worden gekopieerd naar het **ontwerp knooppunt**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>Op het ontwerp knooppunt: de open bare sleutel van het certificaat importeren

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Het certificaat maken op het ontwerp knooppunt

Het versleutelings certificaat kan ook worden gemaakt op het **ontwerp knooppunt**, met de **persoonlijke sleutel** geëxporteerd als een pfx-bestand en vervolgens worden geïmporteerd op het **doel knooppunt**. Dit is de huidige methode voor het implementeren van DSC-referentie versleuteling op _nano server_. Hoewel de PFX met een wacht woord is beveiligd, moet deze tijdens de overdracht veilig worden bewaard. Het volgende voor beeld:

1. Hiermee maakt u een certificaat op het **ontwerp knooppunt**.
2. exporteert het certificaat inclusief de persoonlijke sleutel op het **ontwerp knooppunt**.
3. Hiermee verwijdert u de persoonlijke sleutel van het **ontwerp knooppunt**, maar behoudt u het certificaat voor de open bare sleutel in de **mijn** Store.
4. importeert het certificaat van de persoonlijke sleutel in het certificaat archief mijn (persoonlijk) op het **doel knooppunt**.
   - het moet worden toegevoegd aan het hoofd archief zodat het wordt vertrouwd door het **doel knooppunt**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>Op het ontwerp knooppunt: het certificaat maken en exporteren

> Doel knooppunt: Windows Server 2016 en Windows 10

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

Na het exporteren `DscPrivateKey.pfx` moet de worden gekopieerd naar het **doel knooppunt**.

> Doel knooppunt: Windows Server 2012 R2/Windows 8,1 en eerder
> [!WARNING]
> Omdat de `New-SelfSignedCertificate` cmdlet op Windows-besturings systemen vóór Windows 10 en Windows Server 2016 niet de **type** parameter ondersteunt, is een alternatieve methode voor het maken van dit certificaat vereist op deze besturings systemen. In dit geval kunt u `makecert.exe` of gebruiken `certutil.exe` om het certificaat te maken. Een alternatieve methode is [het script New-SelfSignedCertificateEx. ps1 te downloaden uit het micro soft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) en dit te gebruiken om in plaats daarvan het certificaat te maken:

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>Op het doel knooppunt: de persoonlijke sleutel van het certificaat importeren als een vertrouwde basis

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Configuratiegegevens

In het configuratie gegevens blok worden de doel knooppunten gedefinieerd waarop moet worden toegepast, ongeacht of de referenties, de wijze van versleuteling en andere gegevens moeten worden versleuteld. Zie de [configuratie-en omgevings gegevens scheiden](../configurations/configData.md)voor meer informatie over het gegevens blok van de configuratie.

De volgende elementen kunnen worden geconfigureerd voor elk knoop punt dat is gerelateerd aan referentie versleuteling:

- **Nodenaam** : de naam van het doel knooppunt waarvoor de referentie versleuteling wordt geconfigureerd.
- **PsDscAllowPlainTextPassword** : Hiermee wordt aangegeven of niet-versleutelde referenties mogen worden door gegeven aan dit knoop punt. Dit wordt **niet aanbevolen**.
- **Vinger afdruk** : de vinger afdruk van het certificaat dat wordt gebruikt voor het ontsleutelen van de referenties in de DSC-configuratie op het _doel knooppunt_. **Dit certificaat moet aanwezig zijn in het certificaat archief van de lokale computer op het doel knooppunt.**
- **CertificateFile** : het certificaat bestand (alleen de open bare sleutel) dat moet worden gebruikt om de referenties voor het _doel knooppunt_te versleutelen. Dit moet een DER Encoded Binary X. 509 of base-64 Encoded X. 509-indeling certificaat bestand.

In dit voor beeld wordt een blok van een configuratie gegevens weer gegeven waarin een doel knooppunt wordt opgegeven voor het uitvoeren van de naam targetNode, het pad naar het certificaat bestand met de open bare sleutel (met de naam targetNode. CER) en de vinger afdruk voor de open bare sleutel.

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

## <a name="configuration-script"></a>Configuratie script

In het configuratie script zelf gebruikt u de `PsCredential` para meter om ervoor te zorgen dat referenties voor de kortst mogelijke tijd worden opgeslagen. Wanneer u het opgegeven voor beeld uitvoert, wordt u gevraagd referenties op te vragen en vervolgens het MOF-bestand te versleutelen met behulp van de CertificateFile die is gekoppeld aan het doel knooppunt in het configuratie gegevens blok. In dit code voorbeeld wordt een bestand gekopieerd van een share die is beveiligd met een gebruiker.

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

## <a name="setting-up-decryption"></a>Ontsleuteling instellen

Voordat [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) u kunt werken, moet u de lokale Configuration Manager op elk doel knooppunt vertellen welk certificaat moet worden gebruikt om de referenties te ontsleutelen, met behulp van de CertificateID-resource om de vinger afdruk van het certificaat te verifiëren. In dit voor beeld wordt het juiste lokale certificaat gevonden (mogelijk moet u het aanpassen zodat het exacte certificaat wordt gevonden dat u wilt gebruiken):

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

Met het certificaat dat is geïdentificeerd door de vinger afdruk, kan het configuratie script worden bijgewerkt om de waarde te gebruiken:

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

Op dit moment kunt u de configuratie uitvoeren, waardoor twee bestanden worden uitgevoerd:

- Een \* . meta. MOF-bestand waarmee de lokale Configuration Manager worden geconfigureerd om de referenties te ontsleutelen met behulp van het certificaat dat is opgeslagen in het archief van de lokale computer en wordt geïdentificeerd door de vinger afdruk.
  [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx)past het \* . meta. MOF-bestand toe.
- Een MOF-bestand dat de configuratie werkelijk toepast. Start-DscConfiguration past de configuratie toe.

Met deze opdrachten voert u de volgende stappen uit:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

In dit voor beeld wordt de DSC-configuratie naar het doel knooppunt gepusht. De DSC-configuratie kan ook worden toegepast met behulp van een DSC-pull-server, als er een beschikbaar is.

Zie [een DSC-pull-client instellen](pullClient.md) voor meer informatie over het Toep assen van DSC-configuraties met behulp van een DSC-pull-server.

## <a name="credential-encryption-module-example"></a>Voor beeld van referentie versleutelings module

Hier volgt een volledig voor beeld waarin al deze stappen zijn opgenomen, plus een helper-cmdlet waarmee de open bare sleutels worden geëxporteerd en gekopieerd:

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
