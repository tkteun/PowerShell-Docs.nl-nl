---
ms.date: 04/10/2020
ms.topic: reference
title: Help voor PowerShell-modules schrijven
description: Help voor PowerShell-modules schrijven
ms.openlocfilehash: 3bef45c0dd8a7e63bc419bb3e5a7a1783810105b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654649"
---
# <a name="writing-help-for-powershell-modules"></a>Help voor PowerShell-modules schrijven

Power shell-modules kunnen Help-onderwerpen bevatten over de module en over de module leden, zoals cmdlets, providers, functies en scripts. De `Get-Help` cmdlet geeft de Help-onderwerpen van de module weer in dezelfde indeling als de Help-informatie voor andere Power shell-items en gebruikers gebruiken standaard `Get-Help` opdrachten om de Help-onderwerpen te ontvangen.

In dit document vindt u informatie over de indeling en de juiste plaatsing van de Help-onderwerpen over modules en suggesties voor richt lijnen voor de Help-inhoud van de module.

## <a name="types-of-module-help"></a>Typen module Help

Een module kan de volgende soorten Help bevatten.

- **Help voor cmdlets**. De Help-onderwerpen waarin cmdlets in een module worden beschreven, zijn XML-bestanden die gebruikmaken van het opdracht Help-schema

- **Help** voor de provider. De Help-onderwerpen waarin providers in een module worden beschreven, zijn XML-bestanden die gebruikmaken van het Help-schema van de provider.

- **Functie Help**. De Help-onderwerpen die functies in een module beschrijven, kunnen XML-bestanden zijn die gebruikmaken van de opdracht Help-schema of de Help-onderwerpen op basis van opmerkingen in de functie, of het script of de script module

- **Help voor scripts**. De Help-onderwerpen waarin scripts in een module worden beschreven, kunnen XML-bestanden zijn die gebruikmaken van de opdracht Help-schema of de Help-onderwerpen op basis van opmerkingen in de script-of script module.

