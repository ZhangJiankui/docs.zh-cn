---
title: 创建自定义流控制活动
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: f457e6f8cefd7183ca20cb449adf1ac15d7bde79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647150"
---
# <a name="creating-custom-flow-control-activities"></a>创建自定义流控制活动
.NET Framework 包含多种流控制活动的作用类似抽象编程结构 (如<xref:System.Activities.Statements.Flowchart>) 或标准编程语句 (如<xref:System.Activities.Statements.If>)。 本主题讨论的示例项目之一的体系结构[非泛型 ForEach](./samples/non-generic-foreach.md)。  
  
## <a name="creating-the-custom-class"></a>创建自定义类  
 由于非泛型 ForEach 类将需要安排子活动，因此它需要从 <xref:System.Activities.NativeActivity> 派生，这是因为派生自 <xref:System.Workflow.Activities.CodeActivity> 的活动不具有此功能。  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 自定义类需要多个成员来存储活动所使用的数据，并提供用于执行该活动的子活动的功能。 这些成员包括：  
  
- `valueEnumerator`：非公共<xref:System.Activities.Variable%601>类型的<xref:System.Collections.IEnumerator>用于循环访问的项的集合。 此成员的类型为 <xref:System.Activities.Variable%601>，由于它是在活动内部而非自变量或公共属性内部使用的，因此如果该对象具有活动外部的来源，则将使用此成员。  
  
- `OnChildComplete`：公共<xref:System.Activities.CompletionCallback>执行每个子级完成执行后的属性。 此成员将定义为 CLR 属性，因为其值将不会随活动实例的不同而不同。  
  
- `Values`：输入用于迭代的子活动的集合。 此成员的类型为 <xref:System.Activities.InArgument%601>，因为该数据的来源位于活动外部，但集合的内容不应在活动执行期间发生更改。 如果该活动需要此功能以便在活动执行期间更改此集合的内容（例如，添加或移除活动），则此成员应已定义为 <xref:System.Activities.ActivityAction>，之后，每当访问该成员时，系统都会对其进行计算，以使更改对该活动可用。  
  
- `Body`：此成员定义中的每个项执行的活动`Values`集合。 此成员定义为 <xref:System.Activities.ActivityAction>，以便每当访问此成员时，系统都会对其进行计算。  
  
- `Execute`：此方法使用`InternalExecute`， `OnForEachComplete`，和`GetStateAndExecute`非公共成员来安排执行和分配 Body 成员中定义的子活动的完成处理程序。  
  
- `CacheMetadata`：此成员将向运行时提供其执行活动所需的信息。 默认情况下，一个活动的 `CacheMetadata` 方法会将该活动的所有公共成员告知运行时，但由于此活动对某些功能使用了私有成员，因此它需要告知运行时存在这些私有成员，以便运行时能注意到它们。 在此示例中，将重写 `CacheMetadata` 函数以便能访问私有 `valueEnumerator` 成员。 此成员还为该活动的值创建了一个自变量，以便这些值能在执行期间传入该活动中。
