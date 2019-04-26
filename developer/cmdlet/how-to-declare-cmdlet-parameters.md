---
title: Cmdlet parametreleri bildirmek nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067932"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cmdlet Parametrelerini Bildirme

Bu örnekler bildirir adlandırılmış, konumsal, gerekli, isteğe bağlı ve parametreleri geçiş işlemini göstermektedir. Bu örnekler, ayrıca bir parametre diğer adını tanımlamak nasıl gösterir.

## <a name="how-to-declare-a-named-parameter"></a>Adlandırılmış parametre bildirmek nasıl

- Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın. Parametre özniteliği eklediğinizde atlamak `Position` özniteliğinden anahtar sözcüğü.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Konumsal bir parametre bildirmek nasıl

- Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın. Parametre özniteliği eklediğinizde ayarlamak `Position` bağımsız değişken konumu için anahtar sözcüğü. 0 değeri ilk konumu gösterir.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Nasıl zorunlu bir parametre bildirmek için

- Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın. Parametre özniteliği eklediğinizde ayarlamak `Mandatory` anahtar `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>İsteğe bağlı bir parametre bildirmek nasıl

- Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın. Parametre özniteliği eklediğinizde atlamak `Mandatory` anahtar sözcüğü.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Nasıl bir anahtar parametresi eklendi

- Bir ortak özellik türü olarak tanımlamanız [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)ve ardından parametre özniteliği bildirin.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Nasıl diğer adlar bir parametreyle bildirin

- Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın. Parametresi için diğer adlar listeleyen bir diğer ad özniteliğini ekleyin. Bu örnekte, üç diğer adları aynı parametresi için tanımlanır. İlk diğer bir kısayol sağlar. İkinci ve üçüncü diğer adları farklı senaryolar için kullanabileceğiniz adlar sağlar.

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

Diğer ad özniteliği hakkında daha fazla bilgi için bkz. [diğer ad özniteliği bildirimi](./alias-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Parametre özniteliği bildirimi](./parameter-attribute-declaration.md)

[Diğer ad özniteliği bildirimi](./alias-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
