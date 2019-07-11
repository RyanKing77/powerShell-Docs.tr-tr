---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734285"
---
# <a name="prerequisites"></a>Önkoşullar

Yeterli yönetim PowerShell 5.0 ve üzeri bulunan bir özelliktir. Bu makalede jea'yı kullanmaya başlamak için karşılanması gereken önkoşulları açıklanır.


## <a name="check-which-version-of-powershell-is-installed"></a>Yüklü PowerShell sürümünü denetleme

Hangi PowerShell sürümünü sisteminizde yüklü olmadığını denetlemek için kontrol `$PSVersionTable` bir Windows PowerShell isteminde değişken.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA kullanılabilir PowerShell 5.0 ve üzeri. Tam işlevsellik için sisteminiz için PowerShell kullanılabilir en son sürümünü yüklemeniz önerilir. Aşağıdaki tabloda, Windows Server üzerinde JEA'ün kullanılabilirlik açıklanmaktadır:

| Sunucu işletim sistemi |                JEA kullanılabilirlik                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Önceden                                   |
| Windows Server 2012 R2  | WMF 5.1 tam işlevselliğiyle                |
| Windows Server 2012     | WMF 5.1 tam işlevselliğiyle                |
| Windows Server 2008 R2  | İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile |

JEA, ev veya iş bilgisayarınızda de kullanabilirsiniz:

| İstemci işletim sistemi |                   JEA kullanılabilirlik                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Önceden                                         |
| Windows 10 1603, 1511   | Önceden, ile işlevselliği azaltılmış<sup>2</sup> |
| Windows 10 1507         | Mevcut değil                                        |
| Windows 8, 8.1          | WMF 5.1 tam işlevselliğiyle                      |
| Windows 7               | İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile       |

- <sup>1</sup> JEA, Windows Server 2008 R2 veya Windows 7 Grup yönetilen hizmet hesaplarını kullanmak için yapılandırılamaz. Sanal hesaplar ve diğer JEA özellikleri *olan* desteklenir.

- <sup>2</sup> aşağıdaki JEA özellikleri, Windows 10 sürüm 1511 ve 1603 desteklenmez:

  - Bir grup yönetilen hizmet hesabı olarak çalışıyor
  - Oturum yapılandırmaları koşullu erişim kuralları
  - Kullanıcı sürücü
  - Yerel kullanıcı hesapları için erişim verme

  Bu özellikler için destek almak için sürüm 1607 (Yıldönümü güncelleştirmesi) için Windows update veya üzeri.

### <a name="install-windows-management-framework"></a>Windows Management Framework'ü yükleme

PowerShell daha eski bir sürümünü çalıştırıyorsanız, en son Windows Management Framework (WMF) güncelleştirmesiyle sisteminizi güncelleştirmeniz gerekebilir. Daha fazla bilgi için [WMF belgeleri](/powershell/wmf/overview).

Tüm sunucularınızı yükseltmeden önce WMF İş yükünüzün uyumluluğu test önerilir.

Windows 10 kullanıcıları, Windows PowerShell'ın geçerli sürümü almak için en son özellik güncelleştirmeleri yüklemeniz gerekir.

## <a name="enable-powershell-remoting"></a>PowerShell uzaktan iletişimini etkinleştirme

PowerShell uzaktan iletişimini JEA yerleşik bir temel sunar. PowerShell uzaktan iletişimini etkin ve JEA kullanmadan önce düzgün şekilde güvenliğinin emin olmak gereklidir. Daha fazla bilgi için [WinRM güvenlik](/powershell/scripting/learn/remoting/winrmsecurity).

PowerShell uzaktan iletişimini, Windows Server 2012, 2012 R2 ve 2016 varsayılan olarak etkindir. PowerShell uzaktan iletişimini yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak etkinleştirebilirsiniz.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell modülü ve komut dosyası bloğu günlüğünü (isteğe bağlı) etkinleştirme

Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemleri için günlük kaydını etkinleştirir. PowerShell modülü günlüğü JEA için gerekli değildir, ancak komutları kullanıcıların çalışmasını sağlamak için günlüğe kaydetmeyi önerilir merkezi bir konuma kaydedilir.

Grup İlkesi kullanarak PowerShell modülü oturum ilkesi yapılandırabilirsiniz.

1. Bir iş istasyonundaki yerel Grup İlkesi Düzenleyicisi'ni veya bir Grup İlkesi nesnesi bir Active Directory etki alanı denetleyicisinde Grup İlkesi Yönetim Konsolu'nu açma
2. Gidin **Bilgisayar Yapılandırması\\Yönetim Şablonları\\Windows bileşenleri\\Windows PowerShell**
3. Çift **modülü günlüğünü etkinleştirme**
4. Tıklayın **etkin**
5. Seçenekler bölümünde tıklayarak **Göster** modül adlarını yanındaki
6. Tür `*` komutları tüm modüllerden oturum açılan penceresinde.
7. Tıklayın **Tamam** ilkesini ayarlamak için
8. Çift **günlük PowerShell komut dosyası bloğu üzerinde Aç**
9. Tıklayın **etkin**
10. Tıklayın **Tamam** ilkesini ayarlamak için
11. (Etki alanına katılmış makinelerde yalnızca) Çalıştırma `gpupdate` veya güncelleştirilmiş ilke işlemek ve ayarları uygulamak Grup İlkesi için bekleyin

Sistem genelinde PowerShell transkripsiyonu Grup İlkesi aracılığıyla da etkinleştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Bir rol özelliği dosyası oluşturma](role-capabilities.md)

[Oturum yapılandırma dosyası oluşturma](session-configurations.md)

## <a name="see-also"></a>Ayrıca bkz.

[WinRM güvenlik](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ mavi takım](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
