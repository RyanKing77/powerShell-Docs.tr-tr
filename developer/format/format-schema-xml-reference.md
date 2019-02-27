---
title: Şema XML başvurusu biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 4dfe27a5105d82fa18e35f965f92fad16d390a2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848065"
---
# <a name="format-schema-xml-reference"></a>Biçim Şeması XML Başvurusu

Bu bölümdeki konular (Format.ps1xml dosyaları) biçimlendirme tarafından kullanılan XML öğeleri açıklar. .NET nesnesini nasıl görüntüleneceğini biçimlendirme dosyaları tanımlayın. nesne değişmez.

## <a name="in-this-section"></a>Bu Bölümde

[TableControl (biçimi) için TableColumnHeader için hizalama öğesi](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) bir sütun üst bilgisindeki verilerin nasıl görüntüleneceğini tanımlar.

[TableControl (biçimi) için TableColumnItem için hizalama öğesi](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) satırdaki verileri nasıl görüntüleneceğini tanımlar.

[TableControl (biçimi) için AutoSize öğesi](./autosize-element-for-tablecontrol-format.md) veri boyutuna bağlı olup sütun boyutu ve sütun sayısı ayarlanır belirtir.

[AutoSize öğesi WideControl (biçimi) için](./autosize-element-for-widecontrol-format.md) veri boyutuna bağlı olup sütun boyutu ve sütun sayısı ayarlanır belirtir.

[ColumnNumber öğesi WideControl (biçimi) için](./columnnumber-element-for-widecontrol-format.md) geniş görüntülenmesini sütun sayısını belirtir.

[Yapılandırma öğesi (biçimi)](./configuration-element-format.md) biçimlendirme dosyanın üst düzey öğesi temsil eder.

[Denetim öğesi yapılandırma (biçimi) için denetimleri için](./control-element-for-controls-for-configuration-format.md) biçimlendirme dosya ve denetime başvurmak için kullanılan ad tüm görünümler tarafından kullanılan ortak bir denetimi tanımlar.

[Denetim öğesi görünümü (biçimi) için denetimleri için](./control-element-for-controls-for-view-format.md) Görünüm ve denetimin başvurmak için kullanılan ad tarafından kullanılabilecek bir denetimi tanımlar.

[Denetimleri yapılandırma (biçimi) için öğe](./controls-element-for-configuration-format.md) biçimlendirme dosyanın tüm görünümler tarafından kullanılabilen ortak denetimleri tanımlar.

[Denetimleri öğesi görünümü (biçimi) için](./controls-element-for-view-format.md) belirli bir görünüm tarafından kullanılabilen görünüm denetimlerini tanımlar.

[Özel denetim öğesi denetimi için yapılandırma (biçimi)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) bir denetimi tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Özel denetim öğesi denetimi için Görünüm (biçimi) için denetimleri](./customcontrol-element-for-control-for-controls-for-view-format.md) görünüm tarafından kullanılan bir denetimi tanımlar.

[GroupBy (biçimi) için özel denetim öğesi](./customcontrol-element-for-groupby-format.md) yeni grubu gösteren özel bir denetimi tanımlar.

[Özel denetim öğesi (biçimi)](./customcontrol-element-for-groupby-format.md) görünüm için bir özel denetim biçimini tanımlar.

[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding CustomControlName öğesi](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) ortak bir denetimin adını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[CustomControlName öğesi görünümü (biçimi) için denetimleri için ExpressionBindine için](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) bir ortak denetimi veya bir görünüm denetimi adını belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[GroupBy (biçimi) öğesinin CustomControlName](./customcontrolname-element-for-groupby-format.md) yeni grubunu görüntülemek için kullanılan özel bir denetimin adını belirtir. Bu öğe, bir tablo, liste, geniş veya özel denetimi görünüm tanımlarken, kullanılır.

[Yapılandırma (biçimi) için denetimler için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) bir tanımı ortak denetimi sağlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[CustomEntry öğesi görünümü (biçimi) için denetimleri için CustomEntries için](./customentry-element-for-customentries-for-controls-for-view-format.md) denetim tanımını sağlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[CustomEntry öğesi görünümü (biçimi) için CustomEntries için](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) özel denetim görünüm tanımını sağlar.

