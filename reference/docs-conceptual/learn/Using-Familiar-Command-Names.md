---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Tanıdık Komut Adlarını Kullanma
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030903"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="eebbd-103">Tanıdık komut adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="eebbd-103">Using familiar command names</span></span>

<span data-ttu-id="eebbd-104">PowerShell komutları için diğer adlar tarafından başvurmak için diğer adlar destekler.</span><span class="sxs-lookup"><span data-stu-id="eebbd-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="eebbd-105">Diğer ad kullanımı deneyimi kullanıcılarla PowerShell de benzer işlemler için kullanıcılarınızın zaten bildikleri ortak komut adlarını kullanmak için diğer Kabukları sağlar.</span><span class="sxs-lookup"><span data-stu-id="eebbd-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="eebbd-106">Diğer ad kullanımı, yeni bir ad ile başka bir komuta ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="eebbd-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="eebbd-107">Örneğin, adında bir iç işlev PowerShell sahip `Clear-Host` , çıktı penceresini temizler.</span><span class="sxs-lookup"><span data-stu-id="eebbd-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="eebbd-108">Yazabilirsiniz `cls` veya `clear` diğer bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="eebbd-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="eebbd-109">PowerShell, bu diğer adlar yorumlar ve çalışan `Clear-Host` işlevi.</span><span class="sxs-lookup"><span data-stu-id="eebbd-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="eebbd-110">Bu özelliği PowerShell öğrenmek için kullanıcılara yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="eebbd-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="eebbd-111">İlk olarak, çoğu **cmd.exe** ve UNIX kullanıcıları kullanıcılar adına göre zaten bildiğiniz komut büyük bir topluluğu.</span><span class="sxs-lookup"><span data-stu-id="eebbd-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="eebbd-112">PowerShell eşdeğeri aynıdır sonuçları vermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="eebbd-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="eebbd-113">Ancak, sonuçları Kapat kullanıcıların yeterli PowerShell komut adını bilmeden çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="eebbd-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="eebbd-114">"Finger bellek" yeni bir komut kabuğunu öğrenme sıkıntıya başlıca kaynaklarından başka bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="eebbd-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="eebbd-115">Kullandıysanız **cmd.exe** reflexively yazabilir, yıllardır `cls` ekranı temizlemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="eebbd-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="eebbd-116">Diğer olmadan `Clear-Host`, bir hata iletisi alır ve çıktıyı temizlemek için yapmanız gerekenler bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="eebbd-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="eebbd-117">Aşağıdaki listede, birkaç ortak gösterilir **cmd.exe** ve PowerShell'de kullanabilirsiniz UNIX komutları:</span><span class="sxs-lookup"><span data-stu-id="eebbd-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="eebbd-118">Cat</span><span class="sxs-lookup"><span data-stu-id="eebbd-118">cat</span></span>|<span data-ttu-id="eebbd-119">dizini</span><span class="sxs-lookup"><span data-stu-id="eebbd-119">dir</span></span>|<span data-ttu-id="eebbd-120">Bağlama</span><span class="sxs-lookup"><span data-stu-id="eebbd-120">mount</span></span>|<span data-ttu-id="eebbd-121">RM</span><span class="sxs-lookup"><span data-stu-id="eebbd-121">rm</span></span>|
|<span data-ttu-id="eebbd-122">CD</span><span class="sxs-lookup"><span data-stu-id="eebbd-122">cd</span></span>|<span data-ttu-id="eebbd-123">echo</span><span class="sxs-lookup"><span data-stu-id="eebbd-123">echo</span></span>|<span data-ttu-id="eebbd-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="eebbd-124">move</span></span>|<span data-ttu-id="eebbd-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="eebbd-125">rmdir</span></span>|
|<span data-ttu-id="eebbd-126">chdir</span><span class="sxs-lookup"><span data-stu-id="eebbd-126">chdir</span></span>|<span data-ttu-id="eebbd-127">silme</span><span class="sxs-lookup"><span data-stu-id="eebbd-127">erase</span></span>|<span data-ttu-id="eebbd-128">popd</span><span class="sxs-lookup"><span data-stu-id="eebbd-128">popd</span></span>|<span data-ttu-id="eebbd-129">Uyku</span><span class="sxs-lookup"><span data-stu-id="eebbd-129">sleep</span></span>|
|<span data-ttu-id="eebbd-130">Temizle</span><span class="sxs-lookup"><span data-stu-id="eebbd-130">clear</span></span>|<span data-ttu-id="eebbd-131">H</span><span class="sxs-lookup"><span data-stu-id="eebbd-131">h</span></span>|<span data-ttu-id="eebbd-132">ps</span><span class="sxs-lookup"><span data-stu-id="eebbd-132">ps</span></span>|<span data-ttu-id="eebbd-133">Sıralama</span><span class="sxs-lookup"><span data-stu-id="eebbd-133">sort</span></span>|
|<span data-ttu-id="eebbd-134">CLS</span><span class="sxs-lookup"><span data-stu-id="eebbd-134">cls</span></span>|<span data-ttu-id="eebbd-135">geçmiş</span><span class="sxs-lookup"><span data-stu-id="eebbd-135">history</span></span>|<span data-ttu-id="eebbd-136">pushd</span><span class="sxs-lookup"><span data-stu-id="eebbd-136">pushd</span></span>|<span data-ttu-id="eebbd-137">Tee</span><span class="sxs-lookup"><span data-stu-id="eebbd-137">tee</span></span>|
|<span data-ttu-id="eebbd-138">kopyalama</span><span class="sxs-lookup"><span data-stu-id="eebbd-138">copy</span></span>|<span data-ttu-id="eebbd-139">sonlandırma</span><span class="sxs-lookup"><span data-stu-id="eebbd-139">kill</span></span>|<span data-ttu-id="eebbd-140">Parola</span><span class="sxs-lookup"><span data-stu-id="eebbd-140">pwd</span></span>|<span data-ttu-id="eebbd-141">tür</span><span class="sxs-lookup"><span data-stu-id="eebbd-141">type</span></span>|
|<span data-ttu-id="eebbd-142">DEL</span><span class="sxs-lookup"><span data-stu-id="eebbd-142">del</span></span>|<span data-ttu-id="eebbd-143">LP</span><span class="sxs-lookup"><span data-stu-id="eebbd-143">lp</span></span>|<span data-ttu-id="eebbd-144">r</span><span class="sxs-lookup"><span data-stu-id="eebbd-144">r</span></span>|<span data-ttu-id="eebbd-145">Yazma</span><span class="sxs-lookup"><span data-stu-id="eebbd-145">write</span></span>|
|<span data-ttu-id="eebbd-146">Fark</span><span class="sxs-lookup"><span data-stu-id="eebbd-146">diff</span></span>|<span data-ttu-id="eebbd-147">Ls</span><span class="sxs-lookup"><span data-stu-id="eebbd-147">ls</span></span>|<span data-ttu-id="eebbd-148">ren</span><span class="sxs-lookup"><span data-stu-id="eebbd-148">ren</span></span>||

