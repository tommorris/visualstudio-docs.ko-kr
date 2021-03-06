---
title: '방법: 프로그래밍 방식으로 문서에서 모든 메모 제거'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 005414fce7b7bc04c22b266f5f5f6d54a399a182
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674854"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>방법: 프로그래밍 방식으로 문서에서 모든 메모 제거
  사용 된 `DeleteAllComments` Microsoft Office Word 문서에서 모든 메모를 제거 하는 방법입니다.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>문서 수준 사용자 지정의 일부인 문서에서 모든 메모를 제거하려면  
  
1.  프로젝트에서 <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> 클래스의 `ThisDocument` 메서드를 호출합니다. 이 코드 예제를 사용하려면 `ThisDocument` 클래스에서 실행합니다.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>VSTO 추가 기능을 사용 하 여 문서에서 모든 메모를 제거 하려면  
  
1.  메모를 제거하려는 <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> 의 <xref:Microsoft.Office.Interop.Word.Document> 메서드를 호출합니다.  
  
     다음 코드 예제에서는 활성 문서에서 모든 메모를 제거합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>참고자료  
 [방법: 프로그래밍 방식으로 문서의 텍스트에 주석 추가](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [문서 호스트 항목](../vsto/document-host-item.md)  
  
  