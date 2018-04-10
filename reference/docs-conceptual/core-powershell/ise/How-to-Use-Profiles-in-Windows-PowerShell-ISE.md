---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Profilleri Kullanma
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: 8789d6283457f790fdea27657abb2612304e10a1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Windows PowerShell ISE’de Profilleri Kullanma

Bu konu, Windows PowerShell® Tümleşik komut dosyası ortamı (ISE içinde) profilleri kullanmayı açıklar. Bu bölümde görevleri gerçekleştirmeden önce gözden geçirmenizi öneririz [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ya da konsol bölmesinde, türü, `Get-Help about_Profiles` ve basın **ENTER**.

Yeni bir oturumu yeniden başlattığınızda, otomatik olarak çalışan bir Windows PowerShell ISE komut profilidir.  Windows PowerShell ISE için bir veya daha fazla Windows PowerShell profilleri oluşturmak ve bunları Windows PowerShell veya Windows PowerShell ISE ortamı yapılandırma eklemek için değişkenleri, diğer adlar, İşlevler, renk ve yazı tipi kullanımınız için hazırlama kullanın kullanılabilir olmasını istediğiniz Tercihler. Bir profili başlattığınız her Windows PowerShell ISE oturumuna etkiler.

> [!NOTE]
> Windows PowerShell yürütme ilkesini betik çalıştıran ve bir profil yük olup olmadığını belirler. Varsayılan yürütme İlkesi "Kısıtlı," tüm komut dosyalarının engeller profilleri de dahil olmak üzere çalışmasını. "Kısıtlı" ilkesi kullanırsanız, profil yüklenemiyor. Yürütme İlkesi hakkında daha fazla bilgi için bkz: [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Windows PowerShell ISE kullanmak için bir profil seçme

Geçerli kullanıcı ve tüm kullanıcılar için Windows PowerShell ISE profillerini destekler. Ayrıca, tüm ana bilgisayarlar için geçerli Windows PowerShell profillerini destekler.

Kullandığınız profili, Windows PowerShell ve Windows PowerShell ISE kullanma tarafından belirlenir.

- Windows PowerShell'i çalıştırmak için yalnızca Windows PowerShell ISE kullanırsanız, tüm öğelerinizi CurrentUserCurrentHost için Windows PowerShell ISE veya AllUsersCurrentHost profili için Windows PowerShell ISE gibi işe özgü profillerini birinde kaydedin.

- Windows PowerShell'i çalıştırmak için birden çok ana bilgisayar programlar kullanıyorsanız, işlevleri, diğer adlar, değişkenler ve komutları CurrentUserAllHosts gibi tüm konak programlar etkileyen bir profil veya AllUsersAllHosts profilinde kaydedin ve işe özgü özellikler gibi kaydedin Windows PowerShell ISE için renk ve yazı tipi özelleştirme Windows PowerShell ISE veya AllUsersCurrentHost profili CurrentUserCurrentHost profilinde.

Oluşturulan ve Windows PowerShell ISE kullanılan profilleri şunlardır: Her profil kendi belirli yoluna kaydedilir.

| Profil türü | Profil yolu |
| --- | --- |
| **Geçerli kullanıcı, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, veya `$PROFILE` |
| **Tüm kullanıcılar, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Geçerli kullanıcı, tüm ana bilgisayarlar**| `$PROFILE.CurrentUserAllHosts` |
| **Tüm kullanıcılar, tüm ana bilgisayarlar** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Yeni bir profil oluşturmak için

Yeni "geçerli bir kullanıcı, Windows PowerShell ISE" oluşturmak için profili, bu komutu çalıştırın:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Yeni bir "Tüm kullanıcılar, Windows PowerShell ISE" oluşturmak için profili, bu komutu çalıştırın:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

"Geçerli kullanıcının tüm barındıran" yeni bir profil oluşturmak için bu komutu çalıştırın:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

"Tüm kullanıcılar, tüm barındıran" yeni bir profil oluşturmak için şunu yazın:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Bir profili düzenlemek için

1. Profil açmak için komut psedit düzenlemek istediğiniz profili belirten değişkeni ile çalıştırın. Örneğin, "Current user, Windows PowerShell ISE" açmak için profil, yazın: `psEdit $PROFILE`

2. Bazı öğeler profilinize ekleyin. Başlamanıza yardımcı olmak için birkaç örnek verilmiştir:

   - Konsol bölmesinde, profil dosya türü olarak mavi varsayılan arka plan rengini değiştirmek için: `$psISE.Options.OutputPaneBackground = 'blue'` . $PsISE değişken hakkında daha fazla bilgi için bkz: [Windows PowerShell ISE nesne modeli başvurusu](The-ISE-Object-Model-Hierarchy.md).

   - 20, profil dosya türü için yazı tipi boyutunu değiştirmek için: `$psISE.Options.FontSize =20`

3. Profil dosyanızı üzerinde kaydetmek için **dosya** menüsünde tıklatın **kaydetmek**. Windows PowerShell ISE sonraki açışınızda özelleştirmelerinizi uygulanır.

## <a name="see-also"></a>Ayrıca bkz:

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Windows PowerShell ISE Tanıtımı](Introducing-the-Windows-PowerShell-ISE.md)