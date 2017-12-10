---
title: "ICorProfilerFunctionControl 인터페이스"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl
helpviewer_keywords: ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09a0a839c9cd69c7926c19cceffc56ee928f2f02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="4673e-102">ICorProfilerFunctionControl 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4673e-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="4673e-103">코드 프로파일러가 CLR(공용 언어 런타임)과 통신하여 특정 메서드를 다시 컴파일할 때 JIT 컴파일러가 코드를 생성하는 방법을 제어할 수 있도록 하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4673e-104">메서드</span><span class="sxs-lookup"><span data-stu-id="4673e-104">Methods</span></span>  
  
|<span data-ttu-id="4673e-105">메서드</span><span class="sxs-lookup"><span data-stu-id="4673e-105">Method</span></span>|<span data-ttu-id="4673e-106">설명</span><span class="sxs-lookup"><span data-stu-id="4673e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4673e-107">SetCodegenFlags 메서드</span><span class="sxs-lookup"><span data-stu-id="4673e-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="4673e-108">하나 이상의 플래그 설정 된 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) 다시 컴파일된 함수는-just-in-time (JIT)에 대 한 코드 생성을 제어 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="4673e-109">SetILFunctionBody 메서드</span><span class="sxs-lookup"><span data-stu-id="4673e-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="4673e-110">메서드의 공용 중간 언어(CIL) 본문을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="4673e-111">SetILInstrumentedCodeMap 메서드</span><span class="sxs-lookup"><span data-stu-id="4673e-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="4673e-112">지정한 CIL(공용 중간 언어) 맵 엔트리를 사용하여 지정된 함수에 대한 코드 맵을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4673e-113">설명</span><span class="sxs-lookup"><span data-stu-id="4673e-113">Remarks</span></span>  
 <span data-ttu-id="4673e-114">`ICorProfilerFunctionControl` 인터페이스는 다시 컴파일된 단일 함수에 대한 코드 생성을 제어하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="4673e-115">프로파일러를 통해이 인터페이스의 인스턴스를 가져옵니다는 [icorprofilercallback4:: Getrejitparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) 콜백 합니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="4673e-116">`ICorProfilerFunctionControl`의 각 인스턴스가 단일 함수의 모든 인스턴스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4673e-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4673e-117">Requirements</span></span>  
 <span data-ttu-id="4673e-118">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4673e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4673e-119">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4673e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4673e-120">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4673e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4673e-121">**.NET framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4673e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4673e-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4673e-122">See Also</span></span>  
 [<span data-ttu-id="4673e-123">ICorProfilerInfo4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4673e-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="4673e-124">프로 파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4673e-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="4673e-125">EnumJITedFunctions2 메서드</span><span class="sxs-lookup"><span data-stu-id="4673e-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)