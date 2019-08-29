---
title: Bir Veri Deposuna Erişmek İçin Cmdlet Oluşturma
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 7acccbd48dcfb654b11e448a1f24835ad3668fae
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104459"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Bir Veri Deposuna Erişmek İçin Cmdlet Oluşturma

Bu bölümde, bir Windows PowerShell sağlayıcısı aracılığıyla depolanan verilere erişen bir cmdlet 'in nasıl oluşturulacağı açıklanmaktadır. Bu tür bir cmdlet, Windows PowerShell çalışma zamanının Windows PowerShell sağlayıcısı altyapısını kullanır ve bu nedenle, cmdlet sınıfı [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfından türetilmelidir.

Burada açıklanan Select-Str cmdlet 'i bir dosya veya nesne içindeki dizeleri bulabilir ve seçebilir. Dizeyi tanımlamak için kullanılan desenler, cmdlet 'in `Path` parametresi aracılığıyla açıkça veya `Script` parametresi aracılığıyla örtük olarak belirtilebilir.

Cmdlet 'i, [System. Management. Automation. Provider. ıtentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)'dan türetilen herhangi bir Windows PowerShell sağlayıcısını kullanmak için tasarlanmıştır. Örneğin cmdlet 'i, Windows PowerShell tarafından sunulan dosya sistemi sağlayıcısını veya değişken sağlayıcısını belirtebilir. Windows PowerShell sağlayıcılarını Aboutmore hakkında daha fazla bilgi için bkz. [Windows PowerShell sağlayıcınızı tasarlama](../prog-guide/designing-your-windows-powershell-provider.md).

## <a name="defining-the-cmdlet-class"></a>Cmdlet sınıfını tanımlama

Cmdlet oluşturma 'nın ilk adımı her zaman cmdlet 'i adlandırarak ve cmdlet 'i uygulayan .NET sınıfını bildiriyor. Bu cmdlet belirli dizeleri algılar, bu nedenle burada seçilen fiil adı [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) sınıfı tarafından tanımlanan "Select" olur. "Str" ad adı, cmdlet dizeler üzerinde hareket ettiğinden kullanılır. Aşağıdaki bildirimde, cmdlet fiilinin ve ad adının cmdlet sınıfının adında yansıtıldığını unutmayın. Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz. [cmdlet fiil adları](./approved-verbs-for-windows-powershell-commands.md).

Bu cmdlet 'in .NET sınıfı, Windows PowerShell sağlayıcısı altyapısını kullanıma sunmak için Windows PowerShell çalışma zamanı için gereken desteği sağladığından [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfından türetilmelidir. Bu cmdlet 'in Ayrıca [System. Text. RegularExpressions. Regex](/dotnet/api/System.Text.RegularExpressions.Regex)gibi .NET Framework normal ifade sınıflarını da kullanabileceğini unutmayın.

Aşağıdaki kod, bu Select-Str cmdlet 'inin sınıf tanımıdır.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Bu cmdlet, sınıf bildirimine `DefaultParameterSetName` Attribute anahtar sözcüğünü ekleyerek varsayılan bir parametre kümesini tanımlar. Varsayılan parametre kümesi `PatternParameterSet` `Script` parametresi belirtilmediğinde kullanılır. Bu parametre kümesi hakkında daha fazla bilgi için aşağıdaki bölümdeki `Pattern` ve `Script` parametresi tartışmasına bakın.

## <a name="defining-parameters-for-data-access"></a>Veri erişimi için parametreleri tanımlama

Bu cmdlet, kullanıcının depolanan verilere erişmesine ve bunları incelemesine izin veren çeşitli parametreleri tanımlar. Bu parametreler, veri `Path` deposunun konumunu, aramada kullanılacak kalıbı belirten bir `Pattern` parametreyi ve aramanın nasıl yapıldığını destekleyen diğer birkaç parametreyi içerir.

