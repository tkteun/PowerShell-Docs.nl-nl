---
ms.date: 09/13/2016
ms.topic: reference
title: Runspaces maken
description: Runspaces maken
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649346"
---
# <a name="creating-runspaces"></a>Runspaces maken

Een runs Pace is de besturings omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing. Deze omgeving bevat de opdrachten en gegevens die momenteel aanwezig zijn en de taal beperkingen die momenteel van toepassing zijn.

 Hosttoepassingen kunnen gebruikmaken van de standaard runs Pace van Windows Power shell, die alle beschik bare kern opdrachten bevat, of een aangepaste runs Pace maken die alleen een subset van de beschik bare opdrachten bevat. Als u een aangepaste runs Pace wilt maken, maakt u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object en wijst u dit toe aan uw runs Pace.

## <a name="runspace-tasks"></a>Runs Pace-taken

1. [Een InitialSessionState maken](./creating-an-initialsessionstate.md)

2. [Een beperkte runspace maken](./creating-a-constrained-runspace.md)

3. [Meerdere runspaces maken](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Zie ook
