---
title: Windows PowerShell dosyaları biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 35efd36fd70c209e3cbeb9eff0ddf978615fffd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845601"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell Biçimlendirme Dosyaları

Windows PowerShell, bazı biçimlendirme dosyaları sağlar (. format.ps1xml) yükleme dizininde bulunur (`$pshome`). Bu dosyaların her biri, .NET nesneleri belirli bir dizi varsayılan görünümünü tanımlar. Bu dosyaları hiçbir zaman değiştirilmelidir. Ancak, bunları bir başvuru olarak kendi özel biçimlendirme dosyaları oluşturmak için kullanabilirsiniz.

Certificate.Format.ps1xml x.509 sertifikaları gibi sertifika deposu ve sertifika depolarını nesneleri görüntüsünü tanımlar.

DotNetTypes.Format.ps1xml CultureInfo FileVersionInfo ve EventLogEntry nesneleri gibi çeşitli .NET nesneleri görüntüsünü tanımlar.

Dosya ve dizin nesneleri gibi dosya sistemi nesneleri görüntülenmesini FileSystem.Format.ps1xml tanımlar.

Tarafından kullanılan farklı görünümleri Help.Format.ps1xml tanımlar [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'in ayrıntılı, tam, parametreleri ve örnek görünümleri gibi.
Tarafından kullanılan farklı görünümleri tanımlar [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'in ayrıntılı, tam, parametreleri ve örnek görünümleri gibi.

PowerShellCore.Format.ps1xml tanımlar tarafından döndürülen nesne gibi Windows PowerShell core cmdlet'leri tarafından oluşturulan nesnelerin görünümünü [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) ve [Get-geçmiş](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet'leri.
Tarafından döndürülen nesne gibi Windows PowerShell core cmdlet'leri tarafından oluşturulan nesnelerin görünümünü tanımlar [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) ve [Get-geçmiş](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet'leri.

PowerShellTrace.Format.ps1xml gibi olanlar tarafından oluşturulan izleme nesneleri görüntüsünü tanımlar [izleme komut](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet'i.
İzleme nesneleri tarafından oluşturulan olanlar gibi görüntüsünü tanımlar [izleme komut](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet'i.

Görüntü kayıt defteri anahtarı ve giriş nesneleri gibi nesnelerin Registry.Format.ps1xml tanımlar.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](../cmdlet/writing-a-windows-powershell-cmdlet.md)
