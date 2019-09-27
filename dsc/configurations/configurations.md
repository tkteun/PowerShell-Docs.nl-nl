---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: DSC-configuraties
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323256"
---
# <a name="dsc-configurations"></a>DSC-configuraties

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

DSC-configuraties zijn Power shell-scripts waarmee een speciaal type functie wordt gedefinieerd.
Voor het definiëren van een configuratie gebruikt u de **configuratie**van het Power shell-tref woord.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Sla het script op als `.ps1` een bestand.

## <a name="configuration-syntax"></a>Configuratie syntaxis

Een configuratie script bestaat uit de volgende onderdelen:

- Het **configuratie** blok. Dit is het buitenste script blok. U definieert deze met behulp van het sleutel woord **Configuration** en geeft een naam op. In dit geval is de naam van de configuratie ' MyDscConfiguration '.
- Een of meer **knooppunt** blokken. Hier worden de knoop punten (computers of Vm's) gedefinieerd die u configureert. In de bovenstaande configuratie bevindt zich één **knooppunt** blok dat gericht is op een computer met de naam ' test-PC1 '. Het knooppunt blok kan meerdere computer namen accepteren.
- Een of meer resource blokken. Hier stelt de configuratie de eigenschappen in voor de resources die worden geconfigureerd. In dit geval zijn er twee resource blokken, die elk de resource ' WindowsFeature ' aanroepen.

Binnen een **configuratie** blok kunt u alles doen wat u normaal gesp roken in een Power shell-functie zou kunnen uitvoeren. Als u bijvoorbeeld in het vorige voor beeld niet de naam van de doel computer in de configuratie wilt coderen, kunt u een para meter voor de knooppunt naam toevoegen:

In dit voor beeld geeft u de naam van het knoop punt op door dit door te geven als de para meter **ComputerName** wanneer u de configuratie compileert. De naam wordt standaard ingesteld op localhost.

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

Het **knooppunt** blok kan ook meerdere computer namen accepteren. In het bovenstaande voor beeld kunt u de `-ComputerName` para meter gebruiken of een door komma's gescheiden lijst met computers rechtstreeks aan het **knooppunt** blok door geven.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Wanneer u een lijst met computers voor het **knooppunt** blok opgeeft, moet u in een configuratie matrix-Notation gebruiken.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>De configuratie compileren

Voordat u een configuratie kunt vastleggen, moet u deze compileren in een MOF-document.
U doet dit door de configuratie aan te roepen, net zoals u een Power shell-functie zou aanroepen.
De laatste regel van het voor beeld met alleen de naam van de configuratie roept de configuratie aan.

> [!NOTE]
> Voor het aanroepen van een configuratie moet de functie zich in een globaal bereik bevinden (net als bij een andere Power shell-functie).
> U kunt dit doen door het script of door het-configuratie script uit te voeren met F5 of door te klikken op de knop **script uitvoeren** in het ISE.
> Als u het script wilt punt, voert u de `. .\myConfig.ps1` opdracht `myConfig.ps1` uit, waarbij de naam is van het script bestand dat uw configuratie bevat.

Wanneer u de configuratie aanroept, doet u het volgende:

- Hiermee worden alle variabelen omgezet
- Hiermee maakt u een map in de huidige map met dezelfde naam als de configuratie.
- Hiermee maakt u een bestand met de naam ' _nodenaam_. mof ' in de nieuwe map, waarbij _knooppuntnaam_ de naam is van het doel knooppunt van de configuratie.
  Als er meer dan één knoop punt is, wordt voor elk knoop punt een MOF-bestand gemaakt.

> [!NOTE]
> Het MOF-bestand bevat alle configuratie-informatie voor het doel knooppunt. Daarom is het belang rijk dat u deze veilig blijft beveiligen.
> Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)voor meer informatie.

Het compileren van de eerste configuratie hierboven resulteert in de volgende mapstructuur:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Als voor de configuratie een para meter wordt gebruikt, zoals in het tweede voor beeld, die tijdens het compileren moet worden gegeven. Dit ziet er als volgt uit:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Nieuwe resources in uw configuratie gebruiken

Als u de voor gaande voor beelden hebt uitgevoerd, bent u mogelijk opgevallen dat u een resource hebt gebruikt zonder deze expliciet te importeren.
In de PSDesiredStateConfiguration-module van DSC worden er nu 12 resources geleverd.

De cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan worden gebruikt om te bepalen welke resources op het systeem zijn geïnstalleerd en beschikbaar zijn voor gebruik door de LCM.
Zodra deze modules zijn geplaatst `$env:PSModulePath` en op de juiste wijze worden herkend door [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), moeten ze nog steeds worden geladen in uw configuratie.

**Import-dscresource bieden** is een dynamisch tref woord dat alleen kan worden herkend binnen een **configuratie** blok en dat het geen cmdlet is.
**Import-dscresource bieden** ondersteunt twee para meters:

- **Module** naam is de aanbevolen methode voor het gebruik van **import-dscresource bieden**. De naam van de module die de resources bevat die moeten worden geïmporteerd (en een teken reeks matrix van module namen), wordt geaccepteerd.
- **Naam** is de naam van de resource die u wilt importeren. Dit is niet de beschrijvende naam die wordt geretourneerd als ' name ' door [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), maar de naam van de klasse die wordt gebruikt bij het definiëren van het resource schema (geretourneerd als **resource type** op [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Zie `Import-DSCResource` [using import-dscresource bieden](import-dscresource.md) voor meer informatie over het gebruik van.

## <a name="powershell-v4-and-v5-differences"></a>Verschillen Power shell v4 en V5

Er zijn verschillen in waar DSC-resources moeten worden opgeslagen in Power Shell 4,0. Zie [Resource Location](import-dscresource.md#resource-location)(Engelstalig) voor meer informatie.

## <a name="see-also"></a>Zie ook

- [Overzicht van desired state Configuration voor Windows Power shell](../overview/overview.md)
- [DSC-resources](../resources/resources.md)
- [De lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)
