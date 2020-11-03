---
description: Beschrijft een **CimSession** -object en het verschil tussen CIM-sessies en Power shell-sessies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 21015e1457dfcc037dd65cbf3b2f7f85c9076106
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252117"
---
# <a name="about-cimsession"></a>Over CimSession

## <a name="short-description"></a>Korte beschrijving
Beschrijft een **CimSession** -object en het verschil tussen CIM-sessies en Power shell-sessies.

## <a name="long-description"></a>Lange beschrijving

Een Common Information Model-sessie (CIM) is een client-side object dat een verbinding met een lokale computer of een externe computer vertegenwoordigt. U kunt CIM-sessies gebruiken als alternatief voor Power shell-sessies (PSSessions). Beide benaderingen hebben voor delen.

U kunt de- `New-CimSession` cmdlet gebruiken om een CIM-sessie te maken die informatie bevat over een verbinding, zoals de computer naam, het protocol dat wordt gebruikt voor de verbinding, de sessie-id en de exemplaar-id.

Nadat u een **CimSession** -object hebt gemaakt waarmee de vereiste informatie voor het maken van een verbinding wordt opgegeven, wordt de verbinding niet onmiddellijk door Power shell tot stand gebracht. Wanneer een cmdlet gebruikmaakt van de CIM-sessie, maakt Power shell verbinding met de opgegeven computer en wordt de verbinding door Power Shell beëindigd wanneer de cmdlet is voltooid.

Als u een **PSSession** maakt in plaats van een CIM-sessie, worden de verbindings instellingen door Power shell gevalideerd en wordt de verbinding tot stand gebracht en onderhouden. Als u CIM-sessies gebruikt, opent Power shell pas een netwerk verbinding als dat nodig is. Zie [about_PSSessions](about_PSSessions.md)voor meer informatie over Power shell-sessies.

## <a name="when-to-use-a-cim-session"></a>Wanneer moet u een CIM-sessie gebruiken?

Alleen cmdlets die samen werken met een Windows Management Instrumentation provider (WMI) of CIM over WS-Man CIM-sessies accepteren. Gebruik **PSSessions** voor andere cmdlets.

Wanneer u een CIM-sessie gebruikt, voert Power shell de cmdlet uit op de lokale client. Er wordt verbinding gemaakt met de WMI-provider met behulp van de CIM-sessie. De doel computer vereist geen Power shell of zelfs geen versie van het Windows-besturings systeem.

Daarentegen wordt een cmdlet uitgevoerd met behulp van een **PSSession** -uitvoering op de doel computer.
Hiervoor is Power shell vereist op het doel systeem. Daarnaast stuurt de cmdlet gegevens terug naar de lokale computer. Power shell beheert de gegevens die via de verbinding worden verzonden en behoudt de grootte binnen de limieten die zijn ingesteld met behulp van Windows Remote Management (WinRM). CIM-sessies leggen geen WinRM-limieten toe.

## <a name="using-cdxml-cmdlets"></a>CDXML-cmdlets gebruiken

Cmdlets voor de CDXML-cmdlets (op basis van CIM) kunnen worden geschreven voor het gebruik van elke WMI-provider. Alle WMI-providers gebruiken **CimSession** -objecten. Zie [CDXML definitie en voor waarden](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)voor meer informatie over CDXML.

CDXML-cmdlets hebben een automatische **CimSession** -para meter die een matrix van **CimSession** -objecten kan maken. Power shell beperkt het aantal gelijktijdige CIM-verbindingen standaard tot 15. Deze limiet kan worden overschreven door CDXML-cmdlets die de **ThrottleLimit** implementeren. Raadpleeg de afzonderlijke cmdlet-documentatie voor meer informatie over de **ThrottleLimit**.

## <a name="see-also"></a>ZIE OOK

[New-CimSession](xref:CimCmdlets.New-CimSession)

[about_PSSessions](about_PSSessions.md)
