---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 8b414331bbfb7dc71d960241a6bc83b0b22641db
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="f234d-102">Özel türler PowerShell sınıflarını kullanarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="f234d-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="f234d-103">Biz resmi sözdizimi ve diğer nesne odaklı programlama dili için benzer semantiği kullanarak sınıfları ve diğer kullanıcı tanımlı türler tanımlamak için PowerShell dil geliştirdik.</span><span class="sxs-lookup"><span data-stu-id="f234d-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="f234d-104">Geliştiriciler ve BT uzmanları geniş bir grup kullanım durumları için PowerShell çekirdeğin, geliştirme (örneğin, DSC kaynakları) PowerShell yapılarının basitleştirmek ve yönetim yüzeyleri kapsamını hızlandırmak etkinleştirmek için belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f234d-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="f234d-105">Bu sürümde desteklenen senaryolar</span><span class="sxs-lookup"><span data-stu-id="f234d-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="f234d-106">PowerShell dilini kullanarak DSC kaynakları ve bunların ilişkili türlerini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="f234d-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="f234d-107">Özel türler hakkında bilgi sahibi nesne odaklı programlama yapıları, sınıfları, özellikleri, yöntemleri, vb. gibi kullanarak PowerShell'de tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f234d-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="f234d-108">PowerShell ve sınıf temel DSC kaynağı sınıfında devralma desteği</span><span class="sxs-lookup"><span data-stu-id="f234d-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="f234d-109">PowerShell dilini kullanarak türleri hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f234d-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="f234d-110">Oluşturma ve resmi mekanizmalarını kullanarak ve sağ düzeyinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="f234d-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

