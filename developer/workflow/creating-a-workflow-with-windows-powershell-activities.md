---
title: Het maken van een werkstroom met Windows PowerShell-activiteiten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055424"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Een werkstroom maken met Windows PowerShell-activiteiten

U kunt een Windows PowerShell-werkstroom maken door te selecteren van activiteiten in de Visual Studio-werkset en ze naar de Workflow Designer-venster te slepen. Zie voor meer informatie over het toevoegen van Windows PowerShell-activiteiten naar de Visual Studio-werkset [Windows PowerShell-activiteiten toe te voegen aan de Visual Studio-werkset](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

De volgende procedures wordt beschreven hoe u een werkstroom maken die controleert de domeinstatus van een groep computers door gebruiker opgegeven, maakt u ze lid aan een domein als ze niet al zijn gekoppeld, en de status vervolgens opnieuw controleert.

### <a name="setting-up-the-project"></a>Instellen van het Project

1. Volg de procedure in [Windows PowerShell-activiteiten toe te voegen aan de Visual Studio-werkset](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) een werkstroom-project maken en toevoegen van de activiteiten van de [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) en [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assembly's aan de werkset.

2. System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities en Microsoft.PowerShell.Commands.Management garantie voor het project als verwijzing assembly's toevoegen.

### <a name="adding-activities-to-the-workflow"></a>Activiteiten toe te voegen aan de werkstroom

1. Voeg een **reeks** activiteit naar de werkstroom.

2. Maken van een argument met de naam `ComputerName` met een argumenttype van `String[]`. Dit argument geeft de namen van de computers om te controleren en te koppelen.

3. Maken van een argument met de naam `DomainCred` van het type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Dit argument vertegenwoordigt de domeinreferenties van een domeinaccount dat gemachtigd is op een computer toevoegen aan het domein.

4. Maken van een argument met de naam `MachineCred` van het type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Dit argument geeft de referenties van een beheerder op de computers om te controleren en te koppelen.

5. Voeg een **ParallelForEach** activiteit binnen de **reeks** activiteit. Voer `comp` en `ComputerName` in de tekstvakken zodat de lus de elementen van doorloopt de `ComputerName` matrix.

6. Voeg een **reeks** activiteit aan de hoofdtekst van de **ParallelForEach** activiteit. Stel de **DisplayName** eigenschap van de reeks aan `JoinDomain`.

7. Voeg een **GetWmiObject** activiteit in op de **JoinDomain** volgorde.

8. Bewerk de eigenschappen van de **GetWmiObject** activiteit als volgt te werk.

   |Eigenschap|Waarde|
   |--------------|-----------|
   |**Klasse**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Toevoegen een **AddComputer** activiteit naar de **JoinDomain** volgorde na de **GetWmiObject** activiteit.

10. Bewerk de eigenschappen van de **AddComputer** activiteit als volgt te werk.

    |Eigenschap|Waarde|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Toevoegen een **RestartComputer** activiteit naar de **JoinDomain** volgorde na de **AddComputer** activiteit.

12. Bewerk de eigenschappen van de **RestartComputer** activiteit als volgt te werk.

    |Eigenschap|Waarde|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Referentie**|MachineCred|
    |**voor**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Wacht|True|
    |PSComputerName|{""}|

13. Toevoegen een **GetWmiObject** activiteit naar de **JoinDomain** volgorde na de **RestartComputer** activiteit. Bewerk de eigenschappen niet dezelfde zijn als de vorige **GetWmiObject** activiteit.

    Wanneer u klaar bent met de procedures, de werkstroom ontwerpen-venster als volgt uitzien.

    ![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")