---
title: Runspaces maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779570"
---
# <a name="creating-runspaces"></a>Runspaces maken

Een runs Pace is de besturings omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing. Deze omgeving bevat de opdrachten en gegevens die momenteel aanwezig zijn en de taal beperkingen die momenteel van toepassing zijn.

 Hosttoepassingen kunnen gebruikmaken van de standaard runs Pace van Windows Power shell, die alle beschik bare kern opdrachten bevat, of een aangepaste runs Pace maken die alleen een subset van de beschik bare opdrachten bevat. Als u een aangepaste runs Pace wilt maken, maakt u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object en wijst u dit toe aan uw runs Pace.

## <a name="runspace-tasks"></a>Runs Pace-taken

1. [Een InitialSessionState maken](./creating-an-initialsessionstate.md)

2. [Een beperkte runspace maken](./creating-a-constrained-runspace.md)

3. [Meerdere runspaces maken](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Zie ook
