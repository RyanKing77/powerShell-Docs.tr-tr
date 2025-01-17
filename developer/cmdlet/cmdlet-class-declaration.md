---
title: Cmdlet'i sınıf bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068649"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet Sınıf Bildirimi

Microsoft .NET Framework sınıf belirterek bir cmdlet bildirilen **cmdlet'i** öznitelik olarak meta veri sınıfı. ( **Cmdlet'i** tüm cmdlet'ler için tek gereken özniteliği bir özniteliktir). Belirttiğinizde **cmdlet'i** özniteliği, kullanıcı cmdlet'e tanımlayan fiil-isim çift belirtmeniz gerekir. Ayrıca, cmdlet destekleyen Windows PowerShell işlevler açıklamanız gerekir. Belirtmek için kullanılan bildirim sözdizimi hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).

> [!NOTE]
> **Cmdlet'i** özniteliği tarafından tanımlanan [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) sınıfı. Bu sınıf özelliklerini öznitelik bildirdiğinizde, kullanılan bildirim parametrelere karşılık gelir.

## <a name="nouns"></a>Adlar

Cmdlet isim cmdlet yapan kaynakları belirtir. İsim cmdlet'lerinizi diğer cmdlet'lerinden ayırır.

İsimleri, cmdlet adları olmalıdır ve söz konusu olduğunda genel isimleri, özel, gibi *sunucu*, kaynağınızı benzer diğer kaynaklardan ayırır kısa bir önek eklemek idealdir. Örneğin, bir isim öneki içeren bir cmdlet adı olan `Get-SQLServer`. Belirli bir isim daha genel bir fiil birleşimi cmdlet eylemi tarafından kolayca bulmak ve gereksiz cmdlet adı çoğaltma kaçınarak Bu cmdlet tarafından kaynağı tanımlamak kullanıcı sağlar.

Cmdlet adları kullanılamaz, özel karakterler bir listesi için bkz. [gerekli geliştirme yönergeleri](./required-development-guidelines.md).

## <a name="verbs"></a>Fiiller

Fiil belirttiğinizde, geliştirme yönergeleri Windows PowerShell tarafından sağlanan önceden tanımlanmış fiillerden biri kullanmanızı gerektirir. Bu önceden tanımlanmış fiillerden biri kullanarak yazdığınız cmdlet'leri ve Microsoft tarafından ve başkaları tarafından yazılan cmdlet'ler arasında tutarlılığı garanti eder. Örneğin, "Al" fiili veri almak için cmdlet'leri kullanılır.

Fiiller yönergeleri hakkında daha fazla bilgi için bkz. [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md). Cmdlet adları kullanılamaz, özel karakterler bir listesi için bkz. [gerekli geliştirme yönergeleri](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Windows PowerShell işlevselliği destekleme

**Cmdlet'i** özniteliği de cmdlet'inize bazı Windows PowerShell tarafından sağlanan genel işlevlerini destekler belirtmenize olanak verir. Bu, kullanıcı geri bildirim onayı (ShouldProcess özelliği desteği olarak adlandırılır) gibi ortak işlevselliği ve işlemler için desteği içerir. (İşlemler için destek Windows PowerShell 2. 0'de sunulmuştur).

Belirtmek için kullanılan bildirim sözdizimi hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Cmdlet'i sınıf tanımı

Aşağıdaki kod, GetProc cmdlet'i sınıf tanımıdır. Bu Pascal casing kullanılır ve sınıf adını fiil ve isim cmdlet içerir dikkat edin.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal büyük/küçük harf

Cmdlet adı Pascal kullanarak büyük/küçük harf. Örneğin, `Get-Item` ve `Get-ItemProperty` cmdlet'leri cmdlet'leri adlandırırken büyük küçük harf kullanımının doğru şekilde gösterir.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute bildirimi](./cmdlet-attribute-declaration.md)

[Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
