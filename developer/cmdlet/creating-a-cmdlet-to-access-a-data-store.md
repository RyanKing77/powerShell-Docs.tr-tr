---
title: Data Store erişmek için bir Cmdlet oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 6171f96d66d0b2aa0fd9cb2a939768287c4bcb87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849185"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Bir Veri Deposuna Erişmek İçin Cmdlet Oluşturma

Bu bölümde, bir Windows PowerShell sağlayıcısı yoluyla depolanan verilere erişen bir cmdlet oluşturmayı açıklar. Bu tür bir cmdlet Windows PowerShell çalışma zamanı Windows PowerShell sağlayıcısı altyapısını kullanır ve bu nedenle, cmdlet sınıfı öğesinden türetilmelidir [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfı.

Burada açıklanan seçin Str cmdlet'i, bulun ve dizeleri bir dosya veya nesne seçin. Dizeyi tanımlamak için kullanılan desenleri ile açıkça belirtilmesi `Path` parametre cmdlet veya örtük olarak aracılığıyla `Script` parametresi.

Cmdlet, türetilen herhangi bir Windows PowerShell sağlayıcısı kullanmak üzere tasarlanmış [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Örneğin, cmdlet, dosya sistemi sağlayıcısı veya Windows PowerShell tarafından sağlanan değişken sağlayıcı belirtebilirsiniz. Daha fazla bilgi aboutWindows için PowerShell sağlayıcıları, bkz: [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](../prog-guide/designing-your-windows-powershell-provider.md).

Bu bölümdeki konular şunlardır:

- [Cmdlet'i sınıf tanımlama](#Defining-the-Cmdlet-Class)

- [Veri erişimi için parametreleri tanımlama](#Declaring-the-Path-Parameter)

- [Geçersiz kılma yöntemleri işleme giriş](#Overriding-Input-Processing-Methods)

- [İçerik erişme](#Accessing-Content)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme](#Declaring-Search-Support-Parameters)

- [Cmdlet oluşturma](#Building-the-Cmdlet)

- [Sınama cmdlet'i](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Cmdlet'i sınıf tanımlama

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Bu cmdlet, burada seçilen fiil adı "Seçin", bu nedenle belirli dizeleri tanımlanan algılar [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) sınıfı. Cmdlet dizeleri karıncaların isim adı "Dizesi" kullanılır. Cmdlet fiil ve isim adı cmdlet'i sınıfının adını yansıtılır bildiriminde unutmayın. Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Bu cmdlet için .NET sınıf öğesinden türetilmelidir [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfı, çünkü Windows PowerShell sağlayıcısını kullanıma sunmak için Windows PowerShell çalışma zamanı tarafından gereken desteği sağlar Altyapı. Bu cmdlet ayrıca yapar Not gibi .NET Framework normal ifade sınıfları, kullanın [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).

Bu seçim Str cmdlet için sınıf tanımının kodudur.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Bu cmdlet varsayılan parametre ekleyerek ayarlayın tanımlar `DefaultParameterSetName` anahtar sözcüğü bir sınıf bildirimine özniteliği. Varsayılan parametre kümesi `PatternParameterSet` kullanıldığında `Script` parametresi belirtilmedi. Bu parametre kümesi hakkında daha fazla bilgi için bkz. `Pattern` ve `Script` aşağıdaki bölümdeki parametresi tartışma.

## <a name="defining-parameters-for-data-access"></a>Veri erişimi için parametreleri tanımlama

Bu cmdlet, erişim ve depolanan verileri incelemek kullanıcının olanak tanıyan çeşitli parametreleri tanımlar. Bu parametreler içeren bir `Path` veri deposunun konumu belirten bir parametre bir `Pattern` parametresi aramada kullanılacak desenini belirtir ve arama nasıl gerçekleştirildiğini destekleyen çeşitli diğer parametreleri.

> [!NOTE]
> Parametreleri tanımlama temelleri hakkında daha fazla bilgi için bkz: [parametreler, işlem komut satırı girişi ekleme](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Path parametresi bildirme

Veri deposu bulmak için bu cmdlet bir Windows PowerShell yolu veri deposuna erişim için tasarlanan Windows PowerShell sağlayıcısı tanımlamak için kullanmanız gerekir. Bu nedenle, tanımladığı bir `Path` sağlayıcının konumu belirtmek için türü dize dizisi parametresi.

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

Bu parametre için iki farklı parametre kümesine ait olan ve bir diğer ad olduğunu unutmayın.

İki [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) öznitelikleri bildirme `Path` parametresi ait `ScriptParameterSet` ve `PatternParameterSet`. Parametre kümeleri hakkında daha fazla bilgi için bkz. [bir cmdlet'e parametre ayarlar ekleme](./adding-parameter-sets-to-a-cmdlet.md).

[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) öznitelik bildirir bir `PSPath` için diğer ad `Path` parametresi. Bu diğer ad bildirmek için Windows PowerShell sağlayıcıları erişen diğer cmdlet'ler ile tutarlılık önemle önerilir. Daha fazla bilgi aboutWindows için PowerShell yolları, bkz: "PowerShell yolu kavramlar" [nasıl Windows PowerShell çalışır](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="declaring-the-pattern-parameter"></a>Desen parametresini bildirme

Aranacak desenleri belirtmek için bu cmdlet'i bildirir. bir `Pattern` , dizelerden oluşan bir dizi parametre. Herhangi bir kalıpla veri deposunda bulunduğunda, pozitif bir sonuç döndürülür. Bu düzenleri, derlenmiş normal ifadeler bir dizi veya joker karakter düzenleri değişmez değer aramaları için kullanılan bir dizi içine derlenebilir unutmayın.

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

Bu parametre belirtildiğinde cmdlet varsayılan parametre kümesi kullanır. `PatternParameterSet`. Bu durumda, dizeleri seçmek için burada belirtilen desenleri cmdlet'ini kullanır. Buna karşılık, `Script` parametresi de kullanılabilen desenleri içeren bir betik sağlamak için. `Script` Ve `Pattern` parametreleri tanımlayan iki ayrı parametre kümesi için karşılıklı olarak birbirini dışlar.

### <a name="declaring-search-support-parameters"></a>Arama desteği parametreleri bildirme

Bu cmdlet, cmdlet arama özellikleri değiştirmek için kullanılan aşağıdaki Destek parametreleri tanımlar.

`Script` Parametresi bir alternatif arama mekanizması cmdlet'i için sağlamak için kullanılan bir betik bloğu belirtir. Betik eşleştirmek için kullanılan desenleri içerir ve dönüş bir [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) nesne. Bu parametre tanımlayan benzersiz bir parametre olduğunu unutmayın `ScriptParameterSet` parametre kümesi. Windows PowerShell çalışma zamanı bu parametreyi gördüğünde ait parametreleri kullanır. `ScriptParameterSet` parametre kümesi.

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

`SimpleMatch` Parametredir cmdlet bunlar verdiği düzenlerine açıkça uygun olup olmadığını belirten bir anahtar. Ne zaman, kullanıcının belirttiği komut satırı parametresi (`true`), bunlar verdiği desenleri cmdlet'ini kullanır. Parametre belirtilmezse, (`false`), normal ifadeler cmdlet'ini kullanır. Bu parametre için varsayılan değer `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

`CaseSensitive` Parametredir büyük küçük harfe duyarlı bir arama yapılıp yapılmayacağını belirten bir anahtar. Ne zaman, kullanıcının belirttiği komut satırı parametresi (`true`), cmdlet için büyük harf denetler ve küçük karşılaştırılırken karakter desen. Parametre belirtilmezse, (`false`), cmdlet büyük ve küçük harfler arasında ayrım yapmaz. Örneğin "MyFile" ve "myfile" her ikisi de pozitif isabet sayısı döndürülür. Bu parametre için varsayılan değer `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

`Exclude` Ve `Include` açıkça dışında tutulan veya aramaya dahil öğeleri parametreleri tanımlayın. Varsayılan olarak, cmdlet, veri deposunda tüm öğeleri arar. Ancak, cmdlet tarafından gerçekleştirilen arama sınırlamak için bu parametreleri açıkça aramaya dahil edilecek öğeleri belirtmek için kullanılabilir veya atlanmış.

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

### <a name="declaring-parameter-sets"></a>Parametre kümeleri bildirme

Bu cmdlet, iki parametre kümeleri kullanır (`ScriptParameterSet` ve `PatternParameterSet`, varsayılan olan) olarak kullanılan veri erişimi, iki parametre kümesi adları. `PatternParameterSet` Varsayılan parametre kümesi ve kullanıldığında `Pattern` parametre belirtildi. `ScriptParameterSet` Alternatif arama bir mekanizma aracılığıyla kullanıcının belirttiği kullanıldığında `Script` parametresi. Parametre kümeleri hakkında daha fazla bilgi için bkz. [bir cmdlet'e parametre ayarlar ekleme](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Geçersiz kılma yöntemleri işleme giriş

Cmdlet'leri geçersiz kılması gerekir bir veya daha fazla işleme için yöntemleri giriş [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı. Giriş işleme yöntemleri hakkında daha fazla bilgi için bkz. [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

Bu cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) derlenmiş normal ifadeler başlatma sırasında bir dizi oluşturmak için yöntemi. Bu basit eşleştirme kullanmayan arama sırasında performansı artırır.

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

Bu cmdlet ayrıca geçersiz kılar [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) komut satırında kullanıcının yaptığı dize seçimleri işlemek için yöntemi. Özel bir nesne biçiminde dize seçim sonuçlarının, özel bir çağırarak Yazar **MatchString** yöntemi.

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

      // Check if the path represens one of the items to be
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
            // Add the block(line) that did notmatch to the
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

## <a name="accessing-content"></a>İçerik erişme

Cmdlet'inize verilere erişebilmesi için Windows PowerShell yoluyla belirtilen sağlayıcı açmanız gerekir. [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) nesne sağlayıcıya erişim için kullanılan çalışma için while [System.Management.Automation.Pscmdlet.Invokeprovider*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) özelliği cmdlet, sağlayıcı açmak için kullanılır. İçeriğe erişimi alınmasını tarafından sağlanan [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) sağlayıcısı nesne açılır.

Bu örnek seçin Str cmdlet'ini kullanır [System.Management.Automation.Providerintrinsics.Content*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) tarama için içerik kullanıma sunmak için özellik. Ardından çağırabilirsiniz [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) yöntemini gerekli Windows PowerShell yolu.

## <a name="code-sample"></a>Kod örneği

Aşağıdaki kod bu sürümü bu seçin Str cmdlet uygulamasını gösterir. Bu kod cmdlet'i sınıf, cmdlet tarafından kullanılan özel yöntemleri ve cmdlet kaydetmek için kullanılan Windows PowerShell ek bileşenini kod içerdiğini unutmayın. Cmdlet kaydetme hakkında daha fazla bilgi için bkz. [Cmdlet oluşturmaya](#Building-the-Cmdlet).

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
    /// a PSPath alias to provide consistancy with other cmdlets that use
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
    /// is perfored.
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

          // Check if the path represens one of the items to be
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
                // Add the block(line) that did notmatch to the
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
    /// specified, and not on the exclude list if the explude list was specified.
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
    /// Specifiy the description of the PowerShell snap-in.
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

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz. Aşağıdaki yordam, örnek seçin Str cmdlet test etmek için kullanılabilir.

1. Windows PowerShell'i başlatın ve ".NET" ifadesiyle satırları oluşumlarını notları dosyada arayın. Yol birden fazla sözcük oluşuyorsa yolun adını tırnak gerekli olduğunu unutmayın.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    Aşağıdaki çıktı görünür.

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

2. Herhangi bir metin tarafından izlenen "içinde" sözcüğünü içeren satırları oluşumlarını notları dosyada arayın. `SimpleMatch` Parametrenin varsayılan değerini kullanarak `false`. Arama büyük/küçük harfe duyarsızdır çünkü `CaseSensitive` parametrenin ayarlanmış `false`.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    Aşağıdaki çıktı görünür.

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

3. Bir normal ifade deseni olarak kullanarak notları dosyada arayın. Cmdlet alfabetik karakterler ve boşluklar parantez içine alınmış arar.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    Aşağıdaki çıktı görünür.

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

4. "Parametre" sözcüğü oluşumlarını için Notlar dosyasının büyük küçük harfe duyarlı bir arama gerçekleştirin.

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    Aşağıdaki çıktı görünür.

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

5. Arama değişken sağlayıcısı, 0-9 arası sayısal değerlere sahip değişkenler için Windows PowerShell ile birlikte gelir.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    Aşağıdaki çıktı görünür.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Bir betik bloğu, "Pos" dizesini SelectStrCommandSample.cs dosyayı aramak için kullanın. **Cmatch** betik büyük küçük harf duyarsız Desen eşleştirmesi gerçekleştirir için işlev.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    Aşağıdaki çıktı görünür.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i oluşturma](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[İlk Cmdlet'inize oluşturma](./creating-a-cmdlet-without-parameters.md)

[Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell sağlayıcınız tasarlama](../prog-guide/designing-your-windows-powershell-provider.md)

[Windows PowerShell nasıl çalışır?](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
