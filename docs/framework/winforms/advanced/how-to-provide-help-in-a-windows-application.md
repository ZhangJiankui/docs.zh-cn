---
title: 如何：在 Windows 应用程序中提供帮助
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 19bf6a8de3f9ddd5babd149747df87c54b456aeb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211366"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>如何：在 Windows 应用程序中提供帮助

可以使用的<xref:System.Windows.Forms.HelpProvider>组件将附加到 Windows 窗体上的特定控件的帮助文件中的帮助主题。 帮助文件可以是 HTML、HTMLHelp 1.x 或更高版本的格式。

## <a name="provide-help"></a>提供的帮助信息

1. 在 Visual Studio 中，从**工具箱**，拖动<xref:System.Windows.Forms.HelpProvider>向窗体组件。

     该组件将位于 Windows 窗体设计器底部的栏中。

2. 在中**属性**窗口中，设置<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>属性设置为.chm、.col 或.htm 帮助文件。

3. 选择你在窗体中，然后在另一个控件**属性**窗口中，设置<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>属性。

     这是通过传递的字符串<xref:System.Windows.Forms.HelpProvider>组件到帮助文件用于请求相应的帮助主题。

4. 在中**属性**窗口中，将<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>属性的值的<xref:System.Windows.Forms.HelpNavigator>枚举。

     这可确定以何种方式将 **HelpKeyword** 属性传递给帮助系统。 下表显示可能的设置及其说明。

    |成员名称|描述|
    |-----------------|-----------------|
    |AssociateIndex|指定在指定 URL 中执行指定主题的索引。|
    |查找|指定显示指定 URL 的搜索页。|
    |索引|指定显示指定 URL 的索引。|
    |KeywordIndex|指定要搜索的关键字和要在指定 URL 中采取的操作。|
    |TableOfContents|指定显示 HTML 1.0 帮助文件的目录。|
    |主题|指定显示指定 URL 引用的主题。|

 在运行时，按 f1 键时控件 — 对于您设置**HelpKeyword**并**HelpNavigator**属性 — 具有焦点将打开与该关联的帮助文件<xref:System.Windows.Forms.HelpProvider>组件。

 目前， **HelpNamespace**属性支持以下三种格式的帮助文件：HTMLHelp 1.x、 HTMLHelp 2.0 中和 HTML。 因此，可以将 **HelpNamespace** 属性设置为 http:// 地址（如网页）。 如果此操作已完成，系统会打开默认浏览器，并显示作为定位标记的 **HelpKeyword** 属性中指定的字符串所对应的网页。 定位标记用于跳转到 HTML 页的特定部分。

> [!IMPORTANT]
> 一定要先仔细检查从客户端发来的所有信息，再在应用程序中使用这些信息。 恶意用户可能会尝试发送或注入可执行脚本、SQL 语句或其他代码。 显示用户的输入、将其存储在数据库中或使用它之前，请确定它没有包含可能的不安全信息。 通常的检查方法是在收到某个用户发来的输入后，使用正则表达式查找关键字，如“SCRIPT”。

此外可以使用<xref:System.Windows.Forms.HelpProvider>组件显示弹出帮助，即使将其配置为显示 Windows 窗体上控件的帮助文件。 有关详细信息，请参阅[如何：显示弹出帮助](how-to-display-pop-up-help.md)。

## <a name="see-also"></a>请参阅

- [如何：显示弹出帮助](how-to-display-pop-up-help.md)
- [使用工具提示的控件帮助](control-help-using-tooltips.md)
- [在 Windows 窗体中集成用户帮助](integrating-user-help-in-windows-forms.md)
- [Windows 窗体](../index.md)
