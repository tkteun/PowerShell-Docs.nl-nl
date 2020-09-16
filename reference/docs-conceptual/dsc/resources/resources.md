---
ms.date: 07/23/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-resources
ms.openlocfilehash: 6ab831c9d423c6189951b43bfab92f800366ceca
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87777920"
---
# <a name="dsc-resources"></a>DSC-resources

> Is van toepassing op Windows Power Shell 4,0 en up.

## <a name="overview"></a>Overzicht

Resources voor desired state Configuration (DSC) bieden de bouw stenen voor een DSC-configuratie. Een resource kan eigenschappen weer geven die kunnen worden geconfigureerd (schema) en de Power shell-script functies bevat die de lokale Configuration Manager (LCM) aanroept om het te maken.

Een resource kan een model als algemeen hebben als een bestand of als een IIS-server instelling. Groepen van like-resources worden gecombineerd in naar een DSC-module, waarmee alle vereiste bestanden in worden ingedeeld in een geportablee structuur en die meta gegevens bevat om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.

Elke resource heeft een *-schema dat bepaalt de syntaxis die nodig is voor het gebruik van de bron in een [configuratie](../configurations/configurations.md).
Het schema van een resource kan op de volgende manieren worden gedefinieerd:

- `Schema.Mof` bestand: de meeste resources definiëren hun _schema_ in een `schema.mof` bestand met behulp van [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- `<Resource Name>.schema.psm1` bestand: [samengestelde resources](../configurations/compositeConfigs.md) definiëren hun _schema_ in een `<ResourceName>.schema.psm1` bestand met behulp van een [parameter blok](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- `<Resource Name>.psm1` bestand: DSC-resources op basis van klassen definiëren hun _schema_ in de klassedefinitie. Syntaxis items worden aangeduid als klasse-eigenschappen. Zie [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)voor meer informatie.

Als u de syntaxis voor een DSC-resource wilt ophalen, gebruikt u de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) met de para meter **syntax** . Dit gebruik is vergelijkbaar met het gebruik van [Get-opdracht](/powershell/module/microsoft.powershell.core/get-command) met de **syntaxis** parameter om de syntaxis van de cmdlet op te halen. De uitvoer die wordt weer gegeven, toont de sjabloon die wordt gebruikt voor een resource blok voor de resource die u opgeeft.

```powershell
Get-DscResource -Syntax Service
```

De uitvoer die u ziet, moet vergelijkbaar zijn met de onderstaande uitvoer, hoewel de syntaxis van deze resource in de toekomst kan veranderen. Net als de syntaxis van de cmdlet zijn de _sleutels_ in vier Kante haken optioneel. De typen geven het type gegevens op dat elke sleutel verwacht.

> [!NOTE]
> De sleutel **controleren** is optioneel omdat deze standaard is ingesteld op pres.

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

> [!NOTE]
> In Power shell-versies onder 7,0 worden `Get-DscResource` op klassen gebaseerde DSC-resources niet gevonden.

Binnen een configuratie kan een **service** bron blok er als volgt uitzien, om **ervoor te zorgen** dat de Spooler-service wordt uitgevoerd.

> [!NOTE]
> Voordat u een resource in een configuratie gaat gebruiken, moet u deze importeren met [import-dscresource bieden](../configurations/import-dscresource.md).

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

Configuraties kunnen meerdere exemplaren van hetzelfde bron type bevatten. Elk exemplaar moet een unieke naam hebben. In het volgende voor beeld wordt een tweede **service** resource blok toegevoegd voor het configureren van de DHCP-service.

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
> Vanaf Power shell 5,0 is IntelliSense toegevoegd voor DSC. Met deze nieuwe functie kunt u de <kbd>Tab</kbd> - <kbd>en</kbd> + <kbd>plaatsings ruimte</kbd> gebruiken om sleutel namen automatisch te volt ooien.

![Resource IntelliSense met Tab-aanvulling](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a>Typen resources

Windows wordt geleverd met ingebouwde resources en Linux heeft specifieke resources voor het besturings systeem. Er zijn resources voor [afhankelijkheden tussen knoop punten](../configurations/crossNodeDependencies.md), resources voor pakket beheer en[resources die eigendom](https://github.com/dsccommunity)zijn van de community. U kunt de bovenstaande stappen gebruiken om de syntaxis van deze resources te bepalen en hoe u deze gebruikt. De pagina's van deze resources zijn onder **verwijzing**gearchiveerd.

### <a name="windows-built-in-resources"></a>Ingebouwde Windows-resources

- [Archiefresource](../reference/resources/windows/archiveResource.md)
- [Omgevingsresource](../reference/resources/windows/environmentResource.md)
- [Bestandsresource](../reference/resources/windows/fileResource.md)
- [Groepsresource](../reference/resources/windows/groupResource.md)
- [GroupSet-resource](../reference/resources/windows/groupSetResource.md)
- [Logboekresource](../reference/resources/windows/logResource.md)
- [Pakketresource](../reference/resources/windows/packageResource.md)
- [ProcessSet-resource](../reference/resources/windows/ProcessSetResource.md)
- [Registerresource](../reference/resources/windows/registryResource.md)
- [Scriptresource](../reference/resources/windows/scriptResource.md)
- [Serviceresource](../reference/resources/windows/serviceResource.md)
- [ServiceSet-resource](../reference/resources/windows/serviceSetResource.md)
- [Gebruikersresource](../reference/resources/windows/userResource.md)
- [WindowsFeature-resource](../reference/resources/windows/windowsFeatureResource.md)
- [WindowsFeatureSet-resource](../reference/resources/windows/windowsFeatureSetResource.md)
- [WindowsOptionalFeature-resource](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [WindowsOptionalFeatureSet-resource](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [WindowsPackageCabResource-resource](../reference/resources/windows/windowsPackageCabResource.md)
- [WindowsProcess-resource](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a>Afhankelijkheids bronnen voor meerdere knoop punten

- [WaitForAll-resource](../reference/resources/windows/waitForAllResource.md)
- [WaitForSome-resource](../reference/resources/windows/waitForSomeResource.md)
- [WaitForAny-resource](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a>Pakket beheer resources

- [Package Management-resource](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [PackageManagementSource-resource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a>Linux-Resources

- [Resource voor Linux-archief](../reference/resources/linux/lnxArchiveResource.md)
- [Resource van Linux-omgeving](../reference/resources/linux/lnxEnvironmentResource.md)
- [Linux FileLine-resource](../reference/resources/linux/lnxFileLineResource.md)
- [Linux-bestands resource](../reference/resources/linux/lnxFileResource.md)
- [Resource van Linux-groep](../reference/resources/linux/lnxGroupResource.md)
- [Linux-pakket resource](../reference/resources/linux/lnxPackageResource.md)
- [Linux-script bron](../reference/resources/linux/lnxScriptResource.md)
- [Resource van Linux-service](../reference/resources/linux/lnxServiceResource.md)
- [Linux SshAuthorizedKeys-resource](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [Linux-gebruikers resource](../reference/resources/linux/lnxUserResource.md)
