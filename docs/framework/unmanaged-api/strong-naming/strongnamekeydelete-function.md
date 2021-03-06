---
title: StrongNameKeyDelete 函数
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636741"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete 函数

删除指定的密钥容器。

此函数已弃用。 使用[iclrstrongname:: Strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)方法相反。

## <a name="syntax"></a>语法

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>参数

`wszKeyContainer`\
[in]若要删除的密钥容器的名称。

## <a name="return-value"></a>返回值

`true` 在成功完成;否则为`false`。

## <a name="remarks"></a>备注

使用[StrongNameKeyInstall](strongnamekeyinstall-function.md)函数导入容器的公钥/私钥对。

如果`StrongNameKeyDelete`函数不成功完成，则调用[StrongNameErrorInfo](strongnameerrorinfo-function.md)函数检索最后一个生成的错误。

## <a name="requirements"></a>要求

**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。

**标头：** StrongName.h

**库：** 包含为 MsCorEE.dll 中的资源

**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>请参阅

- [StrongNameKeyDelete 方法](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall 方法](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName 接口](../hosting/iclrstrongname-interface.md)
