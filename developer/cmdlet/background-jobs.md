---
title: Arka plan işleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794714"
---
# <a name="background-jobs"></a>Arka Plan İşleri

Dahili olarak veya bir Windows PowerShell cmdlet'leri, eylem gerçekleştirebilir*arka plan işi*. Bir cmdlet bir arka plan işi çalıştığında, iş cmdlet'ini kullanarak işlem hattı iş parçacığından ayrı kendi iş parçacığında zaman uyumsuz olarak gerçekleştirilir. Bir cmdlet bir arka plan işi çalıştığında kullanıcı açısından bakıldığında, komut istemini hemen iş işleminin tamamlanması zaman alır ve iş çalışırken kullanıcı kesinti olmadan devam etmek bile döndürür.

## <a name="background-jobs-child-jobs-and-the-job-repository"></a>Arka plan işleri, alt işler ve iş havuz

Arka plan işleri destekleyen cmdlet'ler tarafından döndürülen iş nesnesi, iş tanımlar. ( [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet ayrıca bir iş nesnesi döndürür.) İş, iş, durum bilgisi ve alt projeleri belirtmek için kullanılan tanımlayıcı adını bu tanımında dahil edilir. İşi iş gerçekleştirmez. Alt iş asıl işi gerçekleştirdiğinden her bir arka plan iş en az bir alt iş sahiptir. Böylece iş arka plan işi olarak gerçekleştirilen bir cmdlet'ini çalıştırdığınızda, cmdlet işi ve alt işlerin olarak adlandırılır, ortak bir depoya eklemeniz gerekir *iş depo*.

Arka plan işleri komut satırında nasıl işleneceğini hakkında daha fazla bilgi için aşağıdakilere bakın:

- [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [about_Job_Details](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [about_Remote_Jobs](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a>Arka plan işi olarak çalıştırılan bir Cmdlet yazma

Arka plan işi olarak çalıştırılabilir bir cmdlet yazmak için aşağıdaki görevleri tamamlamanız gerekir:

- Tanımlayan bir `asJob` kullanıcı cmdlet'i bir arka plan işi çalıştırmak karar verebilir böylece parametresi geçin.

- Türetilen bir nesne oluşturma [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) sınıfı. Bu nesne bir özel iş nesnesi veya gibi Windows PowerShell tarafından sağlanan bir iş nesnesi olabilir bir [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) nesne.

- Bir kayıt işleme yöntemine ekleyin bir `if` cmdlet'i bir arka plan işi çalıştırılıp çalıştırılmayacağını algılar deyimi.

- Özel iş nesneler için iş sınıfı uygulayın.

- Cmdlet'i bir arka plan işi çalışıp bağlı olarak uygun nesneleri döndürür.

Kod örneği için bkz: [destek işleri nasıl](./how-to-support-jobs.md).

## <a name="background-job-related-apis"></a>Arka plan işi ile ilgili API'ler

Aşağıdaki API'leri arka plan işlerini yönetmek için Windows PowerShell tarafından sağlanır.

[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) özel iş nesneleri türetilir. Bu bir soyut sınıftır.

[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) yönetir ve geçerli etkin arka plan işleri hakkında bilgi sağlar.

[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) arka plan işinin durumunu tanımlar. Başlarken, çalışan ve durduruldu durumları içerir.

[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) bir arka plan işi durumu hakkında bilgi sağlar ve bir hata nedeniyle, işin geçerli durumuna girdiğinin son durumu değiştirirseniz neden oldu.

[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) bir arka plan işi durumu değiştiğinde bir olay bağımsız değişkenleri sağlar.

## <a name="windows-powershell-job-cmdlets"></a>Windows PowerShell iş cmdlet'leri

Aşağıdaki cmdlet, arka plan işlerini yönetmek için Windows PowerShell tarafından sağlanır.

[Get-Job](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

Geçerli oturumda çalışan Windows PowerShell arka plan işleri alır.

[Alma işlemi](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

Geçerli oturumda Windows PowerShell arka plan işleri sonuçlarını alır.

[Remove-Job](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

Bir Windows PowerShell arka plan işi siler.

[İşi Başlat](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

Bir Windows PowerShell arka plan işi başlatır.

[Durdurma işi](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

Bir Windows PowerShell arka plan işi durdurulur.

[İşi bekleyin](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

Komut isteminden birini veya tümünü oturumda çalışan Windows PowerShell arka plan işleri tamamlanana kadar engeller.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
