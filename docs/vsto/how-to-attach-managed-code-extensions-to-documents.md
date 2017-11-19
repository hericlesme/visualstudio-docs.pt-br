---
title: "Como: anexar extensões de código gerenciado a documentos | Microsoft Docs"
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3f5703b54a1deb96e9d6719c2726164e1002a18f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Como anexar extensões de código gerenciado a documentos
  Você pode anexar um assembly de personalização para um documento existente do Microsoft Office Word ou pasta de trabalho do Microsoft Office Excel. O documento ou a pasta de trabalho pode ser qualquer formato compatível com as ferramentas de desenvolvimento no Visual Studio e projetos do Microsoft Office. Para obter mais informações, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para anexar uma personalização para um documento do Word ou Excel, use o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe. Porque o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe é projetada para ser executado em um computador que não tenha o Microsoft Office instalado, você pode usar esse método em soluções que não estão diretamente relacionadas ao desenvolvimento do Microsoft Office (como um aplicativo de Windows Forms ou console).  
  
> [!NOTE]  
>  A personalização não carregarão se o código espera que o documento especificado não tem controles.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: anexar ou desanexar um Assembly do VSTO de um documento do Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Para anexar extensões de código gerenciado para um documento  
  
1.  Em um projeto que não exigem o Microsoft Office, como um aplicativo de console ou formulários do Windows, adicione uma referência ao Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll e Microsoft.VisualStudio.Tools.Applications.Runtime.dll módulos (assemblies).  
  
2.  Adicione o seguinte **Imports** ou **usando** instruções para a parte superior do seu arquivo de código.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Chamar estático <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> método.  
  
     O seguinte exemplo de código usa o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> sobrecarga. Essa sobrecarga toma o caminho completo do documento e um <xref:System.Uri> que especifica o local do manifesto de implantação para a personalização que você deseja anexar ao documento. Este exemplo assume que um documento do Word chamado **WordDocument1.docx** está na área de trabalho, e que o manifesto de implantação está localizado em uma pasta denominada **publicar** que também está na área de trabalho.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Compile o projeto e executar o aplicativo no computador em que você deseja anexar a personalização. O computador deve ter o Visual Studio 2010 Tools for Office Runtime instalada.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Como: remover extensões de código gerenciado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  