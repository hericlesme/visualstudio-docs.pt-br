---
title: 'Como: abrir programaticamente os arquivos de texto como pastas de trabalho | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cafe64ce693972bd9c254a6bdfc1dcbf70f004c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Como abrir arquivos de texto como pastas de trabalho programaticamente
  Você pode abrir um arquivo de texto como uma pasta de trabalho. Você deve passar o nome do arquivo de texto que você deseja abrir. Você pode especificar vários parâmetros opcionais, como o número da linha para iniciar analisar e o formato de coluna de dados no arquivo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer os seguintes componentes:  
  
-   Um arquivo de texto delimitado por vírgula chamado `Test.txt` que contém pelo menos três linhas de texto.  
  
-   O arquivo de texto `Test.txt` a ser armazenado na unidade C.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Como: programaticamente abrir pastas de trabalho](../vsto/how-to-programmatically-open-workbooks.md)   
 [Como: criar programaticamente novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Como: programaticamente salvar pastas de trabalho](../vsto/how-to-programmatically-save-workbooks.md)   
 [Como: programaticamente fechar pastas de trabalho](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  