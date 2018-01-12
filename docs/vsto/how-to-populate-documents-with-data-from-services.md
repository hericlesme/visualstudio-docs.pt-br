---
title: "Como: preencher documentos com dados de serviços | Microsoft Docs"
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
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eb06e77cf45a3c912f569686cdbe246baece8a03
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Como preencher documentos com dados de serviços
  Acesso a dados funciona da mesma maneira no nível de documento do Microsoft Office, como faz em projetos do Windows Forms. Usar as mesmas ferramentas e código para trazer os dados para sua solução, e você pode até usar controles de formulários do Windows para exibir os dados. Além disso, você pode tirar proveito dos controles chamados controles de host, que são objetos nativo no Microsoft Office Excel e o Microsoft Office Word que foram aprimorados com eventos e a capacidade de associação de dados. Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 O exemplo a seguir mostra como adicionar controles de dados associados aos documentos em tempo de design. Para obter um exemplo de como adicionar controles associados a dados nos suplementos do VSTO em tempo de execução, consulte [passo a passo: vinculação de dados de um serviço em um VSTO suplemento no projeto](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como i: interagem com os serviços Web do Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Para popular um projeto no nível do documento com dados de um serviço Web  
  
1.  Abra o **fontes de dados** janela e criar uma fonte de dados de serviço para o seu projeto. Para obter mais informações, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).  
  
2.  Arraste a tabela ou campo desejado a **fontes de dados** janela para o documento.  
  
     Um controle é criado no documento, um <xref:System.Windows.Forms.BindingSource> é criado que é associado à classe de objeto em seu projeto e classes são geradas para o serviço.  
  
3.  Em seu código, crie uma instância da classe de serviço da Web que você se conectou no etapa 1.  
  
4.  Se houver propriedades que são necessárias para a comunicação com o serviço Web, crie instâncias dessas propriedades.  
  
5.  Criar e enviar uma solicitação de dados usando os métodos expostos pelo serviço da Web e de qualquer instância de propriedade criado na etapa 4.  
  
     Os métodos que você usa dependem do serviço Web oferece.  
  
6.  Atribuir a resposta de dados do serviço da Web para o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade o <xref:System.Windows.Forms.BindingSource>.  
  
 Quando você executar o projeto, os controles de exibem o primeiro registro na fonte de dados. Você pode habilitar a percorrer os registros manipulando eventos de moeda usando os objetos de <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="see-also"></a>Consulte também  
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources)   
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Como: preencher planilhas com dados de um banco de dados](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Como: preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Como atualizar uma fonte de dados usando dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  