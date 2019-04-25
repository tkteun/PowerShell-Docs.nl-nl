---
title: Het maken van een werkstroom met behulp van een Windows PowerShell-Script | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080370"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Een werkstroom maken met behulp van een Windows PowerShell-script

U kunt een werkstroom maken door een Windows PowerShell-script te schrijven. Gebruik het sleutelwoord workflow gevolgd door een naam op voor de werkstroom voor de hoofdtekst van het script voor het maken van een werkstroom. Bijvoorbeeld:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

U vindt de werkstroom in de dezelfde manier als andere Windows PowerShell-opdracht.

## <a name="implementing-parallel-and-sequence"></a>Parallelle en Takenreeksen implementeren

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) ondersteunt de uitvoering van activiteiten parallel. Voor het implementeren van deze mogelijkheid in een Windows PowerShell-script, gebruikt u de `parallel` sleutelwoord vóór een scriptblok. U kunt ook de `foreach -parallel` bouw aan een verzameling van objecten tegelijk doorlopen. Als u wilt een groep activiteiten worden uitgevoerd in opeenvolgende volgorde binnen een parallel blok, plaatst u deze groep van activiteiten in een scriptblok en voorafgaan aan het blok met het trefwoord volgorde.

## <a name="joining-computers-to-a-domain"></a>Computers toevoegen aan een domein

Het volgende script maakt u een werkstroom die controleert de domeinstatus van een groep computers door gebruiker opgegeven, maakt u ze lid aan een domein als ze niet al zijn gekoppeld, en de status vervolgens opnieuw controleert. Dit is een scriptversie van de XAML-werkstroom uitgelegd in [het maken van een werkstroom met Windows PowerShell-activiteiten](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```