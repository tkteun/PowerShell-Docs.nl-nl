---
title: Windows Power shell-activiteiten toevoegen aan de Visual Studio-werkset | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352169"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Windows PowerShell-activiteiten toevoegen aan de Visual Studio-werkset

Voordat u een Power shell-werk stroom met Workflow Designer maakt, moet u eerst de Power shell-activiteiten toevoegen aan de werkset in een toepassings project van een Visual Studio-werk stroom console. De volgende procedure laat zien hoe u de activiteiten van de assembly micro soft. Power shell. core. activities kunt toevoegen aan de Visual Studio-werkset.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Windows Power shell-activiteiten toevoegen aan de werkset

1. Maak een nieuw werk stroom console toepassings project in Visual Studio.

2. Klik in het menu **beeld** op **werkset**.

3. Voeg een nieuw tabblad in de werkset toe door met de rechter muisknop te klikken in de werkset en op **tabblad toevoegen**te klikken en het nieuwe tabblad een naam te geven, zoals Power shell-activiteiten.

   Door een tabblad toe te voegen, kunt u de Power shell-activiteiten groeperen, gescheiden van andere hulpprogram ma's in de werkset.

4. Klik op het tabblad nieuwe werkset op **items kiezen...** . Het dialoog venster **werkset-items kiezen** wordt weer gegeven.

5. Klik in het dialoog venster **werkset-items kiezen** op het tabblad **System. activities** .

6. Klik op **Bladeren**.

7. Ga naar de map%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e en dubbel klik op micro soft. Power shell. core. activities. dll.

8. Klik op **OK**. De activiteiten die zijn gedefinieerd door de assembly micro soft. Power shell. core. activities zijn nu beschikbaar in de werkset.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-werk stroom schrijven](./writing-a-windows-powershell-workflow.md)

[Een werk stroom maken met Windows Power shell-activiteiten](./creating-a-workflow-with-windows-powershell-activities.md)