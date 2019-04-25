---
title: Achtergrondtaken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068675"
---
# <a name="background-jobs"></a>Achtergrondtaken

Cmdlets hun actie kunt uitvoeren, intern of als een Windows PowerShell*achtergrondtaak*. Wanneer een cmdlet wordt uitgevoerd als achtergrondtaak, de bewerkingen worden asynchroon in een eigen thread gescheiden van de pijplijn-thread die door de cmdlet wordt gebruikt. Vanuit het gebruikersperspectief, wanneer een cmdlet wordt uitgevoerd als achtergrondtaak, retourneert de opdrachtprompt onmiddellijk, zelfs als de taak een uitgebreide hoeveelheid tijd in beslag neemt en de gebruikers zonder onderbreking houden toegang terwijl de taak wordt uitgevoerd.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Achtergrondtaken, onderliggende taken en de opslagplaats van de taak

Het taakobject dat wordt geretourneerd door de cmdlets die ondersteuning bieden voor achtergrondtaken definieert de taak. (De [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet retourneert ook een taakobject.) De naam van de taak, een id die wordt gebruikt om op te geven van de taak, de informatie over de status en de onderliggende taken zijn opgenomen in deze definitie. De taak uitvoeren niet een van de hoeveelheid werk. Elke achtergrondtaak heeft ten minste één onderliggende taak, omdat de onderliggende taak het echte werk voert. Wanneer u een cmdlet uitvoert, zodat het werk wordt uitgevoerd als achtergrondtaak, de cmdlet de taak en de onderliggende taken moet toevoegen aan een algemene opslagplaats, aangeduid als de *taak opslagplaats*.

Zie de volgende onderwerpen voor meer informatie over hoe achtergrondtaken worden verwerkt op de opdrachtregel:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Schrijven van een Cmdlet die wordt uitgevoerd als een achtergrondtaak

Voor het schrijven van een cmdlet die kan worden uitgevoerd als achtergrondtaak, moet u de volgende taken uitvoeren:

- Definieer een `asJob` overschakelen parameter zodat de gebruiker kunt vervolgens beslissen of de cmdlet uitvoeren als achtergrondtaak.

- Maken van een object dat is afgeleid van de [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klasse. Dit object is een aangepaste taak of een taakobject dat is geleverd door Windows PowerShell, zoals een [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.

- Een verwerkingsmethode voor de van de record, Voeg een `if` instructie waarmee wordt gedetecteerd of de cmdlet moet worden uitgevoerd als achtergrondtaak.

- Voor taakobjecten van de aangepaste, de taakklasse te implementeren.

- Retourneert de juiste objecten, afhankelijk van of de cmdlet wordt uitgevoerd als achtergrondtaak.

Zie voor een codevoorbeeld van [hoe ondersteuning taken](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>Achtergrond taakgerelateerde API 's

De volgende API's worden geleverd door Windows PowerShell voor het beheren van achtergrondtaken.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) is afgeleid van aangepaste taakobjecten. Dit is een abstracte klasse.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Hiermee beheert u en bevat informatie over de huidige actieve achtergrondtaken.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definieert de status van de achtergrondtaak. Statussen zijn gestart, die wordt uitgevoerd en gestopt.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) vindt u informatie over de status van een achtergrondtaak en, als de laatste status gewijzigd is veroorzaakt door een fout op de reden dat de taak hebt ingevoerd voor de huidige status.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) biedt de argumenten voor een gebeurtenis die wordt gegenereerd wanneer de status van een achtergrondtaak wordt gewijzigd.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell-taak-Cmdlets

De volgende cmdlets worden geleverd door Windows PowerShell voor het beheren van achtergrondtaken.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Hiermee haalt u Windows PowerShell-achtergrondtaken die worden uitgevoerd in de huidige sessie.

[Receive-Job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Hiermee haalt de resultaten van de Windows PowerShell-achtergrondtaken in de huidige sessie.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Hiermee verwijdert u een achtergrondtaak van Windows PowerShell.

[Taak starten](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Start een achtergrondtaak van Windows PowerShell.

[Stop-Job](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Hiermee stopt u een achtergrondtaak van Windows PowerShell.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Onderdrukt de opdrachtprompt totdat een of meer van de Windows PowerShell-achtergrondtaken die worden uitgevoerd in de sessie voltooid zijn.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
