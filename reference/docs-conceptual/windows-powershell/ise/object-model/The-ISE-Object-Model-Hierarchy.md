---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811042"
---
# <a name="the-ise-object-model-hierarchy"></a>De objectmodelhiërarchie van ISE

In dit onderwerp wordt de hiërarchie weer gegeven van objecten die deel uitmaken van Windows Power shell Integrated Scripting Environment (ISE). Windows PowerShell ISE is opgenomen in Windows Power Shell 3,0, 4,0 en 5,1. Klik op een object om naar de referentie documentatie te gaan voor de klasse die het object definieert.

## <a name="psise-object"></a>$psISE-object

Het `$psISE` object is het [hoofd object](The-ObjectModelRoot-Object.md) van de hiërarchie van het Windows PowerShell ISE-object. Op het hoogste niveau worden de volgende objecten beschikbaar gemaakt voor het uitvoeren van scripts:

## <a name="psisecurrentfile"></a>[$psISE. CurrentFile](The-ISEFile-Object.md)

Het `$psISE.CurrentFile` object is een exemplaar van de klasse [ISEFile](The-ISEFile-Object.md) .

## <a name="psisecurrentpowershelltab"></a>[$psISE. CurrentPowerShellTab](The-PowerShellTab-Object.md)

Het `$psISE.CurrentPowerShellTab` object is een exemplaar van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE. CurrentVisibleHorizontalTool

Het `$psISE.CurrentVisibleHorizontalTool` object is een exemplaar van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de bovenrand van het Windows PowerShell ISE-venster.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE. CurrentVisibleVerticalTool

Het `$psISE.CurrentVisibleHorizontalTool` object is een exemplaar van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de rechter rand van het Windows PowerShell ISE-venster.

## <a name="psiseoptions"></a>[$psISE. opties](The-ISEOptions-Object.md)

Het `$psISE.Options` object is een exemplaar van de klasse [ISEOptions](The-ISEOptions-Object.md) . Het ISEOptions-object vertegenwoordigt verschillende instellingen voor Windows PowerShell ISE. Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEOptions.

## <a name="psisepowershelltabs"></a>[$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md)

Het `$psISE.PowerShellTabs` object is een exemplaar van de klasse [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) . Het is een verzameling van alle momenteel geopende Power shell-tabbladen die de beschik bare Windows Power shell-omgevingen voor uitvoeren op de lokale computer of op verbonden externe computers vertegenwoordigen. Elk lid van de verzameling is een exemplaar van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="see-also"></a>Zie ook

- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
