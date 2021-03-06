---
title: 如何：获取变量的地址 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bc5776bc57096b88a71ff786915553ae9aa04b7b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635062"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>如何：获取变量的地址（C# 编程指南）

若要获取计算结果为固定变量的一元表达式的地址，请使用 address-of 运算符 `&`：  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 address-of 运算符只适用于变量。 如果变量是可移动变量，则可以使用[固定语句](../../../csharp/language-reference/keywords/fixed-statement.md)临时固定变量，再获取其地址。 有关可移动变量的详细信息，请参阅[固定变量和可移动变量](/dotnet/csharp/language-reference/language-specification/unsafe-code#fixed-and-moveable-variables)。 
  
 由你负责确保变量已初始化。 如果未初始化变量，编译器不会发出错误消息。  
  
 你也无法获取常量或值的地址。  
  
## <a name="example"></a>示例  
 在此示例中，已声明一个指向 `int` 和 `p` 的指针，并向其赋予了整型变量 `number` 的地址。 向 `*p` 赋值后导致初始化变量 `number`。 如果向此赋值语句添加注释，将删除变量 `number` 的初始化，但不会产生任何编译时错误。  

> [!NOTE]
> 使用 [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) 编译器选项编译此示例。
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [指针类型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [类型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed 语句](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