<span data-ttu-id="eebbd-149">`Get-Alias` Cmdlet'i bir diğer ad ile ilişkili yerel PowerShell komutunu gerçek adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eebbd-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="eebbd-150">Standart diğer adlar yorumlama</span><span class="sxs-lookup"><span data-stu-id="eebbd-150">Interpreting standard aliases</span></span>

<span data-ttu-id="eebbd-151">Daha önce açıklanan diğer adı-diğer komut Kabuk ile uyumluluk için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="eebbd-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="eebbd-152">PowerShell'de yerleşik çoğu diğer adlar, konuyu uzatmamak amacıyla tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="eebbd-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="eebbd-153">Daha kısa adları, tür, ancak bunlar ne başvuruda bulunulan tanımadığınız varsa okunması zor kolaydır.</span><span class="sxs-lookup"><span data-stu-id="eebbd-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="eebbd-154">PowerShell diğer adları arasında netlik ve kısaltma tehlikeye deneyin.</span><span class="sxs-lookup"><span data-stu-id="eebbd-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="eebbd-155">PowerShell, diğer adlar standart bir dizi ortak adlar ve fiiller için kullanır.</span><span class="sxs-lookup"><span data-stu-id="eebbd-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="eebbd-156">Örnek kısaltmalar:</span><span class="sxs-lookup"><span data-stu-id="eebbd-156">Example abbreviations:</span></span>

