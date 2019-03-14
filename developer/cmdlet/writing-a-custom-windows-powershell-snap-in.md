---
title: Bir özel Windows PowerShell ek bileşenini yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795598"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Özel Windows PowerShell Ek Bileşeni Yazma

Bu örnek, bazı cmdlet'ler kaydeder bir Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir.

Bu tür ek bileşeninin hangi cmdlet'leri, sağlayıcıları, türleri veya biçimleri kaydetmek için belirtin. Bir derlemede tüm cmdlet'leri ve sağlayıcıları kaydettirir bir ek bileşenini yazma hakkında daha fazla bilgi için bkz. [yazma bir Windows PowerShell ek bileşenini](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Bir Windows PowerShell ek bileşenini yazmak için bazı cmdlet'ler kaydeder.

1. RunInstallerAttribute özniteliği ekleyin.

2. Türetilen bir ortak sınıf oluşturun [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) sınıfı.

   Bu örnekte, "CustomPSSnapinTest" sınıf adıdır.

3. (Gerekli) ek bileşenini adı için bir ortak özelliği ekleyin. Ek bileşenler adlandırırken şu karakterlerin hiçbirini kullanmayın: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   Bu örnekte ek bileşenini "CustomPSSnapInTest" adıdır.

4. (Gerekli) ek bileşenini, satıcı için ortak özelliği ekleyin.

   Bu örnekte, satıcı "Microsoft" ise.

5. Satıcı kaynak ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.

   Bu örnekte, "CustomPSSnapInTest, Microsoft" Satıcı kaynaktır.

6. (Gerekli) ek bileşenini açıklaması için bir ortak özelliği ekleyin.

   Bu örnekte, bir açıklaması verilmiştir: "Bu bir özel Windows PowerShell ek-Test-HelloWorld ve Test CustomSnapinTest cmdlet'leri içeren bileşenidir".

7. Açıklama kaynağı ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.

   Bu örnekte, "CustomPSSnapInTest, bir özel Windows PowerShell Test-HelloWorld ve Test CustomSnapinTest cmdlet'leri içeren eklentisini budur" Satıcı kaynaktır.

8. Özel ek bileşenini (isteğe bağlı) kullanarak ait cmdlet'lerin belirtin [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) sınıfı. Buraya eklenen bilgilerin (cmdlet Yardım dosya adının biçimi name.dll help.xml olmalıdır) cmdlet Yardım dosyası adı cmdlet ve .NET türü adını içerir.

   Bu örnek, Test-HelloWorld ve TestCustomSnapinTest cmdlet'leri ekler.

9. Özel ek bileşenini (isteğe bağlı) ait sağlayıcılarını belirtin.

   Bu örnek, bir sağlayıcısı belirtmiyor.

10. Özel ek bileşenini (isteğe bağlı) ait türlerini belirtin.

    Bu örnek, herhangi bir tür belirtmiyor.

11. Özel ek bileşenini (isteğe bağlı) ait biçimleri belirtin.

    Bu örnek, diğer biçimleri belirtmiyor.

## <a name="example"></a>Örnek

Bu örnekte, Test-HelloWorld ve Test CustomSnapinTest cmdlet'lerini kaydetmek için kullanılan bir özel Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir. Bu örnekte, tam derleme diğer cmdlet'leri ve bu eklenti tarafından kayıtlı değil sağlayıcılarını içerebilir dikkat edin.

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

Eklentileri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) içinde [Windows PowerShell Programcı Kılavuzu](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