[GroupBy (biçimi) için özel denetim için CustomEntry öğesi](./customentry-element-for-customcontrol-for-groupby-format.md) denetim tanımını sağlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[Yapılandırma (biçimi) için özel denetim için CustomEntries öğesi](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) tanımlarını bir ortak denetimi sağlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[CustomEntries öğesi görünümü (biçimi) için denetimler için özel denetim için](./customentries-element-for-customcontrol-for-controls-for-view-format.md) tanımları denetimi sağlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[GroupBy (biçimi) için özel denetim için CustomEntries öğesi](./customentries-element-for-customcontrol-for-groupby-format.md) tanımları denetimi sağlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[CustomEntries öğesi görünümü (biçimi) için özel denetim için](./customentries-element-for-customcontrol-for-view-format.md) özel denetim görünüm tanımını sağlar. Özel denetimin görünümü, bir veya daha fazla tanımları belirtmeniz gerekir.

[Yapılandırma için denetimleri için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-controls-for-configuration-format.md) hangi verilerin denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[CustomItem öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./customitem-element-for-customentry-for-controls-for-view-format.md) hangi verilerin denetimi tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[CustomItem öğesi görünümü (biçimi) için CustomEntry için](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) hangi verileri özel denetim görünüm tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için CustomEntry için CustomItem öğesi](./customitem-element-for-customentry-for-groupby-format.md) hangi verileri özel denetim görünüm tarafından görüntülenen ve nasıl görüntüleneceğini tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[DefaultSettings öğesi (biçimi)](./defaultsettings-element-format.md) biçimlendirme dosyanın tüm görünümleri için geçerli genel ayarlarını tanımlar. Ortak ayarları hataları görüntüleme koleksiyonları nasıl genişletilir, tanımlama, tabloları ve diğer metin kaydırma içerir.

[DisplayError öğesi (Frmat)](./displayerror-element-format.md) bir hata oluştuğunda bir veri parçasını görüntüleme dizesi #ERR görüntüleneceğini belirtir.

[İçin yapılandırma (biçimi) için denetimleri için CustomEntry EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) ortak denetimi veya bu denetim için kullanılacak bulunmalıdır koşul tanımı kullanan .NET türlerini tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[EntrySelectedBy öğesi görünümü (biçimi) için denetimleri için CustomEntry için](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) bu denetimi tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[EntrySelectedBy öğesi görünümü (biçimi) için CustomEntry için](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) bu özel giriş veya kullanılmak üzere bu giriş için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.

[EntrySelectedBy öğesi EnumerableExpansion (biçimi) için](./entryselectedby-element-for-enumerableexpansion-format.md) bu tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar.

[GroupBy (biçimi) için CustomEntry için EntrySelectedBy öğesi](./entryselectedby-element-for-customentry-for-groupby-format.md) bu denetimi tanımı veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[EntrySelectedBy öğesi ListEntry ListControl (biçimi) için için](./entryselectedby-element-for-listentry-for-listcontrol-format.md) bu liste görünümü tanımını veya kullanılmak üzere bu tanım için bulunması gereken bir koşulu kullanan .NET türlerini tanımlar. Çoğu durumda, yalnızca bir tanımı bir liste görünümü için gereklidir. Ancak, farklı nesneler için farklı veri görüntülemek için aynı liste görünümü kullanmak istiyorsanız, liste görünümü için birden çok tanım sağlayabilirsiniz.

[EntrySelectedBy öğesi TableRowEntry (biçimi) için](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) özellik değerleri satır içinde görüntülenen .NET türlerini tanımlar.

[EntrySelectedBy öğesi WideEntry (biçimi) için](./entryselectedby-element-for-wideentry-format.md) geniş bir görünüm veya bu tanım için kullanılacak bulunmalıdır koşul bu tanımı kullanan .NET türlerini tanımlar.

[EnumerableExpansion öğesi (biçimi)](./enumerableexpansion-element-format.md) nesneler Görünümü'nde görüntülendiğinde genişletilmiş belirli .NET koleksiyonu tanımlar.

[EnumerableExpansions öğesi (biçimi)](./enumerableexpansions-element-format.md) Görünümü'nde görüntülendiğinde .NET koleksiyon nesnelerini nasıl genişletilir tanımlar.

