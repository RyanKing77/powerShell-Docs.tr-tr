---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE Betik Oluşturma Nesne Modelinin Amacı
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086825"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Windows PowerShell ISE Betik Oluşturma Nesne Modelinin Amacı

Nesneleri, form ve işlevi, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) ile ilişkilendirilir. Nesne Modeli Başvurusu özellikleri ve bu nesneler kullanıma yöntemleri üyeyle ilgili ayrıntıları sağlar. Örnekler, doğrudan bu yöntemlere ve özelliklere erişmek için komut dosyalarını nasıl kullanabileceğinizi gösterecek şekilde sağlanır. Betik oluşturma nesne modeli, aşağıdaki dizi kolaylaştırır.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Windows PowerShell ISE görünümünü özelleştirme

Uygulama ayarları ve seçenekleri değiştirmek için nesne modeli kullanabilirsiniz. Örneğin, bunları aşağıdaki gibi değiştirebilirsiniz:

- Hata ayıklama çıkarır ve hataları, uyarıları, ayrıntılı çıkış rengini değiştirebilirsiniz.
- Get veya komut bölmesi, çıkış bölmesi ve betik bölmesini arka plan renklerini ayarlayın.
- Çıkış Bölmesi ' ön plan rengini ayarlayabilirsiniz.
- Windows PowerShell ISE için yazı tipi boyutunu ve yazı tipi adı ayarlayabilirsiniz.
- Uyarıları yapılandırabilirsiniz. Bu ayar birden fazla PowerShell sekme veya dosyayı kaydetmeden önce bir betik dosyasında çalıştırıldığında bir dosya açıldığında, verilen uyarıları içerir.
- Betik bölmesini çıkış Bölmesi'üstünde olduğu betik bölmesi ve çıkış Bölmesi ' yan yana olduğu bir görünümü ve görünüm arasında geçiş yapabilirsiniz. Alt veya üst çıkış bölmesi için komut bölmesine sabitleyebilirsiniz.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Windows PowerShell ISE işlevselliğini geliştirme

Windows PowerShell ISE işlevselliğini geliştirmek için nesne modeli kullanabilirsiniz. Örneğin, şunları yapabilirsiniz:

- Ekleyebilir ve Windows PowerShell ISE kendi örneğini değiştirebilirsiniz. Örneğin, menüleri değiştirmek için yeni menü öğeleri ekleme ve betikleri için yeni menü öğelerini eşleyin.
- Windows PowerShell ISE'de düğmeler ve menü komutlarını kullanarak gerçekleştirebileceğiniz görevlerden bazılarını gerçekleştirmek betikleri oluşturun. Örneğin, Ekle, Kaldır veya PowerShell sekmesini seçin.
- Menü komutları ve düğmeleri kullanarak gerçekleştirilebilir tamamlayan görev. Örneğin, bir PowerShell sekmesi yeniden adlandırabilirsiniz.
- Bir dosyayla ilişkili metin arabelleği komut bölmesi, çıkış bölmesi ve betik bölmesini işleyin. Örneğin, şunları yapabilirsiniz:
  - Alın veya tüm metni ayarlayın.
  - Alın veya metin seçimi ayarlayın.
  - Komut dosyası çalıştırma veya seçili bir bölümü bir komut çalıştırın.
  - Bir satır görünümüne gidin.
  - Giriş işareti konumuna metin ekleyin.
  - Metin bloğu seçin.
  - Son satır numarasını alın.
- Dosya işlemleri gerçekleştirin. Örneğin, şunları yapabilirsiniz:
  - Bir dosyayı açmak, bir dosyaya kaydedin veya farklı bir ad kullanarak bir dosyaya kaydedin.
  - Son kaydedildikten sonra bir dosyanın değiştirilip değiştirilmediğini belirler.
  - Dosya adını alın.
  - Bir dosya seçin.

## <a name="automating-tasks"></a>Görevleri otomatikleştirme

Betik oluşturma nesne modeli, sık kullanılan işlemler için klavye kısayolları oluşturmak için kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)