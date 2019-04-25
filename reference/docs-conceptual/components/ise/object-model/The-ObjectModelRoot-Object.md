---
ms.date: 08/25/2017
keywords: PowerShell-cmdlet
title: Het ObjectModelRoot-object
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086779"
---
# <a name="the-objectmodelroot-object"></a>Het ObjectModelRoot-object

De **$psISE** object, dat het basis-principal-object in Windows PowerShell® Integrated Scripting Environment (ISE is) is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
In dit onderwerp beschrijft de eigenschappen van de **ObjectModelRoot** object.

## <a name="properties"></a>Eigenschappen

### <a name="currentfile"></a>CurrentFile

> In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die het bestand dat is gekoppeld aan deze hostobject dat de focus heeft opgehaald.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de PowerShell-tabblad opgehaald die heeft de focus.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de momenteel zichtbare Windows PowerShell ISE-invoegtoepassing hulpprogramma opgehaald die bevindt zich in de horizontale taakvenster aan de onderkant van de editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de momenteel zichtbare Windows PowerShell ISE-invoegtoepassing hulpprogramma opgehaald die bevindt zich in de verticale taakvenster aan de rechterkant van de editor.

### <a name="options"></a>Opties

> In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de verschillende opties opgehaald die kunt in Windows PowerShell ISE wijzigen.

### <a name="powershelltabs"></a>PowerShellTabs

> In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de verzameling van de PowerShell-tabbladen die geopend in Windows PowerShell ISE zijn opgehaald. Dit object bevat standaard een PowerShell-tabblad. U kunt echter meer PowerShell-tabbladen toevoegen aan dit object met behulp van scripts of met behulp van de menu's in Windows PowerShell ISE.

## <a name="see-also"></a>Zie ook

- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)