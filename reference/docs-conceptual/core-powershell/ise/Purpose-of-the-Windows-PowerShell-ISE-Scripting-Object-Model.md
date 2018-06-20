---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE Betik Oluşturma Nesne Modelinin Amacı
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951333"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Windows PowerShell ISE Betik Oluşturma Nesne Modelinin Amacı

Form ve işlevi, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) ile ilişkili nesneleridir. Nesne Modeli Başvurusu, özellikleri ve bu nesnelerin kullanıma yöntemleri üye hakkında ayrıntılar sağlar. Doğrudan bu yöntemlere ve özelliklere erişmek için komut dosyalarını nasıl kullanabileceğiniz göstermek için örnekler verilmiştir. Komut dosyası nesne modeli görevleri aşağıdaki aralığı kolaylaştırır.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Windows PowerShell ISE görünümünü özelleştirme

Uygulama ayarları ve seçenekleri değiştirmek için nesne modeli kullanabilirsiniz. Örneğin, bunları aşağıdaki gibi değiştirebilirsiniz:

- Hata ayıklama çıkarır ve hatalar, uyarılar, ayrıntılı çıktı rengini değiştirebilirsiniz.
- Alın veya komut bölmesi, çıkış bölmesi ve betik bölmesine ilişkin arka plan renklerini ayarlayın.
- Çıkış bölmesinde ön plan rengini ayarlayabilirsiniz.
- Windows PowerShell ISE için yazı tipi adı ve yazı tipi boyutunu ayarlayabilirsiniz.
- Uyarılar yapılandırabilirsiniz. Bu ayar, birden çok PowerShell sekmelerdeki veya dosyayı kaydetmeden önce bir komut dosyasındaki çalıştırdığınızda bir dosya açıldığında, verilen uyarıları içerir.
- Betik bölmesine çıkış Bölmesi'üstünde olduğu betik bölmesine ve çıkış bölmesi yan yana nerede bir görünümü ve görünüm arasında geçiş yapabilirsiniz. Komut bölmesi veya çıkış bölmesi En Alta sabitleyebilirsiniz.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Windows PowerShell ISE işlevselliğini geliştirme

Windows PowerShell ISE işlevselliğini geliştirmek için nesne modeli kullanabilirsiniz. Örneğin, aşağıdakileri yapabilirsiniz:

- Ekleyebilir ve Windows PowerShell ISE kendisini örneği değiştirebilirsiniz. Örneğin, menüler değiştirmek için yeni menü öğeleri ekleme ve komut dosyaları için yeni menü öğelerini eşleyin.
- Windows PowerShell ISE düğmeleri ve menü komutlarını kullanarak gerçekleştirebileceğiniz görevlerden bazılarını gerçekleştirmek komut dosyaları oluşturun. Örneğin, Ekle, Kaldır veya PowerShell sekmesini seçin.
- Menü komutları ve düğmeleri kullanarak gerçekleştirilen görevleri tamamlama. Örneğin, bir PowerShell sekmesi yeniden adlandırabilirsiniz.
- Bir dosyayla ilişkili metin arabelleği komut bölmesi, çıkış bölmesi ve betik bölmesine yönetme. Örneğin, aşağıdakileri yapabilirsiniz:
  - Alın veya tüm metni ayarlayın.
  - Alın veya bir metin seçimini ayarlayın.
  - Komut dosyası çalıştırma veya bir komut dosyası seçili bir bölümünü çalıştırın.
  - Bir satır görünümüne gidin.
  - Metin bir şapka konumuna ekleyin.
  - Bir metin bloğunu seçin.
  - Son satır numarasını alır.
- Dosya işlemleri Örneğin, aşağıdakileri yapabilirsiniz:
  - Bir dosyayı açın, bir dosyayı kaydedin veya bir dosyayı farklı bir ad kullanarak kaydedin.
  - Son kaydedildikten sonra dosya değiştirilip değiştirilmediğini belirleyin.
  - Dosya adını alır.
  - Bir dosya seçin.

## <a name="automating-tasks"></a>Görevleri otomatikleştirme

Komut dosyası nesne modeli, sık kullanılan işlemleri için klavye kısayolları oluşturmak için kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)