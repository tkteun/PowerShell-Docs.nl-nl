---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-Resources
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046688"
---
# <a name="dsc-resources"></a>DSC-Resources

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Desired State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie. Een resource beschrijft de eigenschappen die kunnen worden geconfigureerd (schema) en bevat de PowerShell-script-functies die de lokale Configuration Manager (LCM) zodat de "," aanroept.

Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model.  Groepen, zoals resources worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die draagbare en is voorzien van metagegevens voor het identificeren van hoe de resources zijn bedoeld om te worden gebruikt.

Elke resource heeft een * schema waarmee wordt bepaald van de syntaxis van de benodigde voor het gebruik van de resource in een [configuratie](../configurations/configurations.md). Schema van een resource kan worden gedefinieerd in de volgende manieren:

- **'Schema.Mof'** bestand: De meeste resources definiëren hun *schema* in een 'schema.mof'-bestand, met behulp van [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **'\<Resourcenaam\>. schema.psm1'** bestand: [Samengestelde Resources](../configurations/compositeConfigs.md) definiëren hun *schema* in een '<ResourceName>. schema.psm1' met behulp van het bestand een [parameterblok](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **'\<Resourcenaam\>.psm1'** bestand: Klasse van DSC-resources definiëren hun *schema* in het klassendefinitie van de. Syntaxis van de items worden aangeduid als de klasse-eigenschappen. Zie voor meer informatie, [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Als u wilt ophalen van de syntaxis voor een DSC-resource, gebruikt u de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet met de `-Syntax` parameter. Dit gebruik is vergelijkbaar met [Get-Command](/powershell/module/microsoft.powershell.core/get-command) met de `-Syntax` parameter om op te halen van de cmdlet-syntaxis. De uitvoer u ziet ziet de sjabloon die wordt gebruikt voor de blokkering van een resource voor de resource die u opgeeft.

```powershell
Get-DscResource -Syntax Service
```

De uitvoer u ziet zijn vergelijkbaar met de uitvoer hieronder, hoewel de syntaxis van deze resource in de toekomst kan veranderen. Syntaxis van de cmdlet, zoals de *sleutels* weergegeven tussen vierkante haken, zijn optioneel. De typen Geef het type gegevens die elke sleutel wordt verwacht.

> [!NOTE]
> De **Zorg ervoor dat** sleutel is optioneel, omdat deze standaard ingesteld op 'Aanwezig'.

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

In een configuratie met een **Service** resource blok kan er als volgt aan **Zorg ervoor dat** die de Spooler-service wordt uitgevoerd.

> [!NOTE]
> Voordat u een resource in een configuratie gebruikt, moet u importeren met behulp van [sleutelwoorden Import-dscresource bieden](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Configuraties kunnen meerdere exemplaren van hetzelfde resourcetype bevatten. Elk exemplaar moet een unieke naam hebben. In het volgende voorbeeld wordt een tweede **Service** resource blok wordt toegevoegd aan de 'DHCP'-service configureren.

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> Begin in PowerShell 5.0, is intellisense toegevoegd voor DSC. Deze nieuwe functie kunt u gebruikmaken van \<tabblad\> en \<Ctrl + spatie\> naar sleutelnamen automatisch aanvullen.

![Tab-aanvulling van resource](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Ingebouwde resources

Naast de bronnen van de community zijn er ingebouwde resources voor Windows, resources voor Linux en resources voor de afhankelijkheid van meerdere knooppunten. U kunt de bovenstaande stappen gebruiken om te bepalen van de syntaxis van deze resources en het gebruik ervan. De pagina's die u beschikbaar deze resources maakt zijn gearchiveerd onder **verwijzing**.

Ingebouwde resources voor Windows

* [Archiefresource](../reference/resources/windows/archiveResource.md)
* [Omgevingsresource](../reference/resources/windows/environmentResource.md)
* [Bestandsresource](../reference/resources/windows/fileResource.md)
* [Groepsresource](../reference/resources/windows/groupResource.md)
* [GroupSet-resource](../reference/resources/windows/groupSetResource.md)
* [Logboekresource](../reference/resources/windows/logResource.md)
* [Pakketresource](../reference/resources/windows/packageResource.md)
* [ProcessSet-resource](../reference/resources/windows/ProcessSetResource.md)
* [Registerresource](../reference/resources/windows/registryResource.md)
* [Scriptresource](../reference/resources/windows/scriptResource.md)
* [Serviceresource](../reference/resources/windows/serviceResource.md)
* [ServiceSet-resource](../reference/resources/windows/serviceSetResource.md)
* [Gebruikersresource](../reference/resources/windows/userResource.md)
* [WindowsFeature-resource](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet-resource](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature-resource](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet-resource](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource Resource](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess-resource](../reference/resources/windows/windowsProcessResource.md)

[Afhankelijkheid van meerdere knooppunten](../configurations/crossNodeDependencies.md) resources

* [WaitForAll Resource](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome Resource](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny Resource](../reference/resources/windows/waitForAnyResource.md)

Package Management-resources

* [PackageManagement-Resource](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource Resource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux-resources

* [Linux-Archiefresource](../reference/resources/linux/lnxArchiveResource.md)
* [Linux-Omgevingsresource](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine Resource](../reference/resources/linux/lnxFileLineResource.md)
* [Linux-bestand voor Resource](../reference/resources/linux/lnxFileResource.md)
* [Linux-groep-Resource](../reference/resources/linux/lnxGroupResource.md)
* [Linux-Pakketresource](../reference/resources/linux/lnxPackageResource.md)
* [Linux-Script-Resource](../reference/resources/linux/lnxScriptResource.md)
* [Bron van het Linux-Service](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys Resource](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux-gebruikersbron](../reference/resources/linux/lnxUserResource.md)
