---
title: Kimlik bilgisi öznitelik bildiriminin | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059261"
---
# <a name="credential-attribute-declaration"></a>Kimlik Bilgisi Özniteliği Bildirimi

Kimlik bilgisi türü parametrelerle kullanılabilecek isteğe bağlı bir öznitelik kimlik bilgisi özniteliktir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir. Bu öznitelik için bir parametre bildirimi eklendiğinde, Windows PowerShell bir dize girişi dönüştürür bir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesne. Örneğin, [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet, Windows PowerShell oluşturmak için bu öznitelik kullanır [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet'i tarafından döndürülen nesne.

## <a name="syntax"></a>Sözdizimi

```csharp
[Credential]
```

## <a name="remarks"></a>Açıklamalar

- Bu öznitelik türünde bir parametre tarafından genellikle kullanılan [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir. Olduğunda bir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesne parametresi için geçirilen, Windows PowerShell hiçbir şey yapmaz.

- Oluştururken [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesnesi, Windows PowerShell, kullanıcıya uygun yönergeleri görüntülemek için geçerli ana bilgisayar kullanır. Örneğin, bu öznitelik kullanıldığında varsayılan ana bilgisayar için bir kullanıcı adı ve parola istemi görüntüler. Ancak, özel bir ana bilgisayar kullanılıyorsa farklı bir komut istemi tanımlayan sonra Bu istem görüntülenir.

- Bu öznitelik ile parametre özniteliği kullanılır. Bu özniteliği hakkında daha fazla bilgi için bkz. [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

- Kimlik bilgisi özniteliği tarafından tanımlanan [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[Parametre diğer adları](./parameter-aliases.md)

[Parametre özniteliği bildirimi](./parameter-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
