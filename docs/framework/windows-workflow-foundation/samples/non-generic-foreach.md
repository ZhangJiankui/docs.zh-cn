---
title: 非泛型 ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 46db1d455bcbdd28e02d3cddfe0c9248b4abd91c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620845"
---
# <a name="non-generic-foreach"></a>非泛型 ForEach
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 的工具箱中附带了一组控制流活动，其中包括可用来循环访问 <xref:System.Activities.Statements.ForEach%601> 集合的 <xref:System.Collections.Generic.IEnumerable%601>。  
  
 <xref:System.Activities.Statements.ForEach%601> 要求其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 属性为 <xref:System.Collections.Generic.IEnumerable%601> 类型。 这将阻止用户循环访问实现 <xref:System.Collections.Generic.IEnumerable%601> 接口（例如，<xref:System.Collections.ArrayList>）的数据结构。 非泛型版本的 <xref:System.Activities.Statements.ForEach%601> 没有这一需求，不过与此对应的代价是，需要更复杂的运行时来确保集合中的值类型的兼容性。  
  
 此示例演示如何实现非泛型的 <xref:System.Activities.Statements.ForEach%601> 活动及其设计器。 此活动可用于循环访问 <xref:System.Collections.ArrayList>。  
  
## <a name="foreach-activity"></a>ForEach 活动  
 C#/VB `foreach` 语句枚举集合的元素，对集合中的每个元素执行嵌入语句。 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 的 `foreach` 等效活动为 <xref:System.Activities.Statements.ForEach%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。 <xref:System.Activities.Statements.ForEach%601> 活动包含一个值列表和一个主体。 在运行时，将循环访问此列表，并对列表中的每个值执行主体。  
  
 对于大多数情况，此活动的泛型版本应为首选解决方案，因为它涵盖了应使用此活动的大多数方案，并且提供编译时类型检查。 非泛型版本可用于循环访问实现非泛型 <xref:System.Collections.IEnumerable> 接口的类型。  
  
## <a name="class-definition"></a>类定义  
 下面的代码示例显示非泛型 `ForEach` 活动的定义。  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Body（可选）  
 <xref:System.Activities.ActivityAction> 类型的 <xref:System.Object>，将对集合中的每个元素执行它。 每个个体元素都通过其 `Argument` 属性传递到 Body。  
  
 Values（可选）  
 循环访问的元素集合。 在运行时确保所有集合元素为兼容类型。  
  
## <a name="example-of-using-foreach"></a>使用 ForEach 的示例  
 下面的代码演示如何在应用程序中使用 ForEach 活动。  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|条件|消息|严重性|异常类型|  
|---------------|-------------|--------------|--------------------|  
|Values 为 `null`|未提供必需活动自变量“Values”的值。|Error|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>ForEachT 设计器  
 此示例的活动设计器的外观与为内置 <xref:System.Activities.Statements.ForEach%601> 活动提供的设计器的外观相似。 在设计器将显示在工具箱中**示例**，**非泛型活动**类别。 名为设计器**ForEachWithBodyFactory**在工具箱中，因为该活动公开<xref:System.Activities.Presentation.IActivityTemplateFactory>在工具箱中，这将创建该活动使用正确配置<xref:System.Activities.ActivityAction>。  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a>运行此示例  
  
1. 将您选择的项目设置为解决方案的启动项目：  
  
    1. **Codetestclient**演示如何使用活动使用代码。  
  
    2. **Designertestclient**演示如何使用设计器中的活动。  
  
2. 生成并运行该项目。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
