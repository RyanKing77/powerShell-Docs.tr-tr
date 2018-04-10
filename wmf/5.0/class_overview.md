---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 7eaa4dfb68bc299ad31bce81af96b6a760c4fcc5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="189dd-102">PowerShell Sınıfları Kullanarak Özel Türler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="189dd-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="189dd-103">Biz resmi sözdizimi ve diğer nesne odaklı programlama dili için benzer semantiği kullanarak sınıfları ve diğer kullanıcı tanımlı türler tanımlamak için PowerShell dil geliştirdik.</span><span class="sxs-lookup"><span data-stu-id="189dd-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="189dd-104">Geliştiriciler ve BT uzmanları geniş bir grup kullanım durumları için PowerShell çekirdeğin, geliştirme (örneğin, DSC kaynakları) PowerShell yapılarının basitleştirmek ve yönetim yüzeyleri kapsamını hızlandırmak etkinleştirmek için belirtilir.</span><span class="sxs-lookup"><span data-stu-id="189dd-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="189dd-105">Bu sürümde desteklenen senaryolar</span><span class="sxs-lookup"><span data-stu-id="189dd-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="189dd-106">PowerShell dilini kullanarak DSC kaynakları ve bunların ilişkili türlerini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="189dd-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="189dd-107">Özel türler hakkında bilgi sahibi nesne odaklı programlama yapıları, sınıfları, özellikleri, yöntemleri, vb. gibi kullanarak PowerShell'de tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="189dd-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="189dd-108">PowerShell ve sınıf temel DSC kaynağı sınıfında devralma desteği</span><span class="sxs-lookup"><span data-stu-id="189dd-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="189dd-109">PowerShell dilini kullanarak türleri hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="189dd-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="189dd-110">Oluşturma ve resmi mekanizmalarını kullanarak ve sağ düzeyinde özel durumları işleme</span><span class="sxs-lookup"><span data-stu-id="189dd-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>