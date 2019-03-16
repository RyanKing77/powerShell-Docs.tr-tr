---
title: Windows PowerShell oturum durumu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059550"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell Oturum Durumu

Oturum durumu için Windows PowerShell oturumunda veya modül geçerli yapılandırmasını ifade eder. Bir Windows PowerShell oturumu etkileşimli komut satırı kullanıcı veya program aracılığıyla bir ana bilgisayar uygulaması tarafından kullanılan işlem ortamıdır. Oturum durumu bir oturum için genel oturum durumuna adlandırılır.

Geliştirici açısından bakıldığında, bir Windows PowerShell oturumu ana bilgisayar uygulamasına bir Windows PowerShell çalışma açıldığında ve çalışma kapattığı zaman arasındaki süreyi ifade eder. Başka bir şekilde baktığı, çalışma alanı bulunduğu sürece, çağrılan Windows PowerShell altyapısı örneği ömrünü oturumdur.

## <a name="module-session-state"></a>Modül oturum durumu

Modül veya iç içe geçmiş kendi modüllerinin bir oturuma aktarılır her modül oturum durumları oluşturulur. Cmdlet'i, işlev veya betik gibi bir öğenin bir modül dışa aktardığında, oturumun genel oturum durumuna bu öğeye bir başvuru eklenir. Ancak, öğe çalıştırdığınızda, oturum durumu modülü içinde yürütülür.

## <a name="session-state-data"></a>Oturum durumu verileri

Oturum durumu verilerini, genel veya özel olabilir. Özel veriler yalnızca oturum durumu içinden kullanılabilir olduğu sürece genel veri oturum durumu dışından çağrılar için kullanılabilir. Örneğin, bir modül yalnızca modül veya yalnızca dahili olarak adlandırılan özel bir işlevi olabilir aktarılmış olan bir genel öğe. Bu bir .NET Framework türü özel ve genel üyeleri benzer.

Oturum durumu verilerini, yürütme altyapısı geçerli Windows PowerShell oturumu bağlamında geçerli örneği tarafından depolanır. Oturum durumu verileri şu öğelerden oluşur:

- Yol bilgileri

- Sürücü bilgileri

- Windows PowerShell sağlayıcısı bilgileri

- İçeri aktarılan modülleri ve modül tarafından dışarı aktarılan modül öğelere (örneğin, cmdlet'ler, İşlevler ve betikler) başvurular hakkında bilgi. Bu bilgiler ve bu başvuruları yalnızca genel oturum durumu için var.

- Oturum durumu değişken bilgileri

## <a name="accessing-session-state-data-within-cmdlets"></a>Cmdlet'ler içinde oturum durumu verilerine erişme

Cmdlet'leri erişebilir oturum durumu verilerini ya da dolaylı olarak ile [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) özelliğini cmdlet'i sınıf veya doğrudan aracılığıyla [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) sınıfı. [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) sınıfı, farklı türde oturum durumu verileri araştırmak için kullanılan özellikleri sağlar.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate? Displayproperty tam adı =](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell cmdlet'leri](./cmdlet-overview.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
