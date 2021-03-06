---
title: '방법: TileBrush의 바둑판 크기 설정'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: e1ba1a25281ffdd1cc00e0bed0efe4f8508780be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467837"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>방법: TileBrush의 바둑판 크기 설정
에 대 한 타일 크기를 설정 하는 방법을 보여주는이 예제는 <xref:System.Windows.Media.TileBrush>합니다. 기본적으로 <xref:System.Windows.Media.TileBrush> 는 사용자가 칠하고 있는 영역을 완전히 채우는 단일 타일을 생성 합니다. 설정 하 여이 동작을 재정의할 수는 <xref:System.Windows.Media.TileBrush.Viewport%2A> 고 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 속성입니다.  
  
 합니다 <xref:System.Windows.Media.TileBrush.Viewport%2A> 속성에 대 한 타일 크기를 지정 된 <xref:System.Windows.Media.TileBrush>합니다. 기본적으로 값을 <xref:System.Windows.Media.TileBrush.Viewport%2A> 속성은 그리는 영역의 크기를 기준으로 합니다. 수 있도록 합니다 <xref:System.Windows.Media.TileBrush.Viewport%2A> 속성이 절대 타일 크기를 지정 설정 합니다 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 속성을 <xref:System.Windows.Media.BrushMappingMode.Absolute>입니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 <xref:System.Windows.Media.ImageBrush>, 형식의 <xref:System.Windows.Media.TileBrush>, 타일을 사용 하 여 사각형을 그립니다. 이 예제에서는 각 타일을 출력 영역(사각형)의 50% x 50%로 설정합니다. 결과적으로 이미지 프로젝션 4개를 사용한 사각형이 그려집니다.  
  
 다음 그림에서는 예제가 생성하는 출력을 보여 줍니다.
  
 ![이미지 브러시를 사용한 바둑판식 배열 예제](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 다음 예제에서는 <xref:System.Windows.Media.ImageBrush>, 설정 해당 <xref:System.Windows.Media.TileBrush.Viewport%2A> 를 `0,0,25,25` 고 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 에 <xref:System.Windows.Media.BrushMappingMode.Absolute>, 하는 다른 사각형을 그리는 데 사용 합니다. 결과적으로 이 브러시는 너비 및 높이가 각각 25픽셀인 타일을 생성합니다.  
  
 다음 그림에서는 예제가 생성하는 출력을 보여 줍니다.  
  
 ![Viewport가 0,0,0.25,0.25인 바둑판 모양의 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 앞의 예제는 큰 샘플의 일부입니다. 전체 샘플을 참조 하세요 [ImageBrush 샘플](https://go.microsoft.com/fwlink/?LinkID=160005)합니다.  
  
 이 예제에서는 합니다 <xref:System.Windows.Media.ImageBrush> 클래스를 <xref:System.Windows.Media.TileBrush.Viewport%2A> 및 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 속성을 다른 동일 하 게 작동 <xref:System.Windows.Media.TileBrush> 개체, 즉,에 대 한 <xref:System.Windows.Media.DrawingBrush> 및 <xref:System.Windows.Media.VisualBrush>. 에 대 한 자세한 내용은 <xref:System.Windows.Media.ImageBrush> 집합과 <xref:System.Windows.Media.TileBrush> 개체를 참조 하세요 [이미지, 그림 및 시각적 표시로 그리기](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Windows.Media.TileBrush>  
 [이미지, 그림 및 시각적 표시로 그리기](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush로 다른 바둑판식 배열 패턴 만들기](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