[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding EnumerateCollection öğesi](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) belirtilen koleksiyonun öğelerini denetimi tarafından görüntülenen. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[EnumerateCollection öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) öğelerini koleksiyonlar görüntülenir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[EnumerateCollection öğesi görünümü (biçimi) için özel denetim için ifade bağlama](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) koleksiyon öğelerini görüntülendiğini belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için ExpressionBinding için EnumerateCollection öğesi](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) koleksiyon öğelerini görüntülendiğini belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[Öğesi (biçimi) genişletin](./expand-element-format.md) koleksiyon nesnesi bu tanım için nasıl genişletilmiş belirtir.

[İçin yapılandırma (biçimi) için denetimleri için CustomItem ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) denetimi tarafından görüntülenen verileri tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[ExpressionBinding öğesi görünümü (biçimi) için denetimleri için CustomItem için](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) denetimi tarafından görüntülenen verileri tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[ExpressionBinding öğesi görünümü (biçimi) için özel denetim için CustomItem için](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) denetimi tarafından görüntülenen verileri tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için CustomItem için ExpressionBinding öğesi](./expressionbinding-element-for-customitem-for-groupby-format.md) denetimi tarafından görüntülenen verileri tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) veri ilk satırının sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Çerçeve, denetimlerin görünümünü (biçimi) öğesinin FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) veri ilk satırının sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[FirstLineHanging öğesi görünümü (biçimi) için özel denetim için çerçeve için](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) veri ilk satırının sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için bir çerçeve için FirstLineHanging öğesi](./firstlinehanging-element-for-frame-for-groupby-format.md) veri ilk satırının sola kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[Denetimler için yapılandırma (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) verilerin ilk satırı sağa kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Çerçeve, denetimlerin görünümünü (biçimi) öğesinin FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) verilerin ilk satırı sağa kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) verilerin ilk satırı sağa kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için bir çerçeve için FirstLineIndent öğesi](./firstlineindent-element-for-frame-for-groupby-format.md) verilerin ilk satırı sağa kaydırılacak karakterlerinin kaçının tutulacağını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ListItem (biçimi) için FormatString öğesi](./formatstring-element-for-listitem-for-listcontrol-format.md) özelliği veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

[TableColumnItem (biçimi) için FormatString öğesi](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) tablo özelliği veya komut dosyası değerini nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

[WideItem WideControl (biçimi) için için FormatString öğesi](./formatstring-element-for-wideitem-for-widecontrol-format.md) Görünümü'nde özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim desenini belirtir.

[Öğe denetimleri için yapılandırma (biçimi) için CustomItem için çerçeve](./frame-element-for-customitem-for-controls-for-configuration-format.md) verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Çerçeve öğesi görünümü (biçimi) için denetimleri için CustomItem için](./frame-element-for-customitem-for-controls-for-view-format.md) verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[Çerçeve öğesi için CustomItem Görünüm (biçimi) için özel denetim için](./frame-element-for-customitem-for-customcontrol-for-view-format.md) verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[Çerçeve öğesi için CustomItem GroupBy (biçimi) için](./frame-element-for-customitem-for-groupby-format.md) verinin, veri sola veya sağa kaydırma gibi görüntülenme şeklini tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[GroupBy öğesi görünümü (biçimi) için](./groupby-element-for-view-format.md) Windows PowerShell yeni bir grup nesnelerin biçimini tanımlar.

[HideTableHeaders öğesi (biçimi)](./hidetableheaders-element-format.md) Tablo üst bilgilerini görüntülenmediğini belirler.

