---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085788"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="f8e11-102">PowerShell Sınıfları Kullanarak Özel Türler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8e11-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="f8e11-103">Biçimsel sözdizimi ve diğer nesne yönelimli programlama dillerinde benzer semantiği kullanarak sınıfları ve diğer kullanıcı tanımlı türleri tanımlamak için PowerShell dili iyileştirdik.</span><span class="sxs-lookup"><span data-stu-id="f8e11-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="f8e11-104">Geliştiriciler ve BT uzmanları geniş bir kullanım için PowerShell Kucak, PowerShell yapıtları (örneğin, DSC kaynakları) geliştirilmesini basitleştirin ve yönetim yüzeyleri kapsamını hızlandırmanız, hedef etkinleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="f8e11-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="f8e11-105">Bu sürümde desteklenen senaryolar</span><span class="sxs-lookup"><span data-stu-id="f8e11-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="f8e11-106">PowerShell dilini kullanarak DSC kaynakları ve ilişkili türlerini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="f8e11-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="f8e11-107">Bilinen nesne yönelimli programlama yapıları, sınıflar, özellikler, yöntemler vb. gibi kullanarak PowerShell'de özel türleri tanımla</span><span class="sxs-lookup"><span data-stu-id="f8e11-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="f8e11-108">PowerShell ve sınıf temel DSC kaynak sınıfıyla devralma desteği</span><span class="sxs-lookup"><span data-stu-id="f8e11-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="f8e11-109">PowerShell dilini kullanarak türlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f8e11-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="f8e11-110">Oluşturma ve resmi mekanizmalarını kullanarak ve doğru düzeyde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="f8e11-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
