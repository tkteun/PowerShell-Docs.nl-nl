---
title: Het maken van Runspaces | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082937"
---
# <a name="creating-runspaces"></a>Runspaces maken

Een runspace is de operationele omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing. Deze omgeving omvat de opdrachten en gegevens die momenteel aanwezig zijn en de taal-beperkingen die momenteel van toepassing.

 Hosting van toepassingen kunnen gebruiken de standaard-runspace die wordt geleverd door Windows PowerShell, waaronder alle beschikbare core opdrachten, of maak een aangepaste runspace met slechts een subset van de beschikbare opdrachten. Voor het maken van een aangepaste runspace, maakt u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object en wijs deze toe aan uw runspace.

## <a name="runspace-tasks"></a>Runspace taken

1. [Het maken van een InitialSessionState](./creating-an-initialsessionstate.md)

2. [Het maken van een beperkte runspace](./creating-a-constrained-runspace.md)

3. [Het maken van meerdere runspaces](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Zie ook