[İçin yapılandırma (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Görünüm (biçimi) için denetimleri için ExpressionBinding ItemSelectionCondition öğesinin](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[ItemSelectionCondition öğesi görünümü (biçimi) için özel denetim için ifade bağlama](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bir denetim öğesi için belirtilip seçimi koşullar sayısı sınırı yoktur. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için ExpressionBinding için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) bu denetim için kullanılacak bulunmalıdır koşulu tanımlar. Bir denetim öğesi için belirtilip seçimi koşullar sayısı sınırı yoktur. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ListItem (biçimi) için ItemSelectionCondition öğesi](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) bu liste öğesi için kullanılacak bulunmalıdır koşulu tanımlar.

[Etiket öğesi için ListItem için ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) satırda özelliği veya betik değer etiketini belirtir.

[GroupBy (biçimi) için etiket öğesi](./label-element-for-groupby-format.md) yeni bir grup ile karşılaşıldığında görüntülenen etiketi belirtir.

[Etiket öğesi TableColumnHeader (biçimi) için](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) sütunun en üstünde gösterilen etiketi tanımlar.

[Denetimler için yapılandırma (biçimi) için bir çerçeve için LeftIndent öğesi](./leftindent-element-for-frame-for-controls-for-configuration-format.md) veri uzağa sol kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Çerçeve, denetimlerin görünümünü (biçimi) öğesinin LeftIndent](./leftindent-element-for-frame-for-controls-for-view-format.md) veri uzağa sol kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[LeftIndent öğesi görünümü (biçimi) için özel denetim için çerçeve için](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) veri uzağa sol kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için bir çerçeve için LeftIndent öğesi](./leftindent-element-for-frame-for-groupby-format.md) veri uzağa sol kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ListControl öğesi (biçimi)](./listcontrol-element-format.md) görünüm için bir liste biçimini tanımlar.

[ListEntry öğesi (biçimi)](./listentry-element-for-listcontrol-format.md) liste görünümü tanımını sağlar.

[ListEntries öğesi (biçimi)](./listentries-element-for-listcontrol-format.md) satırları liste görünümünün nasıl görüntüleneceğini tanımlar.

[LISTITEM öğesinin (biçimi)](./listitem-element-for-listitems-for-listcontrol-format.md) betik değeri liste görünümünün bir satır görüntülenir ve özelliği tanımlar.

[ListItems öğesi (biçimi)](./listitems-element-for-listentry-for-listcontrol-format.md) liste görünümünde görüntülenen betikleri ve özellikleri tanımlar.

[Ad öğesi denetimi için yapılandırma (biçimi) için denetimleri](./name-element-for-control-for-controls-for-configuration-format.md) denetimin adını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Öğe adı SelectionSet (biçimi) için](./name-element-for-selectionset-format.md) seçimi kümesi başvurmak için kullanılan adı belirtir.

[Öğesi görünümü (biçimi) için ad](./name-element-for-view-format.md) görünümü tanımlamak için kullanılan adı belirtir.

[Yeni satır öğesi için yapılandırma (biçimi) için denetimleri için CustomItem](./newline-element-for-customitem-for-controls-for-configuration-format.md) denetimin görünümünü için boş bir satır ekler. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Yeni satır öğesi görünümü (biçimi) için denetimleri için CustomItem için](./newline-element-for-customitem-for-controls-for-view-format.md) denetimin görünümünü için boş bir satır ekler. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[Yeni satır öğesi görünümü (biçimi) için özel denetim için CustomItem için](./newline-element-for-customitem-for-customcontrol-for-view-format.md) denetimin görünümünü için boş bir satır ekler. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için CustomItem için yeni satır öğesi](./newline-element-for-customitem-for-groupby-format.md) denetimin görünümünü için boş bir satır ekler. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[PropertyName öğesi için yapılandırma (biçimi) için denetimleri için ExpressionBinding](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) .NET özelliğinin değeri bir ortak denetimi tarafından görüntülenen belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[PropertyName öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) .NET özelliğinin değeri denetimi tarafından görüntülenen belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[PropertyName öğesi görünümü (biçimi) için özel denetim için ExpressionBinding için](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) .NET özelliğinin değeri denetimi tarafından görüntülenen belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için ExpressionBinding için PropertyName öğesi](./propertyname-element-for-expressionbinding-for-groupby-format.md) .NET özelliğinin değeri denetimi tarafından görüntülenen belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[GroupBy (biçimi) için PropertyName öğesi](./propertyname-element-for-groupby-format.md) .NET özelliğinin değeri değiştiğinde yeni bir grup başlatan belirtir.

