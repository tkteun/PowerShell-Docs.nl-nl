---
title: Schrijfhulp voor Windows PowerShell-Modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845456"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Help voor Windows PowerShell-modules schrijven

Windows PowerShell-modules kunnen Help-onderwerpen over de module en de leden van de module, zoals cmdlets, providers, functies en scripts bevatten. De `Get-Help` cmdlet wordt de module Help-onderwerpen in dezelfde indeling als deze geeft Help weer voor andere Windows PowerShell-items en gebruikers standaard gebruiken `Get-Help` opdrachten voor het ophalen van de Help-onderwerpen.

Dit document wordt uitgelegd voor de indeling en de juiste plaatsing van module Help-onderwerpen en er wordt verwezen naar richtlijnen voor de module Help-inhoud.

## <a name="types-of-module-help"></a>Typen Help bij integratiemodule

Een module kan de volgende typen van Help-informatie bevatten.

- **Help van de cmdlet**. De Help-onderwerpen waarin wordt beschreven cmdlets in een module zijn XML-bestanden die met de opdracht help schema

- **Provider Help**. De Help-onderwerpen waarin wordt beschreven providers in een module zijn XML-bestanden die gebruikmaken van de provider hulp schema.

- **Functie Help**. De Help-onderwerpen waarin wordt beschreven functies in een module mag XML-bestanden die met de opdracht help schema of op basis van een opmerking Help-onderwerpen in de functie of het script of scriptmodule

- **Help script**. De Help-onderwerpen waarin wordt beschreven scripts in een module kan het XML-bestanden die met de opdracht help schema of Help-onderwerpen op basis van een opmerking in het script of de scriptmodule zijn.

- **Conceptuele ('About'), Help**. U kunt een conceptuele ('about'), Help-onderwerp gebruiken om te beschrijven van de module en de bijbehorende leden en waarin wordt uitgelegd hoe de leden kunnen samen worden gebruikt om uit te voeren taken. Algemene Help-onderwerpen zijn tekstbestanden met Unicode (UTF-8)-codering. De bestandsnaam moet gebruiken de `about_<name>.help.txt` indeling, zoals about_MyModule.help.txt. Standaard Windows PowerShell bevat meer dan 100 van deze concepten over het Help-onderwerpen en ze zijn opgemaakt als in het volgende voorbeeld.

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

## <a name="placement-of-module-help"></a>Plaatsing van de Help bij integratiemodule

De `Get-Help` cmdlet module Help-Onderwerpbestanden in submappen van de modulemap taalspecifieke zoekt.

Bijvoorbeeld, ziet het volgende diagram voor directory-structuur u de locatie van de Help-onderwerpen voor de module SampleModule.

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
> In het voorbeeld wordt de  *\<ModulePath >* een tijdelijke aanduiding voor een van de paden in de `PSModulePath` omgevingsvariabele, zoals $home\Documents\Modules, $pshome\Modules of een aangepast pad dat de gebruiker opgeeft.

## <a name="getting-module-help"></a>Module Help opvragen

Wanneer een gebruiker een module wordt geïmporteerd in een sessie, wordt de Help-onderwerpen voor die module worden geïmporteerd in de sessie, samen met de module. U kunt de Help-onderwerp-bestanden in de waarde van de sleutel FileList in de module-manifest weergeven, maar het Help-onderwerpen worden niet beïnvloed door de `Export-ModuleMember` cmdlet.

U kunt de module Help-onderwerpen in verschillende talen opgeven. De `Get-Help` cmdlet module Help-onderwerpen automatisch weergegeven in de taal die is opgegeven voor de huidige gebruiker van het onderdeel Landinstellingen in het Configuratiescherm. In Windows Vista en latere versies van Windows, `Get-Help` zoekt naar de Help-onderwerpen in taalspecifieke submappen van de modulemap in overeenstemming met de taal terugval standaarden die zijn vastgelegd voor Windows.

In Windows PowerShell 3.0 wordt uitgevoerd vanaf een `Get-Help` opdracht voor een cmdlet of de functie activeert automatisch importeren van de module. De `Get-Help` cmdlet wordt de inhoud van de help-onderwerpen onmiddellijk weergegeven in de module.

Als de module geen help-onderwerpen bevat en er geen help-onderwerpen voor de opdrachten in de module op de computer van de gebruiker zijn, `Get-Help` wordt automatisch gegenereerde help weergegeven. De automatisch gegenereerde help bevat de syntaxis, parameters en invoer- en -typen, maar bevat geen beschrijvingen. De help voor het automatisch gegenereerde bevat tekst waarmee de gebruiker om te proberen te gebruiken de `Update-Help` cmdlet help voor de opdracht downloaden vanaf Internet of een bestandsshare. Dit ook is de aanbevolen met behulp van de **Online** parameter van de `Get-Help` cmdlet om op te halen van de online versie van het help-onderwerp.

## <a name="supporting-updatable-help"></a>Ondersteunende help die kan worden bijgewerkt

Gebruikers van Windows PowerShell 3.0 en latere versies van Windows PowerShell kunnen downloaden en installeren van bijgewerkte help-bestanden voor een module van het Internet of vanaf een lokaal bestand-share. De `Update-Help` en `Save-Help` cmdlets verbergen de details van de management van de gebruiker. Gebruikers voeren de `Update-Help` cmdlet en gebruik vervolgens de `Get-Help` cmdlet voor het lezen van de meest recente help-bestanden voor de module bij de opdrachtprompt van Windows PowerShell. Gebruikers hoeven niet opnieuw opstarten van Windows of Windows PowerShell.

Gebruikers achter firewalls en die geen toegang tot Internet kunnen gebruiken bij te werken Help, evenals. Beheerders met Internet gebruik toegang tot de `Save-Help` cmdlet om te downloaden en installeren van de meest recente help-bestanden naar een bestandsshare. Vervolgens gebruikt u gebruikers de **pad** parameter van de `Update-Help` cmdlet om op te halen van de meest recente help-bestanden van de bestandsshare.

Auteurs kunnen help-bestanden opnemen in de module en gebruik bij te werken Help bijwerken van de help-bestanden of weglaten help-bestanden van de module en gebruik bij te werken Help zowel om te installeren en deze kunnen worden bijgewerkt.

Zie voor meer informatie over het bij te werken Help [ondersteunende bij te werken Help](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Ondersteunende online help

Gebruikers die niet of Installeer geen bijgewerkte help-bestanden op hun computers is vaak afhankelijk van de online versie van de module help-onderwerpen zijn. De **Online** parameter van de `Get-Help` cmdlet opent de online versie van een cmdlet of een geavanceerde functie help-onderwerp voor de gebruiker in de standaardbrowser van het Internet.

De `Get-Help` cmdlet wordt de waarde van de **HelpUri** eigenschap van de cmdlet of de functie voor het vinden van de online versie van het help-onderwerp.

Vanaf Windows PowerShell 3.0, kunt u gebruikers de online versie van de cmdlet en de functie help-onderwerpen vinden door te definiëren van het kenmerk HelpUri van de cmdlet-klasse of de **HelpUri** eigenschap van de **CmdletBinding** kenmerk. De waarde van het kenmerk is de waarde van de **HelpUri** eigenschap van de cmdlet of functie.

Zie voor meer informatie, [ondersteunende Online Help](./supporting-online-help.md).

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)

[Ondersteunende Help die kan worden bijgewerkt](./supporting-updatable-help.md)

[Ondersteunende Online Help](./supporting-online-help.md)