---
title: 如何：使用设计器将快捷菜单附加到 TreeNode
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 9be633d14429bc2ceda1f0db2ff09252d55d5dd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337443"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>如何：使用设计器将快捷菜单附加到 TreeNode
Windows 窗体<xref:System.Windows.Forms.TreeView>控件显示的节点，类似于文件和 Windows 操作系统中的 Windows 资源管理器功能的左窗格中显示的文件夹层次结构。 通过设置<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>属性，您可以区分上下文的操作向用户提供他们右键单击时<xref:System.Windows.Forms.TreeView>控件。 通过将相关联<xref:System.Windows.Forms.ContextMenuStrip>组件与单个<xref:System.Windows.Forms.TreeNode>项，可以添加到快捷菜单上功能的自定义的级别应用<xref:System.Windows.Forms.TreeView>控件。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>要在设计时与树节点关联的快捷菜单  
  
1. 添加<xref:System.Windows.Forms.TreeView>控制对窗体中，以及如何将节点<xref:System.Windows.Forms.TreeView>根据需要。 有关详细信息，请参阅[如何：添加和删除节点与 Windows 窗体 TreeView 控件](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)。  
  
2. 添加<xref:System.Windows.Forms.ContextMenuStrip>组件向窗体，然后将菜单项添加到表示你想要在运行时提供节点级别操作的快捷菜单。 有关详细信息，请参阅[如何：向 ContextMenuStrip 添加菜单项](how-to-add-menu-items-to-a-contextmenustrip.md)。  
  
3. 重新打开**TreeNodeEditor**对话框<xref:System.Windows.Forms.TreeView>控件中，选择节点以编辑，并设置其<xref:System.Windows.Forms.ContextMenuStrip>属性设置为您添加的快捷菜单。  
  
4. 当设置此属性时，右键单击节点时，将显示的快捷菜单。  
  
     此外，你将想要编写代码来处理<xref:System.Windows.Forms.ToolStripItem.Click>这些菜单项的事件。  
  
## <a name="see-also"></a>请参阅

- [TreeView 控件](treeview-control-windows-forms.md)
- [TreeView 控件概述](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip 控件](contextmenustrip-control.md)
