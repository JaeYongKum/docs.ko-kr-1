---
title: "ICorDebugCode4 인터페이스"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugCode4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode4
helpviewer_keywords: ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bddbdb0986392bf1d9664e351bcc654ffa526257
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="87e32-102">ICorDebugCode4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="87e32-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="87e32-103">디버거를 지역 변수 및 함수에 인수를 열거 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="87e32-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87e32-104">메서드</span><span class="sxs-lookup"><span data-stu-id="87e32-104">Methods</span></span>  
  
|<span data-ttu-id="87e32-105">메서드</span><span class="sxs-lookup"><span data-stu-id="87e32-105">Method</span></span>|<span data-ttu-id="87e32-106">설명</span><span class="sxs-lookup"><span data-stu-id="87e32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87e32-107">EnumerateVariableHomes 메서드</span><span class="sxs-lookup"><span data-stu-id="87e32-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="87e32-108">함수에서 지역 변수 및 인수에는 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="87e32-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e32-109">설명</span><span class="sxs-lookup"><span data-stu-id="87e32-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87e32-110">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87e32-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e32-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="87e32-111">Requirements</span></span>  
 <span data-ttu-id="87e32-112">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="87e32-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e32-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87e32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87e32-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87e32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87e32-115">**.NET framework 버전:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e32-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87e32-116">See Also</span></span>  
    
    
 [<span data-ttu-id="87e32-117">ICorDebugCode3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="87e32-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="87e32-118">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="87e32-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)