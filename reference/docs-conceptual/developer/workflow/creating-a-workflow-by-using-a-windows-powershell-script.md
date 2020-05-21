---
title: Een werk stroom maken met behulp van een Windows Power shell-script | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557445"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Een werkstroom maken met behulp van een Windows PowerShell-script

U kunt een werk stroom maken door een Windows Power shell-script te schrijven. Als u een werk stroom wilt maken, gebruikt u het tref woord workflow gevolgd door een naam voor de werk stroom vóór de hoofd tekst van het script. Bijvoorbeeld:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

U vindt de werk stroom op dezelfde manier als elke andere Windows Power shell-opdracht.

## <a name="implementing-parallel-and-sequence"></a>Parallelle en sequentieel implementeren

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) ondersteunt de uitvoering van activiteiten parallel. Als u deze functie in een Windows Power shell-script wilt implementeren, gebruikt u het `parallel` sleutel woord voor een script blok. U kunt ook de `foreach -parallel` constructie gebruiken om een verzameling objecten parallel te herhalen. Als u een groep activiteiten in sequentiële volg orde binnen een parallel blok wilt uitvoeren, sluit u die groep activiteiten in een script blok en plaatst u de blok kering met het sleutel woord sequence.

## <a name="joining-computers-to-a-domain"></a>Computers toevoegen aan een domein

Met het volgende script wordt een werk stroom gemaakt waarmee de domein status wordt gecontroleerd van een groep door de gebruiker opgegeven computers, wordt toegevoegd aan een domein als ze nog niet zijn gekoppeld, waarna de status opnieuw wordt gecontroleerd.
Dit is een script versie van de XAML-werk stroom die wordt uitgelegd in [een werk stroom maken met Windows Power shell-activiteiten](./creating-a-workflow-with-windows-powershell-activities.md).

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
