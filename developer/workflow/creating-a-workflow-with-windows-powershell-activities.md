---
title: Windows PowerShell etkinlikleriyle iş akışı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080449"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Windows PowerShell Etkinlikleri ile İş Akışı Oluşturma

Bir Windows PowerShell iş akışı etkinlikleri Visual Studio araç kutusundan seçip iş akışı Tasarımcısı penceresine sürükleyerek oluşturabilirsiniz. Windows PowerShell etkinlikler Visual Studio araç kutusuna ekleme hakkında daha fazla bilgi için bkz: [ekleyerek Windows PowerShell etkinlikler Visual Studio araç kutusu](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Aşağıdaki yordamlar, kullanıcı tarafından belirtilen bilgisayarlar etki alanı durumunu denetler, zaten birleştirilmemiş ve sonra durumu yeniden denetler bunları bir etki alanına katılan bir iş akışının nasıl oluşturulacağını açıklar.

### <a name="setting-up-the-project"></a>Projeyi ayarlama

1. Verilen yordamı izleyin [ekleyerek Windows PowerShell etkinlikler Visual Studio araç kutusu](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) bir iş akışı projesi oluşturun ve etkinlikler eklemek için [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) ve [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) araç kutusu derlemeler.

2. System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities ve Microsoft.PowerShell.Commands.Management proje için başvuru bütünleştirilmiş kodları olarak ekleyin.

### <a name="adding-activities-to-the-workflow"></a>İş akışına etkinlikler ekleme

1. Ekleme bir **dizisi** iş akışı için etkinlik.

2. Adlandırılmış bağımsız değişken oluşturma `ComputerName` türünde bir bağımsız değişken ile `String[]`. Bu bağımsız değişken denetleyip katılmak için bilgisayarların adlarını temsil eder.

3. Adlandırılmış bağımsız değişken oluşturma `DomainCred` türü [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Bu bağımsız değişken, bir bilgisayarın etki alanına katılmasını sağlamak için yetkili bir etki alanı hesabı etki alanı kimlik bilgilerini temsil eder.

4. Adlandırılmış bağımsız değişken oluşturma `MachineCred` türü [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Bu bağımsız değişken denetleyip katılmak için bilgisayarlarda yönetici kimlik bilgilerini temsil eder.

5. Ekleme bir **ParallelForEach** etkinliği içinde **dizisi** etkinlik. Girin `comp` ve `ComputerName` içinde döngü öğeleri yinelenir. böylece, metin kutuları `ComputerName` dizisi.

6. Ekleme bir **dizisi** body etkinlik **ParallelForEach** etkinlik. Ayarlama **DisplayName** özelliği dizinin `JoinDomain`.

7. Ekleme bir **GetWmiObject** etkinliğini **JoinDomain** dizisi.

8. Özelliklerini düzenlemek **GetWmiObject** etkinlik aşağıdaki gibi.

   |Özellik|Değer|
   |--------------|-----------|
   |**Sınıfı**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Ekleme bir **AddComputer** etkinliğini **JoinDomain** sonra sıra **GetWmiObject** etkinlik.

10. Özelliklerini düzenlemek **AddComputer** etkinlik aşağıdaki gibi.

    |Özellik|Değer|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Ekleme bir **RestartComputer** etkinliğini **JoinDomain** sonra sıra **AddComputer** etkinlik.

12. Özelliklerini düzenlemek **RestartComputer** etkinlik aşağıdaki gibi.

    |Özellik|Değer|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Kimlik bilgisi**|MachineCred|
    |**için**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Zorla**|True|
    |bekleme|True|
    |PSComputerName|{""}|

13. Ekleme bir **GetWmiObject** etkinliğini **JoinDomain** sonra sıra **RestartComputer** etkinlik. Önceki olarak aynı olacak şekilde özelliklerini düzenleme **GetWmiObject** etkinlik.

    Yordamları tamamladıktan sonra iş akışı tasarım penceresini aşağıdaki gibi görünmelidir.

    ![İş Akışı Tasarımcısı'nda JoinDomain XAML](../media/joindomainworkflow.png)
    ![JoinDomain XAML iş akışı Tasarımcısı'nda](../media/joindomainworkflow.png "JoinDomainWorkflow")