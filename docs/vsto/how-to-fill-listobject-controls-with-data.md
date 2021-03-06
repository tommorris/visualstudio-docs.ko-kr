---
title: '방법: 데이터를 사용 하 여 채우기 ListObject 컨트롤'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9e255d4099a90173b9dbc7ff6fd7b2225d0622d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255706"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>방법: 데이터를 사용 하 여 채우기 ListObject 컨트롤
  신속하게 문서에 데이터를 추가하는 방법으로 데이터 바인딩을 사용할 수 있습니다. 목록 개체에 데이터를 바인딩한 후 해당 데이터를 표시하지만 더 이상 데이터 원본에 바인딩되지 않도록 목록 개체의 연결을 끊을 수 있습니다.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![비디오 링크](../vsto/media/playvideo.gif "비디오 링크") 관련된 비디오 데모를 참조 하세요. [방법: 만들기 SharePoint 목록에 연결 된 Excel 목록?](http://go.microsoft.com/fwlink/?LinkID=130263)합니다.  
  
### <a name="to-bind-data-to-a-listobject-control"></a>ListObject 컨트롤에 데이터를 바인딩하려면  
  
1.  클래스 수준에서 <xref:System.Data.DataTable> 을 만듭니다.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  `Startup` 클래스(문서 수준 프로젝트) 또는 `Sheet1` 클래스(응용 프로그램 수준 프로젝트)의 `ThisAddIn` 이벤트 처리기에서 샘플 열과 데이터를 추가합니다.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 메서드를 호출하고 표시할 순서대로 열 이름을 전달합니다. 목록 개체의 열 순서는 <xref:System.Data.DataTable>에 표시되는 순서와 다를 수 있습니다.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>데이터 원본에서 ListObject 컨트롤의 연결을 끊으려면  
  
1.  <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 의 `List1`메서드를 호출합니다.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compile-the-code"></a>코드 컴파일  
 이 코드 예제에서는 이 코드가 표시되는 워크시트에 <xref:Microsoft.Office.Tools.Excel.ListObject> 이라는 기존 `list1` 가 있는 것으로 간주합니다.  
  
## <a name="see-also"></a>참고자료  
 [Word 문서 및 런타임에 VSTO 추가 기능에서 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)   
 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [방법: 데이터를 지도 ListObject 열](../vsto/how-to-map-listobject-columns-to-data.md)   
 [확장 된 개체를 사용 하 여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 컨트롤](../vsto/listobject-control.md)   
 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [방법: 데이터베이스의 데이터로 워크시트 채우기](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  