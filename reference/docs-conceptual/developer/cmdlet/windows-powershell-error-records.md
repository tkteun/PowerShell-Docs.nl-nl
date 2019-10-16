---
title: Windows Power Shell-fout records | Microsoft Docs
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
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359118"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell-foutrecords

Cmdlets moeten worden door gegeven aan een [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object dat de fout voorwaarde voor afsluitende en niet-afsluit fouten identificeert.

Het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) bevat de volgende informatie:

- De uitzonde ring die de fout beschrijft. Vaak is dit een uitzonde ring die de cmdlet heeft onderschept en omgezet in een fout record. Elke fout record moet een uitzonde ring bevatten.

Als de cmdlet geen uitzonde ring heeft ondervangen, moet deze een nieuwe uitzonde ring maken en de uitzonderings klasse kiezen die het beste de fout voorwaarde beschrijft. U hoeft de uitzonde ring echter niet te genereren omdat deze toegankelijk is via de eigenschap [System. Management. Automation. ErrorRecord. Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) van het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

- Een fout-id die een bepaalde aanduiding levert die kan worden gebruikt voor diagnostische doel einden en Windows Power shell-scripts voor het afhandelen van specifieke fout voorwaarden met specifieke fout afhandeling. Elke fout record moet een fout-id bevatten (Zie fout-id).

- Een fout categorie die een algemene aanduiding biedt die kan worden gebruikt voor diagnostische doel einden. Elke fout record moet een fout categorie (Zie fout categorie) opgeven.

- Een optioneel vervangend fout bericht en een aanbevolen actie (Zie vervangings fout bericht).

- Optionele aanroep informatie over de cmdlet die de fout heeft veroorzaakt. Deze informatie wordt opgegeven door Windows Power shell (Zie aanroep bericht).

- Het doel object dat werd verwerkt toen de fout optrad. Dit kan het invoer object zijn of een ander object dat door de cmdlet werd verwerkt. Voor de opdracht `remove-item -recurse c:\somedirectory` kan de fout bijvoorbeeld een exemplaar zijn van een file info-object voor ' c:\somedirectory\lockedfile '. De gegevens van het doel object zijn optioneel.

## <a name="error-identifier"></a>Fout-id

Wanneer u een fout record maakt, geeft u een id op die de fout voorwaarde binnen uw cmdlet aanduidt. Windows Power shell combineert de doel-id met de naam van uw cmdlet om een volledig gekwalificeerde fout-id te maken. U kunt toegang krijgen tot de volledig gekwalificeerde fout-id via de eigenschap [System. Management. Automation. ErrorRecord. FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) van het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . De fout-id is niet beschikbaar. Het is alleen beschikbaar als onderdeel van de volledig gekwalificeerde fout-id.

Gebruik de volgende richt lijnen om fout-id's te genereren wanneer u fout records maakt:

- Stel fout-id's specifiek in op een fout voorwaarde. Richt de fout-id's in voor diagnostische doel einden en voor scripts die specifieke fout voorwaarden verwerken met specifieke fout afhandeling. Een gebruiker moet de fout-id kunnen gebruiken om de fout en de bron te identificeren. Fout-id's bieden ook rapportage voor specifieke fout voorwaarden van bestaande uitzonde ringen, zodat nieuwe uitzonderings subklassen niet vereist zijn.

