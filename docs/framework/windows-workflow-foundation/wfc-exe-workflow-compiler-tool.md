---
title: Wfc.exe (ワークフローコマンドラインコンパイラツール)
description: ワークフローコマンドラインコンパイラツールである wfc.exe について説明します。
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: cf89962014584adf098118044b063b38b29160b7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844738"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a><span data-ttu-id="ab9af-103">wfc.exe (ワークフローコマンドラインコンパイラツール)</span><span class="sxs-lookup"><span data-stu-id="ab9af-103">wfc.exe (Workflow Command-line Compiler Tool)</span></span>
> [!NOTE]
> <span data-ttu-id="ab9af-104">ここでは、廃止された型と名前空間について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab9af-104">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="ab9af-105">wfc.exe workflow コマンドラインコンパイラツールは、ファイル拡張子が *xoml* (古い) のワークフローマークアップファイルと連携します。</span><span class="sxs-lookup"><span data-stu-id="ab9af-105">The wfc.exe workflow command-line compiler tool works with old workflow markup files that have the file extension *.xoml* (obsoleted).</span></span>

## <a name="compilation-process"></a><span data-ttu-id="ab9af-106">コンパイルプロセス</span><span class="sxs-lookup"><span data-stu-id="ab9af-106">Compilation process</span></span>

<span data-ttu-id="ab9af-107">ワークフローのコンパイル時には、コンパイル手順として次のような処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-107">When workflows are compiled, the following procedures are performed as part of the compilation process:</span></span>

- <span data-ttu-id="ab9af-108">アクティビティ自身が設定したルールに基づいて、ワークフロー アクティビティの検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-108">Validation is performed to ensure that the workflow activities validate based on the rules that the activities have set for themselves.</span></span> <span data-ttu-id="ab9af-109">検証エラーが存在する場合、コンパイラはエラー リストを返します。</span><span class="sxs-lookup"><span data-stu-id="ab9af-109">If there are validation errors, the compiler returns a list of the errors.</span></span>  
- <span data-ttu-id="ab9af-110">コンパイラに入力されるマークアップ定義から部分クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-110">A partial class is generated from the markup definition that is input into the compiler.</span></span>  

- <span data-ttu-id="ab9af-111">アクティビティのランタイム実行を支援するためにコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-111">Code is generated to help with the run-time execution of the activities.</span></span> <span data-ttu-id="ab9af-112">子アクティビティの実行完了を親アクティビティが認識するために役立つイベント サブスクリプションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-112">Event subscriptions are generated, which help activities know when the activities they contain are finished executing.</span></span>  
- <span data-ttu-id="ab9af-113">マークアップ ファイルから生成された部分クラス、およびコード ファイルからの部分クラスは、.NET Framework C# または Visual Basic コンパイラに入力されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-113">The partial classes generated from the markup file and the partial classes from the code file are entered into the .NET Framework C# or Visual Basic compiler.</span></span> <span data-ttu-id="ab9af-114">この処理の出力は .NET アセンブリ WorkflowSample.dll です。</span><span class="sxs-lookup"><span data-stu-id="ab9af-114">The output of this process is the .NET assembly, WorkflowSample.dll.</span></span> <span data-ttu-id="ab9af-115">これを展開してワークフローを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-115">This can be deployed to run the workflow.</span></span>

### <a name="compiler-options"></a><span data-ttu-id="ab9af-116">コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ab9af-116">Compiler options</span></span>

<span data-ttu-id="ab9af-117">このセクションでは、wfc.exe ワークフローコマンドラインコンパイラのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ab9af-117">This section shows the options for the wfc.exe workflow command-line compiler.</span></span>

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a><span data-ttu-id="ab9af-118">注釈</span><span class="sxs-lookup"><span data-stu-id="ab9af-118">Remarks</span></span>
> [!NOTE]
> <span data-ttu-id="ab9af-119">ここでは、廃止された型と名前空間について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab9af-119">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="ab9af-120">承認された型の一覧は、通常、 *wfc.exe.config* ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-120">A list of authorized types is usually defined in the *wfc.exe.config* file.</span></span> <span data-ttu-id="ab9af-121">ワークフローコンパイルの検証フェーズでは、ワークフローソースドキュメントが承認された型の一覧に存在しない .NET Framework 型を直接参照している場合、ワークフローソースドキュメントは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-121">During the validation phase of workflow compilation, a workflow source document is rejected if it or the companion rules file directly references any .NET Framework types not present in a list of authorized types.</span></span> <span data-ttu-id="ab9af-122">承認された型の一覧は、、、、 `Assembly` `Namespace` `TypeName` および承認された { `True`&#124;`False` } インジケーターを各エントリが示す XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="ab9af-122">The list of authorized types is an XML document where each entry indicates an `Assembly`, a `Namespace`, a `TypeName`, and an Authorized {`True`&#124;`False`} indicator.</span></span> <span data-ttu-id="ab9af-123">`AuthorizedType` リスト内のエントリに対応します。</span><span class="sxs-lookup"><span data-stu-id="ab9af-123">`AuthorizedType` corresponds to an entry in the list.</span></span> <span data-ttu-id="ab9af-124">完全な名前空間を含めたり除外したりするために使用できるワイルドカード文字指定は許可されています。</span><span class="sxs-lookup"><span data-stu-id="ab9af-124">Wildcard character designations, which can be used to include or exclude complete namespaces, are allowed.</span></span> <span data-ttu-id="ab9af-125">たとえば、には、 `Type="System.*"` <xref:System> 子名前空間に含まれる型を含む、のすべての型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-125">For example, `Type="System.*"` includes all types in <xref:System>, including types contained in child namespaces.</span></span>
  
<span data-ttu-id="ab9af-126">承認された型の一覧の使用は、オプションによって制御され <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> `'/checktypes'` ます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-126">The use of a list of authorized types is controlled by the <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'`.</span></span>

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> <span data-ttu-id="ab9af-127">`Type="System.*"`型が存在する場合、コンパイルのためになどの他の意図しない型を含めることができ `Type="System.Configuration"` ます。</span><span class="sxs-lookup"><span data-stu-id="ab9af-127">When `Type="System.*"` type is present, it's possible to include other unintended types, such as `Type="System.Configuration"`, for compilation.</span></span> <span data-ttu-id="ab9af-128">注意し、それぞれを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab9af-128">You should be cautious and review each one.</span></span> <span data-ttu-id="ab9af-129">制限する必要がある型については、をに設定してください `Authorized` `False` 。</span><span class="sxs-lookup"><span data-stu-id="ab9af-129">For any type that should be restricted, be sure to set `Authorized` to `False`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab9af-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab9af-130">See also</span></span>

- [<span data-ttu-id="ab9af-131">AuthorizedType クラス</span><span class="sxs-lookup"><span data-stu-id="ab9af-131">AuthorizedType class</span></span>](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)