---
title: Bir Windows PowerShell sağlayıcısı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623832"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Windows PowerShell Sağlayıcısı Oluşturma

Bu bölümde, bir Windows PowerShell sağlayıcısını nasıl oluşturulduğu açıklanır. Bir Windows PowerShell sağlayıcısı iki yolla kabul edilebilir. Kullanıcıya, depolanan veri sağlayıcısını temsil eder. Örneğin, depolanan veriler, Internet Information Services (IIS) metatabanı, Microsoft Windows kayıt defteri, Windows dosya sistemi, Active Directory ve Windows PowerShell tarafından depolanan değişkenini ve diğer veri olabilir.

Geliştiriciler için Windows PowerShell sağlayıcısındaki kullanıcının erişmesi verileri ve kullanıcı arasındaki arabirimdir. Bu açısından bakıldığında, bu bölümde açıklanan sağlayıcısının her türü bir dizi temel sınıflar ve kullanıcı için belirli cmdlet'ler yaygın bir şekilde kullanıma sunmak Windows PowerShell çalışma zamanı izin arabirimleri destekler.

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell tarafından sağlanan sağlayıcıları

Windows PowerShell, bilinen veri depoları erişmek için kullanılan birkaç sağlayıcısı (örneğin, dosya sistemi sağlayıcısı, kayıt defteri sağlayıcısı ve diğer sağlayıcısı) sağlar. Windows PowerShell tarafından sağlanan sağlayıcıları hakkında daha fazla bilgi için çevrimiçi Yardım'a erişmek için aşağıdaki komutu kullanın:

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Windows PowerShell yollar kullanılarak depolanmış verilere erişme

Windows PowerShell sağlayıcıları, Windows PowerShell çalışma zamanı ve komutlar Windows PowerShell yolları kullanılarak programlı olarak erişilebilir. Çoğu zaman, bu yollar, veri sağlayıcısı üzerinden doğrudan erişmek için kullanılır. Ancak, bazı yollar verilere erişmek için Windows PowerShell uygulama programlama arabirimleri (API) kullanmak, bir cmdlet'in yürütülmesinin sağlayıcısı iç yollara çözümlenebilir. Windows PowerShell sağlayıcıları Windows PowerShell içinde nasıl çalışır hakkında daha fazla bilgi için bkz. [nasıl Windows PowerShell çalışır](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Windows PowerShell kullanarak sağlayıcısı cmdlet'leri gösterme sürücüler

Bir Windows PowerShell sağlayıcısı sanal Windows PowerShell sürücülerini kullanarak desteklenen cmdlet'lerini gösterir. Windows PowerShell, Windows PowerShell sürücüsü için aşağıdaki kurallar geçerlidir:

- Bir sürücü adı alfasayısal bir dizisi olabilir.

- Bir sürücü, geçerli herhangi bir noktada bir "Kök" olarak adlandırılan bir yolda belirtilebilir.

- Bir sürücü, yalnızca dosya sistemi gibi depolanan tüm veriler için uygulanabilir.

- Her sürücü arasında sürücüler değiştirirken içeriği korumak kullanıcının kendi geçerli çalışma konumu tutar.

## <a name="in-this-section"></a>Bu Bölümde

Aşağıdaki tabloda, birbirleri üzerinde derlenir ve kod örnekleri dahil konuları listeler. İkinci konu ile başlayarak, temel Windows PowerShell sağlayıcısı başlatılamadı ve Windows PowerShell çalışma zamanı tarafından başlatılmamış bir sonraki konu verilerine erişmek için işlevsellik ekler, bir sonraki konu veri (düzenlemek için işlevsellik ekler. öğeleri depolanmış veriler), ve benzeri.

|Konu|Açıklama|
|-----------|----------------|
|[Windows PowerShell sağlayıcınız tasarlama](./designing-your-windows-powershell-provider.md)|Bu konuda, bir Windows PowerShell sağlayıcısı uygulamadan önce dikkate almanız gereken noktalar açıklanmaktadır. Bunu Windows PowerShell sağlayıcısı temel sınıflar ve arabirimler kullanılan özetler.|
|[Temel Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md)|Bu konuda başlatıp uninitialize sağlayıcısı Windows PowerShell çalışma zamanı sağlayan bir Windows PowerShell sağlayıcısı oluşturma işlemini gösterir.|
|[Bir Windows PowerShell sürücüsünü sağlayıcı oluşturma](./creating-a-windows-powershell-drive-provider.md)|Bu konuda, bir Windows PowerShell sürücüsü bir veri deposuna erişmek kullanıcıya izin veren bir Windows PowerShell sağlayıcısı oluşturma gösterilmektedir.|
|[Bir Windows PowerShell öğesi sağlayıcı oluşturma](./creating-a-windows-powershell-item-provider.md)|Bu konuda, bir veri deposundaki öğeleri işlemek kullanıcıya izin veren bir Windows PowerShell sağlayıcısı oluşturma gösterilmektedir.|
|[Bir Windows PowerShell kapsayıcı sağlayıcı oluşturma](./creating-a-windows-powershell-container-provider.md)|Bu konuda, çok katmanlı bir veri depolarına üzerinde çalışmak kullanıcıya izin veren bir Windows PowerShell sağlayıcısı oluşturma gösterilmektedir.|
|[Bir Windows PowerShell Gezinti sağlayıcı oluşturma](./creating-a-windows-powershell-navigation-provider.md)|Bu konuda, bir veri deposu öğelerinin hiyerarşik olarak gitmek kullanıcıya izin veren bir Windows PowerShell sağlayıcısı oluşturma gösterilmektedir.|
|[Bir Windows PowerShell içerik sağlayıcı oluşturma](./creating-a-windows-powershell-content-provider.md)|Bu konuda, bir veri deposuna öğelerinin içeriğini işlemek kullanıcıya izin veren bir Windows PowerShell sağlayıcısı oluşturma gösterilmektedir.|
|[Bir Windows PowerShell özelliği sağlayıcı oluşturma](./creating-a-windows-powershell-property-provider.md)|Bu konuda, bir veri deposuna öğelerin özelliklerini değiştirmek kullanıcıya izin veren bir Windows PowerShell sağlayıcısı oluşturma gösterilmektedir.|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell nasıl çalışır?](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)
