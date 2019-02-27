---
title: Hataları sonlandıran | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: c593da1f7bdb6ddf09ba8d5de92af730687dbc8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849080"
---
# <a name="terminating-errors"></a>Sonlandırıcı Hatalar

Bu konuda, hataları sonlandıran rapor için kullanılan yöntem anlatılmaktadır. Ayrıca cmdlet yöntemi çağırmak nasıl ele alır ve yöntem çağrıldığında Windows PowerShell çalışma zamanı tarafından döndürülen özel durumlar açıklanır.

Bir sonlandırma hatası oluşur, cmdlet çağırarak hata raporlamalıdır [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) yöntemi. Bu yöntem, cmdlet hatasına neden olan koşul açıklayan bir hata kaydı göndermesini sağlar. Hata kaydı hakkında daha fazla bilgi için bkz: [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).

Zaman [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) yöntemi çağrıldığında, işlem hattının yürütülmesini durdurur ve oluşturur kalıcı olarak Windows PowerShell çalışma zamanı bir [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) özel durum. Çağırmak için sonraki girişimlerini [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), veya birkaç API çağrıları oluşturmak neden bir [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) özel durum.

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) özel işlem hattı durdurmak kullanıcı departmanınız isterse işlem hattındaki başka bir cmdlet bir sonlandırmalı hata bildirirse veya işlem hattı durdurulduysa MFC'yi da gerçekleşebilir herhangi bir nedenle tamamlanmadan önce. Cmdlet catch gerekmez [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) özel durum sürece temizleme kaynakları veya kendi iç durumu açmanız gerekir.

Cmdlet'leri bir sonlandırmalı hata raporlamadan önce herhangi bir sayıda çıkış nesnelerini veya Sonlandırıcı olmayan hatalara yazabilirsiniz. Ancak, işlem hattı ve daha fazla çıktı hataları, sonlandırma, sonlandırma hatası kalıcı olarak durdurur veya Sonlandırıcı olmayan hatalara bildirilebilir.

Cmdlet'leri çağırabilir [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) çağrılan iş parçacığından [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), veya [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) giriş işleme yöntemi. Çağırmaya çalışmayın [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) veya [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) başka bir iş parçacığından. Bunun yerine, hataları ana iş parçacığına geri bildirilmesi gerekir.

Uygulaması bir özel durum bir cmdlet için mümkün olduğu [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), veya [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi. Bu yöntemler (hariç, Windows PowerShell konağı durdurmaya birkaç önemli hata koşulları) şuradan oluşturulduğu herhangi bir özel işlem hattı, ancak Windows PowerShell bir bütün olarak değil durdurur bir sonlandırmalı hata olarak yorumlanır. (Yalnızca ana cmdlet'i iş parçacığı için geçerlidir. Cmdlet tarafından üretilen iş parçacıklarında yakalanmamış özel durumlar genel olarak, Windows PowerShell konağı durdurmak.) Kullanmanızı öneririz [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) hata kaydı hata durumu hakkında ek bilgi sağladığından bir özel durum oluşturmak yerine olduğu için yararlı Son kullanıcı. Cmdlet'leri, yakalama ve tüm özel durumları işleme karşı yönetilen kod kural uymanız (`catch (Exception e)`). Yalnızca bilinen ve beklenen tür özel durumları hata kayıtlarını Dönüştür.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell hata kaydı](./windows-powershell-error-records.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
