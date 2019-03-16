---
title: Cmdlet örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058054"
---
# <a name="cmdlet-samples"></a>Cmdlet Örnekleri

Bu bölümde Windows PowerShell 2.0 SDK'sını sağlanan örnek kod açıklanmaktadır. Bu bölümdeki konular, kodu kopyalayın veya SDK'sı ile yüklü kaynak dosyalarını açın. [Windows PowerShell 2.0 Yazılım Geliştirme Seti (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) Benioku dosyaları, kaynak dosyaları ve her örnek için Visual Studio proje dosyaları sağlar. SDK yüklenmiş altındaki örneklere bulabilirsiniz `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` klasör.

## <a name="in-this-section"></a>Bu Bölümde

[GetProcessSample01 örnek](./getprocesssample01-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir.

[GetProcessSample02 örnek](./getprocesssample02-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir. Bunu, alınacak işlemleri belirtmek için kullanılan bir Name parametresi sağlar.

[GetProcessSample03 örnek](./getprocesssample03-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir. Bu işlem hattı bir nesneden ya da parametre adı ile aynı özellik adı olan bir nesnenin bir özelliğine bir değer alabilen bir Name parametresi sağlar.

[GetProcessSample04 örnek](./getprocesssample04-sample.md) Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir. Bir işlem alınırken bir hata oluşması halinde olmak üzere sonlandırmasız bir hata oluşturur.

[GetProcessSample05 örnek](./getprocesssample05-sample.md) Bu örnek cmdlet Get-Proc tam bir sürümünü gösterir.

[StopProcessSample01 örnek](./stopprocesssample01-sample.md) Bu örnek, bir işlemi durdurmak çalışmadan önce kullanıcıdan geri bildirim istekleri bir cmdlet yazma ve nasıl uygulanacağını gösterir. bir `PassThru` kullanıcı döndürmek için cmdlet istediğini gösterir parametresi bir nesne.

[StopProcessSample02 örnek](./stopprocesssample02-sample.md) Bu örnek, yerel bilgisayarda işlem durdurulurken hata ayıklama, ayrıntılı ve uyarı iletilerini yazan bir cmdlet yazma işlemi gösterilmektedir.

[StopProcessSample03 örnek](./stopprocesssample03-sample.md) Bu örnek, bir cmdlet parametreleri, diğer adlar ve, olan yazma işlemi gösterilmektedir joker karakterleri destekler.

[StopProcessSample04 örnek](./stopprocesssample04-sample.md) Bu örnek, bir cmdlet parametre kümeleri bildirir, varsayılan parametre ayarlama ve Giriş bir nesneyi kabul edebildiğini belirtir yazma işlemi gösterilmektedir.

[Events01 örnek](./events01-sample.md) Bu örnek, kaydetmek kullanıcı tarafından harekete geçirilen olayları sağlayan bir cmdlet oluşturma işlemi gösterilmektedir [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Bu cmdlet ile kullanıcıları Örneğin, belirli bir dizini altında bir dosya oluşturulduğunda yürütülecek bir eylem kaydedebilir. Bu örnek türetildiği [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) temel sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
