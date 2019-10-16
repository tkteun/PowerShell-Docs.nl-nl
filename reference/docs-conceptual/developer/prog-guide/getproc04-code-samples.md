---
title: Voor beelden van GetProc04-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352638"
---
# <a name="getproc04-code-samples"></a>GetProc04-codevoorbeelden

Hier volgen de code voorbeelden voor de voor beeld-cmdlet GetProc04. Dit is het `Get-Process`-cmdlet-voor beeld dat wordt beschreven in het toevoegen van niet- [afsluitende fout rapportage aan uw cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md). Deze `Get-Process`-cmdlet roept de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aan wanneer er een ongeldige bewerkings uitzondering optreedt tijdens het ophalen van proces gegevens.

> [!NOTE]
> U kunt het C# bron bestand (getprov04.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
>
> De gedownloade bron bestanden zijn beschikbaar in de **\<PowerShell-voor beelden >** map.

Zie de volgende onderwerpen voor een volledige voorbeeld code.

|Taal|Onderwerp|
|--------------|-----------|
|C#|[GetProc04 (C#) voorbeeld code](./getproc04-csharp-sample-code.md)|
|VB.NET|[Voorbeeld code voor GetProc04 (VB.NET)](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Zie ook

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)