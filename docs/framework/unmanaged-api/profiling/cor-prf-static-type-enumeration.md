---
title: "COR_PRF_STATIC_TYPE 열거형"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_STATIC_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_STATIC_TYPE
helpviewer_keywords: COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 446967cc157962a1ec4a87193bbf84b1a356efa6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="50768-102">COR_PRF_STATIC_TYPE 열거형</span><span class="sxs-lookup"><span data-stu-id="50768-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="50768-103">필드가 정적인지 여부와 정적인 경우 필드에 적용될 정적 품질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50768-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="50768-104">비트 OR 연산을 사용 하 여 필드에 여러 개의 나타내기 위해이 값을 결합할 수 있습니다 다른 정적 품질을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50768-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50768-105">구문</span><span class="sxs-lookup"><span data-stu-id="50768-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="50768-106">멤버</span><span class="sxs-lookup"><span data-stu-id="50768-106">Members</span></span>  
  
|<span data-ttu-id="50768-107">멤버</span><span class="sxs-lookup"><span data-stu-id="50768-107">Member</span></span>|<span data-ttu-id="50768-108">설명</span><span class="sxs-lookup"><span data-stu-id="50768-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="50768-109">필드가 static이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="50768-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="50768-110">필드에는 응용 프로그램 도메인 static입니다.</span><span class="sxs-lookup"><span data-stu-id="50768-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="50768-111">필드는 스레드에 정적인입니다.</span><span class="sxs-lookup"><span data-stu-id="50768-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="50768-112">상황에 맞는 정적인의 필드가입니다.</span><span class="sxs-lookup"><span data-stu-id="50768-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="50768-113">필드는 상대 가상 주소 (RVA)-정적입니다.</span><span class="sxs-lookup"><span data-stu-id="50768-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50768-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="50768-114">Requirements</span></span>  
 <span data-ttu-id="50768-115">**플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="50768-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50768-116">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50768-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50768-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50768-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50768-118">**.NET framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50768-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50768-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50768-119">See Also</span></span>  
 [<span data-ttu-id="50768-120">프로 파일링 열거형</span><span class="sxs-lookup"><span data-stu-id="50768-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)