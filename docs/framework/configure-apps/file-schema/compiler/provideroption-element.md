---
title: <providerOption> 要素
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 9374fbaf7ceb61e5b72335417d32a08525477e0d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149635"
---
# <a name="provideroption-element"></a>\<providerOption> 要素

言語プロバイダーのコンパイラバージョン属性を指定します。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a>構文  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須の属性です。<br /><br /> オプションの名前を指定します。たとえば、"CompilerVersion" のようになります。|  
|`value`|必須の属性です。<br /><br /> オプションの値を指定します。たとえば、"v 3.5" のようになります。|  
  
### <a name="child-elements"></a>子要素  

 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration> 要素](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom> 要素](system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|  
|[\<compilers> 要素](compilers-element.md)|コンパイラ構成要素のコンテナー。0個以上の要素が含まれてい `<compiler>` ます。|  
|[\<compiler> 要素](compiler-element.md)|言語プロバイダーのコンパイラ構成属性を指定します。|  
  
## <a name="remarks"></a>解説  

 .NET Framework バージョン3.5 では、Code Document Object Model (CodeDOM) コードプロバイダーは、要素を使用してプロバイダー固有のオプションをサポートでき `<providerOption>` ます。  
  
 .NET Framework 3.5 には、更新された .NET Framework 2.0 アセンブリが含まれており、新しい型を含む新しいバージョンの3.5 アセンブリが用意されています。 Microsoft C# および Visual Basic コードプロバイダーは .NET Framework 2.0 アセンブリに含まれていますが、バージョン3.5 コンパイラをサポートするように更新されています。 既定では、更新されたコードプロバイダーはバージョン2.0 コンパイラのコードを生成します。 要素を使用し `<providerOption>` て、ターゲットコンパイラのバージョンを3.5 に変更できます。 これを行うには、属性に "CompilerVersion" を指定し、 `name` 属性に「v 3.5」を指定し `value` ます。 バージョン番号の前には、小文字の "v" を使用する必要があります。  
  
 `<providerOption>`.NET Framework 2.0 Machine.config またはルート Web.config ファイルに要素を追加することで、バージョン指定をグローバルにすることができます。 Machine.config ファイルで既定のコンパイラのバージョンを3.5 に更新した場合は、アプリケーション構成ファイルの要素を使用して、アプリケーションごとに2.0 に戻すことができ `<providerOption>` ます。  
  
 CodeDOM コードプロバイダーの実装者は、型のパラメーターを受け取るコンストラクターを指定することによって、カスタムオプションを処理でき `providerOptions` <xref:System.Collections.Generic.IDictionary%602> ます。  
  
## <a name="example"></a>例  

 次の例は、C# コードプロバイダーのバージョン3.5 を使用するように指定する方法を示しています。  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [構成ファイル スキーマ](../index.md)
- [\<compilers> 要素](compilers-element.md)
- [完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [compilation の compilers の compiler 要素 (ASP.NET 設定スキーマ)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
