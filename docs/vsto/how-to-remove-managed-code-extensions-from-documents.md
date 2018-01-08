---
title: "Como: remover extensões de código gerenciado de documentos | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 77325f725edcec41d71e5af38572f05e59c86198
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Como remover extensões de código gerenciado de documentos
  Programaticamente, você pode remover o assembly de personalização de um documento ou a pasta de trabalho que faz parte de uma personalização no nível do documento para o Microsoft Office Word ou o Microsoft Office Excel. Os usuários podem, em seguida, abra os documentos e exibir o conteúdo, mas nenhuma interface do usuário personalizada (UI) adicionar aos documentos não aparecerá, e seu código não será executado.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Você pode remover o assembly de personalização usando um dos métodos RemoveCustomization fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Método usado depende se você deseja remover a personalização em tempo de execução (ou seja, executando código na personalização enquanto o Word documento ou pasta de trabalho do Excel é aberta), ou se você deseja remover a personalização de um documento fechado ou um documento que i s em um servidor que não tenha o Microsoft Office instalado.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: anexar ou desanexar um Assembly do VSTO de um documento do Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>Para remover o assembly de personalização em tempo de execução  
  
1.  No seu código de personalização, chame o <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> método (para o Word) ou o <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> método (para Excel). Esse método deve ser chamado somente depois que a personalização não é mais necessário.  
  
     Onde você chamar esse método em seu código depende de como a personalização é usada. Por exemplo, se os clientes usam os recursos de personalização até que estejam prontos para enviar um documento para outros clientes que precisam apenas o documento em si (e não a personalização), você pode fornecer algumas interfaces do usuário que chama RemoveCustomization quando o cliente clica nele. Como alternativa, se sua personalização preenche o documento com os dados quando ele é aberto pela primeira vez, mas a personalização não fornece outros recursos que são acessados diretamente por clientes, em seguida, você pode chamar RemoveCustomization assim que a personalização Inicializando o documento de conclusão.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Para remover o assembly de personalização de documentos fechados ou um documento em um servidor  
  
1.  Em um projeto que não exigem o Microsoft Office, como um aplicativo de console ou formulários do Windows, adicione uma referência ao assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Adicione o seguinte **Imports** ou **usando** à parte superior do seu arquivo de código.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Chamar estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> método o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> de classe e especifique o caminho do documento de solução para o parâmetro.  
  
     O exemplo de código a seguir pressupõe que você está removendo a personalização de um documento chamado **WordDocument1.docx** que está na área de trabalho.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Compile o projeto e executar o aplicativo no computador em que você deseja remover a personalização. O computador deve ter o Visual Studio 2010 Tools for Office Runtime instalada.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Como anexar extensões de código gerenciado aos documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  