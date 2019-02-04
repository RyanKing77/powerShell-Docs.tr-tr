---
ms.date: 08/23/2018
keywords: PowerShell cmdlet'i
title: Önemli PowerShell kavramlarını anlama
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686988"
---
# <a name="understanding-important-powershell-concepts"></a>Önemli PowerShell kavramlarını anlama

PowerShell tasarım kavramları birçok farklı ortamlarından tümleştirir. Birkaç kavramı, kişilere tanıdık Kabukları veya programlama ortamlarında deneyimine sahip olur. Ancak, birkaç insanın tümünün hakkında öğrenmiş olacaksınız. Bu kavramlar bazıları isteyen Kabuk yararlı bir genel bakış sağlar.

## <a name="output-is-object-based"></a>Nesne tabanlı bir çıktıdır

Geleneksel komut satırı arabirimlerinden, PowerShell cmdlet'leri nesneleriyle ilgili şekilde tasarlanmıştır.
Daha fazlasını ekranda görünen karakter dizesini yapılandırılmış bilgileri bir nesnedir. Komut çıktısında her zaman ihtiyacınız olduğunda kullanabileceğiniz ek bilgiler taşır.

Geçmiş verileri işlemek için metin işleme araçları kullandıysanız, farklı PowerShell'de kullanıldığında davranırlar olduğunu bulabilirsiniz. Çoğu durumda, belirli bilgileri ayıklamak için metin işleme araçları gerekmez. Doğrudan, standart PowerShell nesne sözdizimi kullanarak verileri bölümlerini de erişin.

## <a name="the-command-family-is-extensible"></a>Komut seridir Genişletilebilir

Gibi arabirimleri **cmd.exe** doğrudan yerleşik bir komut kümesi genişletmek bir yol sağlaması gerekmez. İçinde çalışan dış komut satırı araçları oluşturabilirsiniz **cmd.exe**. Ancak bu dış Araçlar Yardım tümleştirmesi gibi hizmetlerin yoktur. **cmd.exe** otomatik olarak bu dış Araçlar geçerli komutları olduğunu bilmez.

PowerShell komutları yerel olarak da bilinir *cmdlet'leri* (command-let olarak okunur). Kendi cmdlet modülleri oluşturabilir ve işlevleri kullanarak kod veya betiklerde derlenir. Modülleri, cmdlet'leri ve sağlayıcıları kabuğa ekleyebilirsiniz. PowerShell UNIX Kabuk betikleri için benzer bir komut dosyalarını da destekler ve **cmd.exe** toplu iş dosyaları.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell konsol girdisi ve görüntü işleme

Bir komut yazın, PowerShell'i her zaman komut satırı girişi doğrudan işler. PowerShell, ayrıca ekranda gördüğünüz çıkış biçimlendirir. İş her cmdlet azaltır çünkü bu önemli bir farktır. Herhangi bir cmdlet'i ile aynı şekilde her zaman şeyler yapabilirsiniz sağlar. Cmdlet geliştiriciler komut satırı bağımsız değişkenlerini ayrıştırma veya çıktıyı biçimlendirmek için kod yazmanız gerekmez.

Geleneksel komut satırı araçları, isteme ve Yardım görüntüleme için kendi şemalara sahip. Bazı komut satırı araçlarını kullanmak **/?** Yardım görüntüleme tetiklemek için; diğerlerinde **-?**, **/H**, hatta **//**. Bir GUI penceresi yerine konsolunda görünen bazı Yardım görüntülenir. Yanlış parametre kullanırsanız, araç, yazılan ve otomatik olarak bir görevi çalıştırmaya başlar yoksay.
PowerShell otomatik olarak ayrıştırır ve komut satırı işlemleri **-?** parametresi her zaman "Yardım için bu komutu Göster" anlamına gelir.

> [!NOTE]
> PowerShell'de bir grafik uygulaması çalıştırırsanız, uygulama için bir pencere açılır.
> PowerShell, yalnızca zaman komut satırı işleme, tedarik veya konsol penceresine döndürülen uygulama çıktısı giriş müdahalesi. Uygulama dahili olarak şeklini etkilemez.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell kullanan bazı C# sözdizimi

PowerShell, .NET Framework üzerinde oluşturulur. Bu bazı özellikleri söz dizimi ve anahtar sözcükler C# programlama dilinin paylaşır. PowerShell öğrenmek, C# öğrenmek çok daha kolay zorlaştırabilir. Zaten C# ile biliyorsanız, bu benzerlikler PowerShell daha kolay öğrenme yapabilirsiniz.
