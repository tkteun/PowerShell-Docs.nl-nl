---
title: Runspaces maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357727"
---
# <a name="creating-runspaces"></a>Runspaces maken

Een runs Pace is de besturings omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing. Deze omgeving bevat de opdrachten en gegevens die momenteel aanwezig zijn en de taal beperkingen die momenteel van toepassing zijn.

 Hosttoepassingen kunnen gebruikmaken van de standaard runs Pace van Windows Power shell, die alle beschik bare kern opdrachten bevat, of een aangepaste runs Pace maken die alleen een subset van de beschik bare opdrachten bevat. Als u een aangepaste runs Pace wilt maken, maakt u een [System. Management. Automation. Runspaces. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object en wijst u dit toe aan uw runs Pace.

## <a name="runspace-tasks"></a>Runs Pace-taken

1. [Een InitialSessionState maken](./creating-an-initialsessionstate.md)

2. [Een beperkte runs Pace maken](./creating-a-constrained-runspace.md)

3. [Meerdere runspaces maken](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Zie ook
