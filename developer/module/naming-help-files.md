---
title: Yardım dosyalarını adlandırma | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082190"
---
# <a name="naming-help-files"></a>Yardım Dosyalarını Adlandırma

Bu konu başlığında, bir XML tabanlı Yardım dosyasını adlandırmak açıklanmaktadır böylece [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'i, bulabilirsiniz. Ad gereksinimleri, her komut türü için farklılık gösterir.

## <a name="cmdlet-help-files"></a>Cmdlet Yardım dosyaları

İçin Yardım dosyasına bir C# cmdlet tanımlanır derleme için cmdlet adı. Aşağıdaki dosya adı biçimi kullanın:

```
<AssemblyName>.dll-help.xml
```

Derleme bir iç içe modül olsa bile, derleme adı biçimi gereklidir.

Örneğin, [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet'i Microsoft.PowerShell.Diagnostics.dll derlemesinde tanımlanmıştır. `Get-Help` Cmdlet için Yardım konusunun arar `Get-WinEvent` cmdlet'i yalnızca modül dizinini Microsoft.PowerShell.Diagnostics.dll help.xml dosyasında.

## <a name="provider-help-files"></a>Sağlayıcı Yardım dosyaları

Yardım dosyası bir Windows PowerShell sağlayıcısı için sağlayıcı tanımlandığı derleme için adlandırılmalıdır. Aşağıdaki dosya adı biçimi kullanın:

```
<AssemblyName>.dll-help.xml
```

Derleme bir iç içe modül olsa bile, derleme adı biçimi gereklidir.

Örneğin, sertifika sağlayıcısı Microsoft.PowerShell.Security.dll derlemede tanımlandı. `Get-Help` Cmdlet'i yalnızca modül dizinini Microsoft.PowerShell.Security.dll help.xml dosyasında sertifika sağlayıcısı için bir Yardım konusu arar.

## <a name="function-help-files"></a>Yardım dosyaları işlevi

İşlevleri kullanarak konusunda açıklanmaktadır [açıklama tabanlı Yardım](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) veya bir XML Yardım dosyasında belirtilmiştir. İşlevi, bir XML dosyasında belirtildiği zaman, işlev olmalıdır bir `.ExternalHelp` işlevi olan XML dosyası ilişkilendirir anahtar sözcüğü açıklama satırı yapın. Aksi takdirde, `Get-Help` cmdlet Yardım dosyasını bulamıyor.

Bir işlev Yardım dosyasının adı için teknik gereksinimi yoktur. Ancak, en iyi uygulama işlevi tanımlandığı betik modülü için Yardım dosyasına ad sağlamaktır. Örneğin, aşağıdaki işlev MyModule.psm1 dosyasında tanımlanır.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM komut Yardım dosyaları

CIM komut için Yardım dosyasına CIM komut tanımlandığı CDXML dosyayı adlandırılmalıdır. Aşağıdaki dosya adı biçimi kullanın:

```
<FileName>.cdxml-help.xml
```

CIM komutları modülleri iç içe modül olarak yer alan CDXML dosyalarından tanımlanır. Windows PowerShell CIM komut işlevi olarak oturuma aktarıldığında ekler bir `.ExternalHelp` anahtar sözcüğü bir XML Yardım işlevi ilişkilendirir işlev tanımı için Dosya Açıklama CIM komut tanımlanır CDXML dosyayı adlı.

## <a name="script-workflow-help-files"></a>Betik iş akışı Yardım dosyaları

XML-tabanlı Yardım dosyaları belgelenmesi modüllerde yer alan komut dosyası iş akışları. Yardım dosyasının adı için teknik gereksinimi yoktur. Ancak, en iyi uygulama akışının tanımlandığı betik modülü için Yardım dosyasına ad sağlamaktır. Örneğin:

```
<ScriptModule>.psm1-help.xml
```

Diğer komut dosyalı komutlar, komut dosyası iş akışları gerektirmeyen bir `.ExternalHelp` anahtar sözcüğü, bir Yardım dosyası ile ilişkilendirilecek yorum. Bunun yerine, Windows PowerShell modülü dizininin XML tabanlı Yardım dosyaları için kullanıcı Arabirimi kültüre özgü alt dizinleri arar ve Yardım iş akışı içindeki tüm dosyaları arar. `.ExternalHelp` Açıklama anahtar sözcüğü göz ardı edilir.

Çünkü `.ExternalHelp` açıklama anahtar sözcüğünü sayılır `Get-Help` cmdlet'i bulabilir Yardım iş akışları için Modüller yalnızca dahil olduğunda.