---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Soms moet u in uw scripts, een tijdelijk bestand maken. U kunt eenvoudig doen met de **nieuw TemporaryFile** cmdlet:

PS C:\\ &gt; $tempFile = New-TemporaryFile

PS C:\\ &gt; $tempFile.FullName

C:\\gebruikers\\slee\\AppData\\lokale\\Temp\\tmp375.tmp
