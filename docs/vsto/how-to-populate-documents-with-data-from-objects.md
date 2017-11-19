---
title: 'Como: preencher documentos com dados de objetos | Microsoft Docs'
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
- data [Office development in Visual Studio], adding to documents
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 418e56c83a463c10d9dfc990236315751e07c000
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Como preencher documentos com dados de objetos
  Acessar dados em um objeto de dados funcionam da mesma maneira no nível de documento para o Microsoft Office Word como faz em projetos de formulários do Windows. Use as mesmas ferramentas e código para trazer os dados de um objeto para sua solução, e você pode usar controles de formulários do Windows para exibir os dados. Além disso, você pode exibir dados usando controles de host. Controles de host são objetos nativo no Microsoft Office Word que foram aprimorados com eventos e a capacidade de associação de dados. Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Você deve concluir as três etapas básicas para popular o documento com dados de um objeto:  
  
-   Adicione um controle para o documento que você pode associar aos dados.  
  
-   Adicione um objeto de dados para o documento.  
  
-   Conecte-se o objeto de dados para a BindingSource.   
  
## <a name="adding-a-data-object"></a>Adicionar um objeto de dados  
  
#### <a name="to-add-a-data-object"></a>Para adicionar um objeto de dados  
  
-   Abra o **fontes de dados** janela e criar uma fonte de dados de um objeto. Para obter mais informações, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>Conectar-se o objeto de dados para a BindingSource  
 Em projetos de nível de documento, você adicionar controles ao documento e associá-las a dados em tempo de design.  
  
 Em projetos de suplemento do VSTO, criar controles e associá-las em tempo de execução.  
  
### <a name="document-level-projects"></a>Projetos no nível de documento  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Para conectar-se o objeto de dados para a BindingSource  
  
1.  Arraste o campo de dados que você quer o **fontes de dados** janela para o documento. Isso cria automaticamente um controle.  
  
2.  Em seu código, crie uma instância do tipo de objeto que você escolheu para a fonte de dados.  
  
3.  Atribua a instância para o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade o <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="application-level-projects"></a>Projetos no nível de aplicativo  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Para conectar-se o objeto de dados para a BindingSource  
  
1.  Em seu código, crie uma instância do tipo de objeto que está associado com a fonte de dados.  
  
2.  Criar uma instância de um <xref:System.Windows.Forms.BindingSource>.  
  
3.  Atribua a instância de fonte de dados para o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade o <xref:System.Windows.Forms.BindingSource>.  
  
4.  Adicione a fonte de dados como uma associação de dados para o controle.  
  
## <a name="see-also"></a>Consulte também  
 
 [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources)   
 [Vincular controles de Windows Forms a dados no Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Conectando a dados em aplicativos do Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  