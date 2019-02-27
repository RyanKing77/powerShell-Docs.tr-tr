---
title: Bir Windows PowerShell ek bileşenini yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: ee8a6538fa6ad4d0f480f2dac46fe0f823a38be8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845251"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Windows PowerShell Ek Bileşeni Yazma

Bu örnek, bir derlemede tüm cmdlet'leri ve Windows PowerShell sağlayıcıları kaydetmek için kullanılan bir Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir.

Bu tür ek bileşeninin hangi cmdlet'lerini ve sağlayıcıları kaydetmek istediğiniz seçmeyin. Ne kayıtlı seçmenizi sağlayan bir ek bileşenini yazmak için bkz: [bir özel Windows PowerShell ek bileşenini yazma](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Windows PowerShell Ek Bileşeni Yazma

1. RunInstallerAttribute özniteliği ekleyin.

2. Türetilen bir ortak sınıf oluşturun [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) sınıfı.

    Bu örnekte, "GetProcPSSnapIn01" sınıf adıdır.

3. (Gerekli) ek bileşenini adı için bir ortak özelliği ekleyin. Ek bileşenler adlandırırken şu karakterlerin hiçbirini kullanmayın: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    Bu örnekte ek bileşenini "GetProcPSSnapIn01" adıdır.

4. (Gerekli) ek bileşenini, satıcı için ortak özelliği ekleyin.

    Bu örnekte, satıcı "Microsoft" ise.

5. Satıcı kaynak ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.

    Bu örnekte, "GetProcPSSnapIn01, Microsoft" Satıcı kaynaktır.

6. (Gerekli) ek bileşenini açıklaması için bir ortak özelliği ekleyin.

    Bu örnekte, "Get-proc cmdlet kaydeder bir Windows PowerShell ek bileşenini budur" açıklamasıdır.

7. Açıklama kaynağı ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.

    Bu örnekte, "GetProcPSSnapIn01, bu cmdlet get-proc kaydeder bir Windows PowerShell ek bileşenini bir" Satıcı kaynaktır.

## <a name="example"></a>Örnek

Bu örnekte, Get-Proc cmdlet Windows PowerShell shell'de kaydetmek için kullanılan bir Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir. Bu örnekte, tam derleme yalnızca GetProcPSSnapIn01 eklentisini sınıfı ve Get-Proc cmdlet'i sınıfı içerecektir dikkat edin.

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