| <span data-ttu-id="eebbd-157">İsim veya fiili</span><span class="sxs-lookup"><span data-stu-id="eebbd-157">Noun or Verb</span></span> | <span data-ttu-id="eebbd-158">Kısaltması</span><span class="sxs-lookup"><span data-stu-id="eebbd-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="eebbd-159">Alma</span><span class="sxs-lookup"><span data-stu-id="eebbd-159">Get</span></span>          | <span data-ttu-id="eebbd-160">G</span><span class="sxs-lookup"><span data-stu-id="eebbd-160">g</span></span>            |
| <span data-ttu-id="eebbd-161">Ayarla</span><span class="sxs-lookup"><span data-stu-id="eebbd-161">Set</span></span>          | <span data-ttu-id="eebbd-162">s</span><span class="sxs-lookup"><span data-stu-id="eebbd-162">s</span></span>            |
| <span data-ttu-id="eebbd-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="eebbd-163">Item</span></span>         | <span data-ttu-id="eebbd-164">Ben</span><span class="sxs-lookup"><span data-stu-id="eebbd-164">i</span></span>            |
| <span data-ttu-id="eebbd-165">Konum</span><span class="sxs-lookup"><span data-stu-id="eebbd-165">Location</span></span>     | <span data-ttu-id="eebbd-166">m</span><span class="sxs-lookup"><span data-stu-id="eebbd-166">l</span></span>            |
| <span data-ttu-id="eebbd-167">Komut</span><span class="sxs-lookup"><span data-stu-id="eebbd-167">Command</span></span>      | <span data-ttu-id="eebbd-168">cm</span><span class="sxs-lookup"><span data-stu-id="eebbd-168">cm</span></span>           |
| <span data-ttu-id="eebbd-169">Diğer Ad</span><span class="sxs-lookup"><span data-stu-id="eebbd-169">Alias</span></span>        | <span data-ttu-id="eebbd-170">Al</span><span class="sxs-lookup"><span data-stu-id="eebbd-170">al</span></span>           |

<span data-ttu-id="eebbd-171">Kısaltılmış bildiğinizde bu diğer adlar anlaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="eebbd-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="eebbd-172">Cmdlet adı</span><span class="sxs-lookup"><span data-stu-id="eebbd-172">Cmdlet name</span></span>    | <span data-ttu-id="eebbd-173">Diğer Ad</span><span class="sxs-lookup"><span data-stu-id="eebbd-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="eebbd-174">GI</span><span class="sxs-lookup"><span data-stu-id="eebbd-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="eebbd-175">sı</span><span class="sxs-lookup"><span data-stu-id="eebbd-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="eebbd-176">GL</span><span class="sxs-lookup"><span data-stu-id="eebbd-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="eebbd-177">SL</span><span class="sxs-lookup"><span data-stu-id="eebbd-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="eebbd-178">gcm</span><span class="sxs-lookup"><span data-stu-id="eebbd-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="eebbd-179">Gal</span><span class="sxs-lookup"><span data-stu-id="eebbd-179">gal</span></span>   |

<span data-ttu-id="eebbd-180">PowerShell diğer ad kullanımı ile ilgili bilgi sahibi olduğunuzda, tahmin edilmesi kolaydır **sal** diğer başvurduğu `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="eebbd-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="eebbd-181">Yeni takma adlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="eebbd-181">Creating new aliases</span></span>

<span data-ttu-id="eebbd-182">Kendi diğer adları kullanarak oluşturabileceğiniz `Set-Alias` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="eebbd-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="eebbd-183">Örneğin, aşağıdaki deyimleri, daha önce bahsedilen standart cmdlet diğer adlar oluşturma:</span><span class="sxs-lookup"><span data-stu-id="eebbd-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="eebbd-184">Dahili olarak, başlatma sırasında benzer komutlarda PowerShell kullanır, ancak bu diğer adlar takımdaki herhangi biri değildir.</span><span class="sxs-lookup"><span data-stu-id="eebbd-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="eebbd-185">Bu komutlardan birini yürütün çalışırsanız, diğer adı değiştirilemez açıklayan bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="eebbd-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="eebbd-186">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eebbd-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
