---
title: Zelf studie voor GetProc | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: cc99cb4de8e3b8fcab8eac28b21162764aecd8a1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784262"
---
# <a name="getproc-tutorial"></a>GetProc-zelfstudie

Deze sectie bevat een zelf studie voor het maken van een Get-proc-cmdlet die vergelijkbaar is met de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) van Windows Power shell. Deze zelf studie bevat fragmenten van code die illustreert hoe cmdlets worden geïmplementeerd en een uitleg van de code.

## <a name="topics-in-this-tutorial"></a>Onderwerpen in deze zelf studie

De onderwerpen in deze zelf studie zijn zodanig ontworpen dat ze opeenvolgend worden gelezen, met elk onderwerp dat is gebaseerd op wat in het vorige onderwerp is besproken.

[Een cmdlet zonder para meters maken](./creating-a-cmdlet-without-parameters.md) In deze sectie wordt beschreven hoe u een cmdlet maakt waarmee informatie wordt opgehaald van de lokale computer zonder het gebruik van para meters, en vervolgens de informatie naar de pijp lijn schrijft.

[Para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md) In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de cmdlet Get-proc, zodat de cmdlet invoer kan verwerken op basis van expliciete objecten die worden door gegeven aan de cmdlet. De implementatie die hier wordt beschreven, haalt processen op basis van hun naam en schrijft vervolgens de informatie naar de pijp lijn.

[Para meters toevoegen die de invoer van de pijp lijn verwerken](./adding-parameters-that-process-pipeline-input.md) In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de cmdlet Get-proc, zodat de cmdlet objecten kan verwerken die worden door gegeven via de pijp lijn. De implementatie-cmdlet die hier wordt beschreven, haalt processen op basis van objecten die zijn door gegeven aan de cmdlet en schrijft de informatie vervolgens naar de pijp lijn.

[Fout rapportage voor niet-afsluiting aan uw cmdlet toevoegen](./adding-non-terminating-error-reporting-to-your-cmdlet.md) In deze sectie wordt beschreven hoe u niet-afsluit fout rapportage aan een cmdlet toevoegt. De hier beschreven implementatie detecteert niet-afsluit fouten die optreden bij het verwerken van de invoer en schrijft een fout record naar de fout stroom.

## <a name="see-also"></a>Zie ook

[Een cmdlet maken zonder parameters](./creating-a-cmdlet-without-parameters.md)

[Para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md)

[Parameters toevoegen die pijplijninvoer verwerken](./adding-parameters-that-process-pipeline-input.md)

[Fout rapportage voor niet-afsluiting aan uw cmdlet toevoegen](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
