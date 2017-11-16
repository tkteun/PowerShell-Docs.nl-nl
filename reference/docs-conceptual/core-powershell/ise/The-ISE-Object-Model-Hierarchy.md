---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "De hiërarchie ISE"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>De hiërarchie ISE
Dit onderwerp bevat de hiërarchie van objecten die deel uitmaken van Windows PowerShell Integrated Scripting Environment (ISE). Windows PowerShell ISE is opgenomen in Windows PowerShell 3.0 en Windows PowerShell 4.0. Klik op een object waarmee u de documentatie bij de klasse die het object definieert.

## <a name="psise-object"></a>$psISE object

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
Er is een verzameling van alle geopende PowerShell tabbladen met daarin de beschikbare Windows PowerShell op de lokale computer of op externe computers verbonden omgevingen uitgevoerd. Elk lid in de verzameling is een exemplaar van de [PowerShellTab](The-PowerShellTab-Object.md) klasse.

## <a name="see-also"></a>Zie ook
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md)