> [!NOTE]
> Parametreleri tanımlamanın temelleri hakkında daha fazla bilgi için, bkz. [komut satırı girişini Işleyen parametreler ekleme](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Yol parametresini bildirme

Veri deposunun yerini bulmak için, bu cmdlet 'in veri deposuna erişmek için tasarlanan Windows PowerShell sağlayıcısını belirlemek için bir Windows PowerShell yolu kullanması gerekir. Bu nedenle, sağlayıcının konumunu `Path` belirtmek için String dizisi türünde bir parametre tanımlar.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Bu parametrenin iki farklı parametre kümesine ait olduğunu ve bir diğer adı olduğunu unutmayın.

İki [System. Management. Automation. ParameterAttribute özniteliği](/dotnet/api/System.Management.Automation.ParameterAttribute) `Path` `ScriptParameterSet` parametresinin `PatternParameterSet`öğesine ve öğesine ait olduğunu bildirir. Parametre kümeleri hakkında daha fazla bilgi için bkz. [bir cmdlet 'e parametre kümeleri ekleme](./adding-parameter-sets-to-a-cmdlet.md).

[System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) özniteliği `Path` parametresi için bir `PSPath` diğer ad bildirir. Bu diğer adı bildirmek, Windows PowerShell sağlayıcılarına erişen diğer cmdlet 'lerle tutarlılık için önerilir. Windows PowerShell yollarını Aboutmore hakkında daha fazla bilgi için [Windows PowerShell 'In nasıl çalıştığı konusunda](/previous-versions//ms714658(v=vs.85))"PowerShell yol kavramları" başlığına bakın.

### <a name="declaring-the-pattern-parameter"></a>Model parametresini bildirme

Aranacak desenleri belirtmek için, bu cmdlet bir dize dizisi olan bir `Pattern` parametre bildirir. Veri deposunda desenlerden herhangi biri bulunduğunda pozitif bir sonuç döndürülür. Bu desenlerin derlenmiş normal ifadeler dizisine veya sabit değer aramaları için kullanılan joker karakter desenlerine bir diziye derleneceğini unutmayın.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Bu parametre belirtildiğinde, cmdlet varsayılan parametre kümesini `PatternParameterSet`kullanır. Bu durumda, cmdlet dizeleri seçmek için burada belirtilen desenleri kullanır. Buna karşılık `Script` , parametresi desenleri içeren bir komut dosyası sağlamak için de kullanılabilir. `Script` Ve`Pattern` parametreleri iki ayrı parametre kümesi tanımlar, bu nedenle birbirini dışlarlar.

### <a name="declaring-search-support-parameters"></a>Arama desteği parametrelerini bildirme

Bu cmdlet, cmdlet 'in arama yeteneklerini değiştirmek için kullanılabilecek aşağıdaki destek parametrelerini tanımlar.

`Script` Parametresi, cmdlet için alternatif bir arama mekanizması sağlamak üzere kullanılabilecek bir betik bloğu belirtir. Betik, eşleştirmek için kullanılan desenleri içermeli ve bir [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) nesnesi döndürüyor. Bu parametrenin Ayrıca `ScriptParameterSet` parametre kümesini tanımlayan benzersiz parametre olduğunu unutmayın. Windows PowerShell çalışma zamanı bu parametreyi gördüğünde yalnızca `ScriptParameterSet` parametre kümesine ait parametreleri kullanır.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

`SimpleMatch` Parametresi, cmdlet 'in sağlanan desenlerle açıkça eşleşip eşleşmeyeceğini belirten bir switch parametresidir. Kullanıcı parametresini komut satırında (`true`) belirttiğinde, cmdlet, sağlanan desenleri kullanır. Parametresi belirtilmemişse (`false`), cmdlet normal ifadeler kullanır. Bu parametre `false`için varsayılan değer.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

`CaseSensitive` Parametresi, büyük/küçük harfe duyarlı aramanın gerçekleştirilip gerçekleştirilmediğini belirten bir switch parametresidir. Kullanıcı parametresini komut satırında (`true`) belirttiğinde, cmdlet, desenleri karşılaştırırken büyük ve küçük harfli karakterleri denetler. Parametresi belirtilmemişse (`false`), cmdlet büyük harf ve küçük harf ayrımı yapmaz. Örneğin, "dosyam" ve "dosyam" her ikisi de pozitif isabet olarak döndürülür. Bu parametre `false`için varsayılan değer.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

`Exclude` Ve`Include` parametreleri, aramanın açıkça dışlandığı veya aramadan dahil edilen öğeleri belirler. Varsayılan olarak, cmdlet veri deposundaki tüm öğeleri arar. Bununla birlikte, cmdlet tarafından gerçekleştirilen aramayı sınırlamak için bu parametreler, aramaya dahil edilecek veya atlanacaktır öğeleri açıkça belirtmek için kullanılabilir.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>Parametre kümelerini bildirme

Bu cmdlet, veri erişiminde kullanılan iki`ScriptParameterSet` parametre `PatternParameterSet`kümesinin adları olarak iki parametre kümesi (ve varsayılan olan) kullanır. `PatternParameterSet`Varsayılan parametre kümesidir ve `Pattern` parametresi belirtildiğinde kullanılır. `ScriptParameterSet`Kullanıcı `Script` parametresi aracılığıyla alternatif bir arama mekanizması belirttiğinde kullanılır. Parametre kümeleri hakkında daha fazla bilgi için bkz. [bir cmdlet 'e parametre kümeleri ekleme](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Giriş Işleme yöntemlerini geçersiz kılma

Cmdlet 'ler [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı için bir veya daha fazla giriş işleme yöntemlerinden birini geçersiz kılmalıdır. Giriş işleme yöntemleri hakkında daha fazla bilgi için, bkz. [Ilk cmdlet dosyanızı oluşturma](./creating-a-cmdlet-without-parameters.md).

Bu cmdlet, başlangıçtaki bir derlenmiş normal ifadeler dizisi oluşturmak için [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemini geçersiz kılar. Bu, basit eşleştirme kullanmayan aramalar sırasında performansı artırır.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

Bu cmdlet Ayrıca, kullanıcının komut satırında yaptığı dize seçimlerini işlemek için [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodunu geçersiz kılar. Bir özel **matchString** yöntemi çağırarak, dize seçiminin sonuçlarını özel bir nesne biçiminde yazar.

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>Içeriğe erişme

Cmdlet 'nizin, verilere erişebilmeleri için Windows PowerShell yolu tarafından belirtilen sağlayıcıyı açması gerekir. Çalışma için [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) nesnesi sağlayıcıya erişim için kullanılır, ancak cmdlet 'in [System. Management. Automation. pscmdlet. ınvokeprovider *](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) özelliği sağlayıcıyı açmak için kullanılır. İçeriğe erişim, belirtilen sağlayıcı için [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) nesnesinin alınması yoluyla sağlanır.

Bu örnek Select-Str cmdlet 'i, taramanın içeriğini göstermek için [System. Management. Automation. Providerintrinsics. Content *](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) özelliğini kullanır. Daha sonra, gerekli Windows PowerShell yolunu geçirerek [System. Management. Automation. Contentcmdletproviderintrinsics. GetReader *](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) metodunu çağırabilir.

## <a name="code-sample"></a>Kod örneği

Aşağıdaki kod, bu Select-Str cmdlet 'inin bu sürümünün uygulamasını gösterir. Bu kodun cmdlet sınıfını, cmdlet tarafından kullanılan özel yöntemleri ve cmdlet 'i kaydetmek için kullanılan Windows PowerShell ek bileşeni kodunu içerdiğini unutmayın. Cmdlet 'i kaydetme hakkında daha fazla bilgi için bkz. [cmdlet oluşturma](#defining-the-cmdlet-class).

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>Cmdlet 'ı oluşturma

Bir cmdlet uygulandıktan sonra, Windows PowerShell ek bileşeni aracılığıyla Windows PowerShell ile kaydetmeniz gerekir. Cmdlet 'leri kaydetme hakkında daha fazla bilgi için bkz. [cmdlet 'leri, sağlayıcıları ve ana bilgisayar uygulamalarını kaydetme](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Cmdlet 'ı test etme

Cmdlet 'unuz Windows PowerShell ile kaydettirilirse, komut satırında çalıştırarak test edebilirsiniz. Örnek Select-Str cmdlet 'ini test etmek için aşağıdaki yordam kullanılabilir.

1. Windows PowerShell 'i başlatın ve Not dosyasını ".NET" ifadesiyle satır oluşumları için arayın. Yolun adı etrafında tırnak işaretlerinin yalnızca, yol birden fazla sözcükten oluşuyorsa gerekli olduğunu unutmayın.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    Aşağıdaki çıktı görüntülenir.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Notlar dosyasında, "Over" kelimesiyle ve ardından başka bir metinle birlikte satır oluşumları için arama yapın. `SimpleMatch` Parametresi varsayılan değerini kullanıyor `false`. `CaseSensitive` Parametresi olarak ayarlandığı için `false`arama büyük/küçük harfe duyarlıdır.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    Aşağıdaki çıktı görüntülenir.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. Desenler olarak normal bir ifade kullanarak notlar dosyasında arama yapın. Cmdlet 'i, parantez içine alınmış alfabetik karakterleri ve boş boşlukları arar.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    Aşağıdaki çıktı görüntülenir.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. "Parameter" sözcüğünün oluşumları için notlar dosyasında büyük/küçük harfe duyarlı arama gerçekleştirin.

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    Aşağıdaki çıktı görüntülenir.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. 0 ile 9 arasında sayısal değerlere sahip değişkenler için Windows PowerShell ile birlikte gelen değişken sağlayıcıda arama yapın.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    Aşağıdaki çıktı görüntülenir.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. "POS" dizesi için dosya SelectStrCommandSample.cs aramak üzere bir betik bloğu kullanın. Betik için **cmatch** işlevi, büyük/küçük harfe duyarsız bir model eşleşmesi gerçekleştirir.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    Aşağıdaki çıktı görüntülenir.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell cmdlet 'ı oluşturma](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Ilk cmdlet dosyanızı oluşturma](./creating-a-cmdlet-without-parameters.md)

[Sistemi değiştiren bir cmdlet oluşturma](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell sağlayıcınızı tasarlama](../prog-guide/designing-your-windows-powershell-provider.md)

[Windows PowerShell 'in çalışması](/previous-versions//ms714658(v=vs.85))

[Cmdlet 'Leri, sağlayıcıları ve ana bilgisayar uygulamalarını kaydetme](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK 'Sı](../windows-powershell-reference.md)
