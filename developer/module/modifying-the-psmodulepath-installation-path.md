---
title: PSModulePath yükleme yolunu değiştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846511"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>PSModulePath Yükleme Yolunu Değiştirme

`PSModulePath` Ortam değişkeni yollarınızı diske yüklü modülleri depolar. Windows PowerShell, bu değişken, kullanıcı bir modül tam yolunu belirtmediğinde modülleri bulmak için kullanır. Bu değişken yollar göründükleri sırayla aranır.

Windows PowerShell başladığında `PSModulePath` aşağıdaki varsayılan değerine sahip bir sistem ortam değişkeni olarak oluşturulur: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>PSModulePath değişkeni görüntülemek için

Belirtilen yollarını görüntülemek için `PSModulePath` değişken, aşağıdaki komutu yazın:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Konumları PSModulePath değişkeni eklemek için

Bu değişken için yol eklemek için aşağıdaki yöntemlerden birini kullanın:

- Yalnızca geçerli oturum için kullanılabilir olan bir geçici değer eklemek için komut satırında aşağıdaki komutu çalıştırın:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Her bir oturum açıldığında kullanılabilir kalıcı bir değer eklemek için bir Windows PowerShell profiliniz için aşağıdaki komutu ekleyin:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Profilleri hakkında daha fazla bilgi için bkz. [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet Kitaplığı'nda.

- Kayıt defterinde kalıcı olarak değişken eklemek, adlı yeni bir kullanıcı ortam değişkeni oluşturma `PSModulePath` kullanarak ortam değişkenlerini Düzenleyicisi'nde **Sistem Özellikleri** iletişim kutusu.

- Bir komut dosyası kullanarak kalıcı bir değişken eklemek için **SetEnvironmentVariable** ortam sınıfını yöntemi. Örneğin, aşağıdaki komut dosyasını "C:\Program Files\Fabrikam\Module yolu. bilgisayarın PSModulePath ortam değişkeninin değerine ekler Yol kullanıcı PSModulePath ortam değişkeni eklemek için "Kullanıcı" hedef ayarlayın.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Konumları PSModulePath kaldırmak için

Benzer yöntemler kullanarak değişkeninden yolları kaldırabilirsiniz: Örneğin, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` kaldıracak **c:\ModulePath** geçerli oturumun yolu.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