- **Conceptuele informatie ("about")**. U kunt een conceptueel ("about") Help-onderwerp gebruiken om de module en de bijbehorende leden te beschrijven en te uitleggen hoe de leden kunnen worden gebruikt om taken uit te voeren.
  Conceptuele Help-onderwerpen zijn tekst bestanden met Unicode-code ring (UTF-8). De bestands naam moet de `about_<name>.help.txt` indeling gebruiken, bijvoorbeeld `about_MyModule.help.txt` . Power shell bevat standaard meer dan 100 van de volgende conceptuele informatie over Help-onderwerpen en ze zijn ingedeeld zoals in het volgende voor beeld.

  ```Output
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
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

Alle schema bestanden kunnen worden gevonden in de `$PSHOME\Schemas\PSMaml` map.

## <a name="placement-of-module-help"></a>Plaatsing van module-Help

De `Get-Help` cmdlet zoekt naar de Help-onderwerpen van module bestanden in taalspecifieke submappen van de module directory.

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
> In het voor beeld `<ModulePath>` vertegenwoordigt de tijdelijke aanduiding een van de paden in de `PSModulePath` omgevings variabele, zoals `$HOME\Documents\Modules` , `$PSHOME\Modules` , of een aangepast pad dat door de gebruiker is opgegeven.

## <a name="getting-module-help"></a>Help voor module ophalen

Wanneer een gebruiker een module in een sessie importeert, worden de Help-onderwerpen voor die module in de-sessie samen met de module geïmporteerd. U kunt de bestand met Help-onderwerpen weer geven in de waarde van de sleutel file list in het module manifest, maar Help-onderwerpen worden niet beïnvloed door de `Export-ModuleMember` cmdlet.

U kunt Help-onderwerpen over modules in verschillende talen opgeven. Met de `Get-Help` cmdlet worden automatisch Help-onderwerpen over modules weer gegeven in de taal die is opgegeven voor de huidige gebruiker in het onderdeel land instellingen van het configuratie scherm. In Windows Vista en latere versies van Windows zoekt u naar `Get-Help` de Help-onderwerpen in taalspecifieke submappen van de module directory in overeenstemming met de taal vereisten voor het uitvoeren van Windows.

Vanaf Power Shell 3,0 voert een `Get-Help` opdracht uit voor een cmdlet of functie activeert automatisch het importeren van de module. Met de `Get-Help` cmdlet wordt direct de inhoud van de Help-onderwerpen in de module weer gegeven.

Als de module geen Help-onderwerpen bevat en er geen Help-onderwerpen zijn voor de opdrachten in de module op de computer van de gebruiker, `Get-Help` wordt automatisch gegenereerde Help weer gegeven. De automatisch gegenereerde Help omvat de opdracht syntaxis, para meters en invoer-en uitvoer typen, maar bevat geen beschrijvingen. De automatisch gegenereerde Help bevat tekst waarmee de gebruiker wordt gevraagd om de `Update-Help` cmdlet te gebruiken voor het downloaden van de Help voor de opdracht van Internet of een bestands share. U wordt ook aangeraden de **online** -para meter van de `Get-Help` cmdlet te gebruiken om de online versie van het Help-onderwerp op te halen.

## <a name="supporting-updatable-help"></a>Ondersteunende help die kan worden bijgewerkt

Gebruikers van Power Shell 3,0 en latere versies van Power shell kunnen bijgewerkte Help-bestanden downloaden en installeren voor een module van Internet of van een lokale bestands share. De `Update-Help` `Save-Help` cmdlets en verbergen de beheer gegevens van de gebruiker. Gebruikers voeren de `Update-Help` cmdlet uit en gebruiken vervolgens de `Get-Help` cmdlet om de nieuwste Help-bestanden voor de module te lezen in de Power shell-opdracht prompt.
Gebruikers hoeven Windows of Power shell niet opnieuw op te starten.

Gebruikers achter firewalls en verbindingen zonder Internet toegang kunnen ook gebruikmaken van de Bewerk bare Help.
Beheerders met Internet toegang gebruiken de `Save-Help` cmdlet om de nieuwste Help-bestanden te downloaden en te installeren op een bestands share. Vervolgens gebruiken gebruikers de para meter **Path** van de `Update-Help` cmdlet om de nieuwste Help-bestanden van de bestands share op te halen.

Module auteurs kunnen Help-bestanden in de module toevoegen en de Help-informatie gebruiken voor het bijwerken van de Help-bestanden, of de Help-bestanden van de module weglaten en de Bewerk bare Help gebruiken om ze te installeren en bij te werken.

Zie [ondersteunende Help](./supporting-updatable-help.md)voor meer informatie over de Help die kan worden bijgewerkt.

## <a name="supporting-online-help"></a>Ondersteunende online help

Gebruikers die geen bijgewerkte Help-bestanden op hun computers kunnen of installeren, zijn vaak afhankelijk van de online versie van de Help-onderwerpen over modules. Met de para meter **online** van de `Get-Help` cmdlet opent u de online versie van een cmdlet of geavanceerde functie Help onderwerp voor de gebruiker in de standaard browser van Internet.

De `Get-Help` cmdlet gebruikt de waarde van de eigenschap **HelpUri** van de cmdlet of functie om de online versie van het Help-onderwerp te vinden.

Vanaf Power Shell 3,0 kunt u gebruikers helpen bij het vinden van de online versie van cmdlet-en Function Help-onderwerpen door het kenmerk HelpUri te definiëren voor de klasse cmdlet of de eigenschap **HelpUri** van het kenmerk **CmdletBinding** . De waarde van het kenmerk is de waarde van de eigenschap **HelpUri** van de cmdlet of functie.

Zie ondersteuning voor online- [Help](./supporting-online-help.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Een PowerShell-module schrijven](../module/writing-a-windows-powershell-module.md)

[Ondersteunende help die kan worden bijgewerkt](./supporting-updatable-help.md)

[Ondersteunende online help](./supporting-online-help.md)
