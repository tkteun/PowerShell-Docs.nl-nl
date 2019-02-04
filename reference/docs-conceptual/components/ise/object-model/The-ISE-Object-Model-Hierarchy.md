---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683770"
---
# <a name="the-ise-object-model-hierarchy"></a>De objectmodelhiërarchie van ISE

Dit onderwerp bevat de hiërarchie van objecten die deel uitmaken van Windows PowerShell Integrated Scripting Environment (ISE).
Windows PowerShell ISE is opgenomen in Windows PowerShell 3.0 en Windows PowerShell 4.0.
Klik op een object waarmee u de referentiedocumentatie voor de klasse die het object definieert.

## <a name="psise-object"></a>$psISE Object

De **$psISE** -object is de [hoofdobject](The-ObjectModelRoot-Object.md) van de hiërarchie van Windows PowerShell ISE-object.
Op het hoogste niveau bevindt, wordt de volgende objecten beschikbaar zijn voor het uitvoeren van scripts:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

De **$psISE.CurrentFile** object is een exemplaar van de [ISEFile](The-ISEFile-Object.md) klasse.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

De **$psISE.CurrentPowerShellTab** object is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.
Staat voor het hulpprogramma geïnstalleerde invoegtoepassingen die momenteel is gekoppeld aan de bovenkant van de Windows PowerShell ISE-venster.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.
Staat voor het hulpprogramma geïnstalleerde invoegtoepassingen die momenteel is gekoppeld aan de rechterzijde van de Windows PowerShell ISE-venster.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

De **$psISE.Options** object is een exemplaar van de [ISEOptions](The-ISEOptions-Object.md) klasse.
Het ISEOptions-object vertegenwoordigt diverse instellingen voor Windows PowerShell ISE.
Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

De **$psISE.PowerShellTabs** object is een exemplaar van de [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasse.
Er is een verzameling van alle geopende PowerShell tabbladen die staan voor de beschikbare Windows PowerShell op de lokale computer of op externe computers verbonden omgevingen uitvoeren.
Elk lid in de verzameling is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.

## <a name="see-also"></a>Zie ook

- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)