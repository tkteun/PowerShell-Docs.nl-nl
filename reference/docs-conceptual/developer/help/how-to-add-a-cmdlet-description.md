---
title: Een cmdlet-beschrijving toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353317"
---
# <a name="how-to-add-a-cmdlet-description"></a>Een cmdlet-beschrijving toevoegen

In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de sectie Beschrijving van de Help van de cmdlet. In het Help-bestand wordt deze inhoud toegevoegd aan het opdracht knooppunt voor elke cmdlet.

> [!NOTE]
> Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden. Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.

### <a name="to-add-a-description"></a>Een beschrijving toevoegen

- Begin met het uitleggen van de basis functies van de cmdlet in meer detail. In veel gevallen kunt u de termen die worden gebruikt in de naam van de cmdlet uitleggen en niet-bekende concepten illustreren met een voor beeld. Als met de cmdlet bijvoorbeeld gegevens worden toegevoegd aan een bestand, wordt uitgelegd dat er gegevens aan het einde van een bestaand bestand worden toegevoegd.

- Als u alle functies van de cmdlet wilt vinden, controleert u de lijst met para meters. Beschrijf de primaire functie van de cmdlet en voeg vervolgens andere functies en onderdelen toe. Als de hoofd functie van de cmdlet bijvoorbeeld één eigenschap wijzigt, maar de cmdlet alle eigenschappen kan wijzigen, doet u dat in de gedetailleerde beschrijving. Als met de cmdlet-para meters de gebruikers informatie op verschillende manieren kunnen vragen, moet u deze uitleggen.

- Neem naast het duidelijke gebruik ook informatie op over manieren waarop gebruikers de cmdlet kunnen gebruiken. U kunt bijvoorbeeld het object gebruiken dat door de `Get-Host`-cmdlet wordt opgehaald om de kleur van tekst in het Windows Power shell-opdracht venster te wijzigen.

  Voor beeld: met de cmdlet `Get-Acl` worden objecten opgehaald die de security descriptor van een bestand of resource vertegenwoordigen. De security descriptor bevat de toegangs beheer lijsten (Acl's) van de resource. In de ACL worden de machtigingen opgegeven die gebruikers en gebruikers groepen hebben om toegang te krijgen tot de resource.

- In de gedetailleerde beschrijving wordt de cmdlet beschreven, maar het mag niet de concepten beschrijven die de cmdlet gebruikt. Concept definities plaatsen in aanvullende notities.

## <a name="see-also"></a>Zie ook

[Windows Power shell SDK](../windows-powershell-reference.md)
