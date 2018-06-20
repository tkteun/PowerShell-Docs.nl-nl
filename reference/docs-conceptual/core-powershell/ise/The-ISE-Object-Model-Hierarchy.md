---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De objectmodelhiërarchie van ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950689"
---
# <a name="the-ise-object-model-hierarchy"></a>De objectmodelhiërarchie van ISE

Dit onderwerp bevat de hiërarchie van objecten die deel uitmaken van Windows PowerShell Integrated Scripting Environment (ISE).
Windows PowerShell ISE is opgenomen in Windows PowerShell 3.0 en Windows PowerShell 4.0.
Klik op een object waarmee u de documentatie bij de klasse die het object definieert.

## <a name="psise-object"></a>$psISE Object

De **$psISE** -object is de [hoofdobject](The-ObjectModelRoot-Object.md) van de hiërarchie van Windows PowerShell ISE-object.
Zich bevindt op het hoogste niveau, maakt de volgende objecten beschikbaar zijn voor het uitvoeren van scripts:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

De **$psISE.CurrentFile** object is een exemplaar van de [ISEFile](The-ISEFile-Object.md) klasse.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

De **$psISE.CurrentPowerShellTab** object is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.
Deze vertegenwoordigt het geïnstalleerde invoegtoepassing hulpprogramma dat momenteel is gekoppeld aan de bovenkant van het Windows PowerShell ISE-venster.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

De **$psISE.CurrentVisibleHorizontalTool** object is een exemplaar van de [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasse.
Deze vertegenwoordigt het geïnstalleerde invoegtoepassing hulpprogramma dat momenteel is gekoppeld aan de rechterzijde van het Windows PowerShell ISE-venster.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

De **$psISE.Options** object is een exemplaar van de [ISEOptions](The-ISEOptions-Object.md) klasse.
Het object ISEOptions vertegenwoordigt diverse instellingen voor Windows PowerShell ISE.
Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

De **$psISE.PowerShellTabs** object is een exemplaar van de [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasse.
Er is een verzameling van alle geopende PowerShell tabbladen met daarin de beschikbare Windows PowerShell op de lokale computer of op externe computers verbonden omgevingen uitgevoerd.
Elk lid in de verzameling is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.

## <a name="see-also"></a>Zie ook

- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)