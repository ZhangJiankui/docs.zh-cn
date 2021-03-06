---
title: -win32res（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 4026fcbd7dc2ef29c1e7ee01a0f37b3ff471b187
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322369"
---
# <a name="-win32res-c-compiler-options"></a>-win32res（C# 编译器选项）
-win32res 选项会在输出文件中插入 Win32 资源。  
  
## <a name="syntax"></a>语法  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>自变量  
 `filename`  
 想向输出文件添加的资源文件。  
  
## <a name="remarks"></a>备注  
 Win32 资源文件可以用[资源编译器](../../language-reference/compiler-options/resource-compiler-option.md)创建。 在编译 Visual C++ 程序时会调用资源编译器；.res 文件是从 .rc 文件创建的。  
  
 Win32 资源可以包含版本或位图（图标）信息，这些信息有助于在文件资源管理器中标识您的应用程序。 如果不指定 -win32res，编译器将根据程序集版本生成版本信息。  
  
 请参阅 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)（引用）或 [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)（附加）.NET Framework 资源文件。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1. 打开项目的“属性”页。  
  
2. 单击“应用程序”属性页。  
  
3. 单击“资源文件”按钮，然后使用组合框选择一个文件。  
  
## <a name="example"></a>示例  
 编译 `in.cs` 并附加 Win32 资源文件 `rf.res` 以生成 `in.exe`：  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>请参阅

- [C# 编译器选项](../../../csharp/language-reference/compiler-options/index.md)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
