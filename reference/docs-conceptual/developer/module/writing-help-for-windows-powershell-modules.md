---
title: Help voor Windows Power shell-modules schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352806"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Help voor Windows PowerShell-modules schrijven

Windows Power shell-modules kunnen Help-onderwerpen bevatten over de module en over de module leden, zoals cmdlets, providers, functies en scripts. Met de cmdlet `Get-Help` worden de Help-onderwerpen van de module weer gegeven in dezelfde indeling als de Help-informatie voor andere Windows Power shell-items. gebruikers gebruiken standaard `Get-Help` opdrachten om de Help-onderwerpen te ontvangen.

In dit document vindt u informatie over de indeling en de juiste plaatsing van de Help-onderwerpen over modules en suggesties voor richt lijnen voor de Help-inhoud van de module.

## <a name="types-of-module-help"></a>Typen module Help

Een module kan de volgende soorten Help bevatten.

- **Help voor cmdlets**. De Help-onderwerpen waarin cmdlets in een module worden beschreven, zijn XML-bestanden die gebruikmaken van het opdracht Help-schema

- **Help**voor de provider. De Help-onderwerpen waarin providers in een module worden beschreven, zijn XML-bestanden die gebruikmaken van het Help-schema van de provider.

- **Functie Help**. De Help-onderwerpen die functies in een module beschrijven, kunnen XML-bestanden zijn die gebruikmaken van de opdracht Help-schema of de Help-onderwerpen op basis van opmerkingen in de functie, of het script of de script module

- **Help voor scripts**. De Help-onderwerpen waarin scripts in een module worden beschreven, kunnen XML-bestanden zijn die gebruikmaken van de opdracht Help-schema of de Help-onderwerpen op basis van opmerkingen in de script-of script module.

- **Conceptuele informatie ("about")** . U kunt een conceptueel ("about") Help-onderwerp gebruiken om de module en de bijbehorende leden te beschrijven en te uitleggen hoe de leden kunnen worden gebruikt om taken uit te voeren. Conceptuele Help-onderwerpen zijn tekst bestanden met Unicode-code ring (UTF-8). De bestands naam moet de `about_<name>.help.txt` indeling gebruiken, zoals about_MyModule. Help. txt. Standaard bevat Windows Power Shell meer dan 100 van de volgende conceptuele informatie over Help-onderwerpen en worden deze ingedeeld zoals in het volgende voor beeld.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Plaatsing van module-Help

De cmdlet `Get-Help` zoekt naar de Help-onderwerpen van module bestanden in taalspecifieke submappen van de module directory.

In het volgende diagram van een mapstructuur ziet u bijvoorbeeld de locatie van de Help-onderwerpen voor de module SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> In het voor beeld vertegenwoordigt de tijdelijke aanduiding *\<para modulepath in >* een van de paden in de omgevings variabele `PSModulePath`, zoals $Home \documents\modules, $pshome \modules of een aangepast pad dat door de gebruiker is opgegeven.

## <a name="getting-module-help"></a>Help voor module ophalen

Wanneer een gebruiker een module in een sessie importeert, worden de Help-onderwerpen voor die module in de-sessie samen met de module geïmporteerd. U kunt de bestand met Help-onderwerpen weer geven in de waarde van de sleutel file list in het module manifest, maar Help-onderwerpen worden niet beïnvloed door de `Export-ModuleMember`-cmdlet.

U kunt Help-onderwerpen over modules in verschillende talen opgeven. Met de cmdlet `Get-Help` worden automatisch Help-onderwerpen over modules weer gegeven in de taal die is opgegeven voor de huidige gebruiker in het onderdeel land instellingen van het configuratie scherm. In Windows Vista en latere versies van Windows `Get-Help` zoekt naar de Help-onderwerpen in taalspecifieke submappen van de module-map, overeenkomstig de taal vereisten voor het instellen van Windows.

Met ingang van Windows Power Shell 3,0, met een `Get-Help`-opdracht voor een cmdlet of functie activeert automatisch importeren van de module. Met de cmdlet `Get-Help` wordt de inhoud van de Help-onderwerpen in de module direct weer gegeven.

Als de module geen Help-onderwerpen bevat en er geen Help-onderwerpen zijn voor de opdrachten in de module op de computer van de gebruiker, `Get-Help` automatisch gegenereerde Help weer gegeven. De automatisch gegenereerde Help omvat de opdracht syntaxis, para meters en invoer-en uitvoer typen, maar bevat geen beschrijvingen. De automatisch gegenereerde Help bevat tekst waarmee de gebruiker wordt gevraagd om de `Update-Help`-cmdlet te gebruiken voor het downloaden van de Help voor de opdracht van Internet of een bestands share. U wordt ook aangeraden de para meter **online** van de cmdlet `Get-Help` te gebruiken om de online versie van het Help-onderwerp op te halen.

## <a name="supporting-updatable-help"></a>Ondersteunende help die kan worden bijgewerkt

Gebruikers van Windows Power Shell 3,0 en latere versies van Windows Power shell kunnen bijgewerkte Help-bestanden downloaden en installeren voor een module van Internet of van een lokale bestands share. De `Update-Help`-en `Save-Help`-cmdlets verbergen de beheer gegevens van de gebruiker. Gebruikers voeren de `Update-Help` cmdlet uit en gebruiken vervolgens de `Get-Help` cmdlet om de nieuwste Help-bestanden voor de module te lezen bij de opdracht prompt van Windows Power shell. Gebruikers hoeven Windows of Windows Power shell niet opnieuw op te starten.

Gebruikers achter firewalls en verbindingen zonder Internet toegang kunnen ook gebruikmaken van de Bewerk bare Help. Beheerders met Internet toegang gebruiken de cmdlet `Save-Help` om de nieuwste Help-bestanden te downloaden en te installeren op een bestands share. Vervolgens gebruiken gebruikers de para meter **Path** van de cmdlet `Update-Help` om de nieuwste Help-bestanden van de bestands share op te halen.

Module auteurs kunnen Help-bestanden in de module toevoegen en de Help-informatie gebruiken voor het bijwerken van de Help-bestanden, of de Help-bestanden van de module weglaten en de Bewerk bare Help gebruiken om ze te installeren en bij te werken.

Zie [ondersteunende Help](./supporting-updatable-help.md)voor meer informatie over de Help die kan worden bijgewerkt.

## <a name="supporting-online-help"></a>Ondersteunende online help

Gebruikers die geen bijgewerkte Help-bestanden op hun computers kunnen of installeren, zijn vaak afhankelijk van de online versie van de Help-onderwerpen over modules. Met de para meter **online** van de cmdlet `Get-Help` opent u de online versie van een cmdlet of geavanceerde functie Help onderwerp voor de gebruiker in de standaard browser van Internet.

De cmdlet `Get-Help` gebruikt de waarde van de eigenschap **HelpUri** van de cmdlet of functie om de online versie van het Help-onderwerp te vinden.

Met ingang van Windows Power Shell 3,0 kunt u gebruikers helpen de online versie van cmdlet en Function Help-onderwerpen te vinden door het kenmerk HelpUri te definiëren voor de klasse cmdlet of de eigenschap **HelpUri** van het kenmerk **CmdletBinding** . De waarde van het kenmerk is de waarde van de eigenschap **HelpUri** van de cmdlet of functie.

Zie ondersteuning voor online- [Help](./supporting-online-help.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-module.md)

[Ondersteunende Help die kan worden bijgewerkt](./supporting-updatable-help.md)

[Online-Help ondersteunen](./supporting-online-help.md)