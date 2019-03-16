---
title: Cmdlet'leri onaylamanızı isteyen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057414"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Cmdlet’lerden Onay İsteme

Windows PowerShell ortamının dışında sistemi için bir değişiklik yapmak üzere olduklarında cmdlet'leri onayını istemeniz gerekir. Örneğin, bir cmdlet hakkında bir kullanıcı hesabı ekleyin veya bir işlemi durdurmak için ise, devam etmeden önce cmdlet kullanıcı onayı gerektirmelidir. Bir cmdlet hakkında bir Windows PowerShell değişkeni değiştirmek için ise, buna karşılık, cmdlet onay gerektirmek gerek yoktur.

Bir onay isteği yapmak için cmdlet onay isteklerini destekler ve çağırmanız gerekir belirtmelidir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) bir onay isteği iletisi görüntülemek için (isteğe bağlı) yöntemleri.

## <a name="supporting-confirmation-requests"></a>Onay isteklerini destekleme

Onay isteklerini desteklemek için cmdlet ayarlamalısınız `SupportsShouldProcess` için Cmdlet öznitelik parametresinin `true`. Böylece `Confirm` ve `WhatIf` cmdlet parametreleri, Windows PowerShell tarafından sağlanır. `Confirm` Parametresi onaylama isteği görüntülenip görüntülenmeyeceğini kullanıcının denetlemesine olanak sağlar. `WhatIf` Parametresi cmdlet bir ileti görüntüleyebilir veya eylem gerçekleştirmek belirlemek kullanıcı olanak sağlar. El ile ekleme `Confirm` ve `WhatIf` bir cmdlet için parametreleri.

Aşağıdaki örnek, onay isteklerini destekleyen bir Cmdlet özniteliği bildirimi gösterir.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Onay isteği yöntemleri çağırma

Cmdlet kodda çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sistem değişiklikleri işlemin gerçekleştirilmesinden önce yöntemi. Olması durumunda çağrı değerini döndürür. Bu nedenle cmdlet tasarım `false`işlemi yapılmaz ve bir sonraki işlemi cmdlet tarafından işlenen.

## <a name="calling-the-shouldcontinue-method"></a>ShouldContinue yöntemi çağırma

Çoğu cmdlet onay yalnızca kullanarak istek [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi. Ancak, bazı durumlarda ek onay gerektirebilir. Bu durumlarda ek [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağırma çağrısı ile [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi. Bu cmdlet veya kapsamını daha ince denetlemekte sağlayıcısı sağlar **Tümüne Evet** yanıt olarak onay istemi.

Bir cmdlet çağırırsa [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi, cmdlet sağlamalıdır ayrıca bir `Force` parametre geçin. Kullanıcı belirtiyorsa `Force` kullanıcı cmdlet çalıştırdığında, cmdlet hala çağırmalıdır [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), ancak çağrısı atlama [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) etkileşimli olmayan bir ortamdan kullanıcı burada istemde bulunulamaz çağrıldığında, bir özel durum oluşturur. Ekleme bir `Force` parametresi, etkileşimli olmayan bir ortamda çağrıldığında komutu hala gerçekleştirilebileceğini sağlar.

Aşağıdaki örnek nasıl çağrılacağını gösterir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Davranışını bir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı cmdlet'i çağrılır ortamına bağlı olarak farklılık gösterir. Önceki yönergeleri kullanarak, cmdlet tutarlı olarak ana bilgisayar ortamının bağımsız olarak diğer cmdlet'lerle aynı şekilde davrandığını olmanıza yardımcı olur.

Çağırma örneği [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi bkz [istek onayları nasıl](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Etki düzeyi belirtin

Cmdlet oluşturduğunuzda, değişiklik etkisi düzeyini (önem derecesi) belirtin. Bunu yapmak için değeri ayarlamak `ConfirmImpact` yüksek, Orta veya düşük cmdlet'i özniteliğinin parametresi. İçin bir değer belirtebilirsiniz `ConfirmImpact` yalnızca ayrıca belirttiğinizde `SupportsShouldProcess` cmdlet'i için parametre.

Çoğu cmdlet için açıkça belirtmeniz gerekmez `ConfirmImpact`.  Bunun yerine, Orta olduğu parametresinin varsayılan ayarı kullanın. Ayarlarsanız `ConfirmImpact` varsayılan olarak yüksek olarak işlemi onaylanması. Bu ayar için bir sabit disk birimi biçimlendirmeden gibi yüksek oranda kesintiye uğratan Eylemler saklı tutarız.

## <a name="calling-non-confirmation-methods"></a>Onay olmayan yöntemleri çağırma

Cmdlet veya sağlayıcısı gerekir ileti gönderme, ancak onay isteği yok, aşağıdaki üç yöntemi çağırabilirsiniz. Kullanmaktan kaçının [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) çünkü bu tür iletileri göndermek için yöntemi [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) çıkış intermingled normal çıkış cmdlet'ini veya sağlayıcısı ile betik yazma zorlaştırır.

- Cmdlet'ini veya sağlayıcı kullanıcı dikkat ve işleme devam etmek için sonuna çağırabilirsiniz [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) yöntemi.

- Kullanıcı kullanarak alabilirsiniz. ek bilgi sağlamak için `Verbose` parametresi, cmdlet veya sağlayıcı çağırabilir [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi.

- Ürün desteği veya diğer geliştiriciler için hata ayıklama düzeyinde ayrıntı sağlamak için cmdlet veya sağlayıcı çağırabilir miyim [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi. Kullanıcı bu bilgileri kullanarak alabilirsiniz `Debug` parametresi.

Cmdlet'lerini ve sağlayıcıları, Windows PowerShell dışında bir sistem değişiklikleri bir işlemi gerçekleştirmeye çalışmadan önce onay isteği için aşağıdaki yöntemleri çağırın:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Çağrı yaparak bunu [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi kullanıcı komutu nasıl çağrılan dayalı olarak işlemini onaylamak için kullanıcıya sorar.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
