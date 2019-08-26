---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017940"
---
# <a name="prerequisites"></a>Önkoşullar

Yalnızca PowerShell 5,0 ve üzeri sürümlerde bulunan bir özelliktir. Bu makalede, JEA kullanmaya başlamak için karşılanması gereken önkoşullar açıklanmaktadır.


## <a name="check-which-version-of-powershell-is-installed"></a>Hangi PowerShell sürümünün yüklü olduğunu denetleyin

Sisteminizde hangi PowerShell sürümünün yüklü olduğunu denetlemek için bir Windows PowerShell komut isteminde `$PSVersionTable` değişkeni denetleyin.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA, PowerShell 5,0 ve üzeri sürümlerde kullanılabilir. Tam işlevsellik için, sisteminizde kullanılabilir olan PowerShell 'in en son sürümünü yüklemenizi öneririz. Aşağıdaki tabloda, JEA 'nın Windows Server 'da kullanılabilirliği açıklanmıştır:

| Sunucu Işletim sistemi |                JEA kullanılabilirliği                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016 +    | Önceden yüklenmiş                                   |
| Windows Server 2012 R2  | WMF 5,1 ile tam işlevsellik                |
| Windows Server 2012     | WMF 5,1 ile tam işlevsellik                |
| Windows Server 2008 R2  | WMF 5,1 ile azaltılmış işlevsellik<sup>1</sup> |

JEA 'yı evinizde veya iş bilgisayarınızda da kullanabilirsiniz:

| İstemci Işletim sistemi |                   JEA kullanılabilirliği                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607 +        | Önceden yüklenmiş                                         |
| Windows 10 1603, 1511   | Önceden yüklenmiş, azaltılmış işlevsellik<sup>2</sup> |
| Windows 10 1507         | Mevcut değil                                        |
| Windows 8, 8,1          | WMF 5,1 ile tam işlevsellik                      |
| Windows 7               | WMF 5,1 ile azaltılmış işlevsellik<sup>1</sup>       |

- <sup>1</sup> Jea, windows Server 2008 R2 veya Windows 7 ' de grup tarafından yönetilen hizmet hesaplarını kullanacak şekilde yapılandırılamaz. Sanal hesaplar ve diğer JEA özellikleri desteklenir.

- <sup>2</sup> aşağıdaki Jea özellikleri 1511 ve 1603 Windows 10 sürümlerinde desteklenmez:

  - Grup tarafından yönetilen hizmet hesabı olarak çalışıyor
  - Oturum yapılandırmalarında koşullu erişim kuralları
  - Kullanıcı sürücüsü
  - Yerel Kullanıcı hesaplarına erişim verme

  Bu özelliklere yönelik destek almak için Windows 'u sürüm 1607 (yıldönümü güncelleştirmesi) veya sonraki bir sürüme güncelleştirin.

### <a name="install-windows-management-framework"></a>Windows Management Framework 'Ü yükler

PowerShell 'in eski bir sürümünü çalıştırıyorsanız sisteminizi en son Windows Management Framework (WMF) güncelleştirmesiyle güncelleştirmeniz gerekebilir. Daha fazla bilgi için bkz. [WMF belgeleri](/powershell/wmf/overview).

Tüm sunucularınızı yükseltmeden önce iş yükünüzün WMF ile uyumluluğunu test etmeniz önerilir.

Windows 10 kullanıcıları, geçerli Windows PowerShell sürümünü edinmek için en son özellik güncelleştirmelerini yüklemelidir.

## <a name="enable-powershell-remoting"></a>PowerShell uzaktan iletişimini etkinleştir

PowerShell Remoting, JEA 'nın oluşturulduğu temeli sağlar. JEA kullanabilmeniz için PowerShell Remoting 'in etkinleştirildiğinden ve düzgün şekilde güvende olduğundan emin olmanız gerekir. Daha fazla bilgi için bkz. [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).

PowerShell uzaktan Iletişimi Windows Server 2012, 2012 R2 ve 2016 üzerinde varsayılan olarak etkindir. Yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak PowerShell uzaktan iletişimini etkinleştirebilirsiniz.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell modülünü ve betik bloğu günlüğünü etkinleştir (isteğe bağlı)

Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemleri için günlük kaydını etkinleştirir. PowerShell modülü günlüğü JEA için gerekli değildir, ancak kullanıcıların çalıştırdığı komutların merkezi bir konumda günlüğe kaydedilmesini sağlamak için günlüğe kaydetmeyi açmanız önerilir.

Grup ilkesi kullanarak PowerShell modülü günlük ilkesini yapılandırabilirsiniz.

1. Bir iş istasyonunda Yerel Grup İlkesi Düzenleyicisi veya bir Active Directory Etki Alanı Denetleyicisindeki Grup İlkesi Yönetim Konsolu bir grup ilkesi nesnesi açın
2. **Windows bileşenleri\\\\WindowsPowerShellYönetimŞablonlarıbilgisayaryapılandırması'nagidin.\\**
3. **Modül günlüğünü aç** ' a çift tıklayın
4. **Etkin** ' e tıklayın
5. Seçenekler bölümünde, modül adlarının yanındaki **göster** ' e tıklayın.
6. Tüm `*` modüllerdeki komutları günlüğe kaydetmek için açılır pencereyi yazın.
7. İlkeyi ayarlamak için **Tamam** ' ı tıklatın
8. **PowerShell betik bloğu günlüğünü aç** ' a çift tıklayın
9. **Etkin** ' e tıklayın
10. İlkeyi ayarlamak için **Tamam** ' ı tıklatın
11. (Yalnızca etki alanına katılmış makinelerde) `gpupdate` Grup İlkesi güncelleştirilmiş ilkeyi işlemesini ve ayarları uygulamayı bekleyin

Ayrıca, grup ilkesi aracılığıyla sistem genelinde PowerShell dökümünü de etkinleştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

[Rol yetenek dosyası oluşturma](role-capabilities.md)

[Oturum yapılandırma dosyası oluşturma](session-configurations.md)

## <a name="see-also"></a>Ayrıca bkz.

[WinRM güvenliği](/powershell/scripting/learn/remoting/winrmsecurity)

[Mavi ekibi ♥ PowerShell](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
