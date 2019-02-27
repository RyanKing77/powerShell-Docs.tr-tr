---
title: Cmdlet özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 2bc03aaade1f18d48f65ecf5f9ee437ffaf07f92
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852013"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet Özniteliği Bildirimi

Cmdlet öznitelik, bir cmdlet olarak bir Microsoft .NET Framework sınıf tanımlar ve fiil ve isim cmdlet'ini çağırmak için kullanılan belirtir.

## <a name="syntax"></a>Sözdizimi

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parametreler

`VerbName` ([System.String](/dotnet/api/System.String)) gereklidir. Cmdlet fiilini belirtir. Bu eylem, cmdlet tarafından gerçekleştirilecek eylemi belirtir. Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md) ve [gerekli geliştirme yönergeleri](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) gereklidir. Cmdlet isim belirtir. Bu isim cmdlet temel aldığı kaynak belirtir. Cmdlet isimleri hakkında daha fazla bilgi için bkz: [cmdlet'i bildirimi](./cmdlet-class-declaration.md) ve [geliştirme yönergeleri kesinlikle teşvik](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. `True` cmdlet çağrıları desteklediğini gösterir [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi cmdlet sistem değişiklikleri bir eylem gerçekleştirilmeden önce kullanıcıdan istemek için bir yol sağlar. `False`, varsayılan değeri belirten cmdlet çağrılarını desteklemiyor [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi. Onay istekleri hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) isteğe bağlı parametre adı. Ne zaman cmdlet'inin eylemi için yapılan bir çağrı tarafından onaylanması belirtir [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi. [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Confirmımpact değeri (varsayılan olarak, Orta) cmdlet'inin değerinden büyük veya eşit olduğunda çağrılacak `$ConfirmPreference` değişkeni. Bu parametre belirtilmelidir yalnızca `SupportsShouldProcess` parametre belirtildi.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) isteğe bağlı parametre adı. Windows PowerShell çalışma zamanı kullanmak için hangi parametre kümesi belirleyemediğinde kullanmayı denerse, varsayılan parametre belirtir. Bu durumda her bir parametre zorunlu bir parametre parametresi benzersiz hale getirerek kaldırılabilir dikkat edin.

Windows PowerShell varsayılan parametre kümesi adı belirtilmiş olsa bile varsayılan parametresinde burada kullanılamaz bir durumda yoktur. Windows PowerShell çalışma zamanı, parametre kümeleri yalnızca nesne türüne göre arasında ayrım yapamaz. Örneğin, bir dizeyi dosya yolu ve başka bir küme alan bir parametre kümesi varsa alır bir **FileInfo** doğrudan, Windows PowerShell kullanmak üzere hangi parametresi için geçirilen değerlere göre belirleyemiyor nesnesi cmdlet'ini ve varsayılan parametre kümesi kullanmaz. Bu durumda, varsayılan parametre kümesi adı belirtin, Windows PowerShell belirsiz parametre kümesi hata iletisi oluşturur.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı. `True` cmdlet'i bir işlem içinde kullandığını gösterir. Zaman `True` belirtilen, Windows PowerShell çalışma zamanı ekler `UseTransaction` parametresini cmdlet'e parametre listesi. `False`, varsayılan değeri belirten cmdlet'i bir işlem içinde kullanılamaz.

## <a name="remarks"></a>Açıklamalar

- Kayıtlı cmdlet'inize tanımlamak ve cmdlet'inize bir betiğin içerisinden çağrılacak birlikte fiil ve isim kullanılır.

- Cmdlet Windows PowerShell konsolundan çağrıldığında, aşağıdaki komutu komut benzer şekilde görünür:

**VerbName NounName**

- Windows PowerShell dışında kaynakları değiştirmek tüm cmdlet'ler içermelidir `SupportsShouldProcess` çağırmak cmdlet sağlayan Cmdlet öznitelik bildirildiğinde anahtar sözcüğü [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet eylemi gerçekleştirmeden önce yöntemi. Varsa [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrısı döndürür `false`, eylem yok edilmelidir. Tarafından oluşturulan onay istekleri hakkında daha fazla bilgi için [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağırmak için bkz: [onay isteme](./requesting-confirmation-from-cmdlets.md).

`Confirm` Ve `WhatIf` cmdlet parametreleri destekleyen cmdlet'ler kullanılabilir [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağırır.

## <a name="example"></a>Örnek

Aşağıdaki sınıf tanımını cmdlet'i özniteliği için .NET Framework sınıf tanımlamak için kullanır. bir **Get-Proc** cmdlet'i yerel bilgisayar üzerinde çalışan işlemleri hakkındaki bilgileri alır.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Hakkında daha fazla bilgi için **Get-Proc** cmdlet'ini bkz [GetProc öğretici](./getproc-tutorial.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
