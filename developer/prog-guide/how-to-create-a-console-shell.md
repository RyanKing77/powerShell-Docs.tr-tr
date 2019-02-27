---
title: Bir konsol Kabuk oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845062"
---
# <a name="how-to-create-a-console-shell"></a>Konsol Kabuğu Oluşturma

Windows PowerShell, "Oluştur-Genişletilebilir değil bir konsol Kabuk oluşturmak için kullanılan Seti", başvurulan bir yap-Shell araç sağlar. Bu yeni araçla oluşturulan Kabukları daha sonra bir Windows PowerShell ek bileşeni genişletilemez.

## <a name="syntax"></a>Sözdizimi

Oluştur-Kabuğu'ndan yapma dosyasında çalıştırmak için kullanılan sözdizimi aşağıdadır.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parametreler

Oluştur-Shell parametrelerinin kısa bir açıklamasını aşağıda verilmiştir.

> [!CAUTION]
> Derlemelere UNC yollarını olun-Shell tarafından desteklenmez.

|Parametre|Açıklama|
|---------------|-----------------|
|-out n.exe|Zorunlu. Kabuk üretmek için adı. Yolu, bu parametre bir parçası olarak belirtilir.<br /><br /> Belirtilmezse olun-shell ".exe" Bu değeri ekleyin. **Dikkat:**  Başvurulan .dll dosyasıyla aynı ada sahip bir çıktı dosyası oluşturmayın. Bunu denerseniz olun-Shell araç cmdlet'ini kaynak kodunuzun .cs dosyanın üzerine yazar aynı ada sahip bir .cs dosyası oluşturur.|
|-namespace ns|Zorunlu. Türetilmiş için kullanılacak ad [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) oluşturma Seti oluşturur ve derler sınıfı.|
|-libdirectory1 lib [, libdirectory2,..]|Windows PowerShell derlemeler tarafından belirtilen derlemeleri de dahil olmak üzere, .NET derlemeleri için Aranan dizinleri `reference` parametre başka bir derleme tarafından dolaylı olarak başvurulan derlemeler ve .NET system derlemeleri.|
|-başvuru ca1.dll[,ca2.dll,...]|Kabukta içerecek şekilde derlemeleri virgülle ayrılmış listesi. Bu derlemeler, tüm cmdlet ve sağlayıcı derlemeleri, aynı zamanda yüklenmesi gereken kaynak derlemeleri içerir. Bu parametre belirtilmezse, bir kabuk yalnızca çekirdek cmdlet'lerinin ve Windows PowerShell tarafından sağlanan sağlayıcıları içeren oluşturulur.<br /><br /> Derlemeler, kendi tam yolu kullanılarak belirtilebilir, aksi takdirde bunlar tarafından belirtilen yolu kullanarak için aranır `lib` parametresi.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Kabukta dahil etmek için biçim verileri virgülle ayrılmış listesi. Bu parametre belirtilmezse, bir kabuk yalnızca Windows PowerShell tarafından sağlanan biçim verilerini içeren oluşturulur.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Kabukta eklenecek tür verileri virgülle ayrılmış listesi. Bu parametre belirtilmezse, bir kabuk yalnızca Windows PowerShell tarafından sağlanan türü verileri içeren oluşturulur.|
|-source c1.cs [,c2.cs,...]|Kabuk oluşturmak için gereken herhangi bir kaynak kodu içeren Kabuk geliştirici tarafından sağlanan, bir dosya adı.<br /><br /> Kaynak kodu dosyası aşağıdaki kaynak kodunu birini içerebilir:<br /><br /> -Varsayılan Yetkilendirme Yöneticisi'ni geçersiz kılmalar Yetkilendirme Yöneticisi uygulamasıdır. (Bu da bir bütünleştirilmiş kod içine derlenmiş sağlanması.)<br />-Derleme bilgilendirme öznitelik bildirimleri: AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, ve AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Yetkilendirme Yöneticisi uygulaması içeren türü. Bu kaynak kodunda tanımlanamıyor, veya bir bütünleştirilmiş kod içine derlenmiş (tarafından belirtilen `reference` parametresi). Bu parametre belirtilmezse, varsayılan güvenlik Yöneticisi'ni kullanılır. Değer, ad alanları da dahil olmak üzere tam tür adı olmalıdır.|
|-win32icon i.ico|Kabuk .exe dosyasının simge. Belirtilmezse, kabuk c# derleyicisi (varsa) içeren simgesine sahip.|
|-initscript p.ps1|Başlatma profili Kabuğu. Dosya bulunur "olarak-olan"; hiçbir geçerlilik denetimi yapma-Shell tarafından gerçekleştirilir.|
|-builtinscript s1.ps1[,s2.ps1,...]|Yerleşik komut kabuğu listesi. Bu betikler, yolun betiklerde önce bulunan ve bunların içeriğini Kabuk derlendikten sonra değiştirilemez.<br /><br /> Dosyaların "olarak-olan"; hiçbir geçerlilik denetimi yapma-Shell tarafından gerçekleştirilir.|
|-Kaynak resourcefile.txt|.txt, Yardım ve başlık kaynaklarını Kabuğu içeren dosya. İlk kaynak ShellHelp adlı ve Kabuk ile çağrılırsa görüntülenen metni içeren `help` parametresi. İkinci kaynak ShellBanner adlı ve metin ve etkileşimli modda Kabuk başlatıldığında görüntülenen telif hakkı bilgileri içerir.<br /><br /> Bu parametre sağlanmazsa veya bu kaynakları mevcut olmayan, genel Yardım ve başlık kullanılır.|
|-cscflags cscFlags|Geçirilmesi bayrakları C# derleyici (csc.exe). Bunlar arasında değişmeden geçirilir. Bu parametre, boşluk içeriyorsa, çift tırnak içine.|
|-?<br /><br /> -Yardım|Oluştur-Shell komut satırı seçenekleri ve telif hakkı iletisini görüntüler.|
|-verbose|Kabuk oluşturulurken ayrıntılı bilgileri görüntüler.|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)