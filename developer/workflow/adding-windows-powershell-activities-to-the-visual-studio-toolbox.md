---
title: Windows PowerShell-activiteiten toe te voegen aan de werkset van Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852106"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Windows PowerShell-activiteiten toevoegen aan de Visual Studio-werkset

Voordat u een PowerShell-werkstroom met Workflow Designer ontwerpt, moet u eerst de PowerShell-activiteiten toevoegen aan de werkset in een werkstroom met Visual Studio-consoletoepassingsproject. De volgende procedure beschrijft hoe de activiteiten van de assembly Microsoft.PowerShell.Core.Activities toevoegen aan de werkset van Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Windows PowerShell-activiteiten toe te voegen aan de werkset

1. Maak een nieuwe werkstroom consoletoepassingsproject in Visual Studio.

2. Op de **weergave** menu, klikt u op **werkset**.

3. Een nieuw tabblad in de werkset toevoegen door te klikken en met de rechtermuisknop op in de werkset **tabblad toevoegen**, en geef een naam, zoals "Activiteiten PowerShell" op het nieuwe tabblad.

   Een tabblad toe te voegen, kunt u de PowerShell-activiteiten gescheiden van andere hulpprogramma's in de werkset van de groep.

4. Klik op het nieuwe tabblad van de werkset **Items kiezen...** . De **Items in de werkset Kies** dialoogvenster wordt weergegeven.

5. In de **Items in de werkset Kies** dialoogvenster, klikt u op de **System.Activities** tabblad.

6. Klik op **Bladeren**.

7. Navigeer naar de map %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e en dubbelklikt u op Microsoft.PowerShell.Core.Activities.dll.

8. Klik op **OK**. De activiteiten die zijn gedefinieerd door de assembly Microsoft.PowerShell.Core.Activities zijn nu beschikbaar in de werkset.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-werkstroom](./writing-a-windows-powershell-workflow.md)

[Het maken van een werkstroom met Windows PowerShell-activiteiten](./creating-a-workflow-with-windows-powershell-activities.md)