---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737029"
---
# <a name="the-ise-object-model-hierarchy"></a>De objectmodelhiërarchie van ISE

In dit onderwerp wordt de hiërarchie weer gegeven van objecten die deel uitmaken van Windows Power shell Integrated Scripting Environment (ISE). Windows PowerShell ISE is opgenomen in Windows Power Shell 3,0, 4,0 en 5,1. Klik op een object om naar de referentie documentatie te gaan voor de klasse die het object definieert.

## <a name="psise-object"></a>$psISE-object

Het `$psISE`-object is het [hoofd object](The-ObjectModelRoot-Object.md) van de object hiërarchie Windows PowerShell ISE. Op het hoogste niveau worden de volgende objecten beschikbaar gemaakt voor het uitvoeren van scripts:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE. CurrentFile](The-ISEFile-Object.md)

Het `$psISE.CurrentFile`-object is een instantie van de klasse [ISEFile](The-ISEFile-Object.md) .

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE. CurrentPowerShellTab](The-PowerShellTab-Object.md)

Het `$psISE.CurrentPowerShellTab`-object is een instantie van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE. CurrentVisibleHorizontalTool

Het `$psISE.CurrentVisibleHorizontalTool`-object is een instantie van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de bovenrand van het Windows PowerShell ISE-venster.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE. CurrentVisibleVerticalTool

Het `$psISE.CurrentVisibleHorizontalTool`-object is een instantie van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) . Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de rechter rand van het Windows PowerShell ISE-venster.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE. opties](The-ISEOptions-Object.md)

Het `$psISE.Options`-object is een instantie van de klasse [ISEOptions](The-ISEOptions-Object.md) . Het ISEOptions-object vertegenwoordigt verschillende instellingen voor Windows PowerShell ISE. Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md)

Het `$psISE.PowerShellTabs`-object is een instantie van de klasse [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) . Het is een verzameling van alle momenteel geopende Power shell-tabbladen die de beschik bare Windows Power shell-omgevingen voor uitvoeren op de lokale computer of op verbonden externe computers vertegenwoordigen. Elk lid van de verzameling is een exemplaar van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="see-also"></a>Zie ook

- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
