---
title: Bir ikili PowerShell modülü yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847155"
---
# <a name="how-to-write-a-powershell-binary-module"></a>PowerShell İkili Modülü Yazma

İkili bir modül, cmdlet sınıfları içeren herhangi bir derleme (.dll) olabilir. İkili modül içeri aktarıldığında varsayılan olarak derleme içindeki tüm cmdlet'ler içeri aktarılır. Ancak, kök derleme modülüdür bir modül bildirimi oluşturarak içeri aktarılan cmdlet'ler kısıtlayabilirsiniz. (Örneğin, bildirimin CmdletsToExport anahtarı gerekli cmdlet'leri dışarı aktarmak için kullanılabilir.) Ayrıca, bir ikili modül ek dosyalar, bir dizin yapısına ve diğer yararlı yönetim bilgilerine tek bir cmdlet yükleyemediği parçalarını içerebilir.

Aşağıdaki yordam, oluşturma ve ikili bir PowerShell modülü yükleme açıklar.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Oluşturma ve PowerShell ikili modülünü yükleme

1. İkili bir PowerShell çözümü oluşturun (yazılan bir cmdlet gibi C#), özellikleriyle gerekir ve düzgün çalıştığından emin olun.

   Kod açısından bakıldığında, ikili bir modülün çekirdek sadece bir cmdlet derlemesidir. Aslında, PowerShell cmdlet'i tek bir bütünleştirilmiş kod yükleme ve kaldırma ile Geliştirici tarafında ek çaba açısından bir modül olarak değerlendirir. Bir cmdlet yazma hakkında daha fazla bilgi için bkz. [yazma bir Windows PowerShell cmdlet'i](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Gerekirse, çözümünüzün rest oluşturun: (ek cmdlet'leri, XML dosyaları vb.) ve bunları bir modül bildirimi ile açıklar.

   Çözümünüzü cmdlet'i derlemelerde açıklayan ek olarak, bir modül bildirimi dışarı ve içeri aktarılan modülünüzde istediğiniz, hangi cmdlet'leri sunulur ve ek dosyaları ne modüle geçer tanımlayabilirsiniz. Ancak daha önce belirtildiği gibi PowerShell gibi ek çaba sahip bir modül ikili bir cmdlet davranabilirsiniz. Bu nedenle, bir modül bildirimi çoğunlukla birden çok dosyayı tek bir paket birleştirmek için veya belirli bir derleme için yayın açıkça denetlemek için yararlıdır. Daha fazla bilgi için [bildirim PowerShell modülü yazma](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

   Aşağıdaki kod bir son derece basittir C# aynı dosyada bir modül olarak kullanılabilecek üç cmdlet'leri içeren bir kod bloğu.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Çözümünüzü paketini ve paket için bir yere kaydedin PowerShell modülü yolda.

   `PSModulePath` Genel ortam değişkeni PowerShell modülünüzde bulmak için kullanacağı varsayılan yollarını açıklar. Örneğin, bir sistemde bir modüle kaydetmek için yaygın bir yolu olabilir `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Varsayılan yolları kullanmıyorsanız, modülünüzün konumu yükleme sırasında açıkça durum gerekecektir. Birden çok derlemeleri ve çözümünüz için dosyaları depolamak için klasör gerekebilir, modülünüzde kaydedileceği klasörü oluşturmak emin olun.

   Teknik olarak, modülünüzün herhangi bir yere yüklemek ihtiyacınız yoktur, Not `PSModulePath` -yalnızca PowerShell modülünüzde için görüneceğini varsayılan konumları olanlardır. Ancak, modülünüzde başka bir yerde depolanması için geçerli bir nedeniniz yoksa, bunu yapmak için en iyi kabul edilir. Daha fazla bilgi için [PowerShell modülünü yükleme](./installing-a-powershell-module.md) ve [PowerShell modülü yükleme yolunu değiştirmek](./modifying-the-psmodulepath-installation-path.md).

4. Bir çağrı ile PowerShell içinde modülü içeri [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   İçin çağırma [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) modülünüzde etkin belleğe yüklenir. PowerShell 3.0 kullanıyorsanız ve daha sonra kodda çağrısı yaparak modülünüzün adını da alma işlemi Daha fazla bilgi için [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Ek derlemeler modül içeri aktarma

Cmdlet'leri ve ek bileşenini derlemeleri yok sağlayıcıları, ikili modülleri olarak yüklenebilir. Ek derlemeler ikili modülleri yüklü olduğunda, cmdlet'leri ve sağlayıcıları ek bileşeninde kullanıcıya kullanılabilir ancak ek bileşenini derlemede sınıfı, göz ardı edilir ve ek bileşenini kayıtlı değil. Sonuç olarak, cmdlet'leri ve sağlayıcıları oturuma kullanılabilir olsa bile ek bileşenini Windows PowerShell tarafından sağlanan ek bileşenini cmdlet'leri algılayamaz.

Ayrıca, eklenti tarafından başvurulan türleri biçimlendirme veya dosyaları ikili bir modülün bir parçası olarak içeri aktarılamaz. Biçimlendirme ve türleri dosyalarını içeri aktarmak için bir modül bildirimi oluşturmanız gerekir. Bkz, [nasıl yazılacağını bir PowerShell modülü bildirim](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
