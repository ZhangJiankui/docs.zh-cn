---
title: ICorDebugManagedCallback::Break 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 621c5b1e32a1a21c2b0b883249c3b65fadceb5f2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632352"
---
# <a name="icordebugmanagedcallbackbreak-method"></a>ICorDebugManagedCallback::Break 方法

通知调试器时<xref:System.Reflection.Emit.OpCodes.Break>执行代码流中的指令。

## <a name="syntax"></a>语法

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a>参数

`pAppDomain`\
[in]指向一个 ICorDebugAppDomain 对象，表示包含 break 指令的应用程序域的指针。

`thread`\
[in]指向表示，包含 break 指令的线程的 ICorDebugThread 对象的指针。

## <a name="requirements"></a>要求

**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。

**标头：** CorDebug.idl、 CorDebug.h

**库：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>请参阅

- [ICorDebugManagedCallback 接口](icordebugmanagedcallback-interface.md)
