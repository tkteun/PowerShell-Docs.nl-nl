---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "62057720"
---
# <a name="the-ise-object-model-hierarchy"></a>De objectmodelhiërarchie van ISE

In dit onderwerp wordt de hiërarchie weer gegeven van objecten die deel uitmaken van Windows Power shell Integrated Scripting Environment (ISE).
Windows PowerShell ISE is opgenomen in Windows Power Shell 3,0 en in Windows Power Shell 4,0.
Klik op een object om naar de referentie documentatie te gaan voor de klasse die het object definieert.

## <a name="psise-object"></a>$psISE-object

Het **$psISE** -object is het [hoofd object](The-ObjectModelRoot-Object.md) van de object hiërarchie Windows PowerShell ISE.
Op het hoogste niveau worden de volgende objecten beschikbaar gemaakt voor het uitvoeren van scripts:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE. CurrentFile](The-ISEFile-Object.md)

Het object **$psISE. CurrentFile** is een instantie van de klasse [ISEFile](The-ISEFile-Object.md) .

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE. CurrentPowerShellTab](The-PowerShellTab-Object.md)

Het object **$psISE. CurrentPowerShellTab** is een instantie van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE. CurrentVisibleHorizontalTool

Het object **$psISE. CurrentVisibleHorizontalTool** is een instantie van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) .
Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de bovenrand van het Windows PowerShell ISE-venster.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE. CurrentVisibleVerticalTool

Het object **$psISE. CurrentVisibleHorizontalTool** is een instantie van de klasse [ISEAddOnTool](The-ISEAddOnTool-Object.md) .
Het bevat het geïnstalleerde invoeg programma dat momenteel is gekoppeld aan de rechter rand van het Windows PowerShell ISE-venster.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE. opties](The-ISEOptions-Object.md)

Het object **$psISE. options** is een instantie van de klasse [ISEOptions](The-ISEOptions-Object.md) .
Het ISEOptions-object vertegenwoordigt verschillende instellingen voor Windows PowerShell ISE.
Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md)

Het object **$psISE. PowerShellTabs** is een instantie van de klasse [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) .
Het is een verzameling van alle momenteel geopende Power shell-tabbladen die de beschik bare Windows Power shell-omgevingen voor uitvoeren op de lokale computer of op verbonden externe computers vertegenwoordigen.
Elk lid van de verzameling is een exemplaar van de klasse [PowerShellTab](The-PowerShellTab-Object.md) .

## <a name="see-also"></a>Zie ook

- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)