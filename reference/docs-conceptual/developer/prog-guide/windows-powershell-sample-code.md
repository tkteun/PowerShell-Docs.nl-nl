---
title: Voorbeeld code voor Windows Power shell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 76b4195eb33a1058109df8f6174a89708ba039d1
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563247"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell-voorbeeldcode

Windows Power shell®-voor beelden zijn beschikbaar via de Windows SDK. Deze sectie bevat de voorbeeld code die is opgenomen in de Windows SDK-voor beelden.

> [!NOTE]
> Wanneer de Windows SDK is geïnstalleerd, wordt er een map met voor **beelden** gemaakt waarin alle voor beelden van Windows Power shell beschikbaar worden gesteld. Een typische installatie directory is **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Start Windows Power shell en typ **' cd Samples\SysMgmt\PowerShell '** om de map met Windows Power shell-voor beelden te vinden. In dit document wordt de map Windows Power shell-voor beelden wordt aangeduid als ** \< Power shell **-voor beelden>.

## <a name="sample-code-listing"></a>Voorbeeld code weer geven

|                                    Voorbeeldcode                                    |                                                                                                                                           Beschrijving                                                                                                                                           |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AccessDbProviderSample01-codevoorbeeld](./accessdbprovidersample01-code-sample.md) | Dit is de provider die wordt beschreven in [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md).                                                                                                                                                            |
| [AccessDBProviderSample02-codevoorbeeld](./accessdbprovidersample02-code-sample.md) | Dit is de provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md).                                                                                                                                                            |
| [AccessDBProviderSample03-codevoorbeeld](./accessdbprovidersample03-code-sample.md) | Dit is de provider die wordt beschreven in [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md).                                                                                                                                                              |
| [AccessDBProviderSample04-codevoorbeeld](./accessdbprovidersample04-code-sample.md) | Dit is de provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).                                                                                                                                                    |
| [AccessDBProviderSample05-codevoorbeeld](./accessdbprovidersample05-code-sample.md) | Dit is de provider die wordt beschreven in [een Windows Power shell-navigatie provider maken](./creating-a-windows-powershell-navigation-provider.md).                                                                                                                                                  |
| [AccessDBProviderSample06-codevoorbeeld](./accessdbprovidersample06-code-sample.md) | Dit is de provider die wordt beschreven in [een Windows Power shell-inhouds provider maken](./creating-a-windows-powershell-content-provider.md).                                                                                                                                                        |
| [GetProc01-codevoorbeelden](./getproc01-code-samples.md)                             | Dit is het basis `Get-Process` voorbeeld van de cmdlet die wordt beschreven in [uw eerste cmdlet maken](../cmdlet/creating-a-cmdlet-without-parameters.md).                                                                                                                                                     |
| [GetProc02-codevoorbeelden](./getproc02-code-samples.md)                             | Dit is het `Get-Process` cmdlet-voor beeld dat wordt beschreven in [para meters toevoegen die opdracht regel invoer verwerken](../cmdlet/adding-parameters-that-process-command-line-input.md).                                                                                                                       |
| [GetProc03-codevoorbeelden](./getproc03-code-samples.md)                             | Dit is het `Get-Process` cmdlet-voor beeld dat wordt beschreven in [para meters toevoegen die de invoer van de pijp lijn verwerken](../cmdlet/adding-parameters-that-process-pipeline-input.md).                                                                                                                               |
| [GetProc04-codevoorbeelden](./getproc04-code-samples.md)                             | Dit is het `Get-Process` cmdlet-voor beeld dat wordt beschreven in het toevoegen van niet- [afsluitende fout rapportage aan uw cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).                                                                                                                |
| [GetProc05-codevoorbeelden](./getproc05-code-samples.md)                             | Deze `Get-Process` cmdlet is vergelijkbaar met de cmdlet die wordt beschreven in het toevoegen van niet- [afsluitende fout rapportage aan uw cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).                                                                                                     |
| [StopProc01-codevoorbeelden](./stopproc01-code-samples.md)                           | Dit is het `Stop-Process` cmdlet-voor beeld dat wordt beschreven in [het maken van een cmdlet waarmee het systeem wordt gewijzigd](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).                                                                                                                                    |
| [StopProcessSample04-codevoorbeelden](./stopprocesssample04-code-samples.md)         | Dit is het `Stop-Process` cmdlet-voor beeld dat wordt beschreven in het [toevoegen van parameter sets aan een cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).                                                                                                                                                      |
| [Runspace01-codevoorbeelden](./runspace01-code-samples.md)                           | Dit zijn de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).                                                                                      |
| [Runspace02-codevoorbeelden](./runspace02-code-samples.md)                           | In dit voor beeld wordt de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) gebruikt om de cmdlet synchroon uit te voeren `Get-Process` .                                                                                                            |
| [Runspace03-codevoorbeelden](./runspace03-code-samples.md)                           | Dit zijn de code voorbeelden voor de runs Pace die wordt beschreven in een console toepassing maken die een opgegeven script uitvoert.                                                                                                                                                                         |
| [Runspace04-codevoorbeelden](./runspace04-code-samples.md)                           | Dit is een code voorbeeld voor een runs Pace die gebruikmaakt van de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) om een script uit te voeren dat een afsluit fout genereert.                                                                         |
| [Runspace05-codevoorbeeld](./runspace05-code-sample.md)                             | Dit is de bron code voor het Runspace05-voor beeld dat wordt beschreven in [een runs Pace configureren met behulp van RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).                                                                                                           |
| [Runspace06-codevoorbeeld](./runspace06-code-sample.md)                             | Dit is de bron code voor het Runspace06-voor beeld dat wordt beschreven in [een runs Pace configureren met een Windows Power shell-module](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).                                                                                                    |
| [Runspace07-codevoorbeeld](./runspace07-code-sample.md)                             | Dit is de bron code voor het Runspace07-voor beeld dat wordt beschreven in [een console toepassing maken waarmee opdrachten worden toegevoegd aan een pijp lijn](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).                                                                                              |
| [Runspace08-codevoorbeeld](./runspace08-code-sample.md)                             | Dit is de bron code voor het Runspace08-voor beeld dat wordt beschreven in [een console toepassing maken die para meters toevoegt aan een opdracht](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).                                                                                             |
| [Runspace09-codevoorbeeld](./runspace09-code-sample.md)                             | Dit is de bron code voor het Runspace09-voor beeld dat wordt beschreven in [een console toepassing maken die een pijp lijn asynchroon aanroept](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).                                                                                        |
| [Runspace10-codevoorbeeld](./runspace10-code-sample.md)                             | Dit is de bron code voor het Runspace10-voor beeld, waarmee een cmdlet wordt toegevoegd aan [System. Management. Automation. Runspaces. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) en vervolgens de gewijzigde configuratie-informatie gebruikt om de runs Pace te maken. |

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
