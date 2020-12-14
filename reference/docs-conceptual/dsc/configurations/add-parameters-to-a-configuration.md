---
ms.date: 12/12/2018
keywords: DSC, Power shell, resource, Galerie, Setup
title: Parameters toevoegen aan een configuratie
description: DSC-configuraties kunnen worden para meters voor het toestaan van meer dynamische configuraties op basis van gebruikers invoer.
ms.openlocfilehash: 72f3cf9efb5d99170e71992bed86a20a57132250
ms.sourcegitcommit: 62282bb9c36fea3b4290b9263c1cd8e9ac216e29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96470329"
---
# <a name="add-parameters-to-a-configuration"></a>Parameters toevoegen aan een configuratie

Net als-functies kunnen [configuraties](configurations.md) worden para meters om meer dynamische configuraties op basis van gebruikers invoer toe te staan. De stappen zijn vergelijkbaar met die beschreven in [functies met para meters](/powershell/module/microsoft.powershell.core/about/about_functions).

Dit voor beeld begint met een basis configuratie waarmee de ' Spooler-service ' wordt uitgevoerd '.

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a>Ingebouwde configuratie parameters

In tegens telling tot een functie, voegt het kenmerk [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) geen functionaliteit toe. Naast de [algemene para meters](/powershell/module/microsoft.powershell.core/about/about_commonparameters)kunnen configuraties ook gebruikmaken van de volgende ingebouwde para meters, zonder dat u ze hoeft te definiëren.

|        Parameter        |                                         Beschrijving                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | Gebruikt voor het definiëren van [samengestelde configuraties](compositeconfigs.md)                             |
| `-DependsOn`            | Gebruikt voor het definiëren van [samengestelde configuraties](compositeconfigs.md)                             |
| `-PSDSCRunAsCredential` | Gebruikt voor het definiëren van [samengestelde configuraties](compositeconfigs.md)                             |
| `-ConfigurationData`    | Wordt gebruikt voor het door geven van gestructureerde [configuratie gegevens](configData.md) voor gebruik in de configuratie. |
| `-OutputPath`           | Wordt gebruikt om op te geven waar uw ' \<computername\> . MOF-bestand ' wordt gecompileerd                      |

## <a name="adding-your-own-parameters-to-configurations"></a>Uw eigen para meters aan configuraties toevoegen

Naast de ingebouwde para meters kunt u ook uw eigen para meters aan uw configuraties toevoegen.
Het parameter blok gaat direct in de configuratie declaratie, net als een functie. Een configuratie parameter blok moet zich buiten eventuele **knooppunt** declaraties bevinden en boven alle *import* instructies. Door para meters toe te voegen, kunt u uw configuraties robuuster en dynamisch maken.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Een ComputerName-para meter toevoegen

De eerste para meter die u kunt toevoegen is een `-Computername` para meter, zodat u dynamisch een '. MOF-bestand ' kunt compileren dat `-Computername` u door gegeven aan uw configuratie. Net als functions kunt u ook een standaard waarde definiëren, voor het geval de gebruiker geen waarde doorgeeft voor `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Binnen uw configuratie kunt u vervolgens uw `-ComputerName` para meter opgeven wanneer u het knooppunt blok wilt definiëren.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Uw configuratie met para meters aanroepen

Nadat u para meters aan uw configuratie hebt toegevoegd, kunt u ze op dezelfde manier gebruiken als met een cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Meerdere MOF-bestanden compileren

Het knooppunt blok kan ook een door komma's gescheiden lijst met computer namen accepteren en de MOF-bestanden genereren. U kunt het volgende voor beeld uitvoeren om ". MOF"-bestanden te genereren voor alle computers die worden door gegeven aan de `-ComputerName` para meter.

```powershell
Configuration TestConfig
{
    param
    (
        [String[]]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a>Geavanceerde para meters in configuraties

Naast een `-ComputerName` para meter kunnen we para meters voor de service naam en-status toevoegen.
In het volgende voor beeld wordt een parameter blok met een `-ServiceName` para meter toegevoegd en gebruikt om het **service** bron blok dynamisch te definiëren. Er wordt ook een `-State` para meter toegevoegd om de **status** in het **service** resource blok dynamisch te definiëren.

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

    # It is best practice to explicitly import any required resources or modules.
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
> In meer geavanceerde scenario's kan het zinvol zijn om uw dynamische gegevens te verplaatsen naar een gestructureerde [configuratie gegevens](configData.md).

De voorbeeld configuratie heeft nu een dynamische `$ServiceName` , maar als er geen is opgegeven, wordt er een fout opgetreden bij het compileren van resultaten. U kunt bijvoorbeeld een standaard waarde toevoegen, zoals in dit voor beeld.

```powershell
[String]
$ServiceName="Spooler"
```

In dit geval is het beter om de gebruiker te dwingen een waarde voor de para meter op te geven `$ServiceName` . `parameter`Met het kenmerk kunt u verdere validatie en pijplijn ondersteuning toevoegen aan de para meters van uw configuratie.

Voeg boven een parameter declaratie het `parameter` kenmerk blok toe, zoals in het onderstaande voor beeld.

```powershell
[parameter()]
[String]
$ServiceName
```

U kunt argumenten opgeven voor elk `parameter` kenmerk om aspecten van de gedefinieerde para meter te beheren. In het volgende voor beeld wordt `$ServiceName` een **verplichte** para meter gemaakt.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Voor de `$State` para meter willen we voor komen dat de gebruiker waarden opgeeft buiten een vooraf gedefinieerde set (zoals actief, gestopt). het `ValidationSet*` kenmerk zou voor komen dat de gebruiker waarden opgeeft buiten een vooraf gedefinieerde set (zoals actief, gestopt). In het volgende voor beeld wordt het `ValidationSet` kenmerk toegevoegd aan de `$State` para meter. Omdat we de `$State` para meter niet **verplicht** moeten maken, moeten we een standaard waarde voor deze vereiste toevoegen.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> U hoeft geen kenmerk op te geven `parameter` Wanneer u een `validation` kenmerk gebruikt.

Meer informatie over de `parameter` en validatie kenmerken vindt u in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).

## <a name="fully-parameterized-configuration"></a>Volledig geparametriseerde configuratie

We hebben nu een configuratie met para meters waarmee de gebruiker een `-InstanceName` , `-ServiceName` , en de `-State` para meter valideert.

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
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

## <a name="see-also"></a>Zie ook

- [Help schrijven voor DSC-configuraties](configHelp.md)
- [Dynamische configuraties](flow-control-in-configurations.md)
- [Configuratie gegevens in uw configuraties gebruiken](configData.md)
- [Afzonderlijke configuratie-en omgevings gegevens](separatingEnvData.md)
