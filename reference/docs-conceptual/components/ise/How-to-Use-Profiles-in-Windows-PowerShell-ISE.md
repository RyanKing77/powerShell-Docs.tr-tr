---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Profilleri Kullanma
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057545"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Windows PowerShell ISE’de Profilleri Kullanma

Bu konu, Windows PowerShell® Tümleşik komut dosyası ortamı (ISE içinde) profilleri kullanmayı açıklar. Bu bölümde görevleri gerçekleştirmeden önce gözden geçirmenizi öneririz [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ya da konsol bölmesinde, türü, `Get-Help about_Profiles` basın **ENTER**.

Yeni bir oturum başlattığınızda otomatik olarak çalışan bir Windows PowerShell ISE betik profilidir.  Windows PowerShell ISE için bir veya daha fazla Windows PowerShell profilleri oluşturmak ve bunları yapılandırma Windows PowerShell veya Windows PowerShell ISE ortamı eklemek için değişkenleri, diğer adlar, İşlevler, renk ve yazı tipi, kullanımınız için hazırlama kullanın kullanılabilir olmasını istediğiniz tercihleri. Bir profili başlattığınız her Windows PowerShell ISE oturumuna etkiler.

> [!NOTE]
> Windows PowerShell yürütme İlkesi betikleri çalıştırabilir ve profil yükleme olup olmadığını belirler. Varsayılan yürütme ilkesini "Yasak" engelleyen tüm betikleri profilleri de dahil olmak üzere çalışmasını. "Restricted" ilkesini kullanırsanız, profil yüklenemiyor. Yürütme İlkesi hakkında daha fazla bilgi için bkz. [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Windows PowerShell ISE'de kullanmak için bir profil seçme

Geçerli kullanıcı ve tüm kullanıcılar için Windows PowerShell ISE profillerini destekler. Ayrıca, tüm Konaklara uygulamak Windows PowerShell profillerini destekler.

Kullandığınız profili, Windows PowerShell ve Windows PowerShell ISE'yi kullanma tarafından belirlenir.

- Windows PowerShell'i çalıştırmak için yalnızca Windows PowerShell ISE kullanırsanız, tüm öğeleri bir Windows PowerShell ISE CurrentUserCurrentHost profilini veya Windows PowerShell ISE AllUsersCurrentHost profilini gibi işe özgü profilini kaydedin.

- Windows PowerShell'i çalıştırmak için birden çok konak programlar kullanıyorsanız işlevleri, diğer adlar, değişkenler ve komutları CurrentUserAllHosts gibi tüm konak programlar etkileyen bir profilinde AllUsersAllHosts kaydedin ve işe özgü özellikler gibi Windows PowerShell ISE için renk ve yazı tipi özelleştirme için Windows PowerShell ISE profilini veya AllUsersCurrentHost profilini CurrentUserCurrentHost profilinde.

Oluşturulan ve kullanılan Windows PowerShell ISE'de profilleri aşağıda verilmiştir. Her profil belirli kendi yoluna kaydedilir.

| Profil türü | Profil yolu |
| --- | --- |
| **Geçerli kullanıcı, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, veya `$PROFILE` |
| **Tüm kullanıcılar, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Geçerli kullanıcı, tüm konaklar**| `$PROFILE.CurrentUserAllHosts` |
| **Tüm kullanıcılar, tüm konaklar** | `$PROFILE.AllUsersAllHosts` |

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

"Geçerli kullanıcının tüm barındıran" yeni bir profil oluşturmak için şu komutu çalıştırın:

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

1. Profil açmak için komut psedit düzenlemek istediğiniz profili belirten değişkeni ile çalıştırın. Örneğin, "geçerli kullanıcının, Windows PowerShell ISE" açmak için profil, yazın: `psEdit $PROFILE`

2. Bazı öğeler profilinize ekleyin. Başlamanıza yardımcı olmak için bazı örnekler şunlardır:

   - Konsol bölmesinde, profili dosya türünü mavi varsayılan arka plan rengini değiştirmek için: `$psISE.Options.OutputPaneBackground = 'blue'` . $PsISE değişken hakkında daha fazla bilgi için bkz. [Windows PowerShell ISE nesne modeli başvurusu](object-model/The-ISE-Object-Model-Hierarchy.md).

   - Profil dosya türü 20 yazı tipi boyutunu değiştirmek için: `$psISE.Options.FontSize =20`

3. Profil dosyanızı ile tasarruf için **dosya** menüsünde tıklatın **Kaydet**. Özelleştirmelerinizi Windows PowerShell ISE, sonraki açışınızda uygulanır.

## <a name="see-also"></a>Ayrıca bkz:

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Windows PowerShell ISE Tanıtımı](Introducing-the-Windows-PowerShell-ISE.md)