---
title: Windows PowerShell-fout registreert | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: f6f5e50c55b477cbbeeaaf4f3ea665d5dc07758c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067039"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell-foutrecords

Cmdlets moet slagen voor een [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object waarmee de foutstatus voor afsluitfouten als niet-afsluitfouten.

De [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object bevat de volgende informatie:

- De uitzondering die de fout wordt beschreven. Dit is vaak een uitzondering die de cmdlet onderschept en geconverteerd naar een foutrecord voor een. Elke foutrecord moet een uitzondering bevatten.

Als de cmdlet heeft een uitzondering niet werkelijk, moet een nieuwe uitzondering maken en kies de uitzonderingsklasse die het beste het probleem beschrijft. Echter, u hoeft niet op het gebruik van de uitzondering omdat deze kunnen worden geopend via de [System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) eigenschap van de [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)object.

- Een fout-id waarmee een aanduiding van de doelgroep die kan worden gebruikt voor diagnostische doeleinden en met Windows PowerShell-scripts voor het afhandelen van specifieke foutvoorwaarden met specifieke foutenhandlers. Elke foutrecord een fout-id moet bevatten (Zie fout-id).

- Een Foutcategorie die het biedt een algemene eenheidsaanduiding die kan worden gebruikt voor diagnostische doeleinden. Elke foutrecord een Foutcategorie moet opgeven (Zie Foutcategorie).

- Een optionele replacement foutbericht weergegeven en een aanbevolen actie (Zie vervanging foutbericht wordt weergegeven).

- Optionele aanroep informatie over de cmdlet die de fout heeft veroorzaakt. Deze informatie is opgegeven door de Windows PowerShell (Zie de aanroep bericht).

- Het doelobject dat wordt verwerkt als de fout is opgetreden. Dit wordt mogelijk het invoerobject of een ander object dat de verwerking van de cmdlet kan zijn. Bijvoorbeeld, voor de opdracht `remove-item -recurse c:\somedirectory`, de fout is mogelijk een exemplaar van een FileInfo-object voor 'c:\somedirectory\lockedfile'. De objectgegevens van het doel is optioneel.

## <a name="error-identifier"></a>Fout-id

Wanneer u een foutrecord voor een maakt, geeft u een id waarmee wordt aangegeven van het probleem binnen uw cmdlet. Windows PowerShell en de betreffende id combineert met de naam van de cmdlet voor het maken van een volledig gekwalificeerde fout-id. De volledig gekwalificeerde fout-id is toegankelijk via de [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) eigenschap van de [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)object. De fout-id is niet beschikbaar op zichzelf. Deze beschikbaar is uitsluitend als onderdeel van de volledig gekwalificeerde fout-id.

Gebruik de volgende richtlijnen voor het genereren van fout-id's bij het maken van foutrecords:

- Fout-id's specifieke aanbrengen in een foutstatus. Richt de fout-id's voor diagnostische doeleinden en scripts die specifieke foutvoorwaarden met specifieke foutenhandlers verwerkt. Een gebruiker zou het mogelijk de fout-id gebruiken om de fout en de bron te identificeren. Fout-id's ook inschakelen rapportage voor specifieke foutvoorwaarden van bestaande uitzonderingen zodat nieuwe uitzondering subklassen niet vereist zijn.

- In het algemeen verschillende fout-id's toewijzen aan andere codepaden. De eindgebruiker profiteren van specifieke id's. Vaak, elk codepad die worden aangeroepen [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) heeft zijn eigen id. Als een regel, definieert u een nieuwe id bij het definiëren van een tekenreeks in een nieuwe sjabloon voor het foutbericht en vice versa. Gebruik het foutbericht niet als een id.

- Wanneer u code met behulp van een bepaalde fout-id publiceert, moet u instellen dat de semantiek van fouten met deze id voor uw volledige product lifecycle ondersteunen. Niet opnieuw gebruiken in een context die semantisch verschilt van de oorspronkelijke context. Als de semantiek van deze fout wilt wijzigen, maak en gebruik vervolgens een nieuwe id.

- U moet een bepaalde fout-id in het algemeen alleen voor uitzonderingen van een bepaald CLR-type gebruiken. Als het type van de uitzondering of het type van het doelobject wordt gewijzigd, maakt en gebruikt u een nieuwe id.

- Kies tekst voor de fout-id die bondig overeenkomt met de fout die u wilt rapporteren. Standaard .NET Framework-conventies voor naamgeving van hoofdletters en kleine letters gebruiken. Gebruik geen spaties of leestekens. Fout-id's niet lokaliseren.

- Dynamisch genereren geen fout-id's in een niet-reproduceerbare manier. Foutinformatie, zoals een proces-id bijvoorbeeld niet is opgenomen Fout-id's zijn alleen nuttig als ze overeenkomen met de fout-id's zichtbaar voor andere gebruikers die de dezelfde fout zich voordoet.

## <a name="error-category"></a>Foutcategorie

Wanneer u een foutrecord voor een maakt, geeft u de categorie van de fout met behulp van een van de constanten zijn gedefinieerd door de [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) opsomming. Windows PowerShell maakt gebruik van de Foutcategorie informatie over de fout weergegeven wanneer gebruikers de `$ErrorView` variabele `"CategoryView"`.

Vermijd het gebruik van de [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) constante. Als u alle informatie over de fout of de bewerking die de fout heeft veroorzaakt hebt, kiest u de categorie die het beste de fout, of de bewerking beschrijft, zelfs als de categorie niet een perfecte is.

De informatie die wordt weergegeven door Windows PowerShell is de categorie-view-tekenreeks genoemd en wordt samengesteld uit de eigenschappen van de [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) klasse. (Deze klasse wordt geopend via de fout [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) eigenschap.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

De volgende lijst bevat de informatie die wordt weergegeven:

- Categorie: Een Windows PowerShell-gedefinieerd [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) constante.

- Doelnaam: Standaard de naam van het object de cmdlet is verwerking wanneer de fout is opgetreden. Of een andere cmdlet gedefinieerde tekenreeks.

- TargetType: Standaard wordt het type van het doelobject. Of een andere cmdlet gedefinieerde tekenreeks.

- Activiteit: Standaard de naam van de cmdlet die de foutrecord is gemaakt. Of een andere cmdlet-tekenreeks is gedefinieerd.

- Reden: Standaard wordt het uitzonderingstype. Of een andere cmdlet gedefinieerde tekenreeks.

## <a name="replacement-error-message"></a>Vervanging van foutbericht

Wanneer u een foutrecord met voor een cmdlet ontwikkelt, het standaardfoutbericht voor de fout die afkomstig is van de standaard berichttekst in de [System.Exception.Message](/dotnet/api/System.Exception.Message) eigenschap. Dit is een alleen-lezen eigenschap waarvan de berichttekst is alleen bedoeld voor foutopsporing (op basis van de richtlijnen voor .NET Framework). U wordt aangeraden dat u een foutmelding krijgen dat vervangt of de standaard berichttekst verbetert maken. Controleer het bericht meer gebruiksvriendelijker en meer specifiek aan de cmdlet.

Het bericht vervanging wordt geleverd door een [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) object. Gebruik een van de volgende constructoren van dit object omdat ze voorzien in extra lokalisatie-informatie die kan worden gebruikt door Windows PowerShell.

- [ErrorDetails.ErrorDetails (Cmdlet, String, String, Object\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Deze constructor gebruiken als de tekenreeks van uw sjabloon is een resourcetekenreeks in dezelfde assembly waarin de cmdlet is geïmplementeerd of als u wilt laden van de sjabloon-tekenreeks met een onderdrukking van de [System.Management.Automation.Cmdlet.GetResourceString ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) methode.

- [ErrorDetails.ErrorDetails (Assembly, String, String, Object\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Deze constructor gebruiken als de sjabloon-tekenreeks in een ander assembly is en u deze niet via een onderdrukking van laden kan [System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Het bericht vervanging moet voldoen aan de richtlijnen voor het ontwerpen van .NET Framework voor het schrijven van berichten met een klein verschil uitzondering. De status van de richtlijnen die uitzondering tekstberichten worden geschreven voor ontwikkelaars. Deze vervanging tekstberichten worden geschreven voor de cmdlet-gebruiker.

Het foutbericht vervanging moet worden toegevoegd voordat de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methoden worden genoemd. Instellen als u wilt toevoegen een vervangende-bericht, de [System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) eigenschap van de foutrecord. Als deze eigenschap is ingesteld, Windows PowerShell wordt weergegeven de [System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) eigenschap in plaats van de standaard berichttekst.

## <a name="recommended-action-information"></a>Aanbevolen actie-informatie

De [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) object biedt ook informatie over acties die worden aanbevolen als de fout optreedt.

## <a name="invocation-information"></a>Aanroep informatie

Wanneer een cmdlet gebruikt [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) voor het rapporteren van een foutrecord, Windows PowerShell informatie over de opdracht die is aangeroepen wanneer de fout is opgetreden worden automatisch toegevoegd. Deze informatie wordt verstrekt door een [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) object met de naam van de cmdlet die door de opdracht de opdracht zelf is aangeroepen en informatie over de pijplijn of het script. Deze eigenschap is alleen-lezen.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell die fouten rapporteren](./error-reporting-concepts.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
