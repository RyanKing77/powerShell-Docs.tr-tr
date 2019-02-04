---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688360"
---
# <a name="prerequisites"></a>Önkoşullar

> Şunun için geçerlidir: Windows PowerShell 5.0

Yeterli yönetim, Windows PowerShell 5.0 ve üzeri bulunan bir özelliktir.
Bu konuda jea'yı kullanmaya başlamak için karşılanması gereken önkoşulları açıklanmaktadır.

## <a name="install-jea"></a>Jea'yı yükleme

JEA kullanılabilir Windows PowerShell 5.0 ve üzeri, ancak tam işlevsellik için sisteminiz için PowerShell kullanılabilir en son sürümünü yüklemeniz önerilir.
Aşağıdaki tabloda, Windows Server üzerinde JEA'ün kullanılabilirlik açıklanmaktadır:

Sunucu işletim sistemi   | JEA kullanılabilirlik
--------------------------|--------------------------------
Windows Server 2016       | Önceden
Windows Server 2012 R2    | WMF 5.1 tam işlevselliğiyle
Windows Server 2012       | WMF 5.1 tam işlevselliğiyle
Windows Server 2008 R2    | İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile

JEA, ev veya iş bilgisayarınızda de kullanabilirsiniz:

İstemci işletim sistemi   | JEA kullanılabilirlik
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Önceden
Windows 10 1603, 1511     | Önceden, ile işlevselliği azaltılmış<sup>2</sup>
Windows 10 1507           | Mevcut değil
Windows 8, 8.1            | WMF 5.1 tam işlevselliğiyle
Windows 7                 | İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile

<sup>1</sup> JEA, Grup yönetilen hizmet hesapları, Windows Server 2008 R2 veya Windows 7'yi kullanmak için yapılandırılamaz.
Sanal hesaplar ve diğer JEA özellikleri *olan* desteklenir.

<sup>2</sup> Windows 10 sürüm 1511 ve 1603 aşağıdaki JEA özellikleri desteklemez: Grup yönetilen hizmet hesabı, oturum yapılandırmaları koşullu erişim kuralları, kullanıcı sürücüsünde ve erişebilmesi için yerel kullanıcı hesapları olarak çalıştırmak.
Bu özellikler için destek almak için sürüm 1607 (Yıldönümü güncelleştirmesi) için Windows update veya üzeri.

### <a name="check-which-version-of-powershell-is-installed"></a>Yüklü PowerShell sürümünü denetleme

Hangi PowerShell sürümünü sisteminizde yüklü olmadığını denetlemek için kontrol `$PSVersionTable` bir Windows PowerShell isteminde değişken.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA, kullanıma hazır *ana* sürümüdür eşit veya ondan **5**.
En iyi deneyimi ve tüm yeni özelliklere erişimi için PowerShell sürümüne yükseltmeniz kesinlikle önerilir **5.1** mümkün olduğunda.

### <a name="install-windows-management-framework"></a>Windows Management Framework'ü yükleme

PowerShell daha eski bir sürümünü çalıştırıyorsanız, sisteminizi en son Windows Management Framework (WMF) güncelleştirmesi ile güncelleştirmeniz gerekecektir.
Güncelleştirme paketlerini ve en son WMF sürüm notlarını bağlantı kullanılabilir [İndirme Merkezi](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).

Tüm sunucularınızı yükseltmeden önce WMF İş yükünüzün uyumluluğu test önemle tavsiye edilir.

Windows 10 kullanıcıları, Windows PowerShell'ın geçerli sürümü almak için en son özellik güncelleştirmeleri yüklemeniz gerekir.

## <a name="enable-powershell-remoting"></a>PowerShell uzaktan iletişimini etkinleştirme

PowerShell uzaktan iletişimini JEA yerleşik bir temel sunar.
Bu nedenle PowerShell uzaktan iletişimini etkin emin olmak gerekli olan ve [düzgün güvenli](/powershell/scripting/setup/winrmsecurity) sisteminize JEA kullanmadan önce.

PowerShell uzaktan iletişimini, Windows Server 2012, 2012 R2 ve 2016 varsayılan olarak etkindir.
PowerShell uzaktan iletişimini yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak etkinleştirebilirsiniz.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell modülü ve komut dosyası bloğu günlüğünü (isteğe bağlı) etkinleştirme

Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemleri için günlük kaydını etkinleştirir.
PowerShell modülü günlüğü JEA için gerekli değildir, ancak bu komutları kullanıcıların çalışmasını sağlamak için açmanız önerilir merkezi bir konuma kaydedilir.

Grup İlkesi kullanarak PowerShell modülü oturum ilkesi yapılandırabilirsiniz.

1. Bir iş istasyonundaki yerel Grup İlkesi Düzenleyicisi'ni veya bir Grup İlkesi nesnesi bir Active Directory etki alanı denetleyicisinde Grup İlkesi Yönetim Konsolu'nu açma
2. Gidin **Bilgisayar Yapılandırması\\Yönetim Şablonları\\Windows bileşenleri\\Windows PowerShell**
3. Çift tıklayın **modülü oturum açın**
4. Tıklayın **etkin**
5. Seçenekler bölümünde tıklayarak **Göster** modül adlarını yanındaki
6. Tür `\*` açılır pencerede içinde. Bu PowerShell komutları tüm modüllerden oturum bildirir.
7. Tıklayın **Tamam** ilkesini ayarlamak için
8. Çift tıklayın **PowerShell komut dosyası bloğu oturum açın**
9. Tıklayın **etkin**
10. Tıklayın **Tamam** ilkesini ayarlamak için
11. (Etki alanına katılmış makinelerde yalnızca) Çalıştırma `gpupdate` veya güncelleştirilmiş ilke işlemek ve ayarları uygulamak Grup İlkesi için bekleyin

Sistem genelinde PowerShell transkripsiyonu Grup İlkesi aracılığıyla da etkinleştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Bir rol özelliği dosyası oluşturma](role-capabilities.md)

[Oturum yapılandırma dosyası oluşturma](session-configurations.md)

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell uzaktan iletişimini ve WinRM güvenliği hakkında ek bilgi](/powershell/scripting/setup/winrmsecurity)

[*PowerShell mavi takımın ♥* güvenlik blog gönderisi](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)