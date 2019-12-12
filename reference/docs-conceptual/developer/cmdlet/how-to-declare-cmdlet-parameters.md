---
title: Cmdlet-para meters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356397"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cmdlet-parameters declareren

In deze voor beelden ziet u hoe u para meters met de naam, positioneel, required, optional en switch declareert. In deze voor beelden ziet u ook hoe u een parameter alias definieert.

## <a name="how-to-declare-a-named-parameter"></a>Een benoemde para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Wanneer u het parameter kenmerk toevoegt, laat u het sleutel woord `Position` weg van het kenmerk.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-a-positional-parameter"></a>Een positionele para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Wanneer u het parameter kenmerk toevoegt, stelt u het sleutel woord `Position` in op de argument positie. De waarde 0 geeft de eerste positie aan.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-a-mandatory-parameter"></a>Een verplichte para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Wanneer u het parameter kenmerk toevoegt, stelt u het sleutel woord `Mandatory` in op `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-an-optional-parameter"></a>Een optionele para meter declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Als u het parameter kenmerk toevoegt, laat u het sleutel woord `Mandatory` weg.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Een para meter voor een switch declareren

- Definieer een open bare eigenschap als type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)en Declareer vervolgens het parameter kenmerk.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.

## <a name="how-to-declare-a-parameter-with-aliases"></a>Een para meter met aliassen declareren

- Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven. Voeg een alias kenmerk toe met een lijst met de aliassen voor de para meter. In dit voor beeld worden drie aliassen gedefinieerd voor dezelfde para meter. De eerste alias biedt een snelkoppeling. De tweede en derde alias geven namen op die u voor verschillende scenario's kunt gebruiken.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie over het alias kenmerk.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Parameter kenmerk declaratie](./parameter-attribute-declaration.md)

[Alias kenmerk declaratie](./alias-attribute-declaration.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
