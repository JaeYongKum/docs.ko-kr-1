---
title: ICeeGen::GetSectionBlock 메서드
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5da2936a46dcf3d8f69acc3367db64712165b0cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444069"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock 메서드
코드 베이스의 섹션 블록을 가져옵니다.  
  
 이 메서드는 사용 되지 않으며 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a>매개 변수  
 `section`  
 [in] 코드 베이스의 블록 검색 하려는 섹션입니다.  
  
 `len`  
 [in] 검색할 블록의 길이입니다.  
  
 `align`  
 [in] 블록의 첫 번째 바이트를 정렬 하는 데 사용할 섹션의 시작을 기준으로 바이트입니다. 이 섹션 내에서 블록의 위치입니다.  
  
 `ppBytes`  
 [out] 검색 된 블록의 주소를 받는 위치에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  
 호출 `GetSectionBlock` 다른 방법으로 처리 되지 않는 섹션 특별 한 요구 사항이 있는 경우에 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:** 참조 [시스템 요구 사항](../../../../docs/framework/get-started/system-requirements.md)합니다.  
  
 **헤더:** Cor.h  
  
 **라이브러리:** MsCorEE.dll에서 리소스로 사용  
  
 **.NET framework 버전:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목  
 [ICeeGen 인터페이스](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
