---
title: GetProc-zelfstudie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851329"
---
# <a name="getproc-tutorial"></a>GetProc-zelfstudie

In deze sectie bevat een zelfstudie voor het maken van een cmdlet Get-Proc die is vergelijkbaar met de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) geleverd door Windows PowerShell cmdlet. Deze zelfstudie bevat codefragmenten die laten zien hoe de cmdlets worden geïmplementeerd en een uitleg van de code.

## <a name="topics-in-this-tutorial"></a>Onderwerpen in deze zelfstudie

De onderwerpen in deze zelfstudie zijn ontworpen om te worden opeenvolgend gelezen met elk onderwerp bouwen op wat is besproken in het vorige onderwerp.

[Het maken van een Cmdlet zonder Parameters](./creating-a-cmdlet-without-parameters.md) in deze sectie wordt beschreven hoe u een cmdlet die wordt informatie opgehaald uit de lokale computer zonder het gebruik van parameters en vervolgens schrijft de informatie in de pijplijn te maken.

[Dat proces Command-Line invoer Parameters toe te voegen](./adding-parameters-that-process-command-line-input.md) in deze sectie wordt beschreven hoe u een parameter toevoegen aan de cmdlet Get-Proc dat invoer op basis van expliciete objecten die zijn doorgegeven aan de cmdlet kan worden verwerkt door de cmdlet. De implementatie dan beschreven staat hier haalt processen op basis van hun naam en vervolgens schrijft de informatie in de pijplijn.

[Parameters die invoer van de pijplijn proces toe te voegen](./adding-parameters-that-process-pipeline-input.md) in deze sectie wordt beschreven hoe u een parameter toevoegen aan de cmdlet Get-Proc zodat de cmdlet objecten die worden doorgegeven via de pijplijn kan verwerken. De implementatie-cmdlet beschreven hier opgehaald op basis van objecten die zijn doorgegeven aan de cmdlet processen, en vervolgens schrijft de informatie in de pijplijn.

[Nonterminating foutrapportage toevoegen aan uw Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) in deze sectie wordt beschreven hoe u om toe te voegen nonterminating die fouten rapporteren aan een cmdlet. De hier beschreven implementatie detecteert afsluitfouten die optreden bij het verwerken van invoer en een foutrecord schrijft naar de foutstroom.

## <a name="see-also"></a>Zie ook

[Het maken van een Cmdlet zonder Parameters](./creating-a-cmdlet-without-parameters.md)

[Parameters die opdrachtregel verwerken toe te voegen](./adding-parameters-that-process-command-line-input.md)

[Parameters die proces Pipeline ingevoerd toe te voegen](./adding-parameters-that-process-pipeline-input.md)

[Nonterminating die fouten rapporteren aan uw Cmdlet toe te voegen](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
