---
title: "ICorProfilerInfo4::GetFunctionFromIP2 메서드"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2173326c5c67d1f4d3a8e28f84508fd6affb8299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="bfc75-102">ICorProfilerInfo4::GetFunctionFromIP2 메서드</span><span class="sxs-lookup"><span data-stu-id="bfc75-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="bfc75-103">관리 되는 코드의 명령 포인터는 함수의 JIT 다시 컴파일된 버전에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc75-104">구문</span><span class="sxs-lookup"><span data-stu-id="bfc75-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfc75-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bfc75-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="bfc75-106">[in] 관리 코드에서 명령 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="bfc75-107">[out] 함수 id입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="bfc75-108">[out] 함수의 JIT 다시 컴파일된 버전의 id입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfc75-109">설명</span><span class="sxs-lookup"><span data-stu-id="bfc75-109">Remarks</span></span>  
 <span data-ttu-id="bfc75-110">`GetFunctionFromIP2`유사한 `GetFunctionFromIP`제외 하 고 지정 된 IP 주소를 포함 하는 함수의 함수 ID가 아닌 JIT 다시 컴파일된 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfc75-111">`GetFunctionFromIP2`가비지 수집을 트리거할 수 있는 반면 `GetFunctionFromIP` 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="bfc75-112">자세한 내용은 참조 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfc75-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bfc75-113">Requirements</span></span>  
 <span data-ttu-id="bfc75-114">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bfc75-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfc75-115">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfc75-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfc75-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfc75-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfc75-117">**.NET framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfc75-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc75-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfc75-118">See Also</span></span>  
 [<span data-ttu-id="bfc75-119">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bfc75-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)