---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057844"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Soms moet u een tijdelijk bestand maken in uw scripts. U kunt heel gemakkelijk doen dit met de **New-TemporaryFile** cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\gebruikers\\slee\\AppData\\lokale\\Temp\\tmp375.tmp
