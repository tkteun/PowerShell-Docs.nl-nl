---
title: Een cmdlet-beschrijving toevoegen
ms.date: 09/13/2016
ms.openlocfilehash: 2b98c4cefc3a55eccfeb7eba5a290e7d93a6088b
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893234"
---
# <a name="how-to-add-a-cmdlet-description"></a>Een cmdlet-beschrijving toevoegen

In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de sectie **Beschrijving** van de Help van de cmdlet. In het Help-bestand wordt deze inhoud toegevoegd aan het **opdracht** knooppunt voor elke cmdlet.

> [!NOTE]
> Als u een volledig overzicht van een Help-bestand wilt weer geven, opent u een van de `dll-Help.xml` bestanden die zich in de installatie directory van Power shell bevinden. Het `Microsoft.PowerShell.Commands.Management.dll-Help.xml` bestand bevat bijvoorbeeld inhoud voor verschillende Power shell-cmdlets.

### <a name="to-add-a-description"></a>Een beschrijving toevoegen

- Begin met het uitleggen van de basis functies van de cmdlet in meer detail. In veel gevallen kunt u de termen die worden gebruikt in de naam van de cmdlet uitleggen en niet-bekende concepten illustreren met een voor beeld. Als met de cmdlet bijvoorbeeld gegevens worden toegevoegd aan een bestand, wordt uitgelegd dat er gegevens aan het einde van een bestaand bestand worden toegevoegd.

- Als u alle functies van de cmdlet wilt vinden, controleert u de lijst met para meters. Beschrijf de primaire functie van de cmdlet en voeg vervolgens andere functies en onderdelen toe. Als de hoofd functie van de cmdlet bijvoorbeeld één eigenschap wijzigt, maar de cmdlet alle eigenschappen kan wijzigen, doet u dat in de gedetailleerde beschrijving. Als met de cmdlet-para meters de gebruikers informatie op verschillende manieren kunnen vragen, moet u deze uitleggen.

- Neem naast het duidelijke gebruik ook informatie op over manieren waarop gebruikers de cmdlet kunnen gebruiken. U kunt bijvoorbeeld het object dat door de cmdlet wordt `Get-Host` opgehaald, gebruiken om de kleur van tekst in het Windows Power shell-opdracht venster te wijzigen.

  Voor beeld: de `Get-Acl` cmdlet haalt objecten op die de security descriptor van een bestand of resource vertegenwoordigen. De security descriptor bevat de toegangs beheer lijsten (Acl's) van de resource. In de ACL worden de machtigingen opgegeven die gebruikers en gebruikers groepen hebben om toegang te krijgen tot de resource.

- In de gedetailleerde beschrijving wordt de cmdlet beschreven, maar het mag niet de concepten beschrijven die de cmdlet gebruikt. Concept definities plaatsen in aanvullende notities.

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
