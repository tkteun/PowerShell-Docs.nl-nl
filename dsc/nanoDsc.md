---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC gebruiken op Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190244"
---
# <a name="using-dsc-on-nano-server"></a>DSC gebruiken op Nano Server

> Van toepassing op: Windows PowerShell 5.0

**DSC op Nano Server** is een optioneel pakket in de `NanoServer\Packages` map van de Windows Server 2016-media. Het pakket kan worden geïnstalleerd wanneer u een VHD voor een Nano Server door op te geven maken **Microsoft-NanoServer-DSC-Package** als de waarde van de **pakketten** parameter van de **nieuw NanoServerImage**  functie. Als u een VHD voor een virtuele machine maakt, wordt door de opdracht er als volgt:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Zie voor meer informatie over het installeren en gebruiken van Nano Server, evenals de Nano Server met PowerShell op afstand beheren [aan de slag met Nano Server](https://technet.microsoft.com/library/mt126167.aspx).


## <a name="dsc-features-available-on-nano-server"></a>DSC-functies die beschikbaar zijn op Nano Server

 Omdat Nano Server alleen een beperkte set van vergeleken met een volledige versie van Windows Server-API's ondersteunt, heeft DSC op Nano Server geen volledig functionele pariteit met DSC op volledige SKU's voor de tijd die wordt uitgevoerd. DSC op Nano Server is in de actieve ontwikkeling en is nog niet voltooid functie.

 De volgende DSC-functies zijn momenteel beschikbaar op Nano Server:


* Zowel push als pull-modi

* Alle DSC-cmdlets die bestaan op een volledige versie van Windows Server, waaronder het volgende:
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn521621.aspx)
  * [Schakel DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [Update DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Aanroepen DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Zoeken naar DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* Compileren van configuraties (Zie [DSC-configuraties](configurations.md))

  **Probleem:** wachtwoordversleuteling (Zie [beveiligen van het MOF-bestand](securemof.md)) tijdens het configureren van de compilatie niet werkt.

* Metaconfigurations compileren (Zie [configureren van de lokale Configuration Manager](metaConfig.md))

* Een bron op onder de gebruikerscontext wordt uitgevoerd (Zie [DSC uitgevoerd met de referenties van gebruiker (RunAs)](runAsUser.md))

* Klasse-bronnen (Zie [schrijven van een aangepaste DSC-resource met PowerShell klassen](authoringResourceClass.md))

* Foutopsporing van DSC-resources (Zie [foutopsporing DSC-resources](debugresource.md))

  **Probleem:** werkt niet als een resource maakt gebruik van PsDscRunAsCredential (Zie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md))

* [Afhankelijkheden van meerdere knooppunten opgeven](crossNodeDependencies.md)

* [Resource-versies](sxsResource.md)

* Pull-client (configuraties en resources) (Zie [instellen van een pull-client met behulp van configuratienamen](pullClientConfigNames.md))

* [Gedeeltelijke configuraties (pull & push)](partialConfigs.md)

* [Melden van pull-server](reportServer.md)

* MOF-versleuteling

* Logboekregistratie van gebeurtenissen

* Rapportage van Azure Automation DSC

* Resources die volledig functioneel zijn
  * [Archief](archiveResource.md)
  * [Omgeving](environmentResource.md)
  * [Bestand](fileResource.md)
  * [Log](logResource.md)
  * ProcessSet
  * [Register](registryResource.md)
  * [Script](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (Zie [geven cross-knooppunt afhankelijkheden](crossNodeDependencies.md))
  * WaitForAny (Zie [geven cross-knooppunt afhankelijkheden](crossNodeDependencies.md))
  * WaitForSome (Zie [geven cross-knooppunt afhankelijkheden](crossNodeDependencies.md))

* Resources die gedeeltelijk functioneel zijn
  * [Groep](groupResource.md)
  * GroupSet

  **Probleem:** hierboven resources mislukken als specifieke exemplaar tweemaal wordt genoemd (met dezelfde configuratie tweemaal)

  * [Service](serviceResource.md)
  * ServiceSet

  **Probleem:** werkt alleen voor (status)-service starten/stoppen. Mislukt, als een probeert te wijzigen van andere service-kenmerken zoals startuptype, referenties, beschrijving, enzovoort... De opgetreden fout is vergelijkbaar met:

  *Kan type [management.managementobject] niet vinden: Controleer of de assembly met dit type is geladen.*

* Resources die geen functionele
  * [Gebruiker](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a>DSC-functies niet beschikbaar op Nano Server

De volgende DSC-functies zijn momenteel niet beschikbaar op Nano Server:

* Ontsleutelen van MOF-document met versleutelde wachtwoord(en)
* Pull-Server kan niet op dit moment instellen van een pull-server op Nano Server
* Iets dat zich niet in de lijst met de functie werkt

## <a name="using-custom-dsc-resources-on-nano-server"></a>Met behulp van aangepaste DSC-resources op Nano Server

Als gevolg van een beperkte sets van Windows-API's en CLR-bibliotheken die beschikbaar is op Nano Server werken DSC-resources die op de volledige CLR-versie van Windows werken mogelijk niet op Nano Server.
Volledige end-to-end testen voordat u een aangepaste DSC-resources in een productieomgeving implementeert.

## <a name="see-also"></a>Zie ook
- [Aan de slag met Nano Server](https://technet.microsoft.com/library/mt126167.aspx)