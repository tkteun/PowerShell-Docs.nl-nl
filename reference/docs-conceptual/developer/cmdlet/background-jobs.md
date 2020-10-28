---
ms.date: 09/13/2016
ms.topic: reference
title: Achtergrondtaken
description: Achtergrondtaken
ms.openlocfilehash: 5478789a2ee1f2eabc71a46673e3a707643cdba8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648613"
---
# <a name="background-jobs"></a>Achtergrondtaken

Cmdlets kunnen hun actie intern of als Windows Power shell- *achtergrond taak* uitvoeren. Wanneer een cmdlet wordt uitgevoerd als een achtergrond taak, wordt het werk asynchroon uitgevoerd in een eigen thread, gescheiden van de pijplijn thread die de cmdlet gebruikt. Wanneer een cmdlet wordt uitgevoerd als achtergrond taak, retourneert de opdracht prompt onmiddellijk, zelfs als de taak een lange tijd lang duurt om te worden voltooid, en de gebruiker kan zonder onderbreking door gaan terwijl de taak wordt uitgevoerd.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Achtergrond taken, onderliggende taken en de taak opslagplaats

Het taak object dat wordt geretourneerd door de cmdlets die ondersteuning bieden voor achtergrond taken, definieert de taak. (De cmdlet [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) retourneert ook een taak object.) De naam van de taak, een id die wordt gebruikt om de taak op te geven, de status informatie en de onderliggende taken zijn opgenomen in deze definitie. De taak voert geen werk uit. Elke achtergrond taak heeft ten minste één onderliggende taak omdat de onderliggende taak het werkelijke werk uitvoert. Wanneer u een cmdlet uitvoert zodat het werk wordt uitgevoerd als een achtergrond taak, moet de cmdlet de taak en de onderliggende taken toevoegen aan een algemene opslag plaats, waarnaar wordt verwezen als de *taak opslagplaats* .

Zie het volgende voor meer informatie over de manier waarop achtergrond taken worden verwerkt op de opdracht regel:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Een cmdlet schrijven die als achtergrond taak wordt uitgevoerd

Als u een cmdlet wilt schrijven die als achtergrond taak kan worden uitgevoerd, moet u de volgende taken uitvoeren:

- Definieer een `asJob` Switch parameter zodat de gebruiker kan bepalen of de cmdlet moet worden uitgevoerd als achtergrond taak.

- Maak een-object dat is afgeleid van de klasse [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) . Dit object kan een aangepast taak object zijn of een taak object dat wordt meegeleverd met Windows Power shell, zoals een [System. Management. Automation. Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) -object.

- Voeg in een methode voor het verwerken van records een `if` instructie toe die detecteert of de cmdlet moet worden uitgevoerd als een achtergrond taak.

- Implementeer voor aangepaste taak objecten de taak klasse.

- De juiste objecten retour neren, afhankelijk van het feit of de cmdlet wordt uitgevoerd als een achtergrond taak.

Zie [taken ondersteunen](./how-to-support-jobs.md)voor een code voorbeeld.

## <a name="background-job-related-apis"></a>Api's voor achtergrond Job-Related

De volgende Api's worden verzorgd door Windows Power shell voor het beheren van achtergrond taken.

Met [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) worden aangepaste taak objecten afgeleid. Dit is een abstracte klasse.

[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) beheert en bevat informatie over de huidige actieve achtergrond taken.

[System. Management. Automation. Jobstate](/dotnet/api/System.Management.Automation.JobState) definieert de status van de achtergrond taak. Statussen zijn gestart, actief en gestopt.

[System. Management. Automation. Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) biedt informatie over de status van een achtergrond taak en, als de laatste status wijziging is veroorzaakt door een fout, de reden waarom de taak de huidige status heeft opgegeven.

[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) biedt de argumenten voor een gebeurtenis die optreedt wanneer de status van een achtergrond taak wordt gewijzigd.

## <a name="windows-powershell-job-cmdlets"></a>Windows Power shell-taak-cmdlets

De volgende cmdlets worden verzorgd door Windows Power shell voor het beheren van achtergrond taken.

[Get-job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Hiermee worden Windows Power shell-achtergrond taken opgehaald die worden uitgevoerd in de huidige sessie.

[Receive-job](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Hiermee worden de resultaten van de Windows Power shell-achtergrond taken in de huidige sessie opgehaald.

[Verwijderen-taak](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Hiermee verwijdert u een Windows Power shell-achtergrond taak.

[Begin taak](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Start een Windows Power shell-achtergrond taak.

[Stoppen-taak](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Hiermee stopt u een Windows Power shell-achtergrond taak.

[Wait-Job](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Onderdrukt de opdracht prompt totdat een of alle Windows Power shell-achtergrond taken die in de sessie worden uitgevoerd, zijn voltooid.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
