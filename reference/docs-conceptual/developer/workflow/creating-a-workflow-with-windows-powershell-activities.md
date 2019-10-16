---
title: Een werk stroom maken met Windows Power shell-activiteiten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352155"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Een werkstroom maken met Windows PowerShell-activiteiten

U kunt een Windows Power shell-werk stroom maken door activiteiten in de Visual Studio-werkset te selecteren en deze naar het Workflow Designer venster te slepen. Zie [Windows Power shell-activiteiten toevoegen aan de werkset van Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)voor meer informatie over het toevoegen van Windows Power shell-activiteiten aan de Visual Studio-werkset.

In de volgende procedures wordt beschreven hoe u een werk stroom maakt waarmee de domein status wordt gecontroleerd van een groep door de gebruiker opgegeven computers, wordt toegevoegd aan een domein als deze nog niet is gekoppeld en vervolgens de status opnieuw controleert.

### <a name="setting-up-the-project"></a>Het project instellen

1. Volg de procedure in [Windows Power shell-activiteiten toevoegen aan de Visual Studio-werkset](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) om een werk stroom project te maken en de activiteiten toe te voegen vanuit de [Microsoft. Power shell. activities](/dotnet/api/Microsoft.PowerShell.Activities) en [micro soft. Power shell. Management. activities ](/dotnet/api/Microsoft.PowerShell.Management.Activities)assembly's in de werkset.

2. Voeg System. Management. Automation, micro soft. Power shell. activities, System. Management, micro soft. Power shell. Management. activities en micro soft. Power shell. commands. Management toe aan het project als referentie verzamelingen.

### <a name="adding-activities-to-the-workflow"></a>Activiteiten toevoegen aan de werk stroom

1. Voeg een **reeks** activiteit toe aan de werk stroom.

2. Maak een argument met de naam `ComputerName` met het argument type `String[]`. Dit argument vertegenwoordigt de namen van de computers die moeten worden gecontroleerd en toegevoegd.

3. Maak een argument met de naam `DomainCred` van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Dit argument vertegenwoordigt de domein referenties van een domein account dat is gemachtigd om een computer toe te voegen aan het domein.

4. Maak een argument met de naam `MachineCred` van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Dit argument vertegenwoordigt de referenties van een beheerder op de computers om te controleren en samen te voegen.

5. Voeg een **ParallelForEach** -activiteit toe binnen de **reeks** activiteit. Voer `comp` en `ComputerName` in de tekst vakken in, zodat de lus door de elementen van de matrix `ComputerName` doorloopt.

6. Voeg een **sequentie** activiteit toe aan de hoofd tekst van de **ParallelForEach** -activiteit. Stel de eigenschap **DisplayName** van de reeks in op `JoinDomain`.

7. Voeg een **GetWmiObject** -activiteit toe aan de **JoinDomain** -reeks.

8. Bewerk de eigenschappen van de **GetWmiObject** -activiteit als volgt.

   |Eigenschap|Value|
   |--------------|-----------|
   |**Klasse**|"Win32_ComputerSystem"|
   |**PSComputerName**|Comp|
   |**PSCredential**|MachineCred|

9. Voeg een **AddComputer** -activiteit toe aan de **JoinDomain** -reeks na de activiteit **GetWmiObject** .

10. Bewerk de eigenschappen van de **AddComputer** -activiteit als volgt.

    |Eigenschap|Value|
    |--------------|-----------|
    |**ComputerName**|Comp|
    |**DomainCredential**|DomainCred|

11. Voeg een **RestartComputer** -activiteit toe aan de **JoinDomain** -reeks na de activiteit **AddComputer** .

12. Bewerk de eigenschappen van de **RestartComputer** -activiteit als volgt.

    |Eigenschap|Value|
    |--------------|-----------|
    |**ComputerName**|Comp|
    |**Referentie**|MachineCred|
    |**Zo**|Micro soft. Power shell. commands. WaitForServiceTypes. Power shell|
    |**Verkopers**|True|
    |Bewerking|True|
    |PSComputerName|{""}|

13. Voeg een **GetWmiObject** -activiteit toe aan de **JoinDomain** -reeks na de activiteit **RestartComputer** . Bewerk de eigenschappen zodanig dat deze hetzelfde zijn als de vorige **GetWmiObject** -activiteit.

    Wanneer u de procedures hebt voltooid, ziet het werk stroom ontwerp venster er als volgt uit.

    ![JoinDomain XAML in Workflow Designer @ no__t-1![JOINDOMAIN XAML in Workflow Designer](../media/joindomainworkflow.png "JoinDomainWorkflow")