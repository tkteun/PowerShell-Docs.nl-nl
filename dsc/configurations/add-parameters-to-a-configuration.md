---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, galerie, instellen
title: Parameters toevoegen aan een configuratie
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685401"
---
# <a name="add-parameters-to-a-configuration"></a>Parameters toevoegen aan een configuratie

Functies, zoals [configuraties](configurations.md) kunnen als parameters worden gebruikt om toe te staan van meer dynamische configuraties op basis van de invoer van de gebruiker. De stappen zijn vergelijkbaar met die wordt beschreven in [functies met Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).

In dit voorbeeld begint met een basisconfiguratie om configureert u de 'Spooler' service ' Actief '.

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Ingebouwde configuratieparameters

In tegenstelling tot een functie echter de [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) kenmerk geen functionaliteit wordt toegevoegd. Naast [algemene Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), configuraties kunnen ook de volgende parameters, zonder dat u voor het definiëren van deze ingebouwde gebruiken.

|Parameter  |Beschrijving  |
|---------|---------|
|`-InstanceName`|Gebruikt bij het definiëren van [samengestelde configuraties](compositeconfigs.md)|
|`-DependsOn`|Gebruikt bij het definiëren van [samengestelde configuraties](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Gebruikt bij het definiëren van [samengestelde configuraties](compositeconfigs.md)|
|`-ConfigurationData`|Gebruikt om door te geven in gestructureerde [configuratiegegevens](configData.md) voor gebruik in de configuratie.|
|`-OutputPath`|Gebruikt om op te geven waar uw "\<computername\>.mof ' wordt gecompileerd aan de bestand|

## <a name="adding-your-own-parameters-to-configurations"></a>Uw eigen parameters toe te voegen aan configuraties

Naast de ingebouwde parameters kunt u ook uw eigen parameters toevoegen aan uw configuraties. Het parameterblok gaat direct in de declaratie van de configuratie, net als een functie. Een configuratie-parameterblok moet buiten een **knooppunt** declaraties, en boven een *importeren* instructies. Door parameters toe te voegen, kunt u uw configuraties meer robuuste en dynamisch.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Voeg een parameter ComputerName toe

De eerste parameter, u toevoegen kunt, is een `-Computername` parameter, zodat u een bestand ".mof" dynamisch voor een compileren kunt `-Computername` u doorgeeft aan uw configuratie. Functies, zoals kunt u ook definiëren een standaardwaarde in het geval de gebruiker voldoet niet aan een waarde voor `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

In de configuratie, geeft u aan uw `-ComputerName` parameter bij het definiëren van uw blok knooppunt.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Aanroepen van de configuratie met parameters

Nadat u parameters aan uw configuratie hebt toegevoegd, kunt u ze gebruiken, net zoals u zou met een cmdlet doen.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compileren van meerdere MOF-bestanden

Het knooppunt blok kan ook een door komma's gescheiden lijst van computernamen accepteren en MOF-bestanden voor elk gegenereerd. U kunt uitvoeren in het volgende voorbeeld voor het genereren van 'MOF-bestanden voor alle computers die is doorgegeven aan de `-ComputerName` parameter.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Geavanceerde parameters in configuraties

Naast een `-ComputerName` parameter, kunnen we de parameters voor de servicenaam en staat toevoegen. Het volgende voorbeeld wordt een parameterblok met een `-ServiceName` parameter en gebruikt deze om dynamisch te bepalen de **Service** resource blokkeren. Ook wordt toegevoegd een `-State` parameter om dynamisch te bepalen de **status** in de **Service** resource blokkeren.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> In andere advacned-scenario's, kan het zinvol meer dynamische gegevens verplaatsen naar een gestructureerde [configuratiegegevens](configData.md).

De configuratie van het voorbeeld wordt een dynamisch `$ServiceName`, maar als deze niet is opgegeven, compileren van een fout leidt. U kunt een standaardwaarde zoals in dit voorbeeld kan toevoegen.

```powershell
[String]
$ServiceName="Spooler"
```

In dit geval echter het verstandig meer om gewoon de gebruiker te dwingen een waarde opgeven voor de `$ServiceName` parameter. De `parameter` kenmerk kunt u verdere validatie en pijplijn ondersteuning voor parameters van uw configuratie toevoegen.

Boven een parameterdeclaratie toevoegen de `parameter` kenmerk blokkeren zoals in het onderstaande voorbeeld.

```powershell
[parameter()]
[String]
$ServiceName
```

U kunt argumenten aan elk opgeven `parameter` kenmerk voor het besturingselement aspecten van de gedefinieerde parameter. Het volgende voorbeeld wordt de `$ServiceName` een **verplichte** parameter.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Voor de `$State` parameter, willen we graag om te voorkomen dat de gebruiker op te geven waarden buiten een vooraf gedefinieerde set (zoals die wordt uitgevoerd, gestopt) de `ValidationSet*`kenmerk dat de gebruiker van de waarden buiten een vooraf gedefinieerde set (zoals die wordt uitgevoerd, op te geven Gestopt). Het volgende voorbeeld wordt de `ValidationSet` kenmerk aan de `$State` parameter. Omdat we niet wilt maken de `$State` parameter **verplichte**, moeten we een standaardwaarde voor het toevoegen.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> U hoeft niet om op te geven een `parameter` kenmerk bij het gebruik van een `validation` kenmerk.

U kunt meer lezen over de `parameter` en validatie kenmerken in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Configuratie van volledig met parameters

We hebben nu een geparameteriseerde configuratie die ervoor zorgt dat de gebruiker om op te geven een `-InstanceName`, `-ServiceName`, en valideert de `-State` parameter.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Zie ook

- [Schrijven van de help voor DSC-configuraties](configHelp.md)
- [Dynamische configuraties](flow-control-in-configurations.md)
- [Van configuratiegegevens in uw configuraties gebruiken](configData.md)
- [Afzonderlijke configuratie- en omgevingsgegevens gegevens](separatingEnvData.md)
