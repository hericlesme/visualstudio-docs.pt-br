---
title: 'Como: pesquisar texto em intervalos de planilhas programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2749834f459085b8d182b58f12a4c372f7493cba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Como localizar texto em intervalos de planilhas programaticamente
  O <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> método o <xref:Microsoft.Office.Interop.Excel.Range> objeto permite procurar texto dentro do intervalo. Esse texto também pode ser qualquer uma das cadeias de caracteres de erro que podem aparecer em uma célula de planilha como `#NULL!` ou `#VALUE!`. Para obter mais informações sobre cadeias de caracteres de erro, consulte [valores de erro de célula](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 O exemplo a seguir procura um intervalo nomeado `Fruits` e modifica a fonte para as células que contêm a palavra "maçãs". Esse procedimento também usa o <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método, que usa previamente definidas procurar configurações para repetir a pesquisa. Especifique a célula depois da qual pesquisar e o <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> método trata o restante.  
  
> [!NOTE]  
>  O <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> pesquisa do método encapsula volta para o início do intervalo de pesquisa depois que ele tenha atingido o final do intervalo. Seu código deve garantir que a pesquisa não quebra ao redor em um loop infinito. O procedimento de exemplo mostra uma maneira de lidar com isso usando o <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> propriedade.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer: usar o método Find em um suplemento do Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Para pesquisar texto em um intervalo de planilha  
  
1.  Declare variáveis para todo o intervalo, o primeiro intervalo encontrado e o intervalo de encontrado atual de controle.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Procurar a primeira correspondência, especificando todos os parâmetros, exceto a célula para pesquisar depois.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Continue a pesquisa enquanto houver correspondência.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Comparar o primeiro intervalo encontrado (`firstFind`) para **nada**. Se `firstFind` não contém nenhum valor, os repositórios de código fora do intervalo encontrado (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Sair do loop, se o endereço do intervalo encontrado corresponde ao endereço do primeiro intervalo encontrado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Defina a aparência do intervalo encontrado.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Execute outra pesquisa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 O exemplo a seguir mostra o método complete.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com intervalos](../vsto/working-with-ranges.md)   
 [Como: aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Como: referência a intervalos de planilhas em código programaticamente](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  