---
title: Nasıl güncelleştirilebilir Yardımı Works | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794391"
---
# <a name="how-updatable-help-works"></a>Güncelleştirilebilir Yardım Nasıl Çalışır?

Bu konu, CAB ve HelpInfo XML dosyası her modül için dosyaları ve yükler güncelleştirilebilir Yardımı işlemleri kullanıcıları için Yardım nasıl güncelleştirileceğini açıklar.

## <a name="the-update-help-process"></a>Update-Help işlemi

Aşağıdaki listede eylemleri açıklar [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) bir kullanıcı belirli bir kullanıcı Arabirimi kültürünü bir modülde Yardım dosyaları güncelleştirmek için bir komutu çalıştırdığında cmdlet'i.

1. `Update-Help` değeri tarafından belirtilen konumdan uzak HelpInfo XML dosyasını alır **HelpInfoURI** anahtar modül bildiriminde ve dosyanın şemaya karşı doğrular. (Şemasını görüntülemek için bkz: [HelpInfo XML Şeması](./helpinfo-xml-schema.md).) Ardından `Update-Help` kullanıcının bilgisayarında yerel HelpInfo XML dosyasının modülü modülü dizinde arar.

2. `Update-Help` Yardım dosyaları uzak ve yerel HelpInfo XML dosyalarında modül için belirtilen UI kültürü için sürüm numarasını karşılaştırır. Uzak dosya çubuğunda sürüm numarasını sürüm numarası yerel dosya çubuğunda büyükse veya orada yerel HelpInfo XML dosyası modülü için ise `Update-Help` yeni Yardım dosyalarını indirmek hazırlar.

3. `Update-Help` Modül için CAB dosyası tarafından belirtilen konuma seçer **HelpContentUri** uzak HelpInfo XML dosyasında öğe. CAB dosyası tanımlamak için modül adı, modül GUID ve kullanıcı Arabirimi kültürünü kullanır.

4. `Update-Help` CAB dosyası indirilir, bu ayıklar, Yardım içerik dosyalarını doğrular ve Yardım içerik dosyalarını bir modül dizini dile özgü alt dizinde kullanıcının bilgisayarında kaydeder.

5. `Update-Help` Uzak HelpInfo XML dosyasını kopyalayarak bir yerel HelpInfo XML dosyası oluşturur. Yüklü CAB dosyası için öğeleri içeren yerel HelpInfo XML dosyasını düzenler. Ardından yerel HelpInfo XML dosyası bir modül dizine kaydeder ve güncelleştirme burada sona eriyor.

## <a name="the-save-help-process"></a>Save-Help işlemi

Aşağıdaki listede eylemleri açıklar [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) ve [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kullanıcı Yardım dosyaları bir dosya paylaşımındaki güncelleştirin ve ardından Yardım dosyalarını güncelleştirmek için bu dosyaları kullanmak için komutları çalıştırdığında cmdlet'leri kullanıcının bilgisayarına.

`Save-Help` Cmdlet'i tarafından belirtilen bir dosya paylaşımındaki bir modül için Yardım dosyaları kaydetmek için bir komuta verilen yanıt aşağıdaki eylemleri gerçekleştirir **HedefYolu** parametresi.

1. `Save-Help` değeri tarafından belirtilen konumdan uzak HelpInfo XML dosyasını alır **HelpInfoURI** anahtar modül bildiriminde ve dosyanın şemaya karşı doğrular. (Şemasını görüntülemek için bkz: [HelpInfo XML Şeması](./helpinfo-xml-schema.md).) Ardından `Save-Help` tarafından belirtilen dizine yerel bir HelpInfo XML dosyasını arar **HedefYolu** parametresinde `Save-Help` komutu.

2. `Save-Help` Yardım dosyaları uzak ve yerel HelpInfo XML dosyalarında modül için belirtilen UI kültürü için sürüm numarasını karşılaştırır. Uzak dosya çubuğunda sürüm numarasını sürüm numarası yerel dosya çubuğunda büyükse veya orada yerel HelpInfo XML dosyası içinde modülü için ise **HedefYolu** dizin `Save-Help` yeni Yardım dosyalarını indirmek hazırlar.

3. `Save-Help` Modül için CAB dosyası tarafından belirtilen konuma seçer **HelpContentUri** uzak HelpInfo XML dosyasında öğe. CAB dosyası tanımlamak için modül adı, modül GUID ve kullanıcı Arabirimi kültürünü kullanır.

4. `Save-Help` CAB dosyası indirilir ve onu kaydeder **HedefYolu** dizin. (Herhangi bir dile özgü alt oluşturmaz.)

5. `Save-Help` Uzak HelpInfo XML dosyasını kopyalayarak bir yerel HelpInfo XML dosyası oluşturur. Yalnızca, kaydedilmiş CAB dosyası için öğeleri içeren yerel HelpInfo XML dosyasını düzenler. Yerel HelpInfo XML dosyasında kaydeder ve sonra **HedefYolu** dizin ve güncelleştirme burada sona eriyor.

   `Update-Help` Cmdlet'i tarafından belirtilen bir dosya paylaşımındaki dosyalardan bir kullanıcının bilgisayarında Yardım dosyalarını güncelleştirmek için bir komuta verilen yanıt aşağıdaki eylemleri gerçekleştirir **SourcePath** parametresi.

1. `Update-Help` Uzak HelpInfo XML dosyasından alır **SourcePath** dizin. Ardından kullanıcının bilgisayarında yerel HelpInfo XML dosyasının modülü dizinde arar.

2. `Update-Help` Yardım dosyaları uzak ve yerel HelpInfo XML dosyalarında modül için belirtilen UI kültürü için sürüm numarasını karşılaştırır. Uzak dosya çubuğunda sürüm numarasını sürüm numarası yerel dosya çubuğunda büyükse veya orada hiçbir yerel HelpInfo XML dosyası ise `Update-Help` yeni Yardım dosyalarını yüklemeye hazırlanır.

3. `Update-Help` modülünden için CAB dosyası seçer **SourcePath** dizin. CAB dosyası tanımlamak için modül adı, modül GUID ve kullanıcı Arabirimi kültürünü kullanır.

4. `Update-Help` CAB dosyasını ayıklar, Yardım içerik dosyalarını doğrular ve Yardım içerik dosyalarını bir modül dizini dile özgü alt dizinde kullanıcının bilgisayarında kaydeder.

5. `Update-Help` Uzak HelpInfo XML dosyasını kopyalayarak bir yerel HelpInfo XML dosyası oluşturur. Yüklü CAB dosyası için öğeleri içeren yerel HelpInfo XML dosyasını düzenler. Ardından yerel HelpInfo XML dosyası bir modül dizine kaydeder ve güncelleştirme burada sona eriyor.