[PropertyName öğesi için yapılandırma (biçimi) için denetimleri için ItemSeclectionCondition](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[PropertyName öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[Görünüm için özel denetim için ItemSelectionCondition için PropertyName öğesi (biçim](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için ItemSelectionCondition için PropertyName öğesi](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ListItem (biçimi) için ItemSelectionCondition için PropertyName öğesi](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve görünümü kullanılır. Bu öğe, bir liste görünümü tanımlarken kullanılır.

[ListItem ListControl (biçimi) için için PropertyName öğesi](./propertyname-element-for-listitem-for-listcontrol-format.md) .NET özelliğinin değeri listesinde görüntülenen belirtir.

[PropertyName öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve giriş kullanılır. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[PropertyName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve giriş kullanılır. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[PropertyName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[PropertyName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır.

[GroupBy (biçimi) için SelectionCondition için PropertyName öğesi](./propertyname-element-for-selectioncondition-for-groupby-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[PropertyName öğesi SelectionCondition ListEntry (biçimi) için EmtrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve liste girdisini kullanılır.

[PropertyName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tablo girişi kullanılır.

[PropertyName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) koşul tetikleyen .NET alan özelliği belirtir. Bu özellik mevcut olduğunda veya için değerlendirirken `true`, koşul karşılanır ve tanımı kullanılır.

[PropertyName öğesi TableColumnItem (biçimi) için](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) değeri satır sütununda görüntülenen alan özelliği belirtir.

[PropertyName öğesi WideItem (biçimi) için](./propertyname-element-for-wideitem-for-widecontrol-format.md) değeri, geniş görünümde görüntülenir nesnesinin özelliğini belirtir.

[Denetimler için yapılandırma (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-controls-for-configuration-format.md) veri uzağa sağ kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Çerçeve, denetimlerin görünümünü (biçimi) öğesinin RightIndent](./rightindent-element-for-frame-for-controls-for-view-format.md) veri uzağa sağ kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[RightIndent öğesi](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) veri uzağa sağ kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için bir çerçeve için RightIndent öğesi](./rightindent-element-for-frame-for-groupby-format.md) veri uzağa sağ kenar boşluğu IPSec'in karakterlerinin kaçının tutulacağını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ScriptBlock öğesi için yapılandırma (biçimi) için denetimleri için ExpressionBinding](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) değeri ortak denetimi tarafından görüntülenen komut dosyasını belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[ScriptBlock öğesi görünümü (biçimi) için denetimleri için ExpressionBinding için](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) değeri denetimi tarafından görüntülenen komut dosyasını belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[ScriptBlock öğesi görünümü (biçimi) için CustomCustomControl için ExpressionBinding için](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) değeri denetimi tarafından görüntülenen komut dosyasını belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için ExpressionBinding için ScriptBlock öğesi](./scriptblock-element-for-expressionbinding-for-groupby-format.md) değeri denetimi tarafından görüntülenen komut dosyasını belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[GroupBy (biçimi) için ScriptBlock öğesi](./scriptblock-element-for-groupby-format.md) değeri değiştiğinde yeni bir grup başlatan betiği belirtir.

[ScriptBlock öğesi için yapılandırma (biçimi) için denetimleri için ItemSelectionCondition](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[ScriptBlock öğesi görünümü (biçimi) için denetimleri için ItemSelectionCondition için](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[ScriptBlock öğesi görünümü (biçimi) için özel denetim için ItemSelectionCondition için](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için ItemSelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve denetimi kullanılır. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ScriptBlock öğesi ItemSelectionCondition ListControl (biçimi) için için](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve liste öğesi kullanılır. Bu öğe, bir liste görünümü tanımlarken kullanılır.

[ListItem (biçimi) için ScriptBlock öğesi](./scriptblock-element-for-listitem-for-listcontrol-format.md) değeri listesinin satırında görüntülenen komut dosyasını belirtir.

[ScriptBlock öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[ScriptBlock öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[ScriptBlock öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[ScriptBlock öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) koşul tetikleyen betiği belirtir.

[GroupBy (biçimi) için SelectionCondition için ScriptBlock öğesi](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tanımı kullanılır. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[ScriptBlock öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve liste girdisini kullanılır.

[ScriptBlock öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) koşul tetikler betik bloğu belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve tablo girişi kullanılır.

[ScriptBlock öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) koşul tetikleyen betiği belirtir. Ne zaman bu kod değerlendirilir için `true`, koşul karşılanır ve geniş bir girdi tanımı kullanılır.

[ScriptBlock öğesi TableColumnItem (biçimi) için](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) değeri satır sütununda görüntülenen komut dosyasını belirtir.

[ScriptBlock öğesi WideItem (biçimi) için](./scriptblock-element-for-wideitem-for-widecontrol-format.md) değeri, geniş görünümde görüntülenir betiği belirtir.

[İçin yapılandırma (biçimi) için CustomEntry için EntrySelectedBy SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) kullanılacak ortak bir denetim tanımı için bulunması gereken bir koşulu tanımlar. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[SelectionCondition öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) kullanılacak denetimi tanımı bulunması gereken bir koşulu tanımlar. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[SelectionCondition öğesi görünümü (biçimi) için özel denetim için EntrySelectedBy için](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) kullanılmak üzere bir denetim tanımı için bulunması gereken bir koşulu tanımlar. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[SelectionCondition öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) bu tanımın koleksiyon nesnelerini genişletmek için bulunması gereken koşulu tanımlar.

[GroupBy (biçimi) için EntrySelectedBy için SelectionCondition öğesi](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) kullanılmak üzere bir denetim tanımı için bulunması gereken bir koşulu tanımlar. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[SelectionCondition öğesi EntrySelectedBy ListEntry (biçimi) için için](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) liste görünümünde bu tanımı kullanmak için mevcut olmalıdır koşulu tanımlar. Bir liste tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.

[SelectionCondition öğesi EntrySelectedBy TableRowEntry (biçimi) için için](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) bu tabloda görünüm tanımı için kullanılmak üzere mevcut olmalıdır koşulu tanımlar. Tablo tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.

[SelectionCondition öğesi EntrySelectedBy WideEntry (biçimi) için için](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) kullanılmak üzere bu tanım için bulunması gereken koşulu tanımlar. Geniş bir girdi tanımı için belirtilen seçim koşullar sayısı sınırı yoktur.

[SelectionSet öğesi (biçimi)](./selectionset-element-format.md) kümesinin adı tarafından başvurulan bir .NET nesne tanımlar.

[İçin yapılandırma (biçimi) için denetimleri için EntrySelectedBy SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) denetimi bu tanımı kullanan .NET türleri kümesini belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[SelectionSetName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) denetimi bu tanımı kullanan .NET türleri kümesini belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[SelectionSetName öğesi EntrySelectedBy CustomEntry (biçimi) için için](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) .NET nesneleri listesi girişi için bir dizi belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.

[SelectionSetName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) bu tanımı tarafından genişletilen .NET türleri kümesini belirtir.

[GroupBy (biçimi) için EntrySelectedBy için SelectionSetName öğesi](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) .NET nesneleri listesi girişi için bir dizi belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[SelectionSetName öğesi EntrySelectedBy ListEntry (biçimi) için için](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) .NET nesneleri listesi girişi için bir dizi belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.

[SelectionSetName öğesi EntrySelectedBy TableRowEntry (biçimi) için için](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) .NET bir dizi tablo görünümü, bu girdi kullanım türleri belirtir. Bir giriş için belirtilen seçim kümeleri sayısı sınırı yoktur.

[SelectionSetName öğesi EntrySelectedBy WideEntry (biçimi) için için](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) tanımı için bir .NET nesne belirtir. Bu nesnelerden birinin görüntülendiği zaman tanımı kullanılır.

[İçin yapılandırma (biçimi) için denetimleri için SelectionCondition SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[SelectionSetName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[EntrySelectedBy öğesi görünümü (biçimi) için CustomEntry için](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[SelectionSetName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır.

[GroupBy (biçimi) için SelectionCondition için SelectionSetName öğesi](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu denetimi kullanarak görüntülenir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[SelectionSetName öğesi SelectionCondition ListEntry (biçimi) için EntrySelectedBy için için](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu liste görünümü tanımını kullanarak görüntülenir.

[SelectionSetName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu tablo görünümü tanımını kullanarak görüntülenir.

[SelectionSetName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) tetikleyen koşulu .NET türleri kümesini belirtir. Bu türlerinden herhangi birini mevcut olduğunda, koşul karşılanır ve nesne bu geniş görünüm tanımını kullanarak görüntülenir.

[SelectionSetName öğesi ViewSelectedBy (biçimi) için](./selectionsetname-element-for-viewselectedby-format.md) görünüm tarafından görüntülenen .NET nesneleri kümesini belirtir.

[SelectionSets öğesi (biçimi)](./selectionsets-element-format.md) tek biçim görünümler tarafından kullanılan .NET nesneleri kümesini tanımlar.

[ShowError öğesi (biçimi)](./showerror-element-format.md) tam hata kaydı, bir veri parçasını görüntülenirken bir hata oluştuğunda görüntülendiğini belirtir.

[TableControl (biçimi) için TableHeaders için TableColumnHeader öğesi](./tablecolumnheader-element-format.md) etiketi, bir sütunun genişliğini ve hizalamasını tablosunun bir sütunu etiketi tanımlar.

[TableColumnItem öğesi (biçimi)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) özellik veya betik değeri satır sütununda görüntülenen tanımlar.

[TableColumnItems öğesi (biçimi)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) betikleri değerleri satır görüntülenir ve özellikleri tanımlar.

[TableControl öğesi (biçimi)](./tablecontrol-element-format.md) bir görünüm için bir tablo biçiminde tanımlar.

[TableHeaders öğesi (biçimi)](./tableheaders-element-format.md) üstbilgileri için bir tablonun sütunlarını tanımlar.

[TableRowEntries öğesi (biçimi)](./tablerowentries-element-for-tablecontrol-format.md) tablonun satırlarını tanımlar.

[TableRowEntry öğesi (biçimi)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) bir tablonun satırında görüntülenen verileri tanımlar.

[Metin öğesi için yapılandırma (biçimi) için denetimleri için CustomItem](./text-element-for-customitem-for-controls-for-configuration-format.md) gibi bir etiket denetimi tarafından görüntülenen verilere eklenir belirtir metin, köşeli ayraçlar veri ve veri girintilemek için alanları içine almak için. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[Metin öğesi görünümü (biçimi) için denetimleri için CustomItem için](./text-element-for-customitem-for-controls-for-view-format.md) gibi bir etiket denetimi tarafından görüntülenen verilere eklenir belirtir metin, köşeli ayraçlar veri ve veri girintilemek için alanları içine almak için. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[Metin öğesi CustomItem (biçimi) için](./text-element-for-customitem-for-customview-for-view-format.md) gibi bir etiket denetimi tarafından görüntülenen verilere eklenir belirtir metin, köşeli ayraçlar veri ve veri girintilemek için alanları içine almak için. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[GroupBy (biçimi) için CustomItem için metin öğesi](./text-element-for-customitem-for-groupby-format.md) gibi bir etiket denetimi tarafından görüntülenen verilere eklenir belirtir metin, köşeli ayraçlar veri ve veri girintilemek için alanları içine almak için. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[TypeName öğesi için yapılandırma (biçimi) için denetimleri için EntrySelectedBy](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) denetimi bu tanımı kullanan bir .NET türü belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[TypeName öğesi görünümü (biçimi) için denetimleri için EntrySelectedBy için](./typename-element-for-entryselectedby-for-controls-for-view-format.md) denetimi bu tanımı kullanan bir .NET türü belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[TypeName öğesi görünümü (biçimi) için CustomEntry için EntrySelectedBy için](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) özel denetim görünümün bu tanımı kullanan bir .NET türü belirtir. Bir tanımı için belirtilebilen türleri sayısı sınırı yoktur.

[TypeName öğesi EntrySelectedBy EnumerableExpansion (biçimi) için için](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) bu tanımı tarafından genişletilen bir .NET türünü belirtir. Bu öğe, varsayılan ayarları tanımlarken kullanılır.

[GroupBy (biçimi) için EntrySelectedBy için TypeName öğesi](./typename-element-for-entryselectedby-for-groupby-format.md) özel denetimin bu tanımı kullanan bir .NET türü belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[TypeName öğesi EntrySelectedBy ListControl (biçimi) için için](./typename-element-for-entryselectedby-for-listcontrol-format.md) liste görünümünün bu girişi kullanan .NET türü belirtir. Bir liste girişi için belirtilebilen türleri sayısı sınırı yoktur.

[TypeName öğesi EntrySelectedBy TableRowEntry (biçimi) için için](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Tablo görünümünde bu girişi kullanan bir .NET türü belirtir. Bir tablo girişi için belirtilebilen türleri sayısı sınırı yoktur.

[TypeName öğesi EntrySelectedBy WideEntry (biçimi) için için](./typename-element-for-entryselectedby-for-wideentry-format.md) tanımı için bir .NET türünü belirtir. Bu nesne görüntülenen her tanımı kullanılır.

[TypeName öğesi için yapılandırma (biçimi) için denetimleri için SelectionCondition](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu öğe, biçimlendirme dosyası içindeki tüm görünümler tarafından kullanılan bir ortak denetimi tanımlarken kullanılır.

[TypeName öğesi görünümü (biçimi) için denetimleri için SelectionCondition için](./typename-element-for-selectioncondition-for-controls-for-view-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu öğe bir görünüm tarafından kullanılan denetimler tanımlarken kullanılır.

[TypeName öğesi görünümü (biçimi) için özel denetim için SelectionCondition için](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu öğe, bir özel denetim görünüm tanımlarken kullanılır.

[TypeName öğesi SelectionCondition EnumerableExpansion (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) koşul tetikleyen bir .NET türünü belirtir.

[GroupBy (biçimi) için SelectionCondition için TypeName öğesi](./typename-element-for-selectioncondition-for-groupby-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu öğe, yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlarken kullanılır.

[TypeName öğesi SelectionCondition EntrySelectedBy ListControl (biçimi) için için için](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu tür, mevcut olduğunda listesi girişi kullanılır.

[TypeName öğesi SelectionCondition TableRowEntry (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu türü mevcut olduğunda, koşul karşılanır ve tablo satırı kullanılır.

[TypeName öğesi SelectionCondition WideEntry (biçimi) için EntrySelectedBy için için](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) koşul tetikleyen bir .NET türünü belirtir. Bu tür, mevcut olduğunda tanımı kullanılır.

[TypeName öğesi türleri (biçimi) için](./typename-element-for-types-format.md) .NET seçimi kümesine ait olan bir nesne türünü belirtir.

[TypeName öğesi ViewSelectedBy (biçimi) için](./typename-element-for-viewselectedby-format.md) görünüm tarafından görüntülenen bir .NET nesnesini belirtir.

[Öğesi (biçimi) türleri](./types-element-for-selectionset-format.md) seçiminde ayarlanan .NET nesneleri tanımlar.

[Öğesi (biçimi) görüntülemek](./view-element-format.md) bir veya daha fazla .NET nesneleri görüntülemek için kullanılan bir görünüm tanımlar.

[ViewDefinitions öğesi (biçimi)](./viewdefinitions-element-format.md) nesneleri görüntülemek için kullanılan görünümleri tanımlar.

[ViewSelectedBy öğesi (biçimi)](./viewselectedby-element-format.md) görünüm tarafından görüntülenen .NET nesneleri tanımlar.

[WideControl öğesi (biçimi)](./widecontrol-element-format.md) geniş (çoklu değer) listesini biçimlendirmek için görünümü tanımlar. Bu görünüm, tek bir özellik değeri ya da her nesne için betik değeri görüntüler.

[WideEntries öğesi (biçimi)](./wideentries-element-for-widecontrol-format.md) geniş görünüm tanımını sağlar. Geniş bir görünüm, bir veya daha fazla tanımları belirtmeniz gerekir.

[WideEntry öğesi (biçimi)](./wideentry-element-for-widecontrol-format.md) geniş görünüm tanımını sağlar.

[WideItem öğesi (biçimi)](./wideitem-element-for-widecontrol-format.md) betik değeri görüntülenir ve özelliği tanımlar.

[Genişlik öğesi (biçimi)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) (karakter cinsinden) bir sütunun genişliğini tanımlar.

[Öğesi (biçimi) sarmalamak](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) sütun genişliğini aşıyor metin ve sonraki satırda görüntüleneceğini belirtir.

[WrapTables öğesi (biçimi)](./wraptables-element-format.md) veri sütunun genişliği uzunsa veri tablo hücresi içinde sonraki satıra taşınır belirtir.

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
