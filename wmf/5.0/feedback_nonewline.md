---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057227"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="f7011-102">Parameter NoNewLine</span><span class="sxs-lookup"><span data-stu-id="f7011-102">NoNewLine parameter</span></span>
<span data-ttu-id="f7011-103">**Out-File**, **toevoegen-inhoud**, en **Set-inhoud** hebben nu een nieuwe **– NoNewline** switch die gewoon een nieuwe regel na de uitvoer wordt weggelaten.</span><span class="sxs-lookup"><span data-stu-id="f7011-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="f7011-104">Zonder **– NoNewline** opgegeven, wordt elk fragment zou worden op een afzonderlijke regel:</span><span class="sxs-lookup"><span data-stu-id="f7011-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
