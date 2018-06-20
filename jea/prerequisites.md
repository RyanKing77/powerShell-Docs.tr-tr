---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: a5cf5519b30b24d44c12bdeedcf4cd763e2edbde
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189780"
---
# <a name="prerequisites"></a>Önkoşullar

> Uygulandığı öğe: Windows PowerShell 5.0

Yalnızca yeterli Yönetimi Windows PowerShell 5.0 ve üzeri bulunan bir özelliktir.
Bu konuda JEA kullanmaya başlamak için karşılanması gereken önkoşulları açıklanmaktadır.

## <a name="install-jea"></a>JEA yükleyin

JEA Windows PowerShell 5. 0 ile kullanılabilir ve daha yüksek, ancak tam işlevsellik için sisteminizi PowerShell kullanılabilir en son sürümünü yüklemeniz önerilir.
Aşağıdaki tabloda, Windows Server'da JEA'in kullanılabilirlik açıklanmaktadır:

Sunucu işletim sistemi   | JEA kullanılabilirliği
--------------------------|--------------------------------
Windows Server 2016       | Önceden yüklenmiş
Windows Server 2012 R2    | WMF 5.1 tam işlevsellikle
Windows Server 2012       | WMF 5.1 tam işlevsellikle
Windows Server 2008 R2    | İşlevleri azaltılmış<sup>1</sup> WMF 5.1 ile

Ev veya iş bilgisayarınızda JEA de kullanabilirsiniz:

İstemci işletim sistemi   | JEA kullanılabilirliği
--------------------------|-----------------------------------------------------
Windows 10 1607 +          | Önceden yüklenmiş
Windows 10 1603, 1511     | Önceden, azaltılmış işlevsellik ile<sup>2</sup>
Windows 10 1507           | Mevcut değil
Windows 8, 8.1            | WMF 5.1 tam işlevsellikle
Windows 7                 | İşlevleri azaltılmış<sup>1</sup> WMF 5.1 ile

<sup>1</sup> JEA, Windows Server 2008 R2 veya Windows 7 üzerinde Grup yönetilen hizmet hesapları kullanacak şekilde yapılandırılamaz.
Sanal hesaplar ve diğer JEA özellikleri *olan* desteklenir.

<sup>2</sup> Windows 10 sürüm 1511 ve 1603 aşağıdaki JEA özellikleri desteklemez: Grup yönetilen hizmet hesabı, oturum yapılandırmaları koşullu erişim kuralları, kullanıcı sürücüsünde ve erişebilmesi için yerel kullanıcı hesapları olarak çalıştırmak.
Bu özellikler için destek almak için Windows 1607 (Yıldönümü güncelleştirmesi) sürümüne güncelleştirin ya da daha yüksek.

### <a name="check-which-version-of-powershell-is-installed"></a>PowerShell hangi sürümünün yüklü denetleyin

Sisteminizde yüklü PowerShell sürümünü denetlemek için kontrol `$PSVersionTable` bir Windows PowerShell isteminde değişken.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA, kullanıma hazır *ana* sürümüdür eşit veya bundan büyük **5**.
En iyi deneyim için ve en son özelliklere erişim sağlamak için PowerShell sürüme yükseltmeniz önerilir **5.1** mümkün olduğunda.

### <a name="install-windows-management-framework"></a>Windows Management Framework'ü yükleme

PowerShell daha eski bir sürümü çalıştırıyorsanız, sisteminizi en son Windows Management Framework (WMF) güncelleştirmesi ile güncelleştirmeniz gerekir.
Güncelleştirme paketleri ve en son WMF sürüm notlarını bağlantı bulunan [Yükleme Merkezi'nden](https://aka.ms/WMF5).

Tüm sunucularınız yükseltmeden önce WMF İş yükünüzün uyumluluğunu test önerilir.

Windows 10 kullanıcıları Windows PowerShell geçerli sürümünü elde etmek için en son özellik güncelleştirmeleri yüklemeniz gerekir.

## <a name="enable-powershell-remoting"></a>PowerShell uzaktan iletişimini etkinleştirme

PowerShell uzaktan iletişimi JEA yerleşik olan temel sağlar.
Bu nedenle PowerShell uzaktan iletişimi etkin emin olmak gerekli olan ve [düzgün güvenli](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) JEA kullanmadan önce sisteminizdeki.

PowerShell uzaktan iletişimi, Windows Server 2012, 2012 R2 ve 2016 varsayılan olarak etkindir.
PowerShell uzaktan iletişimi yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak etkinleştirebilirsiniz.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell modülü ve komut dosyası bloğunun günlüğünü (isteğe bağlı) etkinleştirme

Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemler için günlük kaydını etkinleştirin.
PowerShell günlük modülü için JEA gerekli değildir, ancak bu komutları kullanıcıların çalışmasını sağlamak için açmanız önerilir merkezi bir konumda kaydedilir.

PowerShell modülü günlüğü ilkesini Grup İlkesi kullanarak yapılandırabilirsiniz.

1. Bir iş istasyonunda yerel Grup İlkesi Düzenleyicisi'ni veya bir Grup İlkesi nesnesi bir Active Directory etki alanı denetleyicisinde Grup İlkesi Yönetim Konsolu'nu açın
2. Gidin **Bilgisayar Yapılandırması\\Yönetim Şablonları\\Windows bileşenleri\\Windows PowerShell**
3. Çift tıklatın **modülü günlük özelliğini açın**
4. Tıklatın **etkin**
5. Seçenekler bölümünde tıklayın **Göster** modül adlarını yanındaki
6. Türü "**\***" açılır pencerede içinde. PowerShell komutları tüm modüllerden oturum bildirir.
7. Tıklatın **Tamam** ilkesini ayarlamak için
8. Çift tıklatın **PowerShell betik bloğu günlük özelliğini açın**
9. Tıklatın **etkin**
10. Tıklatın **Tamam** ilkesini ayarlamak için
11. (Etki alanına katılmış makinelerde yalnızca) Çalıştırma **gpupdate** veya güncelleştirilmiş ilke işlemek ve ayarları uygulamak Grup İlkesi için bekleyin

Grup İlkesi aracılığıyla sistem genelinde PowerShell transcription de etkinleştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Bir rol özelliği dosyası oluşturma](role-capabilities.md)
- [Oturum yapılandırma dosyası oluşturma](session-configurations.md)

## <a name="see-also"></a>Ayrıca bkz:

- [PowerShell uzaktan iletişimi ve WinRM güvenlik hakkında ek bilgi](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ mavi takım* güvenlik blog gönderisi](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)