- Over het algemeen wijst u verschillende fout-id's toe aan verschillende code paden. De voor delen van eind gebruikers van specifieke id's. Vaak is elk codepad dat [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aanroept een eigen id. Als regel definieert u een nieuwe id wanneer u een nieuwe sjabloon teken reeks definieert voor het fout bericht en vice versa. Gebruik het fout bericht niet als een id.

- Wanneer u code publiceert met een bepaalde fout-id, kunt u de semantiek van fouten met die id instellen voor uw volledige product Support Lifecycle. Hergebruik deze niet in een context die semantisch afwijkt van de oorspronkelijke context. Als de semantiek van deze fout is gewijzigd, maakt en gebruikt u een nieuwe id.

- U moet over het algemeen een bepaalde fout-id alleen gebruiken voor uitzonde ringen van een bepaald CLR-type. Als het type van de uitzonde ring of het type van het doel object wordt gewijzigd, maakt en gebruikt u vervolgens een nieuwe id.

- Kies tekst voor de fout-id die beknopt overeenkomt met de fout die u wilt rapporteren. Gebruik standaard .NET Framework naamgeving en kapitalisatie conventies. Gebruik geen spaties of lees tekens. Fout-id's niet lokaliseren.

- Genereer niet dynamisch fout-id's op een niet-reproduceer bare manier. Neem bijvoorbeeld geen fout gegevens op zoals een proces-ID. Fout-id's zijn alleen nuttig als ze overeenkomen met de fout-id's die worden weer gegeven door andere gebruikers die dezelfde fout situatie ondervinden.

## <a name="error-category"></a>Fout categorie

Wanneer u een fout record maakt, geeft u de categorie van de fout op met behulp van een van de constanten die zijn gedefinieerd door de inventarisatie [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) . Windows Power shell gebruikt de fout categorie om fout gegevens weer te geven wanneer gebruikers de variabele `$ErrorView` instellen op `"CategoryView"`.

Vermijd het gebruik van de constante [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified** . Als u informatie over de fout hebt of over de bewerking die de fout heeft veroorzaakt, kiest u de categorie die het beste de fout of de bewerking beschrijft, zelfs als de categorie geen perfecte overeenkomst is.

De informatie die wordt weer gegeven door Windows Power shell wordt aangeduid als de categorie-weergave teken reeks en wordt samengesteld op basis van de eigenschappen van de klasse [System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) . (Deze klasse wordt geopend via de eigenschap [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) .)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

De volgende lijst bevat de informatie die wordt weer gegeven:

- Categorie: een door Windows Power shell gedefinieerde [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) -constante.

- TargetName: standaard is dit de naam van het object dat door de cmdlet werd verwerkt toen de fout optrad. Of een andere cmdlet-gedefinieerde teken reeks.

- Target Type: standaard is dit het soort van het doel object. Of een andere cmdlet-gedefinieerde teken reeks.

- Activiteit: standaard is dit de naam van de cmdlet waarmee de fout record is gemaakt. Of een andere, door cmdlet gedefinieerde teken reeks.

- Reden: standaard het type uitzonde ring. Of een andere cmdlet-gedefinieerde teken reeks.

## <a name="replacement-error-message"></a>Vervangings fout bericht

Wanneer u een fout record voor een cmdlet ontwikkelt, wordt het standaard fout bericht van de fout opgehaald van de standaard bericht tekst in de eigenschap [System. Exception. Message](/dotnet/api/System.Exception.Message) . Dit is een alleen-lezen eigenschap waarvan de bericht tekst alleen bedoeld is voor fout opsporing (volgens de .NET Framework richt lijnen). We raden u aan een fout bericht te maken dat de standaard bericht tekst vervangt of uitbreidt. Maak het bericht meer gebruikers vriendelijk en specifiek voor de cmdlet.

Het vervangende bericht wordt gegeven door een [System. Management. Automation. error Details](/dotnet/api/System.Management.Automation.ErrorDetails) -object. Gebruik een van de volgende constructors van dit object omdat deze aanvullende lokalisatie gegevens bieden die kunnen worden gebruikt door Windows Power shell.

- [Error Details (cmdlet, String, String, object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): gebruik deze constructor als uw sjabloon reeks een resource teken reeks is in dezelfde assembly waarin de cmdlet is geïmplementeerd, of als u de sjabloon reeks wilt laden via een onderdrukking van de [ Methode System. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) .

- [Error Details (assembly, String, String, object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): gebruik deze constructor als de sjabloon teken reeks zich in een andere assembly bevindt en u deze niet laadt via een onderdrukking van [System. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Het vervangings bericht moet voldoen aan de .NET Framework ontwerp richtlijnen voor het schrijven van uitzonderings berichten met een klein verschil. In de richt lijnen staat dat uitzonderings berichten moeten worden geschreven voor ontwikkel aars. Deze vervangings berichten moeten worden geschreven voor de cmdlet-gebruiker.

Het vervangings fout bericht moet worden toegevoegd voordat de methoden [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) worden aangeroepen. Als u een vervangend bericht wilt toevoegen, stelt u de eigenschap [System. Management. Automation. ErrorRecord. error Details](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) van de fout record in. Wanneer deze eigenschap is ingesteld, wordt in Windows Power shell de eigenschap [System. Management. Automation. error Details. Message *](/dotnet/api/System.Management.Automation.ErrorDetails.Message) weer gegeven in plaats van de standaard bericht tekst.

## <a name="recommended-action-information"></a>Informatie over de aanbevolen actie

Het object [System. Management. Automation. error Details](/dotnet/api/System.Management.Automation.ErrorDetails) kan ook informatie bevatten over welke acties worden aanbevolen wanneer de fout optreedt.

## <a name="invocation-information"></a>Aanroep gegevens

Wanneer een cmdlet [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) gebruikt om een fout record te melden, voegt Windows Power shell automatisch informatie toe met een beschrijving van de opdracht die is aangeroepen toen de fout optrad. Deze informatie wordt verstrekt door een [System. Management. Automation. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) -object dat de naam bevat van de cmdlet die is aangeroepen door de opdracht, de opdracht zelf en informatie over de pijp lijn of het script. Deze eigenschap is alleen-lezen.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. error Details](/dotnet/api/System.Management.Automation.ErrorDetails)

[System. Management. Automation. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows Power Shell-fout rapportage](./error-reporting-concepts.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
